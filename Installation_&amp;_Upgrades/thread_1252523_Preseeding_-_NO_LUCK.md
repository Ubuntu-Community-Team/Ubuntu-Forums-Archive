---
title: "Preseeding - NO LUCK"
date: 2009-08-28
forum: Installation &amp; Upgrades
---

### Post by relay23 on 2009-08-28
Greetings, I hope someone is feeling like a good samaritan because here's your opportunity to free someone from the depths of hell. 

This is a preseeding question very similar to [http://ubuntuforums.org/showthread.php?t=1128753](http://ubuntuforums.org/showthread.php?t=1128753)
---Considering that question didn't ever get answered I don't think i'll have much luck but it's worth a shot

I have been trying for months now to get preseeding working and am finally at a point where I have exhausted all of the threads available. What I am doing should be very simple and I don't know why everyone can do it so easily.

The goal is mundane- to customize my installation so that the questions for language, keyboard type, time zone, user account setup, default apps, partition style, etc etc are all applied without user intervention. I have tried the most simple preseed value of just setting the time zone: "d-i time/zone string US/Central" and it still comes up as US/Eastern every time. The partitioning options also do not have any effect, the gui installer prompts for what to do about /dev/sda (which is unformatted).

Here's what I've done:
1. download latest jaunty installer iso, mount it and rsync to another folder
2. Edited isolinux/text.cfg to use a new filename 'xyz.seed'. I have used many different options in append but right now I am using the most simplistic version : 
"append file=/cdrom/preseed/xyz.seed DEBCONF_DEBUG=5 boot=casper initrd=/casper/initrd.gz quiet splash --"
(I have also tried adding the locale options to ensure it loads that stuff first)
3. Created xyz.seed with minimal options (as aformentioned)
4. I have even captured the md5 and put in md5sum.txt like how ubuntu.seed is referenced and that doesn't work either. Once i start making changes I just delete the line in md5sum.txt to make sure it's not going to refuse it for a wrong entry match. Currently it is removed.
5. I then roll up the cd into the ISO. 

I am booting it in Virtualbox, boots just fine. I can see any little simple modifications inserted in the boot options from text.cfg.I know after going to the desktop, after quitting out of the installer, and looking at /var/log/syslog and /var/log/casper.log that it is loading the right preseed file, and there are no errors present.

I am just completely stumped.. I have never actually seen it work so I don't know how it should even be behaving, but I would assume there should be SOME effect. 

Please be the one to tell me I am doing something stupid and what the thing I'm forgetting is, I would be forever grateful.

Thanks in advance
Chris

---

### Post by relay23 on 2009-09-04
Well, I am thinking that Ubiquity's gui installer interface is to blame. I will have to try this with the alternate CD to use the standard debian preseeding options. I will post back with the conclusion when i reach it.

---

### Post by relay23 on 2009-09-04
Got it, it was the ALTERNATE CD that was essential.. in the documentation it does say to go download the alternate cd but it doesn't say that's REQUIRED. Would have saved me a lot of time, but then again, i guess i am just an idiot for not following it to the tee.

---

