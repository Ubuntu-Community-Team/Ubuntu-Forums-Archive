---
title: "Best Installation of SSL Certificate"
date: 2008-08-27
forum: General Help
---

### Post by Bill Day on 2008-08-27
I am installing, at a minimum, Apache 2, Courier, Postfix, and Fetchmail all of which make use of a domain name SSL certificate.  I would like to be able to install one certificate for ease of maintenance.

Is such an approach feasible?

What is the best location for the certificate?

---

### Post by Dr Small on 2008-08-27
Greetings neighbor,
Have you read this?
[https://help.ubuntu.com/community/forum/server/apache2/SSL](https://help.ubuntu.com/community/forum/server/apache2/SSL)

Dr Small

---

### Post by Bill Day on 2008-08-27
Dr. Small,

Thank you for the very helpful pointer to the relevant documentation.  Having looked it over quickly, however, I think there is one remaining question.

Suppose, for example, I generate a signed certificate and install it in /usr/share/ca-certificates.

Can I then point Postfix and Apache to /usr/share/ca-certificates?

Alternatively, can I symlink /etc/apache2/ssl/apache.pem, for example, to the certificate in /usr/share/ca-certificates?

Or is it in fact necessary, every time I renew the certificate, to place a new copy in /usr/share/ca-certificates/, /etc/apache2/ssl/, /etc/posfix/ssl/ and so on?

Naturally, I will do whatever is required, but it seems as though it would be simpler if there were a way to have one certificate serve for all.

Sincerely,

Bill Day

---

