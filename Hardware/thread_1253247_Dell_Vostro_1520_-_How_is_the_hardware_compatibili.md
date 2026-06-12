---
title: "Dell Vostro 1520 - How is the hardware compatibility?"
date: 2009-08-29
forum: Hardware
---

### Post by johnnydopefish on 2009-08-29
Hello,

I'm considering getting a Vostro 1520 and will want to install Ubuntu over pre-installed Vista.  

In the past I had a tendency to buy hardware without checking the HCL, then tear my hair out in frustration trying to make it work.  I'm trying to do things differently nowadays but I don't see many reports, successful or not, concerning this laptop-- just a few sporadic problems here and there, nothing consistent.

My biggest concern is the wireless.  I would appreciate some confirmation that wireless works with WPA-PSK/TKIP networks (specifically on the Dell Wireless 1397 card).  In the past I've been burned by reports saying "hey, (some card) works with NDISwrapper" only to find that they didn't test against anything more sophisticated than WEP.

So is anybody running Ubuntu on a 1520?  I'd appreciate any information concerning your experience installing/configuring Ubuntu on it.

Thanks

Updates:
For archival's sake, I did find one report for running Arch that looked alright.  No confirmation on the wireless encryption though.
[http://www.linlap.com/wiki/dell+vostro+1520](http://www.linlap.com/wiki/dell+vostro+1520)

---

### Post by johnnydopefish on 2009-09-01
Well, I went ahead and ordered one anyway and will update the HCL accordingly.  Here's hoping it works out.

---

### Post by hodet on 2009-09-01
i just got my Vostro 1520 yesterday and the wireless worked fine from a stock install.  I have only tried WEP but the options are there for WPA and should hopefully work fine.  There appears to be a bug with the touchpad and keyboard that can be rectified by adding a change to your grub.conf file and updating grub.
details here
[http://ubuntuforums.org/showthread.php?p=7633298#post7633298](http://ubuntuforums.org/showthread.php?p=7633298#post7633298)

this fix has worked for me so far but I am working on a limited sample.  :-)

everything else seems to work fine.

good luck

---

### Post by shelbijoseph on 2009-09-02
Really I am very disappointed with Ubuntu 9.04 on Vostro 1520. The worst part is keyboard and the touch pad which I arranged by adding a line on the grub(still it gets stuck sometimes). I also suffered with samba which could n't give access to windows machines.  Now for the last few days I am battling with audio problems. First of all gnome-volume-control does n't show much options like in the other machines. I could more or less arrange the audio level but now when I reboot, I get distorted audio. Built in microphone does n't work (I stll could n't find solutions) and finally when I connect a headphone you can hear audio both on the headset and the speakers..weird.

It's such a pity that a good machine like vostro is completely hostile to ubuntu.

If you find any solution, pls, send me your comments.

Thanks and good luck

shelbi

---

### Post by hodet on 2009-09-02
i just got my notebook but will check these things you mentioned.  I watched a movie last night and sound was working fine with the headset.  I never noticed if sound  came out of the speakers.

So far it has been pretty impressive for me.  Sucks about the keyboard/trackpad.  I fully expect to have problems as well now.

---

### Post by johnnydopefish on 2009-09-03
Argh.  Where were all you guys *before* I placed the order? :P

Sort of unrelated question-- how long does it typically take Dell to ship orders?  In the past I got stuff pretty quick from them but they're telling me my new laptop is not expected to be delivered for another two weeks, and it's been "in production" for the last few days.

---

### Post by hodet on 2009-09-03
Took about a week and a half to receive. I am in Ontario Canada.  I don't know but this thing is working sweet for me.  I guess everyones mileage may vary.  I have had no issues with networking or sound or anything,  the only thing I have not tested is the camera but I have no real use for it anyway.

Ubuntu has come a long way.  My only disappointment is no straight way to do full disk encryption without requiring an engineering degree.  I was pumped when Truecrypt had a Linux version but it does not do full disk encryption the way it does in Windows.  Ah well....one thing at a time.  Since fixing the crashing keyboard and touchpad this thing works very well for me.

---

### Post by jobst on 2009-09-04
> **shelbijoseph said:**
> Really I am very disappointed with Ubuntu 9.04 on Vostro 1520. The worst part is keyboard and the touch pad which I arranged by adding a line on the grub(still it gets stuck sometimes). I also suffered with samba which could n't give access to windows machines.  Now for the last few days I am battling with audio problems. First of all gnome-volume-control does n't show much options like in the other machines. I could more or less arrange the audio level but now when I reboot, I get distorted audio. Built in microphone does n't work (I stll could n't find solutions) and finally when I connect a headphone you can hear audio both on the headset and the speakers..weird.


