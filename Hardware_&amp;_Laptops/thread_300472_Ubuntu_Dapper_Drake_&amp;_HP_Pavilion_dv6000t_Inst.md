---
title: "Ubuntu Dapper Drake &amp; HP Pavilion dv6000t Installation notes:"
date: 2006-11-15
forum: Hardware &amp; Laptops
---

### Post by dogging_99 on 2006-11-15
PC includes:
-  Windows XP Professional
- Intel(R) Core(TM) 2 Duo processor T5600 (1.83 GHz)
- 15.4" WXGA BrightView Widescreen
- 256MB NVIDIA(R) GeForce(R) Go 7400 
- HP IMPRINT Finish + Microphone + Webcam 
- 1.0GB DDR2 SDRAM (2x512MB)
- Hard Drive 80 GB 5400 RPM
- LightScribe Super Multi 8X DVD+/-RW w/Double Layer
- Intel(R) PRO/Wireless 3945ABG Network w/Bluetooth
- 6 Cell Lithium Ion Battery
- HP Mobile Remote Control

For starters I have resized the ntfs partition from 65gb => 30gb:
I made sda2 primary and sda5-7 extended partitions.

sda1 + Primary 30gb ntfs (HP Factory WinXP Pro) (used 50%)
sda2 Primary -35gb (Extended Partition Table) 
-sda5 Extended 20gb ext3 (ubuntu-6.06.1-desktop-i386) (/... /boot... /home...) (used 26%)
-sda6 Extended 2gb linux-swap (used 0%)
-sda7 Extented 13gb fat32 (share ubuntu & winxp) (used 10%)
sda3 Primary 10gb fat32 (HP PC Restore) (used 90%)  	??
sda4 Primary 1gb ntfs (HP Quick Play ? / Winxp System Restore ?) (used 90%)	 ??

This is the order of my installation, but I would do it differently nowing what I know now!

Grub installed to sda1 (no choice?) I intended to use (bootpart.exe and add a line to boot.ini) I expected the install program to ask me like the edgy installer (edgy was twooo buggy) o-well thats ok the remote boots up grub and I can select Ubuntu (default), WinXP, Quick Play or HP PC Recover by the handy remote.  Me and Wifey like using the remote for watching dvd movies in my camper.

**GRUB MENU.LST**
===================================================================================================
# menu.lst - See: grub(8'), info grub, update-grub(8')
#            grub-install(8'), grub-floppy(8'),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

-------SNIP-------------

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-27-686
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-27-686 root=/dev/sda5 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-686 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-27-686 root=/dev/sda5 ro single
initrd		/boot/initrd.img-2.6.15-27-686
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda5 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda5 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda5 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda5 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows NT/2000/XP PC RECOVER
root		(hd0,2)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Microsoft Windows XP Embedded QUICKPLAY
root		(hd0,3)
savedefault
makeactive
chainloader	+1
===================================================================================================
**END GRUB**

After a lot of effort, googling and reading and apt-get install-xxx I came across **Automatix2**!
Is that cool or what? I had already installed about half of what I needed but Automatix2 made the rest of my installs painless. **(Great Job!! Automatix)**

**lm-sensores** (did not work for me)
-how do I uninstall?

**gdesklets** (some app's not function)
-menu rocks!

**Gkrell** (worked out of the box)

**sudo apt-get install nvidia-glx**  (worked but lost hibernation)
-I tried the driver hack but did not help
-also removed splash
-Googleearth rocks!


**sudo apt-get install linux-686-smp** (cool now both proccessors working!)
-I also notice less heat running app's 
-I sensor CPU and GPU heat aswell now in gkrell
-gpu 45c-50c and cpu 39c-45c

Installed **GnuCash**
exported money .qif
imported .qif to GnuCash
-Looks great (I need to use GC more then I can drop MS Money)
-when I was in buisiness I used Peach Tree (I Liked PT but too cumbersum for Home Finances)

**Vmware**- OK
**Open Office** &#8211; OK
**Streamtunner** &#8211; OK rocks!
**Streamripper** &#8211; OK  rocks!

What Dosen't Work?
1)Headphone Jack (no sound) UPDATE WORKING!
2)Hibernate locks-up (must hold power down to shutdown) removed from menu!
3)Suspend (lost eth1 wifi and other problems) removed from menu!
4)Web-Cam (not tried)
5)Skype (not tried)
6)Bluetooth (not tried)
7)QuickPlay (need just reboot select in grub or use totem-xine)
8')Burn CD DVD (not tried)

