---
title: "I broke my sound.  No sound on my computer anymore.  Need help pronto."
date: 2007-12-27
forum: Hardware &amp; Laptops
---

### Post by Psyco_Chipmunk on 2007-12-27
I was trying to fix a problem on my laptop, when ever i pluged in headphones to my laptop,  the laptop speakers wouldent go of.  So i tryed to fix it by following this little guide.

> Hi,

Ubuntu Rocks!! Fiesty is good. I got my sound working. So what I did was go to the wiki and read howto troubleshoot Sound.
Well summarizing it all this is what I did.
First of all I will like to tell you that there is a excellent guide here: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting). Please read it before doing what is given below. (thanks to ikonia at irc)

Step 1)
sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant

Step 2)
wget [ftp://ftp.alsa-project.org/pub/drive....14rc1.tar.bz2](ftp://ftp.alsa-project.org/pub/drive....14rc1.tar.bz2)
tar jxvf alsa-driver-1.0.14rc1.tar.bz2
cd alsa-driver-1.0.14rc1/
sudo ./configure --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=hda-intel
sudo make
sudo make install

Step 3)
vi /etc/modprobe.d/options
Here I wrote:
options snd-hda-intel model=laptop-eapd
save and quit.

Step 4) Reboot

Step 5) Enable Internal Modem from within the BIOS

Step 6) Booted Ubuntu Fiesty Linux.

Step 7). LOL !!

Sound's working !! Cheers.

Regards
Deepsa
__________________

I did all of the steps, but when it came to step 3, i think i messed up.  Here's what I did.  I ran vi /etc/modprobe.d/options in the terminal, no gedit bofor it or anything, just plane vi /etc/modprobe.d/options.  So this thing came up in the terminal, 
_________________________________________________________________
[COLOR="Yellow"]
 options snd-hda-intel model=laptop-eapd[/COLOR]#Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

options snd-hda-intel model=laptop-eapd # Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2
model=default
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
"/etc/modprobe.d/options" [readonly] 7 lines, 187 characters

Being stupid like i am, i do the next part of step 3 right away, i past options snd-hda-intel model=laptop-eapd right into the terminal where its highlighted and pressed enter.

Something came up 

W10: Warning: Changing a readonly file 
E325: ATTENTION
Found a swap file by the name "/var/tmp/options.swp"
          owned by: luke   dated: Thu Dec 27 01:14:45 2007
         file name: /etc/modprobe.d/options
          modified: YES
         user name: luke   host name: luke-laptop
        process ID: 23642
While opening file "/etc/modprobe.d/options"
             dated: Thu Dec 27 02:02:05 2007
      NEWER than swap file!

