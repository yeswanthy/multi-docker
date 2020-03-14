FROM node:alpine as builder

WORKDIR '/app'

COPY ./package.json ./

RUN npm install

COPY ./ ./

RUN npm run build	# this creates a build folder inside /app that need to be copied to nginx which is used for routing


FROM nginx

EXPOSE 3000

COPY ./nginx/default.conf /etx/nginx/conf.d/default.conf

COPY --from=builder /app/build /usr/share/nginx/html
