---
title: "My Journey Through Linux.. beginnings"
date: 2008-10-22
forum: General Help
---

### Post by sirdouglas on 2008-10-22
Hello Ubuntu Community,

I have had Linux for about a week now, and already have over 10 posts on the forums, most of which I'm sure were problems I had.  Some of them go buried within the hundreds of pages of posts.  Well, instead of posting another individual thread for every problem I currently face, I'll try throw everything together into one post.  After I resolve any issue through your help, I will edit my post (this option exists right?) and type "SOLVED" so that we can clarify obviously that the issue was solved.

The first version I installed was Ubuntu Ultimate 1.4.  It looked great, and I loved the feel of it.  There was an update available for Ubuntu 7.10, so I clicked away and waited for my upgrade to complete.  After installing, my first obvious problem appeared.  My external hard drive (which had been readable, not writable with the previous Ubuntu verision) did not work at all.  It was (and still is) unable to mount... not exactly what I was expecting after an "upgrade." (I posted about this here as well already but didn't resolve it)

At the same time, I was trying to dual-boot Windows Vista on top of my Linux to allow some specific programs to work, and at least be able to access my external HD.  I ran into yet another problem within the first step already- creating a partition.  I followed all instructions perfectly, but an error always appeared (see thread: [http://ubuntuforums.org/showthread.php?t=952923](http://ubuntuforums.org/showthread.php?t=952923)).  Well, I think my old 80gb hard drive (2.5") might be breaking down by now, so I just purchased a 320gb (time to upgrade anyways), so maybe that will solve the problem.  For now, I'm holding off on this issue.

Yesterday I finished the upgrade to version 8.04, and along with this came yet another problem.  My laptop's wireless had been working perfectly on the previous version of Ubuntu, but now I can not figure out how to connect.  I see the little symbol for wireless in the upper-right corner (along with the search feature, volume, etc), but after clicking on it I only see one clickable option- "Manual Configuration" (the other being "Wired Network" isn't clickable).  I have roaming mode enabled, but I don't see any place where I can find all the wireless networks available, and even after manually typing in the network name and acess key (and the symbol then shows that it is connected as far as my interpretation goes) I still cannot connect using Firefox.  Hm.  I would expect wireless connection to be easier after upgrading to 8.04.

Next, S-video.  Yes I am a newbie, former Windows-user (trying to adjust to the culture shock of Linux... but loving it!)and I was quite used to the easy Windows way of connecting my laptop to a TV using S=vdieo.  Now, I cannot find a way to connect, even after reading guide after guide supposedly explaing the process in simple terms.  Hm.  Well, any advice on working with this?  Where is the clearest, most simple guide for connecting a TV with S-Video?  Last time I tried and typed in dozens of commands in the terminal window, and for a while my computer wasn't even bootable... don't want that to happen again!

One problem I have involved importing my previous Firefox booksmarks.  Well, I gave up on trying to import them and took someone's advice of installing Foxmarks.  I manually found all my RSS fees again (I know there's a program for this as well, but I prefer Firefox) and updated my bookmarks callection.  After my upgrade to 8.04, all my bookmarks are gone!  I got a message from Foxmarks saying that my bookmark collection had change significantly (from 66 bookmarks to 1).  I obviously chose not to sync as this would erase my saved collection.  So, how do I add my previous bookmarks from Foxmark?

Okay, sorry for the beast of a message, and I know that I posted some of these issues before, but now we have it all organized in one place:)  Here's a quick summary of my issues:

1) External Hard Drive not detected
2) Partition Hard Drive not working
3) Wireless (SOLVED)
4) S-video, how?! (many resources available, I know, but no luck and afraid to blow up my notebook) (priority)
5) Foxmarks, where did my bookmarks go?! (must be an easy solution for this, right?)

Once again, I appreciate everything you guys do to help dummies like me:)  Thank you!

Doug

---

