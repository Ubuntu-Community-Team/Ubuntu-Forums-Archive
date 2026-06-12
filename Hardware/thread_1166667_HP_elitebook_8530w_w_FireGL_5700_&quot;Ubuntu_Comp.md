---
title: "HP elitebook 8530w w/ FireGL 5700 &quot;Ubuntu Compatibility&quot;"
date: 2009-05-22
forum: Hardware
---

### Post by HunterThomson on 2009-05-22
Aloha ):P
by, HunterThomson - HowTo's that WORK !

[COLOR="Blue"][SIZE="3"]The Open Source ATI driver xf86-video-ati is a far better driver then the Catalyst. However, it has poor power saving support, so could run hotter. Also, has poor 3D support but can play Quake Live, Tribal Trouble 2, Super Tux Kart, Open Arena. However, EVERYTHING ells is SUPER. KVM 2D, Video, All that is really good. [/SIZE][/COLOR]

[COLOR="Green"]However, I am happy to say we got **EVERYTHING** working on this laptop. Well all but the fingerprint reader but from what I understand there just is not a Linux driver for the "AuthenTec with 08ff:2810"[/COLOR]
 
[SIZE="3"]This thread will provide you with all the info I have on getting the HP EliteBook 8530w w/ ATI FireGL 5700 to work with Ubuntu Linux. Feel free to post any new info you have. We would all be vary happy to hear what you have to say.[/SIZE]


=;[SIZE="2"][COLOR="Blue"]First things First, in order to avoid a Kernel panic Enter the CMOS set-up and change the option,[/COLOR][/SIZE]
```
"Fan always on while on AC" to "OFF"
```

[SIZE="3"][COLOR="Purple"]Big Thanks to DanaG :D He is the one that found the fix for...[/COLOR][/SIZE]
Getting the Catalyst to work with the acpi services off thing
Booting with EFI/UEFI
Fixing the accelerometer
Blacklisting the driver that sees the accelerometer as a joy stick
Provided the xorg.conf file I use and posted to this thread

_eSATA port     >>>>>     [COLOR="Green"]Works[/COLOR] I have and external HHD plug in it right now_
_Compiz     >>>>>     [COLOR="Green"]Works[/COLOR] With patched Xserver see HowTo below_
_BlueTooth     >>>>>     [COLOR="Green"]Works[/COLOR] _
_Cardreader    >>>>>     [COLOR="Green"]Works[/COLOR]  well I have a SDHC card and it works..._
_Express card  >>>>>     [COLOR="Green"]Works[/COLOR] _
_SmartCard     >>>>>     [COLOR="Green"]Works[/COLOR]  From what I am told_
_Dule Head     >>>>>     [COLOR="Green"]Works[/COLOR]  You just need to set up the xorg.conf file_
_Optical Drive >>>>>     [COLOR="Green"]Works[/COLOR] _
_Audio         >>>>>     [COLOR="Green"]Works[/COLOR]  Out of the Box_
_Fingerprint    >>>>>     [COLOR="Yellow"]Nope[/COLOR]  I think it mite work VirtualBox has an entry for it? OpenBSD sees it too_
_TrackPoint    >>>>>     [COLOR="Green"]Works[/COLOR] _
_Tuchpad       >>>>>     [COLOR="Green"]Works[/COLOR] _
_Volume Slider LED>>>>>     [COLOR="Green"]Works[/COLOR] _
_Mute LED      >>>>>     [COLOR="Green"]Works[/COLOR]_
_Fn backlight  >>>>>     [COLOR="Green"]Works[/COLOR]  Even the auto sensor_
_Suspend       >>>>>     [COLOR="Green"]Works[/COLOR] _
_Hibernate     >>>>>     [COLOR="Green"]Works[/COLOR] _
_Intel WiFi 5300     >>>>>     [COLOR="Green"]Works[/COLOR] You will need to follow the "How To" below_
_Ethernet      >>>>>     [COLOR="Green"]Works[/COLOR] _
_FireGL 5700   >>>>>     [COLOR="Green"]Works[/COLOR]  With tweaking only, only Ubuntu_
_Docking Station>>>>>     [COLOR="Green"]Works[/COLOR] USB,DVI,VGA,LAN,PS2,Serial,Audio Out work>>>Parallel port & Audio In untested_
_3G  HPun2400     >>>>>     [COLOR="Green"]Works[/COLOR]I'll write instructions latter but for now just Google...  HPun2400 ubuntu   ...and you will find how to use it_


