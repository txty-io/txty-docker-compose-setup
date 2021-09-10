ARG BUILDER_IMAGE

FROM $BUILDER_IMAGE as builder

FROM nginx:alpine

WORKDIR /var/www/texterify

COPY docker/web/nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80

COPY --from=builder /var/www/texterify/public /var/www/texterify/public

# Use the "exec" form of CMD so Nginx shuts down gracefully on SIGTERM (i.e. `docker stop`)
CMD [ "nginx", "-g", "daemon off;" ]
