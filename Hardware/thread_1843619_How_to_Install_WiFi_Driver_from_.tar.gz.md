---
title: "How to Install WiFi Driver from .tar.gz"
date: 2011-09-13
forum: Hardware
---

### Post by IrrationalIntellect on 2011-09-13
Just installed Lucid Lynx on a new Compaq Presario CQ57, the wireless doesn't work. So I use Windows to find the driver and get it downloaded and saved on a memory stick.

So I've never put software on Linux from anything other than .deb packages or through package manager. Where do I go from here?

---

### Post by foresthill on 2011-09-14
While I can't give you specific instructions for your particular driver, the basic idea is that you are going to need to put the driver someplace you can easily navigate to, either your Home Folder or the Desktop. Then you'll use the terminal to navigate to the file using the "cd" command, extract the zipped file and "build" the driver using commands like "make" and "make install".

There should be some specific instructions at the site where you downloaded the driver.

If you just wanna look at the files you have, just right-click on the file and choose "extract". That will save you the first step of extracting via the terminal. 

That's the general idea anyway, sorry I could not be more specific, but this process is a little more advanced than just installing via the package manager, but is doable if you have a set of step by step instructions with commands you can copy and paste into the terminal, and you follow them to the letter.

---

### Post by IrrationalIntellect on 2011-09-14
> **foresthill said:**
>  There should be some specific instructions at the site where you downloaded the driver. 
 
I did look for them, but saw none. It was the Realtek website, the mfgr. I even started to search elsewhere, but never got it done.
 
> **foresthill said:**
>  ... extract the zipped file and "build" the driver using commands like "make" and "make install". 
 
I guess I could go look these up in the man and figure it out. I know I have seen this in the past -- just never did it.
 
Thanks.

---

### Post by Redblade20XX on 2011-09-14
Usually in the extracted files there is a README file. Can you list the files in the extracted .tar.gz?

---

### Post by IrrationalIntellect on 2011-09-17
So I found general instructions at [http://www.codecoffee.com/tipsforlinux/articles/27.html]("http://www.codecoffee.com/tipsforlinux/articles/27.html")

Unzipped file and renamed "Wifi_Driver" and cd'ed to it. Then...

```

dlb@PresarioCQ57:~/Software/WiFi_Driver$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-33-generic'
  CC [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/rtl_core.o
  CC [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/rtl_eeprom.o
  CC [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/rtl_wx.o
  CC [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/rtl_cam.o
  CC [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/rtl_pm.o
  CC [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/rtl_pci.o
  CC [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/rtl_ps.o
  CC [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/rtl_debug.o
  CC [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/rtl_ethtool.o
  CC [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/rtl_regd.o
  CC [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/rtl8192c/r8192C_dev.o
  CC [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/rtl8192c/r8192C_tx.o
  CC [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/rtl8192c/r8192C_rx.o
  CC [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/rtl8192c/r8192C_Efuse.o
  CC [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/rtl8192c/r8192C_phy.o
  CC [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/rtl8192c/r8192C_firmware.o
  CC [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/rtl8192c/r8192C_dmbt.o
  CC [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/rtl8192c/r8192C_dmout.o
  CC [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/rtl8192c/r8192C_dm.o
  CC [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/rtl8192c/r8192C_rtl6052.o
  CC [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/rtl8192c/r8192C_hwimg.o
  CC [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/rtl8192c/r8192C_led.o
  CC [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/rtl8192c/r8192C_com.o
  CC [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/../../rtllib/rtllib_rx.o
  CC [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/../../rtllib/rtllib_softmac.o
  CC [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/../../rtllib/rtllib_tx.o
  CC [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/../../rtllib/rtllib_wx.o
  CC [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/../../rtllib/rtllib_module.o
  CC [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/../../rtllib/rtllib_softmac_wx.o
  CC [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/../../rtllib/rtl819x_HTProc.o
  CC [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/../../rtllib/rtl819x_TSProc.o
  CC [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/../../rtllib/rtl819x_BAProc.o
  CC [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/../../rtllib/dot11d.o
  CC [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/../../rtllib/rtllib_crypt.o
  CC [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/../../rtllib/rtllib_crypt_tkip.o
  CC [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/../../rtllib/rtllib_crypt_ccmp.o
  CC [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/../../rtllib/rtllib_crypt_wep.o
  LD [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/r8192ce_pci.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/dlb/Software/WiFi_Driver/HAL/rtl8192/r8192ce_pci.mod.o
  LD [M]  /home/dlb/Software/WiFi_Driver/HAL/rtl8192/r8192ce_pci.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-33-generic'
 
dlb@PresarioCQ57:~/Software/WiFi_Driver$ sudo make install
[sudo] password for dlb: 
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-33-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-33-generic'
make[1]: Entering directory `/home/dlb/Software/WiFi_Driver/HAL/rtl8192'
make -C /lib/modules/2.6.32-33-generic/build M= CC=gcc modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-33-generic'
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/basic/hash
  HOSTCC  scripts/kconfig/conf.o
scripts/kconfig/conf.c: In function ‘conf_askvalue’:
scripts/kconfig/conf.c:105: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
scripts/kconfig/conf.c: In function ‘conf_choice’:
scripts/kconfig/conf.c:307: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf -s arch/x86/Kconfig
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-33-generic'
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-33-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  UPD     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[3]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[2]: *** [prepare0] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-33-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/dlb/Software/WiFi_Driver/HAL/rtl8192'
make: *** [install] Error 2
dlb@PresarioCQ57:~/Software/WiFi_Driver$ 

```

So... WiFi still does not work. I'm trying to figure out what these error messages mean:
[LIST]
[*]make[2]: *** [prepare0] Error 2
[*]make[1]: *** [modules] Error 2
[*]make: *** [install] Error 2
[/LIST]

...and to see if I can do anything about them.

---

### Post by .... on 2011-09-17
[http://www.cyberciti.biz/tips/build-linux-kernel-module-against-installed-kernel-source-tree.html#comment-156744](http://www.cyberciti.biz/tips/build-linux-kernel-module-against-installed-kernel-source-tree.html#comment-156744)

---

### Post by josephmills on 2011-09-17
Hi there could you open your terminal and type in 
```
lspci -nn
``` then ```
rfkill list all 
``` then ```
lsmod
``` then paste it all here. I think that it uses the ath5k but we will see after you post  thanks

---

### Post by .... on 2011-09-17
Also: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/567016](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/567016)

---

### Post by IrrationalIntellect on 2011-09-17
```
dlb@PresarioCQ57:~$ lspci -nn
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1510]
00:01.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:9804]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] [1002:4391]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 42)
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d] (rev 40)
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
00:14.5 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller [1002:4399]
00:15.0 PCI bridge [0604]: ATI Technologies Inc Device [1002:43a0]
00:15.1 PCI bridge [0604]: ATI Technologies Inc Device [1002:43a1]
00:15.3 PCI bridge [0604]: ATI Technologies Inc Device [1002:43a3]
00:16.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:16.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1700] (rev 43)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1701]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1702]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1703]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1704]
00:18.5 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1718]
00:18.6 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1716]
00:18.7 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1719]
02:00.0 Class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)
dlb@PresarioCQ57:~$