[COLOR="Blue"][SIZE="3"]Ok so, now that we got that out of the way. Here are a few things I found out.[/SIZE] [/COLOR]

1. ATI Mobility FireGL 5700 is not fully supported by the Open Source AIT driver yet so you have to use the Catalyst.

2. Track point falls off real easy. If I were you I'd pull it off now and put a small, vary small amount of glue on it and stick it back on. I used a pin head dot of JB weld (I like the JB weld I suggest it and it is good to have around the house anyway so go buy some) in the rubber button it self not on the keyboard stub(I really used a Pin). Use vary little glue. If any glue squeezes down into the keyboard that would be vary bad. However, you can replace the keyboard vary easyly. First unscrew the two screws on the bottom of the laptop with the picture of a keyboard next to them. Then, you see thoughts four tabs in between the F1-12 keys... you just slide them back away form the screen and the whole keyboard will pop right out.

3. I found a fix for the Intel WiFi 5300 and wrote up a HowTo below. The intel 5300 driver is vary buggy with the current 2.6.28-11 Kernel in Jaunty 9.04. It would cause corruption of downloads and rendered the WiFi useless.

4. The Linux Kernel will crash if you don't change a BIOS setting. You have to go into CMOS set-up and change the "Fan always on wile on AC" to "Off."

5. The BIOS would not see my OCZ Vertex SSD drive if I had even One Logical partition. I don't know if this is a problem with other HHD's SSD's but if your laptop is not booting. Make all the partitions Primary Partitions.

6. The Mobility FireGL 5700 is really a Radeon HD3650.

7. WOW dose this thing run cool. I am downloading a torrent and surfing the web and my CPU (P8400) is at 25C !

I got the Catalyst to work in Archlinux :guitar:

I would like to say....

The WiFi is [COLOR="Blue"]no problem in Arch linux[/COLOR]
Flash is [COLOR="Blue"]no problem in Arch linux[/COLOR]
Video games like supertuxkart in the menu screen thinking that your pressing joydown all the time... [COLOR="Blue"]Is not a problem in Archlinux[/COLOR]
-------------------------------------------------------------------------------------------------------------

[COLOR="Blue"][SIZE="3"]How to get the Intel WiFi 5300 Working in Ubuntu 9.04[/SIZE][/COLOR]

[COLOR="Blue"]OK, you will need to install the new Pre-released Kernel and backports
I think that it is really just the new Ubuntu Kernel that is fixed. So, when we officially are on Ubuntu Kernel 2.6.28-12 then you probably will not need to do this.[/COLOR]

_>OK Before you mess with the Catalyst install you need to upgrade the Kernel so your work will not be in vain._

[COLOR="Blue"]>If you have already installed the Catalyst and are now Fixing the WiFi...
> Just Follow this HowTo "word for word" but this will brake your Catalyst Driver. So, You will need to follow the section I have below "This is What you Will do to Fix It"[/COLOR] 

_>You will need to enable Ubuntu Pre-released updates by first opening the "Software Sources" GUI here..._

```
System/Administration/Software Sources
```

_>Now click on the "Updates" Tab and check the box to the left of "Pre-released updates (jaunty-proposed)"_

_>Then click close and it will up date the package list._

_>Now open a terminal and install the linux-backports-modules-jaunty_

```
sudo apt-get update && sudo apt-get install linux-backports-modules-jaunty
```

_>Now [COLOR="Red"]DON'T Reboot[/COLOR]_

_>Install the Kernel headers for this new Kernel because you will need them latter._

