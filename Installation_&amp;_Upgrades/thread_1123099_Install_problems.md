---
title: "Install problems"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by bewarellamas on 2009-04-11
I'm new to Linux and just installed Ubuntu 8.10. I have having some strange issues and I don't know what to make of them.
I went through the install process successfully and got to the log in screen and logged in. When I log in I get a tan screen that does nothing. As I said I am new and maybe this is what I should see, but I don't know what to do with it. I tried changing the session to GNOME and GNOME failsafe, but that gave the same result. Sometimes when using the default sessions (I can't remember that that was called) the screen would turn black and nothing would happen. In all instances the mouse cursor still moves, but when it turns black the cursor becomes the waiting icon and stays that way. Any advice would be appreciated

oh...
Desktop edition 8.10
768MB Ram
Intel Celeron processor
Trying to fire it up on an old intel machine to try it out.

---

### Post by abn91c on 2009-04-11
it may be the default desktop effects, try this ctr+alt+f1 to get tto a command prompt then type the following commands```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
sudo  reboot
``` it will ask you for your password, you will not get or see any ******* when you type it, that is a normal linux security feature. just type it and hit enter then type the above commands.

---

### Post by nstolar on 2009-04-12
> **bewarellamas said:**
> I'm new to Linux and just installed Ubuntu 8.10. I have having some strange issues and I don't know what to make of them.
I went through the install process successfully and got to the log in screen and logged in. When I log in I get a tan screen that does nothing. As I said I am new and maybe this is what I should see, but I don't know what to do with it. I tried changing the session to GNOME and GNOME failsafe, but that gave the same result. Sometimes when using the default sessions (I can't remember that that was called) the screen would turn black and nothing would happen. In all instances the mouse cursor still moves, but when it turns black the cursor becomes the waiting icon and stays that way. Any advice would be appreciated

oh...
Desktop edition 8.10
768MB Ram
Intel Celeron processor
Trying to fire it up on an old intel machine to try it out.

Hi, I had the same problem when I loaded to a server, I went thru the user name & pass.. then the tan or off color screen. I had two installs on the same hard-drive too. It did the same thing with both installs !
I am going to try the BIOS setup in the morning, There may be a problem there. Going to double check there and turn back the processor voltage a bit and double check the memory setting, although the memtest was fine. I will follow up in the AM. 

I am now using a Celeron 2.4 and 1Gig of RAM on an HP  P-4 Board The Server is a P-4 2.8Ghz 512Mb RAM That has the Off Color Screen 

Good Luck, nstolar

---

### Post by steffan on 2009-04-13
I had problems very similar to yours and got as far as entering user ID and password before ending up with the Tan Screen of Death (TSOD). Symptoms after that were identical.

But it took me some blood sweat and tears to get that far.

Machine is a Dell Optiplex SX260 with a 2.00GHx Pentium 4, 512K RAM and 40 GB HD. I downloaded the 8.10 desktop-i386.iso and it MD5 check summed OK. Burned it from my iMac and the first attempt ended with a 'bad disk' error so I cleaned the CD and the lens in the drive.

Seemed to go OK after that until I got the TSOD.

I wiped the existing XP partition and allowed the setup process to take the whole disk.

I tried the commands suggested above:-

[INDENT]ctr+alt+f1 to get to a command prompt[/INDENT]

but my Linux skills are basic (I stretch to being able to run the uptime command in a Mac OSX terminal) and I get thrown into a black screen with large white text that does nothing but sit there. Can't seem to execute any commands. Trying again ctr+alt+f1 does nothing now.

