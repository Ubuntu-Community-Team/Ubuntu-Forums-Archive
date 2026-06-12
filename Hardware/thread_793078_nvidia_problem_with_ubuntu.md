---
title: "nvidia problem with ubuntu"
date: 2008-05-13
forum: Hardware
---

### Post by Alejandro Castanaza on 2008-05-13
Hi.
I have a problem with a HP Pavilion slimline 3320la, which has an nvidia geforce 7100/nforce 630.
I installed ubuntu 8.04 and it showed a horrible 800x600 screen resolution, no more, no graphics acceleration.
I managed to get a more decent resolution (with the gnome screen utility), 1280x1024 (this is the most I can get), but since my screen is widescreen, i want it to get the recommended resolution, 1680x1050, and graphics acceleration.
The restricted drivers dialog shows the nvidia restricted driver, enabled, but says "Not in use", with a red circle.
I found in the gnome screen settings it is used as a generic vesa card. I disabled, and then, reenabled the restricted nvidia driver, rebooted each time, but still it does not detect the nvidia card.
The lpsi | grep nvidia command shows many lines, so I understand the card it is detected as nvidia geforce 7100 but still does not work.
I even installed the nvidia 169.12 package (as described in ubuntu documentation, titled RestrictedDrivers/NVIDIAOfficial), it compiled nvidia modules, showed no errors, when rebooted still no display. (X tried 3 times to start, failed, and then ubuntu showed a 'low resolution' message), it reverts to the generic vesa display and 800x600 resolution.

This is my one complain with ubuntu, since everything else seems to work perfectly.

Please help.

---

### Post by ubuntu-freak on 2008-05-13
> **Alejandro Castanaza said:**
> Hi.
I have a problem with a HP Pavilion slimline 3320la, which has an nvidia geforce 7100/nforce 630.
I installed ubuntu 8.04 and it showed a horrible 800x600 screen resolution, no more, no graphics acceleration.
I managed to get a more decent resolution (with the gnome screen utility), 1280x1024 (this is the most I can get), but since my screen is widescreen, i want it to get the recommended resolution, 1680x1050, and graphics acceleration.
The restricted drivers dialog shows the nvidia restricted driver, enabled, but says "Not in use", with a red circle.
I found in the gnome screen settings it is used as a generic vesa card. I disabled, and then, reenabled the restricted nvidia driver, rebooted each time, but still it does not detect the nvidia card.
The lpsi | grep nvidia command shows many lines, so I understand the card it is detected as nvidia geforce 7100 but still does not work.
I even installed the nvidia 169.12 package (as described in ubuntu documentation, titled RestrictedDrivers/NVIDIAOfficial), it compiled nvidia modules, showed no errors, when rebooted still no display. (X tried 3 times to start, failed, and then ubuntu showed a 'low resolution' message), it reverts to the generic vesa display and 800x600 resolution.

This is my one complain with ubuntu, since everything else seems to work perfectly.

Please help.

 
Have you tried Envy? Disable the driver in System > Administration > Hardware Drivers and follow the instructions [here](http://albertomilone.com/nvidia_scripts1.html). 
 
If you have problems with Envy which can't be resolved, remove it with:
 
**sudo envyng --uninstall-all**
 
If your resolution is still incorrect after using Envy, press Alt F2, type "gksudo displayconfig-gtk" and your password when prompted, then choose the correct resolution.
 
Nathan

---

### Post by Alejandro Castanaza on 2008-05-13
Thank you, but I have read in other threads in this forum that using Envy is not supported by ubuntu.
Is there something else I should do or look for before trying Envy?

---

### Post by ubuntu-freak on 2008-05-13
> **Alejandro Castanaza said:**
> Thank you, but I have read in other threads in this forum that using Envy is not supported by ubuntu.
Is there something else I should do or look for before trying Envy?

 
That doesn't matter. Envy is in the repos now anyway. Also, the codecs you install from Medibuntu to play audio/video aren't supported by Ubuntu, nor Adobe Flash etc.
 
Give it a try, just write down that uninstall command I gave you (if you uninstall in recovery mode, forget the "sudo" part).
 
Nathan

---

### Post by Alejandro Castanaza on 2008-05-14
Thank you Nathan.
Last night I tried other solutions, and finally it works! without Envy.
As I posted before, I even installed the nvidia 169.12 package, and it compiled the modules without errors.
So, i looked at this post [http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)
and disabled the nv and nvidia_new modules in the /etc/default/linux-restricted-modules-common file.
Then, i ran the nvidia-xconfig and rebooted... finally it displayed nice graphics and I even could enable the desktop effects, I saw that the nvidia-settings utility even recognized correctly my monitor, etc.
One thing I noticed is that the nvidia logo is not shown before the login screen as I read it would happen, but everything seems to me that the driver working now is the one I installed from nvidia.

Before this, I even tried to "sudo apt-get install nvidia-glx" but that did't work, which makes me think that maybe I needed an internet connection (which currently i don't have) in order to download the required 'restricted' drivers from ubuntu to make the graphics card work.