```
sudo apt-get install linux-headers-2.6.28-12-generic
```

>Ok all done really just go back into the "Software Sources" and Un-check that box next to the "Pre-released updates (jaunty-proposed)"

>Then click "close" and it will update the package list agin.

-------------------------------------------------------------------------------------------------------------

[COLOR="Blue"][SIZE="3"]_To install the ATI catalyst Follow these steps._[/SIZE][/COLOR]

I got most of this stuff but not all form this thread and it "mite" be of use to you if you have some question or problem latter on.
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

_1- Download the newest driver from the ATI web site._

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

_	>Select Linux x86 or x86_64 -> Then radeon -> Then HD3xxxx_

_	>If you like you can install this stuff but Ubuntu will install it automatically_

```
sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++5 dkms
```

[U]	>Then open the terminal and change directory (cd) to where you downloaded the catalyst driver. 
	 Like this if you downloaded it to the Desktop.[/U]

```
cd Desktop
```

_	>Then create .deb packages out of the installer. Note the checksum will be off if you downloaded it while on the Intel 5300 wireless card because the download really is corrupted. You will have to be on Ethernet or use a USB wireless card._

```
sh ati-driver-installer-9-*-x86.x86_64.run --buildpkg Ubuntu/jaunty
```

_	>Then run this command and it will error out. That is OK._

```
sudo dpkg -i xorg-driver-fglrx_*.deb fglrx-kernel-source_*.deb fglrx-amdcccle_*.deb
```

_	>Then install the --force command._

```
sudo apt-get install -f
```

_	>Now the installer will work._

```
sudo dpkg -i --force-overwrite xorg-driver-fglrx_*.deb fglrx-kernel-source_*.deb fglrx-amdcccle_*.deb
```

_	>Now you need to download the working xorg.conf.txt file attached to this thread. "Save To your Desktop"_
	
