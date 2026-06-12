---
title: "BIOS problems: HP dv2000"
date: 2007-05-14
forum: Hardware &amp; Laptops
---

### Post by Prometheum on 2007-05-14
I've been running Ubuntu on my dv2000 laptop for around six months now; I started with edgy and switched to Feisty when it was in alpha. I've been having this problem the whole run, though it stabilized for the most part when I switched to Feisty. The problem is, I'll experience crashes, usually when leaving my laptop on overnight (with clear vents so that overheating shouldn't be a problem at all). These crashes are not logged anywhere I can see and I have assumed that they're related to my hardware. The effects of the crash are that my caps lock LED will flash and my screen with lock up, though my screen will light up (or maybe its lit when my laptop is closed, though I doubt it). The fans typically also start running more than they should. 

These crashes seem to be tied to Azureus, though I'm not sure and that's just my speculation. However, today I turned on my laptop after I experienced one of these crashes (I'm forced to do a hard power-off), my computer powered on, lit all the LEDs, and promptly did nothing. The BIOS wouldn't print, my USB drive wouldn't read or mount (the lights didn't go on) and CD's didn't seem to read. I couldn't get it to boot no matter what I did, and eventually I just left it for a few hours. It finally booted and I'm on now posting this, but I just crashed again while writing this (though fortunately I could boot it again) and I don't know when the next one will be.

Has anyone else on a dv2000 experienced this problem? I have an nvidia c51m (mcp51) mobo with an AMD Turion64 x2. How could I get this to stabilize?

---

### Post by Mikecore on 2007-05-14
I have had the same issue. with my dv2210us which is from the HP dv2000 family. I tried many differnet Linux OS's all with the same resault.  My laptop would freeze. The only thing I found out after scanning many linux fourms was linux will run on this hardware but not when its in a HP laptop and the problem dose seem to be in the BIOS.  (AMD Turion64 x2 + nvidia graphics)

I have finally given up on this laptop and gave it to my wife. I would be very careful HP doesn't like 
linux on its laptops and may not warranty any problems if it finds out you put linux on it.  After my 
disappointing time with this HP laptop I got my self a Toshiba Intel Duo core 2x. And no more pain.
:)

I did have Ubuntu running on it AMD64. I can say this it was fast as hell. to bad it keep freezing.

---

### Post by Prometheum on 2007-05-14
I've already experienced HP's fiiiine tech support for linux users. 

So there is **no** fix for this? It seems fitting, considering HP won't even mention the fact that other OS's exist on their website, but its such a shame.... this is my main computer and this wasn't happening much, until today when it just refused to even print the f***ing bios. 

Would any free bios run on it, or is that a totally implausible cause? Also, would there be any way to get it to print the BIOS? Does anyone know whats up with that?

---

### Post by teaker1s on 2007-05-15
I know that the keyboard indicator lights flashing will represent a driver error or hardware fault, it would be wise to check with hp but If I remember correctly the flashing light is a video display error-normally a driver error. most common  things are if the computer suspends. your system log  under 
System>administration>system log 
should help or you can look
/var/log/messages
:KS

---

### Post by Prometheum on 2007-05-15
This isn't happening related to suspension, it will occur almost randomly, sometimes when I'm running with high reasources, sometimes when I'm using no CPU at all. syslog and kernlog doesn't have anything in it pertaining to the crash. Things continue as normal and then I get the boot logs. I haven't checked /var/log/messages, but if it is BIOS would anything be logged?

I'm running the nvidia binary drivers, which shouldn't be an issue. The main problem is, recently, I have been unable to even boot my laptop, due to the BIOS refusing to display or do anything. I have a brick with power and LED's. Is there anything I can do to fix this?

---

### Post by teaker1s on 2007-05-15
if we are saying no bios sometimes after a bios update-if it's still the same expect a hardware fault

---

### Post by buckeliger on 2007-05-16
Does that mean, that the [Notebook I was planning to buy (link)]("http://http://www.notebooks.at/shop/store.asp/default/product/2767") would not work with ubuntu?! So far i had not read any serious problems with the dv2000 series.

---

### Post by teaker1s on 2007-05-16
we have had some incompatibilities with the dv series notebooks, particularly the dv6000.

On the other hand the bios provider is a well known one and there have been updates to resolve known issues.

What I am trying to discover is if we have no bios boot screen sometimes-this indicates bios/ hardware issue.

If we have bios screen every time-but it won't boot always=needs boot options

hope this answers your question

regards

Daniel

---

### Post by Prometheum on 2007-05-16
The specific issue is, my BIOS won't post, display, whatever you want to call it. I'm considerering that I may have just fried my mobo, but every now and again it'll boot successfully. If I try to reboot, it won't post, even immediately after a successful boot. 

I've read nothing about this before now, there is almost no documentation on this if any. Would there be any way to patch the bios, or is my mobo fried if it won't post?

---

### Post by buckeliger on 2007-05-17
Thanks for your replies, 

unfortunately I don't understand what that means in particular for my notebook in spe. I'd like to ask two questions: 

a) does the BIOS problem only affect AMD processors? At that time for me there are two affordable versions of the dv2000 with 14': 1. dv2141eu - AMD Turion™ 64 X2 TL-52 1,60 GHz 512 KB L2-Cache 667 MHz FSB + NVIDIA GeForce Go 6150 and 2. dv2105ea - Intel Core Duo T2050 - 2 x 1,6 GHz + Intel GMA 950. 
 
b) what do I learn about compatibility from booting Ubuntu as a live-cd?

---

### Post by teaker1s on 2007-05-17
booting a live cd on a laptop your considering is a great idea, the operating system will appear slower than when installed-but.
It will give you the chance to see if display and sound will be correctly displayed, without permanantly installing or changing anything.

maybe you would like to look at this link
[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29?highlight=%28dv6000%29]("https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29?highlight=%28dv6000%29")

---

### Post by buckeliger on 2007-05-17
Thanks for the Link! 

As it seems, it is a bit of a gamble if Linux will work properly on these systems. However i have not seen any other 14' notebooks in this price class and my two requirements are: small & Ubuntu. 

I'm currently downloading the 64-bit version and tomorrow I'll test the live-cd on both, the AMD and the Intel chipsets. 
Unfortunately the Dell Laptops with preinstalled Ubuntu are going to be out of my price range. For a lazy person like me, such a notebook would be the perfect solution :).

---

### Post by teaker1s on 2007-05-17
my advice is whatever your choice- make sure you have either nvidia or intel graphics, ATI are troublesome as ATI do not support linux well.

Sometimes we need to configure display (xserver-xorg) if you get a message from xserver on live cd that says it's not correctly configured-it's no big issue.

I would also recommend creating a duel boot laptop-as if you have any warranty claim or need to update a gps or pda etc it's handy:KS

---

### Post by buckeliger on 2007-05-19
uiuiui. i like it! (went with amd and nvidia graphics)

first: thanks for your advices!!! 
2nd: [http://www.kookdujour.com/blog/details/19](http://www.kookdujour.com/blog/details/19) this site helped a lot too
third: automounting removable devices should be disabled during resizing and creating partitions :) 

i know, this posts do not any longer fit to the thread, but maybe they are helpful nevertheless.

---