dlb@PresarioCQ57:~$ rfkill list all
dlb@PresarioCQ57:~$ 

dlb@PresarioCQ57:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
nls_utf8                1069  1 
isofs                  29250  1 
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203376  0 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
uvcvideo               57374  0 
psmouse                63677  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
serio_raw               3978  0 
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  17375  0 
output                  1871  1 video
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_piix4               8335  0 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
usb_storage            39841  2 
r8169                  34140  0 
mii                     4381  1 r8169
ahci                   32360  3 
dlb@PresarioCQ57:~$ 


```

---

### Post by josephmills on 2011-09-17
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [COLOR="Red"][10ec:8176] [/COLOR](rev 01)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
Please try the solution procedure here:

[http://ubuntuforums.org/showthread.php?t=1608908](http://ubuntuforums.org/showthread.php?t=1608908)

KingLear0 is using the same wireless chipset as you are using.

You need the RTL8192CE-VA4 driver.
Mark 
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++



Here's what I did after receiving the info from Mark:

Went to the above thread, which had a link to the Realtek driver website, grabbed the LINUX Realtek RTL8192CE-VA4 driver (previously I had tried to use the Windows 8188 driver from the Dell support website and ndiswrapper to no avail).

After I downloaded the driver I did the following:

1. Make sure you have kernel headers installed (just check in Synaptic "linux-headers-generic") This should be the default in Ubuntu but you never know...
2. Downloaded the Realtek driver to a thumbdrive, opened with archive manager, right click/move to/home folder.
3. Do not unpack the driver archive to the desktop as this causes problems with compiling the driver
4. Open Terminal
5. type command: cd rtl8192se_linux_2.6.0015.0127.2010 (or cd "whatever you have named the new driver folder")
6. type command: sudo su (log in to become "Super user")
7. type command: make (wait for terminal to unpack the file)
8. type command: make install (wait for installation)

9. restart computer
10. using command: lshw -C Network, check to make sure new driver is installed (it should indicate *Network, and the driver can be seen in the Configuration line)
11. Make sure wireless is on (usually F2)
12. Left click the wireless icon to see available networks, and set up your wireless (i had to type in the "key" one time but the rest was already there....

Thanks to the whole community, I love you all. Linux rules. Be good to each other out there.

HighHorse


+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

SOURCE= [https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/132667](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/132667)

---

