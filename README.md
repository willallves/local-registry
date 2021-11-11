# local-registry
Deploy a registry server
```
docker-compose up
```

# Generate certificates
```
openssl req -newkey rsa:4096 -nodes -sha256 -keyout certs/domain.key -addext "subjectAltName = DNS:localregistry.com" -x509 -days 365 -out certs/domain.crt
```

# Copy certificates
```
sudo cp certs/domain.crt certs/domain.key /usr/local/share/ca-certificates/
```

# Update certicates
```
sudo update-ca-certificates --fresh
```

# Download image
```
docker pull golang
```

# Tag image
```
docker tag golang localhost:5000/golang
```

# Push image
```
docker push localhost:5000/golang
```
