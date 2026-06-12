---
title: "Logitech USB headset install"
date: 2005-01-29
forum: Hardware &amp; Laptops
---

### Post by dougr on 2005-01-29
Hi all,

I have a logitech headstet that is USB, and originally sold for the PS2 online service.

I am using this on a ThinkpadT23.

When I plug in the headset it shows that it installs fine and is recognized in the devices as a logitech headset.  Going into Sound, I also see a menu for the headset, but it is not nearly as extensive as the menu for the onboard sound.  Anyhow I am trying to use this with Skype for the most part.  Skype is giving me grief with my current soundcard.  I get a lot of clicking and cutouts.  I have done troubleshooting to verify it is not my network, skype, or the physical hardware(I think). I tested skype and the headset I am using on an identical laptop running windows XP and skype sounded great(this is on the same network as well).  I figure since this headset has an integrated soundcard, I may have better luck.

Anyway when I plug in the headset I can hear that it is definitely activated, and when I move the volume slider up or down for the headset the "hiss" gets louder or softer.  Also I am able to select the device in skype, but I do not hear any sound out of it.  

I guess I am wondering if I need to "unmute" the headset or something.  I am looking for a little direction.

Thanks
Doug

---

### Post by TristanMike on 2005-06-17
How did you get it to install?  I have the same thing, headset for PS2 Online, works in windows, can't get it to recognise in Ubuntu
thanx
TristanMike

---

### Post by Ciego on 2006-11-03
Did anyone ever get this PS2 headset to work?  I am currently trying to do the same thing.  I have a couple extra PS2 USB headsets that I would like to use in Ubuntu with Teamspeak.

---

### Post by icheyne on 2007-11-29
I managed to get it working. The problem is that the headset it not marked as being the default.

You can switch between headset and soundcard by installing and using asoundconf-gtk

---

### Post by aonegodman on 2008-02-05
> **icheyne said:**
> I managed to get it working. The problem is that the headset it not marked as being the default.

You can switch between headset and soundcard by installing and using asoundconf-gtk

I did a search for mentioned gtk program and can't find. Could you or someone please elaborate on how to get my Logitech USB Headset working in Skype on Ubuntu 7.10. Thanks.

---

### Post by aonegodman on 2008-02-05
> **icheyne said:**
> I managed to get it working. The problem is that the headset it not marked as being the default.

You can switch between headset and soundcard by installing and using asoundconf-gtk

Ok I got the program to install > asoundconf-gtk <

I tried to run it in Terminal and got this >

```

You need to make sure asoundconf is active!
By default, asoundconf's configuration file is ~/.asoundrc.asoundconf
and must be included in ~/.asoundrc. Open this file to make sure it is!

```

Any ideas?   Thanks.

---

