---
title: "Vertical lines in Lenovo lappy"
date: 2011-09-18
forum: Hardware
---

### Post by Leecher123 on 2011-09-18
From Live CD of both linux mint 11 and ubuntu 11.04 is showing high resolution 
1366x768 (16:9) but after installation they shows vertical lines.

i searched n found [http://ubuntuforums.org/showthread.php?t=1477668](http://ubuntuforums.org/showthread.php?t=1477668)
post it shows use of nomodeset command... after using tht i had no vertical lines problem but my screen resolution went down to 1024x786 (4:3).

how can i fix this permanently with high resoultion?? plz help :KS

1366x768 (16:9) is not showing in the option :(

---

### Post by foresthill on 2011-09-18
What model laptop and which graphics chip are you using? A little hardware info would be helpful.

---

### Post by Leecher123 on 2011-09-18
> **foresthill said:**
> What model laptop and which graphics chip are you using? A little hardware info would be helpful.

It's Lenovo L420
with Core i3-2310M Dual core processor
Video adapter is Intel HD graphics 3000 Family with latest driver version 8.15.10.2418

---

### Post by maul9999 on 2011-09-18
> **Leecher123 said:**
> It's Lenovo L420
with Core i3-2310M Dual core processor
Video adapter is Intel HD graphics 3000 Family with latest driver version 8.15.10.2418

Have you try hardware driver?

---

### Post by Leecher123 on 2011-09-18
> **maul9999 said:**
> Have you try hardware driver?

How to do that... well am new to Linux
Knows installing drivers for windows only....

will installing help??

---

### Post by maul9999 on 2011-09-18
> **Leecher123 said:**
> How to do that... well am new to Linux
Knows installing drivers for windows only....

will installing help??

Yeah, as long as this driver is a linux software.  Before you installing video card driver, you will want to go to System (it can be Administration too) then update manager.  Update everything.  then go to system again for hardware driver (restricted drivers manager or additional drivers)

Let's me tell you secret, I choose Geforce because of better support for linux video card driver.  Also it give you abilities to play many windows game and play game on VirtualBox.

---

### Post by Leecher123 on 2011-09-22
> **maul9999 said:**
> Yeah, as long as this driver is a linux software.  Before you installing video card driver, you will want to go to System (it can be Administration too) then update manager.  Update everything.  then go to system again for hardware driver (restricted drivers manager or additional drivers)

Let's me tell you secret, I choose Geforce because of better support for linux video card driver.  Also it give you abilities to play many windows game and play game on VirtualBox.

tried installing using updates still not working.

My question is that why is it showing high resolution when it's run by live cd
while showing low fixed resolution when it's installed on HDD.

---

### Post by maul9999 on 2011-09-22
> **Leecher123 said:**
> tried installing using updates still not working.

My question is that why is it showing high resolution when it's run by live cd
while showing low fixed resolution when it's installed on HDD.

Hmm... it look like bug in Ubuntu 11.04. You might want to go back to 10.11 or get beta update to 11.11.

---

