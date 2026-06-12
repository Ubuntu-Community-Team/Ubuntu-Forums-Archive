---
title: "installation reaches prompt screen before finishing"
date: 2008-12-27
forum: Installation &amp; Upgrades
---

### Post by jonmo on 2008-12-27
First let me mention that I am trying to dual boot my laptop with windows and ubuntu.  Windows is already installed.  I shrunk the hard drive by 50 GB (was going to use ~20 for ubuntu, and was going to try to share the other 30 GB) so I should have enough raw room for ubuntu.  Anyway, here's what happens...

I boot to the ubuntu 8.10 cd.  It asks me to enter a language, I choose 'English'. It brings me to the selection screen (run ubuntu from cd, install, et) and I choose 'install'.  At this point ubuntu puts up its loading screen.  After the loading bar moves back and forth, and then fills up, the screen goes black except for a cursor.  Then it brings up a prompt screen with some non-relevant information, and a prompt (ubuntu@ubuntu:~$).  I wasn't expecting this at all.  I've installed ubuntu on my desktop, and it installed without issue.  After the loading bar on the desktop, it ran through a bunch of question and answer screens.

The only thing I can really think of, is that perhaps the video card on this laptop (ATI FireGL v5700) isn't compatible with any drivers on the disc.  Is this the case or is it something else?  If it is the case, how do I go about getting drivers that work with ubuntu, and how do I install them (do I do it in windows or at that prompt screen)?

Thanks for any help.

---

### Post by namdung on 2008-12-27
Try using LiveCD first to check for any issues. 
What is ur hardware spces? 
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by jonmo on 2008-12-27
Hardware specs:
ACPI x86-based PC
Proc - Intel Core 2 Duo T9600 2.8GHz
Mem - 4 GB
Video - ATI Mobility FireGL V5700
Network - Intel Wifi link 5300 AGN
Audio - Conexant High Definition SmartAudio 221
There's also a DVD/CD drive

If you need to know any other specs, ask specifically and I'll try to figure it out.  I'll try to use the LiveCD, but assume that it doesn't work unless I post.  Thanks.

---

### Post by andygegg on 2008-12-28
This isn't any help, but I got exactly the same symptoms on an old PC trying to install Ubuntu 8.10.  No idea what caused it nor what to do!

---

### Post by jonmo on 2008-12-29
andygegg: I think my problem is with switchable graphics, which I've found a solution for (about to try it out).  Since your pc is older this doesn't seem like it would be the problem.  Have you verified that all of your parts are supported and meet the minimum reqs?  Also that you have all of the required parts?

---

