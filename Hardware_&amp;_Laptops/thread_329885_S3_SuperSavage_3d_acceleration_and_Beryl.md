---
title: "S3 SuperSavage 3d acceleration and Beryl"
date: 2007-01-02
forum: Hardware &amp; Laptops
---

### Post by tyrewt on 2007-01-02
I've been trying to get Beryl working on my IBM ThinkPad T23 laptop. Beryl runs, but has yellow lines though everything which leads me to believe it's an issue with video drivers for the S3 SuperSavage/IXC 16mb integrated card.

Does anyone know how to enable 3d acceleration for this card?

Has anyone with this particular laptop successfully got Beryl working? 

Thanks.

---

### Post by tyrewt on 2007-01-17
I've since used XGL and AiXGL.... no luck... anyone out there have Beryl working under a T23?

---

### Post by keith.burgoyne on 2007-04-01
This is something that I am interested in. I was under the impression Beryl required something a little more powerful than what a t23 has to offer -- but I would love to know if this can be done.

---

### Post by lopagof on 2007-05-21
You need to edit your xorg config 

look here> [http://www.vcn.bc.ca/~dugan/t23.html](http://www.vcn.bc.ca/~dugan/t23.html)

---

### Post by lopagof on 2007-05-21
Also what ubuntu version are you using as I am also using a t23:KS

---

### Post by tyrewt on 2007-05-30
I'm using Ubuntu 7.04 (The latest stable release).  So you have Beryl working on a T23 with this config? (That has got to be one of the worst help documents EVER, totally worthless)

Also, is your direct rendering on?  (Mine isn't, which is a bug)

---

### Post by lopagof on 2007-06-23
thats a problem as im a noob.

I think we need the dri drivers. they might be in 7.04 if not you might be able to get them through synaptic.

---

### Post by lopagof on 2007-06-23
I only posted it because there are not many documents about this sort of thing

as i said before we need the dri drivers from dri.freedesktop.org

---

### Post by dugan on 2007-06-25
> **tyrewt said:**
> That has got to be one of the worst help documents EVER, totally worthless

> **lopagof said:**
> I only posted it because there are not many documents about this sort of thing

I just received an email from Lopagof inviting me to join this thread, and the first thing I see is people saying THIS about my webpage. Wow. Thanks a lot, people.

Nevertheless, I'll try to help.

Start by verifying that the following lines are in your xorg.conf and that they have not been commented out:

```

Load       "glx"
Load       "dri"

Section "DRI"
  Mode 0666
EndSection

Section "Extensions"
  Option        "Composite"     "Enable"
EndSection

```

Then, and only then, check if DRI is working.

If not, then you're having driver trouble. The main forum thread for this is here:
[HOWTO: Enable DRI (3D support) on SAVAGE cards [http://ubuntuforums.org/showthread.php?t=75393]](http://ubuntuforums.org/showthread.php?t=75393). No offence, but I found it by searching the forums for "savage". I recommend reading through it (it's interesting, and the latest posts deal with Feisty) and, if needed, continuing the discussion there.

In my experience, though, KDE and Xfce slowed to a crawl on a T23 if I so much as enabled transparent windows. I would definitely not recommend setting up Beryl on this computer.

---

### Post by lopagof on 2007-06-26
> **dugan said:**
> 
In my experience, though, KDE and Xfce slowed to a crawl on a T23 if I so much as enabled transparent windows. I would definitely not recommend setting up Beryl on this computer.


odd as I can turn on all of kde's effects on a sabayon live cd without any noticable performance decrease.

Also there are features that change the speed in the bios, maybe that is affecting something?

---

### Post by lopagof on 2007-06-26
im not talking about beryl though

---

