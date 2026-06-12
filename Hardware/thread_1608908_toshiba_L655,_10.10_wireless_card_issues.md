---
title: "toshiba L655, 10.10 wireless card issues"
date: 2010-10-29
forum: Hardware
---

### Post by KingLear0 on 2010-10-29
SOLVED - See post #3


Ok, here goes:

I just purchased a new laptop, a Toshiba L655.  The laptop is currently set up dual-boot with Windows 7 and 10.10 Meerkat.  The 10.10 is a fresh install, with all standard updates installed.

Upon install the WIRED ethernet works fine right out of the box.  Wireless, on the other hand doesn't work, and seemingly, Ubuntu does not even detect my wireless card.  I have booted into Windows, and wireless works properly, so I know the card itself functions.

After doing a lot og googling and browsing the forums here, I found many options that might work, but I have been unable to get wireless to function.

I have attempted the following fixes:

1) installed the broadcom driver from the broadcom site (hybrid-*x86-64), and followed the 'readme' file and had no success.

2) installed bcmwl-kernel-source & bcmwl-modaliases via apt-get, with no success.

3) Attempted to use Synaptic to install the above modules, also the b43-fwcutter, and the broadcom STA driver, with no success.

My only guess is that ubuntu just doesn't sse my wireless card at all.

I read through the major thread regarding this type of issue on the forums, in which one post later on indicated that maybe the NIC was turned of in the BIOS, but I was unable to find any such setting in my bios options.

So I'm hoping that I'm just missing something obvious, that I misread one of the posts that deals with fixing this error and maybe someone can direct me.  Below is some information on the laptop:


uname -r

```

2.6.35-22-generic

```

lshw -C Network

```

*-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:d4000000-d4003fff
  *-network
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: c1
       serial: 60:eb:69:46:85:fc
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:48 memory:d3000000-d303ffff ioport:2000(size=128)

```

```

eth0      Link encap:Ethernet  HWaddr 60:eb:69:46:85:fc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:48 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:220 errors:0 dropped:0 overruns:0 frame:0
          TX packets:220 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17184 (17.1 KB)  TX bytes:17184 (17.1 KB)

```

LSPCI:
```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series]
01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
04:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

lsmod

```

Module                  Size  Used by
wl                   1965295  0 
lib80211_crypt_tkip     8732  0 
lib80211                6175  2 wl,lib80211_crypt_tkip
nls_iso8859_1           4657  1 
nls_cp437               6375  1 
vfat                   10954  1 
fat                    56244  1 vfat
binfmt_misc             7984  1 
parport_pc             30086  0 
ppdev                   6804  0 
snd_hda_codec_atihdmi     3079  1 
snd_hda_codec_conexant    37356  1 
snd_hda_intel          26019  4 
snd_hda_codec         100919  3 snd_hda_codec_atihdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  3 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
uvcvideo               62379  0 
videodev               49359  1 uvcvideo
v4l1_compat            15519  2 uvcvideo,videodev
v4l2_compat_ioctl32    12486  1 videodev
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 11363  0 
radeon                906714  2 
snd                    64117  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
ttm                    68212  1 radeon
drm_kms_helper         32836  1 radeon
drm                   206161  4 radeon,ttm,drm_kms_helper
psmouse                62080  0 
i2c_algo_bit            6208  1 radeon
serio_raw               4910  0 
intel_ips              13252  0 
video                  22176  0 
intel_agp              32080  0 
output                  2527  1 video
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
usb_storage            50372  1 
ahci                   21857  0 
libahci                26167  6 ahci
atl1c                  34955  0 

```

---

### Post by KingLear0 on 2010-10-29
Ok, So I keep plugging away...

I need to have the realtek 8185L driver installed.  So I just jumped over and installed ndsiwrapper, then installed the appropriate .inf.  

The problem is that Ubuntu doesn't see the hardware.  

So how do I get Ubuntu to recognize that the hardware exists?

---

### Post by KingLear0 on 2010-10-30
SOLVED:

Toshiba L655 have multiple options on the wireless NIC.  The Wireless NIC in my model required the rtl 8192CE driver, available [Here]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2782")

---

### Post by satellite-of-love on 2010-11-29
> **KingLear0 said:**
> SOLVED:

Toshiba L655 have multiple options on the wireless NIC.  The Wireless NIC in my model required the rtl 8192CE driver, available [Here]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2782")

Thanks for that! It solved my wireless woes with the Realtek 8188CE card in the Toshiba L655!

I found that kernel upgrades will require recompiling the driver, so I included the following function in my .bashrc:

```

