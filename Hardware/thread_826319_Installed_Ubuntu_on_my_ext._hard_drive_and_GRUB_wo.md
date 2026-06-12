---
title: "Installed Ubuntu on my ext. hard drive and GRUB won't boot Vista"
date: 2008-06-11
forum: Hardware
---

### Post by open0source on 2008-06-11
I've installed Ubuntu on my external hard drive and it's working fine. I have two problems booting up, however.

1. When the external hard drive is disconnected, GRUB doesn't load and I can't boot Vista (internal drive)

2. When the external hard drive is CONNECTED, GRUB loads correctly. However, when I choose to boot Vista instead of Ubuntu I get an error before it boots up (that I can't quite remember, but it was either "DISK WRITE ERROR" or "DISK READ ERROR")

I *think* that what I'm asking is: how do I get GRUB installed on my internal hard drive (or the "MBR", as I've read about on some other forum posts) while running Ubuntu?  Or, if this isn't what I'm asking: how can I fix this problem?

---

### Post by meierfra. on 2008-06-11
I wrote a HowTo for your first problem:  Click on Dual in my signature.
If you post the output of

```
sudo fdisk -l
```
(l is a lowercase L) I can write up the HowTo tailored to your situation. Once you don't have to worry about the numbers, it is fairly easy.

Since you are having problems booting into Vista, I recommend to replace step 3 (Fixing The MBR) by

[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD]("http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD")

---

### Post by mike_pasara on 2008-06-11
i had a simmilar problem.

Put in your vista cd and boot from it... this should ask you what you want to do... you'll want to select repair then eventually find yourself to command prompt.

once you are there you'll type something along the lines of mbr fix or something along those lines, it's been a while and i don't remember exactly. 


What this will do is recognize that there is only 1 OS installed rather than 2... basically if you installed another OS on your external and its not in there the MBR thinks its going to be there then you get your error.

---

### Post by meierfra. on 2008-06-11
> Put in your vista cd and boot from it... this should ask you what you want to do... you'll want to select repair then eventually find yourself to command prompt.

This is part of the instruction in the link which I provided. But since Grub is not able to boot Vista, something more complicated must be going on. Also it is better to install Grub to the MBR of the external drive **before ** attempting to repair Vista, since otherwise the OP will no longer be able to boot into Ubuntu.

---

