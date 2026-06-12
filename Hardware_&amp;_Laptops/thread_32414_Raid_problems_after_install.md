---
title: "Raid problems after install"
date: 2005-05-07
forum: Hardware &amp; Laptops
---

### Post by alexao on 2005-05-07
I am a former debian user so used to raidtools2. But I am having some problems with getting my software raid configurations working under ubuntu. 

I have the following setup, the supposed md0 is supposed to be: 
/dev/hdc5 and /dev/hdd5

md1: 
/dev/hde5 and /dev/hdg5

Since there are no raidtools software I tried configuring them via the installer, and it seemed to work, but not when the system booted it didnt mount since it said there was no device md0 or md1. I get the arrays working when i run the following commands after booting: 
mdadm --create --verbose /dev/md0 --level=0 --raid-devices=2 /dev/hdc5 /dev/hde5
answer yes on creating a new array
mdadm --create --verbose /dev/md1 --level=0 --raid-devices=2 /dev/hde5 /dev/hdg5
answer yes on creating a new array

and then mount them as usual. 

The question is how I can get them working direct from booting. If I put them in fstab I get the "there is no device"

---

