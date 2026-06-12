---
title: "Sound card not recognised"
date: 2007-06-25
forum: Hardware &amp; Laptops
---

### Post by EYEdROP on 2007-06-25
Hello everyone. I am having a sound issue with ubuntu 7.04 and a Creative Soundblaster Audigy Se Platinum. I took my computer over to a friends house yesterday to compare windows and linux (which went great BTW), and everything was working tip top. I brought it back home to find my sound isnt working anymore. When I try to click on the sound mixer, I get the following messages:  
 
1. No volume control GStreamer plugins and/or devices found. 
 
 
2.  The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu. 
 
When I use alsamixer, I get this: 
 
ian@PR0BATR0N:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
ian@PR0BATR0N:~$  
 
Looks like all of the sudden it wont recognise the card. Help? I need this working soon.

---

### Post by EYEdROP on 2007-06-25
NM, I guess I just needed to re-seat the card. Sorry.

---

