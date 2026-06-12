---
title: "Acer Aspire 5920 ubuntu do not work"
date: 2007-07-30
forum: Hardware &amp; Laptops
---

### Post by thestranger on 2007-07-30
hi
i've just bought acer aspire 5920 and i've tried to install ubuntu 7.04  i386 but 've encountered the standard error ```
/bin/sh can’t access tty; job control mode off
```
so i've tried the text installation and worked fine. When i've rebooted xorg doesn't work due to a screen not found (or configuration ) error.
I've tried ubuntu alternate amd64 but with the same xorg error ...

The 6.06lts amd64 seems to work fine and starts whitout problems, it also discovered and use the audio subsystem but the screen is black with every configuration (neither driver nor vesa)

Can anybody help me...thanks :(

---

### Post by errenay on 2007-08-01
I have installed Kubuntu 7.04 32 bit from alternate CD. During the installation I added resolution "1280x800". After the installation there were problems with blank screen (xorg couldn't find screens). The solution: in GRUB screen edit the kernel parameters (remove "splash quiet") and change the "Driver" in Xorg.conf from "nv" to "vesa". Then I installed the binary drivers from NVIDIA:
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)
Hope it helps.

---

### Post by frenchcr on 2007-08-18
I too had the same problems but in my workaround I didnt need to use the alternate CD, found the easiest fix on ubuntu forums which enables you to still perform live CD install...you can find it here...  [http://allostalk.com/showthread.php?t=500418]("http://allostalk.com/showthread.php?t=500418")  **You will find the solution in post #4 of this thread**. Follow the instructions underneath where it says..."if you are getting this error (and you have a SATA harddrive); this is the fix:"

Once I installed, my sound was not working straight away, the fix was simple...go into sound preferences and enable surround then unmute some others (front was one of them).

I installed nvidia driver using Envy (dont use Automatix2, its nividia driver gave me a black screen after ubuntu splash loaded).

*NOTE: if you do the Envy way, then remember at a later date, when you want to upgrade the kernel (trying to get wireless to work, or dist upgrade) you'll have to uninstall the nvidia driver then Envy before you change the kernel and switch 'nvidia' to 'vesa' in /etc/X11/xorg.conf. Then once youve changed the kernel you can reinstall envy and nvidia driver. Any other way gave me the black screen syndrome.*

Once Envy kindly installed the correct driver for my 8600M GT, i realised I still couldnt change screen resolution in System > Preferences > Screen Resolution. So went into Applications > System Tools > Nvidia Settings where I could change it there. Then in the section X Server Display Configuration in Nvidia Settings, theres a button that says Save to X11 Configuration File this lets you preview the xorg.conf before you save it...copied this xorg.conf and swapped it with my original xorg.conf manually (as root)...this gave me the 1280X800 option in System > Preferences > Screen Resolution :)

**Compiz Fusion**: Once the graphics driver was sorted **I simply followed the instructions in post #1 in the following thread...**

[http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz+fusion]("http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz+fusion")

...abracadabra...Compiz Fusion worked first time in all its glory! :)

PS. For those considering dual boot...im dual booting with Vista...see...

[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first")

i deleted the 10Gb destructive recovery partition and have formatted this as NTFS where i swap files between Vista and Ubuntu. In the D:/ Data drive size ~70Gb I slotted ubuntu in there and have Linux swap in a 2Gb partition on the far right end of the partition table. It works beautifully and is  good way to allocate space efficiently. Just dont get a virus in vista if you do it this way or your 100 bucks for a new install disc.

---

### Post by simonloach on 2007-08-23
Almost working perfectly the only problem is that when ubuntu starts i have to type modprobe piix every time. I've followed the instructions to add piix to /etc/initramfs-tools/modules but that  doesn't seem to fix it. Any help is appreciated.

Simon

---

### Post by frenchcr on 2007-08-24
In the link below

[http://allostalk.com/showthread.php?t=500418](http://allostalk.com/showthread.php?t=500418)

there was a bit saying

> Just to simplify a little, however, after the command (in the chroot env):
> sudo echo piix >> /etc/initramfs-tools/modules
> all I needed to do is issue the command
> sudo update-initramfs -u
> to update the initramfs (thus correcting the system) and then
> exit
>

did you follow this and do...

sudo update-initramfs -u

---

### Post by simonloach on 2007-08-24
Followed it exactly, a few times just to make sure. I've also noticed that I don't need to type modprobe piix at the command prompt that comes up, just typing exit loads the ubuntu login screen.

---

### Post by DSF_70 on 2007-08-25
I have tried all of the above measures and all i seem to get is the black screen. I have manged to load Ubuntu onto a HP NC4400, my desktop and even my old AJP DTR thats about 6 years old.  But for some reason it wont happen with my New Acer 5920G, model no LX.AGS0X.015. I am running Vista Ultimate, partitioned the Hard drives as 70 GB Vista 70 GB for Ubuntu and the remaining for Swap files. This last attemptwas with the alternate CD with i386 support. Can i get any help...PLEASE....

HELP!

My latest screen says

[  190.780000] Kernel panic - not syncing: Attempted to kill init!
[  190.780000]

---

### Post by shador on 2007-08-27
Anyone tried how well Gutsy Gibbon installs on this computer. Since you can get practically prefect operation on Feisty I'd think Gibbon would only make things better but you never know :) 

So anyone tried it?

---

### Post by f76 on 2007-08-27
anyone got the wireless running? I tried the [https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty](https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty)

howto without any avail. i get "netw4x32 : invalid driver!" after installing the ndiswrapper 1.43
I am running feisty64

Its my first laptop so it has to run ubuntu :)

---

### Post by shador on 2007-08-27
> **f76 said:**
> anyone got the wireless running? I tried the [https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty](https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty)

howto without any avail. i get "netw4x32 : invalid driver!" after installing the ndiswrapper 1.43
I am running feisty64

Its my first laptop so it has to run ubuntu :)

Don't have the computer myself (yet) but looking at other posts there doesn't seem to be any big problems with the wireless. Maybe it's because the use of 64 bit edition? 

If you don't have a specifik reason for using the 64 bit edition I think you should stay on the normal 32 bit. A lot better especially if you're somewhat new to the whole thing. 

Other than wireless. How's your experience with the computer? Did the installation trouble you much? 
I would also like to know if the machine is heavy or if it fits for carrying to school and stuff.

---

### Post by DSF_70 on 2007-08-27
WELL WELL WELL!!!! I finally got here... Dual Booting Vista and Ubuntu.... Ctrl+Alt+F1 at blank screen, added a little sauce..[COLOR="Sienna"].sudo dpkg-reconfigure xserver-xorg[/COLOR]... Mixed it with what i knew about Gparted...ALWAYS FORCES vesa, then followed the listings. It worked a treat....
Thank you for all those that have given input to this forum....
Now to battle on.
Wireless, etc.... Give me Hope.....

---

### Post by f76 on 2007-08-27
> **shador said:**
> Don't have the computer myself (yet) but looking at other posts there doesn't seem to be any big problems with the wireless. Maybe it's because the use of 64 bit edition? 

If you don't have a specifik reason for using the 64 bit edition I think you should stay on the normal 32 bit. A lot better especially if you're somewhat new to the whole thing. 

Other than wireless. How's your experience with the computer? Did the installation trouble you much? 
I would also like to know if the machine is heavy or if it fits for carrying to school and stuff.

Well there is some work, and everything works fine, sound is great now :) only wireless not working. But its not very portable. I think its crazy-heavy! Im not going to move it :)

---

### Post by StratosL on 2007-08-27
@f76
for the linux wireless driver, see  [*this thread*]("http://ubuntuforums.org/showthread.php?t=493095&highlight=4965")

Unfortunately, for me this did not work very well, the card seemed to work but practically it was unusable, because the data only came in bursts. I also had to use the 2.6.22 kernel from gutsy to make the drivers work.

However, the ndiswrapper solution (linked in messages earlier) worked just fine. Make sure you download, compile and install the latest version of ndiswrapper (I think 1.47), including all the pre-install clean-upl steps described in the site.

This way you also get the wireless "on" light working!

I have connected to unprotected and wpa networks with no problem.

BTW, Anybody got the webcam working with kopete? It works with V4L2.

PS
Tried to install gusty, but the latest nvidia drivers are still not included in the nvidia-glx or nvidia-glx-new

---

### Post by shador on 2007-08-27
> **f76 said:**
> Well there is some work, and everything works fine, sound is great now :) only wireless not working. But its not very portable. I think its crazy-heavy! Im not going to move it :)

Good to know. But honestly, is 3 kg really that much? I could buy a computer with a weigh in of like 2.5 but then it will be more expensive and with less power. Is it really worth it? 

Acer 5920G seems like a great laptop wich beats everything at it's price range. And it works quite well under linux. A shame if it would fail on just the weight =)

---

### Post by Vermind on 2007-08-28
Hello,
About the wireless.
You do know that a 64-bit Ubuntu wants the 64-bit Windows driver for ndiswrapper?

And for the newest nvidia drivers:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Download the 100.14.11 under amd64 from the nvidia site
Make sure nvidia-glx and nvidia-kernel are uninstalled and that 
/etc/init.d/nvidia*
do not exist
Logoff from X and go to the virtual console (Alt-F1).
shut down gdm (or kdm) with
sudo   killall -s TERM gdm # or kdm
unload old nvidia module if You had one
sudo modprobe -r nvidia
Say chmod 750 NVIDIA*
and
sudo ./NVIDIA-* 
Instructions are straightforward, it even compiles the nvidia-kernel for Your arch and sets Your xorg.conf straight if You let it.
To make sure that this new driver is used on next boot, add
 DISABLED_MODULES="nv nvidia_new"
to /etc/default/linux-restricted-modules-common.
Then restart gdm or kdm
sudo gdm # or kdm
 it should load the new module, and You should see glxinfo talking about a new nvidia driver version:
glxinfo | grep "OpenGL version"
  OpenGL version string: 2.1.1 NVIDIA 100.14.11

These work very well on my desktop (edgy) and they can do beryl/compiz with either AIGLX or Nvidia's own method, which I prefer.
P.S. Trying to start beryl without --force-nvidia crashed the computer with these drivers when I tried it the first time, has worked well since I added that.

---

### Post by frenchcr on 2007-08-31
I have Gutsy and 2.6.22-10-generic kernel loaded now....did all the gutsy upgrades and although its not perfect, it works. Reinstalled envy and envys' nvidia driver and it works nicely with compiz fuzion which is very slick graphically in terms of pixel counts, slicker than beryl ever was.

**UPDATED**

I have everything working in gutsy, bar my usb which doesnt show its icon on the screen when it mounts, but does mount all the same.

**UPDATED**

Solved my usb problem

Solution

cd /usr/share/share/hal/fdi/policy/

rm gparted-disable-automount.fdi

apparently its to do with recent usage and bug Gparted


**Everything Can Work**

---

### Post by frenchcr on 2007-09-09
updated kernel works.

no need for envy.

restricted drivers > nvidia driver does the trick. yay.

see sig new kernel

---

### Post by danieldumitru on 2007-09-16
Hy StratosL 
Ie tried up to now only sdiswrapper on ubuntu feisty with the standard kernel and ](*,)](*,):confused:

I would like also to update the kernel for 7.04 to ubuntu 7.10 kernel for my wireless card.
Can u tel me how U did it or give me the thread.


Sory for my english.

---

### Post by frenchcr on 2007-09-17
**danieldumitru**

for the kernel...

[http://ubuntuforums.org/showthread.php?t=511974&highlight=update+kernel](http://ubuntuforums.org/showthread.php?t=511974&highlight=update+kernel)

you can use wifi-radar to spot networks.

Please make a step by step guide of what you do to get wireless working, then post it on this link. I forgot to do it as i went along and forgot the steps. Cheers.

---

### Post by danieldumitru on 2007-09-18
Starting with the beginning pls be informed that I still test my wifi and mistakes here might be possible so if U see some pls post them.
Also pls note that I´m a beginner with linux but I´ll do my best.

Laptop: Acer Aspire 5920G.
Proc.: T5250, Nvidia 8600M GT (256MB owned), 160 GB HDD, Wlan: Intel 
wifi 802.11b/b/g/Draft N.

Previosly was installed kernel 2.6.22-11-generic
 as in  here: [http://ubuntuforums.org/showthread.php?t=511974&highlight=update+kernel](http://ubuntuforums.org/showthread.php?t=511974&highlight=update+kernel)
After installing the new kernel install ndiswrapper from source as in
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Go to 2nd part of the tutorial and proceed from here
(No Luck Yet? Compile ndiswrapper from Source)

[B]sudo modprobe -r ndiswrapper
sudo ndiswrapper -r bcmwl5
sudo apt-get remove ndiswrapper-utils 
sudo rm -r /etc/ndiswrapper/ 
sudo rm -r /etc/modprobe.d/ndiswrapper[/B]

This part  I did not use and I suppose that is applicable if U had a previous install of Ndiswrapper.
If not then proceed here:

[B]sudo apt-get update
sudo apt-get install build-essential[/B] *(required because is not specified in the installation of the kernel made earlier===if U removed the Gutsy repository from list then U need to reenter it again as in the tutorial for installing kernel)===*

*sudo apt-get install linux-headers-`uname -r`(no need because was installed already)*

This U follow if U like, personaly I didn´t.

[B]sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build
mkdir -p ~/bcm43xx/ndiswrapper; cd ~/bcm43xx/ndiswrapper[/B]

Download Ndiswrapper:

**sudo wgethttp://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.47.tar.gz-Ondiswrapper.tar.gz**
Or download latest stable version(1.47) and proceed further.
[http://sourceforge.net/project/showfiles.php?group_id=93482]("http://sourceforge.net/project/showfiles.php?group_id=93482")

Then in Terminal type as follows

[B]tar xvzf ndiswrapper*.tar.gz
cd ndiswrapper*
make distclean
make
sudo make install[/B]

Go to file containing NETw4x32.INF [download latest driver from Intel site for your card valid for windows xp(V11.1.1.0_XP_DRIVERS was for me)]

[B]sudo ndiswrapper -i NETw4x32.INF 
ndiswrapper -l
sudo modprobe ndiswrapper
sudo ndiswrapper -m [/B]

Now, REBOOT. 

Pls have a look in parallel, with what is written below, to this link for troubleshooting.
 [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,troubleshooting/]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,troubleshooting/")

Now in Terminal insert **sudo ndiswrapper**

nemesis@ubuntu:~$ **sudo ndiswrapper -l**
Password:
netw4x32 : driver installed
        device (8086:4229) present (alternate driver: iwl4965)

nemesis@ubuntu:~$ **sudo rmmod iwl4965**

nemesis@ubuntu:~$ **sudo ndiswrapper -l**

[I]netw4x32 : driver installed
        device (8086:4229) present (alternate driver: iwl4965)[/I](iwl4965 was remover but I do not know why he is showing like this)

If U will remove it again u will get this messages:

nemesis@ubuntu:~$ **sudo rmmod iwl4965**
ERROR: Module iwl4965 does not exist in /proc/modules

nemesis@ubuntu:~$ **sudo ndiswrapper -r iwl4965**
couldn't delete /etc/ndiswrapper/iwl4965: No such file or directory

Precautionary install again  NETw4x32.INF

nemesis@ubuntu:~/V11.1.1.0_XP_DRIVERS$** sudo ndiswrapper -i NETw4x32.INF**
*driver netw4x32 is already installed*

Restart ndiswrapper as follows:
nemesis@ubuntu:~/V11.1.1.0_XP_DRIVERS$ **sudo rmmod ndiswrapper**
nemesis@ubuntu:~/V11.1.1.0_XP_DRIVERS$ **sudo modprobe ndiswrapper**

Give this command dmesg|grep ndiswrapper 
nemesis@ubuntu:~/V11.1.1.0_XP_DRIVERS$ **dmesg|grep ndiswrapper**(below see what showed to me)
[  894.256000] ndiswrapper version 1.45 loaded (smp=yes)
[  894.376000] ndiswrapper: driver netw4x32 (Intel,04/30/2007,11.1.1.11) loaded
[  894.376000] ndiswrapper (NdisWriteErrorLogEntry:192): log: 40001B7C, count: 2, return_address: f8e2a5d2
[  894.376000] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0x56524457
[  894.376000] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0xdd
[  894.416000] ndiswrapper: using IRQ 18
[  894.704000] usbcore: registered new interface driver ndiswrapper
[  894.752000] ndiswrapper (set_scan:1157): scanning failed (C0030001)
[ 1222.032000] ndiswrapper: device wlan0 removed
[ 1222.032000] usbcore: deregistering interface driver ndiswrapper
[ 1222.052000] ndiswrapper version 1.45 loaded (smp=yes)
[ 1222.064000] ndiswrapper: driver netw4x32 (Intel,04/30/2007,11.1.1.11) loaded
[ 1222.068000] ndiswrapper (NdisWriteErrorLogEntry:192): log: 40001B7C, count: 2, return_address: f8e2a5d2
[ 1222.068000] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0x56524457
[ 1222.068000] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0xdd
[ 1222.104000] ndiswrapper: using IRQ 18
[ 1222.372000] usbcore: registered new interface driver ndiswrapper
[ 1225.500000] ndiswrapper (set_scan:1157): scanning failed (C0030001)

**[ 1225.500000] ndiswrapper (set_scan:1157): scanning failed (C0030001)** do not ask me what it mens because I do not have a clue.


nemesis@ubuntu:~/V11.1.1.0_XP_DRIVERS$ **sudo iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

Warning: Driver for device wlan0 has been compiled with version 22
of Wireless Extension, while this program supports up to version 20.
Some things may be broken...

wlan0     IEEE 802.11g  ESSID:off/any (this meens that the wifi si not connected)  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=150 Mb/s   
          Fragment thr=1500000 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
Go to network manger in the bar and conect on the wireless network present there.

Give one mor time command sudo iwfcongig and U should see this:

nemesis@ubuntu:~/V11.1.1.0_XP_DRIVERS$ **sudo iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

Warning: Driver for device wlan0 has been compiled with version 22
of Wireless Extension, while this program supports up to version 20.
Some things may be broken...

wlan0     IEEE 802.11g  ESSID:"default"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0E:2E:AF:02:49   
          Bit Rate=54 Mb/s   
          Fragment thr=540000 B   
          Encryption key:off
          Power Management:off
          Link Quality:84/100  Signal level:-42 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

If U get ESSID:¨default¨ then is working (default is my nework name, yours might be another one, depends on what U selected in Network Manager)

With the hope that I didn´t forgot something I wish U god luck.
Now I have a problem every time when I browse on internet or download something the indicator blink´s.
Somebody can tell me if tis is ok or I might have an error?

---

### Post by danieldumitru on 2007-09-18
It seems that after restart the wireless lan will not start(at least like this was for me) so U need to do this:

```
sudo rmmod iwl4965
```
```
sudo rmmod ndiswrapper
```
```
sudo modprobe ndiswrapper
```

otherwise ndiswrapper will load  iwl4965 and i do not know how good will be.
If somebody else has a beter ideea pls post it.

Relax, is no need to wary. Windows will crush.:)

---

### Post by errenay on 2007-09-20
Does anyone manage to use multimedia keys (on the right side, under Acer Arcade button). It looks like Kubuntu 7.04 recognize two touchpads (first - "media keys" and second - "real touchpad"). More  [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=517156").

---

### Post by StratosL on 2007-10-04
FYI, 

Gutsy beta works out of the box, all wireless problems are gone. Good question about the "touch-keys" on the right.

PS
Using 64bit gutsy

---

### Post by winged_tiger on 2007-10-04
Does anybody know whats up with [http://allostalk.com]("http://allostalk.com")?
I applied for membership 3 days ago and the activationmail didn't come
The main page says no discussions found.
anybody said, there would be the solution with the problem aspire5920G - Ubuntu, but now I can't read it!

---

### Post by sharperguy on 2007-11-27
> **StratosL said:**
> FYI, 

Gutsy beta works out of the box, all wireless problems are gone. Good question about the "touch-keys" on the right.

PS
Using 64bit gutsy

Are you talking about the Acer Aspire 5920G?

I'm looking into buying one but am hoping if I do, not to have loads of issues (especially wireless).

Gutsy has been released now so if you are talking about the Acer Aspire 5920G then that would be great to know.

---

### Post by Bartender on 2007-12-03
sharper -
Everyone disappeared!  Hopefully they're using their 5920's without any problems...

I'd also like to hear about this lappy with Ubuntu 7.10.  It seems like an awfully nice machine for the price.  Circuit City selling it for $650 after the stupid rebate

---

