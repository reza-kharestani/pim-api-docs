### Asset

We refer here to the asset of the [Asset Manager](/documentation/asset-manager.html#the-asset).

::: warning
This resource is only available in the [Entreprise Edition](https://www.akeneo.com/enterprise-edition/).
:::

:::warning
This resource is only available since the version 5.0 of the PHP API client.
:::

#### Get a asset of a given asset family

```php
$client = new \Akeneo\PimEnterprise\ApiClient\AkeneoPimEnterpriseClientBuilder('http://akeneo.com/')->buildAuthenticatedByPassword('client_id', 'secret', 'admin', 'admin');

/*
 * Returns an array like this:
 * [
 *   'code' => 'jeans_care_instructions',
 *   'values' => [
 *     'label' => [
 *       0 => [
 *         'locale' => 'en_US',
 *         'channel' => NULL,
 *         'data' => 'Jeans care instructions',
 *       ],
 *     ],
 *   ],
 * ]
 */
$client->getAssetManagerApi()->get('user_instructions', 'jeans_care_instructions');
```

#### Get the list of the assets of a asset family 

Assets are automatically paginated and can be filtered.

You can get more information about the available query parameters [here](/api-reference-asset-manager.html#get_assets).

```php
$client = new \Akeneo\PimEnterprise\ApiClient\AkeneoPimEnterpriseClientBuilder('http://akeneo.com/')->buildAuthenticatedByPassword('client_id', 'secret', 'admin', 'admin');

$cursor = $client->getAssetManagerApi()->all('user_instructions');
```

#### Upsert a asset of a given asset family

If the asset does not exist yet, this method creates it, otherwise it updates it.

```php
$client = new \Akeneo\PimEnterprise\ApiClient\AkeneoPimEnterpriseClientBuilder('http://akeneo.com/')->buildAuthenticatedByPassword('client_id', 'secret', 'admin', 'admin');

$client->getAssetManagerApi()->upsert('user_instructions', 'jeans_care_instructions', [
    'code' => 'jeans_care_instructions',
    'values' =>  [
        'label' => [
            ['locale' => 'en_US', 'channel' => null, 'data' => 'Jeans care instructions'],
        ]
    ]
]);
```

#### Upsert a list of assets of a given asset family 

This method allows to create or update a list of assets of a given asset family.
It has the same behavior as the `upsert` method for a single asset.

```php
$client = new \Akeneo\PimEnterprise\ApiClient\AkeneoPimEnterpriseClientBuilder('http://akeneo.com/')->buildAuthenticatedByPassword('client_id', 'secret', 'admin', 'admin');

$client->getAssetManagerApi()->upsertList('user_instructions', [
    [
        'code' => 'jeans_care_instructions',
        'values' =>  [
            'label' => [
                ['locale' => 'en_US', 'channel' => null, 'data' => 'Jeans care instructions'],
            ]
        ]
    ],
    [
        'code' => 'shirts_care_instructions',
        'values' =>  [
            'label' => [
                ['locale' => 'en_US', 'channel' => null, 'data' => 'Shirts care instructions'],
            ]
        ]
    ]
]);
```
