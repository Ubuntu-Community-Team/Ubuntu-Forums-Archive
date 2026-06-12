---
title: "Sony Handycam DCR-TRV18 Camcorder as web cam?"
date: 2006-09-15
forum: Hardware &amp; Laptops
---

### Post by Rinnt on 2006-09-15
Hi everyone,

Title pretty much says it all.  I have a Sony Handycam DCR-TRV18 camcorder that I would like to be able to use as a web cam.  My main purpose would be to do animations with the Stop Motion application.  Has anyone been able to get this to work under Ubuntu?  I have set the camcorder to "USB Stream" but it is not detected...

Thanks in advance!

---

### Post by Ashrael on 2006-12-04
Here! Here! I've got a Sony DCR-TRV240E and i hardly ever use it anymore, except as a webcam! It just gives superiour quality videoconferencing. 

Is there any software out there that fools the system into thinking it's a usb webcam? Or am I just thinkig 'W**D**S' again, and is there no need to trick Ubuntu?

Well any help will be appreciated!!

---

### Post by budgie9 on 2006-12-04
Eikga has some software plug-ins  that MAY help you guys.
I have tried the Firewire plug-in and so far have not managed to get it working. I do believe there is an update to the Ekiga software also on the site, but for me it requires a lib file that is already installed and I can't seem to get past that. 
I don't know of any other option but this may help. You may also help me in return as I to would like to use the my Sony camera

---

### Post by chuvisco on 2007-01-16
> **budgie9 said:**
> Eikga has some software plug-ins  that MAY help you guys.
I have tried the Firewire plug-in and so far have not managed to get it working. I do believe there is an update to the Ekiga software also on the site, but for me it requires a lib file that is already installed and I can't seem to get past that. 
I don't know of any other option but this may help. You may also help me in return as I to would like to use the my Sony camera

I just got my firewire camera (Samsung SCD103 Mini DV) working with Ekiga.  I installed the libpt-plugins-avc package, then chose 1394AVC as the video plugin in the Ekiga preferences.  I was confused because it did not show anything under Input device; if I changed the plugin to 1394DC, it would find /dev/raw1394, but then it would come up with an error message.  Eventually I figured out that the camera works fine if I leave the video plugin as 1394AVC (which is what the camera uses in Kino), and then close the preferences window (even though the Input device is blank), the camera works just fine.  I think I should file this as a bug in Ekiga.

---

### Post by Ashrael on 2007-01-17
sorry, was out of office for a while, but now i'm back...I'll try this ekiga stuff, but i prefer it to be working in skype (more users) is there a skype protocol client other than skype itself??

thx..

---

### Post by chele on 2007-01-17
> **Ashrael said:**
> Is there any software out there that fools the system into thinking it's a usb webcam? Or am I just thinkig 'W**D**S' again, and is there no need to trick Ubuntu?I think what is needed is a way to feed the AVC (firewire) signal into V4L (video for linux). Or re-write the Video chat applications to be able to use AVC as well as V4L. That is what Ekiga has done.

I've looked a bit for a way to do that, feed avc to V4L, but did not find the trick. There may be a script around someplace that does it.

---

### Post by chele on 2007-01-17
> **Ashrael said:**
> .I'll try this ekiga stuff, but i prefer it to be working in skype (more users) is there a skype protocol client other than skype itself??Skype cannot be bothered to put out a decent (video) Linux client  themselves, never mind opening up their proprietary protocol so that other's can do the job for them. Ekiga has an experimental Windows client that I am testing now. I have tried to have a friend setup Windows Messenger (which does SIP) while I stay on Ekiga, but the audio did not go through.

---

### Post by Ashrael on 2007-01-27
@chele: you are right about skype!! their software sux for linux!! sound qualiy is soooo baaad....I even resorted to running skype in wine, but that doesn't work either (i can hear, but not be heard)...still workin' on that...So it seems there is no easy fix for my problem (well..problem?)...It's just for fun anyway, but i'm like a pitbull...once I bite, I rarely let go...:D 

thanx

---