_	>Now run this command to backup your cerent xorg.conf and install the working one you downloaded to the Desktop._

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf-bkp && sudo mv ~/Desktop/xorg.conf.txt /etc/X11/xorg.conf
```

_	>Now you have to turn off ACPI support for your ATI grafics card to avoide a Kernel Panic_

```
sudo aticonfig --acpi-services=off
```

_	>Now reboot and all "Should" be well and working._
-------------------------------------------------------------------------------------------------------------
[SIZE="3"][COLOR="Blue"]OK now to make Compiz play nice with Xorg Sever[/COLOR][/SIZE]

_Ok, I got all of this form this link. So look here if this is out of date or not working_

[https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill](https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill)


_>Ok so you need to add a new source to your repo's_

_>Fist open the "Software Sources" GUI_

```
System/Administration/Software Sources
```

_>Then select the tab "Third-Party Software_

_>Then Add... these two APT lines by clicking on the "Add..." button and cut/past them in. Add them "ONE at a Time"_

```
deb http://ppa.launchpad.net/ubuntu-x-swat/xserver-no-backfill/ubuntu jaunty main
deb-src http://ppa.launchpad.net/ubuntu-x-swat/xserver-no-backfill/ubuntu jaunty main
```

_>OK good stuff, Now you just need to enter it's GPG Key_

_>Fist follow this link_

[http://keyserver.ubuntu.com:11371/pks/lookup?search=0x643DC6BD56580CEB1AB4A9F63B22AB97AF1CDFA9&op=index](http://keyserver.ubuntu.com:11371/pks/lookup?search=0x643DC6BD56580CEB1AB4A9F63B22AB97AF1CDFA9&op=index)

_>That "Should" open a new tab, On that tab you will see_

```
pub  1024R/AF1CDFA9 2009-01-20 Launchpad PPA for Ubuntu-X
```

_>Click the "AF1CDFA9" or whatever that # is at the time._

_>Then it should take you to a page with the GPG/PGP key and looks like this_

```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESXVCiwEEANKBDbiSLOJOouub/S97iDifYCVW1b0KONg7XkFYiFos+bMBzzZyGGo90k1h
hCxcseLvqCKPL7dG0RzPRKMo7mvM68yyqi2ljw0ZYC9cVf0YzgKRTohVhihelpwZ+sBRGNYk
OCu+u0Dr+EdVI3u5RNOxAELrbd4vYaS+2cCOfzmLABEBAAG0GkxhdW5jaHBhZCBQUEEgZm9y
IFVidW50dS1YiLYEEwECACAFAkl1QosCGwMGCwkIBwMCBBUCCAMEFgIDAQIeAQIXgAAKCRA7
IquXrxzfqY4HBACIQEFhl59ZkuIhTD3pmCQgfkhpcg0RVdB6Xwhu3QDJvmlWmrs+cofNMzyA
7SwdjD9ARvhGbqHwub+T7oGiHlmFyodGypUZ4i/fdHsZYpsf34MwgYxhyNyOPY/jNImUE/yw
kSI+kV5esWURH4j0jYfkaergFqCpDnsSkxuIvdjH2Q==
=bkAa
-----END PGP PUBLIC KEY BLOCK-----
```

_>Now open up gedit or any text editor you like and Cut+Past in the whole key. Then save the file with any name, like NewRepoKey_1_

_>Back in the "Software Sources" GUI click on the "Authentication" Tab_

_>Then click on the "Import Key File..." button and navigate to the key you saved and click OK._

_>Now click "close"_

_>Now take a brake and have a e-smoke._

_>Now you can up grad you system through any of the multitudes of GUI's Ubuntu preinstalls_

Or just
```
sudo apt-get update && sudo apt-get upgrade
```

--------------------------------------------------------------------------------------------

[COLOR="Blue"]_[SIZE="3"]If for some crazy reason all is not well and not working at all then you can Undo all this stuff by doing this.[/SIZE]_[/COLOR]

_	>Reboot and when the Grub is counting down form 3sec's hit enter._

_	>Then select the Recovery mode._

_	>When you get to the GUI arrow down and select "Root Shell"_

_	>When your in the Root Shell run this command to uninstall all the Catalyst driver stuff you installed._

```
apt-get remove fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx
```

_	>Then replace the old xorg.conf file you backed up by running this command_

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf-ati && mv /etc/X11/xorg.conf-bkp /etc/X11/xorg.conf
```

_	>Now reboot and all should be just as it was before you messed it all up_

```
reboot
```

-------------------------------------------------------------------------------------------------------------
[SIZE="3"][COLOR="Blue"]OK, So now all is working, rock on.
However, time go's on and we get a new kernel and if it brakes the ATI catalyst driver.
All is not lost....

_**This it what you will do to fix it.**_[/COLOR][/SIZE]

1> Go through all the steps I have up above to "Undo" all of the catalyst install. In the "If it didn't work for some crazy reason" section.

2> Then you will boot up again after doing all that and you should be droped at the desktop using the Ubuntu default driver and the xorg.conf-bkp file you moved back to /etc/X11/xorg.conf by doing all the steps above. If not, like some craziness has gone down and all our laptops are not working with the default driver under the new Kernel. Well, I'll fix or if you do first post a HowTo in this thread for us all.
_All should be well though._

3> Just start back at the top and reinstall the newest ATI catalyst driver _by doing "ALL" of the steps that I have up above for installing the Catalyst driver, all over again._

4> Reboot and all should be well again.
-------------------------------------------------------------------------------------------------------------

[COLOR="Blue"][SIZE="3"]If your having problems with games like SuperTuxKart in the menu thinking your always pressing joydown. DanaG fixed this problem on his laptop. I have not tried it becuas I am useing an SSD so I don't care if the accelerometer is not set right and I don't have the joydown problem in Archlinux.[/SIZE][/COLOR]

_**Here is the quote form DanaG that can be found on the next page.**_