### Post by blackened on 2008-10-22
I learn best by breaking things and learning to fix them. It's good that you're staying positive about these things. :)

It might be helpful for you to first list what type of hardware you're running (especially your wireless adapter and videocard models).

---

### Post by sirdouglas on 2008-10-23
Eek, I was just gonna say that I have no idea what my specifications are... but a google search solves everything.  Copy/Paste:

 **Product Name   ** 	 dv1315cl
**US Product Number** 	EC138UA#ABA
**Microprocessor** 	1.73GHz Intel® Centrino™ Mobile Technology featuring Intel® Pentium® M Processor 740
**Microprocessor Cache** 	2MB L2 Cache
**Memory** 	1024MB 333MHz DDR System Memory (2 Dimm)
**Memory Max** 	2048MB
**Video Graphics **	Intel Graphics Media Accelerator 900
**Video Memory **	128mb (shared)
**Hard Drive** 	80GB 4200 Hard Drive
**Multimedia Drive** 	DVD±R/RW and CD-RW Combo Drive with Double Layer Support
**Display **	14.0" WXGA High-Definition BrightView Widescreen (1280 x 768) Display
**Fax/Modem **	high speed 56k modem
**Network Card** 	Integrated 10/100BASE-T Ethernet LAN (RJ-45 connector)
**Wireless Connectivity** 	Intel® PRO/Wireless 2200 802.11BG WLAN
**Sound** 	Altec Lansing
**Keyboard** 	101-key compatible & 2 Quick Launch Buttons
**Pointing Device **	Touch Pad with On/Off button and dedicated vertical Scroll Up/Down pad; QuickPlay Music and DVD buttons
**PC Card Slots **	

    * 1 Type I/II 32-bit card bus (also support 16-bit)

**External Ports 	**

    * 3 Universal Serial Bus (USB) 2.0
    * 1 headphone-out
    * 1 microphone-in
    * 1 VGA (15-pin)
    * 1 TV-Out (S-video)
    * 1 RJ-11 (modem)
    * 1 RJ -45 (LAN)
    * 1 Expansion Port 2
    * 1 IEEE 1394 Firewire(4-pin)
    * 1 Consumer IR (Remote Receiver)

**Power 	**

    * 65W AC adapter
    * 6-Cell Lithium-Ion (43Whr)
----------------------------------------------------

Is that better?  Just ask if any other information I could give would help solve my problems.  

Thanks so much!

Doug

---

### Post by sirdouglas on 2008-10-25
I'll bump this one as I've been the whole week without wireless, and I feel like the solution can't be too complicated.  Could anyone at least help me with that?  My second priority would be my external hard drive not working, and thirdly, if you could simply paste a guide for s-video (a simple guide) that would be spectacular.  

Thanks everyone!

Doug

---

### Post by blackened on 2008-10-25
Don't take this as a cop-out, because it's really not meant that way. The Release Candidate for 8.10 is out, and considering the vast improvements in laptop support under that release I would suggest downloading it and doing a clean install. 

Also you meantioned wanting to dual-boot Vista, and I've always found it much less hassle to install Vista first when setting up dual-boot with it.

---

### Post by TeXtonyx on 2008-10-25
[http://support.mozilla.com/en-US/kb/Backing+up+your+information](http://support.mozilla.com/en-US/kb/Backing+up+your+information)

Copy your firefox profile onto a USB stick or cd along with other
backups. If you lose your old profile, or install Firefox on
another machine, replace the profile that is newly created with
the backed up profile. That is called restoring not importing.
Without getting detailed, importing works when you have other
browsers installed; backup and restore is the easy way to do it.

---

### Post by sirdouglas on 2008-10-26
Woohoo, fixed the internet problem!  Now I just gotta figure out some of the others.. thanks everyone!

Doug

---

### Post by d_skillz on 2008-10-26
Try a live boot of intrepid 8.10 and let us know if wifi is detected.

---

