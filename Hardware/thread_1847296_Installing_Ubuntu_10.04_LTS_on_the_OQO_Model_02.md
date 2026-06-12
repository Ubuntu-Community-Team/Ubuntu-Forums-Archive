---
title: "Installing Ubuntu 10.04 LTS on the OQO Model 02"
date: 2011-09-20
forum: Hardware
---

### Post by cjcardinal on 2011-09-20
As of today, I have successfully installed Ubuntu 10.04 LTS on the OQO Model 02 UMPC.  I have spent the past couple of months working with different options, different distros, and countless forums to achieve this and I would like to share my success for anyone else who has this device and would like to be able to run a current Ubuntu LTS.

[CENTER][IMG]http://media.techworld.com/cmsdata/products/114132/OQO%2002%20196.jpg[/IMG][/CENTER]

I will break this down into steps and try to explain what I did and give credit where credit is due to the best of my ability.

[LIST]
[*]_[SIZE="3"]OQO Friendly Intrepid Ibex Installer[/SIZE]_
[/LIST]


This installer was put together by a member of the OQOTalk Forums by the name of Galtoid.  The thread can be found [**_here_**]("http://www.oqotalk.com/index.php?topic=3287.0") and a direct link to the ISO can be downloaded from [**_here_**]("http://www.randomdynamics.com/ubuntu-8.10-desktop-i386-oqo02.iso") along with the [**_MD5_**]("http://www.randomdynamics.com/ubuntu-8.10-desktop-i386-oqo02.iso.md5sum")

