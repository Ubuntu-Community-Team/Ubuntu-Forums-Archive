---
title: "[SOLVED] open dns"
date: 2008-09-22
forum: General Help
---

### Post by dellboy on 2008-09-22
hi guys i am trying to get ubuntu to work with open dns as i need this for a moment as my own isp dsn is slow on updating and i need to work on a site i can see yet on my isp dsn as of now.

so on the site it says to up in 

gksudo network-admin

the network boxs comes up fine but it will not let me unlock for root so i can change it to use the open dsn ips

this the site i am reading it form
[https://www.opendns.com/smb/start/device/ubuntu](https://www.opendns.com/smb/start/device/ubuntu)

thank you for your help

---

### Post by Titan8990 on 2008-09-22
A much easier way of accomplishing what you want is to just add the site that is not contained in your DNS server to your /etc/hosts list. This will bypass name resolution and take you directly to the site.

Hope that helps.

---

### Post by dellboy on 2008-09-22
like this 

127.0.0.1	localhost
127.0.1.1	username-lindesktop
[www.site.com](www.site.com)

---

### Post by Dr Small on 2008-09-22
Add these two lines to /etc/resolv.conf:
```
nameserver 208.67.222.222 
nameserver 208.67.220.220
```

---

### Post by Titan8990 on 2008-09-22
> like this

127.0.0.1 localhost
127.0.1.1 username-lindesktop
[www.site.com](www.site.com)

Close but the point is to specify and IP here so that it does not need to contact a dns server:


127.0.0.1 localhost
127.0.1.1 username-lindesktop
xxx.xxx.xxx.xxxx [www.site.com](www.site.com)

---

### Post by dellboy on 2008-09-22
thank you Dr small that works great 


for anyone that reads this i did this

#my isp name server
#nameserver xxxxxxxx
#open dsn name server
nameserver 208.67.222.222 
nameserver 208.67.220.220

thank you Titan8990 else well. i could not use the host file because it not on its own ip as its a shared host :D

thank you again guys

a few thank yous coming your ways
> **Dr Small said:**
> Add these two lines to /etc/resolv.conf:
```
nameserver 208.67.222.222 
nameserver 208.67.220.220
```

---

### Post by doorknob60 on 2008-10-12
> **dellboy said:**
> like this 

127.0.0.1	localhost
127.0.1.1	username-lindesktop
[www.site.com](www.site.com)

Thanks for that, my Frets on Fire was giving errors on my Arch box until I added 127.0.0.1 localhost to it :) Finally I can play without booting into Windows :D

---

