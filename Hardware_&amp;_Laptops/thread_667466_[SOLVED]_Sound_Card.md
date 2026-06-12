---
title: "[SOLVED] Sound Card"
date: 2008-01-14
forum: Hardware &amp; Laptops
---

### Post by Rwild on 2008-01-14
Well, I had a problem with HDDs in Vista so I am looking to make Ubuntu my main OS.  I just tried the Live CD of 6.10 and couldn't view my NTFS drives but had audio.  Now, I am running 7.10, can view all of my drives, but have no audio.  I can see three different options for audio.  VIA (mobo), SBLive! (PCI Card) and a Realtek device.  

My volume levels are maxed out in the settings but I still have nothing.  Is there a trick I am missing? :confused:

---

### Post by eggdeng on 2008-01-14
To set the default card, run
```
asoundconf list
```
This will list the available cards. Now run
```
asoundconf set-default-card xyz
```
where xyz is the name of the card you wish to set as default as listed by the first command above. Reboot for changes to take effect.

---

### Post by Rwild on 2008-01-14
HIGH FIVE!  Perfect.  Thank you. :D

---

### Post by dstickst on 2008-01-17
@Eggdeng: Awesome, thanks! I had the same problem and this resolved the issue.

---

