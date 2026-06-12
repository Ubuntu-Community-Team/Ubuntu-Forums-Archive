---
title: "Intel Graphics Video Tearing Problems"
date: 2009-08-13
forum: Hardware
---

### Post by Shibblet on 2009-08-13
I have a netbook (MSI Wind), and a Laptop (Dell Inspiron 1545), and they seem to function just fine with Ubuntu, even though they have Intel 945 graphics adapters.

The only place they really lack is with video playback.  I get constant tearing lines all over the video.

Tearing is usually a product of refresh problems, and I've noticed that Ubuntu doesn't actually have any settings in the xorg.conf file.  

Would setting this up correctly help with any refresh issues?

---

### Post by kerry_s on 2009-08-13
try adding:

```
	Option	    "MigrationHeuristic"	"greedy"
	Option	    "TripleBuffer"		"true"
```

to the device section.

---

### Post by Shibblet on 2009-08-13
Thanks for the input, but it didn't seem to help.  

Is this one of the issues with Intel Graphics Adapters?
I've read about the issues, but it doesn't sound like Karmic is going to have them fixed.

---

### Post by eldragon on 2009-08-13
im not using ubuntu anymore, but the 2.6.31 kernel brings lots of improvements for intel graphics, maybe you should try to backport a karmic kernel...(whatever that means ) im sure it will be much better

---

### Post by Shibblet on 2009-08-13
> **eldragon said:**
> im not using ubuntu anymore, but the 2.6.31 kernel brings lots of improvements for intel graphics, maybe you should try to backport a karmic kernel...(whatever that means ) im sure it will be much better

I've tried upgrading, and it disables my wireless adapter.  What are you using in place of Ubuntu?

---

### Post by lswb on 2009-08-13
If you have CCSM (compiz config settings manager, available from repositories via Synaptic or apt-get), go to General/Display Settings. The "sync to V blank" option may help.

If it does consider yourself very fortunate. Many people using Intel graphics, myself included, have serious video playback problems with stock jaunty install. I was only able to get acceptable and stable performance by using info from this thread to install a newer version of xorg and a newer kernel:

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

There is a similar thread I have seen that describes how to solve the problem by installing the older xorg used in intrepid or jaunty.

---

### Post by eldragon on 2009-08-13
> **Shibblet said:**
> I've tried upgrading, and it disables my wireless adapter.  What are you using in place of Ubuntu?

arch linux, but thats beside the point. ive got the same chipset, and until 2.6.30 ive had lots of problems with gpu performance.

2.6.30 turned out to be really buggy with my hardware, so now im using 2.6.31-rc which actually fixes almost everything....

anyway, one way to see if you can fix your issue is to check what "man intel" gives, it will provide you with many options to include to your xorg.conf, some might actually fix your issue.

if you post your /var/log/Xorg.0.log maybe i can hint you a bit more

---

### Post by Shibblet on 2009-08-13
Yeah, I've read all through that thread.  And for the most part, I don't have many issues.  Just tearing on the video, and a little flicker when I scroll down web-pages with images.

I want to know if this is going to be fixed in Karmic, or if any other Linux Distro doesn't have this problem.

---

### Post by mag1 on 2009-08-14
I also get video tearing with my samsung nc10 netbook, i do dual boot with xp but i find i use ubuntu most of the time so it would be nice to watch videos with it more, i would love a fix but not something that makes serious changes which may cause possible problems elsewhere, so im guessing there is no reasonably simple fix for this otherwise it would have been sorted by now? 

Can we expect to see an official fix come for jaunty in a future update?

---

### Post by eldragon on 2009-08-14
> **mag1 said:**
> I also get video tearing with my samsung nc10 netbook, i do dual boot with xp but i find i use ubuntu most of the time so it would be nice to watch videos with it more, i would love a fix but not something that makes serious changes which may cause possible problems elsewhere, so im guessing there is no reasonably simple fix for this otherwise it would have been sorted by now? 

Can we expect to see an official fix come for jaunty in a future update?

yes, its called karmic koala.

anyway, you are not providing with any relevant info for help. so i wouldnt know even what hardware youve got. if you have an intel GPU, my best advice would be to check what "man intel" provides and after reading through all the options, configure your Xserver accordingly.

