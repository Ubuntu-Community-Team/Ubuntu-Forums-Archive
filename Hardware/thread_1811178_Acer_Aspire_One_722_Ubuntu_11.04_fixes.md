---
title: "Acer Aspire One 722 Ubuntu 11.04 fixes"
date: 2011-07-24
forum: Hardware
---

### Post by zzarko on 2011-07-24
About a week ago, I bought Acer Aspire One 722. After initial installation of Ubuntu 11.04, I had a couple of problems/annoyances, and I managed to solve them. This is a list of fixes that I applied:

**1. Freezing after login (with unplugged network cable)**. This is caused by wireless driver. Easy fix is to make network boot as a first option in BIOS (hold F2 after reboot). The solution for this was found on:

[http://drivard.com/2011/07/20/install-ubuntu-natty-on-acer-aspire-one-722-with-broadcom-4313-bcm4313-wireless-card/](http://drivard.com/2011/07/20/install-ubuntu-natty-on-acer-aspire-one-722-with-broadcom-4313-bcm4313-wireless-card/)

**2. Better power management**. For now, AMD's Catalyst driver doesn't support sleep mode on this netbook (computer freezes on wake-up), but open source Radeon does, and this is why I choosed it. This driver has options for reduced power consumption, but they are not activated by default. To make laptop battery lasts longer, I installed Jupiter. To do this, open terminal and type:
```
sudo su
add-apt-repository ppa:webupd8team/jupiter
apt-get update
apt-get install jupiter
```Don't close the terminal yet. Start the program (Alt+F2, type jupiter-run), and it will add itself to list of allowed programs for systray, and also to startup applications. Beacuse Jupiter (version 0.0.50) still doesn't have options for OSS Radeon driver power management, I added them manually (version 0.0.51 has this fix already included, thanks to fuduntu, so if  you have this version, there is nothing more to do for step 2). To do this, on the same terminal type:
```
mkdir -p /usr/lib/jupiter/vendors/Acer
cd /usr/lib/jupiter/vendors/Acer
gedit battery power
```When gedit opens, copy this to battery script:
```
#!/bin/bash
echo low > /sys/class/drm/card0/device/power_profile
```and this to power script:
```
#!/bin/bash
echo high > /sys/class/drm/card0/device/power_profile
```Save both scripts and close gedit. Then, type this in terminal:
```
chmod 755 battery power
```Details about this changes can be found at:

[COLOR=Blue][http://sourceforge.net/apps/mediawiki/jupiter/index.php?title=Kernel](http://sourceforge.net/apps/mediawiki/jupiter/index.php?title=Kernel)
[http://www.phoronix.com/scan.php?page=article&item=amd_radeon_powerm&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_radeon_powerm&num=1)[/COLOR] 

If you don't want to install Jupiter, but you want better power management, you should look at [sbraz]("http://ubuntuforums.org/member.php?u=1212104")'s post:
[http://ubuntuforums.org/showpost.php?p=11171013&postcount=14](http://ubuntuforums.org/showpost.php?p=11171013&postcount=14)

**3. Touchpad rotating together with screen rotating**. 722 netbook is very suitable to be used as a ebook reader, simply by rotating it's screen by 90 degrees (it comes natural to hold it as a book). Jupiter has nice options for screen rotating, but there is one slight annoyance: when you select different screen orientation, and rotate netbook accordingly, the touchpad movement remains unchanged, and it becomes difficult to navigate. This is solved with latest patches for xorg's synaptics driver. To get the updated driver, open terminal and type:
```
sudo add-apt-repository ppa:aapo-rantalainen/ppa-aaporantalainen
sudo apt-get update
sudo apt-get install xserver-xorg-input-synaptics
```After this, computer needs to be restarted. Now, screen rotation is synchronised with correct touchpad movement. Details about this can be found at:

[COLOR=Blue][http://cc.oulu.fi/~rantalai/synaptics/]("http://cc.oulu.fi/%7Erantalai/synaptics/")[/COLOR]

**4.  Headphone sensing and internal microphone**. In default Ubuntu 11.04 on 722, when you plug your headphones, the sound from speakers isn't turned off and internal microphone isn't working. To solve these issues, download and install (by double-clicking on it):
```
http://people.canonical.com/~diwic/temp/alsa-hda-dkms-acer3830tg_0.1_all.deb
```This patch is actually for another Acer laptop, but I found that it solves the same problem on 722. There are however, two caveats for this. First, external microphone still isn't working, and second, if internal microphone still isn't working, you'll need to go to Sound preferences/Input and mute and then unmute microphone (to enable internal microphone, in Sound Preferences/Hardware "Internal Audio" must be selected, and "Analog Stereo Duplex" profile. On input tab, "Internal microphone" connector should be selected, and Input volume should be adjusted to about 100%). With this fix, Skype and Google Talk/Video work just fine. Details about this fix can be found at:

[COLOR=Blue][http://bugs.launchpad.net/ubuntu/+source/linux/+bug/783582](http://bugs.launchpad.net/ubuntu/+source/linux/+bug/783582)[/COLOR]
    
**5.  CapsLock indicator**. 722 doesn't have keyboard LED indicators, which can be quite annoying, especially with CapsLock. To solve this I installed keylock indicator (by T. Scott Barnes). To do this, open terminal, and type:
```
sudo add-apt-repository ppa:tsbarnes/indicator-keylock
sudo apt-get update
sudo apt-get install indicator-keylock indicator-keylock-ubuntu-mono
```Instead of indicator-keylock-ubuntu-mono, you could use indicator-keylock-humanity or indicator-keylock-elementary (or, you could install them all). After this, open Startup Applications (from System Settings), click on Add, and enter "KeyLock Indicator" for Name and "/usr/bin/indicator-keylock" for Command (without quotes). To start indicator immediately, press Alt+F2 and enter indicator-keylock.

**6. Multitouch gestures**. 722 has a multitouch touchpad, and I found two-finger scrolling quite natural to use. You can enable it by going to Mouse/Touchpad setings (in Control Centre). Select Two-finger scrolling, and enable Horizontal scrolling.

**7. Slow Unity with Catalyst drivers**. When I tried Catalyst drivers, the Unity was slower than with OSS driver. To solve this issue, install CCSM (Compiz Config Settings Manager, it can be found in default repository), and make these changes:
```
In CCSM/Composite: disable Detect Refresh Rate
In CCSM/OpenGL: disable Sync to Vblanc and set texture filter to fast
In Catalyst Control Center in display options disable Tear Free
```After returning to OSS driver, I left the first two fixes (I didn't test if they actually make Unity faster, but they don't slow it down). I found about this fix at:

[COLOR=Blue][http://sprstacic.wordpress.com/2011/06/03/fixing-slow-unity-in-ubuntu-11-04/](http://sprstacic.wordpress.com/2011/06/03/fixing-slow-unity-in-ubuntu-11-04/)[/COLOR]

**8. Power regression in Linux kernel**. The good people at Phoronix found that Linux since version 2.6.38 on many computers has a 10-30% bigger power consumption than previous versions. They found a couple of reasons for this, but the main one was different handling of ASPM (Active-State Power Management). To solve this issue, you need to edit /etc/default/grub file. To do so, open terminal and type:
```
sudo gedit /etc/default/grub
```Now, find the line
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```and change it to
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force"
```Save the file, close gedit and type:
```
sudo update-grub
```After that, restart computer. More details about this fix can be found at:

[http://www.phoronix.com/scan.php?page=article&item=linux_2638_aspm&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_aspm&num=1)


These are the fixes I did so far. If I found more (or, if I remember something I didn't put here), I will add to this post.

Enjoy your 722,
Zarko

P.S. Thanks all for your comments!

**Still unsolved issues:**
 - External microphone doesn't work (for me)
 - Sleep function with proprietary AMD drivers - I tried latest Catalyst driver (11.8 version) and sleep function still doesn't work
 
EDIT 1: Added link for #1 and added #8.
EDIT 2: Added information about Jupiter 0.0.51 and list of unsolved issues (that I know of)
EDIT 3: Tested Catalyst 11.8, added link in #2 to [sbraz]("http://ubuntuforums.org/member.php?u=1212104")'s post about power management
EDIT 4: Corrected error in #2, jupiter-run instead of jupiter after Alt+F2 (thanks [thunderriver]("http://ubuntuforums.org/member.php?u=1308995"))

---

### Post by b1gag3 on 2011-07-26
If the first point is working, your my hero :D Searched since last week for a solution... I'll report later if this works. Thanks a lot so far!

Edit: Its amazing, it works cO Hope this lasts longer as my last success on saturday :)

---

### Post by CBMCO on 2011-07-26
Thank you zzarko for such a great post. The microphone/headphone issue was preventing me from fully enjoying my new netbook but thanks to you my AO722 works great!!!! Thanks for all the detective work. :D

---

### Post by Sterlic on 2011-07-26
> **zzarko said:**
> **1. Freezing after login (with unplugged network cable)**. This is caused by wireless driver. Easy fix is to make network boot as a first option in BIOS (hold F2 after reboot). The solution for this was found on:

[http://drivard.com/2011/07/20/install-ubuntu-natty-on-acer-aspire-one-722-with-broadcom-4313-bcm4313-wireless-card/](http://drivard.com/2011/07/20/install-ubuntu-natty-on-acer-aspire-one-722-with-broadcom-4313-bcm4313-wireless-card/)


Going off of a solution I found for the AO522, you can also fix this by adding "blacklist atl1c" to the end of /etc/modprobe.d/blacklist.conf, but this will also disable your wired ethernet connection.

---

### Post by daud566 on 2011-07-27
Thanks lots Zzarko. My keylocks indicator wasnt working too but now it is!

---

### Post by fuduntu on 2011-07-31
> **zzarko said:**
> **2. Better power management**. For now, AMD's Catalyst driver doesn't support sleep mode on this netbook (computer freezes on wake-up), but open source Radeon does, and this is why I choosed it. This driver has options for reduced power consumption, but they are not activated by default. To make laptop battery lasts longer, I installed Jupiter. To do this, open terminal and type:
```
sudo su
add-apt-repository ppa:webupd8team/jupiter
apt-get update
apt-get install jupiter
```Don't close the terminal yet. Start the program (Alt+F2, type jupiter), and it will add itself to list of allowed programs for systray, and also to startup applications. Beacuse Jupiter (version 0.0.50) still doesn't have options for OSS Radeon driver power management, they I added them manually. To do this, on the same terminal type:
```
mkdir -p /usr/lib/jupiter/vendors/Acer
cd /usr/lib/jupiter/vendors/Acer
gedit battery power
```When gedit opens, copy this to battery script:
```
#!/bin/bash
echo low > /sys/class/drm/card0/device/power_profile
```and this to power script:
```
#!/bin/bash
echo high > /sys/class/drm/card0/device/power_profile
```Save both scripts and close gedit. Then, type this in terminal:
```
chmod 755 battery power
```Details about this changes can be found at:

[COLOR=Blue][http://sourceforge.net/apps/mediawiki/jupiter/index.php?title=Kernel](http://sourceforge.net/apps/mediawiki/jupiter/index.php?title=Kernel)


I added this tweak to my list of tweaks for Jupiter 0.0.51.

---

### Post by zzarko on 2011-07-31
> **fuduntu said:**
> I added this tweak to my list of tweaks for Jupiter 0.0.51.THANKS fuduntu! One less thing to fix next time!

---

### Post by TheManaconda on 2011-08-04
Thank you so much. If it weren't for posts like this I would be left with a useless brick of electronics.

---

### Post by Luther Blissett on 2011-08-13
zzarko, just a quick thank you. It would have probably taken me 3 days to figure out all the fixes that you so neatly summarized. Please keep being so nice to the community!
Cheers,
L

---

### Post by Gobrozhogolo on 2011-08-13
this is awesome. Been a big fan of linux for a long time. Always searched the forums for solutions never been compelled to reply but you've managed  to answer so many problems for my aspire 722 decided to take the time to register and say a Big Thank you to you everything worked! except for suspend u mentioned uv managed to change the driver to radeon to fix the suspend? how do u install the open source radeon and switch it on instead of catalyst?

---

### Post by comebackdan on 2011-08-15
Zzaaaaaaaaaarko! You are awesome! Thank you for explaining the fixes for a complete newb. It really saved my Acer :D

---

### Post by zzarko on 2011-08-18
> **Gobrozhogolo said:**
> except for suspend u mentioned uv managed to change the driver to radeon to fix the suspend? how do u install the open source radeon and switch it on instead of catalyst?Open Additional Drivers, and disable proprietary ATI/AMD driver. After restarting, you should be runnung open source radeon driver.

---

### Post by azonc on 2011-08-20
> open source radeon driver.
Where is open source radeon driver? How to install?
I have A0722 follow your step fix a lot problem. I still have video problem. 
I tried install Ubuntu FGLRX and ATI driver. Both have "AMD unsupported hardware" watermark in the bottom right corner.  Installed ati driver, then run "install-fglrx-debian.sh", the watermark gone. But I lost the "Unity plugin" left side icons. Do you any solution?

Thank you for you help,
Azon Chan

---

### Post by sbraz on 2011-08-20
> **zzarko said:**
> Beacuse Jupiter (version 0.0.50) still doesn't have options for OSS Radeon driver power management, I added them manually (version 0.0.51 has this fix already included, thanks to fuduntu, so if  you have this version, there is nothing more to do for step 2). To do this, on the same terminal type:
```
mkdir -p /usr/lib/jupiter/vendors/Acer
cd /usr/lib/jupiter/vendors/Acer
gedit battery power
```When gedit opens, copy this to battery script:
```
#!/bin/bash
echo low > /sys/class/drm/card0/device/power_profile
```and this to power script:
```
#!/bin/bash
echo high > /sys/class/drm/card0/device/power_profile
```Save both scripts and close gedit. Then, type this in terminal:
```
chmod 755 battery power
```
i'd do this adding a script under /etc/pm/power.d/ which are executed everytime a charger is connected and disconnected.

this is one of my scripts applying powersaving policies to my wifi card:
```
sbraz@sbraz-netbook:/etc/pm/power.d$ cat 2_wireless-power-management 
#!/bin/sh
if on_ac_power; then
iwconfig eth1 power off
else
iwconfig eth1 power on
fi
```
i have some scripts doing similar stuff, one of them manages folding@home so it doesn't run on battery, others manage different powersaving switches.

the main advantage of using /etc/pm/power.d/* scripts is that they doesn't rely on userspace tools which might introduce bugs or use valuable ram amounts and they run even when X is not running. :)

about your microphone issues, i have an acer aspire one 721 with 10.10 and i got so fed up with pulseaudio issues that i just got rid of the whole thing in favour of esound... now everything works fine. make a backup and give it a try. :)
[http://ptspts.blogspot.com/2009/09/how-to-get-rid-of-pulseaudio-on-debian.html](http://ptspts.blogspot.com/2009/09/how-to-get-rid-of-pulseaudio-on-debian.html) (this is a bit old, it might require some changes).

---

### Post by zzarko on 2011-08-22
> **azonc said:**
> Where is open source radeon driver? How to install?
I have A0722 follow your step fix a lot problem. I still have video problem. 
I tried install Ubuntu FGLRX and ATI driver. Both have "AMD unsupported hardware" watermark in the bottom right corner.  Installed ati driver, then run "install-fglrx-debian.sh", the watermark gone. But I lost the "Unity plugin" left side icons. Do you any solution?

Thank you for you help,
Azon ChanI'm not quite sure what you did, but I guess you tried to install fglrx drivers from AMD's site, or using some script (I don't know what "install-fglrx-debian.sh" does). To enable open source drivers, you just need to uninstall AMD drivers. Detailed instructions can be found at:

[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Removing_Catalyst.2Ffglrx)

If you still don't have Unity plugin, try to enable it in ccsm (Compiz Config Settings Manager, it can be installed from Software Center). Also, maybe you switched session from Ubuntu to Ubuntu Classic (check that on your login screen).

I hope this helps. Best regards,
Zarko

---

### Post by Gobrozhogolo on 2011-08-25
So if i was to uninstall my current catalyst driver so that radeon driver kicks in can i still use the hd cord to my sound stereo or tv somehow?

---

### Post by azonc on 2011-08-27
> To enable open source drivers, you just need to uninstall AMD drivers. Detailed instructions can be found at:

[http://wiki.cchtml.com/index.php/Ubu...talyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubu...talyst.2Ffglrx)

I follow it to install. I still have "Unsupported Hardware" Watermark. Is your A0722 C-50/AMD-6270? My is C-60/AMD-6290. I can't find it on AMD web site. It may not support in 11.8 version. Anyway, Thank you so much.

---

### Post by zzarko on 2011-09-02
> **azonc said:**
> I follow it to install. I still have "Unsupported Hardware" Watermark.Then, you still have Catalyst driver. Did yoy maybe install it from Software center AND form amd's site?
> **azonc said:**
> Is your A0722 C-50/AMD-6270? My is C-60/AMD-6290. I can't find it on AMD web site. It may not support in 11.8 version. Anyway, Thank you so much.Yes, mine is C-50.C-60 just got out a few weeks ago, if I'm not mistaken.

---

### Post by thunderriver on 2011-09-02
Just a quick note on jupiter
OP mentioned "Don't close the terminal yet. Start the program (Alt+F2, type jupiter)". Well, the command is actually not jupiter, but "jupiter-run"

As for microphone, with the given instruction, I haven't been able to use the mic at acceptable volume in skype/google talk yet. Still working on it.

But above all, I am still running into system freezes even after I set Netboot as the first in the boot order. It seems that at first boot, you still need to plugin the cat-5, and once it is booted, you can unplug it.

---

### Post by vyszard on 2011-09-03
> **zzarko said:**
> **4.  Headphone sensing and internal microphone**. In default Ubuntu 11.04 on 722, when you plug your headphones, the sound from speakers isn't turned off and internal microphone isn't working. To solve these issues, download and install (by double-clicking on it):
```
http://people.canonical.com/~diwic/temp/alsa-hda-dkms-acer3830tg_0.1_all.deb
```This patch is actually for another Acer laptop, but I found that it solves the same problem on 722.

Thanks zzarko! I spent all night trying to find solution for this until I found your post!

---

### Post by zzarko on 2011-09-07
> **thunderriver said:**
> As for microphone, with the given instruction, I haven't been able to use the mic at acceptable volume in skype/google talk yet. Still working on it.

But above all, I am still running into system freezes even after I set Netboot as the first in the boot order. It seems that at first boot, you still need to plugin the cat-5, and once it is booted, you can unplug it.Regarding your problems, do you maybe have newer 722 netbook with C-60 processor, like [azonc]("http://ubuntuforums.org/member.php?u=1410043")? I didn't see the specs for that one, maybe some other hardware got changed too. I didn't have a single freeze when booting since I allowed netboot. Maybe method from post #4 could help you. Also, post #14 has a different solution to sound problems.

---

### Post by shadowalf on 2011-09-08
So, I bought have an Acer Aspire One 722 as well and put Ubuntu 10.04 on it.  I have been dealing with some of the problems you listed as well and the one that has really stumped me lately is the headphones problem.  I tried the patch you posted but it won't install correctly.

aplay -l outputs:

**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


cat /proc/asound/card0/codec#* | grep Codec outputs:

Codec: ATI R6xx HDMI

and I am using kernel version 2.6.32-33-generic

Does anybody know what I could do?  The only obvious difference between my problem and the original poster's problem seems to be the distro version.  Is there another alsamixer patch for Lucid?  Any help would be much appreciated.

---

### Post by homerhomer on 2011-09-09
Hmm, I have a 722 with a c60 and I had freezes but they went away after messing with it. 

My settings that currently work: 

1) Updating the bios *1.04 for me *
2) I'm using the proprietary AMD blob and it's working fine, I just don't have suspend or hibernate because of a bug <UGH>. Attached is the "remove watermark script" that I used.
3) In the "Main" tab  in the bios I have selected Quiet boot <enabled, Network Boot <disabled>, F12 boot menu <enabled>, D2D Recovery <enabled> and SATA Mode <AHCI MODE>. In the boot tab I also have Network Boot 1st and HDD0 : Hitachi 2nd.
4. I'm not using the Broadcom STA wireless driver from "additional Drivers"

5. I blacklisted a couple of things in /etc/modprobe.d/blacklist.conf appending the following to the end of the file. This disabled the local ethernet device "no freeze ups" and the video framebuffer. Honestly, you might want to not disable the vesafb. seems okay for me with AMD proprietary driver, bootup just isn't so pretty. 


blacklist vesafb
blacklist atl1c


** issues I've noticed
1) suspend and hibernate don't work with the AMD video driver
2) when using the microphone with skype or google vice, I need to go to "sound preferences" > "input tab" and toggle the "connector" and then it works. 

BTW - the HDMI work great with my tv, even with the audio, just make sure you change the sound device when and when not using it. 

Good luck

---

### Post by emilywind on 2011-09-18
In regards to the wireless, you can avoid the need to do anything hackish like moving netboot first if you just remove the broadcom-wl driver via the proprietary drivers menu and instead use the open source brcm80211 driver, known as brcmsmac.

The brcm driver should be available by default in Ubuntu 11.04 and be used as long as you disable the wl driver via the additional drivers menu. Cheers.

---

### Post by mrego on 2011-09-18
Hi,
most of the zzarko's fixes works for me and it's great! But I have little problem with the OSS driver. I want to use the OSS driver due it's much more faster than the proprietary one but with this I can't use Unity and (and this is the main problem for me!) can't rotate the screen. when I used the FGLRX from ATI/AMD it worked fine (and I got even more possibilities in screen resolution in Jupiter) but slower and the "unsupported..." watermark appeared..

have anybody some advice how to fix the rotation?

---

### Post by shugoshin on 2011-09-19
I just installed Ubuntu 11.04 (64-bit) on my new AO722. This thread was very useful, many thanks to all contributors.

Here is a summary from my experience that may be helpful to other users:

1. Sound issues were solved in one easy step using the Step 1 in [this page]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")

After the restart,microphone and headphone sensing started working.

2. Installing latest(11.8 ) ATI graphics driver from AMD web site caused suspend problems as mentioned before. I got help from [this page]("https://help.ubuntu.com/community/RadeonDriver") (see "Removing the proprietary fglrx driver")to carefully remove ATI driver (fglrx) and then installed back the open source Radeon driver from Synaptic Package Manager. I followed zzarko's solution for the power management issues of this driver. As I don't use Unity, I am satisfied with this solution. 

3. Wifi connection was very problematic initially. Installing the broadcom-sta-source (v 5.60.48.36-3) from Synaptic-Package-Manager solved the problems.

I am quite happy with the results: no Windows, great Ubuntu and much better performing AO722 :)

---

### Post by emilywind on 2011-09-20
Just as a tip, things are working great without extra effort in Kubuntu 11.10 Beta, and did in Ubuntu 11.10 as well but 1) Ubuntu 11.10 is less stable atm and 2) I have taken a liking to KDE because of its programs and the ability to easily turn off desktop effects for when playing games (shift+alt+f12 - yes please :D ).

But yeah, the hardware in this laptop is quite new and as such the next generation of up-to-date Linux distros are where we are going to find a lot of fixes already done, and properly, because they have been fixed in upstream software. Not sure about things in regards to the Catalyst drivers though, as sadly they are not part of the changing open source world. Cheers. :)

---

### Post by MarvinVzla on 2011-09-22
Hello, before anything thank you zzarco I am new in ubuntu so is kind of hard to change my windows mind but I am enjoin it, I found this problem after I wrote in the terminal gedit battery power and the laptop does not wake up from suspend
(gedit:3412): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.BV241V': No such file or directory

(gedit:3412): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

Thank you for your help

---

### Post by emilywind on 2011-09-25
> **MarvinVzla said:**
> Hello, before anything thank you zzarco I am new in ubuntu so is kind of hard to change my windows mind but I am enjoin it, I found this problem after I wrote in the terminal gedit battery power and the laptop does not wake up from suspend
(gedit:3412): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.BV241V': No such file or directory

(gedit:3412): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

Thank you for your help
The gedit error should be a non-issue related to running it as root, and suspend not working is an issue with the proprietary driver from the additional drivers dialogue. Suspend works fine with the open source driver, however.

---

### Post by MarvinVzla on 2011-09-28
> **emilywind said:**
> The gedit error should be a non-issue related to running it as root, and suspend not working is an issue with the proprietary driver from the additional drivers dialogue. Suspend works fine with the open source driver, however.

So What should I do?

---

### Post by zzarko on 2011-09-28
> **MarvinVzla said:**
> Hello, before anything thank you zzarco I am new in ubuntu so is kind of hard to change my windows mind but I am enjoin it, I found this problem after I wrote in the terminal gedit battery power and the laptop does not wake up from suspend
(gedit:3412): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.BV241V': No such file or directory

(gedit:3412): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

Thank you for your help
Well, I don't know why this warning appeared, but by looking at it, I think it shouldn't be connected witn creating battery and power files. When you type in terminal:
```
ls -l /usr/lib/jupiter/vendors/Acer/
```do you get something like:
```
rwxr-xr-x battery
rwxr-xr-x power
```If yes, that's how it should be. Did you try to close Jupiter, and thes suspend/resume (just to check if Jupiter is the problem, but I doubt that)?
Did you install AMD's drivers (fglrx)? They don't work with suspend/resume. If yes, uninstall them if you want that functionality.
Do you maybe have a newer C-60 netbook? If yes, see the posts of C-60 version owners, as some hardware is obviously different (I don't have that one and I'm unable to check fixes on that version).

On a side note, many here mentioned AMD unsupported watermark when running fglrx. I tried both version from repository and current stable from AMD's site (11.8, I think) and I haven't seen this watermark. What version did you install?

---

### Post by MarvinVzla on 2011-09-28
Thank you, I found what was the problem, and It was working with the ATI/AMD proprietary FGLRX graphics driver, and as soon I uninstalled everything start to work fine

---

### Post by MarvinVzla on 2011-09-29
Now I found another problem and It is that when I conect the HDMI to my TV to see I just got Picture and no sound, have you find anything like that? I all ready check the audio setup and put in the output the HDMI preference but nothing happens, I would keep cheking out what could be the solution!, thank you for all your help :P,

---

### Post by zzarko on 2011-09-30
Well, HDMI is something I didn't test, as I don't have a TV in my home (by choice, I hate the damn thing). You should try to check the thread from where I found about audio fix, maybe someone there could help you.

---

### Post by emilywind on 2011-10-01
> **zzarko said:**
> On a side note, many here mentioned AMD unsupported watermark when running fglrx. I tried both version from repository and current stable from AMD's site (11.8, I think) and I haven't seen this watermark. What version did you install?
I got that watermark as well, but I have one of the laptops with a C-60 APU, and from what I can find it just came out in August so that may affect the driver's support for it. Going to try the recently released 11.9 fglrx driver and see how that works though.

---

### Post by emilywind on 2011-10-01
> **shadowalf said:**
> So, I bought have an Acer Aspire One 722 as well and put Ubuntu 10.04 on it.  I have been dealing with some of the problems you listed as well and the one that has really stumped me lately is the headphones problem.  I tried the patch you posted but it won't install correctly.

aplay -l outputs:

**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


cat /proc/asound/card0/codec#* | grep Codec outputs:

Codec: ATI R6xx HDMI

and I am using kernel version 2.6.32-33-generic

Does anybody know what I could do?  The only obvious difference between my problem and the original poster's problem seems to be the distro version.  Is there another alsamixer patch for Lucid?  Any help would be much appreciated.
Just follow the instructions which have you updating alsa. In the new versions of ALSA, proper supported has been added for the card in the 722 and it all works perfectly fine. It all works fine for me without tinkering in Kubuntu 11.10, for example.

[http://ubuntuforums.org/showpost.php?p=11264661&postcount=26](http://ubuntuforums.org/showpost.php?p=11264661&postcount=26)

That has a good sound solution for 11.04. Cheers. :)

---

### Post by casainho on 2011-10-05
Hello :-)

I just documented a few tweaks as undervoltage and fan control on Aspire One 522 which should be the same hardware as 722.

Please, document your findings here: [https://help.ubuntu.com/community/AspireOne522](https://help.ubuntu.com/community/AspireOne522)

---

### Post by Elwro on 2011-10-10
I installed 11.04. I compiled the wifi drivers and wifi is working now. But I cannot set the proper screen resolution - 1024x600 is the highest I can go! Doesn't matter whether I use Unity or Classic, doesn't matter whether I use the proprietary or open source driver. I'd really appreciate any tips!

---

### Post by casainho on 2011-10-10
> **Elwro said:**
> I installed 11.04. I compiled the wifi drivers and wifi is working now. But I cannot set the proper screen resolution - 1024x600 is the highest I can go! Doesn't matter whether I use Unity or Classic, doesn't matter whether I use the proprietary or open source driver. I'd really appreciate any tips!

I am sorry to say that probably you just bought the 1024x600 version instead of the 1366x768!! ([read here an example]("http://www.hwupgrade.it/forum/showthread.php?p=35907543"))

My first Aspire One 522 was a version from UK and just had 1024x600 and I had to sent it back to shop because they told on shop it was 1280x720. A few days later I bought the version from Spain and I got the 1280x720 version :-)

Could you please tell us the part number of your Acer? you can find it on the paper box.

My part number is: "Acer Aspire ONE 522-C5Dkk LU.SES0D.132"

---

### Post by Elwro on 2011-10-10
Oh boy. You seem to be 100% correct. I just checked Windows 7, which I dual boot, and it also recognizes 1024x600 as a maximum.

My number is 722-C52kk LU.SFT02.117.

Now I don't even know why I thought it has a bigger resolution, it's not even written on the box.

Thanks for making things clear for me!

---

### Post by casainho on 2011-10-10
> **Elwro said:**
> 
My number is 722-C52kk LU.SFT02.117.

Searching on google points to a site where says it's 1024.[/QUOTE]

> **Elwro said:**
> 
Now I don't even know why I thought it has a bigger resolution, it's not even written on the box.

Thanks for making things clear for me!

I bought the 1024x600 on Pixmania online shop and they made the mistake to say it was 1280x720, because of that, I did return it and got my money back! After I bought from another online shop that provided the Serial Number of the product so I verified and trusted it was 1280x720.

Maybe you can do the same... return and get a correct one! I had an Acer Aspire One 110 that is 1024x600... and there is an HUGE difference for the 1280x720!!

---

### Post by Elwro on 2011-10-10
> **casainho said:**
> Maybe you can do the same... return and get a correct one!Unfortunately, I can't do that - it seems I tricked myself and no one else is to blame. That was an extremely cheap offer, and now I know why ;)

Eh, it's still usable. I'll be using it for quick LaTeX jobs on my presentations (in Emacs), which will be compiled to PDFs and for showing these presentations using the Adobe reader. It'll do :-)

Still, thanks again, I'm a bit ashamed to say this but I wasted at least 3 hours downloading and compiling different driver versions...

---

### Post by scootaloo on 2011-10-10
I tried the to remove the watermark, but I ended up bricking my Ubuntu install. If I try a regular boot, all I get now is a terminal. Reduced graphics mode works fine. Much help would be appreciated.

---

### Post by demeter on 2011-10-11
yes, thank you so much for posting the fix about freezing after log in, have been worrying about it since I installed natty on my lenovo G475 a few days ago. now the only thing that isnt working is the internal microphone, as the headphones works just fine. also why is that on emphaty the video call and the audio call options are not accessible? I installed cheese and the built in camera works. also, about the power management that you posted, would it work on G475? as ive noticed, I have less battery power on natty compared to as Im on Win 7, yes I'm  on dual boot....once again thank you very much....

---

### Post by zzarko on 2011-10-11
> **scootaloo said:**
> I tried the to remove the watermark, but I ended up bricking my Ubuntu install. If I try a regular boot, all I get now is a terminal. Reduced graphics mode works fine. Much help would be appreciated.
Start computer in reduced graphics mode. If you installed fglrx drivers form repository, just deactivate them via Additional hardware. If you install them using latest version from AMD's site, follow instructions for removing fglrx drivers from:
[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Removing_Catalyst.2Ffglrx)
After one of these procedures, you should have open source driver active again.

---

### Post by orewacrazy on 2011-10-14
Thanks, :D

---

### Post by zzarko on 2011-10-16
I'm planning to make a new thread for 11.10. But, right now, after update from 11.04 to 11.10, I'm still trying to make my wireless to work. My 722 has Broadcom 4313 chip, and I didn't manage to make it work nor with OSS, nor with proprietary drivers (I was using OSS drivers in 11.04). Ahyone had success with this?

EDIT: Success! I just don't know what of several things I tried enabled it...

---

### Post by Anool on 2011-10-17
Hey zzarko and others,
You guys saved my day - and AO722. Many thanks.

Anool

---

### Post by scootaloo on 2011-10-17
> **zzarko said:**
> Start computer in reduced graphics mode. If you installed fglrx drivers form repository, just deactivate them via Additional hardware. If you install them using latest version from AMD's site, follow instructions for removing fglrx drivers from:
[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Removing_Catalyst.2Ffglrx)
After one of these procedures, you should have open source driver active again.

Thanks, that allowed me to boot in normal mode. I reinstalled the AMD drivers per the instructions on their website. For some reason, the open source graphics restricts me to only 800 x 600.

However, I still can't figure out how to remove the watermark without bricking the graphics again. I ran the script that was found earlier in this thread. :\

---

### Post by brub2 on 2011-10-17
Just my 2¢... I have experimented with 11.04 (Mint 11) but 10.10 (Mint 10) is really a better choice for this laptop, at least if you want the Catalyst driver. Also, you will need the proprietary wi-fi driver. But you get a better battery life. Also, suspend and resume WORK out of the box with Catalyst driver (but not with the open driver)!!! There is a watermark with the proposed one, but it's easy to install the latest version instead.

---

### Post by mrego on 2011-10-22
> I'm planning to make a new thread for 11.10.

Did you (or anybody else) make the new thread for 11.10? I didn't find any..
thx

---

### Post by casainho on 2011-10-22
> **mrego said:**
> Did you (or anybody else) make the new thread for 11.10? I didn't find any..
thx

I am running on 11.10 (did update from 11.04) and looks like the problems/solutions are just the same!

I think the wiki page is the best place to document: [https://help.ubuntu.com/community/AspireOne522](https://help.ubuntu.com/community/AspireOne522)

---

### Post by Alexomnom on 2011-10-25
> **zzarko said:**
> I'm planning to make a new thread for 11.10. But, right now, after update from 11.04 to 11.10, I'm still trying to make my wireless to work. My 722 has Broadcom 4313 chip, and I didn't manage to make it work nor with OSS, nor with proprietary drivers (I was using OSS drivers in 11.04). Ahyone had success with this?

EDIT: Success! I just don't know what of several things I tried enabled it...


I uninstalled the Broadcom STA-WLAN Driver and booted from "Atheros Network" and it really seem to work. Maybe it will work for you, too.
It works for me since 3,5 days.

---

### Post by Rubykuby on 2011-11-08
I've just got a new AO722 today. I've installed Ubuntu 11.10 after going through the install of the abomination that is Windows 7. Nevertheless, I haven't been able to sit down with the laptop and really use it on Ubuntu just yet. What fixes as seen in the first post are actually applicable to Ubuntu 11.10? Cheers.

---

### Post by hitime on 2011-11-08
Hey all,

I and my laptop have been following this thread intently, we really appreciate all the help.  There is one thing I can not get fully going tho and that is full 720p video playback with no chop (mkv, avi, mp4 -- h.264)... I have the latest proprietary drivers installed on Ubuntu 11.10 x64 with 4 gigs of ram.  Xine seems to be the the best so far, but the CPUs jump to almost full load and doesn't seem to be utilizing the GPU.  Have been testing with PowerTop.  Any help would be appreciated.

Thanks,
Derek

BTW another helpful tip, if you want to do a fresh install of 11.10 from USB use Yumi to load it onto the pendrive and the install will work (I read that 11.10 install direct was broke on the wiki)

---

### Post by shugoshin on 2011-11-12
Hi, I am wondering whether anyone else experience webcam problem with AO722. The webcam on my machine is recognized as ```
Bus 002 Device 002: ID 04f2:b209 Chicony Electronics Co., Ltd 
```. Running cheese shows just a black window. Running it VLC using the command ```
vlc v4l2:///dev/video0
``` returns ```
VLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x917e2fc] main interface error: no suitable interface module
[0x90d5914] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x90d5914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x917e5d4] [rc] lua interface: Listening on host "*console".
VLC media player 1.1.9 The Luggage
Remote control interface initialized. Type `help' for help.

```
Does anyone have any suggestion?

---

### Post by LewisTM on 2011-11-18
Thanks zzarko for all those tips! Just applied them to an install of Xubuntu 11.10 and couldn't be happier.
Running xfwm4 as window manager (no Compiz, too slow) and the opensource drivers. The machine is extremely responsive.
When compared side by side with the same machine running Win7, the netbook boots 10 seconds quicker and the apps (compared Firefox and LibreOffice) come up MUCH faster. Everything in Windows seems so sluggish.

A few more comments:
1) Dont' forget to install the preload daemon to speed up your machine.
2) The patched mplayer referred to in [this forum]("http://forum.notebookreview.com/linux-compatibility-software/546342-linux-amd-fusion-4.html") (#35) allows me to watch smooth 720p in Smplayer. Also, upping the performance with Jupiter helps.
3) Xfce's volume daemon doesn't work and the volume keys are inactive. You can disable xfce4-volumed from starting up and bind the Fn-Up/Down to amixer commands instead.
4)Making the microphone work in Skype is still tricky. Tried to uninstall Pulseaudio and run on pure ALSA but then the microphone produces horrible noise.
5)Package gpointing-device-settings works well in Xfce to enable two-finger scrolling.
5)With Jupiter set to conservative settings plus Xfce power manager set to blank the screen and spin down the disk on idle time, your power consumption should be equivalent to the Windows version.
6) I found that not only is Compiz slow, it overtaxes the GPU and drains the battery. Better stick with a simpler window manager (Xfwm4, Mutter, Openbox) and get some serious computing done.

Hope this helps or motivates someone!
A happy Xubuntu netbook user.

---

### Post by emilywind on 2011-11-19
> **LewisTM said:**
> Thanks zzarko for all those tips! Just applied them to an install of Xubuntu 11.10 and couldn't be happier.
Running xfwm4 as window manager (no Compiz, too slow) and the opensource drivers. The machine is extremely responsive.
When compared side by side with the same machine running Win7, the netbook boots 10 seconds quicker and the apps (compared Firefox and LibreOffice) come up MUCH faster. Everything in Windows seems so sluggish.

A few more comments:
1) Dont' forget to install the preload daemon to speed up your machine.
2) The patched mplayer referred to in [this forum]("http://forum.notebookreview.com/linux-compatibility-software/546342-linux-amd-fusion-4.html") (#35) allows me to watch smooth 720p in Smplayer. Also, upping the performance with Jupiter helps.
3) Xfce's volume daemon doesn't work and the volume keys are inactive. You can disable xfce4-volumed from starting up and bind the Fn-Up/Down to amixer commands instead.
4)Making the microphone work in Skype is still tricky. Tried to uninstall Pulseaudio and run on pure ALSA but then the microphone produces horrible noise.
5)Package gpointing-device-settings works well in Xfce to enable two-finger scrolling.
5)With Jupiter set to conservative settings plus Xfce power manager set to blank the screen and spin down the disk on idle time, your power consumption should be equivalent to the Windows version.
6) I found that not only is Compiz slow, it overtaxes the GPU and drains the battery. Better stick with a simpler window manager (Xfwm4, Mutter, Openbox) and get some serious computing done.

Hope this helps or motivates someone!
A happy Xubuntu netbook user.

Do you get around 7-8 hours of battery life? The most I have gotten with the open source drivers is around 4 (even with a simple Openbox set up in Arch Linux), sadly. :( If they gave more I would happily remove Windows 7 entirely and use Linux and them all the time. >.>

EDIT: I have to partially take that back about the Win 7 bit, because I have not actually used the Windows 7 install on it in ages despite leaving it on for the suspend ability. xD

---

### Post by LewisTM on 2011-11-19
I've managed 6h25min on the Acer in Xubuntu 11.10. Decent for me.

Key settings:
1. Followed the OP's directions. The GRUB ASPM trick and Jupiter are critical.
2. Dimmed the display 50% on battery.
3. Set to spin down disks on idle.
4. Set my HDD filesystems in my /etc/fstab to disable journaling of acces times with the *noatime* switch. This prevents the disk from being constantly written.
5. Disabled Bluetooth

I also found that the Win7 claim of 7 hours is a bit of a stretch. Reviewers obtained 6h53 with light web browsing. I found that power consumption increases a lot when you start launching more programs, perhaps because Windows is heavier on the processor and disk. 

Cheers!

---

### Post by danieljeronimo on 2011-11-21
I would just like to Thank Zzarko and everyone in this thread. I'm running Linux Mint 11, but almost every tip here has worked just fine. I still have problems with the AMD drivers, as it seems impossible to get the HD acceleration running on the C-60 processor of my machine, but what can I do except waiting for new drivers to come out?

---

### Post by sbraz on 2011-11-21
> **danieljeronimo said:**
> but what can I do except waiting for new drivers to come out?
unfortunately nothing exept writing in amd's official support forums.

proprietary driver => proprietary rules :\

---

### Post by emilywind on 2011-11-21
Okay, I think what I was missing from Jupiter was the cpufreq stuff. For those who are interested, you can bypass the need to install Jupiter and have automagical better power management with the open source drivers on battery by doing the following.

[Download this script](http://pastie.org/2905074) then copy/move it to /etc/pm/power.d/1-apu and give it executable permissions via sudo chmod +x /etc/pm/power.d/1-apu.

It will set things to use dynamic power management for the video and ondemand for the cpu when plugged in, and switch to low profile and powersave respectively when on battery.

This is preferred for me since I would rather not install a GTK mono program such as Jupiter on my Kubuntu, plus this has the niceness of transparency and automation. If Jupiter does anything else important that I should add to that script, let me know.

EDIT: Removed steps which I found were unrequired and updated the script to change cpufreq details without needing cpufreq-utils. Also includes an extra power management option recommended by lesswatts.org. Cheers.

UPDATE: That script should more than suffice for people who share a lack of interest in using mono gtk software to control their power settings. A test of Fuduntu with Jupiter on powersave compared to my typical Kubuntu install (no effects in KDE and using plastic theme) both reported the same; around 5+ hours of battery. Using Kubuntu for taking notes via KWord in class gave real world support to the claim as well, as I only lost about 20% battery in 1:20 or so.

---

### Post by jessedyer on 2011-11-30
Zzarok, thank you so much for this post!  I used this for Linux Mint, and the only thing that I had to change was the method for installing Jupiter ([http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html](http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html))

---

### Post by zzarko on 2011-12-01
Unfortunately, my work schedule still doesn't allow me to sit down and test all fixes for vanilla 11.10 (it took me a few days of searching and testing for the original post). I'm currently quite annoyed by several bugs in 11.10 (I reported them, or joined watch list if they were already reported, but it seems that all canonical developers are making new Unity features, but almost none is fixing existing bugs) and I'm thinking about Mint... Anyway, I hope I will have the free time before NY.

---

### Post by zzarko on 2011-12-04
Did any of you experience hard disk clicks when running on battery? On my 722 they were regular, about once in 10 seconds, and for a long time I assumed this to be normal. And today I looked at:
[https://wiki.ubuntu.com/DanielHahler/Bug59695](https://wiki.ubuntu.com/DanielHahler/Bug59695)
It seems that Ubuntu was trying to spin-down HD too often, and because the HD was in use, it was spinned-up immediatly after. I applied the proposed fix (hdparm -B 254 /dev/sda) and the clicks were gone! I just hope this didn't damage my hard disk too much...

---

### Post by fuduntu on 2011-12-04
> **emilywind said:**
> UPDATE: That script should more than suffice for people who share a lack of interest in using mono gtk software to control their power settings. A test of Fuduntu with Jupiter on powersave compared to my typical Kubuntu install (no effects in KDE and using plastic theme) both reported the same; around 5+ hours of battery. Using Kubuntu for taking notes via KWord in class gave real world support to the claim as well, as I only lost about 20% battery in 1:20 or so.

No it won't, it's missing more than half of the power saving tweaks found in Jupiter.

Jupiter's Mono GTK applet is just a configuration and reporting tool.  You can delete it from the filesystem and Jupiter will still function (you just won't be able to configure it easily).

I'm confident that if you measure the actual run time of Kubuntu with your script vs Fuduntu with Jupiter you'll find that Fuduntu will by far outlast Kubuntu.

---

### Post by emilywind on 2011-12-04
> **fuduntu said:**
> No it won't, it's missing more than half of the power saving tweaks found in Jupiter.

Jupiter's Mono GTK applet is just a configuration and reporting tool.  You can delete it from the filesystem and Jupiter will still function (you just won't be able to configure it easily).

I'm confident that if you measure the actual run time of Kubuntu with your script vs Fuduntu with Jupiter you'll find that Fuduntu will by far outlast Kubuntu.
Okay I shall look at the source and add the missing tweaks then. Thanks for the heads up. :)

---

### Post by fuduntu on 2011-12-04
> **emilywind said:**
> Okay I shall look at the source and add the missing tweaks then. Thanks for the heads up. :)

Meh, that or you could just use Jupiter which has already has a few years of maturity under its belt.

---

### Post by emilywind on 2011-12-05
> **fuduntu said:**
> Meh, that or you could just use Jupiter which has already has a few years of maturity under its belt.
Mono and gtk dependencies aside, it still did not even properly run under Kubuntu as it had errors trying to run. Besides, this also uses existing freedesktop standards ([http://pm-utils.freedesktop.org/wiki/](http://pm-utils.freedesktop.org/wiki/)), which also has some years of maturity behind it.

For the interested, the other tweaks for /etc/power.d/ .

[http://pastie.org/2967787](http://pastie.org/2967787)

- Save as /etc/power.d/2-misc and give permission to execute.

Also, an updated /etc/power.d/1-apu

[http://pastie.org/2967818](http://pastie.org/2967818)

---

### Post by fuduntu on 2011-12-05
> **emilywind said:**
> Mono and gtk dependencies aside, it still did not even properly run under Kubuntu as it had errors trying to run. Besides, this also uses existing freedesktop standards ([http://pm-utils.freedesktop.org/wiki/](http://pm-utils.freedesktop.org/wiki/)), which also has some years of maturity behind it.

For the interested, the other tweaks for /etc/power.d/ .

[http://pastie.org/2967787](http://pastie.org/2967787)

- Save as /etc/power.d/2-misc and give permission to execute.

Also, an updated /etc/power.d/1-apu

[http://pastie.org/2967818](http://pastie.org/2967818)

Uhh, Jupiter plugs into power.d, that's how it works.  I also know of several people that use it under kubuntu without any issue.

Good luck supporting this.

---

### Post by LewisTM on 2011-12-05
> **zzarko said:**
> Did any of you experience hard disk clicks when running on battery? On my 722 they were regular, about once in 10 seconds, and for a long time I assumed this to be normal. And today I looked at:
[https://wiki.ubuntu.com/DanielHahler/Bug59695](https://wiki.ubuntu.com/DanielHahler/Bug59695)
It seems that Ubuntu was trying to spin-down HD too often, and because the HD was in use, it was spinned-up immediatly after. I applied the proposed fix (hdparm -B 254 /dev/sda) and the clicks were gone! I just hope this didn't damage my hard disk too much...
zzarko, you did it again!

I placed the command in my rc.local file. Now my netbook is not only ninja quick, it's also ninja silent.

How this fix will impact power consumption remains to be determined. The proper power management of the hard disk could be a game changer. If we could prevent Ubuntu from needlessly accessing the HDD, we could take advantage of the aggressive power management settings.

Wonder if the (many) tweaks found [here]("http://en.dogeno.us/2010/01/karmic-with-solid-state-disk-how-to-optimize-ubuntu-for-ssd/") for SDD could also apply and benefit this netbook.

---

### Post by emilywind on 2011-12-06
> **fuduntu said:**
> Uhh, Jupiter plugs into power.d, that's how it works.  I also know of several people that use it under kubuntu without any issue.

Good luck supporting this.
When use KDE I prefer KDE and QT apps; simple as.

Furthermore, Linux is quintessentially about choice, and I am choosing a lightweight, gui-free solution. These scripts are for others who wish to do the same and to know what is happening behind the scenes. I have no intention to start/maintain a project out of simple scripts.

Why do you have seemingly have inane issues with me choosing/providing a slim power management option?

---

### Post by fuduntu on 2011-12-06
> **emilywind said:**
> When use KDE I prefer KDE and QT apps; simple as.

Furthermore, Linux is quintessentially about choice, and I am choosing a lightweight, gui-free solution. These scripts are for others who wish to do the same and to know what is happening behind the scenes. I have no intention to start/maintain a project out of simple scripts.

Why do you have seemingly have inane issues with me choosing/providing a slim power management option?

.. because your time would have been better spent working on improving the existing tool, rather than forking it and maintaining a fork.

The problem you have created is that you now have scripts in a forum that you have admitted that you won't support which reference an upstream project (which is required per the GPL) which is exactly where users of this script will go for help a year from now when you have long since gone on to something else and they need help.

I don't have any problem with you choosing what you are calling a "slim power management option".  I do have a problem with your implication that it is an alternative option when you said yourself in this very reply that you have no intention of turning it into a project and supporting it long term.  Once you paste them in public view, they are no longer "just simple scripts".  ;)

So, as I said, good luck supporting this. :D

---

### Post by dflt on 2011-12-17
so, how can I get the 1333mhz turbo boost? I've tried k10ctl and tpc but I get &quot;not supported&quot; and nothing changes.

---

### Post by gnemo on 2011-12-19
> **fuduntu said:**
> .. because your time would have been better spent working on improving the existing tool, rather than forking it and maintaining a fork.

Fuduntu, I thank you sincerely for the work you have done in creating and maintaining this useful tool. Nice work!

That said, Emilywind made it clear why she preferred to roll her own solution. She didn't like your toolkit of choice, and wanted a lighter solution that used less resources. It really isn't up to you to decide what is the best use of *her* time, you know, nor to dictate to anyone else the terms on which they are allowed to create or not create something of their own.

I can quite understand that you may be burned out from the work of creating and maintaining your own software, and would like additional help. I'm sure there are people out there who would help you if you asked them. But being rather rude to helpful and creative people who showed up on this thread (Emilywind) is not the way to get the help you want.

I now I hope this thread goes back to the very positive tone it has had right up until you got rather upset over Emilywind choosing to take her own direction and find her own solution, rather than use the one you provided.

I have recently become the owner of one of these nice little netbooks (Aspire One, A0722), and look forward to freeing it from the default Windows 7 OS and getting Linux humming nicely on it.

-Gnemo

---

### Post by fuduntu on 2011-12-20
> **gnemo said:**
> Fuduntu, I thank you sincerely for the work you have done in creating and maintaining this useful tool. Nice work!

Thanks.

> **gnemo said:**
>  That said, Emilywind made it clear why she preferred to roll her own solution. She didn't like your toolkit of choice, and wanted a lighter solution that used less resources. It really isn't up to you to decide what is the best use of *her* time, you know, nor to dictate to anyone else the terms on which they are allowed to create or not create something of their own.

I didn't dictate terms.  I simply complained.  It is a free internet. ;)

> **gnemo said:**
> I can quite understand that you may be burned out from the work of creating and maintaining your own software, and would like additional help. I'm sure there are people out there who would help you if you asked them. But being rather rude to helpful and creative people who showed up on this thread (Emilywind) is not the way to get the help you want.

I'm not burned out, nor was I rude.  I wouldn't really call taking something and chopping parts off and calling it your own - "creative", but that's just my opinion.  If you'll re-read my comment I didn't complain that it was forked.  I complained that it was called an alternative.  It is hardly worthy of being called anything other than a hack job much less an "alternative", but I was trying to be kind.

> **gnemo said:**
> I now I hope this thread goes back to the very positive tone it has had right up until you got rather upset over Emilywind choosing to take her own direction and find her own solution, rather than use the one you provided.

You read too much emotion into a post where there was none.  It isn't a case of "upset", it is a case of noticing something being called something that it is not and commenting on it.  I do have the right to comment on whatever I want.  That being said, I stand by the implications made in my original comment.

If you want to take it further, I can call it a GPL violation because it uses my source and does not include the proper licensing information.

If I wanted to be rude, I could have hit the report button and had it erased for violating the license I released Jupiter under.

.. but I didn't.

---

### Post by xterminus on 2011-12-24
> **Rubykuby said:**
> I've just got a new AO722 today. I've installed Ubuntu 11.10 after going through the install of the abomination that is Windows 7. Nevertheless, I haven't been able to sit down with the laptop and really use it on Ubuntu just yet. What fixes as seen in the first post are actually applicable to Ubuntu 11.10? Cheers.

I just got my AO722 the other week.  Installed 11.10 on it after fooling with Win7 for a total of maybe 10 minutes. :)  As far as I can tell...

1.  You still need to do the BIOS boot re-ordering so it tries to Network boot first.  It's not much of a hassle to enable and deal with, I think it adds maybe 1 second to the boot process anyway.  

If you don't need the ethernet port, removing the Atheros driver REALLY stabilizes things.  eg:

    /etc/modprobe.d/blacklist-atheros.conf
```

# Additional Stuff for 4313 Driver
blacklist bcma
blacklist brcmfmac
blacklist brcmsmac

# Blacklist ethernet card, elminate lockups
blacklist atl1c

```

By disabling the ethernet card when I don't need it (which is pretty much never), I got resume/hibernate to work flawlessly.

You'll notice I disabled bcma, etc.  The stock kernel driver seems to get in the way of the sta driver, which I prefer.  Mostly because while the stock driver works great on 802.11a/b/g networks, it totally mucks up on 802.11n connections and I get a lot of packetloss/dropped connections.  The STA driver works fine on those high-speed wifi connections.

2. I don't use or like jupiter, but I have a few scripts I drop in /etc/pm/power.d that do the same thing.  (they aren't AO722 or acer specific, they just fool with the governor, laptop-mode settings, etc, etc) There really isn't anything in jupiter that I know of acer specific other than the provided scripts in the above post.  In any case, if you don't want to play around in /etc/pm/power.d, jupiter is probably a good idea.

3. I couldn't get the screen rotating in sync with the touchpad to work properly at all.  The ppa for the synaptics driver causes a failure to even load the touchpad driver.  I had to plug in a usb mouse, remove the new synaptics xorg driver, remove the ppa, install the old driver, and reboot to get working again.  So I'd avoid that ppa for now.

4. Alsa/Pulseaudio jack sensing works fine out of the box so far, no fix needed.

5. Capslock indicator is probably a good idea.  I use the [gnome-shell equivalent](https://extensions.gnome.org/extension/36/lock-keys/).

6. Multitouch (two finger scrolling) is okay if you like it.  The AO722 has a "scroll area" on the touchpad anyway, which I think is more convenient.

7. The Catalyst video drivers (the proprietary ones) did NOT work well for me at all.  They were prone to cause wierd artifacts on the screen, crash X at random, and other such fun.  That and sleeping/hibernation is impossible with them too.  Stick with the default radeon x server/driver.  I'm not a gamer so super-performance in my video isn't really needed.  480p videos look fine.  Haven't tried anything more (yet).

8. Power regression notes for grub were a good idea.

---

### Post by hitime on 2011-12-30
For some reason I can not get the microphone working on my system, I'm running Xubuntu 11.10 with pulseaudio.  I'm tring to use Audacity to do some test recording with no luck.  The line seems to get static when selecting Conexiant for audio in (can see it in the monitor) but nothing external at all.  I'm not seeing anything in the mixer(s) either.  Any help would be appreciated.

Thanks,
hitime

---

### Post by shugoshin on 2011-12-30
> **hitime said:**
> For some reason I can not get the microphone working on my system, I'm running Xubuntu 11.10 with pulseaudio.  I'm tring to use Audacity to do some test recording with no luck.  The line seems to get static when selecting Conexiant for audio in (can see it in the monitor) but nothing external at all.  I'm not seeing anything in the mixer(s) either.  Any help would be appreciated.

Thanks,
hitime

Try installing kernel 3.1.4. This solved my problem with Lubuntu (and recently with Linux Mint LXDE 11) With this kernel if you run ```
alsamixer
``` in terminal you may see three options for capture device. Selecting one of them should work.

---

### Post by dwaszuk on 2012-01-02
Hi, I'm stucked trying to install Ubuntu in a brand new Aspire One 722. I've tried with versions 11.04 and 11.10 but it hangs at startup (just after the logo with the buttons that change colors below it).

I've created the usb with both 'Startup Disk Creator' and 'Unetbootin' with the same result. Also tried with network as first boot option and usb as second, without luck.

I'm sorry for not giving more info, but I don't know what else I can do.

Any help will be appreciated.

Happy new year,

---

### Post by casainho on 2012-01-02
> **dwaszuk said:**
> Also tried with network as first boot option and usb as second, without luck.

And are you sure network were the first to boot (and fail, skipping to next boot device, the USB)?

---

### Post by zzarko on 2012-01-02
> **dwaszuk said:**
> Hi, I'm stucked trying to install Ubuntu in a brand new Aspire One 722...I'm not sure which F key does this, but after inserting the USB, try to find the command line for starting Ubuntu, and before starting, delete "quiet" and "splash" keywords from it. Then, send last few lines that are displayed after freezing. Also, which 722 do you have (C-50, C-60, something else)?

---

### Post by dwaszuk on 2012-01-02
> **casainho said:**
> And are you sure network were the first to boot (and fail, skipping to next boot device, the USB)?

I didn't let the network option boot... is it necessary? I've thought it was just a matter of order in settings...

---

### Post by dwaszuk on 2012-01-02
> **zzarko said:**
> I'm not sure which F key does this, but after inserting the USB, try to find the command line for starting Ubuntu, and before starting, delete "quiet" and "splash" keywords from it. Then, send last few lines that are displayed after freezing. Also, which 722 do you have (C-50, C-60, something else)?

I'm sorry for not mentioning it.

It's an AMD Dual-core Processor C60... I'm trying to find the correct F function. As soon as I get it I'll let you know. But first I will try with what casainho told of letting network boot and fail..

---

### Post by dwaszuk on 2012-01-02
Well finally after letting the network boot to fail and booting from usb, it let me start with the process... Sorry, I didn't understand that it was necessary..

Thank you for your replies, casainho and zzarko. I'll continue with the installation taking into account what is posted in this forum.

Regards.

---

### Post by Fo2adZz on 2012-01-04
[SIZE=4]I really want to thank everyone for the valuable information it helped alot. I have an Acer 722 with APU C-50 and yesterday I updated the BIOS using windows 7 to the latest 1.07, and then I installed ubuntu 11.10 and now i dont need to set the network to boot first in the BIOS and there is no lockups or freezes. :D[/SIZE]

---

### Post by LewisTM on 2012-01-05
> **Fo2adZz said:**
> [SIZE=4]I really want to thank everyone for the valuable information it helped alot. I have an Acer 722 with APU C-50 and yesterday I updated the BIOS using windows 7 to the latest 1.07, and then I installed ubuntu 11.10 and now i dont need to set the network to boot first in the BIOS and there is no lockups or freezes. :D[/SIZE]
Managed to upgrade the BIOS with a bootable USB DOS disk. The lockups still happen for me, no change :(
I have an Acer 722 with C60. 
Perhaps one needs to install Ubuntu *after* the BIOS has been changed? Or maybe it's the different APU, no clue.
I will try to do a grub-update, see if it picks up anything new and will post back if successful.

---

### Post by r_howie on 2012-01-05
> **LewisTM said:**
> 
Perhaps one needs to install Ubuntu *after* the BIOS has been changed?
Yes, that seems about right. It was the only way to make things work on my Acer Aspire One 522 C-50:
1) change boot order in BIOS;
2) install Ubuntu.

---

### Post by dwaszuk on 2012-01-05
> **LewisTM said:**
> 
I have an Acer 722 with C60.

Same model as mine. I had to put network as first boot option and let it fail while booting in order to install ubuntu (as suggested in previous replies). After having it installed I've changed boot options. Now I have 1) usb disk 2) hdd 3) network and boots ok.

> **LewisTM said:**
>  
Perhaps one needs to install Ubuntu *after* the BIOS has been changed? 

That's the way I've done it.  Hope it helps...

Now everything is going smoothly except for the video resolution. Can't set it higher than 1024x600 (I've not installed propietary drivers). Tried to configure it with xrandr (adding modes) but it crashes.. I think I'll have to get used to this lower resolution :)

---

### Post by matbonucci on 2012-01-06
i played 1080p mkv's videos on windows and they played flawless even connected to a tv through hdmi but with ubuntu the video freezes i've tried fglrx but same problem and it was kinda slow and no suspend, now i'm using open source (also tried xorg-edgers) and the system is faster and it suspend but wont play mkv's

i have to resign to only play mkvs on windows? :neutral: somebody has this same problem? did you found any solution?

---

### Post by LewisTM on 2012-01-06
> **matbonucci said:**
> i played 1080p mkv's videos on windows and they played flawless even connected to a tv through hdmi but with ubuntu the video freezes i've tried fglrx but same problem and it was kinda slow and no suspend, now i'm using open source (also tried xorg-edgers) and the system is faster and it suspend but wont play mkv's

i have to resign to only play mkvs on windows? :neutral: somebody has this same problem? did you found any solution?
I don't think it's a display driver issue, it's more about using an optimized decoder.

How I made it work:
1. Enable the multiverse repository in the Software Sources
2. Add the PPA for CoreAVC (sudo apt-add-repository ppa:ripps818/coreavc) and update
3. Install mplayer2
4. Install umplayer
6. Setup UMplayer performance options to use two threads and skip the loop filter on HD video only.
6. Set Jupiter or other CPU throttle to maximum performance
7. Enjoy smooth 720p and decent 1080p in UMplayer.
The latter software has the bonus of searching and playing Youtube videos. I found it was the only way to view HD Youtube on the Acer.

Cheers!

---

### Post by goldup on 2012-01-07
> **Fo2adZz said:**
> [SIZE=4]I really want to thank everyone for the valuable information it helped alot. I have an Acer 722 with APU C-50 and yesterday I updated the BIOS using windows 7 to the latest 1.07, and then I installed ubuntu 11.10 and now i dont need to set the network to boot first in the BIOS and there is no lockups or freezes. :D[/SIZE]
I've updated bios to 1.07 and problem still occur. I've got c-60, like LewisTM and maybe this is problem, or maybe installing ubuntu after bios upgrade. Don't know it yet ;). Anyway please tell me: do you have restricted or open broadcom drivers?

---

### Post by Fo2adZz on 2012-01-09
> **goldup said:**
> I've updated bios to 1.07 and problem still occur. I've got c-60, like LewisTM and maybe this is problem, or maybe installing ubuntu after bios upgrade. Don't know it yet ;). Anyway please tell me: do you have restricted or open broadcom drivers?
I have installed the restricted broadcom drivers.

---

### Post by antiplex on 2012-01-19
hi ao722-folks,

i just jumped on board of the ao722-ship (C60-model) after really being frustrated with the bad quality of the asus 1215b (but where ubuntu 11.10 worked out of the box without any hazzles admittedly).

i've found this thread quite useful altough i was really unsure what of zzarko's carefully described fixes is necessary with ubuntu 11.10.
[xterminus points out some good ones in his post (77)]("http://ubuntuforums.org/showpost.php?p=11562325&postcount=77") but i did not get what he meant by '8. Power regression notes for grub were a good idea.'. can anybody explain maybe?

since i already had installed the os on my ssd through the other netbook and didn't want to go though all the customizing again i found that i have to set the network boot option before the internal disk in the bios boot-order dialogue (and of course enable network booting there as well).
i also flashed the latest bios (v1.08 [link]("http://support.acer.com/product/default.aspx?tab=5&modelId=3658") ) but that didn't change anything in this matter.

i had access to a 8gb 204-pin ddr3 ram-bar but running memtest86+ with it throwed errors around 7851mb, not sure if the bios can't handle 8gb (as stated by asus) or if there is possibly a defect within the ram. system was running fine though with 8gb installed but i did not use all of the available memory and switched back to 4gb instead as i could not cross-check the ram with another machine.

since some compiz features are really useful to me i have a hard time deciding between using the proprietary drivers (as currently the case) and missing hibernation (standby works fine!) and using the open source drivers that seem to allow hibernate *sigh*.

one thing i did not get was if it would make any sense to use jupiter together with the proprietary ati fglrx drivers, can anybody give me a hint here please?

everything else seems to work fine, looking forward to diving deeper into the world of running a netbook running ubuntu.

a wiki page for the ao722 would make sense in my opinion, did anybody already start with creating one? please share the link if so... did't find any yet...

oh, and of course thanks for all the good hints!
cheers,
anti

---

### Post by zzarko on 2012-01-20
> **antiplex said:**
> i've found this thread quite useful altough i was really unsure what of zzarko's carefully described fixes is necessary with ubuntu 11.10.
[xterminus points out some good ones in his post (77)]("http://ubuntuforums.org/showpost.php?p=11562325&postcount=77") but i did not get what he meant by '8. Power regression notes for grub were a good idea.'. can anybody explain maybe?He probably mentioned #8 fix from first post (kernel power regression). As far as I know, this should be fixed in upcoming 3.3 kernel:
[http://www.phoronix.com/scan.php?page=news_item&px=MTA0MTM](http://www.phoronix.com/scan.php?page=news_item&px=MTA0MTM)

---

### Post by LewisTM on 2012-01-20
> **antiplex said:**
> a wiki page for the ao722 would make sense in my opinion, did anybody already start with creating one? please share the link if so... did't find any yet...
There [is one]("https://help.ubuntu.com/community/AspireOne522") that covers both the Acer 522 and 722. It might need updating by some dedicated soul :D

The consensus seems to be: 'Use the ATI open source driver'. It performs well, Compiz works OK with it. Not that I use compiz, xfwm4 is still way faster and doesn't require as much power.

Cheers!

---

### Post by r_howie on 2012-01-20
> **LewisTM said:**
> There [is one]("https://help.ubuntu.com/community/AspireOne522") that covers both the Acer 522 and 722. It might need updating by some dedicated soul :D

The consensus seems to be: 'Use the ATI open source driver'. 

I agree with everything, and I use the open source driver myself (AO522 C-50, 2GB RAM). With those drivers I can play videos at acceptable quality and show them on a tv screen with the HDMI cable. (Although some really high-quality videos play bumpy at times.)

Wiki page: I have contributed a few bits to it already, but more work needs to be done and a nice table summary added at the beginning, similarly to [this template](https://help.ubuntu.com/community/MacBookAir4-2). Also, I think we should change the title of the wiki page to be 522/722 neutral. Possibly "Acer Netbooks with AMD C-Series processors" (too long and not convenient to remember... just an example).

Another question: have you guys got Bluetooth to work on your 522/722?

---

### Post by jazz.h on 2012-01-22
Hi guys!
I just registered on this forum to thank you for these more than usefull AO722 tips. Too bad I didn't find them earlier when I tried Ubuntu 11.04 and 11.10, following with Kubuntu, Lubuntu and other Ubuntu based distros. I've found this thread when I had had Mint installed so I'm running Mint 12 Classic at the moment, with all the tips applied from the 1st ZZarko's post, thank you ZZarko again (especially for wifi freeze upon boot trick - bios network boot as the 1st boot choice). 

I can also confirm that after bios ver 1.08 network boot doesn't have to be 1st boot choice, nor Broadcom drivers have to be blacklisted any more, at least on my AO722 C-50.

As for bluetooth, it works when windows 7 starter is running first then rebooted and entered Linux, than it's visible after Fn+F3 key.

Questions:
Two remarks after bios ver 1.08: 

1. I think a cooling fan is heard  louder than before, but I'm not sure. Although the temperature is the same. Anyone  else noticed this issue?

2. The last thing I'm having problem with and it's a big issue for me - I can't wake up from suspend or hibernation, black screen only. I have ati fglrx 11.12 drivers activated.

---

### Post by zzarko on 2012-01-22
> **jazz.h said:**
> I can also confirm that after bios ver 1.08 network boot doesn't have to be 1st boot choice, nor Broadcom drivers have to be blacklisted any more, at least on my AO722 C-50.I downloaded that BIOS, but haven't tested it yet. There is also a custom 1.04 BIOS with unlocked advanced menus, but I haven't tried that either. I hope I will in next few weeks...
> **jazz.h said:**
> 2. The last thing I'm having problem with and it's a big issue for me - I can't wake up from suspend or hibernation, black screen only. I have ati fglrx 11.12 drivers activated.You'll need to go back to open source radeon driver for suspend or hibernation to work. This is a very old fglrx bug that probably will never be resolved...

---

### Post by jazz.h on 2012-01-22
Thank you zzarko, I'll try with radeon driver, since I didn't find any signficant improvements with fglrx, should I just deactivate it, or it's a tricky action?

Regarding the fan, do you happen to know a way to monitor fan speed, I tried system benchmark, conky hwmon fan variable, conky acpifan variable... nothing seems able to measure it?

One more thing, I'm not sure if I should make a separate post for this...

On my dualboot Acer 722 after installation of Mint 12 64bit, I noticed this warning in DiskUtility - "Extended partition misaligned by 1024 bytes!".
Apparently my WD scorpio blue is advanced format type 4096 kbytes physical sector size.
I  installed "WD Align by Acronis" cause it can align the partitions without  data loss, but it says everything is OK when running from windows.
I also instaled smartmon tools, smart status is fine, I also fixed the load_cycle_count issue, btw...

I read a whole thread about this bug here -> [http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018), this post excerpt looks quite comfort to me: 
> You do not need to adjust the Linux partitions (/dev/sda6 and  /dev/sda7), nor do you need to adjust the extended partition  (/dev/sda3), despite the fact that its starting sector number is not a  multiple of 8; the extended partition is just a placeholder for the  logical partitions it contains, and it's their alignment that's  important, not the extended partition itself. 
Should I be worried or not, cause it's just extended partition in stake?
I didn't notice any slowdown in Mint though, nor some malfunctions in everyday work...

---

### Post by jazz.h on 2012-01-24
> **jazz.h said:**
> 
I can also confirm that after bios ver 1.08 network boot doesn't have to be 1st boot choice, nor Broadcom drivers have to be blacklisted any more, at least on my AO722 C-50.


Bad news, this is not true, while on battery it still freezes.:-(

---

### Post by antiplex on 2012-01-26
> **jazz.h said:**
> Bad news, this is not true, while on battery it still freezes.:-(

ack, not working for me either as mentioned in my previous post =(

i also found hibernation not to work for me either, i just switched from fglrx to radeon but after hibernating, the boot process just takes place as it usually does. i have enough swap (8gb with 4gb ram) and i also enabled the power regression flag (pcie_aspm=force). any other ideas what i might need to do here?

one more thing: some of you might run unity2D which i am currently havin a look at. whats missing for me is a way to modify some ui-settings (such as reducing the size of the launcher). only some changes in ccsm seem to work; is there another approach? maybe i should also take a look at xfwm4 some time...

regards, anti

---

### Post by xterminus on 2012-01-26
> **antiplex said:**
> ack, not working for me either as mentioned in my previous post =(

i also found hibernation not to work for me either, i just switched from fglrx to radeon but after hibernating, the boot process just takes place as it usually does. i have enough swap (8gb with 4gb ram) and i also enabled the power regression flag (pcie_aspm=force). any other ideas what i might need to do here?

I'm not sure why hibernate wouldn't pick up a properly written suspend image in swap.  As far as I know, as long as an image is written to swap, the kernel should detect it and use it.  My guess is somehow hibernate (pm-disk?) isn't writing or completing the hibernate process.  I think pm-utils logs power events into /var/log/pm-suspend or /var/log/pm-powersave or something like that.  I'd poke through them and look for something odd.

That said, my experience with the stock hibernate/suspend system is pretty minimal.  I only tried the default hibernate system once or twice before deciding that it took FOREVER to write all 4 gigs of ram to disk and switched over to suspend2 (also called tuxonice), which only seems to write what's actually used to disk and operates 2 to 3x as fast as a result.  That it looks pretty and provides feedback on the hibernate process is a nice bonus too.

I also use the hibernate script (apt-get install hibernate) to manage bringing various services online/offline, mute the volume/stop mp3 playback, etc, etc.  It might be something to fool with when you get things working.

> **antiplex said:**
> one more thing: some of you might run unity2D which i am currently havin a look at. whats missing for me is a way to modify some ui-settings (such as reducing the size of the launcher). only some changes in ccsm seem to work; is there another approach? maybe i should also take a look at xfwm4 some time...

I'm pretty sure unity2d doesn't use compiz for many of it's settings, since the whole idea behind it is *not* to use all those fancy 3d effects which compiz provides.  You might need to tweak unity settings using the gconf or dconf editor.  I'm sure there are lots of threads on this site covering this.

If your looking at a low-powered window managers, a lot of people really like the fluxbox/openbox approach, or even the tiling window managers, (xmonad, wmii, etc).  Then again, users who like the feel of those managers also seem to be cli junkies too ;)

I find gnome-shell eats less cpu/ram than unity, which might be something to look into as well.  There is a fork of gnomeshell the mint guys are doing that looks interesting if you like the old gnome-feel too.

---

### Post by xterminus on 2012-01-26
> **jazz.h said:**
> Bad news, this is not true, while on battery it still freezes.:-(

Same here, just updated bios yesterday - didn't notice any difference in behavior.  Then again, if you disable the ethernet port entirely, everything seems to behave much more nicely and you can ignore the lockups - which is what I do instead of fooling with the boot order.

---

### Post by ard213 on 2012-01-29
Thank you all for all the helpful information in this thread.  I've been running Ubuntu on my C-60 722 for months now, thanks to you.  Though I've been a lurker for a while, I thought I'd chime in on a couple of points:

> **xterminus said:**
> Same here, just updated bios yesterday - didn't notice any difference in behavior.  Then again, if you disable the ethernet port entirely, everything seems to behave much more nicely and you can ignore the lockups - which is what I do instead of fooling with the boot order.

Unfortunately, disabling the ethernet driver does not fully fix the boot problems in my C-60 722.  It worked flawlessly when plugged in, but when running on battery power it froze before the desktop could finish loading.  I've reverted to booting with the network, and removed the ethernet driver from the blacklist.
   
For what its worth, I am running Ati Catalyst 11.12.  Other than the lack of sleep/hibernation, my netbook runs flawlessly.  Since I've upgraded my ram after partitioning the HD, I probably won't be able to hibernate without a clean install anyway, so I'm not bothered by it.

Speaking of which, upgrading to 4 gigs of ram, from the stock 2 gigs, sped up my netbook considerably.  Adding Flash-aid and Flash-video-replacer ([http://www.webgapps.org/add-ons/](http://www.webgapps.org/add-ons/)) helped my youtube & hulu experiences considerably.

The Jupiter applet works very well for me (thank you, Fuduntu!).  6 hours of battery is a given, and I've seen up to 8.5 depending on my use.

Has anyone managed to play around with the unlocked bios yet?  I am very hesitant to try (I can't afford to brick this computer!), and have read (on the bios-mod forums) that it slows down the booting sequence significantly...  Still any reliable info would be welcome :D

Thanks again for all the info, and keep up the good work!

---

### Post by ard213 on 2012-01-29
Just to clarify: Flash-video-replacer does not work with hulu, but having the latest Flash installed helped a lot.  Flash-aid guaranteed that I had the latest 64 bit flash installed... I thought I did, but was wrong.

---

### Post by jazz.h on 2012-01-30
> **zzarko said:**
> You'll need to go back to open source radeon driver for suspend or  hibernation to work. This is a very old fglrx bug that probably will  never be resolved...

I'm on open source driver now, suspend and hibernation works as expected.:D

And for this...

> **jazz.h said:**
> I noticed this warning in DiskUtility - "Extended partition misaligned by 1024 bytes!".

It's definitely a bug in DiskUtility, tried everything so far...

Since now my system (nearly) works as I expect, I'll perform an ext4 partition backup to image from CloneZilla immediately. :)

Said nearly, cause these 2 issues are still open - 1) wifi led is always off even with wifi enabled and working, and b) in Skype internal mic problems...

---

### Post by Elssha on 2012-01-30
Hi, 
  I just installed 11.10 on AAO 722 and everything within ubuntu works okay, though getting used to unity is annoying atm >_<
My problem is that my windows 7 partition is not an option at boot. I have ubuntu, memtest and even the recovery partition boot for win 7, but not the win 7 itself. I checked in ubuntu and nothing is wrong with the partition itself (my first thought was that maybe i formatted the wrong partition); grub just doesn't list it. 
Anyone encounter this, or know how to fix it (tried updating grub already; no luck)? Thanks!
El

---

### Post by antiplex on 2012-01-31
xterminus, thank you very much for your detailed post reagrding the my issues!
> **xterminus said:**
> I'm not sure why hibernate wouldn't pick up a properly written suspend image in swap.  As far as I know, as long as an image is written to swap, the kernel should detect it and use it.  My guess is somehow hibernate (pm-disk?) isn't writing or completing the hibernate process.  I think pm-utils logs power events into /var/log/pm-suspend or /var/log/pm-powersave or something like that.  I'd poke through them and look for something odd.
i just checked the contents of /var/log/pm-suspend.log and most entries here show no signs of trouble except maybe ```
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
``` (still seems successful...) and ```
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
``` and maybe also ```
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

...
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.
``` dont know what to do about #1 and #3 but i'll try to disable wlan&bt before my next attempt.

one other thing i noticed is that (having splash disabled during boot) i can see some entries about orphaned inodes flash by when booting after hiberate (not the case after a plain shutdown). even worse, after entering my pwd in the login dialogue, the whole system seems to freeze (key-combinations ctrl + del or ctrl + alt + f1 seem to have no effect). on the next reboot everything is normal again (but hibernation-data seems all lost).

> **xterminus said:**
> That said, my experience with the stock hibernate/suspend system is pretty minimal.  I only tried the default hibernate system once or twice before deciding that it took FOREVER to write all 4 gigs of ram to disk and switched over to suspend2 (also called tuxonice), which only seems to write what's actually used to disk and operates 2 to 3x as fast as a result.  That it looks pretty and provides feedback on the hibernate process is a nice bonus too.

I also use the hibernate script (apt-get install hibernate) to manage bringing various services online/offline, mute the volume/stop mp3 playback, etc, etc.  It might be something to fool with when you get things working.if i read the repository information correcly suspend2 is part of the hibernate package, right? i also installed it (reads nice, thanks for the hint) but issues remain the same.

> **xterminus said:**
> I'm pretty sure unity2d doesn't use compiz for many of it's settings, since the whole idea behind it is *not* to use all those fancy 3d effects which compiz provides.  You might need to tweak unity settings using the gconf or dconf editor.  I'm sure there are lots of threads on this site covering this.

If your looking at a low-powered window managers, a lot of people really like the fluxbox/openbox approach, or even the tiling window managers, (xmonad, wmii, etc).  Then again, users who like the feel of those managers also seem to be cli junkies too ;)

I find gnome-shell eats less cpu/ram than unity, which might be something to look into as well.  There is a fork of gnomeshell the mint guys are doing that looks interesting if you like the old gnome-feel too. there are several threads regarding the configurability of unity (especially 2d) and the bottom line is more or less that there is only very little possibility to customize unity2d (e.g. launcher icon size) which seems to be wanted to be like this for some odd reason and changing this after several demands has no high priority for now.

while i am open to try out other wm's i found one thing that i would not want to miss from unity: **the integration of the top-window-frame into the top panel for maximized windows**. this is really great since almost all displays nowadays seem to come in 16:9 aspect ratio vertical space becomes more and more valuable and i found this a nice way of saving some otherwise useless wasted space.
of course chances are that this concept has been invented by unity and might be used within other wm's as well. anybody got any ideas here? gnome3 doesn't as it seems.

---

### Post by antiplex on 2012-01-31
> **jazz.h said:**
> It's definitely a bug in DiskUtility, tried everything so far...
...
Said nearly, cause these 2 issues are still open - 1) wifi led is always off even with wifi enabled and working, and b) in Skype internal mic problems...
jazz, are you sure that it's a bug in diskUtility? i've found it working very well in my case. how did you partition your drive? by the installer? that should normally do it correctly afaik. could you post the outcome of ```
sudo fdisk -l
```
wifi led is working fine in my case, not using skype, but google talk works flawlessly for me.

---

### Post by jazz.h on 2012-01-31
> **antiplex said:**
> jazz, are you sure that it's a bug in diskUtility? i've found it working very well in my case. how did you partition your drive? by the installer? that should normally do it correctly afaik. could you post the outcome of ```
sudo fdisk -l
```wifi led is working fine in my case, not using skype, but google talk works flawlessly for me.

Yes, I'm almost sure, I repeated the partitioning process 3 times. First, by the installer. Then 2 times manually:

1. Booted from Win7 Starter and made 1 extended partition from there (because of aligning).
2. Created ntfs  sda5 (300 gb) into newly extended partition 
3.  Booted from live usb and created sda6 ext4 50gb for Mint12, sda7 ext4 50 gb for some KDE distro, sda8 swap.
4. Checked from Disk utility if warning align messages are gone, yes, now everything is fine, no errors.
5. Installed Mint12 into sda6.
6. Checked DiskUtility again - now mislaignment warning message is there again. :o

On this thread I first saw suspicions of bug in DiskUtility in case of extended partitions.
-> [http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

The picture of my hdd before this action (but the warning is the same) is here:
[IMG]http://forums.linuxmint.com/download/file.php?id=9187[/IMG]

I can't reproduce the response to "fdisk -l" cause my laptop is not here atm, but I'll do it later.

Any ideas...?

---

### Post by ard213 on 2012-01-31
I see the same behavior as jazz.h on my 722, and running fdisk-l gives me the following:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0006b156

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   621514751   310756352   83  Linux
/dev/sda2       621516798   625141759     1812481    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5       621516800   625141759     1812480   82  Linux swap / Solaris
```For whatever its worth, this has not given me any problems, and I have successfully ignored it so far :P

---

### Post by antiplex on 2012-01-31
ard213, i think (although not 100% sure, can anybody confirm?) your partition scheme is fine and resembles what i suspect causes the warning on jazz.h's installation.

basically, if the drive used is not an advanced format one (=sector size 4096 bytes) the alignment can't be really wrong but with the new drives, data-partitions should be aligned to the physical sectors of the disk.

your fdisk states that its units consist of logical sectors that are 512 bytes big. so if you would want to align the start of a data-partition to the physical sectors, the numbers provided in logical sectors (512byte) should be divisible by 8 (because 8*512 = 4096 = 1 physical sector) without remainder.

your partitions start at 2048 (sda1), 621516798 (sda2, Extended) and 621516800 (sda5). the only number not divisible by 8 without reminder is the one of sda2, the extended partition. since this is not a data-partition but some sort of wrapper-partition (in your case holding one data-partition, sda5), the alignment doesn't really matter for this one as long as the contained data-partitions are correctly aligned.



bad news with my own issues (mainly hibernate atm), even when powering off wireless networking & bluetooth the system seems only to find 'orphaned inodes' upon resume and freezes right after login.

i also could not find any window-manager that merges its top window border with the top panel with maximized windows (and saves vertical space for more important panels). anybody seen something like this anywhere? hints welcome ;)

regards, anti

---

### Post by jazz.h on 2012-01-31
> **antiplex said:**
> could you post the outcome of ```
sudo fdisk -l

here it is:

[CODE]Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0e8f6e23

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    27265023    13631488   27  Hidden NTFS WinRE
/dev/sda2   *    27265024    27469823      102400    7  HPFS/NTFS/exFAT
/dev/sda3        27469824   132327423    52428800    7  HPFS/NTFS/exFAT
/dev/sda4       132329470   976771071   422220801    f  W95 Ext'd (LBA)
Partition 4 does not start on physical sector boundary.
/dev/sda5       132329472   746729471   307200000    7  HPFS/NTFS/exFAT
/dev/sda6       746731520   862074879    57671680   83  Linux
/dev/sda7       862076928   972576767    55249920   83  Linux
/dev/sda8       972578816   976771071     2096128   82  Linux swap / Solaris
```

---

### Post by LewisTM on 2012-01-31
> **antiplex said:**
> 
bad news with my own issues (mainly hibernate atm), even when powering off wireless networking & bluetooth the system seems only to find 'orphaned inodes' upon resume and freezes right after login.

i also could not find any window-manager that merges its top window border with the top panel with maximized windows (and saves vertical space for more important panels). anybody seen something like this anywhere? hints welcome ;)

Hibernation works perfectly here with Xubuntu 11.10 and open source video drivers. Sounds like your system fails to commit file changes to disk before hibernating which results in orphaned inodes. Maybe issuing a 'sync' command before hibernating could help (but it's hardly a permanent fix).

About your WM question, isn't a major point of the new Unity to provide that space-saving feature?  In Xfce I restrict myself to one visible panel (+ 1 autohide dock), I use Chrome sans titlebar or menu and make heavy use of the Alt-F11 fullscreen shortcut. 

Cheers!

---

### Post by antiplex on 2012-02-01
> **jazz.h said:**
> here it is:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0e8f6e23

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    27265023    13631488   27  Hidden NTFS WinRE
/dev/sda2   *    27265024    27469823      102400    7  HPFS/NTFS/exFAT
/dev/sda3        27469824   132327423    52428800    7  HPFS/NTFS/exFAT
/dev/sda4       132329470   976771071   422220801    f  W95 Ext'd (LBA)
Partition 4 does not start on physical sector boundary.
/dev/sda5       132329472   746729471   307200000    7  HPFS/NTFS/exFAT
/dev/sda6       746731520   862074879    57671680   83  Linux
/dev/sda7       862076928   972576767    55249920   83  Linux
/dev/sda8       972578816   976771071     2096128   82  Linux swap / Solaris
```

ah, just as i explained, the only misaligned partition is the one of the extended wrapper one (sda4) which doesn't matter.
sda5,6,7,8 are aligned nicely because
 132329472 % 8 = 0
 746731520 % 8 = 0
 862076928 % 8 = 0
 972578816 % 8 = 0

so, nothing to worry about regarding this, everything should be fine.


> **LewisTM said:**
> ...
About your WM question, isn't a major point of the new Unity to provide that space-saving feature?  In Xfce I restrict myself to one visible panel (+ 1 autohide dock), I use Chrome sans titlebar or menu and make heavy use of the Alt-F11 fullscreen shortcut.  ... you are probably right about the unity philosophy, i thought maybe some other WM had picked up this idea as well.
however, saving vertical space while browing is one use-case, another one would be hacking in eclipse where the resolution of 1356x768 is imho the absolute minimum which one could work with, same applies for advanced uses of gimp or inkscape for example.


i also think i finally found the reason why hibernation did not work for me and as it seems its got nothing to do with the aspire one 722 but more with my decision to choose 'encrypt my home folder' during installation. this seems to automatically lead to the setup of an encrypted swap (which makes absolutely sense seen from a security pov) which encryption key is randomly chosen on boot, so the hibernation-data is effectively gone right when the system powers off after writing the memory contents to swap.
as it seems this has been known for some time to break the ability to hibernate but the ubuntu-maintainers or howevers courtesty this might be have not yet introduced a hint stating such in the install dialogue or disabled the hibernate-selection for systems that use an encrypted home directory.
i've found [this launchpad-bug]("https://bugs.launchpad.net/ecryptfs/+bug/432785") helpful, in comment #15 there is a short description how to disable encrypted swap (**which will lead to a security risk** but should allow hibernation!).

i'll try that and let you know how everything turned out...

EDIT1: seems i get at least a step forward, instead of rebooting, the hibernation-data seems to be loaded but the x-server shows only garbled pixels. when changing to tty1 via 'CTRL + ALT + 1' i see messages like ```
[ 186.528352] radeon 0000:00:01.0: GPU lockup CP stall for more than 10064msec
``` any ideas how to solve this?!?

EDIT2: the lockups went away after further fiddling around but i messed my system up once more *sigh* so i did a fresh reinstall with similar settings as before. here is what i did to get rid of the encrypted swap (dev/sda2 in my case, make sure to adopt this to your swap-partition correctly, otherwise you could lose your data! the sections between '**' are comments and need to be left out): > sudo swapoff -a
sudo cryptsetup remove /dev/mapper/cryptswap1
sudo vim /etc/crypttab **comment out the swap device defined here**
sudo mkswap -L swap /dev/sda2
sudo blkid /dev/sda2 **the id is needed afterwards and might be different each time the previous step is performed**
sudo vim /etc/fstab **instead of '/dev/mapper/cryptswap1' use UUID= followed by the uuid of the previous step**
sudo vim /etc/default/grub **replace the line 'GRUB_CMDLINE_LINUX=""' by GRUB_CMDLINE_LINUX="RESUME=UUID=" followed by the uuid (within the "")**
sudo update-grub
sudo vim /etc/initramfs-tools/conf.d/resume **set 'RESUME=UUID=' followed by the uuid (without '')**
sudo update-initramfs -c -k all
sudo reboot **after the reboot, check e.g. in system monitor if the amount of swap matches**

EDIT3: > **xterminus said:**
> I also use the hibernate script (apt-get install hibernate) to manage bringing various services online/offline, mute the volume/stop mp3 playback, etc, etc.  It might be something to fool with when you get things working.sadly in my case suspend2 of the hibernate package is not working and was the reason for breaking my system earlier. i like the additional output and the possibilities provided by it but resume just wont work, the resume-process stops right after > ...
resume: Compressed image
Loading image data pages (<number> pages)... 100% done
wrote <number> MB in <number> seconds (<number> MB/S)
read <number> MB in <number> seconds (<number> MB/S)
total image i/o: <number> MB in <number> seconds (<number> MB/s)
resume: Compression ratio 0.33nothing is happening after this, even when waiting for minutes.
uninstalling the package won't fix the now broken hibernate (my guess is that some kernel-modules are modified during installation), so the only way back would be a backup-recovery or a fresh install =(
bottom line for now: dont install the suspend2 (package hibernate) if you tweaked your way around encrypted swap like i did.


regards,
anti

---

### Post by ard213 on 2012-02-06
For what its worth:

I recently tried switching to the open-source drivers, using the latest stable versions from [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates), just so I could play around with the suspend feature, and with gnome-shells.

I have discovered that the battery life decreases significantly from the closed-source ati drivers.  I lost about 2 hours of battery life, and significant video performance on youtube.  Suspend worked, as did gnome, but I found out that I really need the extra battery life, and that I *really* like unity.

I did not try the "bleeding edge" ppa ( [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) ), as I must have a stable machine.

So I'm back with ati (version 12.1 now).  Stable, faster than open-source, long battery life, but no suspend or gnome shell (lots of flickering when logging in with any shell but unity). Your mileage may vary, of course, but I thought that this may be useful information for new users.

Again, my 722 has a C-60 apu...

---

### Post by xterminus on 2012-02-06
> **ard213 said:**
> For what its worth:

I recently tried switching to the open-source drivers, using the latest stable versions from [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates), just so I could play around with the suspend feature, and with gnome-shells.

I have discovered that the battery life decreases significantly from the closed-source ati drivers.  I lost about 2 hours of battery life, and significant video performance on youtube.  Suspend worked, as did gnome, but I found out that I really need the extra battery life, and that I *really* like unity.


The opensource drivers will suck juice without a little tweaking.  I dropped the following script into /etc/pm/power.d/radeon to fix that.

```

#!/bin/sh

. "${PM_FUNCTIONS}"


enable_low() {
        # Change Power Profile to low
        echo low > /sys/class/drm/card0/device/power_profile
        # Turn backlight down to 1 (override gnome/whatever!)
        echo 1 > /sys/class/backlight/acpi_video0/brightness
}

enable_high() {
        # Change Power Profile to high
        echo high > /sys/class/drm/card0/device/power_profile
        # Crank backlight back up to 9 (override gnome/whatever!)
        echo 9 > /sys/class/backlight/acpi_video0/brightness
}

case $1 in
    true) enable_low ;;
    false) enable_high ;;
    *) exit $NA ;;
esac

```

I'm still using the stock x drivers, nothing special about em other than they are the ones that come with oneiric.

> **ard213 said:**
> 
I did not try the "bleeding edge" ppa ( [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) ), as I must have a stable machine.

So I'm back with ati (version 12.1 now).  Stable, faster than open-source, long battery life, but no suspend or gnome shell (lots of flickering when logging in with any shell but unity). Your mileage may vary, of course, but I thought that this may be useful information for new users.

Again, my 722 has a C-60 apu...

As for video performance, the FlashAid firefox plugin correctly installed the beta version of the amd64 flash plugin.   I saw a tremendous increase in flash performance as a result.  I can now play 720p videos without any stutter and 1024p with a little jerkiness, where before it was almost unwatchable at either resolution.

---

### Post by ard213 on 2012-02-07
> **xterminus said:**
> The opensource drivers will suck juice without a little tweaking.  I dropped the following script into /etc/pm/power.d/radeon to fix that.

I'm still using the stock x drivers, nothing special about em other than they are the ones that come with oneiric.

As for video performance, the FlashAid firefox plugin correctly installed the beta version of the amd64 flash plugin.   I saw a tremendous increase in flash performance as a result.  I can now play 720p videos without any stutter and 1024p with a little jerkiness, where before it was almost unwatchable at either resolution.

Thanks, xterminus!  I forgot to say that I have Flash-aid, and so I'm running the latest 64bit Flash beta.  Oddly, with radeon drivers I was still lagging a lot in 480p movies. And I got the occasional screen flicker in unity (none of that with the latest proprietary drivers). 

As I don't have much use for the sleep feature (I can just turn my netbook off between classes, it doesn't take that long to boot) I'll happily stick with the ati drivers.  It's much more important that I have 7-8 hours of running time on battery, anyway.  Ati drivers with the jupiter applet give me that, so I won't mess with a winning team. :)

I just wanted to add a bit to the knowledge pool of 722 ubuntu users.  There seems to be a strong preference towards the open source drivers, so I thought I'd add some insight into the proprietary ones.  I may try the open source again in the (distant) future, as it gets ironed out a bit more (perhaps you should submit your script to the developers?).

Cheers,

---

### Post by hitime on 2012-02-07
Has anyone had any luck on bluetooth, the boot into windows is not an option for me since the 1st thing I did when I got mine was format and put Ubuntu on.   Works great with Lubuntu 11.10, just want some bluetooth goodness....

Thanks,
hitime

---

### Post by r_howie on 2012-02-07
> **hitime said:**
> Has anyone had any luck on bluetooth, the boot into windows is not an option for me since the 1st thing I did when I got mine was format and put Ubuntu on.   Works great with Lubuntu 11.10, just want some bluetooth goodness....

One option is to install Windows in a Virtual Machine (e.g. VirtualBox).

Here's how I did it. Note that I didn't test it thoroughly, but I did see the Bluetooth icon pop up in my Ubuntu desktop, with my BT controller listed, so it should work. Here goes:
[list]
[*] install VirtualBox, create a virtual machine (I chose 20GB) with default settings and install Windows in it (in my case, Windows 7)
[*] in Windows 7: Control Panel -> view by icons, then Administrative Tools -> Services -> start Bluetooth (compare with [this SevenForums post](http://www.sevenforums.com/drivers/50787-no-bluetooth-devices-found.html#post471983))
[*] in Windows 7: from Acer website, download and install the Bluetooth drivers. I used this: (Atheros) Bluetooth Driver for Windows 7 SP1 (200MB, 2011/04/12)
[*] reboot Windows 7. You should receive a message similar to *The 'CIESpeechBHO Class' add-on from 'Atheros Communications Inc.' is ready for use.* Click Enable
[*] now, hitting Fn+F3 when your mouse cursor is in the Windows VM, also enables Bluetooth in Linux
[/list]

---

### Post by antiplex on 2012-02-14
> **r_howie said:**
> One option is to install Windows in a Virtual Machine (e.g. VirtualBox).

Here's how I did it. Note that I didn't test it thoroughly, but I did see the Bluetooth icon pop up in my Ubuntu desktop, with my BT controller listed, so it should work. ...
seems i've missed the bluetooth issues since i thought that i was lucky and bt worked on my aspire one (C60) because the bluetooth symbol showed up when i cycled through the wireless settings. now that i tried to connect via bluetooth it dawned on me that this is what the posts here have been around for.
so did i get this correctly that bluetooth hast to be somewhat activated through some (proprietary) windows software before it is fully functional? can bluetooth be turned on and off afterwards without the need to go through the windows activation again?

regards,
anti

---

### Post by antiplex on 2012-02-14
something else i've just discovered:

when i was connected to a wireless lan network before hibernate, the whole system freezed after resume (no chance to switch to console by CTRL + ALT + 1). when i disabled wlan before hibernating i was able to resume but as soon as a reactivated wlan the system was freezing up.

after a bit of searching i came across this [askubuntu-discussion]("http://askubuntu.com/questions/74319/going-back-after-suspend-leads-to-freezing") and tried the described solution of creating a file (i named it '20_wlan-hibernate-fix' in /etc/pm/config.d with the content ```
SUSPEND_MODULES="$SUSPEND_MODULES iwlagn xhci-hcd"
```
[COLOR="Red"]EDIT[/COLOR]: i first thought this would work but soon discovered that the freezing still occurs especially when the available wireless networks change in the meantime (other location).
next thing i'll try is the script described in [this post]("http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug") and let you know how things turn out with this one...
[COLOR="Red"]EDIT2[/COLOR]: unfortunately this also did not work =( same freezeup as before. basically the script unbinds and rebinds the device found at /sys/bus/pci/drivers/ehci_hcd and /sys/bus/pci/drivers/xhci_hcd but since in the ase of the AO722 there is no xhci-device but a ohci device i'll give it another shot with this one...

i wonder if anybody else came across this issue? anybody who can hibernate why connected by wireless lan without a system-freeze on resume without a fix like i just described?

regards,
anti

---

### Post by oz238 on 2012-02-27
Here is a post related to the bluetooth problems:
[http://ubuntuforums.org/showthread.php?t=1930353&highlight=Foxconn+%2F+Hon+Hai+bluetooth]("http://ubuntuforums.org/showthread.php?t=1930353&highlight=Foxconn+%2F+Hon+Hai+bluetooth")

However, it doesn't help. I also tried this:
[http://ubuntuforums.org/showthread.php?t=1917883&highlight=bluetooth+unable+to+find+devices](http://ubuntuforums.org/showthread.php?t=1917883&highlight=bluetooth+unable+to+find+devices)

But it doesn't work for me. I have the same bt device: Foxconn / Hon Hai, 0x0489:0xe03c, Acer 722 C6Ckk, lusft0c056. I have Xubuntu 11.10. Cycling Fn+F3 enables bt but searching other bt devices finds nothing.

Here is another post (for other bt device):
[http://ubuntuforums.org/showthread.php?t=1867447&highlight=bluetooth+unable+to+find+devices](http://ubuntuforums.org/showthread.php?t=1867447&highlight=bluetooth+unable+to+find+devices)

I haven't tried it yet. But I hope, the solution will be simplier than recompiling the kernel.

Here is another interesting link:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/863051](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/863051)

----------
I had also small problem with muting and changing volume using Fn + arrow keys. They worked but it was impossible to mute or change volume. It only changed the state of IEC958 device in mixer. The solution is: go to Settings/Settings Editor, go to xfce4-mixer and change a value of active-card to: PlaybackInternalAudioAnalogueStereoPulseAudioMixer. The value is taken from "sound-cards" list, which is below.
I hope, someone will find this small tip usefull.

---

### Post by zzarko on 2012-03-11
For those of you who don't like mono in Jupiter, there is now Python port. More details can be found on:
[http://www.webupd8.org/2012/03/jupiter-applet-ported-to-python-gets.html](http://www.webupd8.org/2012/03/jupiter-applet-ported-to-python-gets.html)

Cheers,
Zarko

---

### Post by hitime on 2012-03-12
I've been running 12.04 for about 2 weeks now and it does seem quite a bit better at this point.  I'm back to basic Ubuntu, tested open and closed video drivers.  Be warned if you go with AMDs, when ever you do some major Beta update it will kill the desktop (have to uninstall in shell or save yourself the hassle and uninstall it before updating).  Battery life seemed better before the partial beta update yestereday, but overall battery life is better (Jupiter installed).  The audio fix for the builtin mic is not working on 12.04, at this point I would rather have speed/battery then the mic.  If I find more, I'll post it up...

---

### Post by emilywind on 2012-03-16
I just want to say that with the more recent graphics stack and kernel 3.2.9 found in Fedora 16, the amount of heat produced and power used by the graphics/cpu is right on with the proprietary driver in Windows. In fact, after 20min in gnome shell browsing the web and chatting it is actually running cooler than Windows would be at this point doing the same things.

The open source wireless drivers also saw a move out of the staging area in this kernel and are more stable; no longer requiring the bios work around to prevent the netbook from freezing upon wireless connect.

For those still in the Ubuntu world of things with no intention to move, this means Precise should run well without any tweaks needed on it, although the use of power management scripts is still a good idea.

Cheers. :)

---

### Post by casainho on 2012-03-29
Thank you emilywind :-)

---

### Post by colinmb on 2012-03-29
Is it possible to set up the framebuffer console and/or GRUB to use the native 1366x768 panel resolution?

This page has instructions for the 751h model, but that apparently uses an Intel GPU:
[https://help.ubuntu.com/community/AspireOne/AO751h](https://help.ubuntu.com/community/AspireOne/AO751h)

--Colin

---

### Post by abhz on 2012-03-31
@emilywind: Would you mind to share where this information comes from? I bought an Acer Aspire One 722 several weeks ago, and have been desperately trying to get *anything* working on this thing since.

Ubuntu 11.04 was a total nightmare, and since the first beta releases I'm "running" Ubuntu 12.04 which literally gets worse every day.

> The open source wireless drivers also saw a move out of the staging area in this kernel and are more stable; no longer requiring the bios work around to prevent the netbook from freezing upon wireless connect.

I definitely can not confirm this. Without blacklisting the ethernet driver from the kernel config, the netbook freezes a couple of secords after booting, as it always did.

Also, the BIOS workaround does *not* work on all 722's; I'm beaten by such a model, so I know this for a fact. The only way to get networking on this this is to

a) either plug in a ethernet cable and use Ethernet; or
b) blacklist the ethernet driver in the kernel config and use Wireless.

So the Acer Aspire One 722 can be used *either* only with WLAN, or it always has to hang on an ethernet cable. The current beta of Ubuntu 12.04 does *not* change this.

> For those still in the Ubuntu world of things with no intention to move, this means Precise should run well without any tweaks needed on it [...]

I can't confirm this, either. Since a couple of days, I lost the mouse pointer on the desktop (it sticks to the middle of the desktop and can not be moved anymore). The only way to operate this netbook is to switch to the the console screen (Ctrl+Alt+F1) and work on the shell, exactly as I did with my first Linux notebook in the mid-90s.

On this netbook, Ubuntu 12.04 is being updated to the latest updates available at the moment, multiple times per day. I have no 3rd party repositories enabled, it's running just what Ubuntu itself offers.

(Personal notice: My experience with Ubuntu on this netbook was a total catastrophy from the beginning; I planned around six weeks to set this up, and to resolve the numerous issues that Linux has with every notebook. Instead of making any progress, I've given up on using the netbook for wireless browsing the web, checking e-mails on the road, or even displaying images. If Ubuntu doesn't break this also in the next two days, I'll have to copy images from my DSLR via mc on the the. If this still works when I travel on Monday, this would be the only use this netbook would be capable of.)

---

### Post by emilywind on 2012-03-31
Sadly, it seems I was just being hopeful for those wanting to use Ubuntu. I am not sure what it is in Ubuntu 12.04 but I tried Kubuntu 12.04 and it ran with similar issues as to what it used to have. That is, more heat production than normal and only 5 steps of brightness compared to the proper 10.

In Fedora I do not get these issues, which likely has to do with versions of mesa and Xorg, along with kernel versions and/or patches. Whatever it is, Fedora runs better on it due to those issues.

That said, using KDE over Gnome 3 is an obvious confound in the comparison, although in fairness I was using KDE with no effects on verus Gnome 3 standard (which always has effects). Thus I am not sure if KDE was still the culprit of the power consumption issue or something in Ubuntu 12.04.

As for the networking, the freezing decided to show its ugly head when I connected to a network using enterprise security requiring a login. However, it did and does not freeze while connecting to my home network. I have re-enabled the bios work-around for now which *does* work on my particular Aspire One, but hopefully this is sorted in the future.

That said, this will all depend on what comes in your Aspire One 722. You could try Fedora 16 and see how that goes since my results have been best with it, but then again you may have different hardware since you bought it much later than I. ;x

---

### Post by abhz on 2012-04-01
@emilywind: Thanks for the update. Yes, wishful thinking is all that keeps me at Ubuntu, also.

For reference: My AO 722 has a "MFG Date: 2012/01/02" and uses a WLAN chip from Broadcom. It was preconfigured with "Linpus Linux" (which directly boots into a root shell, and did not support "startx", and came without any usage instructions related to running Linux on the device).

Distributon hopping is not an option for me anymore, I did that for years, starting in the 90s; always one thing works better, but at least another thing works worse. I made my decision for Debian a long time ago, and the only possible alternatives for me would be LMDE, Mint, or Debian "testing" (which do not work better on the AO 722, for obvious reasons).

---

### Post by nardis_Miles1 on 2012-04-08
Many thanks for the post. Much of this works for 11.10 as well as 11.04. One problem is that the internal microphone fix doesn't seem to work. I get a lot of these errors:

snd-hda-codec-analog.ko:
Running module version sanity check.

Module has been obsoleted due to being included
in kernel 2.6.99.  We will avoid installing
for future kernels above 2.6.99.
You may override by specifying --force.

So, did you --force?

---

### Post by r_howie on 2012-04-09
I have updated the guide [https://help.ubuntu.com/community/AspireOne522](https://help.ubuntu.com/community/AspireOne522) in the following ways:
[list]
[*] added a table summarizing which features work out of the box, which ones require some fixes, which ones don't work (inspired from [here](https://help.ubuntu.com/community/MacBookAir4-2))
[*] major rewrite of some parts to be more compact - please complete the missing parts
[*] added a "Recommended tweaks" section with the fixes that are easy to implement, not dangerous and certainly useful for the average user (zzarko's fixes at the beginning of this thread to improve power management, setting correct volume for Skype, CapsLock indicator etc.)
[*] the more advanced hacking stuff (unofficial BIOS, etc.), only for the experienced users, are now grouped in the section "Advanced tweaks" in the bottom
[/list]

---

### Post by zzarko on 2012-04-16
I'm testing 12.04 beta 64-bit with all current updates on my 722 with C50 CPU and following hardware:
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6250]
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
06:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v2.0 Fast Ethernet (rev c1)
07:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

I didn't installed any additional software or drivers, except Jupiter and KeyLock indicator (64bit version for Oneric works just fine). Here is list of what works for me:
WiFi: OK
Bluetooth: OK, after several tries (indicator can show that BT is enabled, when, in fact, it isn't - it took a little time fiddling with Fn+F3 and BT indicator)
Internal microphone: almost OK (it is recokgnised, but the volume is too low, even when maxed-out)
Headphones turn off internal speakers: OK

Next, I'll try booting without network boot in BIOS, and I want to see if Catalyst drivers are working (Jockey gave an error after the installation, but the same happened on my desktop). Touchpad rotation, for now, isn't available for 12.04.

EDIT:
Sleep mode with open-source radeon drivers: OK

EDIT2:
Booting without BIOS network boot: OK, but after logging in, WiFi didn't work. I just disable and enable it again, and now it works.
Sleep with Catalyst drivers: NOT working (and probably never will, as AMD guys obviously aren't interested in that)

But, so far, so good :)

Cheers,
Zarko

P.S. If someone wants some other tests, please tell me. If I can, I'll try to make them and I'll post results.

---

### Post by jazz.h on 2012-04-16
> **zzarko said:**
> But, so far, so good  Excellent finding zzarko, thank you.  Please, report on the temperature situation as well as the hdd clicking (load_cycle_counts increasing, hdparm settings).

---

### Post by ard213 on 2012-04-24
> **jazz.h said:**
> Excellent finding zzarko, thank you.  Please, report on the temperature situation as well as the hdd clicking (load_cycle_counts increasing, hdparm settings).

Is there a way to monitor CPU temp on the C-50/C-60 APUs?  I was under the impression that this had not been figured out yet (on linux).  At least on my C-60, running Catalyst 12.3, the jupiter applet fails to report CPU temp.

---

### Post by xterminus on 2012-04-25
> **ard213 said:**
> Is there a way to monitor CPU temp on the C-50/C-60 APUs?  I was under the impression that this had not been figured out yet (on linux).  At least on my C-60, running Catalyst 12.3, the jupiter applet fails to report CPU temp.

Seems to work fine for me.  I don't remember loading any custom modules.

```


$: sensors
radeon-pci-0008
Adapter: PCI adapter
temp1:        +71.0°C  

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +71.0°C  (high = +70.0°C)
                       (crit = +115.0°C, hyst = +107.5°C)


```

---

### Post by ard213 on 2012-04-25
> **xterminus said:**
> Seems to work fine for me.  I don't remember loading any custom modules.



Ah, silly me.  I never got around to installing (and learning how to use) lm-sensor.  Thanks!

Just installed it, and it seems to work perfectly - but jupiter still does not post any temp info.  Is there a work-around for that?

---

### Post by ard213 on 2012-04-25
Also, FWIW, my C-60, running 11.10 and Catalyst 12.3, seems to idle around 55-60 degrees.  Seems standard for a laptop cpu.  

When I upgrade to 12.04 I'll try to remember to check temps with the open-source driver and catalyst (if I go back to catalyst).

```

$ sensors
k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +58.5°C  (high = +70.0°C)
                       (crit = +115.0°C, hyst = +107.5°C)

```

---

### Post by jazz.h on 2012-04-26
> **ard213 said:**
> Catalyst 12.3  Are you satisfied with 12.3 drivers, suspend and hibernation working or not?

---

### Post by ard213 on 2012-04-26
> **jazz.h said:**
> Are you satisfied with 12.3 drivers, suspend and hibernation working or not?

Suspend and hibernate do not work, but I've upgraded my RAM after installing Ubuntu, so my swap isn't big enough -- regardless, I suspect that they wouldn't work anyway.

The performance (most noticeably on hulu and youtube) and battery life of my netbook is better with Catalyst than with the open-source drivers, so I choose to stick with Catalyst.  I may give the open source drivers a shot after upgrading to 12.04, though.  I had back to back 3-hour seminars this semester, and so I needed as much battery life as possible from my netbook.  It looks like that won't be the case next semester, so the video performance will dictate which driver I pick.

Hope this helps!

---

### Post by jazz.h on 2012-04-27
Nice strategy, reasonably thinking... :-) Thanks for the 12.3 report.

---

### Post by b1gag3 on 2012-04-28
After update from 11.10 to 12.04 wlan doesn't work anymore. After login a  message shows up, that the conncetion was terminated, but the systems  shows the connection as enabled without any networks. even if i reenable  the connection, no wlan is listed. blacklisting bcma doesn't work for me :/

---

### Post by ard213 on 2012-04-28
> **b1gag3 said:**
> After update from 11.10 to 12.04 wlan doesn't work anymore. After login a  message shows up, that the conncetion was terminated, but the systems  shows the connection as enabled without any networks. even if i reenable  the connection, no wlan is listed. blacklisting bcma doesn't work for me :/

FWIW, I just updated my netbook (AO722-0473) to 12.04, and have no issues with the wireless adapter.  In fact, the L.E.D. finally turns on (to orange) when the wifi is on.  In 11.10, that l.e.d. never came on.

I did notice a couple of things as I was upgrading, however:

1 - the upgrade process **seems** to crash right as it begins to install the new packages.  In fact, the updater was waiting for my input, but no window came up to let me know.  By clicking on the "show terminal" toggle on the updater window I was able to see a prompt, and after that installation proceeded as normal (I did need to answer yes or no to a handful of prompts through out).

2 - Though I opted to keep my old *sudoers *configuration file, I did update the *networkmanager.conf* file when prompted.  Perhaps this is why my wifi is working well?

Anyway, 12.04 seems to be working quite well so far.  I'm running the stock open drivers, and will report back on the performance after I have some more time with it.  At any rate, I won't change back to Catalyst until I feel that I'm missing something (performance, battery life, whatever).

hope this helps!

P.S. Oh yes, if you **are **running Catalyst, make sure to first uninstall it and rehabilitate the open drivers as per the _[catalyst wiki]("http://wiki.cchtml.com/index.php/Ubuntu")_.

---

### Post by biodojo on 2012-05-02
I just wanted to chime in that this is a great netbook for Ubuntu 11.04 and so far for 12.04. However, suspend isn't working with the Catalyst drivers via the Ubuntu Additional Drivers method or direct download of the 12.4 driver from AMD website for me. However, the Catalyst driver does improve battery life by a large margin (10 watts down to 7 watts for normal usage). 

We have just bought 200+ and will install Ubuntu for use in schools and I would love to get the battery life of the Catalyst driver combined with the suspend of the OSS driver. Any ideas, appreciated! We have hundreds of future Ubuntu users in our classrooms, and I want to give them the best experience possible! 

This is the 722-0369 model: C60 chip with AMD Radeon HD 6290

---

### Post by ard213 on 2012-05-02
I'd be interested in a way to suspend with catalyst as well, as I'm now back to using it.

Neither the stock radeon drivers nor those in the x-swat ppa gave me enough performance to stream in 720p from Hulu.  Video was laggy, and cpu temps shot up to 83 degrees.

With Catalyst 12.4, Hulu streams smoothly, and temperatures seem to peak around 75 degrees.

Boot and shut down times may be a bit faster with the radeon drivers, btw.

Cheers,

---

### Post by brub2 on 2012-05-04
To all of you who would like a functional suspend-resume with Catalyst, please put some pressure on this AMD bug file: [http://ati.cchtml.com/show_bug.cgi?id=327](http://ati.cchtml.com/show_bug.cgi?id=327). Also this Ubuntu bug: [http://bugs.launchpad.net/ubuntu/+source/linux/+bug/767975](http://bugs.launchpad.net/ubuntu/+source/linux/+bug/767975)

---

### Post by zzarko on 2012-05-04
There is also: [http://ati.cchtml.com/show_bug.cgi?id=199](http://ati.cchtml.com/show_bug.cgi?id=199). Unfortunately, it seems that [EMAIL="nobody@cchtml.com"]nobody@cchtml.com[/EMAIL] is always assigned to Linux AMD Catalyst issues...

---

### Post by biodojo on 2012-05-08
I have an issue with the internal mic on my 722 running 11.04. It works fine (with a bit of hum), but it randomly turns itself off. I have to go to Sound prefernces and check and uncheck the mute by the input and then it works fine for as long as I am recording, but if I stop recording, close whatever program I am using (sound recorder, audacity, webcam capture) and then try to record again later, I have to repeat the mic mute and unmute steps. Any ideas?

---

### Post by linlinas on 2012-05-16
hi, is anybody is aware of issue with Turbo Core on amd c60.
powernow-k2 module indicate only 2 pstates 1000 and 800.
Turbo Core should provide preformance boosting up to 1333 Mhz.
Please see my cpufreqd-info below

# cpufreq-info
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to [EMAIL="cpufreq@vger.kernel.org"]cpufreq@vger.kernel.org[/EMAIL], please.
analyzing CPU 0:
  driver: powernow-k8
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 1000 ns.
  hardware limits: 800 MHz - 1000 MHz
  available frequency steps: 1000 MHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 800 MHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz (asserted by call to hardware).
  cpufreq stats: 1000 MHz:0.49%, 800 MHz:99.51%  (1)
analyzing CPU 1:
  driver: powernow-k8
  CPUs which run at the same hardware frequency: 1
  CPUs which need to have their frequency coordinated by software: 1
  maximum transition latency: 1000 ns.
  hardware limits: 800 MHz - 1000 MHz
  available frequency steps: 1000 MHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 800 MHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz (asserted by call to hardware).
  cpufreq stats: 1000 MHz:0.49%, 800 MHz:99.51%  (1)

I have ao722 with Ubuntu 12.04, kernlel 3.2.0.24-generic-poe, bios 1.08

---

### Post by Fo2adZz on 2012-05-22
> **biodojo said:**
> I have an issue with the internal mic on my 722 running 11.04. It works fine (with a bit of hum), but it randomly turns itself off. I have to go to Sound prefernces and check and uncheck the mute by the input and then it works fine for as long as I am recording, but if I stop recording, close whatever program I am using (sound recorder, audacity, webcam capture) and then try to record again later, I have to repeat the mic mute and unmute steps. Any ideas?

If you are having no or extremely low sound from your internal microphone or even a hum noise please read the following information by David Hanningsson and everyone with an acer aspire 722 should report to the bugs he is trying to fix.
Link: [http://voices.canonical.com/david.henningsson/2012/05/22/three-audio-bugs-in-12-04/?utm_source=twitterfeed&utm_medium=twitter](http://voices.canonical.com/david.henningsson/2012/05/22/three-audio-bugs-in-12-04/?utm_source=twitterfeed&utm_medium=twitter)

---

### Post by ant2ne on 2012-05-23
The horror! 

I dropped my acer and cracked the screen. Now I need to get a replacement. I've been googling around and it looks like ebay sells this screen, but I need to verify some plugs and what not. I'm trying to figure out how to crack this thing open but I'm not having any luck. Does anyone know of any good disassembly videos out there on the internet somewhere? I've been googling but not much luck so I figured I'd ask here.

---

### Post by sea_dawg on 2012-05-23
Here is a forum dedicated to the Acer Aspire One laptops.  You may have better luck there.

[http://www.laptop-forums.com/acer-aspire-one-f126.html](http://www.laptop-forums.com/acer-aspire-one-f126.html)

---

### Post by biodojo on 2012-05-26
I had an Acer Aspire One 722 with the Atheros Wifi card and it worked fine on 11.04. So we bought 200 of them for our school. However these all came with the Broadcom BCM4313 wireless card and there are issues. It is using the brcmsmac driver and they connect initially. However after a time (sometimes just a few webpages) some of them lose connection. However, they still have an IP and network-manager says they are connected, but no pages load and you can't ping anything on the LAN or internet. A disconnect/reconnect can fix it, but sometimes a restart is required. It happens frequently so is a major issue.  Lots of broadcom drivers are blacklisted: bcm43xx, b43, brcm80211. Any ideas or experiences with the broadcom4313 card? Please save these computers from a Windows fate!

---

### Post by Fo2adZz on 2012-05-26
> **biodojo said:**
> I had an Acer Aspire One 722 with the Atheros Wifi card and it worked fine on 11.04. So we bought 200 of them for our school. However these all came with the Broadcom BCM4313 wireless card and there are issues. It is using the brcmsmac driver and they connect initially. However after a time (sometimes just a few webpages) some of them lose connection. However, they still have an IP and network-manager says they are connected, but no pages load and you can't ping anything on the LAN or internet. A disconnect/reconnect can fix it, but sometimes a restart is required. It happens frequently so is a major issue.  Lots of broadcom drivers are blacklisted: bcm43xx, b43, brcm80211. Any ideas or experiences with the broadcom4313 card? Please save these computers from a Windows fate!

In case of Broadcom wifi hardware, on newer releases of Ubuntu and Mint and maybe others, the *brcmsmac* open source driver handles the BCM4313 wireless card and does a decent job.  However, it is interfered with by an older one: *bcma*.  If you're seeing frequent random disconnections for wireless networks, try disabling *bcma* by blacklisting it: 
*sudo gedit /etc/modprobe.d/blacklist-bcma.conf* 
*blacklist bcma*

---

### Post by biodojo on 2012-05-29
I have done the step to blacklist bcma and still get spotty wifi. 

I also tried running tail -f /var/log/syslog on a machine that had an issue:

 wpa_supplicant[1029]: Failed to initiate AP scan.
last message repeated 61 times (which repeats every minute)

I am running 11.04 but perhaps 12.04 is worth a shot for updated drivers and the latest kernel.

---

### Post by antiplex on 2012-05-30
err... since i am just running the upgrade to 12.04 in the background and read about the spotty wifi: whats the easiest way to determine what kind of wifi-card is in my aspire one 722-C62bb (MFG-Date 1110)?

regarding the stuck upgrade processes: i also observed that it is necessary to open the terminal-section within the upgrade window and make several confirmations. as already mentioned, one thing asked here is the replacement of /etc/sudoers.
since i have jupiter installed, the diff results in
```
--- /etc/sudoers	2012-02-02 02:25:15.611400191 +0100
+++ /etc/sudoers.dpkg-new	2012-05-16 07:23:06.000000000 +0200
@@ -7,6 +7,7 @@
 # See the man page for details on how to write a sudoers file.
 #
 Defaults	env_reset
+Defaults	secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
 
 # Host alias specification
 
@@ -23,5 +24,6 @@
 # Allow members of group sudo to execute any command
 %sudo	ALL=(ALL:ALL) ALL
 
+# See sudoers(5) for more information on "#include" directives:
+
 #includedir /etc/sudoers.d
-%jupiter ALL=NOPASSWD: /usr/lib/jupiter/scripts/bluetooth, /usr/lib/jupiter/scripts/camera, /usr/lib/jupiter/scripts/cpu-control, /usr/lib/jupiter/scripts/resolutions, /usr/lib/jupiter/scripts/rotate, /usr/lib/jupiter/scripts/touchpad, /usr/lib/jupiter/scripts/vga-out, /usr/lib/jupiter/scripts/wifi

```
i guess it makes sense to replace the sudoers file but keep in mind that the last line showed above was removed in case jupiter doesn't work as expected afterwards.

EDIT: This is the diff of the NetworkManager.conf, i decided to replace it and accept the changes as a previous poster suggested. ```
--- /etc/NetworkManager/NetworkManager.conf	2012-02-15 12:17:27.479589675 +0100
+++ /etc/NetworkManager/NetworkManager.conf.dpkg-new	2012-04-30 16:44:17.000000000 +0200
@@ -1,8 +1,6 @@
-
 [main]
 plugins=ifupdown,keyfile
-
-no-auto-default=2a:a1:22:04:44:d2,dc:0e:a1:4d:e9:63,
+dns=dnsmasq
 
 [ifupdown]
 managed=false

```


cheers,
anti

---

### Post by biodojo on 2012-05-30
Easiest way to check wireless card is to type lspci in terminal. The last card listed is usually your wireless card.

---

### Post by antiplex on 2012-05-31
thanks biodojo,

i keep forgetting such simple commands, output however was (among others)
```
07:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)
```
so i seem to be lucky and have a atheros chipset (details to ar9485 [here]("http://www.qca.qualcomm.com/networking/brand.php?brand=3&product=105")) which up to now works flawless as expected.

cheers, anti

---

### Post by frojnd on 2012-05-31
> **linlinas said:**
> hi, is anybody is aware of issue with Turbo Core on amd c60.
powernow-k2 module indicate only 2 pstates 1000 and 800.
Turbo Core should provide preformance boosting up to 1333 Mhz.
Please see my cpufreqd-info below

# cpufreq-info
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to [EMAIL="cpufreq@vger.kernel.org"]cpufreq@vger.kernel.org[/EMAIL], please.
analyzing CPU 0:
  driver: powernow-k8
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 1000 ns.
  hardware limits: 800 MHz - 1000 MHz
  available frequency steps: 1000 MHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 800 MHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz (asserted by call to hardware).
  cpufreq stats: 1000 MHz:0.49%, 800 MHz:99.51%  (1)
analyzing CPU 1:
  driver: powernow-k8
  CPUs which run at the same hardware frequency: 1
  CPUs which need to have their frequency coordinated by software: 1
  maximum transition latency: 1000 ns.
  hardware limits: 800 MHz - 1000 MHz
  available frequency steps: 1000 MHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 800 MHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz (asserted by call to hardware).
  cpufreq stats: 1000 MHz:0.49%, 800 MHz:99.51%  (1)

I have ao722 with Ubuntu 12.04, kernlel 3.2.0.24-generic-poe, bios 1.08

I have just installed ubuntu 12.4 on this netbook (ao722) and I also have the same cpu-freq-info Have you found the solution? I have default installation everything worked out of the box for now. (I haven't tested bluetooth and SD card reader) But running on only 1000Mhz or 800Mhz is slow. Also I have noticed that ubuntu 12.4 is slooooow. At least default installation. Maybe because of the fact that I can't have 1333Mhz ? 

Any ideas suggestions and workarounds? The performace is really por on ubuntu 12.4 in compare to Windows 7. I can't belive this :( I'd install Archlinux on the netbook but it's not for me.

---

### Post by antiplex on 2012-06-04
hello!

regarding the cpu-frequency of 'only 800-1000 mhz' i just posted a quick explanation [in this other thread]("http://ubuntuforums.org/showthread.php?p=11996660#post11996660") dealing with the same issue.
oh, and i really have a hard time imagining that running windows7 on the acer 722 makes it any faster ;)
what exactly feels faster when running windows7? did you e.g. encode some video or compile a bigger piece of software?

regards,
anti

---

### Post by frojnd on 2012-06-04
Hi antiplex,

It's slower when opening applications. Eg. I click on a left menu and try to click on a let say software center and it needs a couple of seconds to opened. That's for every application. As in Windows 7 Professionals (I can't belive it either) when I click on a file browser it openes instantly. It's A LOT more responsive. Actually I suggestted my gf to use Windows 7 untill I don't resolve this issue. 

I've also noticed that when using open source ati drivers(default ones) youtube is doing fine only on 420p but not in full screen mode. I can't use it on 720p or 1080p. And I can't even use full screen with 420p or above...

I haven't done any compiling. The biggest application I tried was skye and wasn't able to configure internal microphone so it would work. I've followed this wiki: [https://help.ubuntu.com/community/AspireOne522#Sound](https://help.ubuntu.com/community/AspireOne522#Sound)

Unfortuantelly I can't paste the screenshot of alsamixer but maybe someone else can post it here and I can e-mail it to my gf.

Help much appriciated.

---

### Post by LewisTM on 2012-06-04
> **frojnd said:**
> Hi antiplex,

It's slower when opening applications. Eg. I click on a left menu and try to click on a let say software center and it needs a couple of seconds to opened. That's for every application. As in Windows 7 Professionals (I can't belive it either) when I click on a file browser it openes instantly. It's A LOT more responsive. Actually I suggestted my gf to use Windows 7 untill I don't resolve this issue. 

I've also noticed that when using open source ati drivers(default ones) youtube is doing fine only on 420p but not in full screen mode. I can't use it on 720p or 1080p. And I can't even use full screen with 420p or above...

I haven't done any compiling. The biggest application I tried was skye and wasn't able to configure internal microphone so it would work. I've followed this wiki: [https://help.ubuntu.com/community/AspireOne522#Sound](https://help.ubuntu.com/community/AspireOne522#Sound)

Unfortuantelly I can't paste the screenshot of alsamixer but maybe someone else can post it here and I can e-mail it to my gf.

Help much appriciated.
You really can't compare Ubuntu Software Center, which is probably the slowest app to start, to a Windows File browser, which is already loaded in memory. At least compare an instance of Nautilus.
I assume you are running stock Ubuntu. On this machine I'd recommend running a non-3D desktop environment like Unity 2D or Xfce. The machine is extremely responsive under Xubuntu.
Here's a [link]("http://ubuntuforums.org/showthread.php?t=1971229") to fixes for the microphone under 12.04, and [another]("http://ubuntuforums.org/showthread.php?t=1964850") more specific to Xubuntu.
As for video, see post #91. Umplayer helps tremendously for me. Some have [managed]("http://ubuntuforums.org/showthread.php?t=1487327") to set up mplayer to play flash videos in the browser but I haven't tried that yet. Also don't forget to install Jupiter and set it to the highest performance whenever you need to view high-res video.

Cheers!

---

### Post by antiplex on 2012-06-04
> **frojnd said:**
> It's slower when opening applications. Eg. I click on a left menu and try to click on a let say software center and it needs a couple of seconds to opened. 
...
I've also noticed that when using open source ati drivers(default ones) youtube is doing fine only on 420p but not in full screen mode. I can't use it on 720p or 1080p. And I can't even use full screen with 420p or above...


hi frojnd,

i agree that in therms of responsiveness, recent ubuntu-versions feel rather sluggish on small machines such as the aspire one 722.
as lewis pointed out, the software center is one of the worst, others follow. this is something that was well improved on windows7 and should improved on ubuntu as well. but in my view this is not likely to be related to the turbo-mode but i different user experience that one might need to get used to.

flash-video performance under linux was never great and probably never will be, lets hope flash dies quickly and e.g. webm finds its way to the masses.
one firefox-extension that made the youtube-experience a lot better (altough still not perfect) on the ao722 is [FlashVideoReplacer]("https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer"). using this addon leads to a initial delay/refresh of the page but allows you to either open webm-versions of videos in an external player (i successfully use vlc which performes very nice) or internally (html5).

i agree with lewistm that 3d desktops are not recommended on netbooks and for right now go with unity2d but might change back to good old gnome in the future since unity2d fights with its own deamons...

regards,
anti

---

### Post by brub2 on 2012-06-11
Interested by Catalyst with suspend and resume? Really, it seems possible to get a workaround. See my post on this subject here:
[http://forums.linuxmint.com/viewtopic.php?f=191&t=104875](http://forums.linuxmint.com/viewtopic.php?f=191&t=104875)

Even if I'm actually testing LMDE (based on debian), I'm pretty sure the same trick could be applied in recent ubuntus. If you find a way to improve the trick, please post!

---

### Post by biodojo on 2012-06-13
I am still struggling with wireless on the BCM4313 card models of the Acer Asipre One 722. We have 200 of them running 12.04 using the brcmsmac driver. They connect and can browse fine for awhile. However, when a decent load is put on the card (some video, a few webpages loading at once) the netbook can no longer ping anything. Network manager doesn't report disconnect and if I wait a minute, network traffic can resume. Does anyone have an Acer Aspire One with the BCM4313 card working reliably?

---

### Post by emilywind on 2012-06-18
As LewisTM mentioned, this netbook runs *much* better with Xubuntu rather than Ubuntu. For a while I was skeptical about how much better it would run, but I decided to give Xubuntu a shot.

The difference in responsiveness is night and day compared to Ubuntu and it even runs noticeably faster than Windows 7. Installing gnome Do also makes the whole desktop not only snappy but allows for a super efficient workflow as well.

I also timed boot times with a stop watch on this netbook. The booting was timed from selecting the option on GRUB to making it to a completely loaded login screen (skipped the desktop as those should vary most between Ubuntu and Xubuntu). Ordered from slowest to fastest.

Ubuntu - 65 seconds
Windows 7 - 46 seconds
Xubuntu - 20 seconds

As a note, I am still using the stock hard drive. I thought that Xubuntu felt like it booted faster as well as ran faster, but I was not sure. How much faster it turned out booting shocked me though, especially since it runs on the same base system as Ubuntu and both use lightdm for the login screen.

Nonetheless, Xubuntu won by a landslide. So if you want to use a *buntu on here and get notably better rather than worse performance than Windows 7, try Xubuntu. :)

**P.S.** To fix the brightness stepping bug with seems to plague all of the *ubuntus (the one where you get like 3 levels of brightness), check out [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/802276](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/802276) .

Specifically,

echo 0 > /sys/module/video/parameters/brightness_switch_enabled

fixed it for me. :) Can add that to /etc/rc.local to make it persistent across boots. :D

---

### Post by LewisTM on 2012-06-19
Thank you Emilywind for these numbers. Xubuntu being my distro of choice, I never bothered to compare.

From these results I do pity the ones running stock Ubuntu ;)

One last note: in order to keep GNOME dependencies at bay, I suggest you replace GNOME Do with Synapse. You won't be disappointed.

Cheers!

---

### Post by brub2 on 2012-06-21
Following post#166 on suspend/wake with catalyst:
As I said, I can manually get this laptop to wake on Mint Debian xfce. Basically, the idea is to do a manual suspend from a tty and type "sudo vbetool post" (in blind) after a wake.
I tried the trick on Xubuntu 12.04. The "vbetool post" command restores the backlight but all I get is a blinking cursor or flashing red blocks and vertical lines...

To biodojo (post #167): maybe you could try the proprietary driver. I don't know why but it has been activated automatically by Xubuntu on my AO722. I removed it and wifi still works but with strange numbers in connection speed (1 Mb/s). Since I focus on the catalyst problem, I didn't test wifi so much.

---

### Post by Makcum on 2012-06-27
> **biodojo said:**
> I am still struggling with wireless on the BCM4313 card models of the Acer Asipre One 722. We have 200 of them running 12.04 using the brcmsmac driver. They connect and can browse fine for awhile. However, when a decent load is put on the card (some video, a few webpages loading at once) the netbook can no longer ping anything. Network manager doesn't report disconnect and if I wait a minute, network traffic can resume. Does anyone have an Acer Aspire One with the BCM4313 card working reliably?

I have solved the wifi problem moreover it seems like no longer I have to set the ethernet adapter to be the first boot form bios or it was the case with lastes kernel update 3.2.0-26

My setup:
UBUNTU 12.04 - 64bits
wifi:  BCM4313

1. Add this to blacklist

 sudo gedit /etc/modprobe.d/blacklist.conf

> 
blacklist brcm80211
blacklist b43
blacklist brcmsmac
blacklist brcmfmac
blacklist ssb
blacklist bcma


2. add this to /etc/rc.local

> 
modprobe -r wl
sleep 10
modprobe wl


It has to be placed before 
exit 0



Fighting with SUSPEND/RESUME now - had a nice reusult like   PC goes to suspend and when almost OFF it comes back again. (from X.org to X.org)   :)

---

### Post by ard213 on 2012-07-02
> **Makcum said:**
> I have solved the wifi problem moreover it seems like no longer I have to set the ethernet adapter to be the first boot form bios or it was the case with lastes kernel update 3.2.0-26

My setup:
UBUNTU 12.04 - 64bits
wifi:  BCM4313

1. Add this to blacklist

 sudo gedit /etc/modprobe.d/blacklist.conf

2. add this to /etc/rc.local

It has to be placed before 
exit 0

Fighting with SUSPEND/RESUME now - had a nice reusult like   PC goes to suspend and when almost OFF it comes back again. (from X.org to X.org)   :)

I can confirm that this works.  I managed to boot straight to the HD with these modifications (my netbook has a BCM4313 as well).

Could I ask you to post a brief explanation of each step?  I assume that the first is nothing more than blacklisting drivers that may lead to conflcits, but I'm unfamiliar with modprobe, and would like to learn a bit more about what I have just done to my netbook :-)

---

### Post by Makcum on 2012-07-09
> **ard213 said:**
> I can confirm that this works.  I managed to boot straight to the HD with these modifications (my netbook has a BCM4313 as well).

Could I ask you to post a brief explanation of each step?  I assume that the first is nothing more than blacklisting drivers that may lead to conflcits, but I'm unfamiliar with modprobe, and would like to learn a bit more about what I have just done to my netbook :-)

in short.
It will unload the wifi module, wait for 10 seoconds and then load the wifi module again.

---

### Post by ard213 on 2012-07-11
That makes a lot of sense.  Thanks!

---

### Post by brub2 on 2012-07-16
Please Makcum (or anyone getting improvements with post#171) help me to clarify these things.

1) What do you get with this command: lspci -vnn | grep 14e4
Here I get [14e4:4727] BCM4313 (rev 01) and observe no problem with BOTH the open source (brcmsmac) driver or the proprietary one (wl). Maybe there are some hardware variations and this could explain why some have problems with the open source driver. Otherwise, I miss something...

2) Do you  have a (nearer) working suspend/wake (with catalyst) with your trick? Can you elaborate?

3) It may be related to 1) but if I activate the proprietary driver (wl) via the ubuntu applet, I don't have any of your blacklisted module in lsmod. As I understand, it is automatically done by the driver installation (a blacklist-bcm43.conf is written). In fact, on my system the proprietary driver was activated by default (xubuntu 12.04). I removed it to test the open source one. Later, I reactivated it. All with the "additional drivers" applet. So I don't see why I should manually blacklist these modules and manually load the wl module in  /etc/rc.local. I tried it anyway, but see no difference in suspend/wake.

---

### Post by brub2 on 2012-07-16
A little progress in the suspend/wake with catalyst saga. I managed how to get my trick works on xubuntu 12.04.

Here is what I do from the desktop:
1) CTRL-ALT-F1 and login on this text console.
2) sudo /usr/sbin/pm-suspend (have to enter the passwd since this is the first sudo)
3) press a key to wake the laptop => see nothing...
4) sudo vbetool post => I enter this command "in blind" and then the backlight appears with a blinking cursor
5) sudo /usr/sbin/pm-suspend => I also do this "in blind" (yes, a second sleep is required)
6) repeat steps 3 and 4
7) CTRL-ALT-F7 (or maybe CTRL-ALT-F8 => voilà! (return to the desktop)

No idea why I have to do it twice,  but it works. The GOOD part is that if I suspend the laptop from X after this, it works (until the next reboot)!!! I will have to test more to see if it's reliable. Right now, I'm with the wl (proprietary) wifi driver (I dont' know if it matters).

Now I would need help to simplify/improve the process. I could probably automate the "vbetool post" command in a script called lastly in  the wake process (/usr/lib/pm-utils/sleep.d/000kernel-change).

> **brub2 said:**
> 
Interested by Catalyst with suspend and resume? Really, it seems possible to get a workaround. See my post on this subject here:
[URL="http://forums.linuxmint.com/viewtopic.php?f=191&t=104875"]http://forums.linuxmint.com/viewtopic.php?f=191&t=104875
[/URL]

---

### Post by ard213 on 2012-07-19
> **brub2 said:**
> 

1) What do you get with this command: lspci -vnn | grep 14e4
Here I get [14e4:4727] BCM4313 (rev 01) 



I get the same output as yours, and I have never had problems with the open source driver either.  I followed the above instructions in an attempt to boot straight to the hard drive (i.e. without attempting to boot to ethernet first), and it worked.

I just uninstalled the broadcom driver, undid the blacklists and modprobe commands above, and was still able to boot straight to the hard drive without Ubuntu locking up.  I could swear that this was not possible before, but go figure.  Maybe I hadn't tested it with the latest stable kernel...

Fwiw, I'm now running kernel  3.2.0-26

---

### Post by ard213 on 2012-07-26
By the way, does anyone know how to get HDMI audio from the ao722 and Radeon drivers?  I have changed the grub line to
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.audio=1"
and updated grub, but I still cannot select the 2nd audio card on the ubuntu sound menu.  I have even tried booting up with the HDMI cable connected, but to no avail.

I can see the second sound card in alsamixer, but not in the ubuntu sound menu.

FWIW, I get perfect picture, but no sound...

thanks in advance,

---

### Post by biodojo on 2012-07-26
Does anyone else have the internal mic not work without toggling it off and on?

 I did the alsamixer tweak and the mic works, however I need to toggle the mic off and on to get it to start working. Then if I don't use the mic for awhile I have to toggle it off and on again. So it is like power saver is turning off the mic, but then audio recording programs (like audacity and webcam capture) aren't waking it back up.

---

### Post by mardibai on 2012-07-31
thank you very much for this useful thread!

---

### Post by antinea on 2012-08-06
hi all,

**1. Freezing after login (with unplugged network cable)**

for me,
This is caused by ethernet driver, not wireless.
Easy fix is to install an "ALX driver" instead of atl1c.

[http://www.linuxfoundation.org/collaborate/workgroups/networking/alx](http://www.linuxfoundation.org/collaborate/workgroups/networking/alx)


> 06:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v2.0 Fast Ethernet (rev c1)
07:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)


i recommend [http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5-1-snpc.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5-1-snpc.tar.bz2)

or most recently available here
[http://wireless.kernel.org/en/users/Download/stable/#compat-wireless_3.5_stable_releases](http://wireless.kernel.org/en/users/Download/stable/#compat-wireless_3.5_stable_releases)

---

### Post by ard213 on 2012-09-09
I just found out about this fix for the wifi on my A0722, and I thought I'd share it here:
[http://www.techdrivein.com/2012/09/slow-erratic-wifi-ubuntu1204-fixed.html](http://www.techdrivein.com/2012/09/slow-erratic-wifi-ubuntu1204-fixed.html)

At least since installing 12.04 (but perhaps this was true of 11.10 as well), I had extremely slow wifi when running on battery power.  It turns out that the stock network manager in Ubuntu was to blame, and installing Wicd in its place has fixed my problem.

The installation is simple, just install Wicd from the the stock repositories, and uninstall network-manager.  The only downside I've noticed so far is the loss of the network indicator in the top bar, but I can live with that.

here are the commands for this fix:
 ```
sudo apt-get install wicd 
sudo apt-get purge network-manager
```

Note that you'll have to select which users have access to Wicd when installing, so keep an eye out for that prompt.
Also, note that this calls for purging network-manager.  I don't know if this is stricly necessary, but at any rate keep in mind that you'll lose all of your network settings.

---

### Post by LewisTM on 2012-09-09
I don't see a difference in speed between AC and battery or between wicd and NM.
Maybe your wifi setup is particular. In any case, if I ever run into such a situation, I'll make sure to give wicd a try :guitar:

Cheers!

---

### Post by ard213 on 2012-09-15
A quick update on the wifi bug.

It turns out that the problem lies in the power control.  When running network-manager, wifi slows down when on battery power.  But running the following command on a terminal temporarily fixes things:

```
 /sbin/iwconfig eth1 power off
```I have filed a bug on launchpad, and the bug has already been marked as "confirmed."  Hopefully this means a fix will be released in the near future.

In case this issue affects you,  you might want to check out the bug I filed:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1051103](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1051103)

---

### Post by Robin Ahmed on 2012-09-23
thanks!

---

### Post by Bartoo on 2012-09-25
Problem with suspend/resume is solved with new catalyst 12.9

---

### Post by Fo2adZz on 2012-09-26
> **Bartoo said:**
> Problem with suspend/resume is solved with new catalyst 12.9
100% true :guitar: Finally catalyst is working on Ubuntu 12.04, but it doesn't yet support Ubuntu 12.10 (I tried it and didn't work properly) ... Also there is a new Firmware patch from  Acer for this netbook, but I didn't try it yet because I don't have windows installed on mine.

---

### Post by r_howie on 2012-09-29
> **Bartoo said:**
> Problem with suspend/resume is solved with new catalyst 12.9
Excellent news.

> **Fo2adZz said:**
> Finally catalyst is working on Ubuntu 12.04, but it doesn't yet support Ubuntu 12.10 (I tried it and didn't work properly) ... Also there is a new Firmware patch from  Acer for this netbook, but I didn't try it yet because I don't have windows installed on mine.
What does the new firmware improve/fix?

I will update the community guide [https://help.ubuntu.com/community/AspireOne522](https://help.ubuntu.com/community/AspireOne522) now. Please help us improve the guide, either by updating the wiki yourself or by messaging me.

---

### Post by LewisTM on 2012-09-29
Catalyst 12.9 is still in beta. I installed it and, yes it supports Suspend. However, I experienced crashes or malfunction on pretty much all video or OpenGL application I tried. Got me running back to the opensource driver.

I guess YMMV. Any success stories out there? Smooth, accelerated video with nice power management and suspend/resume functionality?

---

### Post by Bartoo on 2012-10-02
Since i installed 12.9 beta, I had no major problems. Once I found a screen crash (black and white rectangles on screen), but after restarting Unity all was fine. Movies are playing without tearing a basicly all seems to be fine. I'm just waiting for final version of driver.:lolflag:

---

### Post by ard213 on 2012-10-15
> **antinea said:**
> hi all,

**1. Freezing after login (with unplugged network cable)**

for me,
This is caused by ethernet driver, not wireless.
Easy fix is to install an &quot;ALX driver&quot; instead of atl1c.
  I just updated to 12.10, and this issue seems to be fixed (fingers crossed).  I was able to boot without the network option with no freezes.    

No fixes yet on the slow wifi on battery power (other than the temporary fix I posted above), but there's activity on the bug I filed, which is very promising.

---

### Post by ard213 on 2012-10-17
Has anyone here managed to update their BIOS using FreeDOS?  I was asked to update mine to the latest bios (1.8 ) to see if that cures my wifi problems, but so far have been unable to do so.

I have created a FreeBIOS bootable USB using unetbootin, copied the DOS folder from the Acer .zip file to that usb, and tried to run bios.bat (curiously named bios.bat.bat), but I get an error message.  Even if I try to run ```
flashit.exe /h
``` I get the same error message.

FWIW, I have an ao722-0473, running bios 1.5

I tried renaming bios.bat.bat to bios.bat, and have tried following the steps listed [here]("http://ubuntuforums.org/showpost.php?p=8922998&postcount=24"), but still had no success.

Any suggestions?

UPDATE:

Nevermind, got it.  It seems that when you boot into FreeDOS, you must choose option 5 (Live CD only), as opposed to the other two live CD options.  Also, you absolutely must be plugged into the AC for the bios to flash (though I'm sure I was every other time).

---

### Post by hamiljf on 2012-10-23
I had hopes, but... my netbook is a 522 and the boot on lan fix did not work for me.  Boots into (X)ububtu and freezes when asking for input.  Oh well...

---

### Post by Fo2adZz on 2012-10-25
A new Catalyst 12.10 driver is out :) I installed it and everything seems to work perfectly. I only noticed the HDMI video output for 1920x1080 not working.

---

### Post by jazz.h on 2012-10-26
Did you try 12.10 Catalyst on Ubuntu 12.10 :) (nice coincidence), or on Ubuntu 12.04?
Never mind for 1080p video reproduction, windows in dual boot will work for that perfectly through hdmi... :(
But if the temp and suspend will work with 12.10 drv on 12.04 Ubuntu it would be fine for me...

---

### Post by LewisTM on 2012-10-26
FYI the 12.9 Catalyst can be installed directly from within Ubuntu by selecting the fglrx-updates driver. Once enabled, it will support Suspend. For the first time, we have a fully functional, high-performance driver available through official channels :)

---

### Post by neu5eeCh on 2012-10-28
Just bought this laptop and am having all the aforementioned problems - installing 12.04.1. Specifically, changing boot order in BIOS (and enabling Network Boot) doesn't help one iota. So far, I'm reading through page 4 of this thread and I still can't figure out how to install Ubuntu. Is it necessary to install Ubuntu without a Network connection? I'm feeling pretty discouraged with this little laptop.

**Edit: **Hail Mary. Am installing Ubuntu with a wired connection (since wireless causes the laptop to lock up). Not sure what I'll do once the installation is done. Just start throwing all the different hacks at it, I guess. Maybe it will behave differently with a full install, but I'm not holding my breath.

**Edit: **OK. Wow. I just spent the morning and afternoon getting Ubuntu setup, and it was a complete waste of time. When I try to reboot, I either get a blank purple screen, a split screen or no screen at all. It's a complete mess. All of you seem to have gotten Linux to work on your Acer laptops, but I think my particular incarnation is simply not Linux compatible.

**Update:**  Nuked the Ubuntu/Unity installation. Installed Xubuntu/Voyager. Everything is sweet as cream. Faster. Smoother. No problems. Wireless works. Suspend works. Still some things I haven't tried, but night and day. Still haven't installed the closed source video drivers. Not sure I need to or am going to.

---

### Post by Fo2adZz on 2012-10-30
> **jazz.h said:**
> Did you try 12.10 Catalyst on Ubuntu 12.10 :) (nice coincidence), or on Ubuntu 12.04?
Never mind for 1080p video reproduction, windows in dual boot will work for that perfectly through hdmi... :(
But if the temp and suspend will work with 12.10 drv on 12.04 Ubuntu it would be fine for me...

Suspend works just perfectly (using Ubuntu 12.04) :popcorn: even youtube runs smoother now :guitar:

---

### Post by neu5eeCh on 2012-10-30
> **LewisTM said:**
> FYI the 12.9 Catalyst can be installed directly from within Ubuntu by selecting the fglrx-updates driver. Once enabled, it will support Suspend. For the first time, we have a fully functional, high-performance driver available through official channels :)

What do you mean "we" kemo sahbe? I installed 12.9 and it broke both hibernate and 
suspend. Still deciding whether to go back to open source where everything just worked.

---

### Post by ard213 on 2012-10-30
> **VTPoet said:**
> What do you mean "we" kemo sahbe? I installed 12.9 and it broke both hibernate and 
suspend. Still deciding whether to go back to open source where everything just worked.

Indeed. On my 722-0473, installing catalyst on 12.10 broke unity (or kept it from loading).  The open-source works well enough, but with shorter battery life than catalyst in 11.10.

---

### Post by LewisTM on 2012-10-30
I forgot to mention I was running Quantal. Did you upgrade? Maybe that makes a difference...

---

### Post by ard213 on 2012-10-30
Mine was an upgrade using a usb drive, not the software internal to ubuntu.  I had to test the Quantal for a bug I filed (shortly before it was released), so I figured I'd just install the latest beta anyway.

Maybe that's my problem.  But anyway, my system is up to date, so I don't imagine that this would make a big difference.

---

### Post by LewisTM on 2012-10-30
Okay so I'll try to backtrack a bit, maybe it will shed some light.

I tried to install Catalyst 12.10 in Quantal from the package found on the AMD website. It corresponds to driver version 9.002.

That did NOT work, I was left with a low-res desktop with no 3D capability. But instead of reverting to the Opensource drivers, I decided to install the proprietary fglrx-updates driver from Software Properties. After reboot, and to my surprise, I got a fully accelerated desktop with 3D and suspend working.

The Quantal driver is version 9.000. I assumed it corresponded to Catalyst 12.09 but I could be mistaken. Both the fglrx and fglrx-updates drivers are currently at that version.

More info:
Acer Aspire One 722-0465
Xubuntu 12.10 64 bit.
AMD Radeon HD 6290
BIOS: 012.036.000.029.041054
Driver package : 8.96.7-120312a-135598C-ATI
2D driver: 9.0.2
Catalyst Control Center v2.17
Randr v1.3
OpenGL version 4.2.11903

P.S. Compiz, and therefore Unity, is VERY buggy in 12.10. I cannot recommend enough to use a more basic and stable DE on this machine.

P.P.S Anyone got the mic working in 12.10 ?? :popcorn:

---

### Post by agastly on 2012-11-02
Working on friend's Acer Aspire One 722, on Mint 13.

Been doing lots of research with 'fixes' for the problem with the internal mic.
The  latest situation was that, using Audacity,  the mic volume was low,  accompanied by lots of background noise.  If I increased the volume  setting, the noise and signal both increased.
Silencing one channel  didn't help or make any real difference.  I tried the patch to invert  one channel, but the expected option in Alsamixer didn't show up.   

Zooming in on the waveform in Audacity, I noticed that it was 50Hz, ie our mains frequency. Ah, I thought, mains hum, unplug the mains.  Still had problem !

To cut a long story short, yesterday morning, I found that suddenly it was working!  No noise at all.  Later, I realised that the mains adapter was switched off, but plugged in.  I think one of the earlier steps had fixed the initial 'not working' problem, but I hadn't noticed as I was then following the noise issue.

So, in summary.  Mains plugged in - lots of noise.  Mains unplugged, still noise, but less, I think.  Mains plugged in but switched off - laptop now earthed? - it works nicely, so far. 

No sound on skype is next.

I hope that helps someone a bit.

---

### Post by neu5eeCh on 2012-11-02
More Info

Acer Aspire One 722-025  
Xubuntu 12.04 64 Bit
Atheros AR8152 v2. Fast Ethernet
Radeon HD 6290
ATI Wrestler HDMI Audio Radeon HD 6250/6310

Symptoms:

1.) Requires Network Boot Option First or Linux Boot-Up will lock up (requiring a hard reboot).

2.) Suspend works on open source driver. However:

2b.) Randomly boots to a [s]blank[/s] **black** screen after GRUB. Able to log in, but still only see a blank screen. Switching to TTY 1-6 is no help. 

3.) Installing FGLRX Updates works but then Suspend doesn't work (don't even mention hibernate).

The biggest problem right now is the [s]blank[/s] **black** screen at boot up. This appears to be random. 

I tried to the following solution:

Changing:

GRUB_CMDLINE_LINUX_DEFAULT=&#8221;"

to

GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet console=tty1 acpi_backlight=vendor acpi_osi=Linux acer_wmi.blacklist=yes mem=1920mb&#8221;

in etc/default/grub

From here: [http://askubuntu.com/questions/127180/12-04-boots-to-blackscree](http://askubuntu.com/questions/127180/12-04-boots-to-blackscree)

But the modification didn't help. I sometimes have to reboot 5 or 6 times to get 'X'. At this point, I still default to Windows as the better option. If I could solve the blank screen problem, that would be a game changer.

---

### Post by ard213 on 2012-11-04
VTPoet,

Just out of curiosity, are you running the STA broadcom drivers? I have a feeling that this driver fixed my boot issues (i.e. I no longer need "network boot").

---

### Post by neu5eeCh on 2012-11-08
> **ard213 said:**
> VTPoet,

Just out of curiosity, are you running the STA broadcom drivers? I have a feeling that this driver fixed my boot issues (i.e. I no longer need "network boot").

No. 

I've got an Atheros Chip. Here's the whole enchilada.

> 00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6290]
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Wrestler HDMI Audio [Radeon HD 6250/6310]
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:15.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:15.2 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB900 PCI to PCI bridge (PCIE port 2)
00:15.3 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB900 PCI to PCI bridge (PCIE port 3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
06:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v2.0 Fast Ethernet (rev c1)
07:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)

---

### Post by biodojo on 2012-11-16
On my AAO 722-0369 I just installed latest 12.10 Catalyst drivers from the AMD website on Ubuntu 12.04 and resume from suspend works. I am not sure if there is any graphics, performance, or battery life improvement yet.

---

### Post by brub2 on 2012-11-18
I have simplified my trick to have a workable suspend/wake with catalyst. I actually use Xubuntu 12.04. Here we go:

Configuration
============
Open a terminal and:
```
sudo VISUAL=/usr/bin/leafpad visudo
```
For each user on the laptop, add a line like this (replace bruno with user name):
```
%bruno ALL=(ALL:ALL) NOPASSWD:/usr/sbin/pm-suspend
```
Then, create a file in your ~/bin directory (or anywhere else in your $path). Name this file with a very short name easy to remember and to type "in blind". Here I choose the name "ve" (in french, veille means suspend). Make it executable (change its permission). Edit this file and add this line:
```
sudo /usr/sbin/pm-suspend
```

Using the trick
============
For the first suspend (after a fresh boot), you have to: 
1) press CTRL-ALT-F1 and login on this text console
2) enter your command (the short name, for me: "ve") => the laptop goes to sleep
3) press a key to wake the laptop => see nothing...
4) type your command again (in blind) => the laptop goes to sleep again
5) press a key to wake the laptop => see nothing...
6) press CTRL-ALT-F7 to return to X

After, you can sleep and resume from the graphical interface until the next reboot. Yes, there is a trick for the first sleep, but it is now very simple to execute. Enjoy!


> **brub2 said:**
> A little progress in the suspend/wake with catalyst saga. I managed how to get my trick works on xubuntu 12.04.

Here is what I do from the desktop:
1) CTRL-ALT-F1 and login on this text console.
2) sudo /usr/sbin/pm-suspend (have to enter the passwd since this is the first sudo)
3) press a key to wake the laptop => see nothing...
4) sudo vbetool post => I enter this command "in blind" and then the backlight appears with a blinking cursor
5) sudo /usr/sbin/pm-suspend => I also do this "in blind" (yes, a second sleep is required)
6) repeat steps 3 and 4
7) CTRL-ALT-F7 (or maybe CTRL-ALT-F8 => voilà! (return to the desktop)

No idea why I have to do it twice,  but it works. The GOOD part is that if I suspend the laptop from X after this, it works (until the next reboot)!!! I will have to test more to see if it's reliable. Right now, I'm with the wl (proprietary) wifi driver (I dont' know if it matters).

Now I would need help to simplify/improve the process. I could probably automate the "vbetool post" command in a script called lastly in  the wake process (/usr/lib/pm-utils/sleep.d/000kernel-change).


[/URL]

---

### Post by frojnd on 2012-11-23
I have one "huge" problem and one not so huge problem:

1) Huge problem, how to set up internal microphone so it will work with skype, google video chat?

2) How to make boot time any less longer? I setup autologin disabled bluetooth service and some other that I don't need and boot time is taking way too long, about 45 seconds with autologin and about 60 seconds if requesting password.

Any tips how can I make boot time shorter? What services I don't need? It takes about 20 seconds from GRUB menu to the image where Xubuntu logo is loading. I think I have a bad configuration.

System I have: Xubuntu 12.10 fresh install
bootchart: bootchart (see attachment)

Please upload your bootchart and specify what system you have Ubuntu / Xubuntu and release name.

EDIT: Here is the direct link to the image due to bad attachment: [http://i.imgur.com/RT2nJ.png?1](http://i.imgur.com/RT2nJ.png?1)

---

### Post by frojnd on 2012-11-23
And here is the bootchart while on battery and autologin: [http://i.imgur.com/RKBLX.png](http://i.imgur.com/RKBLX.png) 
~70 seconds :o

---

### Post by LewisTM on 2012-11-23
Honestly, I'd recommend you install Xubuntu 12.04 LTS.
12.10 boots slower and the mic does not work no matter what. There are [tutorials]("http://bernaerts.dyndns.org/linux/251-ubuntu-precise-acer-ao722") for 12.04 and this thread is also helpful. You can still install Xfce 4.10 through PPA and enjoy most of the improvements.

Cheers!

---

### Post by frojnd on 2012-11-24
After Xubuntu 12.10 booted it was way more responsive than 12.04 (and I mean WAY MORE FASTER) and the blame goes to fglxrx drivers install. In Xubuntu 12.04 I wasn't able to install fglrx drivers within additiona drivers menu in Xubuntu. Also in 12.10 I'm able to suspend to RAM.

If I can do this on 12.4 I'd glad to switch to 12.4


Oh and one of the reason I switched to 12.10 was because I had this random black screens while booting! With 12.10 I disabled boot priority first for ethhernet and those problems are gone -> using Broadcom chipset.

If I can pass through those two limitations I'd switch immediately, but in 12.4 was not able to boot when black screen and this is kinda frustrating.

---

### Post by jazz.h on 2012-12-05
Hi!
I wonder if anyone has tried the new bios v 1.11 (13-NOV-2012)  for this little fellow...and report if some of the issues exposed here  are resolved...
[http://support.acer.com/us/en/product/default.aspx?tab=5&modelId=3658](http://support.acer.com/us/en/product/default.aspx?tab=5&modelId=3658)

---

### Post by ard213 on 2012-12-09
> **jazz.h said:**
> Hi!
I wonder if anyone has tried the new bios v 1.11 (13-NOV-2012)  for this little fellow...and report if some of the issues exposed here  are resolved...
[http://support.acer.com/us/en/product/default.aspx?tab=5&modelId=3658](http://support.acer.com/us/en/product/default.aspx?tab=5&modelId=3658)

I am now running the latest BIOS, and have nothing to report.  The computer still works, but I have not noticed any change from 1.08.  FWIW, my computer is a 722-0473

I do have a quick note on another matter:

When running radeon drivers on 12.10, I often had boot issues (computer would crash at blank/purple screens).  Installing the ATI catalyst drivers fixed that.  The installation was a pain, however (LewisTM had posted about this, IIRC).  Installing the fglrx drivers that come packaged in ubuntu would break Unity, as would a manual install from ATI's website.  

The solution was to install the drivers manually (as per [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide) ) and then install the fglrx-updates from the ubuntu repositories.  This has to be done with unity broken, so start a terminal with ```
 ctrl+alt+t,
``` then run ```
software-center-gtk3
```.  The computer will be VERY slow, but stick with it.  From this point on you should be able to navigate to "software sources" and install the fglrx-updates.  Upon reboot, Unity was fixed (and my battery life was much improved, as was the case with catalyst and Oneiric).

FWIW, I understand that many people run Xubuntu or Lubuntu happily, but I find that Unity makes my life easier (launching documents from the dash is a huge time-saver), and so I stick to the regular distro.  My performance may suffer a bit, but nothing major.  To each their own, but this is just to say that vanilla Ubuntu can work with this netbook.

---

### Post by jazz.h on 2012-12-11
[I]>>I am now running the latest BIOS, and have nothing to report.

[/I]I have discovered that the freeze, which used to happen if the network boot was not the 1st boot choice in BIOS... is solved now!

---

### Post by ard213 on 2012-12-11
> **jazz.h said:**
> [I]>>I am now running the latest BIOS, and have nothing to report.

[/I]I have discovered that the freeze, which used to happen if the network boot was not the 1st boot choice in BIOS... is solved now!

For me, that was solved by the STA wireless driver, but good to know!

---

### Post by Pharee on 2012-12-12
> **jazz.h said:**
> [I]>>I am now running the latest BIOS, and have nothing to report.

[/I]I have discovered that the freeze, which used to happen if the network boot was not the 1st boot choice in BIOS... is solved now!


Hi. jazz.h whitch version of ubuntu are you using? In 12.10 that issue is solved without upgrading bios :)

Guys, what about sleep mode after the latest updates, on my ao722 c-60 ubuntu 12.04.1 with catalyst 9.002 its not working again :/

---

### Post by ard213 on 2012-12-13
> **Pharee said:**
> 
Guys, what about sleep mode after the latest updates, on my ao722 c-60 ubuntu 12.04.1 with catalyst 9.002 its not working again :/

I'm running catalyst and 12.10 on my 722,  and ***suspend*** works perfectly.  I have not tested ***hibernate*** (which is still grayed out -- perhaps there is a way around that).

---

### Post by jazz.h on 2012-12-14
I'm currently on Mint 13 KDE, meaning Ubuntu 12.04.
Suspend works great, without catalyst drivers.
Hibernate is by default disabled in KDE, haven't tried that, I'm used to avoide hibernate anyway because of tripple boot...

---

### Post by ant2ne on 2012-12-14
I got no gnome-shell with the open source drivers. With the fglrx drivers I got no suspend. Sure would like to get get both.

Update: I think I got it. The latest and greatest proprietary drivers have addressed the issue of suspend. To install I created and ran the following script...
```
#!/bin/bash
cd /usr/src
sh /usr/share/ati/amd-uninstall.sh
apt-get remove --purge -y fglrx xserver-xorg-video-radeon 
apt-get remove --purge -y xserver-xorg-video-ati xserver-xorg-video-radeon
apt-get remove --purge -y fglrx*
wget http://www2.ati.com/drivers/linux/amd-driver-installer-catalyst-12.10-x86.x86_64.zip
unzip ./amd-driver-installer-catalyst-12.10-x86.x86_64.zip
chmod +x ./*.run
sh ./amd-driver-installer-catalyst-12.10-x86.x86_64.run
```

I suppose I should mention that I'm using 12.04.

---

### Post by ard213 on 2012-12-18
I just replaced the HDD in my AO722 with an Intel 330 SSD (60GB), and in the process of re-installing the system I struggled once again to get catalyst installed.  Neither the fglrx or fglrx-updates in the repositories or catalyst 12.10 would install without breaking unity.

The answer, in the end, was really simple: I needed to install linux-headers-generic before catalyst could work.

I just ran the following, and rebooted when it was done, and the system is running perfectly well:

```
 sudo apt-get install linux-headers-generic fglrx-updates

```Hopefully this will help some of you.

Also, the SSD is really nice so far (boot up and shut down are very fast) :-)

---

### Post by ant2ne on 2012-12-19
> **ard213 said:**
> I just replaced the HDD in my AO722 with an Intel 330 SSD (60GB), and in the process of re-installing the system I struggled once again to get catalyst installed.  Neither the fglrx or fglrx-updates in the repositories or catalyst 12.10 would install without breaking unity.

The answer, in the end, was really simple: I needed to install linux-headers-generic before catalyst could work.

I just ran the following, and rebooted when it was done, and the system is running perfectly well:

```
 sudo apt-get install linux-headers-generic fglrx-updates

```Hopefully this will help some of you.

Also, the SSD is really nice so far (boot up and shut down are very fast) :-)*forehead smack* I bet that is why my gnome-shell didn't work either. I could install fglrx-updates but it wouldn't log in as gnome-shell. I'm thinking that my method (above) isn't ideal because the system feels a little more sluggish than it did under mint. 

As fate would have it, I'm right now looking at SSDs for mine. I don't suppose you could link me to the one you just purchased if you are happy with it. What kind of battery life improvement have you noticed?

---

### Post by ard213 on 2012-12-20
> **ant2ne said:**
> *forehead smack* I bet that is why my gnome-shell didn't work either. I could install fglrx-updates but it wouldn't log in as gnome-shell. I'm thinking that my method (above) isn't ideal because the system feels a little more sluggish than it did under mint. 

As fate would have it, I'm right now looking at SSDs for mine. I don't suppose you could link me to the one you just purchased if you are happy with it. What kind of battery life improvement have you noticed?

The SSD I bought is this [one]("http://www.amazon.com/gp/product/B007P71IM0/ref=oh_details_o00_s00_i00").  The price is a bit high now, so I'd wait till it comes down again.  I bought the 60GB one for $59.99. 

I haven't had it long enough to see how the battery life has changed, but I'll post an update once I have a few weeks of use under my belt :-)

---

### Post by ant2ne on 2012-12-26
> **ard213 said:**
> I just replaced the HDD in my AO722 with an Intel 330 SSD (60GB), and in the process of re-installing the system I struggled once again to get catalyst installed.  Neither the fglrx or fglrx-updates in the repositories or catalyst 12.10 would install without breaking unity.

The answer, in the end, was really simple: I needed to install linux-headers-generic before catalyst could work.

I just ran the following, and rebooted when it was done, and the system is running perfectly well:

```
 sudo apt-get install linux-headers-generic fglrx-updates

```Hopefully this will help some of you.

Also, the SSD is really nice so far (boot up and shut down are very fast) :-)I got my SSD and did a re-install. I tried this method, but with these fglrx-updates I still got now suspend and resume. Which is a bug fixed in the latest proprietary from their website.

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx")

Does suspend and resume work for you with fglrx? Is there some other step I'm missing?

---

### Post by ard213 on 2012-12-26
> **ant2ne said:**
> 

Does suspend and resume work for you with fglrx? Is there some other step I'm missing?
 
Not sure why our systems aren't working the same way, but I'm running fglrx-updates, and suspend and resume work perfectly.  I did try to install catalyst 12.10 before purging it and installing fglrx-updates alongside linux-headers-generic.  Perhaps something  from catalyst 12.10 stuck around and allowed suspend/resume to work?  Go figure.

How do you like the SSD so far?  I'm seeing some battery life improvement, but I haven't sat down and tried to figure out how much yet...

The main improvements I'm seeing are boot-up & shut down, which are really fast, and the time it takes to save large files in libreoffice.  My netbook used to lag for a few seconds when working on large papers, but now  *ctrl+s* is lightning fast!

---

### Post by wolftune on 2013-01-07
A note for everyone who might come across this:

Most of the details are at the community page:
[https://help.ubuntu.com/community/AspireOne722](https://help.ubuntu.com/community/AspireOne722)

And much of what's on this forum is outdated. If you download the latest stable Catalyst drivers directly from AMD's website, they work flawlessly. All the other issues are basically fixed with the latest BIOS the broadcom proprietary drivers and/or the more recent kernel. The kernel in 12.10, i.e. Linux 3.5 (or later of course) basically deals with the last remaining possible issues.

I've got everything work well on my system.

---

### Post by r_howie on 2013-01-23
> **wolftune said:**
> A note for everyone who might come across this:

Most of the details are at the community page:
[https://help.ubuntu.com/community/AspireOne722](https://help.ubuntu.com/community/AspireOne722)

Hey wolftune, thanks for your work (also on the Wiki guides).

However, because the AO522 and the AO722 are essentially the same machine, I'd rather we focus our efforts on a single page ([https://help.ubuntu.com/community/AspireOne522](https://help.ubuntu.com/community/AspireOne522)), to avoid dispersion of information and duplicating the same work too. In my opinion anyway. :)

---

### Post by LewisTM on 2013-02-20
I have made some progress with the microphone in 12.10. It seems to be working OK now.
I tinkered with the sound settings in alsamixer. I found that the internal mic was functional only when it was set as the only CAPTURE device, which can be toggled with the spacebar. To properly initialize the mic, I had to set the Mic volume as well as both Mic Boost controls to max, toggle the red CAPTURE to Mic then back to 'Internal Mic'. 

I have attached a screenshot as well as a working asound.state file which should be placed in /var/lib/alsa and applied at login with [FONT="Courier New"]alsactl restore[/FONT].

Hope this helps someone!

---