(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two
    different instances of the same file when making changes.
    Quit, or continue with caution.

(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r /etc/modprobe.d/options"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/var/tmp/options.swp"
    to avoid this message.

Interrupt: Press ENTER or type command to continue

  

so i think i just exit out, i might have pressed enter, then i did the rest of the steps, rebooted, and Bam!  No sound! :(.  What  do I do?  How do I fix this?  I really need some good help fast.  Thanks!!!

---

### Post by Psyco_Chipmunk on 2007-12-27
luke@luke-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
05:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
05:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
luke@luke-laptop:~$

---

### Post by Psyco_Chipmunk on 2007-12-27
bump

---

### Post by gobbles414 on 2008-01-01
Psyco_Chipmunk,

You and I were on the same IRC channel the other day, getting some help regarding our sound problems. I have discovered a MUCH easier way to fix the problem than we tried then -- although that plan would have worked with a bit of effort. Anyway, here's the procedure for installing version 4.07a of the driver in Ubuntu 7.10. NOTE: Be careful not to paste commas or periods into the terminal.

1. Go *System => Administration => Software Sources => Updates and put a checkmark next to Pre-released Updates*. Check for and install any updates.

2. Then restart your computer, just to be safe.

3. Download the [Realtek HD audio driver for Linux]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#High%20Definition%20Audio%20Codecs") to your desktop (click on link). Interestingly, this driver is just an automatic version of what you and I tried to install on IRC.

4. Right-Click on the downloaded archive and choose *Extract Here*.

5. Open a terminal window and type *sudo apt-get install linux-backports-modules-generic build-essential gettext libcunit1-ncurses libcunit1-ncurses-dev libncurses5 libncurses5-dev*, and press enter.

6. Just to be safe, restart your computer again.

7. Open the terminal again and type *cd /home/YOURUSERNAME/Desktop/realtek-linux-audiopack-4.07a*, then press enter. Obviously, substitute your own username where I have written YOURUSERNAME. This will move you inside the driver folder.

8. Type *sudo /etc/init.d/alsa-utils stop*, then press enter. Then type *sudo /etc/init.d/alsasound stop*, and press enter. The first one should definitely work. The second may not work now, but it will eventually. NOTE: If asked to reload your speaker icon during either of these steps, say no.

9. Type *sudo ./install*, and press enter. Watch your computer as it installs the driver.

10. If there are not any errors in the installation process, you should be greeted by a screen asking you to select you audio device. Choose the one the talks about *Intel HD Audio (ICH7)*, or similar.

11. Restart your computer.

12. Open the terminal again and type *cat /proc/asound/card0/codec#* | grep Codec*, and press enter. This should tell you what kind of sound you have. In my case, the result was *Realtek ALC660-VD*. WARNING: Your modem may also show up in these results. So be sure that you are about to choose the sound and not the modem by doing some research online.

13. Look at the list below to determine the abbreviation for your sound card. For example, my Realtek ALC660-VD is represented by *3stack-660-digout*.

14. Type *sudo gedit /etc/modprobe.d/alsa-base*, and press enter. A file with some text should open.

15. Go to the last line of text and type options snd-hda-intel model=YOURMODEL. So for example, I have typed options *snd-hda-intel model=3stack-660-digout*. Be sure to save your changes by going *File => Save*!

16. Restart your computer so that your sound can reload itself.

17. I had to do steps 7-16 twice in order to get a successful installation of the audio driver.

18. To get your speaker icon back on your panel (also called a taskbar), *Right-Click on the top panel and choose Add to Panel => System & Hardware => Volume Control => left-click on the Add button*. Right-Clicking on a pane icon will allow you to move it around, or lock it into position.

19. THIS OPTION IS ONLY IF YOUR COMPUTER SUPPORTS SPDIF. Now, right-click on the speaker icon and choose *Open Volume Control*. The title of the Volume Control window should either have ALSA or OSS in it. Either way, go *Edit => Preferences*. If you are in ALSA, look for an option like *IEC958*. Choosing that will place on option in the Switches tab; placing a checkmark in the box there will activate SPDIF sound. It's fine to leave SPDIF on at all times if you want to do so. If you ever need to know about OSS, you can get there by going *File => Change Device* in Volume Control. On my computer, OSS calls SPDIF *Digital-1*. If selected, it will appear in the *Playback tab* of OSS.

20. Each program will behave differently with SPDIF audio. Movie Player (Totem) behaves very well. In Movie Player, you can activate full digital surround sound (Dolby Digital, DTS, etc) by going *Edit => Preferences => Audio and choosing AC3 Passthrough* from the drop-down menu. On the other hand, some audio-related options within the VLC media player can wreck the sound on your entire system! The good news is, you can always fix any damaged caused by VLC by repeating the above steps. Just be careful...

The following are webpages where I found all of this information:
<[https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100_FPG]("https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100_FPG")>
<[http://ubuntuforums.org/showthread.php?t=616845]("http://ubuntuforums.org/showthread.php?t=616845")>
<[http://www.matusiak.eu/numerodix/blog/index.php/2007/10/31/gutsy-on-the-toshiba-u300/]("http://www.matusiak.eu/numerodix/blog/index.php/2007/10/31/gutsy-on-the-toshiba-u300/")>

Here is a list of audio devices:
Model name Description
---------- -----------
ALC880
3stack 3-jack in back and a headphone out
3stack-digout 3-jack in back, a HP out and a SPDIF out
5stack 5-jack in back, 2-jack in front
5stack-digout 5-jack in back, 2-jack in front, a SPDIF out
6stack 6-jack in back, 2-jack in front
6stack-digout 6-jack with a SPDIF out
w810 3-jack
z71v 3-jack (HP shared SPDIF)
asus 3-jack (ASUS Mobo)
asus-w1v ASUS W1V
asus-dig ASUS with SPDIF out
asus-dig2 ASUS with SPDIF out (using GPIO2)
uniwill 3-jack
fujitsu Fujitsu Laptops (Pi1536)
F1734 2-jack
lg LG laptop (m1 express dual)
lg-lw LG LW20/LW25 laptop
tcl TCL S700
clevo Clevo laptops (m520G, m665n)
test for testing/debugging purpose, almost all controls can be
adjusted. Appearing only when compiled with
$CONFIG_SND_DEBUG=y
auto auto-config reading BIOS (default)

ALC260
hp HP machines
hp-3013 HP machines (3013-variant)
fujitsu Fujitsu S7020
acer Acer TravelMate
will Will laptops (PB V7900)
replacer Replacer 672V
basic fixed pin assignment (old default model)
auto auto-config reading BIOS (default)

ALC262
fujitsu Fujitsu Laptop
hp-bpc HP xw4400/6400/8400/9400 laptops
hp-bpc-d7000 HP BPC D7000
benq Benq ED8
benq-t31 Benq T31
hippo Hippo (ATI) with jack detection, Sony UX-90s
hippo_1 Hippo (Benq) with jack detection
sony-assamd Sony ASSAMD
basic fixed pin assignment w/o SPDIF
auto auto-config reading BIOS (default)

ALC268
3stack 3-stack model
toshiba Toshiba A205
acer Acer laptops
auto auto-config reading BIOS (default)

ALC662
3stack-dig 3-stack (2-channel) with SPDIF
3stack-6ch 3-stack (6-channel)
3stack-6ch-dig 3-stack (6-channel) with SPDIF
6stack-dig 6-stack with SPDIF
lenovo-101e Lenovo laptop
auto auto-config reading BIOS (default)

ALC882/885
3stack-dig 3-jack with SPDIF I/O
6stack-dig 6-jack digital with SPDIF I/O
arima Arima W820Di1
targa Targa T8, MSI-1049 T8
asus-a7j ASUS A7J
asus-a7m ASUS A7M
macpro MacPro support
mbp3 Macbook Pro rev3
imac24 iMac 24'' with jack detection
w2jc ASUS W2JC
auto auto-config reading BIOS (default)

ALC883/888
3stack-dig 3-jack with SPDIF I/O
6stack-dig 6-jack digital with SPDIF I/O
3stack-6ch 3-jack 6-channel
3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
6stack-dig-demo 6-jack digital for Intel demo board
acer Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
acer-aspire Acer Aspire 9810
medion Medion Laptops
medion-md2 Medion MD2
targa-dig Targa/MSI
targa-2ch-dig Targs/MSI with 2-channel
laptop-eapd 3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
lenovo-101e Lenovo 101E
lenovo-nb0763 Lenovo NB0763
lenovo-ms7195-dig Lenovo MS7195
haier-w66 Haier W66
6stack-hp HP machines with 6stack (Nettle boards)
3stack-hp HP machines with 3stack (Lucknow, Samba boards)
auto auto-config reading BIOS (default)

ALC861/660
3stack 3-jack
3stack-dig 3-jack with SPDIF I/O
6stack-dig 6-jack with SPDIF I/O
3stack-660 3-jack (for ALC660)
uniwill-m31 Uniwill M31 laptop
toshiba Toshiba laptop support
asus Asus laptop support
asus-laptop ASUS F2/F3 laptops
auto auto-config reading BIOS (default)

ALC861VD/660VD
3stack 3-jack
3stack-dig 3-jack with SPDIF OUT
6stack-dig 6-jack with SPDIF OUT
3stack-660 3-jack (for ALC660VD)
3stack-660-digout 3-jack with SPDIF OUT (for ALC660VD)
lenovo Lenovo 3000 C200
dallas Dallas laptops
hp HP TX1000
auto auto-config reading BIOS (default)

CMI9880
minimal 3-jack in back
min_fp 3-jack in back, 2-jack in front
full 6-jack in back, 2-jack in front
full_dig 6-jack in back, 2-jack in front, SPDIF I/O
allout 5-jack in back, 2-jack in front, SPDIF out
auto auto-config reading BIOS (default)

AD1882
3stack 3-stack mode (default)
6stack 6-stack mode

AD1884
N/A

AD1981
basic 3-jack (default)
hp HP nx6320
thinkpad Lenovo Thinkpad T60/X60/Z60
toshiba Toshiba U205

AD1983
N/A

AD1984
basic default configuration
thinkpad Lenovo Thinkpad T61/X61

AD1986A
6stack 6-jack, separate surrounds (default)
3stack 3-stack, shared surrounds
laptop 2-channel only (FSC V2060, Samsung M50)
laptop-eapd 2-channel with EAPD (Samsung R65, ASUS A6J)
laptop-automute 2-channel with EAPD and HP-automute (Lenovo N100)
ultra 2-channel with EAPD (Samsung Ultra tablet PC)

AD1988
6stack 6-jack
6stack-dig ditto with SPDIF
3stack 3-jack
3stack-dig ditto with SPDIF
laptop 3-jack with hp-jack automute
laptop-dig ditto with SPDIF
auto auto-config reading BIOS (default)

Conexant 5045
laptop Laptop config
test for testing/debugging purpose, almost all controls
can be adjusted. Appearing only when compiled with
$CONFIG_SND_DEBUG=y

Conexant 5047
laptop Basic Laptop config
laptop-hp Laptop config for some HP models (subdevice 30A5)
laptop-eapd Laptop config with EAPD support
test for testing/debugging purpose, almost all controls
can be adjusted. Appearing only when compiled with
$CONFIG_SND_DEBUG=y

STAC9200
ref Reference board
dell-d21 Dell (unknown)
dell-d22 Dell (unknown)
dell-d23 Dell (unknown)
dell-m21 Dell Inspiron 630m, Dell Inspiron 640m
dell-m22 Dell Latitude D620, Dell Latitude D820
dell-m23 Dell XPS M1710, Dell Precision M90
dell-m24 Dell Latitude 120L
dell-m25 Dell Inspiron E1505n
dell-m26 Dell Inspiron 1501
dell-m27 Dell Inspiron E1705/9400

STAC9205/9254
ref Reference board
dell-m42 Dell (unknown)
dell-m43 Dell Precision
dell-m44 Dell Inspiron

STAC9220/9221
ref Reference board
3stack D945 3stack
5stack D945 5stack + SPDIF
intel-mac-v1 Intel Mac Type 1
intel-mac-v2 Intel Mac Type 2
intel-mac-v3 Intel Mac Type 3
intel-mac-v4 Intel Mac Type 4
intel-mac-v5 Intel Mac Type 5
macmini Intel Mac Mini (equivalent with type 3)
macbook Intel Mac Book (eq. type 5)
macbook-pro-v1 Intel Mac Book Pro 1st generation (eq. type 3)
macbook-pro Intel Mac Book Pro 2nd generation (eq. type 3)
imac-intel Intel iMac (eq. type 2)
imac-intel-20 Intel iMac (newer version) (eq. type 3)
dell-d81 Dell (unknown)
dell-d82 Dell (unknown)
dell-m81 Dell (unknown)
dell-m82 Dell XPS M1210

STAC9202/9250/9251
ref Reference board, base config
m2-2 Some Gateway MX series laptops
m6 Some Gateway NX series laptops
pa6 Gateway NX860 series

STAC9227/9228/9229/927x
ref Reference board
3stack D965 3stack
5stack D965 5stack + SPDIF
dell-3stack Dell Dimension E520

STAC9872
vaio Setup for VAIO FE550G/SZ110
vaio-ar Setup for VAIO AR

---

### Post by gobbles414 on 2008-01-07
Psyco_Chipmunk,

Did my solution work for you at all?

---

