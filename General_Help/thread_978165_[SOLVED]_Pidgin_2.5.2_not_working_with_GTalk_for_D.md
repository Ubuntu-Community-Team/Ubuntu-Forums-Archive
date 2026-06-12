---
title: "[SOLVED] Pidgin 2.5.2 not working with GTalk for Domains"
date: 2008-11-10
forum: General Help
---

### Post by Zaskoda on 2008-11-10
I just upgraded from 8.04 to 8.10. Along with the new Ubuntu came a new Pidgin. I forget what was installed previous, but I think it was around 2.4.x... The new ubuntu has 2.5.2 installed.

Gtalk for domains (google apps) worked fine in the previous version of ubuntu, but now produces a "connection refused" error.

I've done a fair amount of searching both on these forums and across the Internet and haven't encountered the problem elsewhere. Is this WORKING for anyone else???

---

### Post by Zaskoda on 2008-11-10
And then I found the solution...

Under Advanced:
 Force old (port 5223) SSL: Checked
 Allow plaintext auth over unencrypted streams: Un-Checked
 Connect Port: 443
 Connect Server: talk.google.com
 Proxy type: Use Global Proxy Settings

Found the workaround here:
[http://www.manast.com/2007/05/11/how-to-configure-pidgin-to-work-with-google-talk/](http://www.manast.com/2007/05/11/how-to-configure-pidgin-to-work-with-google-talk/)

---

### Post by sourabh041149ece on 2008-11-17
Thank u so much it worked .
:)

---

### Post by Zaskoda on 2008-11-17
Ah sweet, I actually helped someone =)

---

### Post by gatux on 2008-12-11
Thanks!!! It works!!! At the end!!!!

Thank you so much!!:p

---

### Post by studo77 on 2008-12-13
That was sweet! Thanks Zaskoda. Been searching, and got numerous different solutions, but this one works.

---

### Post by baytuni on 2008-12-18
Everything were working by default settings until two days before and it suddenly stopped working. my msn account still works with pidgin but when trying to connect gtalk account I get a connection error and this is new. I tried the above solution but it does not help. Anyone has any solutions?

---

### Post by zloy_alenko on 2008-12-28
> **baytuni said:**
> Everything were working by default settings until two days before and it suddenly stopped working. my msn account still works with pidgin but when trying to connect gtalk account I get a connection error and this is new. I tried the above solution but it does not help. Anyone has any solutions?

can't login last few days. But now i've switched from invisible mode to available and it's connected.

---

