---
title: "Hybrid Graphics ATI/AMD Discrete &amp; Intel Integrated Cards"
date: 2011-12-31
forum: Hardware
---

### Post by prd25 on 2011-12-31
I have an AMD Radeon HD 6700M Series graphics card and a 2nd generation Intel i7 processor with an integrated graphics controller.  I am having issues getting the AMD card to work.  Whenever I try updating the drivers for it and installing Catalyst, the system crashes, and I can reboot only into the terminal, not the GUI.  I have tried several methods of getting the card to work listed on this forum and on other sites, although it's definitely possible a solution is out there that I didn't find.  One thing that I found but haven't really looked into is the switcheroo command.  Anyone think this would do the trick?  Anyway, is this a common problem with Ubuntu 11.10 (Oneiric) and the Unity desktop and are there any ideas for  troubleshooting this?  Any help is appreciated.

A related bit of into I found interesting was that I was not able to get compiz to work until I went into the BIOS and change the option from "dynamic" to "fixed" for how operating systems handle the two graphics cards.  As the AMD card is disabled in ubuntu, I'm assuming that the Intel integrated card was the one chosen after I set the option to "fixed."  After doing this, compiz and compiz fusion worked, 3D cube rotation and everything.  Would be nice to have the more powerful AMD card working though.

---

### Post by MoreOrLess on 2012-01-01
'Fixed' uses the discrete AMD card, and since you have installed Catalyst, this is the only way it will work. It's good for performance, but not good for battery.

You can verify you're using the AMD card by looking at /var/log/Xorg.0.log

---

### Post by prd25 on 2012-01-01
I checked /var/log/Xorg.0.log and saw info on the Intel integrated graphics card but no mention of the ATI card.  

After, I tried reactivating the ATI driver and reinstalling catalyst.  2 ATI drivers were listed under "Additional Drivers," one with post-release updates and one without.  The one with post-release updates does not activate without an error but the one without the updates can be activated.  Also, the installation seemed to go smoothly, except whenever I entered fglrx into the terminal I got an error:

[I]X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  155 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12[/I]

Rebooting the system failed to load Ubuntu (said [fail] next to something about being able to generate crash reports), so I had to go into the recovery mode to get into the terminal and replace the xorg.conf file with its backup.  This allowed me to load Ubuntu and type this reply...

However, typing ```
sudo amdcccle
``` gives:

[I]There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.

No AMD graphics driver is installed, or the AMD driver is not functioning properly.
Please install the AMD driver appropriate for you AMD hardware, or configure using aticonfig.[/I]

When I try ```
sudo apt-get install fglrx
``` I get in return:


[I]E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/I]

I am guessing the problem has to do with fglrx, but I'm still confused as to why whenever I modify the xorg.conf file by installing catalyst, the OS has trouble loading.

---

### Post by MoreOrLess on 2012-01-01
Maybe 'fixed' only uses the intel card, in which case Catalyst is a no go.

---

### Post by prd25 on 2012-01-01
[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide)
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

seems like quite a few resources attempt to address this problem.  so far i've had no luck with them =(.

---

### Post by MoreOrLess on 2012-01-02
There are some commands to switch back and forth using Catalyst, but I haven't seen reports of success using them: [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Hybrid_Graphics_and_Catalyst](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Hybrid_Graphics_and_Catalyst)

---

### Post by prd25 on 2012-01-02
I can install Catalyst, and when I go under "Additional Drivers" it says the ATI drivers are activated and currently in use.  However, I cannot (or do not know how to) alter the xorg.conf file.  Use of ```
sudo aticonfig --initial -f
``` causes me to have to load the system in recovery mode and replace the xorg.conf file with its backup in order to load ubuntu normally again.

---

### Post by prd25 on 2012-01-02
I can use the open source ATI drivers though with the BIOS set to 'dynamic'.  Compiz fusion and some games seem to work fine...haven't tried more graphically intensive applications.

---

### Post by markackerman8@gmail.com on 2012-01-14
This same problem is killing my 4 years in Ubuntu without Microsoft - Arghhhhhhh.

Someone must have a solution for the thousands of new computers with intel integrated and amd/ati discrete card combos.  

Unlike so many others I ONLY care about being able to use the Discrete card as that is why I  paid $2000 for this envy 17-2195.

Can someone PLEASE help me with this - I keep searching week after week for a solution to get me out of windows !!!!

PLEASE !!!!!!!!!!!!!!
Mark
[email]markackerman8@gmail.com[/email]

---

### Post by Mark Phelps on 2012-01-15
> **markackerman8@gmail.com said:**
> Someone must have a solution for the thousands of new computers with intel integrated and amd/ati discrete card combos. 
Read the link below:

[https://help.ubuntu.com/community/HybridGraphics]("https://help.ubuntu.com/community/HybridGraphics")

> Unlike so many others I ONLY care about being able to use the Discrete card as that is why I  paid $2000 for this envy 17-2195.

Then, you should have done your research BEFORE you shelled out the money!  Linux has a long-established reputation of having to play catchup to new MS-Windows-only hardware features.

---

### Post by markackerman8@gmail.com on 2012-02-17
Just a bump here for anyone with any new info to help us. Here is what I have done so far ...

The last thing in my many attempts was to reinstall ubuntu to install the amd/ati driver thru additionhal drivers (post release) as I read that this was the only one to work with vgaswitcheroo. Oddly after the reinstall of Ubuntu 11.10 and no updates I saw the switch file (/sys/kernel/debug/vgaswitcheroo/switch) for my first time (Ubuntu 3.0.0-12) (no additional driver yet). Then I tried to install the ati driver no luck - errors so I thought I should update Ubuntu - restart and try again. After the restart my kernel was at 3.0.0-16 from 12, and no /sys/kernel/debug/vgaswitcheroo folder at all arghh going backwards now pls pls help.
Mark
-----------------

here is a sumary of some of the things I have tried to date:
For 2 months and over 100 hours, I have been trying to get my new HP Envy 2195ca working with the Swichable dedicated AMD/ATI HD 6850m graphics card and not the embedded Intel hd3000 low end card, with no success. I think perhaps I am missing something basic and don't know what it is??? Here is what I have tried (part thereof) :
&#8227; Installed using additional drivers - seemingly successfully - ie. says enabled, and active and green dot, but
• running ATI's CCC gives:
&#8728; There was a problem initializing Catalyst Control Center Linux edition. It could be caused by the following.
&#8728; No AMD graphics driver is installed, or the AMD driver is not functioning properly.
&#8728; Please install the AMD driver appropriate for you AMD hardware, or configure using aticonfig.
&#8227; Installed from the amd website: amd-driver-installer-12-1-x86.x86_64.run, (previous version over the past 2 months as well)
• created the 3 debian packages seemingly successfully and installed all three:
&#8728; fglrx_8.930-0ubuntu1_amd64.deb, plus 2 similarly named ones
• For the first time using 12.1 today I seemingly successfully ran:
&#8728; aticonfig --initial -f, with no errors BUTTTTTT
&#8227; after a reboot just a black screen with a few tiny white dots flicking around
• and safe mode works fine
• I can get back into Ubuntu Normal mode by deleting
&#8728; /etc/X11/xorg.conf (perhaps I just need the right file contents for switchable graphics)
&#8227; Again PLEASE HELP. and Thanks in advance
&#8227; Here is some additional information
• lspci -nn | grep VGA
&#8728; 00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
&#8728; 01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Broadway [ATI Mobility Radeon HD 6800 Series] [1002:68a8]
• Recommended configuration for X.org
&#8728; No configuration is necessary for ATI driver in the modern versions of Ubuntu. You can safely take away your xorg.conf and your computer will run fine.
• To see if your driver uses KMS (Kernel Mode Setting), run command
&#8728; ack@Arawn:~$ dmesg | grep drm
[ 9.153946] [drm] Initialized drm 1.1.0 20060810
[ 9.400960] [drm] MTRR allocation failed. Graphics performance may suffer.
[ 9.402250] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[ 9.402255] [drm] Driver supports precise vblank timestamp query.
[ 13.040646] fbcon: inteldrmfb (fb0) is primary device
[ 13.040932] fb0: inteldrmfb frame buffer device
[ 13.040935] drm: registered panic notifier
[ 13.049332] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0


• vgaswitcheroo
&#8728; Never has worked and probably because there is NEVER a file called
&#8227; /sys/kernel/debug/vgaswitcheroo/switch
&#8227; root@Arawn:/home/ack# echo DIGD > /sys/kernel/debug/vgaswitcheroo/switch
• bash: /sys/kernel/debug/vgaswitcheroo/switch: No such file or directory
&#8728; root@Arawn:/home/ack# grep -i switcheroo /boot/config-3.0.*
&#8227; /boot/config-3.0.0-16-generic:CONFIG_VGA_SWITCHEROO=y
&#8728; To test if vga_switcheroo is enabled, look for the switch file:
&#8227; ls -l /sys/kernel/debug/vgaswitcheroo/switch
• ls: cannot access /sys/kernel/debug/vgaswitcheroo/switch: No such file or directory
&#8728; never once had this switch file with or without open source/fglrx/ or no driver at all
&#8227; Apparently, If you are not using the open-source radeon driver (or the nouveau driver in case of nvidia hardware), there won't be a /sys/kernel/debug/vgaswitcheroo/switch file.
• hmmmmmm tried a reinstall as stated at the top of this post which left me with no /vgaswitcheroo FOLDER or /switch file

HEELppppPPPPP PLEASE
Mark

---

### Post by Alexislavie on 2012-02-23
Check this post : [ http://ubuntuforums.org/showthread.php?p=11712748]("http://ubuntuforums.org/showthread.php?p=11712748")

---

