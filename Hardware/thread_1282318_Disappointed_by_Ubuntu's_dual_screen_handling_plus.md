---
title: "Disappointed by Ubuntu's dual screen handling plus problems with resolution"
date: 2009-10-04
forum: Hardware
---

### Post by UeB on 2009-10-04
Hallo,

I bought a 26" TFT monitor and want to use it as a second screen for my laptop. So far I was not able to use it as I had it in mind.

First it only works if I connect it before I boot Ubuntu. Then I am not able to set the right resolution in the gnome display app. The maximal resultion I can set there is 1440x900 which is the resolution of the laptop screen although the correct resolution of the new TFT is 1.920x1.200.

But additionally the default handling of two screens is very confusing. I can drag windows from one screen to the other. That is nice. But when I maximise them they get maximised in BOTH screens as one big window. This behaviour is especially stupid when I want to watch a video file, because the half of the video is shown on each screen.

Ah and by the way the with a hdmi cable only cloning the desktop works so I bound to the vga calbe to be able to run different apps on the monitors.

Needles to say in the pre installed windows vista all worked well and as intended. The right resolution was not set by default but I could easily set it in the windows display app. Also when I maximise or full screen an app it only get maximised / full screened in on the monitor the app window currently is. And HDMI also just worked.


I attached a full list of my laptop hardware (the output of lshw). I have Ubuntu 9.04 and the proprietary ati drivers installed

Thanks in advance for any help or suggestions!

---

### Post by markbuntu on 2009-10-05
Are you using the newest driver from ati?
That will fix your problem.

---

### Post by UeB on 2009-10-05
Uhm yes I forgot to mention this: I use the drive that was recommend by the hardware driver app of Ubuntu 9.04.
I can I just download the newer driver from amd.com and install it or should I first uninstall the one I am using at the moment?

---

### Post by markbuntu on 2009-10-05
You should remove old drivers before installing new ones to avoid problems with kernel updates.

---

### Post by carolinason on 2009-10-05
what about using open source drivers? I have an ATI Radeon 9000 [COLOR="DimGray"]EDIT*** Since the catalyst drivers don't support this card ***EDIT[/COLOR] and have almost the same issue. I am limited in what resolutions I have and this isn't nice, since i could have 1440x900 and only get 1024x768. the other monitor will run at it's best res.

UGH!

---

### Post by markbuntu on 2009-10-05
You should read this if you are using the open source drivers

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by tgalati4 on 2009-10-05
I don't think the VGA cable can handle 1920x1200.  To get the higher resolution you need to use HDMI or DVI.

---

### Post by UeB on 2009-10-06
> **tgalati4 said:**
> I don't think the VGA cable can handle 1920x1200.  To get the higher resolution you need to use HDMI or DVI.

Well in Windows Vista I can set the right resolutin 1920x1200 with either the vga or the hdmi calbe so i do not think that the problems with the right resolution in linux is some sort of hardware limitation.

---

### Post by tgalati4 on 2009-10-06
It's possible that the linux driver does not cycle through all of the resolution combinations (perhaps written before 1920x1200 became popular).

Look through .xsession errors in your home directory and /var/log/Xorg.0.log for clues as to why 1920x1200 is not found or selected.

---

### Post by UeB on 2009-10-06
Sooo I clicked on "remove" (the ati driver) in the ubuntu hardware app, rebooted installed the driver form the amd website (ati-driver-installer-9-9-x86.x86_64.run) rebooted. When I was asked if the installed should create a distribution specific driver I chose the default answer which was no hat the word automatic in the sentencse which so

And well then I got a nice new problem: a splash screen saying: "Ubuntu is running in low-graphics mode" 

Then comes a question: "There already appears to be an X server running on display :0. Should I try another display number?"

I ansered yes and my gnome desktop was stated...
But only on the external monitor the laptop screen is black and after swiching to tty1 and back to X I seem to be have only 256 colors left...

soooo my question is what could I try to well make it work al little better and if this is not possible how to get rid of the driver...

kind regards

---

### Post by UeB on 2009-10-06
First thing I found with google was this poor guy who seems to haven the same problem

