---
title: "Help (if able)!: Upgrade to 9.10 Graphics Problem"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by Johnny M! on 2009-11-07
[B]Saturday 7-Nov-2009
-----------------------------

Second Posting of Topic - Please Help if you Can!
Thank you !!!!!!
---------------------------------------------------------------------

Serious Upgrade Problem (Ubuntu 9.04 to 9.10)[/B] 			
 			 			 		   		 		 		TGIF 6 Nov 2009
-------------------------

Hello Fellow Ubuntu Forumers,

Relatively new to Ubuntu; but have installed/used:

- 8.04 (Wubi)
- 8.10 (Clean Install - Dual Boot with GRUB to either Windows or Ubuntu)
- 9.04 (Upgrade from 8.10)
- 9.10 (Attempted Upgrade from 9.04) ????

My previous upgrade from 8.10 to 9.04 was painless and flawless. But my attempted upgrade from 9.04 to 9.10 had serious problems (ended up reverting back to 9.04 via Acronis True Image Home restoration).

Event Log:

- Attempted to Update 9.04 to 9.10 via Update Manager (29-Oct I think)
- Update appeared to go smoothly (but slow - I suffer from DSL)
- Booted into 9.10 and Desktop appeared normal; but I didn't have time to wring things out.
- A few days later, returned, booted up 9.10 and immediately ran Update Manager (maybe 20MB of stuff downloaded)
- Opened Firefox and was puzzled to see very strange Page Scrolling on web pages.
- Video was jerky and page extremely slow to scroll: almost like the video card was struggling to redraw the page as I scrolled down.
- So I first thought it was the new version of Firefox 3.5.4
- Then I noticed that all maximized window content scrolled the same way; regardless of application
- The jerky movement and slowness of page redraws rendered Ubuntu unusable!
- Smaller windows (sized 25% of my screen size) seemed to scroll OK?

- Troubleshooting:
- System / Administration / Hardware Drivers revealed that the system was NOT using my ATI proprietary Driver for my ATI Radeon 4850 Card (FGLRX); which was OK in previous Ubuntu build.
- 9.10 would not let me re-enable that video driver (FGLRX) in either Hardware Drivers or Synaptic Package Manager (even though it was present).
- I thought I could force the system to use the FGLRX driver so I removed the OS ATI video driver from Package Manager and rebooted.
- Still no Fix!
- Also discovered that the Screensaver functionality was totally inoperative!
- OK; at this point I gave up because I didn't want to devote the time required to fix this problem.  
- I reinstalled 9.04 (via Disaster Recovery Imaging Software)


There was NOT much online about my upgrade problem; except I did find this very interesting and made me feel that I may not be alone:

------------------------------------------------------------------------------------------------------------
[http://www.theregister.co.uk/2009/11...a_frustration/]("http://www.theregister.co.uk/2009/11/03/karmic_koala_frustration/")

Early adopters bloodied by Ubuntu's Karmic Koala

Ubuntu 9.10 is causing outrage and frustration, with early adopters wishing they'd stuck with previous versions of the Linux distro.

Blank and flickering screens, failure to recognize hard drives, defaulting to the old 2.6.28 Linux kernel, and failure to get encryption running are taking their toll, as early adopters turn to the web for answers and log fresh bug reports in Ubuntu forums.

The problems causing the biggest headaches are in graphics, with reports of flickering or dead screens. Adopters have re-downloaded and re-installed Ubuntu 9.10, and people have scoured the web for answers only to hit the same issues.

A bug has now being filed in Ubuntu forums on how Ubuntu 9.10 breaks graphics drivers and X, preventing log in or startx.

A conflict with graphics cards from Nvidia and ATI seems to be the issue, but there's no answer "why" or obvious fix.
--------------------------------------------------------------------------------------------------------------------------

My Plan:

- I'll wait a few weeks and attempt the Upgrade again
- Maybe I'll remove the ATI FGLRX Driver (use the OS version) before the Upgrade and then re-install it once the upgrade is complete. Good idea????

Any ADVICE / HELP Appreciated !!!!!!!!!

BVR
Johnny M!


PS: I also thought about a Clean Install of 9.10; but since I'm using GRUB to dual-boot, I'm afraid that Windows would be lost to the Master Boot Record (MBR); since the MBR points to GRUB (not Windows System partition root files: ntldr & Boot.ini) and I would wonder around in the wilderness of non-funtional computer.

C-Ya Later
):P
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=8260248") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=8260248")

---

