---
title: "Problems with Restart/Suspend/Hibernation"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by jeremyk on 2007-04-22
Hi,

I installed a few days ago feisty on my laptop IBM T30. It is quite impressive. The system is working very well and my overall impression is very positive. However I have three problems:

1- When restarting the computer, login becomes so long that it is practically impossible. I have tried the following working (sudo update-rc.d -f networking remove) but it did not change anything. Then indeed of restart, I have to do shutdown. 


2- Suspend/Hibernation: After suspend or hibernation, the usb port seems to be dead... My external usb mouse  does not work anymore. Plug it out and then plug in again does not help.  Even restarting the X-server does not help. Only a pure shutdown can recover the usb functionality. 

Any workout would be great appreciated. Note that if I have to tweak the bios, please explain me what should be done. 

Thanks.

---

### Post by jeremyk on 2007-04-23
anyone?

---

### Post by computx on 2007-05-01
I have a thinkpad t23 and I too have no usb mouse after suspend.
I have tried modprobe -r uhci_hcd usbhid hid
then modprobe uhci_hcd usbhid hid after suspending which should reload the modules. usb still doesn't work. 
searching google mentions removing the uhci_hcd module before suspend will help. I plan on trying that.  Unfortunately this worked just fine in edgy so hopefully the fiesty dev's will get it fixed soon.

the built in trackpoint device continues working so that should get you through a reboot.

---

### Post by mperry on 2007-05-01
I have thinkpad t40, latest bios and other updates.  No suspend at all for me.  Well, what I mean is no resume so a suspend means the laptop is dead until I pull the battery and power cable and start all over.  Somehow, I don't remember it being this way on edgy.  I tried apm and acpi here to see if there was a difference and unfortunately both cause the laptop to enter some deep sleep with the green moon thing glowing brightly after each lid close or fn-f4 suspend.  On apm, not much is different unfortunately.  I'll have to check whether I have usb; but its gonna be awhile.  I wiped the drive out with feisty on it since it really was not doing me much good and it was irritating my spousal unit every day.

---

### Post by StoneDragon on 2007-05-02
Confirmed for T30 here. There must be a "suspend" configuration file, where the usb-modules are mentioned, but I did not find any yet. Anyone else?

---

### Post by ali4949 on 2007-05-02
same problem here on a T30.. usb ports are dead after suspend.. looking at some other threads, people have mentioned irq poll, noapic and pci=routeirq options but they dont seem to work. any one got a fix for this ???

---

### Post by celsdogg on 2007-05-02
i have a toshiba satellite A25-S279 and have the same problem. i can use and hotswap usb devices fine after a cold boot, but when coming out of hibernation, usb will not work at all.

it worked fine in edgy. . .

---

### Post by ali4949 on 2007-05-03
Hey all
Dont know how many of you are still having problems with this issue, but after lots of searching here is a somewhat detailed description of the issue and some work arounds.

The culprit is the uhci_hcd module which does not work right after a suspend to ram. There are some bugs filed at the launchpad for usb devices failing after suspend, and I guess the USB_SUSPEND is in experimental stage for the kernel. One of the work arounds some people have had success with is to remove the uhci_hcd module before suspend and then modprobe it after the resume. But that doesnt work for me. Interesting to note that if you close the lid on the laptop, it does go to sleep and wakes up with the usb port working.. the both the wireless card and the usb mouse does not  get powered down for the lid suspend.. so thats a work around for the time being until more relaible fox comes around. check out the thinkwiki site for this also.. if anyone has found any fixes please post on here. Also I am trying to understand how the whole suspend/ hibernate  process works on laptops under ubuntu and which scripts under etc/acpi get executed in the correct order.. maybe adding the " rmmod uhci_hcd" in one of those scripts and also adding "modprobe uhci_hcd" including all the dependant modules in a recursive manner might be the way to go but I need help in tying to figure it out so any comments / help will be greatly appreciated.

thanks

Dragon and computx you two seem to be on the right track from what I have seen so far on the web/google/forums.. so lets get a working solution for this problem

---