> Oh yeah, that "acts like joydown is pressed": try blacklisting lis3lv02d -- that's the driver that presents the accelerometer as a joystick. By default, the calibration has the X and Y axes swapped; I had to put this in my /etc/rc.local:
jscal -u 3,1,0,2,0 /dev/input/js0 2>/dev/null || true
-------------------------------------------------------------------------------------------------------------

[COLOR="Blue"][SIZE="3"]_You can boot with the UEFI option. I will referer you to my other thread for UEFI/EFI development for the HP elitebook._[/SIZE][/COLOR]

_[SIZE="3"] Using EFI / UEFI with Linux on HP elitebook  [/SIZE]_
[http://ubuntuforums.org/showthread.php?t=1157586](http://ubuntuforums.org/showthread.php?t=1157586)

-------------------------------------------------------------------------------------------------------------
"Ubuntu" "linux" "how to" "ATI" "Catalyst" "driver" "8730" "HD3650" "FireGL" "Mobility FireGL v5700" "compatibility" "elitebook" "8530" "8530w" "8530p" "Solved" "Working" "Not Working" site:ubuntuforums.org

---

### Post by dkeats on 2009-05-26
Thanks for this. My expensive laptop has been sitting in the cupboard since Jaunty came out. Now it is working again!

One question, if Ubuntu release kernel updates, will it break anything?

regards & thanks again.
derek

---

### Post by HunterThomson on 2009-05-27
Gland to here you got it working :guitar:
It's not hard to do when you know "What" to do. But, Boy it took me a week of headaches to learn it all.


Yes, If you get a kernel update you will have to reinstall the Catalyst.
I'll add that to the stuff to the first post. Thanks for bringing it up.

OK, I edited in what to do if we get a Kernel up date that brakes the ATI Catalyst diver in the first post.

---

### Post by dkeats on 2009-05-27
Just curious if you have noticed any degradation of performance with this driver using Compiz? I am getting weird things, like clicking on Maximize and it takes 1-3 seconds to do it, resizing a window, same thing. If I drop back to Metacity and GTK window decorator, I don't get this.

---

### Post by DanaG on 2009-05-27
Hmm, that compiz-lag issue would probably be this one:  
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186?comments=all](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186?comments=all)

---

### Post by dkeats on 2009-05-27
Thank you DanaG, using the PPA ([https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill](https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill)) and upgrading to that XORG server fixed the issue.

---

### Post by HunterThomson on 2009-05-27
Wow cool I looked how to fix that but never found out how, Nice.
I think I'll write up a section for that.

I think we can solve the Wireless driver problem if I knew how to ether downgrade the to Kernel 2.6.27 or upgrade to Kernel 2.6.29. Or maybe there is a better way to fix the problem. I'll start looking into it.

---

### Post by HunterThomson on 2009-05-28
I may have found a way to get the Intel WiFi 5300 to work.

Well I was reading the bug report in launchpad and on 05/23/2009 it seems this guy installed the backports modual and it worked for him.


> I enabled Pre-released updates in the software sources application. Then I installed the package linux-backports- modules-jaunty. The wifi problem seems to have been solved. And I haven't experienced any side effects. I have now disabled the Pre-released updates and hope that all goes well. Maybe this will help others. But I'm just a user trying some stuff and no linux expert so this is all at your own risk.
This also solved another unrelated wifi issue my parents were experiencing.

I think one of two things could have been the reason this worked for him.

1> The backport driver really did the job.

2> He enabled the Pre-released updates... SO, he is now on the new Ubuntu Kernel 2.6.28-12. We are on 2.6.28-11.

I'll try just installing the new Kernel 2.6.28-12 and see if that works first. If that doesn't work, then I'll go back to 2.6.28-11 and install the backports. If that doesn't work then I'll install the new Kernel 2.6.28-12 and the backports and if I get to this point I sure hope it works.

I'll mess with it tomorrow though, because it installs a new Kernel. I don't want to deal with the ATI crap tonight.

---

### Post by HunterThomson on 2009-05-28
YES :guitar:

I FIXED the WIFI problem :D

I added a HowTo for the WiFi fix up top

