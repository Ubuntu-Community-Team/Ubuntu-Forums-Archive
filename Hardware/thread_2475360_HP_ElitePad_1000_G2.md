---
title: "HP ElitePad 1000 G2"
date: 2022-05-24
forum: Hardware
---

### Post by mail-2o on 2022-05-24
Is anyone else running Ubuntu on the Elitepad?

I've tried Xubuntu 21.04 and Mate 21.04 without much success - freezes or difficulty installing. Lubuntu 22.04 has been successful with a few irritations. IE 
[LIST]
[*]it doesn't retain my Bluetooth keyboard settings so I have to start it with a mouse attached through its somewhat strange USB dongle. 
[*]Also, I've yet to find out how to free the SD Card from 'Read Only'. 
[/LIST]

 A refurbished Elitpad is quite cheap and, in my short experience, works well. I tried it with Win 10 for a while but had forgotten how awful that system is apart from occasional necessary uses (ie Dragon Dictate).

---

### Post by TheFu on 2022-05-24
21.04 support ended in 2021.  Nobody should be using it today.  21.10 support ends in July, so it would be smarter to install the current LTS, 22.04, which gets 3-5 yrs of support, depending on the desktop.  The Gnome4 and Server 22.04 releases get 5 yrs of support (from April 2022).

BTW, using a rpiv4 to run a desktop is a really expensive way to get "meh" performance.  A 5 yr old, used, chromebook for $65 would perform better.  Seriously.  I've run Lubuntu on a 2G Chromebook from 2011 w/ a Celeron 29950u CPU. It wasn't bad.

Bluetooth is a really bad technology for use on desktops, for keyboards or mice. May be ok to use with speakers, if you don't mind others taking over your playback. BT security is and always has been a total joke.

If you copy an ISO to the microSD, it is read-only and will always be read-only.  ISO is a write-once format. There's no editing. That isn't part of the ISO standard.  There are tricks to have overlay file systems over the ISO.  mkusb can do that, but I don't think it works for non-BIOS systems like a raspberry pi.  For an x86-64 system, **mkusb**, **ventoy**, and probably 5 other tools can create an overlay file system so updates and /home are writable areas. The ISO isn't touched/modified in any way.

---

### Post by mail-2o on 2022-05-24
Thanks. Maybe a Chromebook would have been a better purchase. My use of Bluetooth is restricted to home, so not a security issue.
As for the SD issue, no this was not used for the ISO. I've tried reformatting it in Gparted in and out of the machine, and also using the native Win10, but it still appears as read only in Lubuntu. Reading around, it might be some sort of BIOS issue. 

BTW, my Pi4 is an excellent desktop machine for my uses.

---

### Post by guiverc on 2022-05-24
I'll repeat, Ubuntu 21.04 & all *flavors* are EOL (*end of life*)

[https://fridge.ubuntu.com/2022/01/21/ubuntu-21-04-hirsute-hippo-end-of-life-reached-on-january-20-2022/](https://fridge.ubuntu.com/2022/01/21/ubuntu-21-04-hirsute-hippo-end-of-life-reached-on-january-20-2022/)

> As of January 20, 2022, Ubuntu 21.04 is no longer supported. No more  package updates will be accepted to 21.04, and it will be archived to  old-releases.ubuntu.com in the coming weeks.

I have no experience using bluetooth devices so can't help there sorry.  I would expect the different desktops to be rather similar though, as the difference between them is the desktop (user interface & apps) with all of them using the same Ubuntu base.

---

### Post by mail-2o on 2022-05-25
I'm using Lubuntu 22.04. I think the problem is that on shutdown Lubuntu 22.04 save no user info ie the bluetooth settings, whereas Xubuntu 22.04, on my EliteBook, seems to. I'm trying to work out how to get around this. 

The fact that Lubuntu 22.04 works well on the ElitePad surprises me as it seems few people use this with Linux. As I said, a Chromebook might have been a better option for me.

---

### Post by mIk3_08 on 2022-05-25
> **mail-2o said:**
> Is anyone else running Ubuntu on the Elitepad?

I've tried Xubuntu 21.04 and Mate 21.04 without much success - freezes or difficulty installing. Lubuntu 22.04 has been successful with a few irritations. IE 
[LIST]
[*]it doesn't retain my Bluetooth keyboard settings so I have to start it with a mouse attached through its somewhat strange USB dongle.
[*]Also, I've yet to find out how to free the SD Card from 'Read Only'.
[/LIST]

 A refurbished Elitpad is quite cheap and, in my short experience, works well. I tried it with Win 10 for a while but had forgotten how awful that system is apart from occasional necessary uses (ie Dragon Dictate).
I do have my HP Elitebook with Linux Ubuntu installed in it and I'm using this for quite a while now. so far so good. I haven't encountered any errors and all the attached components devices are working smoothly. Thanks to Linux Ubuntu Devs. Regards and Cheers.

---

### Post by mail-2o on 2022-05-25
> **mIk3_08 said:**
> I do have my HP Elitebook with Linux Ubuntu installed in it and I'm using this for quite a while now. so far so good. I haven't encountered any errors and all the attached components devices are working smoothly. Thanks to Linux Ubuntu Devs. Regards and Cheers.Thanks, that's good to know. I'll persevere.

---

### Post by TheFu on 2022-05-25
Elitebooks and Elitepads are different lines of systems. Components change, sometimes even with the exact same model in the same line.  Sometimes, corporate customers can add a contractual mandate that components NOT change, but I'd never trust that with a home purchase.  I've seen mistakes make in huge corporations too - places with over 100K laptops.  When there is a component shortage, either wait or get what they have and deal with it. That happens lots in the corporate world.

When seeking tips to get any OS installed on any hardware, google is your friend.  Use "{OS version} {model number}" in the search terms.  Often, this will return any model-specific tricks for the install or the first boot or how some manual EFI files need to be moved around or renamed for EFI BIOSes that don't follow the standards.  There are still some out there,

---

### Post by mail-2o on 2022-05-25
Thanks. I forget what a difficult job the Ubuntu team have to do. I only wanted a 10" tablet to replace my UBtouch tablet that I destroyed trying to charge it from a cheap solar panel! Expensive error.

---

### Post by mIk3_08 on 2022-05-26
> **mail-2o said:**
> Thanks, that's good to know. I'll persevere. 
As far as I remember, few years ago when I started to use/install Linux Ubuntu Operating System with my HP Elitebook. some of the components wont work. Yes, that's true. And I haven't received any updates from the Linux Ubuntu Operating System to make it automatically run completely those built-in components in my laptop. example Bluetooth, wifi, fingerprint and etc. What I did is just read and read some of the thread in this community not only here but also on other community web discussion like askubuntu, debian community, wikiubuntu, launchpad and github and other Linux community website until I found out some discussion about sort of components which I also have in my laptop. And they discuss about the code located on github so I grab the code. But there are some of the code are to be modify because it might break your hardware system if you continue to use it on your own risk.  And I just follow some of the instructions then there.... The results amaze me! The components works smoothly. The key is just always be active to the community and read some of the discussion that may help you solve your device component issue. Regards and Cheers.

---

### Post by mail-2o on 2022-05-27
Thanks for all your advice. I see some helpful YouTube videos as well.

---

