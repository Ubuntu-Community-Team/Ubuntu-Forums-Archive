---
title: "External Harddrive"
date: 2007-12-23
forum: Hardware &amp; Laptops
---

### Post by jhyatt7823 on 2007-12-23
Today my western digital Hard drive decided to stop working,  Every time I plug it in the light turns on and it makes 7 or so consecutive clicking noises and then stops and never mounts.  Is there anything to try to fix this.  If not can I save the hard drive even if it means losing data.

---

### Post by edward4130 on 2007-12-23
the clicking is bad, you may not recover the data and the drive may be toast.

First check in gparted to see if it can mount or be seen.  That will tell if it is a full failure or not.. clicking is bad though

edward4130
kansas city ks

---

### Post by logos34 on 2007-12-23
If the drive has SMART capabilty (should), you can run some diagnotics on it.

sudo apt-get install smartmontools

info:

sudo smartctl -i /dev/sda (or 'sdb', whatever)

sudo smartctl -a /dev/sda

self-test (~10 min):

sudo smartctl -t short /dev/sda

---

### Post by xzero1 on 2007-12-23
You will very likely loose your data if you keep using your hd. Try a data recovery tool. I recommend spinrite see: [http://www.grc.com/sr/spinrite.htm]("http://www.grc.com/sr/spinrite.htm")
SMART is useless since you already know the drive has problems.

---

### Post by jhyatt7823 on 2007-12-23
Thanks for the feedback.  The smart thing did not work and I didn't have enough data to worry about buying the spin right software.  It is still under warranty would sending in be my only next option.  And what do they do with any data that they can get off my old drive?

---

### Post by Sef on 2007-12-23
Download [Knoppix]("http://knoppix.org") and see if you can get your data off.

---

