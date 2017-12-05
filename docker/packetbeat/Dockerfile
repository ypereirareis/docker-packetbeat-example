FROM docker.elastic.co/beats/packetbeat:6.0.0

COPY packetbeat.yml /usr/share/packetbeat/packetbeat.yml

USER root

RUN yum -y install nc

RUN mkdir -p /var/log/packetbeat \
    && chown packetbeat /usr/share/packetbeat/packetbeat.yml \
    && chmod go-w /usr/share/packetbeat/packetbeat.yml \
    && chown packetbeat /var/log/packetbeat

COPY entrypoint.sh /usr/local/bin/custom-entrypoint
RUN chmod +x /usr/local/bin/custom-entrypoint

USER packetbeat

ENTRYPOINT ["/usr/local/bin/custom-entrypoint"]