Well anyway, it works now so thank you for your help, and maybe this helps others having similar issues.

---

### Post by Alejandro Castanaza on 2008-05-14
> **Alejandro Castanaza said:**
> 
Before this, I even tried to "sudo apt-get install nvidia-glx" but that did't work, which makes me think that maybe I needed an internet connection (which currently i don't have) in order to download the required 'restricted' drivers from ubuntu to make the graphics card work.


This makes me think, if my system is running with the installer that i downloaded from nvidia instead of the debian package ubuntu provides, will that be a problem when i have an internet connection (which i will, soon, since its my home computer), and try to upgrade the system?
I have just looked at the packages.ubuntu.com and found the nvidia-glx-new package and it is the same version I installed from nvidia, only better managed by the system with deb packages.

---

### Post by ubuntu-freak on 2008-05-14
Yes, it's better to let Ubuntu handle it, as a kernel upgrade will cause you problems if you're using the driver from the NVIDIA site.
 
Also, perhaps you should report/confirm a bug on Launchpad and tell them how you worked around it.
 
Nathan

---

### Post by Alejandro Castanaza on 2008-05-14
Thank you.
I would like to.
Where should i confirm?
What is launchpad? (sorry, I'm new here)

---

### Post by sideburns on 2008-05-14
I'm doing tech support for my sister's Ubuntu box.  We tried Envy, but still can't get above 800x600.  We tried displayconfig-gtk like reassuringlyoffensive suggested, but nothing.  I'd rather not go digging into config files unless I really have to, as it's not my machine.  Any more suggestions?

---

### Post by ubuntu-freak on 2008-05-14
> **sideburns said:**
> I'm doing tech support for my sister's Ubuntu box.  We tried Envy, but still can't get above 800x600.  We tried displayconfig-gtk like reassuringlyoffensive suggested, but nothing.  I'd rather not go digging into config files unless I really have to, as it's not my machine.  Any more suggestions?

 
Strange. Did you try selecting different monitor types with displayconfig-gtk, and not just the resolution? 
 
Also, try Alt F2 and type "gksudo nvidia-settings". Lots of options in there.
 
Nathan

---

### Post by ubuntu-freak on 2008-05-14
> **Alejandro Castanaza said:**
> Thank you.
I would like to.
Where should i confirm?
What is launchpad? (sorry, I'm new here)
 

Looks like you were right to install the driver from nvidia.com. There is an issue with the Ubuntu packaged version and Xorg 7.3, I found the bug report for you: 
 
[https://bugs.launchpad.net/ubuntu/+bug/222407](https://bugs.launchpad.net/ubuntu/+bug/222407)
 
You can add your comments there if you want, but they already mention the workaround.
 
Nathan

---

### Post by sideburns on 2008-05-14
I tried nvidia-settings and it complained that I wasn't using the right driver and should use nvidia-xconfig.  That, of course, wasn't installed.  Alas, it didn't help.  I know she has an nVidia Geoforce card, but without cracking the case, I can't tell just which one, and itt won't auto-detect.  It woks fine in Win2K, and I don't want to have to ask her to replace a working card as money is tight.  Any other ideas.

---

### Post by ubuntu-freak on 2008-05-14
> **sideburns said:**
> I tried nvidia-settings and it complained that I wasn't using the right driver and should use nvidia-xconfig.  That, of course, wasn't installed.  Alas, it didn't help.  I know she has an nVidia Geoforce card, but without cracking the case, I can't tell just which one, and itt won't auto-detect.  It woks fine in Win2K, and I don't want to have to ask her to replace a working card as money is tight.  Any other ideas.

 
You haven't got the proprietary driver installed? Didn't Ubuntu offer to install it? Check System > Administration > Hardware Drivers. If that doesn't work, try Envy, as mentioned on the previous page.
 
Nathan

---

### Post by sideburns on 2008-05-14
Ubuntu claimed to have installed it the first time we booted after installing it.  Until now, I thought we had it.  As far as Envy, we've already used it.  Weird!

---

### Post by ubuntu-freak on 2008-05-14
> **sideburns said:**
> Ubuntu claimed to have installed it the first time we booted after installing it.  Until now, I thought we had it.  As far as Envy, we've already used it.  Weird!

 
Used Envy when? You can't use both methods at one time. In Gutsy, enabling effects in System > Preferences > Appearance > Effects, seemed to help the Ubuntu method stick for me.
 
Nathan

---

### Post by sideburns on 2008-05-14
Just today.  When we installed, before the newest version came out, it claimed ot install the proper drivers.  It wasn't until we learned that we can't get above 800x600 that we realized that all was not well and started looking.  I found the post about Envy and tried it, but we still don't seem to have the right drivers.

---

### Post by ubuntu-freak on 2008-05-15
> **sideburns said:**
> Just today.  When we installed, before the newest version came out, it claimed ot install the proper drivers.  It wasn't until we learned that we can't get above 800x600 that we realized that all was not well and started looking.  I found the post about Envy and tried it, but we still don't seem to have the right drivers.

 
Hmm I don't know. So you haven't had success even with Envy? Newest version of what? Not sure what you meant there.
 
Is this your first experience with Ubuntu? If so, I think it would make more sense to install Gutsy, the previous version of Ubuntu. You can try Hardy again when they release 8.04.1 on July 3rd, with bug fixes and a better driver from NVIDIA. I just don't want you getting headaches by using the driver from nvidia.com and trying to install it yourself, disabling modules etc.
 
[http://releases.ubuntu.com/7.10/](http://releases.ubuntu.com/7.10/)
 
Nathan

---

### Post by sideburns on 2008-05-15
I've been using Fedora for years, and RedHat before Fedora started up.  Ubuntu is for my sister's box, as she's not a computer geek.  We installed Gutsy, and it said it installed the proper proprietary drivers for the nVidia card.  About the only problem we had was that the setup screens for Evolution were too big for her monitor.  Then, when Hardy came out, we let it upgrade.  We were trying with Evolution again and I found that the screen was set to a low resolution and couldn't be adjusted, so I looked here.  I tried Envy today to see if it would help, but no.  I see no reason to downgrade her system, especially when you consider that the problem was already there before Hardy came out.  Any more ideas, or will I have to crack her case, take out the card and post here exactly what it is?

---

### Post by ubuntu-freak on 2008-05-15
> **sideburns said:**
> I've been using Fedora for years, and RedHat before Fedora started up.  Ubuntu is for my sister's box, as she's not a computer geek.  We installed Gutsy, and it said it installed the proper proprietary drivers for the nVidia card.  About the only problem we had was that the setup screens for Evolution were too big for her monitor.  Then, when Hardy came out, we let it upgrade.  We were trying with Evolution again and I found that the screen was set to a low resolution and couldn't be adjusted, so I looked here.  I tried Envy today to see if it would help, but no.  I see no reason to downgrade her system, especially when you consider that the problem was already there before Hardy came out.  Any more ideas, or will I have to crack her case, take out the card and post here exactly what it is?

 
Have you tried the workaround mentioned by the OP? I can't understand why it didn't even work in Gutsy either. In Gutsy, I used "sudo dpkg-reconfigure -phigh xserver-xorg" to correct my resolution, but that's not supported in Hardy. Did you try that in Gutsy?
 
The card details can be discovered with the "sudo lspci" command, by the way. 
 
Nathan

---

### Post by Alejandro Castanaza on 2008-05-15
(For what I went thru, I would suggest first, if you have an internet connection, then let ubuntu upgrade, if not, go to packages.ubuntu.com and find the nvidia-glx restricted drivers, download them, and install them. But you have to enable them in the 'restricted drivers manager' (i can't remember the exact name, mine is in Spanish), in the System menu.
If that does not work, then you will have to dig into some config files. The good is that if that x doesn't start, you can always go to a tty and edit the files again.)

Sorry, i din't see the previous posts. Yes as Nathan said, you can view the exact details of the card with the **lspci |grep nvidia** command. There should be one line with something like "VGA compatible controller: NVidia ..." etc etc. It is there where you can see how it is being detected.

---

### Post by Alejandro Castanaza on 2008-05-15
> **reassuringlyoffensive said:**
> Looks like you were right to install the driver from nvidia.com. There is an issue with the Ubuntu packaged version and Xorg 7.3, I found the bug report for you: 
 
[https://bugs.launchpad.net/ubuntu/+bug/222407](https://bugs.launchpad.net/ubuntu/+bug/222407)
 
You can add your comments there if you want, but they already mention the workaround.
 
Nathan

thank you, I have just posted 'my experience' with this bug. :)

---

### Post by ubuntu-freak on 2008-05-15
> **Alejandro Castanaza said:**
> thank you, I have just posted 'my experience' with this bug. :)

If you or sideburns disabled "nv" and "nvidia_new" in /etc/default/linux-restricted-modules-common, by opening it within the Terminal:

**gksudo gedit /etc/default/linux-restricted-modules-common**

Then disabling the drivers like so:

**DISABLED_MODULES="nv nvidia_new"**

Well, wouldn't that enable Envy to work? Cos, "nvidia_new" is just Ubuntu's packaged driver, not Envy's, and "nv" is the open source unaccelerated driver. It's much simpler to use Envy, rather than download the drivers from NVIDIA.com. Envy will cope with kernel updates and even system updates now.

I may be wrong. Just can't see how doing the above can enable the driver from NVIDIA.com to work, but not when using Envy.

Nathan

---

### Post by sideburns on 2008-05-15
> **Alejandro Castanaza said:**
> (For what I went thru, I would suggest first, if you have an internet connection, then let ubuntu upgrade,

It upgraded about a day or two after Hardy came out, but before we'd realized what the trouble is.  Checking, lspci shows she has a GeForce Ti Rev 2 card, not listed in the known cards and the Proprietary Drivers (restricted) option is checked.

---

### Post by sideburns on 2008-05-15
I've gone to the nVidia site and found the specific drivers.  Will install them on her box and report back...

---

### Post by Alejandro Castanaza on 2008-05-15
> **reassuringlyoffensive said:**
> If you or sideburns disabled "nv" and "nvidia_new" in /etc/default/linux-restricted-modules-common, by opening it within the Terminal:

**gksudo gedit /etc/default/linux-restricted-modules-common**

Then disabling the drivers like so:

**DISABLED_MODULES="nv nvidia_new"**

Well, wouldn't that enable Envy to work? Cos, "nvidia_new" is just Ubuntu's packaged driver, not Envy's, and "nv" is the open source unaccelerated driver. It's much simpler to use Envy, rather than download the drivers from NVIDIA.com. Envy will cope with kernel updates and even system updates now.

I may be wrong. Just can't see how doing the above can enable the driver from NVIDIA.com to work, but not when using Envy.

Nathan

Perhaps you are right, but in my case, since it is my first time I install Ubuntu (and I didn't expect it to fail for what I have read in the internet about this distribution), I went to Ubuntu's documentation and support, and the last thing I saw was envy, and not so good comments. I haven't tried it, so I can't say it is good or bad, or if works or not, but I thought, if the nvidia driver is the problem, the nvidia web site should have a driver for linux. That's what I tried, and finally it was fixed. My next move was going to be replace the installation with opensuse or fedora, and try if they worked. And now that is not necessary.

But don't think wrong please, i really appreciate your help.

---

### Post by Alejandro Castanaza on 2008-05-15
> **sideburns said:**
> I've gone to the nVidia site and found the specific drivers.  Will install them on her box and report back...

if you do, just make sure you read this guides first:
[https://help.ubuntu.com/community/RestrictedDrivers/NVIDIAOfficial?highlight=%28restricted%29](https://help.ubuntu.com/community/RestrictedDrivers/NVIDIAOfficial?highlight=%28restricted%29)
and
[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

those helped me with my problem.

Also if running sudo nvidia-settings complains that the nvidia driver is not enabled, run sudo nvidia-xconfig, restart x server (ctrl+alt+backspace) or reboot.

---

### Post by sideburns on 2008-05-15
I tried downloading and installing the drivers.  I got a lot of flack about it being supported by the Open Source nv driver and other complaints, then it refused to install while X was running.  I tried rebooting with init=3 added to the kernel line but that didn't give me enough of a system to install, and I can't force the system to change to text only while running.  I suspect that we'll just have to throw some more money at it.

Shame, really, as I'm sure the card was great when new.  The system was a gift, as a friend is trying to cut down on the number of unneeded computers he has and I know him well enough to say that he'd never use second-rate components, although, as he says, he does a lot of dumb stuff so that the rest of us don't have to.

Thanx to all of you for all of your help!

---

### Post by Alejandro Castanaza on 2008-05-15
> **sideburns said:**
> I tried downloading and installing the drivers.  I got a lot of flack about it being supported by the Open Source nv driver and other complaints, then it refused to install while X was running.  I tried rebooting with init=3 added to the kernel line but that didn't give me enough of a system to install, and I can't force the system to change to text only while running.  I suspect that we'll just have to throw some more money at it.

Shame, really, as I'm sure the card was great when new.  The system was a gift, as a friend is trying to cut down on the number of unneeded computers he has and I know him well enough to say that he'd never use second-rate components, although, as he says, he does a lot of dumb stuff so that the rest of us don't have to.

Thanx to all of you for all of your help!

Did you stop X before installing the drivers?
I did not have to change init or anything. Just stop gdm and execute the .run package downloaded from nvidia.

---

