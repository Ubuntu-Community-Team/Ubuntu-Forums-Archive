---
title: "Problem installing cURL (with ssl support)"
date: 2008-08-30
forum: General Help
---

### Post by nightmarestreet on 2008-08-30
Hi folks,

I just installed curl, and I wasn't sure whether I had to install curl-ssl as well or not.

So I tested a simple script to log into an ssl page (which I tested in Cygwin on my Windows machine).

When I ran the exact same script on my Ubuntu box I got this error:

curl: (77) error setting certificate verify locations:
   CAfile: /etc/ssl/certs/ca-certificates.crt
   CApath: none


So I tried to install curl-ssl but apparently it is already installed.

Any ideas how I can get curl working with ssl?

---

### Post by nightmarestreet on 2008-08-30
It appears I was too quick to post this.

After some searching, I found this bug report: [https://bugs.launchpad.net/ubuntu/+source/curl/+bug/152781](https://bugs.launchpad.net/ubuntu/+source/curl/+bug/152781)

I installed ca-certificates as recommended and everything works now.

---

