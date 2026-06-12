---
title: "Ftp"
date: 2006-02-21
forum: Hardware &amp; Laptops
---

### Post by souteneur3190 on 2006-02-21
My friends school blocked limewire and most other P2P.  How do I set up an ftp server so she can download music from me.  Or is there any other way to send large amounts of files?

---

### Post by simon_is_learning on 2006-02-21
proftpd

that will make your computer an ftp-server.

sudo apt-get install proftpd

---

### Post by souteneur3190 on 2006-02-21
uh....one with a gui?  Or atleast show me how to work it in the command line.

---

### Post by Killgore on 2006-02-21
[http://ubuntuguide.squarecows.com/doku.php#ftp_server](http://ubuntuguide.squarecows.com/doku.php#ftp_server)

This is a good guide to setting it up. I would reccomend changing the default port to something very high eg >30000 because the common ftp ports could be blocked.

---

