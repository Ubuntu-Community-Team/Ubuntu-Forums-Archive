---
title: "slapd and ssl - help"
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by greydove on 2009-10-07
I've been working through setting up LDAP on my ubuntu server following directions on [https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html](https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html)

I'm stuck on TLS and SSL section

I've gone through and created the Certificate Authority, several times, and the server key and the server certificate.  But once I enter them into cn=config and try to restart slapd, it won't start.

in /var/log/syslog I get 
Oct  7 06:52:00 pdc slapd[6856]: main: TLS init def ctx failed: -1

which I understand from googling is a problem with ssl certs or key

just ran openssl x509 -in /etc/ssl/certs/cacert.pem -noout -text and it spewed out lots of pretty info about the cert I created.  It did the same when I ran that command against the server crt which I created.  I'm not sure how to check the server.key file

Any assistance is greatly appreciated

---

### Post by greydove on 2009-10-08
I got it following instructions here [http://islandlinux.org/howto/installing-secure-ldap-openldap-ssl-ubuntu-using-self-signed-certificate]("http://islandlinux.org/howto/installing-secure-ldap-openldap-ssl-ubuntu-using-self-signed-certificate")  I'd love to figure this out with certs signed by a certificate authority, but I'll take self signed.

---

### Post by tanveer on 2009-11-29
I think this link will solve the problem if you have created your own CA certificates and to use those for SSL/TLS

[http://www.openldap.org/pub/ksoper/OpenLDAP_TLS.html](http://www.openldap.org/pub/ksoper/OpenLDAP_TLS.html)

---