I even tried the alternative non-graphical ISO and this just comes up with the single option 'Rescue a broken system'. It doesn't seem to do anything because I can't select it :(

Anyone got any ideas?

Cheers

Steffan

---

### Post by bewarellamas on 2009-04-14
Figured it out. For some reason it worked when I started it in safe graphics mode. I put in the Ubuntu disk, let it boot to that menu, hit F4 and selected Safe Graphics Mode, and then booted from first hard drive.

After that the auto updates installed all my driver, rebooted and good to go.

Thanks for all the replys.

---

### Post by Agent.Logic_ on 2009-04-14
Yeah, blank/black/tan screens are more often than not graphics driver issues. I'm glad you didn't have to go through the trouble of experimenting with different video drivers, by apt-get installing them from CLI, and editing the xorg.conf file until you found a working one, like I had to with my laptop install! :D

---

### Post by steffan on 2009-04-14
> **bewarellamas said:**
> Figured it out. For some reason it worked when I started it in safe graphics mode. I put in the Ubuntu disk, let it boot to that menu, hit F4 and selected Safe Graphics Mode, and then booted from first hard drive.

After that the auto updates installed all my driver, rebooted and good to go.

Thanks for all the replys.

That worked for me too. Got the system up and running. Problem is it is limited to 640x480 screen resolution and there are no other selectable options.

Machine is a Dell Optiplex SX280 'small form factor PC' and appears to have an integrated Intel GMA 900 video card (according to net searching - how do I confirm this from within Ubuntu?)

I ran all the system updates, but that did not seem to fix it . Does anyone know how I would go about installing the applicable driver?

Cheers

Steffan

---

### Post by Agent.Logic_ on 2009-04-14
Intel shouldn't have much problems working with linux. Could you confirm what driver is in use by typing the following in the terminal?

```

nano /etc/X11/xorg.conf

```

Look for **Section "Device"** in the result and post it here. Or better yet, copy the entire result and post it here so we can all have a look. To exit the nano editor, press ctrl+x.

Note: I deliberately avoided the sudo prefix to prevent accidental modification to the configuration file.

---

### Post by steffan on 2009-04-15
I get a window that pops up with 'GNU nano 2.0.7' and then a flashing cursor. Other than that the window is empty except for some short cut key commands at the bottom.

I am guessing nano is an editor? If it is, it didn't find anything to edit :(

Thanks for your help - am willing to give anything a shot.

Cheers

Steffan

---

### Post by Agent.Logic_ on 2009-04-15
Yeah, nano is an editor. Weird that nothing shows up... try adding a 'sudo' in front of the command:
```

sudo nano /etc/X11/xorg.conf

```
It will ask for your password, enter it. Now you'll be able to view/edit it. Make sure you don't accidentally change anything. If something does accidentally happen, just hit ctrl+x and select 'No' when it prompts to save.

---

### Post by steffan on 2009-04-15
I'll give that a shot tonight.

Thanks

Steffan

---

### Post by steffan on 2009-04-15
Sudo did the trick...

here is the pasted section:-

[INDENT]Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"[/INDENT]

Looks pretty generic.

Should I be seeing names of devices and drivers other than e.g. vesa?

Thanks

Steffan

---

### Post by Agent.Logic_ on 2009-04-15
The vesa driver is a pretty basic driver, the one used for "safe" graphics so you don't get locked out when the graphics load. Have you installed the intel driver for linux? Go to the Synaptic Package Manager (System > Administration > Synaptic Package Manager), enter your password when it prompts, and search for **xserver-xorg-video-intel**. This is the driver you need to have installed for your chipset family. Once that is done, you'll need to edit your xorg.conf file. First, make a backup of your current xorg.conf file, like so:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```

If you should run into some trouble later regarding graphics, you can revert to this later from the recovery mode.

Now, onto editing the xorg.conf file. :D
```

sudo gedit /etc/X11/xorg.conf

```
That should bring up the graphical text editor with the xorg.conf settings. You need to change the **driver** entry from **[color=red]vesa[/color]** to **i915**. Save and reboot. Now you will be (hopefully) able to change the resolution after logging in from System > Preferences > Screen Resolution.

Good luck, hope this works for you!

----EDIT----
P.S. Should you run into some trouble, just boot into recovery mode (choose this from the GRUB menu on boot. Usually the second option). Once there, "drop to shell" if you are using Intrepid. Just copy over your backed up xorg.conf file like so:

```

cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

```

That would revert you to the old vesa settings so you can continue using the graphical mode to look for further solutions. Hopefully, it won't come to this! Cheers mate.

---

### Post by steffan on 2009-04-16
Hi,

as it happens I had already donwloaded the driver after doing some more research on the forums. It's pretty awkward doing anything in 640*480 as most dialogue boxes run off the bottom of the screen and I can't reach down low enough to grab a corner and shrink the window. I usually have to tab to what I think is the right 'yes' or 'no' box and hit enter.

The package now shows up with a green square next to it (on the left) which I assume means it is installed.

Anyway I backed up the xorg.conf file and edited it to replace 'vesa' with 'i915' and rebooted.

It ran into problems and I wrote down the error message but left it at home. Will post it tonight but it said something like 'driver not available'.

I will probably restore the original xorg.conf file and ponder my next course of action.

I get the sense that I am very close to solving this problem.

Thanks again for your continued support and attention.

Regards

Steffan :D

---

### Post by Agent.Logic_ on 2009-04-16
You are welcome, mate! :D It's what the community is all about. Haha, I know it is a pain in the rear working with 640x480 these days! I had a hard time setting up graphics to work properly on my laptop.

Regarding the issue, I saw in another post somewhere in another forum that using (oddly) "i810" as the driver will make it work ([link](http://www.unixresources.net/linux/lf/48/archive/00/00/16/06/160607.html)). I also saw someone in the openSUSE forums using "intel" as the driver for a chipset from a sub-family of 915G, but I forgot to save the link :(. Sorry I'm so trial-and-error like, I'm a beginner myself and yet to get a firm grasp on things.

---

### Post by steffan on 2009-04-16
OK - I am going back to the beginning

The Synaptics Package Manager says *xserver-xorg-video-intel* is installed (status = installed, with green square).

My xorg.conf file currently is as follows:-

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

When I have tried replacing "vesa" with either "i915" or "i810" it has failed.

I guess I am stuck again ](*,)

Steffan

---

### Post by Daisuke_Aramaki on 2009-04-16
i think it should be intel.and not i915. Try changing that into intel.

---

### Post by steffan on 2009-04-16
That's it!!!!!!

Problem solved.

I am now rocking and rolling in splendid 1024*768!

:grin:

Thanks Daisuke_Aramaki and Agent.Logic_ for making me a very happy person.

Steffan

---

### Post by Agent.Logic_ on 2009-04-16
Good to hear your problem has been solved! :D I came across quite a number of posts which used i810, i915 and intel as the drivers while looking for a solution. It had to be one of them. I understand it can be a pain in the rear when things don't work out-of-the-box, but configuring and reconfiguring to make things work is the real fun in linux, IMHO. :D

Cheers mate, have fun playing with compiz/beryl! ;)

---

### Post by steffan on 2009-04-17
Hi Guys,

just writing in to report that whilst I am successfully running a reasonable screen resolution I am getting quite a bit of screen flicker and shake.

I downloaded Compiz but it doesn't seem to do anything, and now want to switch it off.

I can't enable Visual effects in Appearance Preferences ('Desktop Effects Could Not be Enabled') and it is set at 'None'.

Looking at the System Monitor the machine is running at between 15-35% CPU load (Intel Pentium 4, 2.00 GHz) and memory at 77.6% (of 512MiB).

Does my little old machine simply not have enough brains to run decent graphics?

Hope this is OK to continue this discussion in this thread.

Thanks

Steffan

---

### Post by Agent.Logic_ on 2009-04-18
Hi steffan,

Its probably just a video card issue. I've also encountered the flickering screen issue, but the additional options I set in the xorg.conf file were driver specific. You need to further configure your xorg.conf file with additional options for your driver. I'll see what I can dig up for you.

Cheers.

---

### Post by Agent.Logic_ on 2009-04-23
Hi steffan,

Been doing some research on your problem, and it seems compiz *should* run "out-of-the-box" on GMA 900 machines, but doesn't in a majority of cases. The user in [this post](http://ubuntuforums.org/showthread.php?t=823486) has a somewhat similar specification as yours, and it apparently works fine for him. However, a majority of people haven't been able to run Compiz, or atleast not able to run it without errors. And like I mentioned in one of my previous posts, the "Driver" section in the xorg.conf file should be indeed i915 for your chipset, but a majority of users haven't been able to get it working. [This thread](http://ubuntuforums.org/showthread.php?t=391105), although not containing a solution, provides some useful info. You might want to follow that thread, it has been active for over a year, although it has remained dormant for a good year or so (you could post in it and get it up and running once again).

---

### Post by apata on 2009-04-23
Hi!

I just installed Ubuntu 8.10 on my PC. After installation I run the upgrades an during this the process stopped and I restarted. After that the following message appeared: 

Starting up ...
0.032002] ..MP-Bios bug: 8254 timer not connected to IO-APIC
1.164148] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown ..
-block(0,0)


So, what can I do?

apata

---

### Post by Agent.Logic_ on 2009-04-23
Hello apata,

Welcome to the forums! I suspect this could be a hdd error. Have you tried to fire up the LiveCD and run the fsck command? Also, if you just installed Ubuntu, and haven't made any major changes (those are hard if not impossible to configure again), you could just reinstall from scratch. Probably the easiest thing to do in case of emergency AND if you haven't made changes/don't have tons of files and data to backup. Could also be that your grub (if that is the bootloader you are using) file has changed. Could you also post the contents of /boot/grub/menu.lst file?

---

### Post by apata on 2009-04-23
When I try to reinstall it, it gets stuck.

---

### Post by apata on 2009-04-23
How do I run the fsck command? What is a scratch? What can I do about the grub and how do I get to know if that is what I am using?

How do I do this? ->  Could you also post the contents of /boot/grub/menu.lst file?[/quote]

Sorry, I am a real beginner.

---

### Post by milesje on 2009-04-23
to run fsck you need to boot from the Live-CD and then hit CTL-ALT-F1 this will put you into a command line, then type fsck this is a tool that will check you hard drive for errors. "reinstall from scratch" means to completely reinstall your system from the Live-CD, besure to reformat the HDD if you do so. Grub is the default boot loader so if you did not change anything during the install of the system you are using grub. to get the contents of /boot/grub/menu.lst file open it up in a text editor like gedit, nano, or vi - type gedit /boot/grub/menu.lst on the command line (terminal).

---

### Post by Agent.Logic_ on 2009-04-23
Sorry about that, apata! I didn't know you were a real beginner! Like milesje says, fsck checks for errors in the hard drive. It is somewhat comparable to "scandisk" in Windows. Boot up from the LiveCD, go to applications > accessories > terminal and type in **fsck** in the terminal window that pops up (which somewhat resembles the CMD black box-like thingy in Windows). After it finishes its work, if it says there are no errors (or "clean", or something similar), it means there are no errors in your hard drive. A similar kernel panic happened to me while my Fedora update got stuck at 40%, and stopped automatically for some reason. An fsck fixed it for me, maybe you will have similar luck.

And could you please explain in detail where it gets stuck when you reinstall? Does it give you any sort of error messages? At what stage does the reinstall get stuck? Please elaborate so we could help you better.

---

