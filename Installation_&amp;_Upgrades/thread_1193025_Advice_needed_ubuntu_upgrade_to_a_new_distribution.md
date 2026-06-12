---
title: "Advice needed: ubuntu upgrade to a new distribution"
date: 2009-06-21
forum: Installation &amp; Upgrades
---

### Post by RGPerson on 2009-06-21
We presently have 8.04 and it appears to be hosed after trying to install our Hauppauge HVR-1600.

I can't figure out how to get into the command line from boot, so I can't see anything there. I can't work with it at all.

I've heard 8.10 works great with the HVR-1600 so I'm willing to give it a try.

Can I install that and somehow keep all our stuff from 8.04?  What can I keep and what can't I? 

E-mail? E-mail settings?
Calendar items?
Downloaded items (video, etc.)
Bookmarks in Firefox....

Things like that.

Thanks

Gabrielle

---

### Post by merlinus on 2009-06-21
You can run the live cd and try to mount your ubuntu partition from that.  Most of what you are wanting to keep live in /home/user, and you may be able to back it up.  You will also have to show hidden directories, e.g. firefox settings and such will be in .mozilla,

---

### Post by lindsay7 on 2009-06-21
If you have a separate /home partition. You can install a newer version of Ubuntu and do so without coping over the /home partition. choose the manual installation and make sure you DO NOT check the format partition for the /home partiton. That will leave it alone and untouched.  Open Gparted and see how your drive is set up before you do anything.

---

### Post by radtek on 2009-06-21
+++100 for the separate /home dir!!!

I've been having trouble as well with the install of 9.04 64bit. I keep a separate /home dir too. So easy.  Also, I've found it wise *to keep an extra hard-drive with a working OS* so I can swap them out if the installation goes awry. **Which it almost always does**... A fresh install 1-2 times a year almost requires the extra hardware. 

I found the ext4 to be exciting and fast but it hosed my system right off the bat. I'm gonna try one more time with ext3- if it is too problematic and since 8.10 64bit runs like a dream for me (why upgrade perfection?) a longer wait will be required... At least in my case since I can't hack worth a damn.

Other than that stuff, a memory stick/dvd for your important files, bookmarks etc...? Plan ahead before you wipe your drive and lose all your important stuff.

---

### Post by RGPerson on 2009-06-21
> **radtek said:**
> +++100 for the separate /home dir!!!

I've been having trouble as well with the install of 9.04 64bit. I keep a separate /home dir too. So easy.  Also, I've found it wise *to keep an extra hard-drive with a working OS* so I can swap them out if the installation goes awry. **Which it almost always does**... A fresh install 1-2 times a year almost requires the extra hardware. 

I found the ext4 to be exciting and fast but it hosed my system right off the bat. I'm gonna try one more time with ext3- if it is too problematic and since 8.10 64bit runs like a dream for me (why upgrade perfection?) a longer wait will be required... At least in my case since I can't hack worth a damn.

Other than that stuff, a memory stick/dvd for your important files, bookmarks etc...? Plan ahead before you wipe your drive and lose all your important stuff.


If I put a USB drive in there, can I get to it by the terminal? The terminal is all I can boot to with our ubuntu 8.04 right now. 

Gabrielle

---

### Post by RGPerson on 2009-06-21
Okay, I've got my stuff backed up.  I halfway want to start fresh.  I also don't.  We'd have to relearn how to install our video card and then try this HVR again.

If I did do so, which version would it work best with?  Presently, it really seems to me that the HVR installed somewhat decently but that it messed with my ATI Radeon 4550 video card. 

We were able to get the GUI on an old monitor with low resolution. But then when we tried the TV again (32" HD LCD we've been using for a monitor for months) we now don't even get the distorted pictures we did have.  Just a blank screen. 

Gabrielle

---

### Post by radtek on 2009-06-23
```
If I put a USB drive in there, can I get to it by the terminal? The terminal is all I can boot to with our ubuntu 8.04 right now.

```

Should be able to do anything through the terminal- you just have to know how... I'm not the best to advise you on *how to do it.*

---

### Post by radtek on 2009-06-24
OK I must apologize about ext4 hosing my system. It was me installing the fglrx(?) drivers. Evidently I don't need to do this anymore to get video and audio codecs working properly. I *did* have to do this in 8.04 & 8.10 or I couldn't get anything to play except for ogg.

I just installed the 'good&bad' gstreamer libraries and I'm all good even with ext4 on my toshiba. Happiness abounds... My lappy is running even better and faster than ever with 9.04 64bit!!!

---

### Post by RGPerson on 2009-07-09
> **radtek said:**
> OK I must apologize about ext4 hosing my system. It was me installing the fglrx(?) drivers. Evidently I don't need to do this anymore to get video and audio codecs working properly. I *did* have to do this in 8.04 & 8.10 or I couldn't get anything to play except for ogg.

I just installed the 'good&bad' gstreamer libraries and I'm all good even with ext4 on my toshiba. Happiness abounds... My lappy is running even better and faster than ever with 9.04 64bit!!!

I've got my stuff backed up once. I've found it.  When I get my extra hard drive back (sent it away to a data recovery place with a crashed hard drive), I'm going to back up the new stuff I've added since.  Then I'm going to format my hard drive and start over!

We upgraded to 8.10 but now it will only boot in Mythbuntu, in some weird virtual partition on my HD in which my real home directory is in another place than the File System and in which the File System only has 340MB of free space and so won't install the ATI drivers that did work well under 8.04.  

When we get that drive back, I'm going to back up the home directory and then format and partition. I'm going to install fresh installs of 8.04, 8.10 and 9.04.  Then we'll be able to play around with the drivers and at least have one workable version as a backup. I can get 8.04 to work with my ATI but not with my Hauppauge. I supposedly can get 9.04 to work with the Hauppauge but not with my ATI...without some major tweakage. Not sure what will work with 8.10 when it has a real place on my HD. We'll see.

Gabrielle

---