What Works!
1)SD-Card (cool! back-up my Axim x50v)
2)HP usb Laser mini mouse, Targus 4 port usb
3)Touch pad (sudo apt-get install gsnyaptics)
4)Screen darken / lighten
5)Sound +, -, and mute &#8220;touch lead-lights&#8221;
6)ipw-3945 wifi w/wep and eth0 wire
7)processor 0, possessor 1, speed stepping
8')Battery charge level (must howto set alarms)
9)**Puppy-Linux** 2.01 ipw-3945.pup rocks! (boot from CD save /sda5 HardDrive-Very Very Fast!)
10)**Qemu-Puppy** USB 2.01-2 fast enuff! (pup_save.3fs interchange w/hd version VERY NICE!!)
11)Headphone Jack (WORKING)!

Correct order of installation:
1)Partition
2)Boot  ubuntu-6.06.1-desktop-i386 &#8220;Install&#8221;
3)apt-get install linux-686-smp
4)apt-get install nvidia-glx
5)Install Automatix2
6)Install GkreLL ...
7)Install gdesklets ...

Conclusion:
Boots faster (40sec) than hibernated windows boots (45sec)
Runs faster than windows
Better looking desktop eye candy and wow! Factor
Great Support (This Site!)

Thanks::mrgreen:  MJM
P.S. dv6000t posts Welcome!

---

### Post by dogging_99 on 2006-11-19
Update Note:

I uninstalled lm-sensors (sudo apt-get remove lm-sensors)
I installed hddtemp (sudo apt-get install hddtemp)

I added my 80gb FUJITSU MHV2080BH to the data base
$ sudo gedit /etc/hddtemp.db
"FUJITSU MHV2080BH"             194  C  "Fujitsu MHV2080BH"


I edited two lines in the following (auto start deamon)
$ sudo gedit /etc/default/hddtemp

RUN_DAEMON="true"
SYSLOG="60"

gdesklets now reads hard drive temp every 60 seconds
I still have cpu and gpu temp readings in gkrellm

Any other hardware fixes for the dv6000t welcome!

---

### Post by sick_nyquil on 2006-11-22
I was able to get my touchpad to behave better using ksynaptics, and adding this line to my xorg.conf touchpad section.
      Option         "SHMConfig" "on"
Ther are other touchpad tools in the repository including gsnyaptics.

The headphone jack is covered on this page [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) ,but it doesn't automatically mute the speakers. The volume buttons now control the headphones, but you can change that I use kmix to change mster channel between speakers and headphones.

---

### Post by mikewhatever on 2006-12-09
Dogging_99, I hope you"ll see this after two weeks since you last post. Have you had any problems with resizing ntfs partition? For some unknown reason I can not get passed that stage. 

Thanks in advance

---

