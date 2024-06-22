## Build
FROM  beevelop/ionic:v2021.06.1 AS ionic
# Create app directory
WORKDIR /usr/src/app
# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied
COPY package*.json ./

RUN rm -rf node_modules && npm install -f --frozen-lockfile --ignore-engines --ignore-platform && npm install -f --dev typescript@3.5.3 --ignore-engines --ignore-platform

# Bundle app source
COPY . .
RUN ionic build
## Run 
FROM nginx:alpine
#COPY www /usr/share/nginx/html
COPY --from=ionic  /usr/src/app/www /usr/share/nginx/html