```
curl -i -X POST \\
    -H "Authorization: Bearer ${FLY\_API\_TOKEN}" -H "Content-Type: application/json" \\
    "${FLY\_API\_HOSTNAME}/v1/apps/my-app-name/machines" \\
  -d '{
      "name": "machine-syd",
      "config": {
        "image": "flyio/fastify-functions",
        "env": {
          "APP\_ENV": "production"
        },
        "services": [
          {
            "ports": [
              {
                "port": 443,
                "handlers": [
                  "tls",
                  "http"
                ]
              },
              {
                "port": 80,
                "handlers": [
                  "http"
                ]
              }
            ],
            "protocol": "tcp",
            "internal\_port": 8080
          }
        ]
      },
      "region": "syd"
    }'

```
**Status: 200**