[http://www.randomdynamics.com/ubuntu-8.10-desktop-i386-oqo02.iso](http://www.randomdynamics.com/ubuntu-8.10-desktop-i386-oqo02.iso)
[http://www.randomdynamics.com/ubuntu-8.10-desktop-i386-oqo02.iso.md5sum](http://www.randomdynamics.com/ubuntu-8.10-desktop-i386-oqo02.iso.md5sum)

He has also included an [**_ISO_**]("http://www.randomdynamics.com/ubuntu-8.10-desktop-i386-usb.img") and the [**_MD5_**]("http://www.randomdynamics.com/ubuntu-8.10-desktop-i386-usb.img.md5sum") for a 1 gig image.

To set the USB drive to boot on the OQO, when you come to the OQO bios splash upon powering on the device, press and hold the **function(FN)key** and press **delete (also the backspace key)** to enter the bios.  Set your USB drive as the first boot option, exit out of the boot menu, and "write the changes to the CMOS."

When the OQO reboots, you will be met with the Ubuntu 8.10 install menu.  Choose the "Install Ubuntu" option.

Once the install is complete, remove the USB stick and restart the device.  You will now boot into Ubuntu 8.10

[LIST]
[*]_[SIZE="3"]Upgrading from Ubuntu 8.10 Intrepid EOL to Ubuntu 9.04 Jaunty EOL[/SIZE]_
[/LIST]


Assistance in upgrading from 8.10 to 9.04 EOL was found in a [**_blog_**]("http://mapopa.blogspot.com/2011/08/upgrading-from-ubuntu-810-to-904.html") written by a user named mariuz.

[http://mapopa.blogspot.com/2011/08/upgrading-from-ubuntu-810-to-904.html](http://mapopa.blogspot.com/2011/08/upgrading-from-ubuntu-810-to-904.html)

The first thing you need to do is edit your /etc/apt/sources.list to add the EOL upgrade repos.

```
sudo gedit /etc/apt/sources.list
```

Remove the Intrepid repositories and replace the contents of your sources.list with the following

```
deb http://old-releases.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ intrepid-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ intrepid-security main restricted universe multiverse
```

Once you save and exit the sources.list, enter the following into the terminal

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Then do the upgrade to 9.04 with the following

```
sudo do-release-upgrade
```

You will be met with the following error

```
sudo do-release-upgrade 
Checking for a new ubuntu release
Failed Upgrade tool signature
Failed Upgrade tool
Done downloading            
extracting 'jaunty.tar.gz'
Failed to extract
Extracting the upgrade failed. There may be a problem with the network or with the server.
```

The problem is with the metadata.  Since 8.10 is an EOL Release, the metadata is pointing to non-existant repos to pull the upgrade.  The same user has uploaded the metadata to point to the "Old Releases" repositories which can be viewed at [**_github_**]("https://gist.github.com/1170565")

To pull the proper metadata from git, ensure you have git installed

```
sudo apt-get install git
```

and once you do, enter the following into the terminal to pull the proper metadata for the EOL upgrade

```
wget https://raw.github.com/gist/1170565/c6d5b3deece6f7451ec76419810d898eda0fadde/metarelease.rvg -O /etc/meta-release.rvg
```

This is what it will look like for Jaunty with the proper upgrade locations in the metadata

```
Dist: jaunty
Name: Jaunty Jackalope
Version: 9.04
Date: Thu, 23 Apr 2009 12:00:00 UTC
Supported: 1
Description: This is the 9.04 release
Release-File: http://old-releases.ubuntu.com/ubuntu/dists/jaunty/Release
ReleaseNotes: http://changelogs.ubuntu.com/EOLReleaseAnnouncement
UpgradeTool: http://old-releases.ubuntu.com/ubuntu/dists/jaunty-proposed/main/dist-upgrader-all/0.111.8/jaunty.tar.gz
UpgradeToolSignature: http://old-releases.ubuntu.com/ubuntu/dists/jaunty-proposed/main/dist-upgrader-all/0.111.8/jaunty.tar.gz.gpg
```

You now need to modify your /etc/update-manager/meta-release file to point to the local metadata.rvg

```
sudo gedit /etc/update-manager/meta-release
```

Replace the URI = with file:///etc/meta-release.rvg

```
[METARELEASE]
URI = file:///etc/meta-release.rvg
URI_LTS = http://changelogs.ubuntu.com/meta-release-lts
URI_UNSTABLE_POSTFIX = -development
URI_PROPOSED_POSTFIX = -proposed
```

Now that you are pointing to the proper location for the Jaunty.tar.gz, enter the following in the terminal to begin the upgrade to 9.04 EOL

```
sudo do-release-upgrade
```

Once the upgrade is finished, reboot, and do

```
lsb_release -a
```

[LIST]
[*][U][SIZE="3"]Upgrading from Ubuntu 9.04 Jaunty EOL to Ubuntu 9.10 Karmic EOL
[/SIZE][/U]
[/LIST]

This next step will probably be considered "ugly" so if someone can offer better way to do it, I will be greatful and update this how-to.

I figured that since the metadata and the sources.list was already proper and setup as it was going from 8.10 to 9.04, that I could just do a do-release-upgrade.  This was not the case.  The update manager tried to point me to 10.04 LTS, which is obviously a jump that can not be done directly from an EOL release such as 9.04 (to my knowledge).  So, I went into the /etc/apt/sources.list and changed "jaunty" to "karmic" for all of the repos to force aptitude to pull a partial upgrade.

```
deb http://old-releases.ubuntu.com/ubuntu/ karmic main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ karmic-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ karmic-security main restricted universe multiverse
```

Once the partial upgrade was complete and I rebooted my device, I did a

```
sudo do-release-upgrade
```

and the upgrade to 9.10 proceeded as it should.

Once the upgrade to 9.10 is complete and you have rebooted, again, do

```
sudo apt-get update
```

and

```
sudo do-release-upgrade
```

to upgrade to 10.04 LTS Lucid.  If all goes well, which it did in my case, you should be looking at Ubuntu 10.04 LTS.  Bluetooth, sound, and wireless all worked after the upgrades.  If while you are upgrading from the initial 8.10 installer you are met with any prompts regarding replacing your blacklist, or your xorg.conf, reply to these with NO.

To close this out, I will say that I have attempted various installs ranging from alternate CD 10.04 installs, to Crunchbang Statler, to Peppermint two, as well as CLI with the above listed and was not successful.  After the steps listed above, this is the first, and only time I have successfully installed a flavor of Ubuntu other than the "OQO Friendly Intrepid Installer" listed at the beginning of this post.  My lack of knowledge in the different CLI options may be the culprit in this instance, but after hours on Google and various UMPC and OQO forums, this is what I Have come up with and I will call it a success.

I Hope this how-to is helpful to anyone out there running this device, as it is a fantastic piece of computer equipment and serves its purpose very well, only to be improved by a late install of Ubuntu.

[[IMG]http://img836.imageshack.us/img836/8751/20110921002346.th.jpg[/IMG]](http://img836.imageshack.us/img836/8751/20110921002346.jpg)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by varunendra on 2011-09-21
Nice job buddy!=D>

Hope you keep it updated, as not many of us have OQOs with us to experiment and suggest. Besides, you may also have to keep an eye on the older and external links in case they get changed / dead. But given the failed attempts on the [other thread]("http://ubuntuforums.org/showthread.php?t=1751565"), this one should definitely prove very helpful to others having similar installation problem with this model.

---

### Post by cjcardinal on 2011-09-22
> **varunendra said:**
> Nice job buddy!=D>

Hope you keep it updated, as not many of us have OQOs with us to experiment and suggest. Besides, you may also have to keep an eye on the older and external links in case they get changed / dead. But given the failed attempts on the [other thread]("http://ubuntuforums.org/showthread.php?t=1751565"), this one should definitely prove very helpful to others having similar installation problem with this model.


Thanks man...and i considered uploading that Intrepid ISO somewhere that I could monitor it and ensure that it didn't die, but I didn't want to take away from someone elses work.  I may do that though.

I am currently running Xubuntu on my OQO 02, from the result of this install (converted ubuntu) and can verify that it runs very well, as does Lubuntu, or just the LXDE.  GNOME/Openbox combo is a little smoother than the standard GNOME loadout, but I am definitely sticking with my XFCE setup.

Since this loadout was completed, I can confirm that Sound, Wireless, and Bluetooth work out of the box, and I also made a call from Skype last night and can verify that the integrated mic also works, and works well.  

Right now I am just cleaning up the install and removing things that I know I will not be using like the GNOME games, etc.  My only grip will obviously be the fact that since using that 8.10 Installer, You are stuck with ext3.  

I will upload the ISO listed in the OP when I get a chance, unless someone else wants to take on that responsibility...the internet out here in Afghanistan is...interesting...to say the least.  Ha.

---

### Post by jaimeaux on 2011-12-03
> **cjcardinal said:**
>  
the internet out here in Afghanistan is...interesting...to say the least. Ha.
 
 
I know what you mean about the internet in Afghanistan. I don't know if you're still here, but it definitely SUCKS.
 
Stay safe, brother.
 
 
Jaimeaux"

---

### Post by jaimeaux on 2011-12-04
I don't suppose you've encountered a problem where it won't load past 5% on the disk-partitioning, have you?
 
or one where you go to "install ubuntu" and it can't find the hard drive?

---

### Post by maestrobwh1 on 2012-01-05
Did the machine still suspend/hibernate after upgrading to LTS ?

I am still running intrepid and the latest postings on the OQO forums/site mention not being able to work out hibernate and suspend.  Suspend is vitally important to a portable device.

---

### Post by maestrobwh1 on 2012-01-10
"necroedit"

I finally did this.  Suspend works. have not tried hibernate.  I did have to add this to /etc/pm/config.d or the track-point will come out of suspend such that it behaves erratically. I found the post involving ThinkPad track-point resume problems with later releases.  

Make a file in that directory called 01trackpoint and paste this:
```
# reload psmouse to reactivate trackpoint scrolling
SUSPEND_MODULES="${SUSPEND_MODULES:+$SUSPEND_MODULES }psmouse"
```

I left my drive as ext3.  I don't have an ssd where ext4 shines and there are advantages to ext4 on "spinning" drives as well but they are not so noticeable that it matters to me.


Original post:
You can convert ext3 to ext4 but you would have to boot a usb image of another linux to do so.  I never really noticed if it was faster on a spinning drive, but it does work faster than ext3 on flash/SSD.  [http://www.cyberciti.biz/tips/linux-convert-ext3-to-ext4-file-system.html](http://www.cyberciti.biz/tips/linux-convert-ext3-to-ext4-file-system.html)

BUT, I am unsure if one should do this if the upgrade from 8.10 includes using the stock kernel with the upgrade.  I am fairly certain the stock kernel for 8.10 won't boot from ext4 easily, although one can mount ext4 using ext4dev in 8.10 [http://pabloseminario.com/2009/07/01/ext4-support-in-ubuntu-intrepid-8-10/](http://pabloseminario.com/2009/07/01/ext4-support-in-ubuntu-intrepid-8-10/)

**I do have one question still; does suspend still work after the upgrade?**

Hope you guys are well and safe still.  -BH


> **cjcardinal said:**
> Thanks man...and i considered uploading that Intrepid ISO somewhere that I could monitor it and ensure that it didn't die, but I didn't want to take away from someone elses work.  I may do that though.

I am currently running Xubuntu on my OQO 02, from the result of this install (converted ubuntu) and can verify that it runs very well, as does Lubuntu, or just the LXDE.  GNOME/Openbox combo is a little smoother than the standard GNOME loadout, but I am definitely sticking with my XFCE setup.

Since this loadout was completed, I can confirm that Sound, Wireless, and Bluetooth work out of the box, and I also made a call from Skype last night and can verify that the integrated mic also works, and works well.  

Right now I am just cleaning up the install and removing things that I know I will not be using like the GNOME games, etc.  My only grip will obviously be the fact that since using that 8.10 Installer, You are stuck with ext3.  

I will upload the ISO listed in the OP when I get a chance, unless someone else wants to take on that responsibility...the internet out here in Afghanistan is...interesting...to say the least.  Ha.

---

### Post by cptncatholic on 2012-02-13
"Upgrading from Ubuntu 9.04 Jaunty EOL to Ubuntu 9.10 Karmic EOL" 

I need some help. At this step, I changed the repos to pull the partial upgrade and did the 'apt-get update' and 'apt-get dist-upgrade'. But when I rebooted, the screen flashed a few times and I got a login prompt. I can't log in because the keyboard isn't responding.

Then if I wait a few minutes, some error messages will pop up that say:

usb 3-2: device not accepting address 10, error -71
hub 3-0:1.0: unable to enumerate USB device on port 2



Anyone have any thoughts? 
everything was going great until this happened.
Thanks!
TC

---

### Post by maestrobwh1 on 2012-02-14
> **cptncatholic said:**
> "Upgrading from Ubuntu 9.04 Jaunty EOL to Ubuntu 9.10 Karmic EOL" 

I need some help. At this step, I changed the repos to pull the partial upgrade and did the 'apt-get update' and 'apt-get dist-upgrade'. But when I rebooted, the screen flashed a few times and I got a login prompt. I can't log in because the keyboard isn't responding.

Then if I wait a few minutes, some error messages will pop up that say:

usb 3-2: device not accepting address 10, error -71
hub 3-0:1.0: unable to enumerate USB device on port 2



Anyone have any thoughts? 
everything was going great until this happened.
Thanks!
TC

Can you boot into recovery mode?

If so, and you can get to a propmt and not go into X and you should have your keyboard (I think the screen flashing is X trying to start), and if you get the blue screen that drops you into root

dpkg --configure -a 

and see if something remained unconfigured.  I had this problem, then I had to bring up an internet connection via command line and do 

apt-get -f upgrade

I had to do this a few times because the upgrade botched.  The issue I had is that the prompt is somehow not showing, becuase the whole visible display is less than the actual display.  I had to blindly type my commands.  Since this was my problem, I got it fixed up.

Other suggestions:
Boot using the pervious kernel if you think it is an acutal usb issue, might not work.

If you can get the internet up from command line, assuming you are at 9.10, you could do a release upgrade and it should go up to Lucid, then it should work.

Did you keep the original xorg.conf from the 8.10 intrepid release?  

Add the following to the boot prompt (hit "e" when you get to the grub options) and insert before "quiet splash"

xforcevesa

If you have NO keyboard response even in recovery mode, and an old kernel won't boot, you probably have to "do over."

---

### Post by cptncatholic on 2012-02-19
> **maestrobwh1 said:**
> Can you boot into recovery mode?

If so, and you can get to a propmt and not go into X and you should have your keyboard (I think the screen flashing is X trying to start), and if you get the blue screen that drops you into root

dpkg --configure -a 

I was finally able to get to a prompt with networking. When I ran this command, I didn't get any output, so I'm assuming that means everything cleared.

> **maestrobwh1 said:**
> and see if something remained unconfigured.  I had this problem, then I had to bring up an internet connection via command line and do 

apt-get -f upgrade

I had to do this a few times because the upgrade botched.  The issue I had is that the prompt is somehow not showing, becuase the whole visible display is less than the actual display.  I had to blindly type my commands.  Since this was my problem, I got it fixed up.

I tried the 'apt-get -f upgrade' command, but did wouldn't pull any other upgrades. Strike two.

> **maestrobwh1 said:**
> Other suggestions:
Boot using the pervious kernel if you think it is an acutal usb issue, might not work.

If you can get the internet up from command line, assuming you are at 9.10, you could do a release upgrade and it should go up to Lucid, then it should work.

Also tried a 'do-release-upgrade' from the command line, but it said "Fetching the upgrade failed. There may be a network problem." Which may be that it's trying to fetch from the wrong place.

> **maestrobwh1 said:**
> Did you keep the original xorg.conf from the 8.10 intrepid release?  

I didn't see any prompts to change or keep it, only the blacklist prompt (to which I said no). So, I'm not sure if the xorg.conf was overwritten automatically or accidentally. 

> **maestrobwh1 said:**
> Add the following to the boot prompt (hit "e" when you get to the grub options) and insert before "quiet splash"

xforcevesa

I tried this once, but I'm not familiar with grub so my changes didn't stick, so I'm not sure if it worked. 

> **maestrobwh1 said:**
> If you have NO keyboard response even in recovery mode, and an old kernel won't boot, you probably have to "do over."

I'm on my 5th do over now. I've tried other ways to get around this hurdle, using the update manager even. But it doesn't work. Thanks for your help! If we can't knick it, I'll just do over and stop at 9.04.

Thanks!
tc

---

### Post by cptncatholic on 2012-02-20
Update:

Since I was able to get into recovery mode in 9.10, and get a root command prompt with networking, with the keyboard still working, this morning I updated the /etc/apt/sources.list with the following for Lucid:

```
deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-security main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-security main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted universe multiverse

```

Then I ran:

```
apt-get update
```

and then:

```
apt-get dist-upgrade
```

and crossed my fingers.

I'll report back later whether or not it worked. [-o<

tc

---

### Post by cptncatholic on 2012-02-21
Okay, well the upgrade worked, but I'm still not getting any love from X and still not able to use the keyboard. 

So.... #-o  ](*,)

still working on this.
tc

---

### Post by maestrobwh1 on 2012-03-01
No keyboard?  Maybe there is something in xorg.  I did ot have the problem but the xorg.con was full of crap with the upgrades and I cleaned it up.

Try my version of xorg.conf

I am still stuck with no 3D effects.  I tried adding virtual so I could enable panning and the driver didn't handle it. It is commented out.  You could use vesa as the driver but the colors and contrast seemed less appealing. 

Another tweak is to add to etc/modules if your trackstick goes nuts.
> option psmouse proto=bare

and this to /etc/pm/sleep.d  --> file called 15mouse
```
!/bin/sh
#       mouse issue

case "$1" in
	hibernate|suspend)
		;;
	thaw|resume)
		sleep .5
		modprobe -r psmouse
		sleep .5
		modprobe psmouse proto=bare
		;;
	*) exit $NA
		;;
esac
```

My /etc/X11/xorg.conf

```
Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "openchrome"
	Option 		"VBEModes" "true"
   	Option 		"EnableAGPDMA" "true"
	Option          "AccelMethod" "EXA"
	Option 		"MigrationHeuristic" "greedy"
	Option 		"SWCursor"
#	Option 		"PanelSize" "800x480"
#	Option 		"ActiveDevice" "LCD"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Option		"DPMS"
	HorizSync	30-92
	VertRefresh	50-85
	Modeline	"800x480" 29.50  800 824 896 992 480 483 493 500 -hsync +vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"800x480" "640x480"
#		Virtual		1600 960
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 		"Default Screen"
EndSection

Section "DRI"
	Group 0
	Mode	0666
EndSection

Section "Extensions"
    	Option 		"Composite" "Enable"
EndSection
```

---

### Post by stevencook17 on 2012-10-28
Hopefully some of you are still attached to this forum, but then again the last post was from March... So we shall see. I have just recently purchased an OQO Model 02 off eBay and will be attempting to perform this guide and see if I can repeat the results found here. I won't have the device for a few more days, but once it arrives I will be sure to post about it and hopefully by then i'll see if anyone is still online to aid me if I end of needing it. Thanks to anyone who returns to here for assistance.

---

### Post by stevencook17 on 2012-11-01
Okay I just got my OQO in the mail and installed my 64GB SSD, I will begin the install process and once i'm done i'll post results.. I wish the previous posters were still here, kinda makes me fell like i'm talking to myself, regardless if future posters find this, then i'll be glad I helped.

---

### Post by varunendra on 2012-11-01
> **stevencook17 said:**
> I wish the previous posters were still here, kinda makes me fell like i'm talking to myself, regardless if future posters find this, then i'll be glad I helped.Indeed you'll be helping many. As I said earlier in this thread, not many of us have OQOs nor any first hand experience with it. Therefore it doesn't make sense to make unnecessary comments which are not helpful. We can only offer general help which is not very specific to the OQO hardware.

Since the last 'Solved' post in this thread is pretty old now, and the OP doesn't seem to be around, I'd suggest to post your experience in a new thread of your own so that we know how compatible the latest Ubuntu version is, whether any workarounds are needed, and overall, if it works! You should then post its link here so anyone who comes across this thread looking for help can follow that.

And please don't think you're talking to yourself ! We'd definitely reply if there is something to speak :).

Good luck!

---

### Post by stevencook17 on 2012-11-03
Thanks and I will do, I have my own thread started, I was double posting in hopes that the others were still around. Now that I know some people are still out there ill continue my testing. I am not very savvy in the area of ubuntu coding or tweaking, but i'm learning. So knowing this i'll be posting in my thread. :)

---

### Post by goatcow on 2013-02-11
I had no problem getting it installed/upgraded through ethernet, but wireless isn't going anywhere - tossing a reply on this thread hoping someone can help:  my issues are listed here with oqo model 02:   [http://ubuntuforums.org/showthread.php?t=2113143](http://ubuntuforums.org/showthread.php?t=2113143)

---

### Post by maestrobwh1 on 2013-08-28
Near the bottom addresses the wifi and sound with 12.04:

You can try ubuntu 12.04 using boot flags:  ```
nomodeset xforcevesa via_agp.blacklist=yes via.blacklist=yes pcspkr.blacklist=yes pcspkr.blacklist=yes snd_hda_codec.blacklist=yes snd_hda_intel.blacklist=yes psmouse.proto=bare 
```  The psmouse reference keeps the mouse from going wild, but it does sometimes anyway.  The hda_intel blacklisting prevents the boot from locking up bc the kernel does not recognize the sound card properly, and streams an error about this module infinitely and one one has to hold the power button in to stop the machine.   

If you can't get it to boot, try the mini.iso for 12.04 as a poster here (goatcow, post 18) got the system installed that way and boot via network/ethernet OR, if you don't have a dock/dongle.  One could also try booting the alternate CD.  The CD boot with 12.04 seems to go awry just before X starts with some weird recurring message about hda-intel: the machine just then locks up.

After the install, before rebooting, mount the disk in terminal the old fashioned manual way to some mount point and make these changes to the installed filesystem.  If you have no docking station, you might be able to network install like the guy above if you have an ethernet/vga dongle.  If not, install ubuntu Maverick with the nomodeset and xforcevesa flags, and upgrade.  Keep the maverick kernel and you won't have to address sound/wifi.  It will just work.

to /etc/default/grub before "quiet splash"
```
nomodeset xforcevesa via_agp.blacklist=yes via.blacklist=yes pcspkr.blacklist=yes snd_hda_codec.blacklist=yes snd_hda_intel.blacklist=yes psmouse.proto=baree
```

I'd actually add the above to the kernel entry in /boot/grub.grub.cfg  I know the file screams at you not to edit it, but if you are connected via ethernet cable and can copy paste the above, and know what you are doing, your boot will go better.  You'll even get a splash.

Add to /etc/modprobe.d/blacklist.conf
```
# oqo model 02
blacklist via
blacklist via_agp
blacklist pcspkr
```

These might be redundant, but my system is rock stable.  

My xorg.conf:
```

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "openchrome"
	Option 		"VBEModes" "true"
   	Option 		"EnableAGPDMA" "true"
	Option          "AccelMethod" "EXA"
	Option 		"MigrationHeuristic" "greedy"
	Option 		"SWCursor" "true"
EndSection

Section "DRI"
	Group 0
	Mode	0666
EndSection

Section "Extensions"
    	Option 		"Composite" "Enable"
EndSection
```

The last kernel that works the wifi and sound on this oqo 02 is 2.6.35 BUT the good new is that it works well if you somehow managed to get some higher version of Ubuntu installed.  It seems kernel 3.x Ubuntu kernel just doesn't play nice with the OQO. in Puppy Linux Precise, kernel 3.9 has sound and wifi so I dont know what in Ubuntu is blocking wifi and sound.

Install the maverick kernel:

open your favorite editor and copy it to /etc/apt/suorces.list.d/ I called it maveric.list (must end in .list)

```
## EOL upgrade sources.list
# Required
deb http://old-releases.ubuntu.com/ubuntu/ maverick main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ maverick-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ maverick-security main restricted universe multiverse

# Optional
deb http://us.archive.ubuntu.com/ubuntu/ maverick main universe restricted multiverse
deb http://old-releases.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
```

then 

to /etc/default/grub before "quiet splash" DELETE the
```
snd_hda_codec.blacklist=yes snd_hda_intel.blacklist=yes
``` 

sudo apt-get update && sudo apt-get install linux-image-2.6.35-32-generic linux-headers-2.6.35-32-generic

REBOOT with that kernel then

REMOVE linux-image-generic, linux-headers-generic, and any linux-image-3.x and those headers... they are useless if you want sound/wifi.  YOU DO NOT WANT THE KERNEL TO UPGRADE.

---

### Post by maestrobwh1 on 2013-08-28
This will boot from USB, but not if you have a save file

[http://murga-linux.com/puppy/viewtopic.php?t=67724](http://murga-linux.com/puppy/viewtopic.php?t=67724)

---