# Add a "wificheck" function to see if Realtek driver module is loaded in the running kernel
# Kludged together by Matt Obert on Friday November 26, 2010
function wificheck(){
KERNEL=`uname -r`
RTKMOD=`find /lib/modules/$KERNEL/ -name r8192ce_pci.ko`
echo "Running kernel is $KERNEL"
if [ $RTKMOD = /lib/modules/$KERNEL/kernel/drivers/net/wireless/r8192ce_pci.ko ]; then
      echo "$RTKMOD is loaded in the running kernel."
    else
      echo "Cannot locate r8192ce_pci.ko module in /lib/modules/$KERNEL/kernel/drivers/net/wireless/ directory."
      echo "To enable wireless support for this kernel, compile and install driver module as root, then reboot."
fi
}

```... and in /root/.bashrc I included this:

```

# Add a "wificheck" function to see if Realtek driver module is loaded in the running kernel
# Kludged together by Matt Obert on Friday November 26, 2010
function wificheck(){
CWD=`pwd`
KERNEL=`uname -r`
RTKMOD=`find /lib/modules/$KERNEL/ -name r8192ce_pci.ko`
echo "Running kernel is $KERNEL"
if [ $RTKMOD = /lib/modules/$KERNEL/kernel/drivers/net/wireless/r8192ce_pci.ko ]; then
      echo "$RTKMOD is loaded in running kernel."
    else
      echo "Cannot locate r8192ce_pci.ko module in /lib/modules/$KERNEL/kernel/drivers/net/wireless/ directory."
      echo "To enable wireless support for this kernel, compile and install driver module as root, then reboot."
      echo "Attempting to change working directory to ~/stage/RTL8188CE/rtl8192ce_linux_2.6.0003.0628.2010/ ..."
      echo
      if [ -f ~/stage/RTL8188CE/rtl8192ce_linux_2.6.0003.0628.2010/Makefile ]; then
          cd ~/stage/RTL8188CE/rtl8192ce_linux_2.6.0003.0628.2010/
        else
          echo "Error: Cannot find Makefile. Please compile module manually."
      fi
      echo "Cleaning up any previous installation attempts ..."
      make clean
      echo "Attempting to compile Realtek driver module ..."
      make
      echo "Attempting automatic installation ..."
      make install
      echo "Returning to working directory $CWD ..."
      cd $CWD
fi
}

