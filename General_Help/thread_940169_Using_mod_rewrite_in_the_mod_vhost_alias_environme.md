---
title: "Using mod_rewrite in the mod_vhost_alias environment?"
date: 2008-10-06
forum: General Help
---

### Post by jusufd on 2008-10-06
I am just wondering how I can set the mod_rewrite configuration inside the mod_vhost_alias environment?

I added the rewrite configuration inside the vhost_alias.conf but it won't work.
----------------------------------------------------------------------
Here is vhost_alias.conf:
<Directory "/home/jusuf/webapp">
        DirectoryIndex index.cfm index.html index.htm
        Options Indexes FollowSymLinks
        AllowOverride None
        Order allow,deny
        Allow from all
       <IfModule mod_rewrite.c>
               RewriteEngine on
               RewriteLog /var/log/apache2/rewrite.log
               RewriteRule ^/product/([A-Za-z0-9-]+) /index.cfm?section=product&title=$1 [PT,L]
       </IfModule>
</Directory>
<Directory "/home/jusuf/webstorage">
        Order Deny,Allow
        Allow from all
</Directory>
Alias /images /home/jusuf/webstorage/images
Alias /js /home/jusuf/webstorage/js
Alias /css /home/jusuf/webstorage/css
Alias /music /home/jusuf/webstorage/music
Alias /video /home/jusuf/webstorage/video 
---------------------------------------------------------------
I also added the rewrite.load inside /etc/apache2/mods-enabled

I found the solution which is I remark the default conf for the default site inside the apache2.conf and move the rewrite configuration to the new file called "rewrite.conf" together with "rewrite.load" inside mods-enabled.

:)

---

