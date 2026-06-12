---
title: "find laptop bios password in linux"
date: 2009-10-22
forum: Hardware
---

### Post by whiffy badger on 2009-10-22
I have just had to replace the motherboard of an Acer aspire 3690 laptop with a 2nd hand motherboard that I bought on ebay.  Both my Windows and Ubuntu installs are showing problems, come to think of it, Windows is trashed but Ubuntu seems to be working very slowly but OK.

I was looking to boot from my hard drive so as do OS reinstalls but unfortunately it is set in bios to automatically boot from the hard drive and I can't change it to boot from CD as there is a phoenix bios password set by the previous mobo owner.  

I have tried the backdoor passwords found on the internet without any joy.

Is there any software which will allow me to find the phoenix bios password?  I have heard of something called "cmospwd".  Does it work?  How would I run it under linux - I am a bit of a linux noob so any assistance would be appreciated.

I suppose the only alternative would be to open the case up and find the cmos battery and clear cmos that way which is something I would like to avoid if possible.

---

### Post by IcarusR on 2009-10-22
Removing the cmos battery may not clear bios pw.
There are windows utilities that will clear bios pw. 
Possibly "Hirons Boot Cd" has such utils.

There is some info/suggestions here 

[http://rahulhackingarticles.wetpaint.com/page/Clear+BIOS+Password,+All+tricks+!]("http://rahulhackingarticles.wetpaint.com/page/Clear+BIOS+Password,+All+tricks+!")

Check the link at bottom of the page for pw removal windows util.

Some more utils at the bottom of this page

[http://technofriends.in/2007/10/14/tools-to-use-clearing-bios-password/]("http://technofriends.in/2007/10/14/tools-to-use-clearing-bios-password/")

If none of these work then trawl the net some more.

Good luck

---

### Post by tarps87 on 2009-10-22
In most cases unplugging the computer and then removing the battry will be enough to reset the password

---

### Post by IcarusR on 2009-10-22
> In most cases unplugging the computer and then removing the battry will be enough to reset the password 

I beg to differ, a lot of new mobos have a security chip that is non-volatile to store bios pw. Particularly laptops, IBM for example. 

Still worth trying though. Leave battery out for an hour or so.

---

### Post by tarps87 on 2009-10-23
> **IcarusR said:**
> I beg to differ, a lot of new mobos have a security chip that is non-volatile to store bios pw. Particularly laptops, IBM for example. 

Still worth trying though. Leave battery out for an hour or so.

Didn't know that, but then again I have only tried it on older motherboards.

---

### Post by IcarusR on 2009-10-23
Hirons Boot CD does indead have bios utilities. It is a useful cd to have around.

[http://www.hirensbootcd.net/]("http://www.hirensbootcd.net/")

---

### Post by H4F on 2009-10-23
if you're lucky you will be able to reset your pass just by removing bios.

if you're not than:
some bioses are non volatile memory. like IBM so you want be able to reset your pass by removing the battery.

More than that you want be able to use hiren boot cd in most cases because most probably first boot device is set to hard disk.

the only one way in that case is to read from the chip directly. which requires deep technical skills. 
one example here for IBM [http://sodoityourself.com/hacking-ibm-thinkpad-bios-password/](http://sodoityourself.com/hacking-ibm-thinkpad-bios-password/)

---

