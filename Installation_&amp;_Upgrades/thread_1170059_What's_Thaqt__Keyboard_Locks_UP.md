---
title: "What's Thaqt?  Keyboard Locks UP?"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by oldefoxx on 2009-05-25
Okay, let's quickly review where I've gotten to.  I've a recent PC, now using Ubuntu 9.04 for host on three partitions, have VirtualBox 2.0.8 installed (more fitting for my situation as explained elsewhere), and Windows 2000 Pro with Office 2000 Pro installed as client.  Also have Nvidia 7100/6800 graphics on the motherboard, so now using the 180.51 deb from the [www.nvidia.com](www.nvidia.com) website.

Pretty good shape overall, but it took me a couple of months of long days to finally get to this point.  It does prove that it can be done.

But have a new though infrequent problem.  I could be typing for awhile, take a break, use the other PC for a bit, or be called to a task by my wife.  And sometimes, I would return to the client side and find that the mouse works fine, but the keyboard is locked up or being disabled.  So what gives?  I had to stop the client and kill the VirtualBox to recover, since they were both being effected.

Ubuntu won't take any responsibility for third party products like VirtualBox, so onece I Checked the VirtualBox web site, I found no bug reports involving the word keyboard.  So I tried to open a bug report.  Nope, not allowed.  I don't have TICKET_CREATE priveleges (I wonder who does?).

So i search around for some other way, and I read that I need to download and read some PDF document, sign it, and fax if off first.  Too much trouble.   Another suggestion is ust to email the developer's group amd say that I accept the MIT terms, which I understand just means I allow Sun to take my patch or whatever and use it as they want to.  Not really a problem, it's just an effort to report what seems like a bug.


So I write a fairly short email giving the particulars, described what seems to be happening, and send it off.  Awhile later I get a rejection from Sun which says I am not premitted to post messages to that email address.  That's not too pleasing in my eye, so I give up on them.  And I sit and have dinner, then go and get a shower.  I did think about appealing the refusal (they do supply a contact for doing that), but if they don't want bug reports from those of us out here, why should any of us bother?

That was the bad news.  The good news I my mind finally keyed in on the time lapse that seem to be followed by these apparent keyboard lockups.  What if the host system was just seeing the lack of keyboard activity as an indication that it should go into sleep mode?  I've got the client is full screen mode, and I cannot see what might be happening at the host level.  Is there a screen saver or blank screen coming into play at that level?  I could not say.

I did a bit of research about Ubuntu and words like sleep, hybernate, and so forth.  I don't see a separate setting anywhere for creating a sleep mode, so what was happening here?

One post gave me a bit of a clue.  Seems that if you did not want your laptop to automatically go into a powerdown or sleep mode, there was a certain setting you could employ when installing Ubuntu.  Now the way I read that, not making this choice before installing means that you leave powerdown enabled on the PC, even if it is not a laptop.  Something to know, right?

There are several posts regarding some things you can do from a command line prompt as super user, but it was unclear as to what would actually work, and whether it would become permanent or not.

Then it came to me that since Nvidia is all concerned about 
X server when you try to install its drivers, maybe i should look at the possible settings allowed by Nvidia's own display toolbox.  
So I went to System/Preferences/Display, and signalled that I wanted the Nvidia ToolBox, then examined some of the settings.  The last one on the left Nvidia-settings configuration, looked promising.  I clicked on that, and on the bottom right was a checkbox for PowerMizer Monitor, and the time allowed is 1000 ms.  I unchecked the box, did the sudo nvidia-settings, then followed that with sudo nvidia-xconfig.  That might have done it.

It could be awhile before I know one way or another if this takes care of the keyboard problem.  But it might also start helping others if they hit a similar snag, or they may find another way to get it right.  I would even think that the install process could be made more pertinant if it asked if you needed power management, as for a laptop or not, as for a desktop.   Could be helpful in my mind.

Well, I let the PC linger in client mode awhile, and the keyboard quit on me again.

So it has to be something else.  This time, under System/Preferences, I noted that there was a screensaver link near the bottom.  I went in there, slid the bar all the way to the right so that the system would only regard the PC as idle after 2 hours, and unchecked the box for enabling the screensaver if the PC is idle.  I didn't even have to kill the VirtualBox process this time, but just restarted the client and the keyboard works, which is a first.  So maybe this will help others as well.

---

### Post by chargersfan420 on 2009-06-01
I've got a similar problem.  When leaving Ubuntu 9.04 idle for a few minutes, or locking the workstation and then unlocking it, my keyboard does not work in Virtualbox.

As a temporary solution, i can move to a different desktop, press a few keys on the keyboard, and then return to virtualbox and all seems to be fine - until the next idle period.

I just switched to (Sun xVM - not OSE) Virtualbox 2.2.4, which came out two days ago.  The behavior has been persistent (and annoying) since 2.2.0.  The guest is XP Pro SP3.

I agree, there is no help already posted to a Vbox forum; I don't really want to sign up for an account there either.  I also read on some forum somewhere to install package "scim-bridge-client-qt", but this didn't seem to help.  Another suggested to disable "Use input method engines (IME) to enter complex characters" from the "System - Administration - Language Support" menu, but i found it already disabled.

IMHO, The best and most stable Vbox I've seen is 2.0.6 - beyond that, I haven't seen any noticeable improvements or useful features... I suppose a downgrade might help...

Anyone else have any suggestions?

---

### Post by tmarcou on 2009-06-05
TMarcou (Chicago, IL) - Same problem with the locking up of the keyboard (mouse continues to work ok) on ubuntu 9.04 ONLY.  Same level of virtual box (2.2.4 r47978) on two machines one running ubuntu 8.10 and the other running 9.04.  ubuntu 8.10 has no problem with VirtualBox, however the problem continues on ubuntu 9.04.

