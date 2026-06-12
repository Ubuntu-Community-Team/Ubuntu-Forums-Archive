---
title: "Nvidia Optimus"
date: 2015-03-04
forum: Hardware
---

### Post by Keith_Helms on 2015-03-04
My quest to get a laptop working using Nvidia Optimus graphics

I bought a new laptop a couple of weeks ago that had the Nvidia Optimus hardware.  This seems to be a common configuration these days and I figured the Nvidia card would be good for playing h264 video files and blu-rays (if Linux ever gets to the point where you can just play them).  Nvidia Optimus is a hardware configuration where your laptop has dual video cards - an Intel card for your low-power, basic video needs, and an Nvidia card for your 3D/hardware accelerated graphics.

I knew Optimus systems had been out for a few years now, and I had previously gotten a laptop working using the Intel half of the duo, so I was curious to see how far the Linux support had progressed.  The best to worst case scenarios would be the following:

1. Both cards fully supported with the driver(s) automatically using whichever card was appropriate for the operation.   I believe that is how the Windows driver works.  A scan on Google didn't seem to indicate any such support from Linux and nothing that seemed to be "in the pipeline".

2. Both cards supported, but only one in use at a given time.  Which card is used would be user selectable and take effect immediately.  It doesn't appear this option is available either.

3. Both cards supported, but only one in use at a given time for all applications, chosen by user selection and requiring reboot or logging out and in.  This appears to be what the Nvidia Prime package is supposed to do.

4. The Intel card is used by default and the Nvidia card can be used for selected applications.   This appears to be what the Bumblebee project is supposed to do.

5. The Nvidia card is not available and only the Intel GPU is used.  This appears to be the default setup after a Linux install.

6. Neither card supported and the hardware could not be used with Linux.  That would suck, but fortunately at least the Intel card seems to be always supported.


I've been a Xubuntu user since Ubuntu moved off of Gnome 2 a couple of years ago, so I started with an install of Xubuntu 14.04.  After the install, the system was using the i915 video driver and the Intel graphics card by default.  The Nvidia card was listed as "Unclaimed".  The additional drivers dialog did not show any options.  So...

Attempt Set 1: I started by installing the latest Nvidia driver listed in the repository, which was version 331.  After doing that and rebooting, I got the Xubuntu splash screen at startup, the screen went black as it usually does for a couple of seconds, and then.... nothing.   The screen stayed black.  I eventually figured out I could reboot, select one of the recovery boot options, and then select resume boot to get back to a gui.  I went into Synaptic and removed the Nvidia drivers and I was then able to boot normally.

Attempt Set 2: Okay, that didn't work.  After some googling, my second attempt was to add a PPA for xorg-edgers which gave me access to more current Nvidia drivers.  I tried installed the Nvidia 340 and then the 346 drivers from that site.   Both of them lead to the same black screen.  After a few cycles of this nonsense, I learned that, when I was at the black screen, I could hit ctrl-alt-f1 to get to a command line and then remove the Nvidia drivers with "sudo apt-get purge nvidia*".  That saved some time between attempts.  I also wondered why there are so darn many versions of Nvidia drivers floating around - 173, 304, 310, 319, 331, 340, 346.  Don't they make the newer ones backwardly compatible with the older ones?

Attempt Set 3: Alright, Nvidia Prime doesn't seem to work, let's try that "Bumblebee" thing.  I installed the bumblebee and bumblebee-nvidia packages along with the nvidia 331 drivers and... hold my breath ... cool, my system boots.  When I do "sudo lshw -C video" from the command line, I only see the Intel card.   The Nvidia card has vanished.  I take off the "-C video" qualifier and Nvidia is in there as unknown and some of the settings have "invalid manufacturer code" or something like that next to them.  I do a bit of poking around and find that bumblebee has blacklisted the nvidia drivers so I guess Linux can't find any drivers that know about the Nvidia card.