### Post by computx on 2007-05-05
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/99267](https://bugs.launchpad.net/bugs/99267) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have found no combination of unloading modules beforehand that will allow having usb after suspend. I tried a suspend2 patched kernel by adding this repository to my sources.lst.
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty suspend2
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty suspend2
That also did not help the problem, I now suspect the acpi package and am looking for an alternate one.

---

### Post by jeremyk on 2007-05-07
Thanks for this pointer to suspend2. It seems to be very interesting. 

Just two questions: 

1- Once the package installed, does a regular suspend or hibernation (with the gui) trigger the use of this script? Or is it necessary to do something else?

2- If it does not work, how do you come back to the initial configuration? Just desinstalling the package?

Thanks.

---

### Post by gorb on 2007-05-07
Hi all,

I have a related problem with suspend/hibernate: my machine is an Athlon AMD64 dual processor, which I am running as an htpc/multimedia box. Therefore I'd very much like to get at least suspend if not hibernate to work...

This is my problem: I can succesfully hibernate the machine the first time. However, during the hibernation process, some console messages relating to usb (they look like dmesgs) flash on the screen - unfortunately to fast to get a good idea of what they say. When I start the machine up again, it shows me a password prompt, and everything seems to work, except that my ir-receiver (usb) does not function anymore.
Also, after the first hibernation, I cannot get it to hibernate again.

Suspend does not function at all, I only get shoved back to a password prompt. The machine doesn't seem to sleep at all.

I have only begun to investigate this, but I'll post my findings here. Any help/suggestions from you would be appreciated!

On a side note, my laptop (a Fujitsu-Siemens Amilo) works brilliantly: screen down and she goes to sleep, works like a charm!
Cheers,
Chris

---

### Post by petersra on 2007-06-13
I have a thinkpad t23 system.  Upgraded to feisty in April.  Since then I have been fighting the suspend/resume problem.  Tried many things, got the network to work but USB still dead.  Tried a clean install of feisty but no help.  Since suspend/resume worked well edgy I can not understand how this regression slipped by.  I am very disappointed and have gone back to edgy.  

You know, I have been trying Linux for 6 months now.   I am moderately technical.  However, the frustration over this issue makes me think that WINXP may be my only option.  I see all the glowing news on how Linux is ready for prime time.  However, based upon my experience, it's got a ways to go.  :(

---

### Post by amac777 on 2007-06-13
Found this solution and it fixed both suspend and hibernate on my computer: (albeit a desktop with ASUS motherboard)

Switch to uswsusp:
sudo apt-get install uswsusp
sudo dpkg-divert --rename --divert /usr/sbin/pmi-disabled /usr/sbin/pmi

if you want to go back to old suspend / hibernate:
sudo dpkg-divert --rename --remove /usr/sbin/pmi


More information is here:

[http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/)

---

### Post by vanadium on 2007-06-13
I confirm this "regression": with Edgy, my Dell Latitude D800 would hibernate without a problem. With Feisty, I get the behaviour you describe and it sometimes doesn work. Sleep works very well, so well that it can get out of sleep anymore: I have to press the on/off button for some time before the computer would reboot.

Looks like a nice fix but I am a bit scared trying it.

---

### Post by ym4546 on 2007-06-13
> **amac777 said:**
> Found this solution and it fixed both suspend and hibernate on my computer: (albeit a desktop with ASUS motherboard)

Switch to uswsusp:
sudo apt-get install uswsusp
sudo dpkg-divert --rename --divert /usr/sbin/pmi-disabled /usr/sbin/pmi

if you want to go back to old suspend / hibernate:
sudo dpkg-divert --rename --remove /usr/sbin/pmi


More information is here:

[http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/)
I'm having a similar problem on a Dell Dimension 8200 desktop.

Is it safe for me to try that fix?

---

### Post by vanadium on 2007-06-13
I couldn't resist trying it. Yep! It seems to do the trick on my Dell Latitude D800!

As the blog says, you can just try it first after installing the uswsusp package

```

sudo s2disk

```

There is indeed a little issue with network manager, though. I need to change the network configuration, then change back before the network is active again (I am currently using a manual configuration with fixed IP address).

---

### Post by ym4546 on 2007-06-13
i tried the sudo s2disk command, and as expected, the computer hibernated after some text about saving pages and such.

However, when i pressed the power button, it went through grub and then i got a blank screen.

Same problem as before. Could it be a bios issue? (I'm pretty scared of upgrading my bios, but I guess i would do it if I had to)

---

### Post by computx on 2007-06-13
For me the fix was to go back to edgy. I have waited for 2 months for a fix to come via software updates, This week I decided there were relly very few advantages to fiesty for me and the suspend problem was a big disadvantage so back to edgy for me. 
I still haven't given up on linux or ubuntu, but it does seem like a major problem after edgy and dapper worked so well. I will give the new  ubuntu release a chance when it gets here.

---

### Post by Talon2 on 2007-06-15
What is frustrating to me is that I can find no work arounds and I can't see where this issue is getting any attention.  If you search launchpad you see that most related bugs are either rated as low priority or haven't been rated yet.

I'd really like to know what the problem is... is this an upstream issue or just an Ubuntu issue?

Running a T23 with Win2000 here.  I can't run Fiesty will the terrible power management it has.

---

### Post by rabideau on 2007-06-15
Here's how I fixed things... my problems were on one of the new **Ubuntu-Dell e1505n** machines.

My machine is running with the **nVidia card, Beryl, and wxga+** resolution.

I fixed the suspend hibernate by doing the following:[LIST=1]
[*]Went to: Applications>>System Tools>>Sysinfo
[*]Opened Sysinfo and accessed nVidia driver info
[*]XServer XVideo settings: set both Sync to VBlank boxes to "BLANK"
[*]Opened Beryl Settings Manager General Options (go to the bottom of the page) and set Sync to VBlank to blank[/LIST]With those setting my suspend and hibernate work.

I hope this helps

---

### Post by petersra on 2007-06-19
Guys,

I spent 2 months trying to fix my feisty suspend/resume problem.  My T23 would get locked KDE locked screen.  Looked over all the posts but little help.  With some work got the screen unfrozen but USB dead and no network.   Fixed the network problem but hit the wall on USB.  As a last resort did a clean install with Feisty, but still no help.  I have given up  and went back to Edgy where suspend works as expected.   Will wait for the fall release and see if this problem is fixed.

Oh by the way, tried to build .21 kernel but that failed as well, probably I did something stupid.:(

---

### Post by ukripper on 2007-06-20
Have developers changed something in feisty in regards to SUSPEND/Hibernate as i have few mates who are having similiar problem and ae not getting any work around it so I suggested them to use Edgy as I have Edgy installed on my desktops and laptop except 1 laptop which is running  feisty and having same problems.

---

### Post by Talon2 on 2007-06-20
> **ukripper said:**
> Have developers changed something in feisty in regards to SUSPEND/Hibernate as i have few mates who are having similiar problem and ae not getting any work around it so I suggested them to use Edgy as I have Edgy installed on my desktops and laptop except 1 laptop which is running  feisty and having same problems.

One big thing that changed is that the Swap file is broken in a lot of systems.  Hibernate can't work without a swap file.

You can find more information by looking at this bug:

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/105490](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/105490)

Here is the fix I use:

Problem:  The Swap partition is assigned a different UUID on each reboot.  This kills Swap capability and hibernate capability.


Fiesty and Gutsy Swap/hibernate fix:

- Check swap:                       $ free | grep Swap

  If you see the follow then your Swap file is broken:

  Swap:            0          0          0


- Find the device name of swap:     $ sudo fdisk -l

  UUID support appears to be broken as far as the Swap is concerned.


- Edit swap line in fstab with correct non-UUID information:     $ sudo gedit /etc/fstab

  Example:  /dev/sda6       none            swap    sw              0       0


- Edit resume with correct non-UUID information:    $ sudo gedit /etc/initramfs-tools/conf.d/resume

  Example: RESUME=/dev/sda6


- sudo update-initramfs -u


- Reboot


- Check swap if you want:                       $ free | grep Swap


- Open some apps


- Test hibernate

---

I'd like to hear from others that find their swap file is dead.

Please note that the bug is listed as a MEDIUM priority.  I don't understand this because this one bug can cause all sorts of problems.  I think the bug should have a SHOWSTOPPER priority.

---

### Post by ukripper on 2007-06-20
> **Talon2 said:**
> One big thing that changed is that the Swap file is broken in a lot of systems.  Hibernate can't work without a swap file.

You can find more information by looking at this bug:

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/105490](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/105490)

Here is the fix I use:

Problem:  The Swap partition is assigned a different UUID on each reboot.  This kills Swap capability and hibernate capability.


Fiesty and Gutsy Swap/hibernate fix:

- Check swap:                       $ free | grep Swap

  If you see the follow then your Swap file is broken:

  Swap:            0          0          0


- Find the device name of swap:     $ sudo fdisk -l

  UUID support appears to be broken as far as the Swap is concerned.


- Edit swap line in fstab with correct non-UUID information:     $ sudo gedit /etc/fstab

  Example:  /dev/sda6       none            swap    sw              0       0


- Edit resume with correct non-UUID information:    $ sudo gedit /etc/initramfs-tools/conf.d/resume

  Example: RESUME=/dev/sda6


- sudo update-initramfs -u


- Reboot


- Check swap if you want:                       $ free | grep Swap


- Open some apps


- Test hibernate

---

I'd like to hear from others that find their swap file is dead.

Please note that the bug is listed as a MEDIUM priority.  I don't understand this because this one bug can cause all sorts of problems.  I think the bug should have a SHOWSTOPPER priority.

i think that explains it all as I have manually mounted my swap in fstab and also assigned uuid manually infront of swap after getting the correct uuid using following command:
```
ls -al /dev/disk/by-uuid
``` This command gives you all uuid assigned to your partitions. If partition has different uuid than in your fstab then you have to manually assign that uuid listed by the above command

---

### Post by geraschenko on 2007-06-28
> **Talon2 said:**
> 
Here is the fix I use:

Problem:  The Swap partition is assigned a different UUID on each reboot.  This kills Swap capability and hibernate capability.

...

I have this problem as well. I tried your fix, and here are the results.

(1) my swap file is not disappearing anymore, which is good.

(2) when I try to hibernate, it looks like my machine "tries" to hibernate, but doesn't. That is, all my windows disappear for a moment, but then come back. Before the fix, the machine would shut down, but not resume properly.

(3) when I try to hibernate using "sudo s2disk" (after installing uswsusp), I get stuck at a black screen with the text "suspend: Snapshotting System" or something like that, and I have to hard boot. Before the fix, the machine would shut down, but not resume properly.

As for suspend, it looks like the system suspends correctly, but it can't resume (I get stuck at a black screen and can't do anything, as far as I can tell).

