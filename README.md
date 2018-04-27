# Centos7 + PHP + Oracle OCI8 Extensions
# 安装脚本
```
wget https://github.com/caffeinalab/php-fpm-oci8/raw/master/oracle/instantclient-sdk-linux.x64-12.2.0.1.0.zip
wget https://github.com/caffeinalab/php-fpm-oci8/raw/master/oracle/instantclient-basic-linux.x64-12.2.0.1.0.zip
wget https://github.com/caffeinalab/php-fpm-oci8/raw/master/oracle/instantclient-sqlplus-linux.x64-12.2.0.1.0.zip

#oci8 安装

unzip -o instantclient-basic-linux.x64-12.2.0.1.0.zip -d /opt/oracle
unzip -o instantclient-sdk-linux.x64-12.2.0.1.0.zip -d /opt/oracle

cat  > /etc/php.d/oci8.ini << EOF
extension=oci8.so
EOF

# create symbolic links
ln -s /opt/oracle/instantclient_12_2/sqlplus /usr/bin/sqlplus
ln -s /opt/oracle/instantclient_12_2 /opt/oracle/instantclient
ln -s /opt/oracle/instantclient_12_2/libclntsh.so.12.1 /opt/oracle/instantclient/libclntsh.so
ln -s /opt/oracle/instantclient_12_2/libocci.so.12.1  /opt/oracle/instantclient/libocci.so
# install oci8
echo 'instantclient,/opt/oracle/instantclient' | sudo pecl install oci8
```