Now it's time to play with Bumblebee.  Apparently I have to run any application I want to use the Nvidia card using the "optirun" command.  I'm not a gamer who's interested in FPS rates for first person shooters, so the two things I want to use the card for are video playback and virtual machines.  I try invoking VLC from the command line using optirun.  Nothing seems to happen.  Okay, I try the same command but with a .mkv file as a parameter.   This time a window opens with the video playing, but there are no menus at the top or navigation controls at the bottom, just a rectangle with a video playing in it.  That's not how it works when I start it from the menus.  I read the man file and find there are multiple versions of the vlc command, some of which have my menus.  I try qvlc instead.  It fails and spits out some messages about not being enabled for threading or something like that.  The other versions of the command give me the same errors.  I google the errors and find some posts suggesting using --no-xlib.  I add that as a parameter and I get a few less errors, but it still doesn't run.

I move on to virtual machines.  I have the free VMware player installed and Windows 7 in a virtual machine.  With the default Xubuntu install, VMware gave me warnings that "3d and hardware acceleration were not enabled".  I try running vmplayer with optirun and the warnings are gone.  Yay.  I go into Windows 7, start up IE 11, and when I browse Yahoo, the pages don't format properly.  I get black blobs instead of text in a lot of places.  The pages seem to load extremely slow also.  Not good.  I shut down the VM, bring it up again and go into edit settings for the Windows 7 vm.  I uncheck the "use 3d acceleration" option and then boot it.  This time the Yahoo pages format properly.  It appears that vmware "thought" it was using hardware acceleration, but it wasn't really working properly.  I google vmware and optirun and find some instructions for vmware workstation 9 (I'm using player 7.1) and ubuntu 12.04.  I figure it's worth a shot.  The instructions have me set up a couple of symlinks to nvidia drivers and to frontend a vmware executible with a script that contains the optirun command.  When I try to start the player, it crashes.

Attempt Set 4: Okay, bumblebee didn't work with the 2 main apps that I would probably use it for.  I configured my system with 3 boot partitions, so I thought I'd try another distro.  I installed Ubuntu 14.04 in the second boot partition.  Yuck, I don't like that Unity "touchscreen friendly, desktop unfriendly" gui.  I do some reading and install something called gnome flashback.  That gives me a fairly normal task bar and I can add quick launchers to it, although the process is a little obscure.  I have to remember to do ctrl-super-rightclick instead of just a normal rightclick.  Anyway, it seems to have most of the xfce/gnome2 features I'm used to, so it's tolerable.  I install the Nvidia 331 drivers from the repository.  After a reboot, the Nvidia X Server Settings tell me I'm using the Nvidia card.  Yay.  VLC seems to work fine.  I go into vmware, reenable 3d acceleration for Windows 7, and boot it.   The Yahoo web pages seem to be formatting properly.  double-yay.  I'm playing with the system and, all of a sudden. the mouse and screen freeze.  What the heck?  I do a ctrl-alt-f1 to get to a command prompt and search the system logfiles.   ????  Nothing in any of them that looks like an error.   I do a ctrl-alt-f7 and I'm back in my gui and the mouse is moving again.  Well, I guess a workaround is a plus.  After a few more minutes, the mouse and screen freeze again.  I use my workaround and am able to go a bit longer.  It appears this freeze problem is going to be too big a pain to make the system useful.  Once I'm in the virtual machine when it freezes.  Ctrl-alt-f1 doesn't do anything there and I can't figure out how to get out of the vm and back to Linux by using hotkeys.  I have to power off and back on.

Attempt Set 5: Well, Ubuntu was close, but it didn't quite work either.  Linux Mint seems to be very popular, so I figure I'll try that in the third boot partition.  I download the Cinnamon flavor of Mint and install it.  Okay, the procedures to set up launchers and stuff are a little different, but the features I want seem to mostly be there.  I install the Nvidia 331 drivers from the repository and reboot.  As with Ubuntu, the Nvidia X Server Settings tell me I'm using the Nvidia card.  Well, that's further than I got with Xubuntu.  I also seem to have that stupid mouse and screen freeze problem.  I figure I'll fall back to the Intel graphics card while I research that problem.  I go into the Nvidia settings dialog, select the Prime profiles option, click on the Intel/low-power option and, BAM!!!.  My system crashes.  Mint spits out an error message to the effect that the xserver has crashed and there are no valid x configurations and graphics have been disabled.  Grrr.  This stuff which has long been annoying is starting to get REALLY ANNOYING!

Attempt Set 6: I wondered if all the changes I made to Xubuntu had somehow fouled things up and was part of my problem.  I decide to try again with a fresh install.  I leave my original Xubuntu boot partition alone, which has a lot of stuff installed and configured, and do a fresh install in place of Linux Mint.  I install the Nvidia 331 drivers yet again and reboot.   Cool, at least this go-around it boots and doesn't give me a black screen instead of login.  After a few minutes, I get the mouse/screen freeze again.  Okay, time to dig deep and see if there's any way to get rid of that.  I google the problem and find dozens of hits.   Some report everything freezes BUT the mouse.   Some report that ctrl-alt-f1 doesn't work to get them out of it.  I concentrate on the ones that seem closest to my problem.  

Eventually, I come across bug 1220426 on the launchpad site.  Yeah, that seems like the same problem.  I scroll down through pages and pages of postings.  The postings all seem to be either people saying "this problem affects me too", or administrator types constantly tweaking the "status" of the bug.  This seems to be leading nowhere when all of a sudden I hit a posting saying "thanks 'somebody's name'!  Your fix works!".   Wait, what?  What fix?  I scroll up a little and find that launchpad has "helpfully" hidden something like 160 postings.  I click on a button to show hidden items and scroll back down.  I find comment 212 by Patrick Mertens contains a link to a patch file and a detailed list of instructions for applying it.  Hey, this MIGHT WORK!  I follow the instructions to download the xserver source code, apply the patch, and then build everything.  The instructions say to apply a couple of deb files, so I figure I'll go back and try to get my original Xubuntu install working.  I remove everything there related to nvidia, and make it reinstall all the xserver stuff.  Now it boots correctly without the black screen instead of login.

I install the deb files.  I cross my fingers, log out, and back in.  Black screen.   Okay, maybe I needed to reboot.  I reboot and, cool, at least I got a login screen.  When the system starts, I get 5 quick popup windows about something in x has crashed.  Uh oh.  Fortunately there were only 5 popups and not an endless series of them.  Once I select cancel on them, the system seems to be working.  I reboot again to see if I'm going to get them every time.  This time the system boots cleanly.  I start playing around with stuff and time passes.  No mouse freezes.  More time passes.  No mouse freezes.  

HOORAY!  I now have a working system with no show-stopper bugs and I'm using the Nvidia graphics card!  I feel like Bill Murray at the end of Groundhog Day.  This has been a very long sequence of near-identical attempts to get something working!

---

### Post by efflandt on 2015-03-06
Not sure if in all that text you mention which Nvidia chip you have, but my experience installing 64-bit Ubuntu 14.04.1 was uneventful with hybrid Intel HD 4600/Nvidia GTX 765m. But in late 2013 I specifically got the laptop with Win7 using legacy BIOS and msdos partitions (although, it is capable of UEFI), so not sure if that was the reason it went smoother. I had obsolete 64-bit 13.10 on a hard drive partition, but ordered an mSATA SSD card to do the fresh 14.04.1 install within the past month and put grub on the mSATA to boot from.

Contrary to usually requiring **nomodeset** during live/install boot for desktop Nvidia cards, I read that **NOT using nomodeset** worked best for hybrid graphics with Nvidia. So the live install went smoothly and I set up some things for trim and tmpfs for /tmp before rebooting the new system. I installed Steam and synaptic from Software Center before installing nvidia-331-updates using synaptic (although, I think that sequence is only an issue for AMD video) and after reboot everything worked great.

Your first point "2." works. NVIDIA X Server Settings can switch between Nvidia (default) or Intel graphics on the fly. Whether your first point "1." works depends upon setting up profiles in NVIDIA X Server Settings which I have not looked into yet. I just left it set for Nvidia, downloaded a Steam game (Team Fortress 2) and it worked great.

Not sure if there are any Nvidia snags related to 14.04.2 because I have heard of some AMD driver issues with that (and at various times with Steam).

---

### Post by Keith_Helms on 2015-03-07
I have the GeForce GTX 860M.

Whenever I use Nvidia X Server Settings to switch between cards, it tells me to log out and back in, so that's why I wrote that 2 doesn't work.   It isn't "immediate" in that you have to logout and in for it to take effect.

If you've come across something that says you can set up a profile that allows both cards to be used automatically by the system, I'd sure like a link to that reference!

Nvidia Prime works on both Xubuntu 14.04.2 and Ubuntu 14.04.2, but there is a bug in xserver (1220426) where my touchpad freezes up randomly when using Optimus graphics.  There is a fix for the bug that hasn't found its way into the distros, but you can apply it manually.  That requires building xserver from source.  I was able to do that on Xubuntu 14.04.2, but Ubuntu 14.04.2 has moved to a higher version of "X" - 1.6.0 vs. 1.5.1 in Xubuntu.  The build instructions didn't work for 1.6.0 and I can't figure out what to do to get them to work.  Oh well, I'll just stay in Xubuntu for graphics intensive use.

---

### Post by Yepi69 on 2015-03-11
I think you guys can help me with this one, when I install bumblebee bumblebee-nvidia and primus to use my Nvidia card (Nvidia GeForce 710M) it always boots Cinnamon into fallback mode, and it always boots like this until I purge bumblebee bumblebee-nvidia and primus, otherwise it doesn't boot with the Intel card and choosing Intel from Nvidia XServer Settings is a dead end cuz it only displays me a error box with no message on it, just a red X
Honestly I don't know what else to do, I purged nvidia-331 and installed again, and same thing happened.

---

### Post by Keith_Helms on 2015-03-11
Well, first of all, bumblebee blacklists the nvidia drivers and then optirun or primusrun loads them under the covers for use by the specified application.   When you have bumblebee installed, Nvidia X Server Settings isn't good for much of anything as the Nvidia driver is not loaded.

You didn't mention Prime, but I'll just throw out a couple of things I discovered.  Bumblebee w/wo primus and Nvidia prime are kind of mutually exclusive.   You can either use bumblebee to invoke the Nvidia card selectively, or without bumblebee you can use Nvidia prime to switch the entire system between the Intel and Nvidia cards.

When you say Cinnamon, are you using that under Ubuntu or are you using Mint?  I ran into a problem trying to use Nvidia Prime under Mint.   Apparently the display manager that Mint uses - mdm - does not work with Prime and you have to install the display manager that the Ubuntu systems use - lightdm - in order for it to work.

I ran into a couple of situations while I was struggling to get this going where I got a black display and no gui instead of the login screen.  After purging and reinstalling to the point where the system should have been the same as when it failed, it decided to work.   Sometimes it seems you just have to wait for this stuff to decide to work.

Bumblebee seemed to cause less problems than Nvidia Prime.  The one time I had problems with bumblebee was when I was trying to use the newer Nvidia 340 or 346 drivers from the xorg-enders PPA.   It turned out that the bumblebee config file wasn't set up to blacklist those newer drivers and I had to manually update it.

Anyway, I'd start by trying to get back to a working system.   Purge both the Nvidia stuff and the bumblebee packages and reset the xserver stuff.

sudo apt-get purge nvidia*
sudo apt-get remove bumblebee bumblebee-nvidia
sudo dpkg-reconfigure xserver-xorg

reboot and cross your fingers.   You *should* get a gui and be running on the Intel card.

Then I'd try reinstalling nvidia-331, then bumblebee and bumblebee-nvidia and primus if you want, then reboot.   You should still get a gui and be using the Intel card, but have the option to use optirun or primusrun to invoke the Nvidia card.

I learned to look at a lot of things when I was trying to figure out what was going on.   Some useful commands and files are:

**sudo lshw -C video** - this will tell you what video cards the system thinks you have and what driver (if any) is being used for them.   If the "-C video" option does not show the Nvidia card, then leave it off.  When bumblebee was installed, my Nvidia card was usually listed as "unknown" and not "unclaimed".

**lspci** - shows various internal hardware components.  Intel is listed as "VGA compatible controller" and Nvidia as "3D controller" on my system.   The output from this command doesn't change, but it's useful to see what hardware Linux is detecting.

**/etc/X11/xorg.conf** - You may or may not have one of these.  xorg.conf is optional in the newer versions of Ubuntu and there is also a bug related to hybrid graphics (nvidia optimus) where xorg.conf gets renamed to xorg.conf.mmddyyyy at boot.  If it's there, it's worth a peek to see what graphics card(s) it's configured for.

**/var/log/Xorg.0.log** - If you cannot get a gui when booting, this is probably where the error will be logged.  It may not tell you anything terribly useful, but it will give you clues.   A couple of times, I just saw "no screen found" in the log and didn't know WHY no screen was found.  That was a clue that something was fouled up with either my drivers or my xorg.conf.

**/var/log/gpu-manager.log** - This also might contain clues as to why your video setup didn't work.

Good luck.  Hopefully this will give you some things to look at and try.

---

### Post by Yepi69 on 2015-03-11
Thanks for the reply, I'm using Linux Mint 17.1 actually and I think its using mdm which I think it explains why it doesn't work, anyways even if I switch to Nvidia using Nvidia XServer Settings, it always boots cinnamon back to fallback mode until I re-open Nvidia XServer settings and manually switch to Intel again to boot properly.

---

### Post by Keith_Helms on 2015-03-11
Ah, yes I found that trying to switch cards using the Nvidia X Server Settings when running on Linux Mint 17.1 with the default display manager (mdm) was the kiss of death for my gui!  I found a posting somewhere that explained how to switch the display manager to lightdm and now that works for me.   Then I ran into the random touchpad freeze bug, but that's another story. <g>

---

### Post by Yepi69 on 2015-03-11
Be that as it may I installed lightdm from Synaptic's packet manager and changed it to lightdm, gonna reboot the computer later at night and see if I can finally use bumblebee and the nvidia card.

EDIT: Well I rebooted the laptop and lightdm wasn't starting, I had to start mdm to get Linux Mint to boot up.

---

### Post by Keith_Helms on 2015-03-12
Try using the instructions here:

[http://mintguide.org/system/208-install-nvidia-prime-of-nvidia-optimus-into-linux-mint-17.html](http://mintguide.org/system/208-install-nvidia-prime-of-nvidia-optimus-into-linux-mint-17.html)

---

### Post by Yepi69 on 2015-03-12
> **Keith_Helms said:**
> Try using the instructions here:

[http://mintguide.org/system/208-install-nvidia-prime-of-nvidia-optimus-into-linux-mint-17.html](http://mintguide.org/system/208-install-nvidia-prime-of-nvidia-optimus-into-linux-mint-17.html)
Thanks for replying, I get the following message:

''Reading package lists... Error!E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/packages.linuxmint.com_dists_rebecca_main_i18n_Translation-pt%5fBR
E: The package lists or status file could not be parsed or opened.
''

---

### Post by Bashing-om on 2015-03-12
Yepi69; Hi !

Most likely a corrupted control file:
> 
''Reading package lists... Error!E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/packages.linuxmint.com_dists_rebecca_main_i18n_Tra nslation-pt%5fBR
E: The package lists or status file could not be parsed or opened.


Try:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
sudo apt-get upgrade

```
to remove the control files, 'update' will rebuild them.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by Keith_Helms on 2015-03-12
I have no clue.  What command were you running when you got that?

If you have broken packages, you can try **sudo apt-get install -f**
and see if that fixes the problem.

---

### Post by Yepi69 on 2015-03-14
I tried that and it worked, I also tried installing lightdm but it did not work, the login screen would pop up, I would type in my password, it would flash a black screen and then would go back to the login screen afterwards, so what should I do from there?

Also I have a new problem, Linux Mint seems to be ignoring my startup commands, I sometimes connect my phone to my laptop through bluetooth in order to play music from the phone to my laptop's headphones, thing is, it never works until I type in the following command in the Terminal ''pactl load-module module-bluetooth-discover'' then my laptop can connect to my phone (A2DP) and vice versa
It used to work but it doesn't, also the same thing happens with xbindkeys and toucnpad-indicator (/usr/share/applications/extras-touchpad-indicator.desktop)

---

