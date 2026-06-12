---
title: "Ubuntu 9.04 and Adaptec 1220sa"
date: 2009-05-09
forum: Hardware
---

### Post by Ubunbar on 2009-05-09
Hello,
I'm a very very newbie to Linux. I installed Ubuntu 9.04 64-bit version. Most hardware installed automatically some needed some tweaking. I managed to get it all working except my Adapted 1220sa Raid controler.

I searched the web for a driver. But only found Suse and Redhat drivers. 

I downloaded the [Adaptec SATA HostRAID SHIM Package v1.6.12086]("http://www.adaptec.com/en-US/speed/raid/aar/linux/adp3132-openbuild-b12086_i386_tar_gz.htm") from the Adaptec website. I followed the instructions from chapter 5 of the readme. What I need to do according to the readme file is this:* ./Build ../driver-axxxxxx/ ../shipped-binary ../../linux-2.6.9-1.667\ try_quick=Yes*.

With lack of extensive documentation on how to proceed I installed 'rpm' and 'build-essentials'. I typed the needed string like below:
*sudo ./build ../driver-adp3132/ ../shipped-binary/ ../../linux-headers-2.6.28-11\ try_quick=Yes*

Then the console sais:
*sudo: ./build: command not found*

what else do I need to install and btw did I use the right 'shipped-binary'??


Hope you can help me! Really need this raid controler to work. And we don't want me to switch back to Windows, right? :)


Thanks in advance.

---

### Post by Ubunbar on 2009-05-18
Well, back to Windows it is then...

):P

---

