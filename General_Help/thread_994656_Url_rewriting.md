---
title: "Url rewriting"
date: 2008-11-27
forum: General Help
---

### Post by ravi.786 on 2008-11-27
Hi Team,
Here is the question which i am really struggling with from a long time....I have my website say([www.myweb.com](www.myweb.com)), When anyone hits it they see [https://68.111.1.111/(dummy-i.p](https://68.111.1.111/(dummy-i.p)), the i.p Address, I am running my website on apache and have ssl enabled.
Below is my Virtual host and URL rewriting please help..
*************************************************************
Listen 443
NameVirtualHost *:443

<VirtualHost *:443>
DocumentRoot /opt/docs/
ServerName [www.myweb.com](www.myweb.com)
ServerAlias [www.myweb.com](www.myweb.com)
<Directory "/opt/docs/">
allow from 68.111.1.11
Options +Indexes
</Directory>
SSLCertificateFile /root/apache2/cert/dummy.cert
SSLCertificateKeyFile /root/apache2/cert/dummy.key
SSLEngine on
</VirtualHost>

RewriteEngine on
RewriteCond %{SERVER_PORT} ^1234$
RewriteRule ^/(.*)$ https://%{SERVER_NAME}/$1 [L,R,NC]
************************************************************

1234 = Dummy port.

I need that my website should continue with the DNS and not show i.p Address...Help Appreciated.

---

### Post by ravi.786 on 2008-11-27
Please help...

---