I also added a HowTo for the patched Xorg install.

The is grate. Now "Everything" is working with this laptop... Well all but the fingerprint reader that to my knowledge just isn't sported in Linux yet. But, I don't care I would not use it anyway.

---

### Post by HunterThomson on 2009-06-04
I started having problems with Flash. I aredy knew there was a native 64bit adobe flash player because Archlinux uses it. However, surprise surprise, Ubuntu doesn't. Here is how you install it.

Download it form here [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

2. Unpackage it:
cd
tar xvzf libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz

3. Create a plugin directory in your $HOME (instead of a system directory):
mkdir -p .mozilla/plugins

4. Move the file to the plugin directory:
mv libflashplayer.so .mozilla/plugins

5. Restart firefox. Go to ```
about:plugins
``` to see if it’s enabled

---

### Post by HunterThomson on 2009-06-04
There seems to be a Bug. When I play a game like supertuxkart at the menu screen the computer thinks I am pressing down the whole time or something.

Do any of you have this problem?

---

### Post by HunterThomson on 2009-06-09
I got the Catalyst to work in Archlinux :guitar:

I would like to say....

The WiFi is no problem in Arch linux
Flash is no problem in Arch linux
The video game like supertuxkart in the menu screen thinking that your pressing joydown all the time... Is not a problem in Archlinux

---

### Post by HunterThomson on 2009-06-09
Boy I got a good deal on this laptop KS054UT#ABA. I got it from compusa.com AKA tigerdirect.com for $799.99 now it is selling for $1,179.99. You can still find it for $900 from web sites that I have never heard of before but who would buy form them?

---

### Post by DanaG on 2009-06-09
Oh yeah, that "acts like joydown is pressed": try blacklisting lis3lv02d -- that's the driver that presents the accelerometer as a joystick.  By default, the calibration has the X and Y axes swapped; I had to put this in my /etc/rc.local: 
jscal -u 3,1,0,2,0 /dev/input/js0 2>/dev/null || true

---

### Post by HunterThomson on 2009-06-11
> **DanaG said:**
> Oh yeah, that "acts like joydown is pressed": try blacklisting lis3lv02d -- that's the driver that presents the accelerometer as a joystick.  By default, the calibration has the X and Y axes swapped; I had to put this in my /etc/rc.local: 
jscal -u 3,1,0,2,0 /dev/input/js0 2>/dev/null || true

Ow, cool. How did you figure that out?

---

### Post by HunterThomson on 2009-06-23
Has anyone tried to get the fingerprint reader to work? I had it listed as not working. But VirtualBox has and entry for it and OpenBSD sees it as well. I bet it is supported and the linlap.com was just wrong about that too.

It is insecure though I don't think anyone cares enough to try. I know I don't. It would just be nice to list that as working :P

---

### Post by DanaG on 2009-06-23
Check here; it looks like they're not supported in the fprint project.
They mention it being hard to find standalone devices, because they're usually in laptops... but it's actually pretty easy: look on partsurfer.hp.com.  Bummer the total price comes out to thirty-something dollars, though.

[http://reactivated.net/fprint/wiki/Unsupported_devices#AuthenTec_AES2550_.26_AES2810](http://reactivated.net/fprint/wiki/Unsupported_devices#AuthenTec_AES2550_.26_AES2810)

---

### Post by HunterThomson on 2009-06-23
Right on. So the OS can see it but there really is no driver.

Owe well, just in case anyone didn't know. All you have to do to hack this thing is just dust the laptop lid or keys with graphite and then pull the fingerprints off with tape. Then swipe it through the fingerprint reader.

And, you know toughs facial-recognition scanners like on my last laptop the Lenovo Ideapad Y510...? All you have to do is have a blown up picture of the person and hold it up for the camera, Cheese :) 

((note: it may take just a couple more tweaks to get these hacks to work but for the most part it is really that easy.))

Moral of the story, use a long pass phrase or maybe facial-recognition & fingerprint reader & long pass phrase all together.

---