---

### Post by climatewarrior on 2007-06-30
I had this problem and it was immediately solved when I got drivers for my video card from synaptic package manager. Before getting this driver my computer would go to suspend and never come back. The only thing that appeared when coming back from suspend was a weird blank screen. have a dell latitude X300 with a Intel Integrated Graphics Card 82852/855 GM. By the way Ubuntu Feisty has provided great support out of the box for most of the hardware in this laptop. Even the wireless card had support out of the box the only thing I had to get was the firmware.

---

### Post by ym4546 on 2007-06-30
> **climatewarrior said:**
> I had this problem and it was immediately solved when I got drivers for my video card from synaptic package manager. Before getting this driver my computer would go to suspend and never come back. The only thing that appeared when coming back from suspend was a weird blank screen. have a dell latitude X300 with a Intel Integrated Graphics Card 82852/855 GM. By the way Ubuntu Feisty has provided great support out of the box for most of the hardware in this laptop. Even the wireless card had support out of the box the only thing I had to get was the firmware.
thats interesting because I'm having the same problem you were having. I have an nVidia card with the proprietary drivers installed (i got them directly from nvidia's website)... that seems to suggest the suspend/hibernate is a video card problem and perhaps not a bios problem.

---

### Post by amac777 on 2007-07-20
For those of you who are getting a blank screen upon resume (either after suspend or hibernate), *and* who are using nvidia drivers, be aware that nvidia needs the following NvAgp option to be set to a 1 in xorg.conf in order to successfully resume.