### Post by dogging_99 on 2006-12-13
First I would Defragment the Hard Drive, the programs I used are QtParted, ntfsresize.   I made a boot cd from this file  systemrescuecd-x86-0.2.19.iso.  Burn an image CD from the iso be sure to check the iso w/ md5sum.exe
get it here: [http://sourceforge.net/project/showfiles.php?group_id=85811](http://sourceforge.net/project/showfiles.php?group_id=85811)

Resizing an NTFS partition with SystemRescueCD 
[http://www.lesbell.com.au/Home.nsf/b8ec57204f60dfcb4a2568c60014ed0f/3287e9f0258f9c33ca256dfc000277a9?OpenDocument](http://www.lesbell.com.au/Home.nsf/b8ec57204f60dfcb4a2568c60014ed0f/3287e9f0258f9c33ca256dfc000277a9?OpenDocument)

:mrgreen:  Hope this helps: MJM

---

### Post by dogging_99 on 2006-12-14
How to SSH-Tunnel VNC to Ubuntu

$ sudo apt-get install ssh
$ sudo apt-get install firestarter (configured firestarter option allow from work IP. You can get your ip here=> Ipchicken.com).

I have three computers and this notebook in my home network and a Netgear Model DG824M ADSL Wireless Gateway & Firewall. I have configured port forwarding 5900-5903 to each computer.
I set to only allow access from my work ip (look here: Ipchicken.com).
I can UltraVNC to each computer from work using WinXP to WinXP W/ UltraVNC. 
UltraVNC => 0.0.0.1::590# (were # = 0,1,2,3)
On the Ultra vncserver in XP I config listing port to 590# (were # = 0,1,2,3)

 In Ubuntu I can only VNC to port 5900 as that is the listening port for vncserver on ubuntu.
Workaround I configured/added the Netgear DG824M SSH PORTS (TCP/UDP) 22,21,23 etc.. to forward to the computer IP's and Allow only my work IP.
You will need to config Ubuntu SSH listening Port
$sudo gedit /etc/ssh/sshd_config (change port 22 to port ## you forwarded to this ip, reboot!)

#Using PuTTy WinXP to Ubuntu

Start putty and enter the address you would like to connect to, 
PuTTy=> 0.0.0.1 (netgear gateway modem ip)
Port=> 22 (the port you forwarded on your modem 21,22,23 etc..)

-------------------SNIP --------------------------------------------------------------
select SSH as the protocol.

On the left hand side you will see various configuration options, click the category named
Tunnels and add the following information under add new forwarded port:
Source Port 5900
Destination Port 127.0.0.1:5900
* Option* Go to section labeled X11  => X display location added=>localhost:0 (I added this from another post not sure why ?)
*Optional* Go to the section labeled SSH and check enable compression, 
with some VNC clients this can cause slower response but 
with the generic realvnc client it works fine.

Save the session
------------------------------------------------------------------------------------------
Download vncviewer from [http://www.realvnc.com](http://www.realvnc.com)
(Or any of the various VNC clients out there like tightvnc or ultravnc)

Open the vncviewer and connect to 127.0.0.1

------------------------------------------------------------------------------------------
Notes:
For added security use your hosts.allow to restrict connections from only localhost
 so that you must use SSH to connect.

If using a router, redirect TCP Port 22 (SSH) from the internet to your PC so
 you can connect remotely but you may want to use your hosts.allow or 
a filter on your router to only allow those connections from a trusted source.

If you are going through a firewall that blocks SSH you can redirect 80 or 443 with iptables.

If you have problems when using ULTRAVNC or TightVNC try using different encoding options,

---------------------------------------END SNIP------------------------------------------------------------------
#Howto SSH tunnel VNC
#Using Command Line Linux to Linux
#In Terminal-1
$ssh -L 5901:localhost:5900 user@0.0.0.1
# Note: if you change port other than 22 then add the -p ## option ($ssh -p 23 user@0.0.0.1)
#In Terminal-2
$vncviewer localhost:1

 :mrgreen:  Wala! Now I can support Mom, Wifey and the Kids from work thru SSH Tunnel!

---

### Post by dogging_99 on 2006-12-14
sick_nyquill, :mrgreen: Thanks
$ sudo apt-get install gsnyaptics 
I was able to get my touchpad scrolling to behave better also using gsynaptics all I had to do was increase sensitivity on the General tab to about 45% (Warning! Do Not increase too much at first, I tried 100% OOPs!)

---

### Post by mikewhatever on 2006-12-16
Thanks, I'll try that RescueCD.

Update: Ubuntu 6.10 successfully installed. Thanks. Need advice on wireless, pls.

---

### Post by dogging_99 on 2007-01-10
:mrgreen: Headphones now working!
I installed the new alsa version: 1.0.14 release candidate 1 
[http://www.alsa-project.org/alsa/ftp....14rc1.tar.bz2](http://www.alsa-project.org/alsa/ftp....14rc1.tar.bz2)
save to MyFolder
$cd MyFolder
$tar jxvf alsa-driver-1.0.14rc1.tar.bz2
$cd alsa-driver-1.0.14rc1

$sudo apt-get install build-essential linux-headers-$(uname -r)
$sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with -cards=hda-intel &#8211;with-oss=yes
$sudo make
$sudo make install

$sudo gedit /etc/modprobe.d/alsa-base
adding the line options snd-hda-intel model=hp

$sudo gedit /etc/modules
adding the line snd-hda-intel

Found solution Here:

[http://www.ubuntuforums.org/showthread.php?t=205449&highlight=hp+pavilion](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=hp+pavilion)

Note: Mute button doesn't work for external speakers now and is lit orange all the time, does work on headphones but led light stays on orange!

Any other hardware fixes for the dv6000t welcome![/QUOTE]

---

### Post by teaker1s on 2007-03-08
[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29]("https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29")

---

### Post by oobuntoo on 2007-03-20
> **dogging_99 said:**
> :mrgreen: Headphones now working!
I installed the new alsa version: 1.0.14 release candidate 1 
[http://www.alsa-project.org/alsa/ftp....14rc1.tar.bz2](http://www.alsa-project.org/alsa/ftp....14rc1.tar.bz2)
save to MyFolder
$cd MyFolder
$tar jxvf alsa-driver-1.0.14rc1.tar.bz2
$cd alsa-driver-1.0.14rc1

$sudo apt-get install build-essential linux-headers-$(uname -r)
$sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with -cards=hda-intel –with-oss=yes
$sudo make
$sudo make install

$sudo gedit /etc/modprobe.d/alsa-base
adding the line options snd-hda-intel model=hp

$sudo gedit /etc/modules
adding the line snd-hda-intel

Found solution Here:

[http://www.ubuntuforums.org/showthread.php?t=205449&highlight=hp+pavilion](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=hp+pavilion)

Note: Mute button doesn't work for external speakers now and is lit orange all the time, does work on headphones but led light stays on orange!

Any other hardware fixes for the dv6000t welcome![/QUOTE]



Mute now works with both headphone and external speakers  under Feisty Herd 5.  The button also only turns  orange when sound is muted.

---

### Post by dogging_99 on 2008-01-18
):P I have moved on to Gutsy. I backed up user data to my shared partition and did a clean install.

Model: HP DV6000T
Processor:  Intel(R) Core(TM) 2 Duo processor T5600 (1.83 GHz)
Wireless Card:  Intel(R) PRO/Wireless 3945ABG Network w/Bluetooth
Graphics Card:  256MB NVIDIA(R) GeForce(R) Go 7400 
Gutsy (Version): 7.10 Desktop amd64 
Boot Parameters: None

What Works!
1) Sound Card ( installed alsa driver)
2) HP usb Laser mini mouse, Targus 4 port usb, sd card reader
3) Touch pad good!
4) Screen darken / lighten
5)  Sound +, -, and mute “touch lead-lights” 
6) ipw-3945 wifi w/wep and eth0 wire
7) processor 0, possessor 1, and speed stepping
8.) Battery charge level indicator
9) Headphone Jack works properly.
10) PPTP VPN Wireless and Wired Ethernet (change ppp0 device to eth0 in '/etc/udev/rules.d/70-persistant-net.rules')
11)Firefox fast now (I had to remove ipv6)
make new file:
sudo gedit /etc/modprobe.d/bad_list
#add this text to the file:
 alias ipv6 off 
12) Key mapping seams correct
13) Suspend works and reconnects to wireless network on resume
14) Printer works could not setup samba to a windows xp shared printer I was able to setup a LPD/LPR printer on a Unix print Server setup on WinXP.
15) NVIDIA worked out of the box! Googleearth works
16) Heat Sensors in Gkrellm  sda, gpu, and thr1 temps, had to setup hddtemp for hard drive temps

Conclusion:
I like Network Manager Better seams more functional (start wireless network, start vpn and uses pass phrase and saves in password key ring)
Boots faster (40sec) than hibernated windows boots (45sec)
Runs faster than windows xp
Better looking desktop eye candy and wow! Factor
Great Support (This Site!)

---

