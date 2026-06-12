---
title: "Total noob needs help with mounting external HD"
date: 2009-11-11
forum: Hardware
---

### Post by jack18 on 2009-11-11
OK, so my desktop got a BSOD a while back, resulting in Windows XP not loading at all. A computer savvy cousin informed me that I would have to reinstall Windows XP after rescuing my documents somehow.
 
Well, the cousin has recently been hard to reach so I've taken it upon myself to get the documents myself. I searched for help on the topic and found Ubuntu. I did what was needed (burning the ISO onto a CD, loading it on the desktop, etc) and managed to get access to the documents.
 
Now, I want to put them onto a recently purchased Western Digital 'My Passport' Essential 250GB external hard drive - which I am finding hard to do. When it comes to inputting codes in the Ubuntu terminal, I have no experience whatsoever. 
 
So, I need to know how I can mount the external hard drive in order to dump my files onto it. Remember, a major noob here, so small words please! :)

---

### Post by ad_267 on 2009-11-11
Hmm well it should really just show up on the desktop when you plug it in. If you go to Places -> Home, does it show up in the menu on the left, or if you click the computer icon? If not then you might need to use some terminal commands to get it mounted, but people here will help you with that.

If you can't find the drive, open a terminal from Applications - Accessories - Terminal and with the drive plugged in, run "lsusb", "mount" and "sudo fdisk -l" and post the outputs here. I don't know of all of those are needed but they should help give us some idea of what's going on :)

---

### Post by jack18 on 2009-11-11
> **ad_267 said:**
> Hmm well it should really just show up on the desktop when you plug it in. If you go to Places -> Home, does it show up in the menu on the left, or if you click the computer icon? If not then you might need to use some terminal commands to get it mounted, but people here will help you with that.
 
If you can't find the drive, open a terminal from Applications - Accessories - Terminal and with the drive plugged in, run "lsusb", "mount" and "sudo fdisk -l" and post the outputs here. I don't know of all of those are needed but they should help give us some idea of what's going on :)
 
I went to try those codes, however when the external hard drive is plugged in, Ubuntu seems to run incredibly slow. For example, after clicking on 'Terminal' it took at least 10 minutes for the terminal to show up. When I tried a code, nothing happened and I had to reboot.
 
I think I'm just going to bite the bullet and get a technician in. I get too easily frustrated trying to figure these things out myself!

---

