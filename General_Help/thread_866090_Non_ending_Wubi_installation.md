---
title: "Non ending Wubi installation"
date: 2008-07-21
forum: General Help
---

### Post by kachaloo on 2008-07-21
hello there
I have download wubi 8.04.1 from wubi-installer.org to install ubuntu on my xp.
When I run the wubi installer it ask for user name/language etc and on the next window it downloads ubuntu. BUT this is never ending process. I have 2MB broadband speed and it takes abot 50 mins to download about 700MB, BUT it is happening over and over.
I have waiting nearly 3 hours and all wubi do is redownling the same file over and over.
How can get it to the next step??

Scott

---

### Post by ago on 2008-07-21
It might be that there are problems with the server.
Download the Ubuntu 8.04.1 DESKTOP ISO manually and place it in the same folder as wubi.exe

---

### Post by kachaloo on 2008-07-21
Thanks.
I have downloaded an ISO and saved it next to wbu installer.

Installation went OK But I ave two Problems now.

1- My mouse not working. I tried PS2 and USB both failed.

2- I then selected the nvidia restricted(i guess) driver for 3D support which was downloaded and installed. After restart the Screen is just BLANK. 

How can I remove the nvidia driver for 3D support?
Why the Mouse is not detected? 

Regards

---

### Post by ago on 2008-07-21
Both look like xorg.conf problems, you can reset by booting in rescue mode, press esc at boot after "ubuntu"

---

### Post by steveneddy on 2008-07-21
It would be easier to partition and install it on your hard drive.

Just my .02

---

### Post by ebolaRETURNS on 2008-07-22
I'm having a similar problem detailed here:
[http://ubuntuforums.org/showthread.php?t=862795](http://ubuntuforums.org/showthread.php?t=862795)

sorry about all the bumping.

---

### Post by ago on 2008-07-22
> **steveneddy said:**
> It would be easier to partition and install it on your hard drive.

Just my .02

Video issues would be IDENTICAL as there is no difference whatsoever in the setup (as far as video goes) between a wubi installation and one to a dedicated partition.

---

### Post by jfare on 2008-07-22
> **ago said:**
> Both look like xorg.conf problems, you can reset by booting in rescue mode, press esc at boot after "ubuntu"

If I went into rescue mode -- what would I do to resolve the problem with xorg.conf?
[J.F.]

---

### Post by jfare on 2008-07-24
I recovered from MY situation like this... See: [http://ubuntuforums.org/showthread.php?p=5450062#post5450062](http://ubuntuforums.org/showthread.php?p=5450062#post5450062)
[J.F.]

---

### Post by satdat on 2008-07-25
same problem of repetitive down load i faced
was that server problem?

---