Keyboard problems, granted but only upon startup.
Its rather strange that you mention samba and make that part of a vostro problem, it cant.

Jobst

---

### Post by jobst on 2009-09-04
> **johnnydopefish said:**
> Well, I went ahead and ordered one anyway and will update the HCL accordingly.  Here's hoping it works out.

It works for me and bloody good (ubuntu 9.04).

granted, their is a startup problem with the keyboard, but this is fixable in many ways and it is a known issue not only for the vostro but for many other machines.

I can suspend/hibernate and it comes back cleanly.
I use my (windows) mobile and bluetooth to surf the net (phone becomes a modem).
I use evolution with sync to update my calendar/contacts/etc from/to my mobile.
I use the laptop as my on the road development station (LAMP) to create webpages/online stuff etc and then use rsync to update the real servers.
I can log into one of my servers and can do emergency work.
I can dual boot with XP.

The only time, in fact, I use XP is to edit office 2007 documents ... 

In fact, I am going to copy content of my laptop onto my company linux box to scrap FC11 for good (but I have a XP workstation too).

---

### Post by hodet on 2009-09-04
Built in webcam now working.    I would say the Vostro 1520 is a fine laptop for ubuntu 9.04.  I can connect to the windows network.  Print to shared printers, copy files back and forth.

Only two annoyances left.  Comes with firefox 3.0x instead of 3.5.   installed 3.5 that is unsupported but have run into issues with flash.
Full disk encryption remains a black art. <--- this one is pretty big for me but I will hammer at it.

Also the keyring manager when doing autologins is a pain (although not Vostro specific), but there is a good tutorial to fix it here;

[http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/)


Edit: Crap just noticed that the speaker still plays when headset plugged in.

---

### Post by johnnydopefish on 2009-09-10
Did you guys install using the alt cd or the live cd?

I installed it twice so far-- the first time using livecd.  No problems whatsoever.
Second time, did the alt cd (because I wanted /home encryption).  The keyboard failed during the installer bootup.  Reboot; installed fine, but on subsequent reboot I lost keyboard control again.

Trying to see if there's a pattern here.  I might try install via livecd again.

---

### Post by hodet on 2009-09-14
live CD here

---

### Post by jward3010 on 2009-09-19
> **shelbijoseph said:**
> I also suffered with samba which could n't give access to windows machines.
That has nothing to do with the laptop, samba is a pain in Ubuntu still, it will go fine if you're good with the smb.conf file. Check this: [http://ubuntuforums.org/showpost.php?p=7903299&postcount=6](http://ubuntuforums.org/showpost.php?p=7903299&postcount=6)

I'm thinking of buying a Vostro 1520, but wont let the Ubuntu incompatibility mess me up. I'll use Vista mostly until the compatiblilty gets better, at the mo it sounds pretty good anyway. Once wireless works and screen resolution is good.

---

### Post by jward3010 on 2009-09-19
To fix the keyboard problem... You've probably seen this but...

"Appending "i8042.reset i8042.nomux i8042.nopnp i8042.noloop" to the end of line "kernel /boot/vmlinuz-2.6.28-15-generic.............."(/boot/grub/menu.lst) works like a charm.

Another description of what to do: [https://bugs.launchpad.net/ubuntu/+bug/341094/comments/14](https://bugs.launchpad.net/ubuntu/+bug/341094/comments/14)

---

### Post by fahadghani on 2009-11-26
> **hodet said:**
> Built in webcam now working.    I would say the Vostro 1520 is a fine laptop for ubuntu 9.04.  I can connect to the windows network.  Print to shared printers, copy files back and forth.


Hey! Can you tell me how to get the webcam working? Ubuntu doesn't detect it on my Vostro. =/
Thanks in advance!

---

### Post by jward3010 on 2009-11-26
> **fahadghani said:**
> Hey! Can you tell me how to get the webcam working? Ubuntu doesn't detect it on my Vostro. =/
Thanks in advance!
Install cheese.
```
sudo apt-get install cheese
```

---

### Post by fahadghani on 2009-11-27
Thanks buddy!!! that worked great! :)

---

### Post by jward3010 on 2009-11-29
I'm not much of a webcam user but I've found cheese to work except for a little mess here and there with jerky video that seems to constantly re-scan the image. Sometimes it's great, sometimes it's hopeless. 

Also give Empathy a try, it also has a webcam mode and that will allow you to use your favoured IM protocol (Yahoo, GoogleTalk, AIM etc.) with your webcam (if they support it of course).

---