I would think that something on 9.04 is causing the problem as 8.10 is as stable as ever.  I will continue to reseach.

TM






> **oldefoxx said:**
> Okay, let's quickly review where I've gotten to.  I've a recent PC, now using Ubuntu 9.04 for host on three partitions, have VirtualBox 2.0.8 installed (more fitting for my situation as explained elsewhere), and Windows 2000 Pro with Office 2000 Pro installed as client.  Also have Nvidia 7100/6800 graphics on the motherboard, so now using the 180.51 deb from the [www.nvidia.com](www.nvidia.com) website.

Pretty good shape overall, but it took me a couple of months of long days to finally get to this point.  It does prove that it can be done.

But have a new though infrequent problem.  I could be typing for awhile, take a break, use the other PC for a bit, or be called to a task by my wife.  And sometimes, I would return to the client side and find that the mouse works fine, but the keyboard is locked up or being disabled.  So what gives?  I had to stop the client and kill the VirtualBox to recover, since they were both being effected.

Ubuntu won't take any responsibility for third party products like VirtualBox, so onece I Checked the VirtualBox web site, I found no bug reports involving the word keyboard.  So I tried to open a bug report.  Nope, not allowed.  I don't have TICKET_CREATE priveleges (I wonder who does?).

So i search around for some other way, and I read that I need to download and read some PDF document, sign it, and fax if off first.  Too much trouble.   Another suggestion is ust to email the developer's group amd say that I accept the MIT terms, which I understand just means I allow Sun to take my patch or whatever and use it as they want to.  Not really a problem, it's just an effort to report what seems like a bug.


So I write a fairly short email giving the particulars, described what seems to be happening, and send it off.  Awhile later I get a rejection from Sun which says I am not premitted to post messages to that email address.  That's not too pleasing in my eye, so I give up on them.  And I sit and have dinner, then go and get a shower.  I did think about appealing the refusal (they do supply a contact for doing that), but if they don't want bug reports from those of us out here, why should any of us bother?

That was the bad news.  The good news I my mind finally keyed in on the time lapse that seem to be followed by these apparent keyboard lockups.  What if the host system was just seeing the lack of keyboard activity as an indication that it should go into sleep mode?  I've got the client is full screen mode, and I cannot see what might be happening at the host level.  Is there a screen saver or blank screen coming into play at that level?  I could not say.

I did a bit of research about Ubuntu and words like sleep, hybernate, and so forth.  I don't see a separate setting anywhere for creating a sleep mode, so what was happening here?

One post gave me a bit of a clue.  Seems that if you did not want your laptop to automatically go into a powerdown or sleep mode, there was a certain setting you could employ when installing Ubuntu.  Now the way I read that, not making this choice before installing means that you leave powerdown enabled on the PC, even if it is not a laptop.  Something to know, right?

There are several posts regarding some things you can do from a command line prompt as super user, but it was unclear as to what would actually work, and whether it would become permanent or not.

Then it came to me that since Nvidia is all concerned about 
X server when you try to install its drivers, maybe i should look at the possible settings allowed by Nvidia's own display toolbox.  
So I went to System/Preferences/Display, and signalled that I wanted the Nvidia ToolBox, then examined some of the settings.  The last one on the left Nvidia-settings configuration, looked promising.  I clicked on that, and on the bottom right was a checkbox for PowerMizer Monitor, and the time allowed is 1000 ms.  I unchecked the box, did the sudo nvidia-settings, then followed that with sudo nvidia-xconfig.  That might have done it.

It could be awhile before I know one way or another if this takes care of the keyboard problem.  But it might also start helping others if they hit a similar snag, or they may find another way to get it right.  I would even think that the install process could be made more pertinant if it asked if you needed power management, as for a laptop or not, as for a desktop.   Could be helpful in my mind.

Well, I let the PC linger in client mode awhile, and the keyboard quit on me again.

So it has to be something else.  This time, under System/Preferences, I noted that there was a screensaver link near the bottom.  I went in there, slid the bar all the way to the right so that the system would only regard the PC as idle after 2 hours, and unchecked the box for enabling the screensaver if the PC is idle.  I didn't even have to kill the VirtualBox process this time, but just restarted the client and the keyboard works, which is a first.  So maybe this will help others as well.

---

### Post by tmarcou on 2009-06-12
> **tmarcou said:**
> TMarcou (Chicago, IL) - Same problem with the locking up of the keyboard (mouse continues to work ok) on ubuntu 9.04 ONLY.  Same level of virtual box (2.2.4 r47978) on two machines one running ubuntu 8.10 and the other running 9.04.  ubuntu 8.10 has no problem with VirtualBox, however the problem continues on ubuntu 9.04.

I would think that something on 9.04 is causing the problem as 8.10 is as stable as ever.  I will continue to reseach.

TM

Looking through a number of reports relating to this issue I came across one suggestion which unlocks the keyboard without having to restart the virtual client.  Pressing the "Print Screen" key wakes up the keyboard and you can continue working.  Not a fix but a quick workaround.

TM 6/12/09

---

### Post by oldefoxx on 2009-09-08
I've updated VirtualBox, and it now seems to offer its own solution.  If you go to full screen, there is a set of icons that show just marginally along the bottom center.  Move your mouse over this area, and some buttons expand upwards.  The leftmost symbol is a stick pin.  Use this if you want these to remain showing.  Then three named categories:  Machine, Devices, Clientname.  The fourth is most important, looking like a small window inside a large window.  Click on this, you go back from full screen, and you keyboard will likely be restored.  So that is some help anyway.

---

