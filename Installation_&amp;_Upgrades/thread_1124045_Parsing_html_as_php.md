---
title: "Parsing html as php"
date: 2009-04-12
forum: Installation &amp; Upgrades
---

### Post by cracker.wizard on 2009-04-12
Hi,

I just installed apache and php5 on my computer and everything seems to be working fine except that I want my html files to be parsed as php.

All my html files are kept in the directory /var/www, I have kept a file .htaccess in the same directory and added the following line

AddHandler x-httpd-php5 .html .htm .php .php5

but the html file is not getting parsed as php. Could someone tell what is the problem. Do i need to write something else in the .htaccess file. Or am I supposed to place the .htaccess file somewhere else.

Looking for your reply.

CW

---

### Post by hyper_ch on 2009-04-13
because you have no rights by default to overwrite those settings. You'll need to have a look at the site configuration and allow overwrite or add the .html as handler in the apache.conf

---

### Post by rage9 on 2009-04-13
Yeah that's probably not going to work so well.  PHP files have the php extention for a reason.  Also the PHP code in a php file executes between the <?php and ?> tags.

---

### Post by hyper_ch on 2009-04-13
the extension has no meaning if you tell apache how to handle the files.

---