```

In order for this to work, I had to leave a copy of the unzipped tarball for rtl8192ce_linux_2.6.0003.0628.2010 in the /root/stage/RTL8188CE/ directory.

Now, if I want to see whether the driver module is loaded in the running kernel, I can just type "wificheck" at a bash prompt. If it tells me that the module is not installed, I can simply "sudo su -" and execute the wificheck function as root to automatically compile and install the kernel module.

If a future kernel upgrade breaks the proprietary driver, I may need to edit the bash function to compile a newer version of the Realtek driver ... but until then, it is pretty much idiot-proof.

Hope someone finds this advice helpful!

---

### Post by canucked on 2010-12-09
Just to let you guys know, there's a PPA for the Realtek RTL8188CE:
[https://launchpad.net/~lexical/+archive/hwe-wireless](https://launchpad.net/~lexical/+archive/hwe-wireless)

For beginners, this is what I ran in Terminal to get the Realtek RTL8188CE wireless working on a Toshiba L655:
```
sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms
```

...but nice work with that script, satellite-of-love!

---

### Post by rubenp on 2011-02-06
[B]Thank you a lot.
I had the same problem with mi laptop toshiba c660 - 10d and its device:
Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
as my sistem check says. 
So I just typed the commands above, rebooted and *ya está*.

Thank you ubuntu forums and Keng-Yü Lin.
[/B]

---

### Post by heath_r on 2011-02-09
Thanks canucked,
That worked for L655-S155.

---

### Post by tlcstat on 2011-02-13
Greetings, 
This worked fine on my Toshiba Netbook NB505-N508BN Running Maverick 10.10. As already posted in this thread.

sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms

I did have to go to the "Additional Drivers" under System Preferences after the install and turn the driver off then reboot and turn the driver back on for some reason. But then my card turned on and picked up my router. 

I have the Realtek 8176 (rev 01) card

Thanks for the help.
tlcstat

---

### Post by Colonel_Ingus on 2011-02-15
> **canucked said:**
> Just to let you guys know, there's a PPA for the Realtek RTL8188CE:
[https://launchpad.net/~lexical/+archive/hwe-wireless]("https://launchpad.net/%7Elexical/+archive/hwe-wireless")

For beginners, this is what I ran in Terminal to get the Realtek RTL8188CE wireless working on a Toshiba L655:
```
sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms
```...but nice work with that script, satellite-of-love!

This worked for me to enable it but now have a harder to diagnose problem:

Wireless networking works fine for about 60 seconds then it freezes or something, can't resolve any domain names, and the only way to get it going again is to reconnect... any ideas?

---

### Post by tlcstat on 2011-02-16
Greetings, 
The script worked fine on my Netbook. I was at the Dentist this morning who has wifi in his office. I installed Kmymoney and then did a complete update over his office wifi running at 200mbs. The update included a kernel update and the drivers were active after the new kernel installed. Not a single problem so far. I suggest that you go to your Admin/Additional Drivers link. Disable the driver, reboot and then re-enable the driver. I won't take much time and stands a good chance of working.
tlcstat

---

### Post by gibffe on 2011-02-20
> **Colonel_Ingus said:**
> This worked for me to enable it but now have a harder to diagnose problem:

Wireless networking works fine for about 60 seconds then it freezes or something, can't resolve any domain names, and the only way to get it going again is to reconnect... any ideas?

I have a similar problem using this solution - my internet freezes after a while (usually few minutes) or it'll freeze if I start downloading something. Tried tweaking MTUs but that didn't seem to have any effect. Ideas ?

---

### Post by ELEE on 2011-02-21
IT WORKED FOR ME TOO!!!!

THIS WAS THE BEFORE......

I have a Toshiba Satallite A665D-S5175  I cannot get my Ubuntu 10.04 to detect the wireless.

09:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device 8181
    Flags: bus master, fast devsel, latency 0, IRQ 11
    I/O ports at c000 [size=256]
    Memory at fe900000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>

0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
    Subsystem: Toshiba America Info Systems Device fd30
    Flags: bus master, fast devsel, latency 0, IRQ 28
    I/O ports at b000 [size=256]
    Memory at d0204000 (64-bit, prefetchable) [size=4K]
    Memory at d0200000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

---

### Post by xplaner800 on 2011-02-26
Thanks to canucked. That worked perfectly on L655-S5150

---

### Post by Quickness on 2011-03-27
> **canucked said:**
> Just to let you guys know, there's a PPA for the Realtek RTL8188CE:
[https://launchpad.net/~lexical/+archive/hwe-wireless]("https://launchpad.net/%7Elexical/+archive/hwe-wireless")

For beginners, this is what I ran in Terminal to get the Realtek RTL8188CE wireless working on a Toshiba L655:
```
sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms
```...but nice work with that script, satellite-of-love!


This also worked on my Toshiba Satellite L645D-S4056 !!!  
Thank you so much!

---

### Post by canucked on 2011-04-01
@Colonel_Ingus, gibffe:

According to someone else's post, you may have difficulty maintaining a connection because of the type of wireless encryption in use.

From this post:
[http://ubuntuforums.org/showpost.php?p=10609298&postcount=15](http://ubuntuforums.org/showpost.php?p=10609298&postcount=15)

tdrusk says: "The driver does not seem to connect to WEP 40/128-bit Key with Open Authentication connections well. If you are having problems with the internet not working after a few minutes you may need to change it to a WEP 40/128-bit Key with Shared Authentication."

Because WEP encryption can easily be compromised, I would suggest switching to WPA or WPA2 wireless encryption if possible.

---

### Post by canucked on 2011-04-01
@tlcstat:

After a kernel update in February (I think), the Realtek RTL8188CE wireless on the Toshiba L655 stopped working.  I too had to disable, reboot, then re-enable the restricted driver in Additional Drivers.  Wireless then worked fine.

After the most recent kernel update, I noticed that this kernel module, rtl8192ce-dkms, failed to properly compile according to the Terminal output, yet wireless still worked.  I wonder if support for the RTL8188CE was added to the newer linux kernel.

Also, Ubuntu 10.10 would not allow removal of rtl8192ce-dkms in Synaptic.

I have no interest in reinstalling Ubuntu 10.10 just to find out if wireless works without rtl8192ce-dkms.  But I intend to try the 11.04 Natty beta Live USB to see if wireless works without adding the lexical/hwe-wireless PPA or manually compiling the driver.

---

### Post by goldenskylark on 2011-08-15
Hi all.
I too have been struggling to get my toshi c660d to detect its wirelss card. my os is natty.  i've tried canuck's suggestion, but to not apparent avail.
After the line:
sudo apt-get install rtl8192ce-dkms

i get:[FONT=monospace]
[/FONT] Reading package lists... Done
Building dependency tree       
Reading state information... Done
rtl8192ce-dkms is already the newest version.
The following packages were automatically installed and are no longer required:
  kdelibs4c2a libqt3-mt-mysql kdelibs-data liblualib50 libavahi-qt3-1 barcode
  apport-hooks-medibuntu liblua50
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 29 not upgraded

there's not change with the non-detection of card and as a newbie to ubuntu, i dont know what to do at this point.  :confused: Can anyone clarify the problem?
thanks in advance

---

### Post by kuric on 2011-09-10
Toshiba NB-500 here.
The wireless drivers are working in Ubuntu 11.04, no need to install them manually anymore. 

Although, the internet connection gets freeze for a few seconds **intermittently**. And I'me using WPA2 wireless encryption.

Any thoughts on this? I believe that this wifi drivers issue is causing a little overheating and excessive power consumption too.

---

### Post by anofeles on 2011-10-27
This fixed it for my HP Mini 110-3700 using Ubuntu 10.04

---