Type sudo nano /etc/X11/xorg.conf and confirm the driver section is 'nvidia' and make sure to add the line in the nvidia section:


```
Section "Device"
        ...
        Option          "NvAGP"       "1"
EndSection
```

More information about suspend with Nvidia drivers is here:
[https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)

---

### Post by StoneDragon on 2007-07-20
Thanks, I'll check on my dell notebook (where the return from suspend is working), if it is set.
On my old thinkpad, it's an ati internal card (urks...), and there I had the problems...

---

### Post by rogun on 2007-07-27
> **Talon2 said:**
> What is frustrating to me is that I can find no work arounds and I can't see where this issue is getting any attention.  If you search launchpad you see that most related bugs are either rated as low priority or haven't been rated yet.

I'd really like to know what the problem is... is this an upstream issue or just an Ubuntu issue?

Running a T23 with Win2000 here.  I can't run Fiesty will the terrible power management it has.


While I can understand both sides, I have to agree that this needs more attention: not just from Ubuntu developers, but from the linux community in general, mind you.  Because while we tout ourselves as being more humanitarian then those who use other operating systems, we're apparently not willing to do what it takes to utilize the energy saving tools available to us.  This is a big deal, because as we're all too aware, people are dying every day in wars for energy and our supply certainly isn't infinite.

