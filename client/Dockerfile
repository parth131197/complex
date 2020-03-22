FROM node:alpine as builder
WORKDIR '/app'
COPY ./package*.json ./
RUN npm install
COPY . .
RUN npm run build

FROM ngnix
COPY ./ngnix/default.conf /etc/nginx/conf.d/default.conf
EXPOSE 3000
COPY --from=builder /app/build /usr/share/ngnix/html