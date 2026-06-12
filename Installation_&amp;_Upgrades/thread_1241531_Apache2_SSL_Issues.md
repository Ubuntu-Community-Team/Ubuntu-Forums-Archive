---
title: "Apache2 SSL Issues"
date: 2009-08-16
forum: Installation &amp; Upgrades
---

### Post by own3mall on 2009-08-16
I followed this guide here:

[http://www.akadia.com/services/ssh_test_certificate.html](http://www.akadia.com/services/ssh_test_certificate.html)

To create a self signed ssl key and certificate.

When I try to restart Apache2, I receive the following error:

```

 * Restarting web server apache2                                                                            Syntax error on line 1 of /etc/apache2/conf.d/ssl.crt:
Invalid command '-----BEGIN', perhaps misspelled or defined by a module not included in the server configuration

```What's causing this error?

I put the following lines in my apache2.conf:

```

SSLEngine on
SSLCertificateFile /etc/apache2/conf.d/ssl.crt/server.crt
SSLCertificateKeyFile /etc/apache2/conf.d/ssl.key/server.key
SetEnvIf User-Agent ".*MSIE.*" nokeepalive ssl-unclean-shutdown
CustomLog logs/ssl_request_log \
   "%t %h %{SSL_PROTOCOL}x %{SSL_CIPHER}x \"%r\" %b"

```What am I doing wrong?

---

### Post by dabang on 2009-08-16
The error message is complaining about
> Syntax error on line 1 of /etc/apache2/conf.d/ssl.crt:
but in apache2.conf you defined
> SSLCertificateFile /etc/apache2/conf.d/ssl.crt/server.crt
as certifcate... Are you sure the files are at the right place? If so, I'd guess there's something wrong with the crt file (like the error says).

---

### Post by lodp on 2011-09-02
Sorry for digging up this old thread, but it turned up on Google when I searched and I have the solution:

You have to move your key and certificate out of the /etc/apache2/conf.d directory, and place them somewhere else. Apparently when the certificate and key files are somewhere below conf.d, Apache reads them as if they were configuration files. Used to be fine in earlier versions though..

Anyway, if you just move the key and certificate files to /etc/apache2/ssl.crt and /etc/apache2/ssl.key respectively, it'll work.

---

### Post by own3mall on 2011-09-04
> **lodp said:**
> Sorry for digging up this old thread, but it turned up on Google when I searched and I have the solution:

You have to move your key and certificate out of the /etc/apache2/conf.d directory, and place them somewhere else. Apparently when the certificate and key files are somewhere below conf.d, Apache reads them as if they were configuration files. Used to be fine in earlier versions though..

Anyway, if you just move the key and certificate files to /etc/apache2/ssl.crt and /etc/apache2/ssl.key respectively, it'll work.

Interesting.  I will give it a try.  Thanks for the post.

---

