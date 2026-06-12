---
title: "Total Linux Noob Needs Some Guidance"
date: 2009-06-27
forum: Installation &amp; Upgrades
---

### Post by ASCIIraider on 2009-06-27
HI Guys,

Well decided to take the plunge away from the Microslop called Windows and installed Ubuntu 7.10 on my HP nc8000 (P4-M/1.4 with 768MB RAM) lappy.  Despite being an old PC Ubuntu installed flawlessly (only one issue relating to an ATI driver but the OS is running ok graphically at the moment so no need to fix this I feel).  So first comment is well done to all who contributed to Ubuntu 7.10, you've done a great job and I personally look forward to the day when it just doesn't make sense to use M$ software anymore.

Ok so I have three issues.
(1) How do I install KTorrent?
I have downloaded a package for version 2.2.8, but see no "setup.exe" file.  Some reading leads me to believe that I must somehow compile the source code for this program on my machine to make it run.   But how to do this escapes me.  Any suggestions would be greatly appreciated.

(2) While my Internet connection came up right away it is rather slow.  So I was wondering if this was a driver issue?  Or maybe I need to configure Ubuntu to maximise my Internet experience?  Again any help here would be great.

(3) In Windows the taskbar shows all the open programs but in Ubuntu I only see one icon on the left showing the currently active app.  How do I get buttons on the "taskbar" for all open apps to appear on the main panel at the bottom of the screen?  Cheers.

So far I am impressed with Ubuntu 7.10 and look forward to learning more about Ubuntu and Linux generally and then spreading the word myself to others.


Thanks.

---

### Post by mikewhatever on 2009-06-27
7.10 was a good release, buy it's no longer supported. Why not use the current 9.04?
Here is a guide to install software. The problem is, there are no repositories for 7.10,[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

Tell us more of you internet connection. Is DSL/cable, ethernet/usb, modem/router, etc.

Not all programs have a notification icon in Ubuntu, same as in windows, by the way.

---

### Post by ASCIIraider on 2009-06-27
Hey Mike,

Thanks for replying!

I guess I started with 7.10 as I wasn't sure if my poor old lappy could handle the newer 9.04 version.  Do you think it could?  It does have a dedicated ATI video card with RAM, but the CPU isn't much chop really.  I checked out the link you posted, and it looks pretty clear.  I did in fact fiddle a bit with the Add/Remove programs and the Synaptic Package Manager but could not get anything to install.  Maybe as 7.10 is no longer supported?  Or I'm just too silly? :(

RE: Internet
It's a 1.5Mbit ADSL1 connection and on Windows its pretty quick with Firefox.  But for some reason with Ubuntu it's a bit slow.  Not dial-up slow, but there's definitely a lag when loading pages.  Maybe upgrading to 9.04 will fix this?

RE: Notification Icons
Well all the active windows are present, it's just that you have to click on the one currently showing to get a vertical list of running programs from which you can switch to.  I guess what I was asking was how do you get them to appear horizontally along the "Ubuntu taskbar"?

Cheers.

---

### Post by mikewhatever on 2009-06-27
> **ASCIIraider said:**
> Hey Mike,

Thanks for replying!

I guess I started with 7.10 as I wasn't sure if my poor old lappy could handle the newer 9.04 version.  Do you think it could?  It does have a dedicated ATI video card with RAM, but the CPU isn't much chop really.  I checked out the link you posted, and it looks pretty clear.  I did in fact fiddle a bit with the Add/Remove programs and the Synaptic Package Manager but could not get anything to install.  Maybe as 7.10 is no longer supported?  Or I'm just too silly? :(

Your CPU and RAM are more then enough for the current version of Ubuntu. If fact, I think 9.04 is actually lighter, and I strongly advise reinstalling.
7.10 code named Gutsy Gibbon reached its end of life in Apr-2009.

> RE: Internet
It's a 1.5Mbit ADSL1 connection and on Windows its pretty quick with Firefox.  But for some reason with Ubuntu it's a bit slow.  Not dial-up slow, but there's definitely a lag when loading pages.  Maybe upgrading to 9.04 will fix this?

I suspect that is the difference between Firefox 3 in Windows and Firefox 2 in 7.10. The current version has the latest FF3.0.0.11. You can test you internet speed with speedtest.com.

> RE: Notification Icons
Well all the active windows are present, it's just that you have to click on the one currently showing to get a vertical list of running programs from which you can switch to.  I guess what I was asking was how do you get them to appear horizontally along the "Ubuntu taskbar"?

Cheers.

That should be working by default. In other words, all open windows appear in the bottom panel. If, for some reason, they don't, you may need to add the 'Window List' applet.

---

### Post by oldos2er on 2009-06-27
"How do I install KTorrent?"

 Normally you'd enter **sudo apt-get update && sudo apt-get install ktorrent** into a terminal, but 7.10's repos are no longer online.

---

### Post by philcamlin on 2009-06-27
> **ASCIIraider said:**
> HI Guys,

Well decided to take the plunge away from the Microslop called Windows and installed Ubuntu 7.10 on my HP nc8000 (P4-M/1.4 with 768MB RAM) lappy.  Despite being an old PC Ubuntu installed flawlessly (only one issue relating to an ATI driver but the OS is running ok graphically at the moment so no need to fix this I feel).  So first comment is well done to all who contributed to Ubuntu 7.10, you've done a great job and I personally look forward to the day when it just doesn't make sense to use M$ software anymore.

Ok so I have three issues.
(1) How do I install KTorrent?
I have downloaded a package for version 2.2.8, but see no "setup.exe" file.  Some reading leads me to believe that I must somehow compile the source code for this program on my machine to make it run.   But how to do this escapes me.  Any suggestions would be greatly appreciated.

sudo apt-get install ktorrent 

(2) While my Internet connection came up right away it is rather slow.  So I was wondering if this was a driver issue?  Or maybe I need to configure Ubuntu to maximise my Internet experience?  Again any help here would be great.

what network hardware do you have?

(3) In Windows the taskbar shows all the open programs but in Ubuntu I only see one icon on the left showing the currently active app.  How do I get buttons on the "taskbar" for all open apps to appear on the main panel at the bottom of the screen?  Cheers.

top right where you find the open apps :)

So far I am impressed with Ubuntu 7.10 and look forward to learning more about Ubuntu and Linux generally and then spreading the word myself to others.

9.04 is out eh :D 

Thanks.

i filled in the stuff inside

---

### Post by earthpigg on 2009-06-27
[http://en.wikipedia.org/wiki/Software_repository](http://en.wikipedia.org/wiki/Software_repository)

since everyone keeps mentioning software repos :P

---

### Post by ASCIIraider on 2009-06-28
Hey guys thanks for all the info and suggestions.

I am going to download Ubuntu 9.04 and run with that.  This is kind of a test run for me, if it all goes well I will look at switching to Linux on my desktop.

So far I am really impressed with Ubuntu and hope that more and more people start using and supporting it.  It's great to see that in this sometimes cynical world that people can come together for the common good and produce something outstanding without trying to grab money.

Long live the Open Source movement and man's humanity to man.

---