I'm tired of hearing linux desktop users brag about how long their computers have been running without a reboot, as if that's an admirable thing for a desktop user to do (I hope it's worth the increase in electrical and cooling bills for them.)  If we were responsible, we would tout how much energy we're saving by running linux, rather then how much we're wasting by leaving our computers running for months on end.

This is one important area where microsoft leads linux, much to my dismay.  I can only hope that our community will wake up and recognize the seriousness of this problem and give it the attention it needs to lend credibility to the claim that we're more humanitarian and environmentally aware then microsoft users.

---

### Post by rogun on 2007-07-27
Btw, I came across this thread looking for a fix for my own problem with putting my machine to sleep (S3). I should probably include my own experience, so here goes:

I switched my desktop from XP to Feisty a few months ago.  I have a home-built computer with hardware that's compatible for suspending/hibernating and everything worked perfectly in XP. Neither suspend nor hibernate worked after switching to Feisty and this was a big problem for me, because I greatly value these features.

After spending several hours on getting them both to work, I was finally able to hibernate flawlessly, but not suspend/sleep/S3. I finally decided that S3 was never going to work with my video card, which was something I had worried about with it all along, because it's the only piece of older hardware I had and I didn't know if it was 100% compatible with ACPI (though it worked fine in Windows, I had to tweak a lot of things to do it.)

Because S3 is so important to me, I upgraded my video card to a Nvidia GForce 7600 GT. After installing the drivers and ensuring that everything was working, I tried to suspend and hibernate, but neither of them worked. This wasn't completely surprising, since I had installed Feisty with an ATI card and the power settings were still setup and tweaked for it. However, I was able to quickly fix it by changing this one line in /etc/default/acpi-support:

**FROM:**

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

**TO:**

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

I suspected this fix might work, because I knew from getting my ATI card to suspend in XP that it needed to be warm-booted, but suspected that my newer Nvidia card didn't. So far, everything seems to be working perfectly and I can now put my desktop to sleep (S3 mode) again. I'm not sure what the default settings are for this, because as I said, I had already tweaked it for my former ATI card before installing the Nvidia card, but it may be something to check for those having problems, which is why I'm posting it.

---

### Post by ym4546 on 2007-07-28
rogun's fix worked for me... at least on suspend. I have not tested it on hibernate yet, but since i have a desktop thats not particularly important for me.

thanks.

---

### Post by maestrobwh1 on 2007-07-31
What would the equivalent to this be in kubuntu (KDE).  I poked around in system settings, but didn't fine "System Tools" obviously.


> **rabideau said:**
> Here's how I fixed things... my problems were on one of the new **Ubuntu-Dell e1505n** machines.

My machine is running with the **nVidia card, Beryl, and wxga+** resolution.

I fixed the suspend hibernate by doing the following:[LIST=1]
[*]Went to: Applications>>System Tools>>Sysinfo
[*]Opened Sysinfo and accessed nVidia driver info
[*]XServer XVideo settings: set both Sync to VBlank boxes to "BLANK"
[*]Opened Beryl Settings Manager General Options (go to the bottom of the page) and set Sync to VBlank to blank[/LIST]With those setting my suspend and hibernate work.

I hope this helps

---

### Post by rabideau on 2007-07-31
I'm sorry I can't help you there... I don't use KDE.:confused:

---

### Post by earther on 2007-08-01
> **amac777 said:**
> For those of you who are getting a blank screen upon resume (either after suspend or hibernate), *and* who are using nvidia drivers, be aware that nvidia needs the following NvAgp option to be set to a 1 in xorg.conf in order to successfully resume.

Type sudo nano /etc/X11/xorg.conf and confirm the driver section is 'nvidia' and make sure to add the line in the nvidia section:


```
Section "Device"
        ...
        Option          "NvAGP"       "1"
EndSection
```

More information about suspend with Nvidia drivers is here:
[https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)
This is exactly the problem that I was having on my machine when I installed the nvidia driver to increase my screen resolution options.  I had to uninstall it because hibernation is non-negotiable.  Now it seems there is hope!!!  The link talks about a laptop but I'm assuming it will also work on a desktop?

---

### Post by ym4546 on 2007-08-02
I was using an AGP nvidia card with nvidia drivers and I didn't use that fix... I just turned off the warm booting and that seemed to do the trick as well.

---

### Post by selda on 2007-08-29
> **amac777 said:**
> For those of you who are getting a blank screen upon resume (either after suspend or hibernate), *and* who are using nvidia drivers, be aware that nvidia needs the following NvAgp option to be set to a 1 in xorg.conf in order to successfully resume.

Type sudo nano /etc/X11/xorg.conf and confirm the driver section is 'nvidia' and make sure to add the line in the nvidia section:


```
Section "Device"
        ...
        Option          "NvAGP"       "1"
EndSection
```

More information about suspend with Nvidia drivers is here:
[https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)

Great, this fixed the problem on my Dell xps 1210. Thanks a lot!

---

### Post by maestrobwh1 on 2007-08-30
Is there any references or documentation of something similar that needs to be added for ATi AGP?

I have put several posts up here and in kubuntu forums and I generally have not had too many responses.  I have tried many different things, but I am almost certain at this point that the computer itself wakes up, but the video card isn't woken/rebooted/restarted.

I am just trying to get suspend to work.  I don't really care about hibernation at this point although I have a swap-space slightly larger than my RAM.  I have 2 GB of physical ram so on on a linux distro, I should not even need a swap, but have it there in case I get this stuff to work.

I have had this problem since Dapper, and it is EXACTLY the same with Gutsy, and every release between them.

I have a Radon 7200 AGP with 64 MB ram

Suspends fine.
Waking --> screen flickers horizontal random bars for a few seconds and goes dark (but not off).  Jiggling the mouse or using the keyboard reproduces the effect.

BUT.. ctrl-alt-F1***** then ctrl-alt-del causes the computer to undergo shutdown activity, as hd light becomes very active, the screen goes completely black (off), bios comes up, and the reboot is normal, meaning that the shutdown process had happened as no disks/partitions flag being unmounted incorrectly.

*****ctrl-alt-bkspace does NOT give me a prompt

---

### Post by nelio2k on 2007-11-07
This method fixed my suspend problem. However, it makes my graphics card super slow that compiz is laggy. Is there anyone who have the same problem or have any fix for it?

Thanks

> **amac777 said:**
> For those of you who are getting a blank screen upon resume (either after suspend or hibernate), *and* who are using nvidia drivers, be aware that nvidia needs the following NvAgp option to be set to a 1 in xorg.conf in order to successfully resume.

Type sudo nano /etc/X11/xorg.conf and confirm the driver section is 'nvidia' and make sure to add the line in the nvidia section:


```
Section "Device"
        ...
        Option          "NvAGP"       "1"
EndSection
```

More information about suspend with Nvidia drivers is here:
[https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)

---

### Post by spectrevk on 2008-03-20
My video card is a Radeon XPress 200, built into my Compaq Presario V5000. I can't seem to get suspend or hibernate to work in Ubuntu no matter what I try. This is a pretty serious problem, because without it my battery life is much shorter.

---