[http://ubuntuforums.org/showthread.php?p=7980092]("http://ubuntuforums.org/showthread.php?p=7980092")

but no answers there...




After a reboot I get the same "... running in low grafics mode ..."  message again. This time I chose "restore configuration form backup" but well just nothing happened when I did this...

---

### Post by UeB on 2009-10-06
Ok managed to get rid of the ATI catalyst 9.9. Old driver restored. Back to the problem of having an TFT with the wrong resolution....

---

### Post by tgalati4 on 2009-10-11
The catalyst driver may work, but you would have to downgrade to Intrepid, because of changes in xorg and the catalyst framework only supports newer ATI cards.

Post a bug against the open ati driver.  If the developers don't have that hardware combination, they can't test it.

---

### Post by UeB on 2009-10-11
Well, I now recognised that the open source ati driver was restored after the removement of the newest fglrx driver and not the older fglrx driver that you can install from within the hardware driver app.

I recognised it because I have no 3D-acceleration with the open source driver; not even SuperTux is playable.

So I just selected the Ati fglrx driver in the hardware driver app but now this older one does not work, too! 

After a reboot I only get a black screen and the computer freezes. 

I already tried it 2 times but the result is the same. So it seems I am stuck the open source driver that is part of xorg and does not support 3D...

So I spend 250 &#8364; on a TFT I cannot properbly use and the what I tried so far to make it work has left me without 3D acceleration which worked since I installed Ubuntu 9.04 6 month ago....

---

### Post by tgalati4 on 2009-10-11
It sounds like the newer proprietary driver left some settings that conflict with the older driver.  I'm not sure how to recover at this point, except:

sudo apt-get purge xorg-driver-fglrx

Also, make a backup of your current /etc/X11/xorg.conf:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg_last_used.conf

Then remove it:

sudo rm /etc/X11/xorg.conf

Then reboot.

Print out a the last few xorg.conf files so you can see what settings have changed with each driver.

---

### Post by UeB on 2009-10-11
na purging xorg-driver-fglrx does not have any different effect then just removing it.

If I install it again after the "purge" it sill does not work (I get only a frozen black screen the moment X should start)
This does not really surprise because if the uninstall script of the ati fglrx driver I directly downloaded from the AMD homepage left something behind (which it did as it seems), it will not be affected by removing the older fglrx driver that I can (un)install with apt-get.

This is my working xorg.config file:
(only non comment lines)
```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

This is the xorg.conf that the fglrx driver creates that I can install with apt-get... The one the worked well until I installed the current fglrx from AMD's website.
(only non comment lines)
```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection
```

when I seach for files and folders with the name fglrx I get several hits.. I could just delete them all... I am not sure if I should to this...

---

### Post by UeB on 2009-10-11
seems that all files containing the string fglrx in their name that I can find with "locate" are either cache files of apt or part of the app jockey which is the ubnutu hardware driver app...

So deleting them will probably not help anything

It is strange that this guide says the fglrx that is in the ubnutu repositories will not work with ubuntu 9.04 because the driver I have installed with this jockey app worked the last months...

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Instructions%20for%20Ubuntu%209.04%20(Jaunty)]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Instructions%20for%20Ubuntu%209.04%20(Jaunty)")

---

### Post by tuxxy on 2009-10-11
It isnt Ubuntu's handling of dual screens thats the problem.  Its your ATI card and them terrible drivers.  Hope you get it fixed but just an FYI dual screens on nvidia in linux is much easier and more complete than the windows equivelant.

---

### Post by tgalati4 on 2009-10-11
Look at the install script for AMD's website installation of the proprietary driver.  That will show the locations for all of the libraries and config files.  It sounds like there is a library, symbolic link, system config setting, or local config setting that is messing up your graphics.

The other thing to try is to bombard xorg.conf with switches:

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
#	SubSection "Display"
#		Virtual	2048 768
#	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver "ati"
	Option "DynamicClocks" "on"
	Option "mtrr" "on"
	Option "DesktopSetup" "Single"
	Option "ScreenOverlap" "0"
	Option "VideoOverlay" "on"
	Option "OpenGLOverlay" "off"
	Option "Stereo" "off"
	Option "StereoSyncEnable" "1"
	Option "FSAAEnable" "no"
	Option "FSAAScale" "1"
	Option "FSAADisableGamma" "no"
	Option "FSAACustomizeMSPos" "no"
	Option "UseFastTLS" "0"
	Option "BlockSignalsOnLock" "on"
	Option "XAANoOffscreenPixmaps"
	Option "AccelMethod" "XAA"
EndSection

Section "ServerFlags"
	Option	"DontZap"	"False"
EndSection

---

### Post by markbuntu on 2009-10-12
If you do not do

aticonfig --initial

or, if you already have an xorg.conf file 

aticonfig --initial -f

after installing the driver it will not work. 

If you are using the rt kernel there is some problems with installing the driver. I have got the 9.9 driver working with the rt kernel only in Hardy and only by doing a manual install and restarting twice.  (The first restart led to a black screen but restarting after that worked).

Remove all options until you have a working driver. Many options that worked in the past have been automated or deprecated in the newer drivers and will cause the driver to fail. Also many options are card specific and may work for only one card or card series but will break the driver if used with others.

---

### Post by UeB on 2009-10-12
> **markbuntu said:**
> 
If you are using the rt kernel there is some problems with installing the driver. 

Is there a chance I am not using the rt kernel because I do not know what it is?

@tuxxy
One year ago when I chose this laptop I deliberately bought one with a ATI card because I read on IT-news sites that AMD had opened the specs and therefor soon there would be open source driver with full feature support. Now I am sitting here using the open source xorg-radeon-driver that still has now 3d support for my card HD 34XX because of some magic interference (or whatever) of the different catalyst drivers that realy should not be there if the guys that had written the install/uninstall scripts had done better jobs.

@topic
I will try to look at the installer of the catalyst 9.9 and try to find out in something that was installed by it is still there as I was suggested here. I will not try to make the 9.9 work. At leat not before the dist upgrade that will come soon. I now want the old catalyst that is in the Ubuntu 9.04 repository back working because at least I know it did work last week...

---

### Post by markbuntu on 2009-10-12
You are most likely not using the rt kernel, you would need to explicitly install it.

Is this a laptop????
If so then you have a Mobility 4850 which is not the same as the HD4850 and is not listed as supported before the 9.9 driver.

sudo apt-get purge may not remove the kernel modules and some other parts if the driver was misinstalled which can happen if you try to use it with a card it does not support. The uninstal script was also broken for a few of the drivers (9.3-9.4...) and if you installed manually or from the hardware manager it does seem to work completely.

sudo apt-get purge fglrx fglrx-kernel-source fglrx-amdcccle

You might also need to remove the directories usr/share/ati and /etc/ati

reboot into recovery and use the fix x option. This will give you a clean xorg.conf and the VESA driver. Then when you get back to your desktop you should download the latest driver from the ati site to your desktop

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

Then make the file executable (right click on it and change the properties/permissions..execute) and run it from a terminal

cd Desktop

sudo sh ./ati-driver-installer....(fill it in the rest of the way)

type your passoword when asked and just hit enter when the install screen comes up.

If there were any errors you will see a message in the terminal and they will be in /usr/share/ati/fglrx-install.log.

The installer builds the fglrx DKMS modules for the kernel and installs them so this is where errors usually occur.

You can also look in /var/log/Xorg.0.log.old which will show errors from the previous boot (Xorg.0.log is from the current boot)

Then, in a terminal type

sudo aticonfig --initial

You should see a message about initializing the drive and replacing xorg.conf and renaming the old one or something like that.

reboot.

**Do not use System/Preferences/Display or anything other than the Catalyst Control Center to adjust your display.**


Make any changes in the Catalyst Control Center which will be in your menus somewhere.  Make only one change at a time and reboot after each change. The driver is very touchy about this. If you are having trouble getting into Catalyst (super user) you can launch it from a terminal with 

sudo amdcccle

---

### Post by UeB on 2009-10-12
Yes, as I wrote when I stated this thread it is a laptop. And yes it it a ATI Mobility Radeon HD 34XX (3450 I think) and not a 4850. And according to the AMD driver webpage the catalyst 9.9 does support this model.

---

### Post by markbuntu on 2009-10-13
Well did you try my suggestions???

---

### Post by UeB on 2009-10-13
Had no time today... Was in office until 20:15 and just drank a bottle of wine with my room mate... have to go to bed now... Maybe tomorrow...

kind regards

---

### Post by markbuntu on 2009-10-14
I hope it was good wine.

---

### Post by UeB on 2009-10-17
Ok I tried to follow your guide to install the latest ati driver from the official website but the result was the same that I discribed earlier in this thread: [http://ubuntuforums.org/showpost.php?p=8063710&postcount=10](http://ubuntuforums.org/showpost.php?p=8063710&postcount=10)

Some details:


> sudo apt-get purge fglrx fglrx-kernel-source fglrx-amdcccle
I could not purge theses things because I already removed them before. In synaptec there were not listed as "non installed packages with remaining configurations" so I did not worry about it.


> You might also need to remove the directories usr/share/ati and /etc/ati
I deleted them.


> reboot into recovery and use the fix x option. This will give you a  >clean xorg.conf and the VESA driver. Then when you get back to your >desktop you should download the latest driver from the ati site to your >desktop

did not see why this is nessecary because I was using the free radeon driver and not the fglrx for the last days so I skipt this part


The I stated the fglrx installer with sudo ./ati-driver-ETC... from a gnome terminal

When asked questions by the installer I always went with the defaut / automatic options.

The installer finished without printing any error msg. to the terminal. Then I ran sudo amdconfig --initial -f
The I rebooted and got the" Ubuntu is running in low-graphics mode" mesg as said before.

Then I looked in the fglrx-install.log which does not seem to report any important errors last few lines are:

```
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.28-15-generic'
build succeeded with return value 0
duplicating results into driver repository...
done.
You must change your working directory to /lib/modules/fglrx
and then call ./make_install.sh in order to install the built module.
- recreating module dependency list
- trying a sample load of the kernel modules
failed.
[Error] Kernel Module : Reboot required. 
```

full file attached

---

### Post by UeB on 2009-11-02
Just to inform you: After I upgraded to 9.10 last weekend and installed the fglrx driver that is in the 9.10 repositories everything is fine.

Now both screens work in the right resolution, I can use the HDMI cable and even the behaviour of app windows is as it should be: maximising works separately for every monitor.

---