---

### Post by Shibblet on 2009-08-14
> **eldragon said:**
> yes, its called karmic koala.

anyway, you are not providing with any relevant info for help. so i wouldnt know even what hardware youve got. if you have an intel GPU, my best advice would be to check what "man intel" provides and after reading through all the options, configure your Xserver accordingly.

See, I wouldn't be asking questions in the forums if I could find the answer in a manual.  

I've read through the Intel Graphics manual.  The problems are...

1.  How do I configure my Xserver?
2.  Which Graphics chip do I actually have?
3.  What are my horizontal and vertical refresh rates?
4.  Which options do I need to use?

---

### Post by eldragon on 2009-08-14
> **Shibblet said:**
> See, I wouldn't be asking questions in the forums if I could find the answer in a manual.  

I've read through the Intel Graphics manual.  The problems are...

1.  How do I configure my Xserver?
dpkg-reconfigure xserver-xorg i think it was (cant remember exactly). this should provide an initial xorg.conf file to tweak, intel options go under the device section (im sure the manual says that)
> 
2.  Which Graphics chip do I actually have?
this should be point #1 instead of 2, since the intel manual applies to...**drumroll** intel chipsets. lspci -vvnn should give you a buttload of info on your hardware.
> 
3.  What are my horizontal and vertical refresh rates?
forget about those settings, they got nothing to do with tearing. more related to screen resolution and modelines. they should be on the manual of your monitor.
> 
4.  Which options do I need to use?
depends. are you using EXA? XAA? UXA? like i said before, without a /var/log/Xorg.0.log there is not much i can help with.

---

### Post by mag1 on 2009-08-15
> **eldragon said:**
> yes, its called karmic koala.

anyway, you are not providing with any relevant info for help. so i wouldnt know even what hardware youve got. if you have an intel GPU, my best advice would be to check what "man intel" provides and after reading through all the options, configure your Xserver accordingly.

Im sure you knew what i meant by a fix for jaunty but yeah i can wait for the next ubuntu realase if i really have to, the hardware is the same or very similar on many netbooks otherwise i wouldn't be posting in this thread, the nc10 uses "Intel® 945GSE 128MB Integrated Graphics", i appretiate the help, i just wish there was a simple fix or an official update for this, im sure many have the issue but don't notice or care enough to come here and post, as long as the ubuntu devs know and try to make a fix at some point is what really matters, i think i can live with it for now, i just hoped there would be an easy fix for it that's all.  :(

---

### Post by eldragon on 2009-08-15
> **mag1 said:**
> Im sure you knew what i meant by a fix for jaunty but yeah i can wait for the next ubuntu realase if i really have to, the hardware is the same or very similar on many netbooks otherwise i wouldn't be posting in this thread, the nc10 uses "Intel® 945GSE 128MB Integrated Graphics", i appretiate the help, i just wish there was a simple fix or an official update for this, im sure many have the issue but don't notice or care enough to come here and post, as long as the ubuntu devs know and try to make a fix at some point is what really matters, i think i can live with it for now, i just hoped there would be an easy fix for it that's all.  :(

this is the problem all feature freeze distros have, once a version is released, you are stuck with whatever buggy software there is. the combo of
mesa 7.5
intel 2.8
kernel 2.6.30 or newer

fixes all issues you are having, even enabling kernel video modesetting works better than the legacy mode (userspace modesetting).

if you are willing to go through the hassle of manualy installing the above packages you will most likely see all your issues gone.

i strongly believe ubuntu should backport the intel drivers and the patckes to i915 in the 30 kernel so that all users with intel graphics can use their hardware hassle free. anyway, its not my call.

---

### Post by Shibblet on 2009-08-17
> **eldragon said:**
> i strongly believe ubuntu should backport the intel drivers and the patckes to i915 in the 30 kernel so that all users with intel graphics can use their hardware hassle free. anyway, its not my call.

I have to agree.  Most people, like myself, who use Intel Graphics adapters got them with a low priced laptop or netbook, and aren't really looking for bleeding-edge-performance.  Just good performance. 

If we want Uber-performance, we get Nvidia cards.

---

