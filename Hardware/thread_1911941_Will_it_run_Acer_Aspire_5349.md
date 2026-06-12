---
title: "Will it run: Acer Aspire 5349"
date: 2012-01-19
forum: Hardware
---

### Post by Nico-dk on 2012-01-19
I'm looking to but an Acer Aspire 5349 with the following specs:

CPU: Intel Celeron B800 / 1.5 GHz (dual core)
Chipset: Mobile Intel HM65 Express
Mem: 8 GB DDR3 SDRAM - 1066 MHz
HDD: 500 GB - 5400 rpm (no brand or model specified)
GFX: Intel HD Graphics (128MB dedicated)

I did a little research, and it seems everything should work fine with Ubuntu.

Would anyone care to share experiences and/or thoughts on running Ubuntu on this setup?

Anything I should look out for?

---

### Post by xyzzyman on 2012-01-22
It'll run, but I'm surpised there's 8GB's of RAM with such a weak processor. With the programs you'd be running on it you'll never use more than 4. You may never even use more than 2GB's.

---

### Post by Nico-dk on 2012-01-22
Thanks, and yes the cpu is a bit on the week side. The other laptop I'm considering is a Toshiba Pro S500.

---

### Post by AlanR8 on 2012-01-22
I have an Acer 5742 and all is well. The only tweak was getting the brightness control to work properly, found at:

[http://ubuntuforums.org/showthread.php?t=1617362](http://ubuntuforums.org/showthread.php?t=1617362)

---

### Post by lenooh on 2012-04-08
Just bought an acer aspire 5349 (celeron B815, 2GB ram, 320 GB disk, 300€), installed 12.04 beta2 and all works except the brightness. Using the trick posted above solves the problem.

I do however have a problem with skype, but at this point I am not sure whether it's a software or hardware problem. Skype works (ie. it runs), but I cannot make calls and audio does not work.

---

### Post by lenooh on 2012-04-22
After using the laptop for some time, I noticed that it is often very sluggish. It "freezes" for a couple of seconds quite randomly.

It seems the disk provided with the laptop is very crappy, cheap and it has a huge spin-up time. Ubuntu power settings (or maybe the manufacturers setting) seem to be very aggressive, which causes the disk to spin-down after a very short time, thus making the laptop freeze whenever the disk was needed.

Disabling disk spin-down seems to solve the problem:
```
sudo hdparm -B 255 /dev/sda
```
but be warned, this will decrease battery life, and also it may damage your disk, if you drop your laptop or bump it somewhere.

The setting will be lost after a reboot.

---

