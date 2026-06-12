---
title: "[SOLVED] Can anyone help with this."
date: 2008-09-07
forum: General Help
---

### Post by tropdoug on 2008-09-07
Can any of the guru's here please see if they might be able to shed some light on this weird wireless issue with Hardy heron 

```
http://ubuntuforums.org/showthread.php?t=907060
```

The reason I am asking here is that there  has been 96 viewers and only 1 reply, who has the exact same issue. The issue seems to be a bug. If this is not the place to try to get more help, can a moderator point me to where I could hopefully get help. 

Thanks

Douglas

---

### Post by Kevbert on 2008-09-07
What's the wireless adapter ?  You are running Ubuntu 8.04 and not Kubuntu ?
Please post the output of 
```
lspci
```
It may mean that wpasupplicant has been corrupted.  Please run
```
sudo apt-get install -f
```
and report if any packages are/were broken.

---

### Post by tropdoug on 2008-09-07
Thanks guys, 

I finally found a solution, here 

[http://www.akyl.net/Network+Manager+problem+in+Ubuntu+8.04](http://www.akyl.net/Network+Manager+problem+in+Ubuntu+8.04)

it appears that the default network manager is still a little buggy. Anyway, after quite a few hours of searching I found that thread, followed it, and installed Wicd, and the issue is solved.. So I can't run those scripts above now. 

If there are others having a flaky wireless connection, try this it worked for me. 

Thanks for the assistance 

Douglas

---

