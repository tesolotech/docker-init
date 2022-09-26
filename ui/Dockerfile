
FROM node:alpine as build-step

WORKDIR /usr/src/app

COPY package.json ./

RUN npm install

COPY . .

RUN npm run build

# Step 2

FROM nginx:alpine

WORKDIR /usr/share/nginx/html 

RUN rm -rf ./*

COPY --from=build-step /usr/src/app/dist/hello-world /usr/share/nginx/html 

