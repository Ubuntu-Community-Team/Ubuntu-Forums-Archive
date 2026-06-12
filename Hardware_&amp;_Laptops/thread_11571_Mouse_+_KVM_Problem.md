---
title: "Mouse + KVM Problem"
date: 2005-01-17
forum: Hardware &amp; Laptops
---

### Post by Ampsonic on 2005-01-17
Hello, 

Sorry if this thread is posted in the wrong location, this seemed the most appropriate place.

Here is the problem I am having:

I am using a generic KVM to switch between my windows and my ubantu system.  Everything works fine on the windows system, but the mouse on the ubantu system acts very crazy, jumping around and opening random things. When the mouse is directly plugged into the ubantu system, it works fine. 

I found this thread on the topic: 
[http://www.ubuntuforums.org/showthread.php?t=2278](http://www.ubuntuforums.org/showthread.php?t=2278)
and that appears to describe my problem. 

In that thread, it says: "I justed edited my config file to represent the correct mouse settings."

I've tried to figure out how to do this on my own, but I'm quite new and have no idea. Any help would be appreciated. Sorry for the long winded post. 

-Nick

---

### Post by Darrena on 2005-01-17
I had this problem when I ran Slackware and updated to the 2.6 series of kernels.  If you do a google search you will see a lot of posts with people having problems like yours with different distro's and MANY different solutions.   I don't know what solution to suggest except that I gave up and switched to a Belkin USB KVM and it worked great, but an iogear USB and Belkin PS2 did not...

---

### Post by Ampsonic on 2005-01-17
What i'm really asking is how to I edit my mouse configuration?

---

### Post by bob k on 2005-01-18
[QUOTE=Ampsonic]What i'm really asking is how to I edit my mouse configuration?[/QUOTE]

These problems aren't usually the mouse config. They usually reside in the kernel mouse driver.

I had this problem in RH9 and they fixed it in FC2, and I never had the problem in warty. I'm using a TRENDnet KVM and all works good. There have been some work arounds like going to terminal mode and back to X every time you switch from windows.

---

### Post by Ampsonic on 2005-01-19
Solution! I'm sending the piece of crap KVM right back to newegg! Any suggestions on which KVM's do work with ubantu?

---

### Post by bob k on 2005-01-20
[QUOTE=Ampsonic]Solution! I'm sending the piece of crap KVM right back to newegg! Any suggestions on which KVM's do work with ubantu?[/QUOTE]

I'm using a Trendnet 210k. It has the kvm + sound and usb, works good here.

---

