---
title: "Wifi"
date: 2008-08-21
forum: Hardware
---

### Post by manolomanolo on 2008-08-21
I've been using my wireless card for a while with no problems. Then I've been connecting with cable. Now I'm unable to connect with wireless anymore. It does work with Windows XP.
Thanks for your time.
Regards.

manolo@manolo-laptop:~$ **lsmod**
Module                  Size  Used by
binfmt_misc            12808  1 
ppdev                  10372  0 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ipv6                  267780  14 
acpi_cpufreq           10796  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  2 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8712  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
container               5632  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
af_packet              23812  6 
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
video                  19856  0 
output                  4736  1 video
battery                14212  0 
ac                      6916  0 
psmouse                40336  0 
sdhci                  19076  0 
iwl3945                89588  0 
snd_hda_intel         359192  5 
serio_raw               7940  0 
ricoh_mmc               4352  0 
mmc_core               51460  1 sdhci
mac80211              221684  1 iwl3945
snd_hwdep              10628  1 snd_hda_intel
fglrx                1555468  23 
cfg80211               35168  2 iwl3945,mac80211
snd_seq_dummy           4996  0 
asus_laptop            19064  0 
led_class               6020  1 asus_laptop
button                  9232  0 
snd_seq_oss            35456  0 
snd_seq_midi            9504  0 
evdev                  13056  7 
snd_rawmidi            25888  1 snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
snd_pcm_oss            42528  0 
snd_mixer_oss          18048  1 snd_pcm_oss
snd_seq                54096  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_pcm                78852  3 snd_hda_intel,snd_pcm_oss
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4224  0 
intel_agp              25492  0 
snd_timer              24964  3 snd_seq,snd_pcm
snd                    57124  19 snd_hda_intel,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_pcm,snd_seq_device,snd_timer
agpgart                34760  2 fglrx,intel_agp
snd_page_alloc         11656  2 snd_hda_intel,snd_pcm
soundcore               8800  1 snd
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
ext2                   73352  2 
mbcache                 9600  1 ext2
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  6 
usbhid                 31872  0 
hid                    38784  1 usbhid
ata_piix               19588  5 
pata_acpi               8320  0 
ata_generic             8324  0 
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
libata                159344  3 ata_piix,pata_acpi,ata_generic
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  4 usbhid,ehci_hcd,uhci_hcd
r8169                  32900  0 
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fuse                   50708  7 
vesafb                  8964  1 
fbcon                  42912  72 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
manolo@manolo-laptop:~$


manolo@manolo-laptop:~$ **lspci**
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
06:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
06:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
06:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
manolo@manolo-laptop:~$ 


manolo@manolo-laptop:~$ **dmesg |grep -i iwl3945**
[   33.285577] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26k
[   33.285585] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   33.311164] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   33.482805] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels


**dmesg | grep -i intel**
[   14.734491] CPU0: Intel Genuine Intel(R) CPU           T2250  @ 1.73GHz stepping 08
[   14.824563] CPU1: Intel Genuine Intel(R) CPU           T2250  @ 1.73GHz stepping 08
[   29.346211] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   33.285577] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26k
[   33.285585] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   33.311164] iwl3945: Detected Intel Wireless WiFi Link 3945ABG

---

### Post by pytheas22 on 2008-08-21
There seem to be a lot of bugs lately with the iwl3945 driver, so I assume that that's what's going on in your case.  It probably used to work, but an update broke it.  Unfortunately dmesg doesn't mention anything very useful about why it won't work.

The simplest solution is probably just to switch to ndiswrapper.  This [thread]("http://ubuntuforums.org/showthread.php?t=765647") has instructions (see post 10) that should work for your card.  If you can't figure out which Windows drivers to use, post the output of:
```

lspci -nn | grep Wireless
```

and I'll find good ones.

---

### Post by manolomanolo on 2008-08-22
Can you send me some link related to the bugs you're referring to, please?

lspci -nn | grep Wireless
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)

Thanks for your time!

---

### Post by pytheas22 on 2008-08-22
To use ndiswrapper instead, please try this:

```
sudo apt-get install ndiswrapper*
echo 'blacklist iwl3945' | sudo tee -a /etc/modprobe.d/blacklist
echo 'ndiswrapper' | sudo tee -a /etc/modules
wget http://burnthesorbonne.com/files/Intel_ipw2200_x32_drivers.tar.gz
tar -xzvf Intel*
cd Intel*
sudo ndiswrapper -i NETw5x32.inf
```

Then reboot and see if things work better.  If not, please post:
```

lshw -C Network
dmesg | grep ndis
ndiswrapper -l
```
> 
Can you send me some link related to the bugs you're referring to, please?

Sure, here are links to threads that I've been involved in lately regarding problems with iwl3945: [http://ubuntuforums.org/showthread.php?t=881757&page=2](http://ubuntuforums.org/showthread.php?t=881757&page=2) ; [http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=5275256](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=5275256) ; [http://georgia.ubuntuforums.org/showthread.php?t=844426](http://georgia.ubuntuforums.org/showthread.php?t=844426) ; [http://ubuntuforums.org/showthread.php?t=891713](http://ubuntuforums.org/showthread.php?t=891713) .  Most of them seem to come down to kernel updates that include a bad build of the iwl3945 driver, but for some reason it still gets pushed out.

---

### Post by manolomanolo on 2008-09-04
I followed your instruction, except that I downloaded Intel_ipw2200_x32_drivers.tar.gz manually to my Desktop, extracted it and run ndiswrapper from there...
I don't think it's working.

**sudo lshw -C Network**
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:17:31:fb:61:25
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.3 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0


**dmesg | grep ndis**
[   30.269024] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   30.456407] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeBugCheck'
[   30.456639] ndiswrapper (load_sys_files:210): couldn't prepare driver 'netw5x32'
[   30.457435] ndiswrapper (load_wrap_driver:112): couldn't load driver netw5x32; check system log for messages from 'loadndisdriver'
[   30.458799] usbcore: registered new interface driver ndiswrapper


** ndiswrapper -l**
netw5x32 : driver installed
	device (8086:4222) present (alternate driver: iwl3945)

---

### Post by pytheas22 on 2008-09-05
hmmm, I'm not sure what's going on.  There's a problem with the Windows drivers that you loaded--ndiswrapper doesn't like them for some reason--but they should work, according to the ndiswrapper site.

You may want to try just going back to the iwl3945 driver, because it may be easier.  Try running these commands:
```

sudo sed 's/iwl3945/ndiswrapper/g' /etc/modprobe.d/blacklist
sudo rmmod ndiswrapper
sudo modprobe iwl3945
dmesg | grep -e ndis -e iwl -e wlan -e eth1
```

Please post all of the output.  Hopefully this will work, or will lead to a concrete solution as to why iwl3945 won't work.  In a worst case, you can compile the latest iwl3945 from source, which may help.

Otherwise, we can keep fighting with ndiswrapper, but since I'm perplexed as to why it doesn't want to work, I think it makes the most sense right now to give iwl3945 another shot.

---

### Post by Crafty Kisses on 2008-09-05
Please do:
```
sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
```
Now does your card scan and connect as expected?

---

### Post by manolomanolo on 2008-09-05
> Now does your card scan and connect as expected? 

sudo rmmod -f iwl3945
ERROR: Removing 'iwl3945': No such file or directory
manolo@manolo-laptop:~$ sudo modprobe iwl3945 disable_hw_scan=1

I loaded Kwifimanager and it doesn't scan as I expect (it says 'The scan is complete, but no networks have been found.').

---

### Post by pytheas22 on 2008-09-05
Please try running these as well and post the output:
```

sudo sed 's/iwl3945/ndiswrapper/g' /etc/modprobe.d/blacklist
sudo rmmod ndiswrapper
sudo modprobe iwl3945
dmesg | grep -e ndis -e iwl -e wlan -e eth1
```

---

### Post by manolomanolo on 2008-09-05
manolo@manolo-laptop:~$ **sudo sed 's/iwl3945/ndiswrapper/g' /etc/modprobe.d/blacklist**
[sudo] password for manolo: 
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# MANOLO: this should remove the "intel_rng: FWH not detected" error
blacklist intel_rng

blacklist ndiswrapper
manolo@manolo-laptop:~$ **sudo rmmod ndiswrapper**
manolo@manolo-laptop:~$  **sudo modprobe iwl3945**
manolo@manolo-laptop:~$ **dmesg | grep -e ndis -e iwl -e wlan -e eth1**
[   48.915008] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   49.110643] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeBugCheck'
[   49.111141] ndiswrapper (load_sys_files:210): couldn't prepare driver 'netw5x32'
[   49.112659] ndiswrapper (load_wrap_driver:112): couldn't load driver netw5x32; check system log for messages from 'loadndisdriver'
[   49.115266] usbcore: registered new interface driver ndiswrapper
[  669.198673] usbcore: deregistering interface driver ndiswrapper
[  669.204239] ndiswrapper (ntoskernel_exit:2708): object df986520(2) was not freed, freeing it now
[  736.144709] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26k
[  736.144723] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[  736.144949] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[  736.206441] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[  736.207410] phy0: Selected rate control algorithm 'iwl-3945-rs'
[  736.501500] ADDRCONF(NETDEV_UP): wlan0: link is not ready
manolo@manolo-laptop:~$ 

One more time kWIFImanager gives the same message: no network found.
Remark I can do connect to my wifi network through Windows XP and through another Ubuntu machine...

---

### Post by pytheas22 on 2008-09-05
Sorry that all that didn't help.  I know that kwifi can't see networks; that's the problem: everything looks like it should work (the module is inserted without a problem, etc.), but for some reason it won't.

I found [this thread]("http://bbs.archlinux.org/viewtopic.php?pid=331641") that seems to describe the exact same problem.  The solution there was to edit /etc/rc.local.  So open up that file:

```
sudo kate /etc/rc.local
```

and make it look like this:
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

modprobe -r iwl3945
modprobe iwl3945

exit 0
```

Then save and close the file, and reboot.  Does the wireless work now?

I don't really know why this would work (you're just reinserting the module), but at least two people said it fixed the problem for them, so it's worth a try.  Please let me know if it helps.

---

### Post by manolomanolo on 2008-09-06
No way. kWIFImanager still gives the same message.
Is it worth trying to make it work through command line?
I mean starting from the beginning (making sure the module is loaded, activating wireless card and so on...)?

thanks for your time.
regards.

---

### Post by pytheas22 on 2008-09-07
Sorry for not responding sooner; I've been away.

> Is it worth trying to make it work through command line?
I mean starting from the beginning (making sure the module is loaded, activating wireless card and so on...)?


It could help, although I admit at this point that I'm not sure where to go next.

One other possible thing that we should check on is that your wireless router is broadcasting on the same frequency as your card is operating in (i.e., they both need to be on 11g or 11b).  Have you checked your router to make sure it's operating in the right mode?  And what is the output of:
```

iwconfig
```

---

### Post by manolomanolo on 2008-09-08
manolo@manolo-laptop:~$ **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr=2352 B   
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

It's the first time I can see that wmaster0 in that list... maybe because of the last tries I've been doing following your advices?

As for the 11b or 11g mode I can see wireless on my router is set to "mixed mode" which should mean using both b and g mode.
How to check whether my wifi card is set accordingly or not?

Thanks for your time.
Regards.

---

### Post by pytheas22 on 2008-09-08
The 'iwconfig' output above says that the card's operating in a, b AND g modes, which is actually a little strange--as far as I know, the card is supposed to be operating on one mode only at a time:
```

wlan0 IEEE **802.11abg** ESSID:""
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
Tx-Power=0 dBm
Retry min limit:7 RTS thr: off Fragment thr=2352 B
Power Management: off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
```

You can try running these commands to switch it to g mode only:
```

sudo iwconfig wlan0 modu 11g
```

If you get an error, try:
```

sudo iwpriv wlan0 network_type g
```

If you still get an error, try:
```

sudo iwpriv wlan0 mode 11g
```

(The method used to switch the mode varies by driver, and I'm not sure what iwl3945 uses...hopefully one of the above commands will work.)  If the mode changes successfully, then you should see in 'iwconfig' only '802.11g,' with no a or b.

You could also try changing your router to operate only in one mode (b or g), not mixed, to see if it makes a difference.

---

### Post by manolomanolo on 2008-09-09
manolo@manolo-laptop:~$ **sudo iwconfig wlan0 modu 11g**
[sudo] password for manolo: 
Error for wireless request "Set Modulation" (8B2F) :
    SET failed on device wlan0 ; Operation not supported.


manolo@manolo-laptop:~$ **sudo iwpriv wlan0 network_type g**
wlan0     no private ioctls.


manolo@manolo-laptop:~$ **sudo iwpriv wlan0 mode 11g**
wlan0     no private ioctls.

After that I tried with kWIFImanager but still no luck :(

---

### Post by pytheas22 on 2008-09-09
hmmmm, sorry that you're still not having success.  One possible solution is to install the ipw3945 driver.  But before doing that, please post a little bit more information, just in case it leads to an easier solution (installing ipw3945 would probably not be very easy).  Please reboot, then post the output of:
```

iwlist scan; iwlist scan
dmesg | tail
dmesg | grep -e iwl -e wlan -e eth1 -e scan -e radio
```

---

### Post by manolomanolo on 2008-09-10
manolo@manolo-laptop:~$ **iwlist scan; iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

manolo@manolo-laptop:~$ **dmesg | tail**
[  105.645359]   groups: 02 01
[  188.817276] iwl3945: Radio Frequency Kill Switch is On:
[  188.817283] Kill switch must be turned off for wireless networking to work.
[  247.269492] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[  247.285226] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[  247.285361] PM: Writing back config space on device 0000:03:00.0 at offset 1 (was 100002, writing 100006)
[  247.343382] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  308.224196] r8169: eth0: link up
[  308.228271] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  324.510051] eth0: no IPv6 routers present
manolo@manolo-laptop:~$ **dmesg | grep -e iwl -e wlan -e eth1 -e scan -e radio**
[   64.023111] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26k
[   64.023122] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   64.023352] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   64.084989] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   64.087095] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   64.576927] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  188.817276] iwl3945: Radio Frequency Kill Switch is On:
[  247.343382] ADDRCONF(NETDEV_UP): wlan0: link is not ready
manolo@manolo-laptop:~$

Searching Goolge for "Kill switch must be turned off for wireless networking to work."
I found:
[http://survivor.sarovar.org/Wireless.html](http://survivor.sarovar.org/Wireless.html)
[http://www.thinkwiki.org/wiki/Intel_PRO/Wireless_3945ABG_Mini-PCI_Express_Adapter](http://www.thinkwiki.org/wiki/Intel_PRO/Wireless_3945ABG_Mini-PCI_Express_Adapter)

As for the first link I did press Fn+F2 and tried back again with kWIFImanager and those last commands you posted, but still no luck. I've been doing many tries with those last commands (iwlist and those two dmesg) supposing wireless card needs a while to start working (activating, scanning for wifi nets etc) but no luck. I've been pressing some times more that Fn+F2 to see if something changes but those dmesg give quite the same result as before.
Should I do something more following those two links or something elese?

Thanks for your time.
Regards.

---

### Post by pytheas22 on 2008-09-10
Ahh, the radio kill switch does indeed appear to be the problem.  Sorry it took so long to discover that.

I'm trying to help someone else with the exact same problem in [this thread]("http://ubuntuforums.org/showthread.php?t=909331").  He or she also uses the iwl3945 driver and is getting the "radio disabled" message no matter how many times the button is pressed to turn on the radio.  This [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/193970") also seems to be describing the same issue.

Please try doing this (the bug report says it works):

1. press Fn+F2
2. run:
```

sudo rmmod iwl3945; sudo modprobe iwl3945
```
3. wait a few seconds.  Does the wireless work?  If not, does the output of "dmesg | tail" still mention radio being disabled?
4. if the wireless is still disabled, press Fn+F2 again, then run again:
```

sudo rmmod iwl3945; sudo modprobe iwl3945
```

and wait again a few seconds to see if the wireless is fixed.

Please let me know if that makes a difference.

---

### Post by manolomanolo on 2008-09-10
Thanks for your support.

I'm about to make those further tests, as you say.
I'm now turning on my wifi card through the physical switch (It allows to turn it ON and OFF, and when I don't use it I put it in OFF. It's not the Fn+F2 key, I hope you know what I mean). So, before executing those last commands you've been posting, I executed:

manolo@manolo-laptop:~/sources/pgsql$ **iwlist scan; iwlist scan**
lo        Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

eth0      Interface doesn't support scanning.

manolo@manolo-laptop:~/sources/pgsql$ **dmesg | tail**
[11250.268992] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[11250.269425] iwl3945: Radio disabled by HW RF Kill switch
[11710.589892] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[11710.590522] iwl3945: Radio disabled by HW RF Kill switch
[11710.592451] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[11710.593003] iwl3945: Radio disabled by HW RF Kill switch
[11913.736517] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[11913.737421] iwl3945: Radio disabled by HW RF Kill switch
[12251.982134] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[12252.046602] ADDRCONF(NETDEV_UP): wlan0: link is not ready

manolo@manolo-laptop:~/sources/pgsql$ **dmesg | grep -e iwl -e wlan -e eth1 -e scan -e radio**
[   64.023111] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26k
[   64.023122] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   64.023352] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   64.084989] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   64.087095] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   64.576927] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  188.817276] iwl3945: Radio Frequency Kill Switch is On:
[  247.343382] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2291.719895] iwl3945: Radio Frequency Kill Switch is On:
[12578.368851] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[12578.418722] iwl3945: MAC is in deep sleep!
[12578.419231] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[12578.479111] iwl3945: MAC is in deep sleep!
[12578.479598] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[12578.539477] iwl3945: MAC is in deep sleep!
[12578.650124] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[    4.438689] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26k
[    4.438696] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[    4.438822] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[    4.500538] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[    4.501306] phy0: Selected rate control algorithm 'iwl-3945-rs'
[    4.666979] iwl3945: Radio disabled by HW RF Kill switch
[    4.816898] iwl3945: Radio disabled by HW RF Kill switch
[    4.876373] iwl3945: Radio disabled by HW RF Kill switch
[    4.877190] iwl3945: Radio disabled by HW RF Kill switch
[    4.992021] iwl3945: Radio disabled by HW RF Kill switch
[    5.017502] iwl3945: Radio disabled by HW RF Kill switch
[    5.018303] iwl3945: Radio disabled by HW RF Kill switch
[   37.683061] iwl3945: Radio disabled by HW RF Kill switch
[   37.970621] iwl3945: Radio disabled by HW RF Kill switch
[  240.927412] iwl3945: Radio disabled by HW RF Kill switch
[  557.309188] iwl3945: Radio disabled by HW RF Kill switch
[  834.652076] iwl3945: Radio disabled by HW RF Kill switch
[  834.655884] iwl3945: Radio disabled by HW RF Kill switch
[ 1077.950562] iwl3945: Radio disabled by HW RF Kill switch
[ 1077.961045] iwl3945: Radio disabled by HW RF Kill switch
[ 1372.186457] iwl3945: Radio disabled by HW RF Kill switch
[ 1703.434388] iwl3945: Radio disabled by HW RF Kill switch
[ 1703.437371] iwl3945: Radio disabled by HW RF Kill switch
[ 1988.615386] iwl3945: Radio disabled by HW RF Kill switch
[ 2274.821569] iwl3945: Radio disabled by HW RF Kill switch
[ 2274.833810] iwl3945: Radio disabled by HW RF Kill switch
[ 2709.136086] iwl3945: Radio disabled by HW RF Kill switch
[ 2709.162606] iwl3945: Radio disabled by HW RF Kill switch
[ 2897.290936] iwl3945: Radio disabled by HW RF Kill switch
[ 2897.298638] iwl3945: Radio disabled by HW RF Kill switch
[ 3376.635059] iwl3945: Radio disabled by HW RF Kill switch
[ 3376.638740] iwl3945: Radio disabled by HW RF Kill switch
[ 3723.872821] iwl3945: Radio disabled by HW RF Kill switch
[ 4070.137706] iwl3945: Radio disabled by HW RF Kill switch
[ 4070.141097] iwl3945: Radio disabled by HW RF Kill switch
[ 4345.331493] iwl3945: Radio disabled by HW RF Kill switch
[ 4345.339456] iwl3945: Radio disabled by HW RF Kill switch
[ 4818.660654] iwl3945: Radio disabled by HW RF Kill switch
[ 4818.666363] iwl3945: Radio disabled by HW RF Kill switch
[ 5229.904911] iwl3945: Radio disabled by HW RF Kill switch
[ 5497.147864] iwl3945: Radio disabled by HW RF Kill switch
[ 5767.345342] iwl3945: Radio disabled by HW RF Kill switch
[ 6067.559372] iwl3945: Radio disabled by HW RF Kill switch
[ 6067.562030] iwl3945: Radio disabled by HW RF Kill switch
[ 6432.809955] iwl3945: Radio disabled by HW RF Kill switch
[ 6653.970372] iwl3945: Radio disabled by HW RF Kill switch
[ 6653.976673] iwl3945: Radio disabled by HW RF Kill switch
[ 6928.174861] iwl3945: Radio disabled by HW RF Kill switch
[ 7120.311078] iwl3945: Radio disabled by HW RF Kill switch
[ 7120.317225] iwl3945: Radio disabled by HW RF Kill switch
[ 7448.545180] iwl3945: Radio disabled by HW RF Kill switch
[ 7448.547741] iwl3945: Radio disabled by HW RF Kill switch
[ 7893.863747] iwl3945: Radio disabled by HW RF Kill switch
[ 8259.219645] iwl3945: Radio disabled by HW RF Kill switch
[ 8461.274521] iwl3945: Radio disabled by HW RF Kill switch
[ 8706.449706] iwl3945: Radio disabled by HW RF Kill switch
[ 9094.703002] iwl3945: Radio disabled by HW RF Kill switch
[ 9094.706655] iwl3945: Radio disabled by HW RF Kill switch
[ 9538.035175] iwl3945: Radio disabled by HW RF Kill switch
[ 9538.040861] iwl3945: Radio disabled by HW RF Kill switch
[ 9747.172647] iwl3945: Radio disabled by HW RF Kill switch
[10034.394526] iwl3945: Radio disabled by HW RF Kill switch
[10034.398802] iwl3945: Radio disabled by HW RF Kill switch
[10274.565482] iwl3945: Radio disabled by HW RF Kill switch
[10499.737613] iwl3945: Radio disabled by HW RF Kill switch
[10867.988093] iwl3945: Radio disabled by HW RF Kill switch
[11250.266794] iwl3945: Radio disabled by HW RF Kill switch
[11250.269425] iwl3945: Radio disabled by HW RF Kill switch
[11710.590522] iwl3945: Radio disabled by HW RF Kill switch
[11710.593003] iwl3945: Radio disabled by HW RF Kill switch
[11913.737421] iwl3945: Radio disabled by HW RF Kill switch
[12252.046602] ADDRCONF(NETDEV_UP): wlan0: link is not ready

Now. I press **Fn+F2** and

manolo@manolo-laptop:~/sources/pgsql$ **sudo rmmod iwl3945; sudo modprobe iwl3945**
[sudo] password for manolo: 
manolo@manolo-laptop:~/sources/pgsql$

then I've been waiting for half a minute but kWIFImanager still gives the same message. That's the present **iwconfig** and **dhclient** output

manolo@manolo-laptop:~/sources/pgsql$ **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

manolo@manolo-laptop:~/sources/pgsql$ **sudo dhclient wlan0**
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:13:02:ef:81:1f
Sending on   LPF/wlan0/00:13:02:ef:81:1f
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

manolo@manolo-laptop:~/sources/pgsql$ **dmesg | tail**
[12727.384046] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[12727.384262] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[12727.384287] PCI: Setting latency timer of device 0000:03:00.0 to 64
[12727.384321] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[12727.429031] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[12727.430981] phy1: Selected rate control algorithm 'iwl-3945-rs'
[12727.804332] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[12728.048571] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[12728.216706] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[12728.280533] ADDRCONF(NETDEV_UP): wlan0: link is not ready

which doesn't seem to show that radio has been disabled...
My last try with kWIFImanager still gives "The scan is complete, but no networks have been found."

---

### Post by pytheas22 on 2008-09-11
hmmmm, I'm sorry that none of that helped.  To be honest I'm not really sure where to go next; I think we've exhausted all of the suggestions that I could find on Google.

One thing to try, and which should be relatively easy, is compiling the latest iwl3945 driver from source.  To do that, run these commands:

```
sudo apt-get install build-essential
wget http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-3945-ucode-15.28.1.6.tgz
tar -xzvf iwlwifi*
cp iwlwifi-3945-ucode-15.28.1.6/iwlwifi-3945-1.ucode /lib/firmware
wget http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2
bunzip2 compat-wireless*
tar xf compat-wireless*
cd compat-wireless-2.6-old/
make ###it will take a few minutes here to compile\; go get a coffee or something
sudo make install
sudo make unload
sudo make load
```

That would give you the very latest stable release of iwl3945 (dated from early this month); hopefully whatever bug is causing the problem for you will be fixed in that release (the module used by default in Ubuntu is probably at least several months old).  After running all of the above, reboot and see what happens.

---

### Post by manolomanolo on 2008-09-11
manolo@manolo-laptop:~$ **sudo apt-get install build-essential**
[sudo] password for manolo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
manolo@manolo-laptop:~$ **wget [http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-3945-ucode-15.28.1.6.tgz](http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-3945-ucode-15.28.1.6.tgz)**
--01:00:14--  [http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-3945-ucode-15.28.1.6.tgz](http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-3945-ucode-15.28.1.6.tgz)
           => `iwlwifi-3945-ucode-15.28.1.6.tgz'
Resolving intellinuxwireless.org... 204.253.143.234
Connecting to intellinuxwireless.org|204.253.143.234|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 67,178 (66K) [application/x-gzip]

100%[====================================>] 67,178        63.51K/s             

01:00:16 (63.35 KB/s) - `iwlwifi-3945-ucode-15.28.1.6.tgz' saved [67178/67178]

manolo@manolo-laptop:~$ **tar -xzvf iwlwifi***
iwlwifi-3945-ucode-15.28.1.6/
iwlwifi-3945-ucode-15.28.1.6/LICENSE.iwlwifi-3945-ucode
iwlwifi-3945-ucode-15.28.1.6/README.iwlwifi-3945-ucode
iwlwifi-3945-ucode-15.28.1.6/iwlwifi-3945-1.ucode
manolo@manolo-laptop:~$ [B]sudo cp iwlwifi-5000-ucode-5.4.A.11/iwlwifi-5000-1.ucode /lib/firmware
cp: cannot stat `iwlwifi-5000-ucode-5.4.A.11/iwlwifi-5000-1.ucode': No such file or directory[/B]
manolo@manolo-laptop:~$ sudo cp iwlwifi-3945-ucode-15.28.1.6   /lib/firmware
iwlwifi-3945-ucode-15.28.1.6/     iwlwifi-3945-ucode-15.28.1.6.tgz
manolo@manolo-laptop:~$ sudo cp iwlwifi-3945-ucode-15.28.1.6/iwlwifi-3945-1.ucode   /lib/firmware
iwlwifi-3945-1.ucode
manolo@manolo-laptop:~$ **cd iwlwifi-3945-ucode-15.28.1.6/**
manolo@manolo-laptop:~/iwlwifi-3945-ucode-15.28.1.6$ ls -la
total 172
drwxr-xr-x   2 manolo manolo   4096 2008-08-07 22:45 .
drwxr-xr-x 108 manolo manolo   4096 2008-09-12 01:00 ..
-r--r--r--   1 manolo manolo 150860 2008-08-07 22:45 iwlwifi-3945-1.ucode
-r--r--r--   1 manolo manolo   2109 2008-08-07 22:45 LICENSE.iwlwifi-3945-ucode
-r--r--r--   1 manolo manolo   5821 2008-08-07 22:45 README.iwlwifi-3945-ucode
manolo@manolo-laptop:~/iwlwifi-3945-ucode-15.28.1.6$ sudo cp iwlwifi-3945-1.ucode /lib/firmware/
manolo@manolo-laptop:~/iwlwifi-3945-ucode-15.28.1.6$ ls -la /lib/firmware/
total 360
drwxr-xr-x  4 root root   4096 2008-09-12 01:03 .
drwxr-xr-x 16 root root   4096 2008-09-07 04:45 ..
drwxr-xr-x  4 root root   4096 2008-06-04 00:51 2.6.24-18-generic
drwxr-xr-x  4 root root   8192 2008-08-02 20:46 2.6.24-19-generic
-r--r--r--  1 root root 150860 2008-09-12 01:03 **iwlwifi-3945-1.ucode**
-rw-r--r--  1 root root 187672 2008-08-02 18:29 **iwlwifi-4965-2.ucode**
manolo@manolo-laptop:~/iwlwifi-3945-ucode-15.28.1.6$ cd
manolo@manolo-laptop:~$ wget [http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2](http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2)
--01:03:57--  [http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2](http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2)
           => `compat-wireless-old.tar.bz2'
Resolving linuxwireless.org... 83.246.72.84
Connecting to linuxwireless.org|83.246.72.84|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,538,383 (1.5M) [application/octet-stream]

100%[====================================>] 1,538,383    540.67K/s             

01:04:01 (539.47 KB/s) - `compat-wireless-old.tar.bz2' saved [1538383/1538383]

manolo@manolo-laptop:~$ bunzip2 compat-wireless*
manolo@manolo-laptop:~$ tar xf compat-wireless*
manolo@manolo-laptop:~$ cd compat-wireless-2.6-old/
manolo@manolo-laptop:~/compat-wireless-2.6-old$ make
./scripts/gen-compat-autoconf.sh config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/2.6.24-19-generic/build M=/home/manolo/compat-wireless-2.6-old modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
/home/manolo/compat-wireless-2.6-old/config.mk:54: **"WARNING: You are running a kernel >= 2.6.23, you should enable in it CONFIG_NETDEVICES_MULTIQUEUE for 802.11[ne] support"**
  LD      /home/manolo/compat-wireless-2.6-old/drivers/misc/built-in.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/misc/eeprom_93cx6.o
  LD      /home/manolo/compat-wireless-2.6-old/drivers/net/built-in.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/b44.o
  LD      /home/manolo/compat-wireless-2.6-old/drivers/net/usb/built-in.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/usb/cdc_ether.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/usb/rndis_host.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/usb/usbnet.o
  LD      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/built-in.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/ipw2100.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/ipw2200.o
include/asm/io_32.h: In function &#8216;memcpy_toio&#8217;:
include/asm/io_32.h:217: warning: passing argument 1 of &#8216;__memcpy&#8217; discards qualifiers from pointer target type
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/at76_usb.o
/home/manolo/compat-wireless-2.6-old/drivers/net/wireless/at76_usb.c:885: warning: &#8216;at76_set_associd&#8217; defined but not used
/home/manolo/compat-wireless-2.6-old/drivers/net/wireless/at76_usb.c:903: warning: &#8216;at76_set_listen_interval&#8217; defined but not used
/home/manolo/compat-wireless-2.6-old/drivers/net/wireless/at76_usb.c:989: warning: &#8216;at76_add_mac_address&#8217; defined but not used
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rndis_wlan.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rtl8180_dev.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rtl8180_rtl8225.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rtl8180_sa2400.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rtl8180_max2820.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rtl8180_grf5101.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rtl8187_dev.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rtl8187_rtl8225.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rtl8180.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rtl8187.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/adm8211.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/mac80211_hwsim.o
  LD      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/ath5k/built-in.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/ath5k/base.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/ath5k/hw.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/ath5k/initvals.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/ath5k/phy.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/ath5k/ath5k.o
  LD      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/ath9k/built-in.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/ath9k/hw.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/ath9k/phy.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/ath9k/regd.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/ath9k/beacon.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/ath9k/main.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/ath9k/recv.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/ath9k/xmit.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/ath9k/rc.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/ath9k/core.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/ath9k/ath9k.o
  LD      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/b43/built-in.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/b43/main.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/b43/tables.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/b43/phy_common.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/b43/phy_g.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/b43/phy_a.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/b43/sysfs.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/b43/xmit.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/b43/lo.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/b43/wa.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/b43/dma.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/b43/pio.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/b43/rfkill.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/b43/leds.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/b43/pcmcia.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/b43/debugfs.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/b43/b43.o
  LD      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/built-in.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/main.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/ilt.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/phy.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/radio.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/sysfs.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/xmit.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/debugfs.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/dma.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/pio.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/b43legacy.o
  LD      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/built-in.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl3945-base.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-3945.o
/home/manolo/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-3945.c: In function &#8216;iwl3945_pass_packet_to_mac80211&#8217;:
/home/manolo/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-3945.c:633: warning: unused variable &#8216;hdr&#8217;
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-3945-rs.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl4965-base.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-4965.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-4965-rs.o
/home/manolo/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-4965-rs.c: In function &#8216;rs_clear&#8217;:
/home/manolo/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-4965-rs.c:2405: warning: unused variable &#8216;priv&#8217;
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-core.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-eeprom.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-hcmd.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-power.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-rx.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-tx.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-sta.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-calib.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-scan.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwlcore.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl3945.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl4965.o
  LD      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/libertas/built-in.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/libertas/main.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/libertas/wext.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/libertas/rx.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/libertas/tx.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/libertas/cmd.o
/home/manolo/compat-wireless-2.6-old/drivers/net/wireless/libertas/cmd.c: In function &#8216;lbs_set_channel&#8217;:
/home/manolo/compat-wireless-2.6-old/drivers/net/wireless/libertas/cmd.c:841: warning: unused variable &#8216;old_channel&#8217;
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/libertas/cmdresp.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/libertas/scan.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/libertas/11d.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/libertas/debugfs.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/libertas/persistcfg.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/libertas/ethtool.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/libertas/assoc.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/libertas/if_cs.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/libertas/if_sdio.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/libertas/if_usb.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/libertas/usb8xxx.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_cs.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_sdio.o
  LD      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/p54/built-in.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/p54/p54common.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/p54/p54usb.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/p54/p54pci.o
  LD      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/built-in.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00dev.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00mac.o
/home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00mac.c: In function &#8216;rt2x00mac_conf_tx&#8217;:
/home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00mac.c:557: warning: comparison is always true due to limited range of data type
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00config.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00queue.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00rfkill.o
/home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00rfkill.c:64: warning: &#8216;rt2x00rfkill_get_state&#8217; defined but not used
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00firmware.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00lib.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00pci.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00usb.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2400pci.o
include/asm/io_32.h: In function &#8216;memcpy_toio&#8217;:
include/asm/io_32.h:217: warning: passing argument 1 of &#8216;__memcpy&#8217; discards qualifiers from pointer target type
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500pci.o
include/asm/io_32.h: In function &#8216;memcpy_toio&#8217;:
include/asm/io_32.h:217: warning: passing argument 1 of &#8216;__memcpy&#8217; discards qualifiers from pointer target type
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt61pci.o
include/asm/io_32.h: In function &#8216;memcpy_toio&#8217;:
include/asm/io_32.h:217: warning: passing argument 1 of &#8216;__memcpy&#8217; discards qualifiers from pointer target type
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500usb.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt73usb.o
  LD      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/built-in.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_chip.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_ieee80211.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_mac.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_rf_al2230.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_rf_rf2959.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_rf_al7230b.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_rf_uw2453.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_rf.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_usb.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd1211rw.o
  LD      /home/manolo/compat-wireless-2.6-old/drivers/ssb/built-in.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/ssb/main.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/ssb/scan.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/ssb/sprom.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/ssb/pci.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/ssb/pcihost_wrapper.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/ssb/pcmcia.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/ssb/driver_chipcommon.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/ssb/driver_pcicore.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/drivers/ssb/b43_pci_bridge.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/ssb/ssb.o
  LD      /home/manolo/compat-wireless-2.6-old/net/ieee80211/built-in.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/ieee80211/ieee80211_module.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/ieee80211/ieee80211_tx.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/ieee80211/ieee80211_rx.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/ieee80211/ieee80211_wx.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/ieee80211/ieee80211_geo.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/net/ieee80211/ieee80211.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_wep.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_ccmp.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_tkip.o
  LD      /home/manolo/compat-wireless-2.6-old/net/mac80211/built-in.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/mac80211/main.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/mac80211/wext.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/mac80211/sta_info.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/mac80211/wep.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/mac80211/wpa.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/mac80211/mlme.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/mac80211/iface.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/mac80211/rate.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/mac80211/michael.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/mac80211/tkip.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/mac80211/aes_ccm.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/mac80211/cfg.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/mac80211/rx.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/mac80211/tx.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/mac80211/key.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/mac80211/util.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/mac80211/event.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/mac80211/led.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/mac80211/debugfs.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/mac80211/debugfs_sta.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/mac80211/debugfs_netdev.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/mac80211/debugfs_key.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/mac80211/mesh.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/mac80211/mesh_pathtbl.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/mac80211/mesh_plink.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/mac80211/mesh_hwmp.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/mac80211/rc80211_pid_algo.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/mac80211/rc80211_pid_debugfs.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/net/mac80211/mac80211.o
  LD      /home/manolo/compat-wireless-2.6-old/net/wireless/built-in.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/wireless/core.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/wireless/sysfs.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/wireless/radiotap.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/wireless/util.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/wireless/reg.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/wireless/compat.o
  CC [M]  /home/manolo/compat-wireless-2.6-old/net/wireless/nl80211.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/net/wireless/cfg80211.o
  LD      /home/manolo/compat-wireless-2.6-old/built-in.o
  Building modules, stage 2.
  MODPOST 44 modules
  CC      /home/manolo/compat-wireless-2.6-old/drivers/misc/eeprom_93cx6.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/misc/eeprom_93cx6.ko
  CC      /home/manolo/compat-wireless-2.6-old/drivers/net/b44.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/b44.ko
  CC      /home/manolo/compat-wireless-2.6-old/drivers/net/usb/cdc_ether.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/usb/cdc_ether.ko
  CC      /home/manolo/compat-wireless-2.6-old/drivers/net/usb/rndis_host.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/usb/rndis_host.ko
  CC      /home/manolo/compat-wireless-2.6-old/drivers/net/usb/usbnet.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/usb/usbnet.ko
  CC      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/adm8211.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/adm8211.ko
  CC      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/at76_usb.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/at76_usb.ko
  CC      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/ath5k/ath5k.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/ath5k/ath5k.ko
  CC      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/ath9k/ath9k.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/ath9k/ath9k.ko
  CC      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/b43/b43.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/b43/b43.ko
  CC      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/b43legacy.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/b43legacy.ko
  CC      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/ipw2100.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/ipw2100.ko
  CC      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/ipw2200.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/ipw2200.ko
  CC      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl3945.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl3945.ko
  CC      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl4965.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl4965.ko
  CC      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwlcore.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwlcore.ko
  CC      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas.ko
  CC      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_cs.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_cs.ko
  CC      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_sdio.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_sdio.ko
  CC      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/libertas/usb8xxx.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/libertas/usb8xxx.ko
  CC      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/mac80211_hwsim.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/mac80211_hwsim.ko
  CC      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/p54/p54common.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/p54/p54common.ko
  CC      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/p54/p54pci.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/p54/p54pci.ko
  CC      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/p54/p54usb.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/p54/p54usb.ko
  CC      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rndis_wlan.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rndis_wlan.ko
  CC      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2400pci.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2400pci.ko
  CC      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500pci.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500pci.ko
  CC      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500usb.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500usb.ko
  CC      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00lib.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00lib.ko
  CC      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00pci.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00pci.ko
  CC      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00usb.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00usb.ko
  CC      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt61pci.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt61pci.ko
  CC      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt73usb.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt73usb.ko
  CC      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rtl8180.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rtl8180.ko
  CC      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rtl8187.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rtl8187.ko
  CC      /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd1211rw.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd1211rw.ko
  CC      /home/manolo/compat-wireless-2.6-old/drivers/ssb/ssb.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/drivers/ssb/ssb.ko
  CC      /home/manolo/compat-wireless-2.6-old/net/ieee80211/ieee80211.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/net/ieee80211/ieee80211.ko
  CC      /home/manolo/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt.ko
  CC      /home/manolo/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_ccmp.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_ccmp.ko
  CC      /home/manolo/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_tkip.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_tkip.ko
  CC      /home/manolo/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_wep.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_wep.ko
  CC      /home/manolo/compat-wireless-2.6-old/net/mac80211/mac80211.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/net/mac80211/mac80211.ko
  CC      /home/manolo/compat-wireless-2.6-old/net/wireless/cfg80211.mod.o
  LD [M]  /home/manolo/compat-wireless-2.6-old/net/wireless/cfg80211.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'

manolo@manolo-laptop:~/compat-wireless-2.6-old$ **sudo make install**
Module ath5k not detected -- this is fine
Enabling ath_pci ...	[OK]	Module enabled: 
/lib/modules/2.6.24-19-generic/madwifi/ath_pci.ko
Disabling b43 ...	[OK]	Module disabled:
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/b43/b43.ko
Disabling b43legacy ...	[OK]	Module disabled:
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/b43legacy/b43legacy.ko
Enabling bcm43xx ...	[OK]	Module enabled: 
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko

Your old wireless subsystem modules were left intact:

/lib/modules/2.6.24-19-generic/kernel/net/mac80211/mac80211.ko
/lib/modules/2.6.24-19-generic/kernel/net/wireless/cfg80211.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/adm8211.ko
/lib/modules/2.6.24-19-generic/ubuntu/wireless/at76/at76_usb.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/ssb/ssb.ko
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl4965.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/ipw2100.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/ipw2200.ko
/lib/modules/2.6.24-19-generic/kernel/net/ieee80211/ieee80211.ko
/lib/modules/2.6.24-19-generic/kernel/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/libertas/libertas_cs.ko
/lib/modules/2.6.24-19-generic/kernel/net/mac80211/mac80211.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/p54pci.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/p54usb.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/rt2x00/rt2400pci.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/rt2x00/rt2500usb.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/rt2x00/rt61pci.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/usb/usbnet.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/usb/cdc_ether.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/usb/rndis_host.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/rtl8187.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko
/lib/modules/2.6.24-19-generic/kernel/net/ieee80211/softmac/ieee80211softmac.ko

make -C /lib/modules/2.6.24-19-generic/build M=/home/manolo/compat-wireless-2.6-old modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
/home/manolo/compat-wireless-2.6-old/config.mk:54: **"WARNING: You are running a kernel >= 2.6.23, you should enable in it CONFIG_NETDEVICES_MULTIQUEUE for 802.11[ne] support"**
  Building modules, stage 2.
  MODPOST 44 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make -C /lib/modules/2.6.24-19-generic/build M=/home/manolo/compat-wireless-2.6-old "INSTALL_MOD_DIR=updates"  \
		modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  INSTALL /home/manolo/compat-wireless-2.6-old/drivers/misc/eeprom_93cx6.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/drivers/net/b44.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/drivers/net/usb/cdc_ether.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/drivers/net/usb/rndis_host.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/drivers/net/usb/usbnet.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/adm8211.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/at76_usb.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/ath5k/ath5k.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/ath9k/ath9k.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/b43/b43.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/b43legacy.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/ipw2100.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/ipw2200.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl3945.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl4965.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwlcore.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_cs.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_sdio.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/libertas/usb8xxx.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/mac80211_hwsim.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/p54/p54common.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/p54/p54pci.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/p54/p54usb.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rndis_wlan.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2400pci.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500pci.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500usb.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00lib.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00pci.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00usb.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt61pci.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt73usb.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rtl8180.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/rtl8187.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd1211rw.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/drivers/ssb/ssb.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/net/ieee80211/ieee80211.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_ccmp.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_tkip.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_wep.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/net/mac80211/mac80211.ko
  INSTALL /home/manolo/compat-wireless-2.6-old/net/wireless/cfg80211.ko
  DEPMOD  2.6.24-19-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'

**Note: madwifi detected**, we're going to disable it. If you would like to enable it later you can run:
    sudo athenable madwifi

Running athenable ath5k...
Disabling ath_pci ...	[OK]	Module disabled:
/lib/modules/2.6.24-19-generic/madwifi/ath_pci.ko

Currently detected wireless subsystem modules:

/lib/modules/2.6.24-19-generic/updates/net/mac80211/mac80211.ko
/lib/modules/2.6.24-19-generic/updates/net/wireless/cfg80211.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/adm8211.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/at76_usb.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/ath5k/ath5k.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/ath9k/ath9k.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/b43/b43.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/b43legacy/b43legacy.ko
/lib/modules/2.6.24-19-generic/updates/drivers/ssb/ssb.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/iwlwifi/iwl3945.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/iwlwifi/iwl4965.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/ipw2100.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/ipw2200.ko
/lib/modules/2.6.24-19-generic/updates/net/ieee80211/ieee80211.ko
/lib/modules/2.6.24-19-generic/updates/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/libertas/libertas_cs.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/rt2x00/rt2400pci.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/rt2x00/rt2500pci.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/rt2x00/rt2500usb.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/rt2x00/rt61pci.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/rt2x00/rt73usb.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/usb/usbnet.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/usb/cdc_ether.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/usb/rndis_host.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/rndis_wlan.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/rtl8180.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/rtl8187.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/zd1211rw/zd1211rw.ko

Now run:

make unload

And then load the wireless module you need. If unsure run:

make load


manolo@manolo-laptop:~/compat-wireless-2.6-old$ **sudo make unload**
Unloading iwl3945...
manolo@manolo-laptop:~/compat-wireless-2.6-old$ **sudo make load**
Loading ipw2100...
Loading ipw2200...
Loading libertas_cs...
Loading usb8xxx...
Loading p54pci...
Loading p54usb...
Loading adm8211...
Loading zd1211rw...
Loading rtl8180...
Loading rtl8187...
Loading p54pci...
Loading p54usb...
Loading iwl3945...
Loading iwl4965...
Loading rtl8180...
Loading rtl8187...
Loading rtl8180...
Loading rtl8187...
Loading rt2400pci...
Loading rt2500pci...
Loading rt61pci...
Loading rt2500usb...
Loading rt73usb...
Loading rndis_wlan...
Loading at76_usb...
Module ath_pci not detected -- this is fine
ath5k loaded successfully
Disabling bcm43xx ...	[OK]	Module disabled:
/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko
Enabling b43 ...	[OK]	Module renamed but another module file is being preferred
Renamed module:		/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/b43/b43.ko
Preferred module:	/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/b43/b43.ko
Enabling b43legacy ...	[OK]	Module renamed but another module file is being preferred
Renamed module:		/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/b43legacy/b43legacy.ko
Preferred module:	/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/b43legacy/b43legacy.ko
b43 loaded successfully
b43legacy loaded successfully
manolo@manolo-laptop:~/compat-wireless-2.6-old$ 

Now I'm going to reboot. Stay tuned.:popcorn:

---

### Post by manolomanolo on 2008-09-11
I had some (silly?) troubles while installing (please see error message in **BOLD**). Unfortunately the result is always the same... even considering that while I was following your procedure Synaptic updated kWIFImanager.

That's the kWIFImanager screenshot
[http://img176.imageshack.us/my.php?image=screenshotjn3.png]("http://img176.imageshack.us/my.php?image=screenshotjn3.png")

Should I try back some commands between the ones you've been posting till now in order to post some dmesg ???

Thanks very much for your time!

---

### Post by pytheas22 on 2008-09-11
The warnings that you got while compiling the new driver (thanks for putting them in bold by the way) aren't serious; it looks like everything went smoothly.  So let's check the output now of:
```

sudo rmmod iwl3945
sudo modprobe iwl3945
dmesg
```

The output is going to be very long, but please just post it all.

---

### Post by manolomanolo on 2008-09-11
Please note that one of the "most serious" errors was on

manolo@manolo-laptop:~$ sudo cp iwlwifi-5000-ucode-5.4.A.11/iwlwifi-5000-1.ucode /lib/firmware
cp: cannot stat `iwlwifi-5000-ucode-5.4.A.11/iwlwifi-5000-1.ucode': No such file or directory

Maybe you wanted me to install a different version? Or was it just a copy/paste error by your side? :confused:

manolo@manolo-laptop:~$ **sudo rmmod iwl3945**
[sudo] password for manolo: 
manolo@manolo-laptop:~$ **sudo modprobe iwl3945**
manolo@manolo-laptop:~$ **dmesg**
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffc0000 (usable)
[    0.000000]  BIOS-e820: 000000003ffc0000 - 000000003ffce000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ffce000 - 0000000040000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 262080) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262080
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262080
[    0.000000] On node 0 totalpages: 262080
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32449 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7AF0 checksum 0
[    0.000000] ACPI: RSDP 000F7AF0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 3FFC0000, 003C (r1 A M I  OEMRSDT  11000617 MSFT       97)
[    0.000000] ACPI: FACP 3FFC0200, 0084 (r2 A M I  OEMFACP  11000617 MSFT       97)
[    0.000000] ACPI: DSDT 3FFC0460, 817C (r1  F3J00 F3J00001        1 INTL  2002026)
[    0.000000] ACPI: FACS 3FFCE000, 0040
[    0.000000] ACPI: APIC 3FFC0390, 005C (r1 A M I  OEMAPIC  11000617 MSFT       97)
[    0.000000] ACPI: MCFG 3FFC03F0, 003C (r1 A M I  OEMMCFG  11000617 MSFT       97)
[    0.000000] ACPI: BOOT 3FFC0430, 0028 (r1 A M I  OEMBOOT  11000617 MSFT       97)
[    0.000000] ACPI: OEMB 3FFCE040, 0046 (r1 A M I  AMI_OEM  11000617 MSFT       97)
[    0.000000] ACPI: TCPA 3FFC85E0, 0032 (r1 A M I  TBLOEMID        1 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:14 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:14 APIC version 20
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bee00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 260033
[    0.000000] Kernel command line: root=UUID=ec89a5ed-236a-490e-b920-43c84e5d00bb ro quiet splash vga=786
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1731.100 MHz processor.
[   19.108119] Console: colour dummy device 80x25
[   19.108123] console [tty0] enabled
[   19.108412] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   19.108785] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   19.136327] Memory: 1026808k/1048320k available (2177k kernel code, 20808k reserved, 1006k data, 368k init, 130816k highmem)
[   19.136335] virtual kernel memory layout:
[   19.136336]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   19.136338]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   19.136339]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   19.136340]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   19.136341]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   19.136343]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
[   19.136344]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
[   19.136347] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   19.136380] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   19.216337] Calibrating delay using timer specific routine.. 3466.42 BogoMIPS (lpj=6932845)
[   19.216360] Security Framework initialized
[   19.216366] SELinux:  Disabled at boot.
[   19.216379] AppArmor: AppArmor initialized
[   19.216383] Failure registering capabilities with primary security module.
[   19.216391] Mount-cache hash table entries: 512
[   19.216501] Initializing cgroup subsys ns
[   19.216507] Initializing cgroup subsys cpuacct
[   19.216517] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000 00000000
[   19.216524] monitor/mwait feature present.
[   19.216526] using mwait in idle threads.
[   19.216530] CPU: L1 I cache: 32K, L1 D cache: 32K
[   19.216532] CPU: L2 cache: 2048K
[   19.216535] CPU: Physical Processor ID: 0
[   19.216537] CPU: Processor Core ID: 0
[   19.216539] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000 00000000
[   19.216548] Compat vDSO mapped to ffffe000.
[   19.216560] Checking 'hlt' instruction... OK.
[   19.232713] SMP alternatives: switching to UP code
[   19.234476] Early unpacking initramfs... done
[   19.599665] ACPI: Core revision 20070126
[   19.599743] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   19.656727] CPU0: Intel Genuine Intel(R) CPU           T2250  @ 1.73GHz stepping 08
[   19.656745] SMP alternatives: switching to SMP code
[   19.657423] Booting processor 1/1 eip 3000
[   19.667656] Initializing CPU#1
[   19.747877] Calibrating delay using timer specific routine.. 3462.44 BogoMIPS (lpj=6924894)
[   19.747884] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000 00000000
[   19.747890] monitor/mwait feature present.
[   19.747893] CPU: L1 I cache: 32K, L1 D cache: 32K
[   19.747895] CPU: L2 cache: 2048K
[   19.747898] CPU: Physical Processor ID: 0
[   19.747899] CPU: Processor Core ID: 1
[   19.747901] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000 00000000
[   19.748417] CPU1: Intel Genuine Intel(R) CPU           T2250  @ 1.73GHz stepping 08
[   19.748440] Total of 2 processors activated (6928.86 BogoMIPS).
[   19.748639] ENABLING IO-APIC IRQs
[   19.748833] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   19.895881] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   19.915882] Brought up 2 CPUs
[   19.915909] CPU0 attaching sched-domain:
[   19.915912]  domain 0: span 03
[   19.915914]   groups: 01 02
[   19.915917] CPU1 attaching sched-domain:
[   19.915919]  domain 0: span 03
[   19.915920]   groups: 02 01
[   19.916174] net_namespace: 64 bytes
[   19.916184] Booting paravirtualized kernel on bare hardware
[   19.916654] Time:  1:31:24  Date: 09/12/08
[   19.916683] NET: Registered protocol family 16
[   19.916903] EISA bus registered
[   19.916908] ACPI: bus type pci registered
[   19.917177] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=6
[   19.917179] PCI: Using configuration type 1
[   19.917198] Setting up standard PCI resources
[   19.921251] ACPI: EC: Look up EC in DSDT
[   19.927958] APIC error on CPU1: 00(40)
[   20.000323] ACPI: Interpreter enabled
[   20.000327] ACPI: (supports S0 S1 S3 S4 S5)
[   20.000346] ACPI: Using IOAPIC for interrupt routing
[   20.008116] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[   20.008119] ACPI: EC: driver started in poll mode
[   20.008250] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   20.009039] Force enabled HPET at base address 0xfed00000
[   20.009045] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   20.009049] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   20.010487] PCI: Transparent bridge - 0000:00:1e.0
[   20.010537] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   20.010729] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   20.010836] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[   20.010951] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[   20.011060] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[   20.011173] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[   20.023679] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *11 12)
[   20.023834] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 12)
[   20.023984] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 12)
[   20.024135] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 *4 5 6 7 12)
[   20.024285] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 12) *0, disabled.
[   20.024437] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 12) *0, disabled.
[   20.024588] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 12) *0, disabled.
[   20.024740] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 12)
[   20.024887] ACPI Warning (tbutils-0217): Incorrect checksum in table [TCPA] -  00, should be 56 [20070126]
[   20.024893] Linux Plug and Play Support v0.97 (c) Adam Belay
[   20.024928] pnp: PnP ACPI init
[   20.024935] ACPI: bus type pnp registered
[   20.027113] pnp: PnP ACPI: found 12 devices
[   20.027116] ACPI: ACPI bus type pnp unregistered
[   20.027119] PnPBIOS: Disabled by ACPI PNP
[   20.027374] PCI: Using ACPI for IRQ routing
[   20.027377] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   20.071745] NET: Registered protocol family 8
[   20.071747] NET: Registered protocol family 20
[   20.071909] hpet clockevent registered
[   20.071915] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   20.071920] hpet0: 3 64-bit timers, 14318180 Hz
[   20.072954] AppArmor: AppArmor Filesystem Enabled
[   20.075610] Time: tsc clocksource has been installed.
[   20.091758] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[   20.091768] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   20.091771] system 00:08: ioport range 0x800-0x87f has been reserved
[   20.091774] system 00:08: ioport range 0x480-0x4bf has been reserved
[   20.091777] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   20.091780] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[   20.091783] system 00:08: iomem range 0xfed45000-0xfed89fff has been reserved
[   20.091787] system 00:08: iomem range 0xffb00000-0xffbfffff could not be reserved
[   20.091790] system 00:08: iomem range 0xfff00000-0xffffffff could not be reserved
[   20.091795] system 00:09: ioport range 0x250-0x253 has been reserved
[   20.091798] system 00:09: ioport range 0x256-0x25f has been reserved
[   20.091802] system 00:09: iomem range 0xfec00000-0xfec00fff has been reserved
[   20.091805] system 00:09: iomem range 0xfee00000-0xfee00fff could not be reserved
[   20.091808] system 00:09: iomem range 0xfec10000-0xfec17fff has been reserved
[   20.091811] system 00:09: iomem range 0xfec18000-0xfec1ffff has been reserved
[   20.091814] system 00:09: iomem range 0xfec20000-0xfec27fff has been reserved
[   20.091820] system 00:0a: iomem range 0xe0000000-0xe3ffffff has been reserved
[   20.091828] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[   20.091831] system 00:0b: iomem range 0xc0000-0xcffff could not be reserved
[   20.091834] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[   20.091837] system 00:0b: iomem range 0x100000-0x3fffffff could not be reserved
[   20.091840] system 00:0b: iomem range 0x0-0x0 could not be reserved
[   20.122271] PCI: Bridge: 0000:00:01.0
[   20.122274]   IO window: 9000-bfff
[   20.122278]   MEM window: fdf00000-fdffffff
[   20.122281]   PREFETCH window: bdf00000-ddefffff
[   20.122285] PCI: Bridge: 0000:00:1c.0
[   20.122288]   IO window: c000-cfff
[   20.122294]   MEM window: fe000000-fe0fffff
[   20.122298]   PREFETCH window: disabled.
[   20.122304] PCI: Bridge: 0000:00:1c.1
[   20.122306]   IO window: disabled.
[   20.122312]   MEM window: fe100000-fe1fffff
[   20.122316]   PREFETCH window: disabled.
[   20.122322] PCI: Bridge: 0000:00:1c.2
[   20.122325]   IO window: d000-dfff
[   20.122331]   MEM window: fe200000-fe9fffff
[   20.122336]   PREFETCH window: ddf00000-dfefffff
[   20.122342] PCI: Bridge: 0000:00:1e.0
[   20.122344]   IO window: disabled.
[   20.122350]   MEM window: fea00000-feafffff
[   20.122354]   PREFETCH window: disabled.
[   20.122373] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   20.122378] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   20.122401] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   20.122408] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   20.122432] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   20.122438] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   20.122462] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   20.122469] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   20.122483] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   20.122494] NET: Registered protocol family 2
[   20.159718] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   20.159945] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   20.160650] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   20.161001] TCP: Hash tables configured (established 131072 bind 65536)
[   20.161004] TCP reno registered
[   20.171797] checking if image is initramfs... it is
[   20.575180] Switched to high resolution mode on CPU 0
[   20.575297] Switched to high resolution mode on CPU 1
[   20.894902] Freeing initrd memory: 7636k freed
[   20.895070] Simple Boot Flag at 0x52 set to 0x1
[   20.895795] audit: initializing netlink socket (disabled)
[   20.895809] audit(1221183084.520:1): initialized
[   20.896018] highmem bounce pool size: 64 pages
[   20.898114] VFS: Disk quotas dquot_6.5.1
[   20.898190] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   20.898330] io scheduler noop registered
[   20.898333] io scheduler anticipatory registered
[   20.898335] io scheduler deadline registered
[   20.898346] io scheduler cfq registered (default)
[   20.898448] Boot video device is 0000:01:00.0
[   20.898565] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   20.898602] assign_interrupt_mode Found MSI capability
[   20.898634] Allocate Port Service[0000:00:01.0:pcie00]
[   20.898718] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   20.898777] assign_interrupt_mode Found MSI capability
[   20.898832] Allocate Port Service[0000:00:1c.0:pcie00]
[   20.898869] Allocate Port Service[0000:00:1c.0:pcie02]
[   20.898975] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   20.899033] assign_interrupt_mode Found MSI capability
[   20.899079] Allocate Port Service[0000:00:1c.1:pcie00]
[   20.899115] Allocate Port Service[0000:00:1c.1:pcie02]
[   20.899222] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   20.899280] assign_interrupt_mode Found MSI capability
[   20.899327] Allocate Port Service[0000:00:1c.2:pcie00]
[   20.899362] Allocate Port Service[0000:00:1c.2:pcie02]
[   20.899639] isapnp: Scanning for PnP cards...
[   21.254276] isapnp: No Plug & Play device found
[   21.283076] Real Time Clock Driver v1.12ac
[   21.283199] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   21.284477] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   21.284549] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   21.284652] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   21.286629] i8042.c: Detected active multiplexing controller, rev 1.1.
[   21.288619] serio: i8042 KBD port at 0x60,0x64 irq 1
[   21.288624] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   21.288627] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   21.288630] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   21.288632] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   21.307503] mice: PS/2 mouse device common for all mice
[   21.307625] EISA: Probing bus 0 at eisa.0
[   21.307663] EISA: Detected 0 cards.
[   21.307666] cpuidle: using governor ladder
[   21.307668] cpuidle: using governor menu
[   21.307755] NET: Registered protocol family 1
[   21.307782] Using IPI No-Shortcut mode
[   21.307812] registered taskstats version 1
[   21.307927]   Magic number: 8:499:508
[   21.308006]   hash matches device 0000:00:01.0
[   21.308017] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   21.308019] EDD information not available.
[   21.308229] Freeing unused kernel memory: 368k freed
[   21.340289] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   21.505942] vesafb: framebuffer at 0xc0000000, mapped to 0xf8880000, using 2400k, total 16384k
[   21.505946] vesafb: mode is 640x480x32, linelength=2560, pages=12
[   21.505949] vesafb: protected mode interface info at c000:ad52
[   21.505951] vesafb: pmi: set display start = c00cade0, set palette = c00caea2
[   21.505954] vesafb: scrolling: redraw
[   21.505956] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[   21.506066] Console: switching to colour frame buffer device 80x30
[   21.529346] fb0: VESA VGA frame buffer device
[   21.838813] usplash[1246]: segfault at b7b07000 eip b7eb2dd6 esp bfbd1f50 error 7
[   22.677626] fuse init (API version 7.9)
[   22.699487] ACPI: SSDT 3FFC8620, 049F (r1    AMI   CPU1PM        1 INTL  2002026)
[   22.700099] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   22.700104] ACPI: Processor [CPU1] (supports 8 throttling states)
[   22.700160] ACPI: SSDT 3FFC8AC0, 049F (r1    AMI   CPU2PM        1 INTL  2002026)
[   22.700738] ACPI: CPU1 (power states: C1[C1] C2[C2])
[   22.700743] ACPI: Processor [CPU2] (supports 8 throttling states)
[   22.701949] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   22.705536] ACPI: Thermal Zone [THRM] (60 C)
[   23.053816] usbcore: registered new interface driver usbfs
[   23.053840] usbcore: registered new interface driver hub
[   23.053876] usbcore: registered new device driver usb
[   23.055031] USB Universal Host Controller Interface driver v3.0
[   23.055084] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[   23.055096] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   23.055101] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   23.055338] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   23.055372] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000ec00
[   23.055509] usb usb1: configuration #1 chosen from 1 choice
[   23.055533] hub 1-0:1.0: USB hub found
[   23.055539] hub 1-0:1.0: 2 ports detected
[   23.115318] SCSI subsystem initialized
[   23.153694] libata version 3.00 loaded.
[   23.157760] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[   23.157774] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   23.157779] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   23.157805] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   23.157838] uhci_hcd 0000:00:1d.1: irq 20, io base 0x0000e880
[   23.157955] usb usb2: configuration #1 chosen from 1 choice
[   23.157979] hub 2-0:1.0: USB hub found
[   23.157985] hub 2-0:1.0: 2 ports detected
[   23.261662] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   23.261676] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   23.261681] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   23.261710] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   23.261746] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e800
[   23.261864] usb usb3: configuration #1 chosen from 1 choice
[   23.261888] hub 3-0:1.0: USB hub found
[   23.261893] hub 3-0:1.0: 2 ports detected
[   23.365584] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   23.365602] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   23.365607] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   23.365632] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   23.365666] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000e480
[   23.365782] usb usb4: configuration #1 chosen from 1 choice
[   23.365808] hub 4-0:1.0: USB hub found
[   23.365814] hub 4-0:1.0: 2 ports detected
[   23.469494] r8169 Gigabit Ethernet driver 2.2LK loaded
[   23.469526] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   23.469548] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   23.469895] eth0: RTL8168b/8111b at 0xf8844000, 00:17:31:fb:61:25, XID 38000000 IRQ 219
[   23.471049] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[   23.471060] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   23.471064] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   23.471092] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   23.475006] ehci_hcd 0000:00:1d.7: debug port 1
[   23.475014] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   23.475020] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfebfbc00
[   23.489386] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   23.489503] usb usb5: configuration #1 chosen from 1 choice
[   23.489527] hub 5-0:1.0: USB hub found
[   23.489533] hub 5-0:1.0: 8 ports detected
[   23.593453] ACPI: PCI Interrupt 0000:06:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   23.646320] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[feaff800-feafffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   23.664296] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[   23.664337] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   23.664350] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   23.667848] ata_piix 0000:00:1f.2: version 2.12
[   23.667854] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[   23.667874] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[   23.667903] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   23.667982] scsi0 : ata_piix
[   23.668032] scsi1 : ata_piix
[   23.669260] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   23.669263] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   23.832636] ata1.00: ATA-7: FUJITSU MHV2120BH PL, 00000029, max UDMA/100
[   23.832645] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   23.848637] ata1.00: configured for UDMA/100
[   24.172213] ata2.01: ATAPI: HL-DT-ST DVDRAM GMA-4082N, HJ02, max UDMA/33
[   24.339978] ata2.01: configured for UDMA/33
[   24.340124] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2120B 0000 PQ: 0 ANSI: 5
[   24.344188] scsi 1:0:1:0: CD-ROM            HL-DT-ST DVDRAM GMA-4082N HJ02 PQ: 0 ANSI: 5
[   24.350431] Driver 'sd' needs updating - please use bus_type methods
[   24.350498] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   24.350512] sd 0:0:0:0: [sda] Write Protect is off
[   24.350514] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.350532] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.350579] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   24.350590] sd 0:0:0:0: [sda] Write Protect is off
[   24.350593] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.350610] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.350613]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   24.432845]  sda1 sda2 < sda5 sda6 sda7 sda8 sda9 >
[   24.527336] sd 0:0:0:0: [sda] Attached SCSI disk
[   24.531843] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   24.531861] sr 1:0:1:0: Attached scsi generic sg1 type 5
[   24.547021] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   24.547026] Uniform CD-ROM driver Revision: 3.20
[   24.547074] sr 1:0:1:0: Attached scsi CD-ROM sr0
[   24.892196] Attempting manual resume
[   24.892200] swsusp: Resume From Partition 8:6
[   24.892202] PM: Checking swsusp image.
[   24.892520] PM: Resume from disk failed.
[   24.919300] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0180003627a2e]
[   31.024821] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   31.567315] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   31.608617] iTCO_vendor_support: vendor-support=0
[   31.772462] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   31.772564] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x0860)
[   31.772605] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   31.787028] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   31.924361] Linux agpgart interface v0.102
[   32.084924] input: Power Button (FF) as /devices/virtual/input/input3
[   32.149104] ACPI: Power Button (FF) [PWRF]
[   32.149203] input: Lid Switch as /devices/virtual/input/input4
[   32.166414] ACPI: Lid Switch [LID]
[   32.166477] input: Power Button (CM) as /devices/virtual/input/input5
[   32.213030] ACPI: Power Button (CM) [PWRB]
[   32.213094] input: Sleep Button (CM) as /devices/virtual/input/input6
[   32.269033] ACPI: Sleep Button (CM) [SLPB]
[   32.305491] asus-laptop: Asus Laptop Support version 0.42
[   32.305744] asus-laptop:   F3JA model detected
[   32.306821] Registered led device: asus:touchpad
[   32.575116] sdhci: Secure Digital Host Controller Interface driver
[   32.575121] sdhci: Copyright(c) Pierre Ossman
[   32.575168] sdhci: SDHCI controller found at 0000:06:01.1 [1180:0822] (rev 19)
[   32.575191] ACPI: PCI Interrupt 0000:06:01.1[B] -> GSI 17 (level, low) -> IRQ 17
[   32.575212] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   32.575265] mmc0: SDHCI at 0xfeaff400 irq 17 DMA
[   32.741665] ricoh-mmc: Ricoh MMC Controller disabling driver
[   32.741670] ricoh-mmc: Copyright(c) Philip Langdale
[   32.741719] ricoh-mmc: Ricoh MMC controller found at 0000:06:01.2 [1180:0843] (rev 1)
[   32.741732] ricoh-mmc: Controller is now disabled.
[   32.867628] ACPI: AC Adapter [AC0] (on-line)
[   33.537880] ACPI: Battery Slot [BAT0] (battery present)
[   33.538332] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:14/LNXVIDEO:00/input/input7
[   33.576128] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   33.598789] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   33.668408] [fglrx] Maximum main memory to use for locked dma buffers: 928 MBytes.
[   33.668449] [fglrx] ASYNCIO init succeed!
[   33.669521] [fglrx] PAT is enabled successfully!
[   33.669542] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   33.890445] sysfs: duplicate filename 'pcspkr' can not be created
[   33.890450] WARNING: at /build/buildd/linux-2.6.24/fs/sysfs/dir.c:424 sysfs_add_one()
[   33.890455] Pid: 2865, comm: modprobe Tainted: P        2.6.24-19-generic #1
[   33.890471]  [<c01d74df>] sysfs_add_one+0x9f/0xe0
[   33.890484]  [<c01d7a18>] create_dir+0x48/0x90
[   33.890490]  [<c01d7a89>] sysfs_create_dir+0x29/0x50
[   33.890494]  [<c02154cf>] kobject_get+0xf/0x20
[   33.890500]  [<c0215993>] kobject_add+0x93/0x1b0
[   33.890507]  [<c0215b41>] kobject_register+0x21/0x50
[   33.890511]  [<c0282041>] bus_add_driver+0x71/0x1e0
[   33.890520]  [<c01507c6>] sys_init_module+0x126/0x19c0
[   33.890540]  [<c013f260>] param_get_int+0x0/0x20
[   33.890549]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[   33.890558]  =======================
[   33.890562] kobject_add failed for pcspkr with -EEXIST, don't try to register things with the same name in the same directory.
[   33.890567] Pid: 2865, comm: modprobe Tainted: P        2.6.24-19-generic #1
[   33.890571]  [<c0215a13>] kobject_add+0x113/0x1b0
[   33.890578]  [<c0215b41>] kobject_register+0x21/0x50
[   33.890582]  [<c0282041>] bus_add_driver+0x71/0x1e0
[   33.890588]  [<c01507c6>] sys_init_module+0x126/0x19c0
[   33.890607]  [<c013f260>] param_get_int+0x0/0x20
[   33.890615]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[   33.890623]  =======================
[   34.043515] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   34.043537] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   34.100323] Synaptics Touchpad, model: 1, fw: 6.1, id: 0xa3a0b3, caps: 0xa04713/0x10008
[   34.141931] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   34.438610] lp: driver loaded but no devices found
[   34.574264] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   34.762005] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeBugCheck'
[   34.762237] ndiswrapper (load_sys_files:210): couldn't prepare driver 'netw5x32'
[   34.763049] ndiswrapper (load_wrap_driver:112): couldn't load driver netw5x32; check system log for messages from 'loadndisdriver'
[   34.764416] usbcore: registered new interface driver ndiswrapper
[   34.793768] Adding 2048248k swap on /dev/sda6.  Priority:-1 extents:1 across:2048248k
[   39.230530] ip_tables: (C) 2000-2006 Netfilter Core Team
[   40.710839] NET: Registered protocol family 17
[   41.284481] No dock devices found.
[   42.885658] apm: BIOS not found.
[   52.134332] r8169: eth0: link up
[   52.134349] r8169: eth0: link up
[   52.749099] NET: Registered protocol family 10
[   52.749567] lo: Disabled Privacy Extensions
[   52.826366] Bluetooth: Core ver 2.11
[   52.827019] NET: Registered protocol family 31
[   52.827028] Bluetooth: HCI device and connection manager initialized
[   52.827035] Bluetooth: HCI socket layer initialized
[   52.901111] Bluetooth: L2CAP ver 2.9
[   52.901120] Bluetooth: L2CAP socket layer initialized
[   53.248835] Bluetooth: RFCOMM socket layer initialized
[   53.248857] Bluetooth: RFCOMM TTY layer initialized
[   53.248862] Bluetooth: RFCOMM ver 1.8
[   53.567450] ppdev: user-space parallel port driver
[   54.154277] audit(1221175918.893:2): type=1502 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5545 profile="/usr/sbin/cupsd" namespace="default"
[   54.494837] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   56.895474] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26k
[   56.895482] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   56.895622] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   56.895641] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   56.895665] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   56.958333] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   56.960267] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   57.022373] [fglrx] Reserve Block - 0 offset =  0X1000000 length = 0X5000
[   57.022380] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
[   57.022383] [fglrx] Reserve Block - 2 offset =  0Xffff000 length = 0X1000
[   57.022386] [fglrx] Reserve Block - 3 offset =  0Xffbf000 length = 0X40000
[   57.183903] [fglrx] interrupt source 10000000 successfully enabled
[   57.183911] [fglrx] enable ID = 0x00000008
[   57.183921] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[   57.207758] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[   57.222352] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   57.222491] PM: Writing back config space on device 0000:03:00.0 at offset 1 (was 100002, writing 100006)
[   57.533527] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   66.939008] eth0: no IPv6 routers present
[   88.756512] CPU0 attaching NULL sched-domain.
[   88.756521] CPU1 attaching NULL sched-domain.
[   88.765131] CPU0 attaching sched-domain:
[   88.765139]  domain 0: span 03
[   88.765141]   groups: 01 02
[   88.765148] CPU1 attaching sched-domain:
[   88.765149]  domain 0: span 03
[   88.765151]   groups: 02 01
[ 1239.442247] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[ 1248.837522] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26k
[ 1248.837534] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[ 1248.837669] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[ 1248.837697] PCI: Setting latency timer of device 0000:03:00.0 to 64
[ 1248.837726] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[ 1248.879144] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[ 1248.880608] phy1: Selected rate control algorithm 'iwl-3945-rs'
[ 1248.906081] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[ 1248.969395] ADDRCONF(NETDEV_UP): **wlan0: link is not ready**
manolo@manolo-laptop:~$

---

### Post by pytheas22 on 2008-09-11
Sorry, yes, I did make a typo.  It still shouldn't really have mattered, however, because the file that you needed should already have been there (I was just going to have you copy it over again in case it would give you a later version, but I don't think it does).  But I've fixed the instructions in post #21 to reflect the correct ones; if you want, you can run all the stuff again.  But I doubt that it will make any difference.

I do have another idea to try.  You can disable apic, which according to [this thread]("http://ubuntuforums.org/showthread.php?t=707741&page=2") might solve the problem.  To do that, first open your grub menu:

sudo gedit /boot/grub/menu.lst

Look for a section that looks similar to this (there may be multiple sections; you can edit just the top one):
```

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b5725877-5158-4c5f-b858-e0f6eededc1e ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```

Change the "kernel" line so that it includes the "noapic" option, as below:
```

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b5725877-5158-4c5f-b858-e0f6eededc1e ro quiet splash **noapic**
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```

Then save and close the file.  Reboot, and make sure you choose at the grub menu to boot to the first kernel (the line at the top; should be default).  Does the wireless work any better?

---

### Post by manolomanolo on 2008-09-12
It Still doesn't work.

manolo@manolo-laptop:~$ **sudo lsmod**
[sudo] password for manolo: 
Module                  Size  Used by
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
iwl3945                89460  0 
mac80211              221300  1 iwl3945
cfg80211               35168  2 iwl3945,mac80211
binfmt_misc            12808  1 
ppdev                  10372  0 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ipv6                  267780  16 
acpi_cpufreq           10796  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  2 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8712  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
container               5632  0 
af_packet              23812  6 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ndiswrapper           192920  0 
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
snd_hda_intel         359192  1 
snd_pcm_oss            42528  0 
snd_mixer_oss          18048  1 snd_pcm_oss
snd_pcm                78852  2 snd_hda_intel,snd_pcm_oss
snd_hwdep              10628  1 snd_hda_intel
snd_seq_dummy           4996  0 
snd_seq_oss            35456  0 
snd_seq_midi            9504  0 
fglrx                1555468  23 
snd_rawmidi            25888  1 snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
snd_seq                54096  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
video                  19856  0 
output                  4736  1 video
asus_laptop            19064  0 
battery                14212  0 
ricoh_mmc               4352  0 
sdhci                  19076  0 
psmouse                40336  0 
ac                      6916  0 
snd_timer              24964  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mmc_core               51460  1 sdhci
serio_raw               7940  0 
led_class               6020  1 asus_laptop
intel_agp              25492  0 
snd                    57124  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         11656  2 snd_hda_intel,snd_pcm
button                  9232  0 
iTCO_wdt               13092  0 
agpgart                34760  2 fglrx,intel_agp
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
iTCO_vendor_support     4868  1 iTCO_wdt
evdev                  13056  7 
soundcore               8800  1 snd
pcspkr                  4224  0 
ext2                   73352  2 
mbcache                 9600  1 ext2
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  6 
ata_piix               19588  5 
pata_acpi               8320  0 
ata_generic             8324  0 
ohci1394               33584  0 
libata                159344  3 ata_piix,pata_acpi,ata_generic
ieee1394               93752  2 sbp2,ohci1394
r8169                  32900  0 
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  4 ndiswrapper,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fuse                   50708  7 
vesafb                  8964  1 
fbcon                  42912  72 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
manolo@manolo-laptop:~$ **sudo rmmod iwl3945**
manolo@manolo-laptop:~$ **sudo modprobe iwl3945**

Please note:
manolo@manolo-laptop:~$ dmesg | grep ndis
[   34.364747] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   34.552205] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeBugCheck'
[   34.552437] ndiswrapper (load_sys_files:210): couldn't prepare driver 'netw5x32'
[   34.553225] ndiswrapper (load_wrap_driver:112): couldn't load driver netw5x32; check system log for messages from 'loadndisdriver'
[   34.554591] usbcore: registered new interface driver ndiswrapper

I mean I'm supposet to use iwl3945, may that rest of ndiswrapper cause any conflict?

That's the whole dmesg
manolo@manolo-laptop:~$ **dmesg**
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffc0000 (usable)
[    0.000000]  BIOS-e820: 000000003ffc0000 - 000000003ffce000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ffce000 - 0000000040000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 262080) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262080
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262080
[    0.000000] On node 0 totalpages: 262080
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32449 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7AF0 checksum 0
[    0.000000] ACPI: RSDP 000F7AF0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 3FFC0000, 003C (r1 A M I  OEMRSDT  11000617 MSFT       97)
[    0.000000] ACPI: FACP 3FFC0200, 0084 (r2 A M I  OEMFACP  11000617 MSFT       97)
[    0.000000] ACPI: DSDT 3FFC0460, 817C (r1  F3J00 F3J00001        1 INTL  2002026)
[    0.000000] ACPI: FACS 3FFCE000, 0040
[    0.000000] ACPI: APIC 3FFC0390, 005C (r1 A M I  OEMAPIC  11000617 MSFT       97)
[    0.000000] ACPI: MCFG 3FFC03F0, 003C (r1 A M I  OEMMCFG  11000617 MSFT       97)
[    0.000000] ACPI: BOOT 3FFC0430, 0028 (r1 A M I  OEMBOOT  11000617 MSFT       97)
[    0.000000] ACPI: OEMB 3FFCE040, 0046 (r1 A M I  AMI_OEM  11000617 MSFT       97)
[    0.000000] ACPI: TCPA 3FFC85E0, 0032 (r1 A M I  TBLOEMID        1 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:14 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:14 APIC version 20
[    0.000000] ACPI: Skipping IOAPIC probe due to 'noapic' option.
[    0.000000] Using ACPI for processor (LAPIC) configuration information
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID: ASUSTeK  Product ID: NAPA         APIC at: 0xFEE00000
[    0.000000] I/O APIC #2 Version 32 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 2
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bee00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 260033
[    0.000000] Kernel command line: root=UUID=ec89a5ed-236a-490e-b920-43c84e5d00bb ro quiet splash noapic vga=786
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1731.137 MHz processor.
[   18.749067] Console: colour dummy device 80x25
[   18.749071] console [tty0] enabled
[   18.749360] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   18.749733] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   18.777247] Memory: 1026808k/1048320k available (2177k kernel code, 20808k reserved, 1006k data, 368k init, 130816k highmem)
[   18.777255] virtual kernel memory layout:
[   18.777256]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   18.777257]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   18.777259]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   18.777260]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   18.777261]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   18.777262]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
[   18.777264]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
[   18.777267] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   18.777300] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   18.857257] Calibrating delay using timer specific routine.. 3466.45 BogoMIPS (lpj=6932911)
[   18.857280] Security Framework initialized
[   18.857287] SELinux:  Disabled at boot.
[   18.857300] AppArmor: AppArmor initialized
[   18.857303] Failure registering capabilities with primary security module.
[   18.857311] Mount-cache hash table entries: 512
[   18.857423] Initializing cgroup subsys ns
[   18.857428] Initializing cgroup subsys cpuacct
[   18.857438] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000 00000000
[   18.857446] monitor/mwait feature present.
[   18.857447] using mwait in idle threads.
[   18.857451] CPU: L1 I cache: 32K, L1 D cache: 32K
[   18.857454] CPU: L2 cache: 2048K
[   18.857456] CPU: Physical Processor ID: 0
[   18.857458] CPU: Processor Core ID: 0
[   18.857460] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000 00000000
[   18.857469] Compat vDSO mapped to ffffe000.
[   18.857481] Checking 'hlt' instruction... OK.
[   18.873632] SMP alternatives: switching to UP code
[   18.875396] Early unpacking initramfs... done
[   19.239984] ACPI: Core revision 20070126
[   19.240063] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   19.243893] ACPI: setting ELCR to 0200 (from 08b8)
[   19.297183] CPU0: Intel Genuine Intel(R) CPU           T2250  @ 1.73GHz stepping 08
[   19.297200] SMP alternatives: switching to SMP code
[   19.297878] Booting processor 1/1 eip 3000
[   19.308111] Initializing CPU#1
[   19.384800] Calibrating delay using timer specific routine.. 3462.44 BogoMIPS (lpj=6924890)
[   19.384808] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000 00000000
[   19.384813] monitor/mwait feature present.
[   19.384817] CPU: L1 I cache: 32K, L1 D cache: 32K
[   19.384819] CPU: L2 cache: 2048K
[   19.384821] CPU: Physical Processor ID: 0
[   19.384822] CPU: Processor Core ID: 1
[   19.384824] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000 00000000
[   19.385382] CPU1: Intel Genuine Intel(R) CPU           T2250  @ 1.73GHz stepping 08
[   19.385405] Total of 2 processors activated (6928.90 BogoMIPS).
[   19.492847] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   19.512852] Brought up 2 CPUs
[   19.512871] CPU0 attaching sched-domain:
[   19.512874]  domain 0: span 03
[   19.512876]   groups: 01 02
[   19.512879] CPU1 attaching sched-domain:
[   19.512881]  domain 0: span 03
[   19.512883]   groups: 02 01
[   19.513142] net_namespace: 64 bytes
[   19.513153] Booting paravirtualized kernel on bare hardware
[   19.513623] Time: 10:37:33  Date: 09/12/08
[   19.513653] NET: Registered protocol family 16
[   19.513872] EISA bus registered
[   19.513877] ACPI: bus type pci registered
[   19.514148] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=6
[   19.514151] PCI: Using configuration type 1
[   19.514170] Setting up standard PCI resources
[   19.518225] ACPI: EC: Look up EC in DSDT
[   19.524621] APIC error on CPU1: 00(40)
[   19.597628] ACPI: Interpreter enabled
[   19.597632] ACPI: (supports S0 S1 S3 S4 S5)
[   19.597651] ACPI: Using PIC for interrupt routing
[   19.605427] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[   19.605430] ACPI: EC: driver started in poll mode
[   19.605563] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   19.606351] Force enabled HPET at base address 0xfed00000
[   19.606357] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   19.606361] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   19.607797] PCI: Transparent bridge - 0000:00:1e.0
[   19.607847] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   19.608120] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   19.608235] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[   19.608364] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[   19.608492] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[   19.608623] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[   19.621147] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *11 12)
[   19.621301] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 12)
[   19.621452] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 12)
[   19.621602] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 *4 5 6 7 12)
[   19.621753] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 12) *0, disabled.
[   19.621904] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 12) *0, disabled.
[   19.622055] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 12) *0, disabled.
[   19.622207] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 12)
[   19.622354] ACPI Warning (tbutils-0217): Incorrect checksum in table [TCPA] -  00, should be 56 [20070126]
[   19.622360] Linux Plug and Play Support v0.97 (c) Adam Belay
[   19.622394] pnp: PnP ACPI init
[   19.622401] ACPI: bus type pnp registered
[   19.624565] pnp: PnP ACPI: found 12 devices
[   19.624568] ACPI: ACPI bus type pnp unregistered
[   19.624571] PnPBIOS: Disabled by ACPI PNP
[   19.624878] PCI: Using ACPI for IRQ routing
[   19.624880] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   19.676574] NET: Registered protocol family 8
[   19.676576] NET: Registered protocol family 20
[   19.676738] hpet clockevent registered
[   19.676744] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   19.676749] hpet0: 3 64-bit timers, 14318180 Hz
[   19.677786] AppArmor: AppArmor Filesystem Enabled
[   19.680564] Time: tsc clocksource has been installed.
[   19.696591] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[   19.696601] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   19.696604] system 00:08: ioport range 0x800-0x87f has been reserved
[   19.696607] system 00:08: ioport range 0x480-0x4bf has been reserved
[   19.696611] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   19.696614] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[   19.696617] system 00:08: iomem range 0xfed45000-0xfed89fff has been reserved
[   19.696620] system 00:08: iomem range 0xffb00000-0xffbfffff could not be reserved
[   19.696623] system 00:08: iomem range 0xfff00000-0xffffffff could not be reserved
[   19.696629] system 00:09: ioport range 0x250-0x253 has been reserved
[   19.696632] system 00:09: ioport range 0x256-0x25f has been reserved
[   19.696635] system 00:09: iomem range 0xfec00000-0xfec00fff has been reserved
[   19.696638] system 00:09: iomem range 0xfee00000-0xfee00fff could not be reserved
[   19.696642] system 00:09: iomem range 0xfec10000-0xfec17fff has been reserved
[   19.696645] system 00:09: iomem range 0xfec18000-0xfec1ffff has been reserved
[   19.696648] system 00:09: iomem range 0xfec20000-0xfec27fff has been reserved
[   19.696653] system 00:0a: iomem range 0xe0000000-0xe3ffffff has been reserved
[   19.696660] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[   19.696663] system 00:0b: iomem range 0xc0000-0xcffff could not be reserved
[   19.696666] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[   19.696669] system 00:0b: iomem range 0x100000-0x3fffffff could not be reserved
[   19.696672] system 00:0b: iomem range 0x0-0x0 could not be reserved
[   19.727101] PCI: Bridge: 0000:00:01.0
[   19.727104]   IO window: 9000-bfff
[   19.727108]   MEM window: fdf00000-fdffffff
[   19.727111]   PREFETCH window: bdf00000-ddefffff
[   19.727115] PCI: Bridge: 0000:00:1c.0
[   19.727118]   IO window: c000-cfff
[   19.727124]   MEM window: fe000000-fe0fffff
[   19.727129]   PREFETCH window: disabled.
[   19.727135] PCI: Bridge: 0000:00:1c.1
[   19.727136]   IO window: disabled.
[   19.727142]   MEM window: fe100000-fe1fffff
[   19.727146]   PREFETCH window: disabled.
[   19.727152] PCI: Bridge: 0000:00:1c.2
[   19.727155]   IO window: d000-dfff
[   19.727161]   MEM window: fe200000-fe9fffff
[   19.727166]   PREFETCH window: ddf00000-dfefffff
[   19.727172] PCI: Bridge: 0000:00:1e.0
[   19.727174]   IO window: disabled.
[   19.727180]   MEM window: fea00000-feafffff
[   19.727184]   PREFETCH window: disabled.
[   19.727372] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   19.727375] PCI: setting IRQ 11 as level-triggered
[   19.727380] ACPI: PCI Interrupt 0000:00:01.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   19.727387] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   19.727411] ACPI: PCI Interrupt 0000:00:1c.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   19.727418] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   19.727603] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[   19.727605] PCI: setting IRQ 5 as level-triggered
[   19.727610] ACPI: PCI Interrupt 0000:00:1c.1[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   19.727617] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   19.727801] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 3
[   19.727804] PCI: setting IRQ 3 as level-triggered
[   19.727809] ACPI: PCI Interrupt 0000:00:1c.2[C] -> Link [LNKC] -> GSI 3 (level, low) -> IRQ 3
[   19.727816] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   19.727830] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   19.727842] NET: Registered protocol family 2
[   19.768546] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   19.768780] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   19.769485] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   19.769835] TCP: Hash tables configured (established 131072 bind 65536)
[   19.769838] TCP reno registered
[   19.780625] checking if image is initramfs... it is
[   20.176267] Switched to high resolution mode on CPU 1
[   20.180128] Switched to high resolution mode on CPU 0
[   20.503650] Freeing initrd memory: 7636k freed
[   20.503831] Simple Boot Flag at 0x52 set to 0x1
[   20.504551] audit: initializing netlink socket (disabled)
[   20.504565] audit(1221215853.488:1): initialized
[   20.504762] highmem bounce pool size: 64 pages
[   20.506847] VFS: Disk quotas dquot_6.5.1
[   20.506926] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   20.507058] io scheduler noop registered
[   20.507061] io scheduler anticipatory registered
[   20.507063] io scheduler deadline registered
[   20.507074] io scheduler cfq registered (default)
[   20.507179] Boot video device is 0000:01:00.0
[   20.507298] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   20.507335] assign_interrupt_mode Found MSI capability
[   20.507367] Allocate Port Service[0000:00:01.0:pcie00]
[   20.507451] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   20.507509] assign_interrupt_mode Found MSI capability
[   20.507556] Allocate Port Service[0000:00:1c.0:pcie00]
[   20.507591] Allocate Port Service[0000:00:1c.0:pcie02]
[   20.507696] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   20.507754] assign_interrupt_mode Found MSI capability
[   20.507810] Allocate Port Service[0000:00:1c.1:pcie00]
[   20.507847] Allocate Port Service[0000:00:1c.1:pcie02]
[   20.507951] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   20.508010] assign_interrupt_mode Found MSI capability
[   20.508056] Allocate Port Service[0000:00:1c.2:pcie00]
[   20.508097] Allocate Port Service[0000:00:1c.2:pcie02]
[   20.508375] isapnp: Scanning for PnP cards...
[   20.863011] isapnp: No Plug & Play device found
[   20.891527] Real Time Clock Driver v1.12ac
[   20.891648] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   20.892939] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   20.893012] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   20.893113] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   20.896890] i8042.c: Detected active multiplexing controller, rev 1.1.
[   20.898923] serio: i8042 KBD port at 0x60,0x64 irq 1
[   20.898928] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   20.898931] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   20.898934] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   20.898936] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   20.927473] mice: PS/2 mouse device common for all mice
[   20.927604] EISA: Probing bus 0 at eisa.0
[   20.927642] EISA: Detected 0 cards.
[   20.927645] cpuidle: using governor ladder
[   20.927647] cpuidle: using governor menu
[   20.927734] NET: Registered protocol family 1
[   20.927760] Using IPI No-Shortcut mode
[   20.927790] registered taskstats version 1
[   20.927903]   Magic number: 8:559:628
[   20.927988] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   20.927990] EDD information not available.
[   20.928200] Freeing unused kernel memory: 368k freed
[   20.962142] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   21.134990] vesafb: framebuffer at 0xc0000000, mapped to 0xf8880000, using 2400k, total 16384k
[   21.134995] vesafb: mode is 640x480x32, linelength=2560, pages=12
[   21.134997] vesafb: protected mode interface info at c000:ad52
[   21.135000] vesafb: pmi: set display start = c00cade0, set palette = c00caea2
[   21.135002] vesafb: scrolling: redraw
[   21.135004] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[   21.135115] Console: switching to colour frame buffer device 80x30
[   21.158398] fb0: VESA VGA frame buffer device
[   21.467798] usplash[1246]: segfault at b7b97000 eip b7f42dd6 esp bff1e290 error 7
[   22.306639] fuse init (API version 7.9)
[   22.328526] ACPI: SSDT 3FFC8620, 049F (r1    AMI   CPU1PM        1 INTL  2002026)
[   22.329139] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   22.329144] ACPI: Processor [CPU1] (supports 8 throttling states)
[   22.329199] ACPI: SSDT 3FFC8AC0, 049F (r1    AMI   CPU2PM        1 INTL  2002026)
[   22.329778] ACPI: CPU1 (power states: C1[C1] C2[C2])
[   22.329783] ACPI: Processor [CPU2] (supports 8 throttling states)
[   22.330996] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   22.334668] ACPI: Thermal Zone [THRM] (59 C)
[   22.694542] usbcore: registered new interface driver usbfs
[   22.694568] usbcore: registered new interface driver hub
[   22.694921] usbcore: registered new device driver usb
[   22.696452] USB Universal Host Controller Interface driver v3.0
[   22.696734] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 7
[   22.696737] PCI: setting IRQ 7 as level-triggered
[   22.696743] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKH] -> GSI 7 (level, low) -> IRQ 7
[   22.696756] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   22.696760] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   22.697023] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   22.697056] uhci_hcd 0000:00:1d.0: irq 7, io base 0x0000ec00
[   22.697204] usb usb1: configuration #1 chosen from 1 choice
[   22.697232] hub 1-0:1.0: USB hub found
[   22.697237] hub 1-0:1.0: 2 ports detected
[   22.801994] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 4
[   22.801999] PCI: setting IRQ 4 as level-triggered
[   22.802004] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 4 (level, low) -> IRQ 4
[   22.802017] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   22.802022] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   22.802049] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   22.802081] uhci_hcd 0000:00:1d.1: irq 4, io base 0x0000e880
[   22.802203] usb usb2: configuration #1 chosen from 1 choice
[   22.802227] hub 2-0:1.0: USB hub found
[   22.802233] hub 2-0:1.0: 2 ports detected
[   22.811532] SCSI subsystem initialized
[   22.846781] libata version 3.00 loaded.
[   22.905649] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 3 (level, low) -> IRQ 3
[   22.905664] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   22.905669] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   22.905694] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   22.905726] uhci_hcd 0000:00:1d.2: irq 3, io base 0x0000e800
[   22.905850] usb usb3: configuration #1 chosen from 1 choice
[   22.905875] hub 3-0:1.0: USB hub found
[   22.905880] hub 3-0:1.0: 2 ports detected
[   23.009560] ACPI: PCI Interrupt 0000:00:1d.3[D] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   23.009574] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   23.009579] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   23.009609] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   23.009642] uhci_hcd 0000:00:1d.3: irq 11, io base 0x0000e480
[   23.009761] usb usb4: configuration #1 chosen from 1 choice
[   23.009784] hub 4-0:1.0: USB hub found
[   23.009790] hub 4-0:1.0: 2 ports detected
[   23.113507] ACPI: PCI Interrupt 0000:00:1d.7[A] -> Link [LNKH] -> GSI 7 (level, low) -> IRQ 7
[   23.113523] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   23.113527] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   23.113553] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   23.117477] ehci_hcd 0000:00:1d.7: debug port 1
[   23.117483] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   23.117490] ehci_hcd 0000:00:1d.7: irq 7, io mem 0xfebfbc00
[   23.133378] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   23.133494] usb usb5: configuration #1 chosen from 1 choice
[   23.133520] hub 5-0:1.0: USB hub found
[   23.133526] hub 5-0:1.0: 8 ports detected
[   23.237364] r8169 Gigabit Ethernet driver 2.2LK loaded
[   23.237397] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   23.237419] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   23.237770] eth0: RTL8168b/8111b at 0xf887c000, 00:17:31:fb:61:25, XID 38000000 IRQ 219
[   23.239138] ACPI: PCI Interrupt 0000:06:01.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   23.291818] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[11]  MMIO=[feaff800-feafffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   23.296568] ACPI: PCI Interrupt 0000:00:1f.2[B] -> Link [LNKD] -> GSI 4 (level, low) -> IRQ 4
[   23.296610] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   23.296624] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   23.300315] ata_piix 0000:00:1f.2: version 2.12
[   23.300321] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[   23.300343] ACPI: PCI Interrupt 0000:00:1f.2[B] -> Link [LNKD] -> GSI 4 (level, low) -> IRQ 4
[   23.300379] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   23.300631] scsi0 : ata_piix
[   23.300702] scsi1 : ata_piix
[   23.301932] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   23.301935] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   23.465661] ata1.00: ATA-7: FUJITSU MHV2120BH PL, 00000029, max UDMA/100
[   23.465670] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   23.481664] ata1.00: configured for UDMA/100
[   23.801245] ata2.01: ATAPI: HL-DT-ST DVDRAM GMA-4082N, HJ02, max UDMA/33
[   23.973003] ata2.01: configured for UDMA/33
[   23.973152] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2120B 0000 PQ: 0 ANSI: 5
[   23.977234] scsi 1:0:1:0: CD-ROM            HL-DT-ST DVDRAM GMA-4082N HJ02 PQ: 0 ANSI: 5
[   23.983504] Driver 'sd' needs updating - please use bus_type methods
[   23.983575] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   23.983589] sd 0:0:0:0: [sda] Write Protect is off
[   23.983592] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   23.983609] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.983657] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   23.983667] sd 0:0:0:0: [sda] Write Protect is off
[   23.983670] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   23.983687] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.983691]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   24.067679]  sda1 sda2 < sda5 sda6 sda7 sda8 sda9 >
[   24.162171] sd 0:0:0:0: [sda] Attached SCSI disk
[   24.167009] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   24.167029] sr 1:0:1:0: Attached scsi generic sg1 type 5
[   24.181471] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   24.181475] Uniform CD-ROM driver Revision: 3.20
[   24.181522] sr 1:0:1:0: Attached scsi CD-ROM sr0
[   24.540855] Attempting manual resume
[   24.540859] swsusp: Resume From Partition 8:6
[   24.540861] PM: Checking swsusp image.
[   24.541192] PM: Resume from disk failed.
[   24.565833] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0180003627a2e]
[   31.251525] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   31.482676] iTCO_vendor_support: vendor-support=0
[   31.550564] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   31.634484] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   31.686822] Linux agpgart interface v0.102
[   31.734339] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   31.734440] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x0860)
[   31.734477] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   31.803540] input: Power Button (FF) as /devices/virtual/input/input3
[   31.857248] ACPI: Power Button (FF) [PWRF]
[   31.857362] input: Lid Switch as /devices/virtual/input/input4
[   31.892225] ACPI: Lid Switch [LID]
[   31.892458] input: Power Button (CM) as /devices/virtual/input/input5
[   31.945140] ACPI: Power Button (CM) [PWRB]
[   31.945204] input: Sleep Button (CM) as /devices/virtual/input/input6
[   31.993103] ACPI: Sleep Button (CM) [SLPB]
[   32.716706] ACPI: AC Adapter [AC0] (on-line)
[   32.816492] sdhci: Secure Digital Host Controller Interface driver
[   32.816497] sdhci: Copyright(c) Pierre Ossman
[   32.816537] sdhci: SDHCI controller found at 0000:06:01.1 [1180:0822] (rev 19)
[   32.816561] ACPI: PCI Interrupt 0000:06:01.1[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   32.816582] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   32.816630] mmc0: SDHCI at 0xfeaff400 irq 5 DMA
[   32.840296] ricoh-mmc: Ricoh MMC Controller disabling driver
[   32.840300] ricoh-mmc: Copyright(c) Philip Langdale
[   32.840337] ricoh-mmc: Ricoh MMC controller found at 0000:06:01.2 [1180:0843] (rev 1)
[   32.840349] ricoh-mmc: Controller is now disabled.
[   32.861994] asus-laptop: Asus Laptop Support version 0.42
[   32.862239] asus-laptop:   F3JA model detected
[   33.021613] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   33.064109] [fglrx] Maximum main memory to use for locked dma buffers: 928 MBytes.
[   33.064150] [fglrx] ASYNCIO init succeed!
[   33.065216] [fglrx] PAT is enabled successfully!
[   33.068595] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   33.101897] ACPI: Battery Slot [BAT0] (battery present)
[   33.102361] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:14/LNXVIDEO:00/input/input7
[   33.104074] Registered led device: asus:touchpad
[   33.149870] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   33.424905] sysfs: duplicate filename 'pcspkr' can not be created
[   33.424910] WARNING: at /build/buildd/linux-2.6.24/fs/sysfs/dir.c:424 sysfs_add_one()
[   33.424915] Pid: 2871, comm: modprobe Tainted: P        2.6.24-19-generic #1
[   33.424931]  [<c01d74df>] sysfs_add_one+0x9f/0xe0
[   33.424944]  [<c01d7a18>] create_dir+0x48/0x90
[   33.424951]  [<c01d7a89>] sysfs_create_dir+0x29/0x50
[   33.424955]  [<c02154cf>] kobject_get+0xf/0x20
[   33.424960]  [<c0215993>] kobject_add+0x93/0x1b0
[   33.424967]  [<c0215b41>] kobject_register+0x21/0x50
[   33.424971]  [<c0282041>] bus_add_driver+0x71/0x1e0
[   33.424981]  [<c01507c6>] sys_init_module+0x126/0x19c0
[   33.425002]  [<c013f260>] param_get_int+0x0/0x20
[   33.425011]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[   33.425021]  =======================
[   33.425025] kobject_add failed for pcspkr with -EEXIST, don't try to register things with the same name in the same directory.
[   33.425031] Pid: 2871, comm: modprobe Tainted: P        2.6.24-19-generic #1
[   33.425034]  [<c0215a13>] kobject_add+0x113/0x1b0
[   33.425041]  [<c0215b41>] kobject_register+0x21/0x50
[   33.425046]  [<c0282041>] bus_add_driver+0x71/0x1e0
[   33.425053]  [<c01507c6>] sys_init_module+0x126/0x19c0
[   33.425072]  [<c013f260>] param_get_int+0x0/0x20
[   33.425080]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[   33.425089]  =======================
[   33.511222] ACPI: PCI Interrupt 0000:00:1b.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   33.511247] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   33.664510] Synaptics Touchpad, model: 1, fw: 6.1, id: 0xa3a0b3, caps: 0xa04713/0x10008
[   33.706046] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   34.251111] lp: driver loaded but no devices found
[   34.364747] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   34.552205] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeBugCheck'
[   34.552437] ndiswrapper (load_sys_files:210): couldn't prepare driver 'netw5x32'
[   34.553225] ndiswrapper (load_wrap_driver:112): couldn't load driver netw5x32; check system log for messages from 'loadndisdriver'
[   34.554591] usbcore: registered new interface driver ndiswrapper
[   34.584049] Adding 2048248k swap on /dev/sda6.  Priority:-1 extents:1 across:2048248k
[   39.076056] ip_tables: (C) 2000-2006 Netfilter Core Team
[   40.567830] NET: Registered protocol family 17
[   41.174669] No dock devices found.
[   42.731394] apm: BIOS not found.
[   52.045105] r8169: eth0: link up
[   52.045116] r8169: eth0: link up
[   52.735266] NET: Registered protocol family 10
[   52.735717] lo: Disabled Privacy Extensions
[   52.759629] Bluetooth: Core ver 2.11
[   52.760056] NET: Registered protocol family 31
[   52.760063] Bluetooth: HCI device and connection manager initialized
[   52.760071] Bluetooth: HCI socket layer initialized
[   53.060729] Bluetooth: L2CAP ver 2.9
[   53.060740] Bluetooth: L2CAP socket layer initialized
[   53.344015] Bluetooth: RFCOMM socket layer initialized
[   53.344037] Bluetooth: RFCOMM TTY layer initialized
[   53.344041] Bluetooth: RFCOMM ver 1.8
[   53.644379] ppdev: user-space parallel port driver
[   54.398256] audit(1221208688.325:2): type=1502 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5538 profile="/usr/sbin/cupsd" namespace="default"
[   54.439938] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   56.970566] [fglrx] Reserve Block - 0 offset =  0X1000000 length = 0X5000
[   56.970580] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
[   56.970586] [fglrx] Reserve Block - 2 offset =  0Xffff000 length = 0X1000
[   56.970595] [fglrx] Reserve Block - 3 offset =  0Xffbf000 length = 0X40000
[   57.099791] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26k
[   57.099803] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   57.099983] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   57.100006] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   57.100038] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   57.129864] [fglrx] interrupt source 10000000 successfully enabled
[   57.129877] [fglrx] enable ID = 0x00000008
[   57.130430] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[   57.163228] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   57.164179] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   57.485476] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[   57.503126] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   57.503277] PM: Writing back config space on device 0000:03:00.0 at offset 1 (was 100002, writing 100006)
[   57.817673] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   69.305599] eth0: no IPv6 routers present
[   90.001091] CPU0 attaching NULL sched-domain.
[   90.001099] CPU1 attaching NULL sched-domain.
[   90.023933] CPU0 attaching sched-domain:
[   90.023940]  domain 0: span 03
[   90.023942]   groups: 01 02
[   90.023945] CPU1 attaching sched-domain:
[   90.023947]  domain 0: span 03
[   90.023949]   groups: 02 01
[  218.016585] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[  230.593639] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26k
[  230.593646] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[  230.594043] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[  230.594066] PCI: Setting latency timer of device 0000:03:00.0 to 64
[  230.594097] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[  230.637080] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[  230.639175] phy1: Selected rate control algorithm 'iwl-3945-rs'
[  230.651627] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[  230.718632] ADDRCONF(NETDEV_UP): wlan0: link is not ready
manolo@manolo-laptop:~$ 

Thanks for your help!!!

---

### Post by pytheas22 on 2008-09-12
ndiswrapper shouldn't cause problems, because iwl3945 should take precedence over it.  But you can get rid of ndiswrapper (since we know it doesn't work anyway) with:
```

echo 'blacklist ndiswrapper' | sudo tee -a /etc/modprobe.d/blacklist
sudo apt-get remove --purge ndiswrapper
```

Then reboot, and try turning the wireless card on a few times and scanning with "iwlist scan."

---

### Post by manolomanolo on 2008-09-12
manolo@manolo-laptop:~$ echo 'blacklist ndiswrapper' | sudo tee -a /etc/modprobe.d/blacklist
[sudo] password for manolo: 
blacklist ndiswrapper
manolo@manolo-laptop:~$ sudo apt-get remove --purge ndiswrapper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**E: Couldn't find package ndiswrapper**

Strange, I found ndiswrapper packages through Synaptic... I "completely remove"'d them.


Reboting, I'll be back in a while.

---

### Post by manolomanolo on 2008-09-13
Still no wireless connection.
I realized a "strange" thing. My laptop's led associated to my wifi card turns on after a little while starting Ubuntu through GRUB. But then, almost at the end of the OS complete loading it turns off.

I think there's something "disturbing" some wireless module or even unloading it...

This is the last dmesg

manolo@manolo-laptop:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffc0000 (usable)
[    0.000000]  BIOS-e820: 000000003ffc0000 - 000000003ffce000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ffce000 - 0000000040000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 262080) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262080
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262080
[    0.000000] On node 0 totalpages: 262080
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32449 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7AF0 checksum 0
[    0.000000] ACPI: RSDP 000F7AF0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 3FFC0000, 003C (r1 A M I  OEMRSDT  11000617 MSFT       97)
[    0.000000] ACPI: FACP 3FFC0200, 0084 (r2 A M I  OEMFACP  11000617 MSFT       97)
[    0.000000] ACPI: DSDT 3FFC0460, 817C (r1  F3J00 F3J00001        1 INTL  2002026)
[    0.000000] ACPI: FACS 3FFCE000, 0040
[    0.000000] ACPI: APIC 3FFC0390, 005C (r1 A M I  OEMAPIC  11000617 MSFT       97)
[    0.000000] ACPI: MCFG 3FFC03F0, 003C (r1 A M I  OEMMCFG  11000617 MSFT       97)
[    0.000000] ACPI: BOOT 3FFC0430, 0028 (r1 A M I  OEMBOOT  11000617 MSFT       97)
[    0.000000] ACPI: OEMB 3FFCE040, 0046 (r1 A M I  AMI_OEM  11000617 MSFT       97)
[    0.000000] ACPI: TCPA 3FFC85E0, 0032 (r1 A M I  TBLOEMID        1 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:14 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:14 APIC version 20
[    0.000000] ACPI: Skipping IOAPIC probe due to 'noapic' option.
[    0.000000] Using ACPI for processor (LAPIC) configuration information
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID: ASUSTeK  Product ID: NAPA         APIC at: 0xFEE00000
[    0.000000] I/O APIC #2 Version 32 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 2
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bee00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 260033
[    0.000000] Kernel command line: root=UUID=ec89a5ed-236a-490e-b920-43c84e5d00bb ro quiet splash noapic vga=786
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1729.134 MHz processor.
[   11.998714] Console: colour dummy device 80x25
[   11.998721] console [tty0] enabled
[   11.999049] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   11.999708] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   12.053393] Memory: 1026808k/1048320k available (2177k kernel code, 20808k reserved, 1006k data, 368k init, 130816k highmem)
[   12.053409] virtual kernel memory layout:
[   12.053411]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   12.053414]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   12.053417]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   12.053420]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   12.053422]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   12.053425]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
[   12.053428]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
[   12.053435] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   12.053493] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   12.133497] Calibrating delay using timer specific routine.. 3463.39 BogoMIPS (lpj=6926785)
[   12.133538] Security Framework initialized
[   12.133548] SELinux:  Disabled at boot.
[   12.133572] AppArmor: AppArmor initialized
[   12.133580] Failure registering capabilities with primary security module.
[   12.133595] Mount-cache hash table entries: 512
[   12.133796] Initializing cgroup subsys ns
[   12.133804] Initializing cgroup subsys cpuacct
[   12.133822] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000 00000000
[   12.133838] monitor/mwait feature present.
[   12.133842] using mwait in idle threads.
[   12.133849] CPU: L1 I cache: 32K, L1 D cache: 32K
[   12.133855] CPU: L2 cache: 2048K
[   12.133859] CPU: Physical Processor ID: 0
[   12.133863] CPU: Processor Core ID: 0
[   12.133867] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000 00000000
[   12.133885] Compat vDSO mapped to ffffe000.
[   12.133908] Checking 'hlt' instruction... OK.
[   12.150225] SMP alternatives: switching to UP code
[   12.153730] Early unpacking initramfs... done
[   12.939872] ACPI: Core revision 20070126
[   12.940024] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   12.948310] ACPI: setting ELCR to 0200 (from 08b8)
[   13.005394] CPU0: Intel Genuine Intel(R) CPU           T2250  @ 1.73GHz stepping 08
[   13.005425] SMP alternatives: switching to SMP code
[   13.006665] Booting processor 1/1 eip 3000
[   13.017170] Initializing CPU#1
[   13.097141] Calibrating delay using timer specific routine.. 3458.40 BogoMIPS (lpj=6916814)
[   13.097154] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000 00000000
[   13.097166] monitor/mwait feature present.
[   13.097172] CPU: L1 I cache: 32K, L1 D cache: 32K
[   13.097176] CPU: L2 cache: 2048K
[   13.097180] CPU: Physical Processor ID: 0
[   13.097183] CPU: Processor Core ID: 1
[   13.097186] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000 00000000
[   13.098190] CPU1: Intel Genuine Intel(R) CPU           T2250  @ 1.73GHz stepping 08
[   13.098231] Total of 2 processors activated (6921.79 BogoMIPS).
[   13.205321] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   13.225346] Brought up 2 CPUs
[   13.225380] CPU0 attaching sched-domain:
[   13.225386]  domain 0: span 03
[   13.225390]   groups: 01 02
[   13.225397] CPU1 attaching sched-domain:
[   13.225401]  domain 0: span 03
[   13.225405]   groups: 02 01
[   13.225875] net_namespace: 64 bytes
[   13.225896] Booting paravirtualized kernel on bare hardware
[   13.226835] Time:  1:02:38  Date: 09/14/08
[   13.226889] NET: Registered protocol family 16
[   13.227306] EISA bus registered
[   13.227315] ACPI: bus type pci registered
[   13.227718] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=6
[   13.227723] PCI: Using configuration type 1
[   13.227764] Setting up standard PCI resources
[   13.236099] ACPI: EC: Look up EC in DSDT
[   13.247847] APIC error on CPU1: 00(40)
[   13.324052] ACPI: Interpreter enabled
[   13.324059] ACPI: (supports S0 S1 S3 S4 S5)
[   13.324100] ACPI: Using PIC for interrupt routing
[   13.340601] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[   13.340606] ACPI: EC: driver started in poll mode
[   13.340890] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   13.341964] Force enabled HPET at base address 0xfed00000
[   13.341974] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   13.341982] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   13.344726] PCI: Transparent bridge - 0000:00:1e.0
[   13.344799] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   13.345394] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   13.345647] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[   13.345927] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[   13.346204] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[   13.346487] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[   13.373538] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *11 12)
[   13.373866] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 12)
[   13.374188] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 12)
[   13.374510] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 *4 5 6 7 12)
[   13.374831] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 12) *0, disabled.
[   13.375155] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 12) *0, disabled.
[   13.375478] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 12) *0, disabled.
[   13.375802] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 12)
[   13.376107] ACPI Warning (tbutils-0217): Incorrect checksum in table [TCPA] -  00, should be 56 [20070126]
[   13.376121] Linux Plug and Play Support v0.97 (c) Adam Belay
[   13.376186] pnp: PnP ACPI init
[   13.376201] ACPI: bus type pnp registered
[   13.380789] pnp: PnP ACPI: found 12 devices
[   13.380794] ACPI: ACPI bus type pnp unregistered
[   13.380802] PnPBIOS: Disabled by ACPI PNP
[   13.381289] PCI: Using ACPI for IRQ routing
[   13.381294] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   13.429267] NET: Registered protocol family 8
[   13.429272] NET: Registered protocol family 20
[   13.429468] hpet clockevent registered
[   13.429478] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   13.429488] hpet0: 3 64-bit timers, 14318180 Hz
[   13.430552] AppArmor: AppArmor Filesystem Enabled
[   13.433038] Time: tsc clocksource has been installed.
[   13.445326] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[   13.445348] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   13.445354] system 00:08: ioport range 0x800-0x87f has been reserved
[   13.445361] system 00:08: ioport range 0x480-0x4bf has been reserved
[   13.445368] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   13.445374] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[   13.445381] system 00:08: iomem range 0xfed45000-0xfed89fff has been reserved
[   13.445388] system 00:08: iomem range 0xffb00000-0xffbfffff could not be reserved
[   13.445395] system 00:08: iomem range 0xfff00000-0xffffffff could not be reserved
[   13.445407] system 00:09: ioport range 0x250-0x253 has been reserved
[   13.445414] system 00:09: ioport range 0x256-0x25f has been reserved
[   13.445421] system 00:09: iomem range 0xfec00000-0xfec00fff has been reserved
[   13.445428] system 00:09: iomem range 0xfee00000-0xfee00fff could not be reserved
[   13.445434] system 00:09: iomem range 0xfec10000-0xfec17fff has been reserved
[   13.445441] system 00:09: iomem range 0xfec18000-0xfec1ffff has been reserved
[   13.445448] system 00:09: iomem range 0xfec20000-0xfec27fff has been reserved
[   13.445460] system 00:0a: iomem range 0xe0000000-0xe3ffffff has been reserved
[   13.445473] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[   13.445480] system 00:0b: iomem range 0xc0000-0xcffff could not be reserved
[   13.445487] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[   13.445493] system 00:0b: iomem range 0x100000-0x3fffffff could not be reserved
[   13.445500] system 00:0b: iomem range 0x0-0x0 could not be reserved
[   13.476367] PCI: Bridge: 0000:00:01.0
[   13.476373]   IO window: 9000-bfff
[   13.476380]   MEM window: fdf00000-fdffffff
[   13.476387]   PREFETCH window: bdf00000-ddefffff
[   13.476394] PCI: Bridge: 0000:00:1c.0
[   13.476399]   IO window: c000-cfff
[   13.476409]   MEM window: fe000000-fe0fffff
[   13.476416]   PREFETCH window: disabled.
[   13.476425] PCI: Bridge: 0000:00:1c.1
[   13.476428]   IO window: disabled.
[   13.476437]   MEM window: fe100000-fe1fffff
[   13.476444]   PREFETCH window: disabled.
[   13.476453] PCI: Bridge: 0000:00:1c.2
[   13.476458]   IO window: d000-dfff
[   13.476467]   MEM window: fe200000-fe9fffff
[   13.476475]   PREFETCH window: ddf00000-dfefffff
[   13.476485] PCI: Bridge: 0000:00:1e.0
[   13.476489]   IO window: disabled.
[   13.476497]   MEM window: fea00000-feafffff
[   13.476504]   PREFETCH window: disabled.
[   13.476894] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   13.476900] PCI: setting IRQ 11 as level-triggered
[   13.476908] ACPI: PCI Interrupt 0000:00:01.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   13.476920] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   13.476955] ACPI: PCI Interrupt 0000:00:1c.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   13.476967] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   13.477353] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[   13.477359] PCI: setting IRQ 5 as level-triggered
[   13.477366] ACPI: PCI Interrupt 0000:00:1c.1[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   13.477379] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   13.477756] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 3
[   13.477761] PCI: setting IRQ 3 as level-triggered
[   13.477768] ACPI: PCI Interrupt 0000:00:1c.2[C] -> Link [LNKC] -> GSI 3 (level, low) -> IRQ 3
[   13.477781] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   13.477802] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   13.477824] NET: Registered protocol family 2
[   13.517332] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   13.517786] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   13.519283] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   13.520030] TCP: Hash tables configured (established 131072 bind 65536)
[   13.520035] TCP reno registered
[   13.529486] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[   13.933064] Switched to high resolution mode on CPU 1
[   14.289316]  it is
[   15.089590] Freeing initrd memory: 7636k freed
[   15.089826] Simple Boot Flag at 0x52 set to 0x1
[   15.091166] audit: initializing netlink socket (disabled)
[   15.091186] audit(1221354159.788:1): initialized
[   15.091524] highmem bounce pool size: 64 pages
[   15.095737] VFS: Disk quotas dquot_6.5.1
[   15.095898] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   15.096163] io scheduler noop registered
[   15.096168] io scheduler anticipatory registered
[   15.096172] io scheduler deadline registered
[   15.096196] io scheduler cfq registered (default)
[   15.096330] Boot video device is 0000:01:00.0
[   15.096554] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   15.096617] assign_interrupt_mode Found MSI capability
[   15.096669] Allocate Port Service[0000:00:01.0:pcie00]
[   15.096819] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   15.096896] assign_interrupt_mode Found MSI capability
[   15.096959] Allocate Port Service[0000:00:1c.0:pcie00]
[   15.097033] Allocate Port Service[0000:00:1c.0:pcie02]
[   15.097198] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   15.097275] assign_interrupt_mode Found MSI capability
[   15.097338] Allocate Port Service[0000:00:1c.1:pcie00]
[   15.097408] Allocate Port Service[0000:00:1c.1:pcie02]
[   15.097572] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   15.097649] assign_interrupt_mode Found MSI capability
[   15.097711] Allocate Port Service[0000:00:1c.2:pcie00]
[   15.097782] Allocate Port Service[0000:00:1c.2:pcie02]
[   15.098274] isapnp: Scanning for PnP cards...
[   15.453716] isapnp: No Plug & Play device found
[   15.511703] Real Time Clock Driver v1.12ac
[   15.511916] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   15.514425] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   15.514563] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   15.514762] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   15.517278] i8042.c: Detected active multiplexing controller, rev 1.1.
[   15.518767] serio: i8042 KBD port at 0x60,0x64 irq 1
[   15.518777] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   15.518783] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   15.518789] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   15.518794] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   15.528536] mice: PS/2 mouse device common for all mice
[   15.528770] EISA: Probing bus 0 at eisa.0
[   15.528824] EISA: Detected 0 cards.
[   15.528830] cpuidle: using governor ladder
[   15.528834] cpuidle: using governor menu
[   15.528994] NET: Registered protocol family 1
[   15.529040] Using IPI No-Shortcut mode
[   15.529092] registered taskstats version 1
[   15.529306]   Magic number: 8:134:3
[   15.529319]   hash matches device ttybe
[   15.529431] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   15.529435] EDD information not available.
[   15.529710] Freeing unused kernel memory: 368k freed
[   15.561295] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   15.745368] vesafb: framebuffer at 0xc0000000, mapped to 0xf8880000, using 2400k, total 16384k
[   15.745377] vesafb: mode is 640x480x32, linelength=2560, pages=12
[   15.745382] vesafb: protected mode interface info at c000:ad52
[   15.745387] vesafb: pmi: set display start = c00cade0, set palette = c00caea2
[   15.745392] vesafb: scrolling: redraw
[   15.745398] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[   15.745607] Console: switching to colour frame buffer device 80x30
[   15.776043] fb0: VESA VGA frame buffer device
[   16.278757] usplash[1246]: segfault at b7bae000 eip b7f59dd6 esp bfab4630 error 7
[   17.076273] fuse init (API version 7.9)
[   17.123117] ACPI: SSDT 3FFC8620, 049F (r1    AMI   CPU1PM        1 INTL  2002026)
[   17.124583] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[   17.124596] ACPI: Processor [CPU1] (supports 8 throttling states)
[   17.124712] ACPI: SSDT 3FFC8AC0, 049F (r1    AMI   CPU2PM        1 INTL  2002026)
[   17.126150] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[   17.126162] ACPI: Processor [CPU2] (supports 8 throttling states)
[   17.128597] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   17.133151] ACPI: Thermal Zone [THRM] (39 C)
[   17.864340] r8169 Gigabit Ethernet driver 2.2LK loaded
[   17.864383] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   17.864414] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   17.864996] eth0: RTL8168b/8111b at 0xf885c000, 00:17:31:fb:61:25, XID 38000000 IRQ 219
[   17.899260] usbcore: registered new interface driver usbfs
[   17.899303] usbcore: registered new interface driver hub
[   17.899357] usbcore: registered new device driver usb
[   17.901773] USB Universal Host Controller Interface driver v3.0
[   17.902274] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 7
[   17.902280] PCI: setting IRQ 7 as level-triggered
[   17.902288] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKH] -> GSI 7 (level, low) -> IRQ 7
[   17.902307] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   17.902315] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   17.902641] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   17.902682] uhci_hcd 0000:00:1d.0: irq 7, io base 0x0000ec00
[   17.902934] usb usb1: configuration #1 chosen from 1 choice
[   17.902983] hub 1-0:1.0: USB hub found
[   17.902994] hub 1-0:1.0: 2 ports detected
[   18.004760] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 4
[   18.004768] PCI: setting IRQ 4 as level-triggered
[   18.004776] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 4 (level, low) -> IRQ 4
[   18.004797] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   18.004805] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   18.004855] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   18.004895] uhci_hcd 0000:00:1d.1: irq 4, io base 0x0000e880
[   18.005124] usb usb2: configuration #1 chosen from 1 choice
[   18.005173] hub 2-0:1.0: USB hub found
[   18.005184] hub 2-0:1.0: 2 ports detected
[   18.044760] SCSI subsystem initialized
[   18.108294] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 3 (level, low) -> IRQ 3
[   18.108317] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   18.108325] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   18.108371] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   18.108412] uhci_hcd 0000:00:1d.2: irq 3, io base 0x0000e800
[   18.108636] usb usb3: configuration #1 chosen from 1 choice
[   18.108686] hub 3-0:1.0: USB hub found
[   18.108697] hub 3-0:1.0: 2 ports detected
[   18.124150] libata version 3.00 loaded.
[   18.212258] ACPI: PCI Interrupt 0000:00:1d.3[D] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   18.212280] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   18.212288] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   18.212339] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   18.212380] uhci_hcd 0000:00:1d.3: irq 11, io base 0x0000e480
[   18.212609] usb usb4: configuration #1 chosen from 1 choice
[   18.212658] hub 4-0:1.0: USB hub found
[   18.212670] hub 4-0:1.0: 2 ports detected
[   18.316270] ACPI: PCI Interrupt 0000:00:1d.7[A] -> Link [LNKH] -> GSI 7 (level, low) -> IRQ 7
[   18.316299] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   18.316307] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   18.316360] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   18.320304] ehci_hcd 0000:00:1d.7: debug port 1
[   18.320315] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   18.320328] ehci_hcd 0000:00:1d.7: irq 7, io mem 0xfebfbc00
[   18.335050] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   18.335266] usb usb5: configuration #1 chosen from 1 choice
[   18.335318] hub 5-0:1.0: USB hub found
[   18.335330] hub 5-0:1.0: 8 ports detected
[   18.445290] ACPI: PCI Interrupt 0000:06:01.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   18.498076] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[11]  MMIO=[feaff800-feafffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   18.502799] ACPI: PCI Interrupt 0000:00:1f.2[B] -> Link [LNKD] -> GSI 4 (level, low) -> IRQ 4
[   18.502863] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   18.502888] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   18.510761] ata_piix 0000:00:1f.2: version 2.12
[   18.510772] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[   18.510805] ACPI: PCI Interrupt 0000:00:1f.2[B] -> Link [LNKD] -> GSI 4 (level, low) -> IRQ 4
[   18.510859] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   18.511576] scsi0 : ata_piix
[   18.511703] scsi1 : ata_piix
[   18.514255] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   18.514262] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   18.676520] ata1.00: ATA-7: FUJITSU MHV2120BH PL, 00000029, max UDMA/100
[   18.676530] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   18.691519] ata1.00: configured for UDMA/100
[   19.012319] ata2.01: ATAPI: HL-DT-ST DVDRAM GMA-4082N, HJ02, max UDMA/33
[   19.183194] ata2.01: configured for UDMA/33
[   19.183480] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2120B 0000 PQ: 0 ANSI: 5
[   19.186878] scsi 1:0:1:0: CD-ROM            HL-DT-ST DVDRAM GMA-4082N HJ02 PQ: 0 ANSI: 5
[   19.199545] Driver 'sd' needs updating - please use bus_type methods
[   19.199680] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   19.199717] sd 0:0:0:0: [sda] Write Protect is off
[   19.199723] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   19.199760] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.199860] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   19.199884] sd 0:0:0:0: [sda] Write Protect is off
[   19.199889] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   19.199926] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.199934]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   19.301628]  sda1 sda2 < sda5 sda6 sda7 sda8 sda9 >
[   19.396219] sd 0:0:0:0: [sda] Attached SCSI disk
[   19.406063] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   19.406158] sr 1:0:1:0: Attached scsi generic sg1 type 5
[   19.418540] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   19.418549] Uniform CD-ROM driver Revision: 3.20
[   19.418643] sr 1:0:1:0: Attached scsi CD-ROM sr0
[   19.427604] Clocksource tsc unstable (delta = -220111935 ns)
[   19.430596] Time: hpet clocksource has been installed.
[   19.771747] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0180003627a2e]
[   19.824868] Attempting manual resume
[   19.824875] swsusp: Resume From Partition 8:6
[   19.824879] PM: Checking swsusp image.
[   19.825232] PM: Resume from disk failed.
[   27.644342] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   27.992216] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   28.056108] iTCO_vendor_support: vendor-support=0
[   28.124075] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   28.124218] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x0860)
[   28.124274] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   28.228034] Linux agpgart interface v0.102
[   28.988413] input: Power Button (FF) as /devices/virtual/input/input2
[   28.999526] ACPI: Power Button (FF) [PWRF]
[   28.999737] input: Lid Switch as /devices/virtual/input/input3
[   29.001562] ACPI: Lid Switch [LID]
[   29.001706] input: Power Button (CM) as /devices/virtual/input/input4
[   29.011528] ACPI: Power Button (CM) [PWRB]
[   29.011667] input: Sleep Button (CM) as /devices/virtual/input/input5
[   29.023538] ACPI: Sleep Button (CM) [SLPB]
[   29.199806] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   29.279567] asus-laptop: Asus Laptop Support version 0.42
[   29.280037] asus-laptop:   F3JA model detected
[   29.282389] Registered led device: asus:touchpad
[   29.503433] sysfs: duplicate filename 'pcspkr' can not be created
[   29.503442] WARNING: at /build/buildd/linux-2.6.24/fs/sysfs/dir.c:424 sysfs_add_one()
[   29.503450] Pid: 2867, comm: modprobe Not tainted 2.6.24-19-generic #1
[   29.503466]  [<c01d74df>] sysfs_add_one+0x9f/0xe0
[   29.503487]  [<c01d7a18>] create_dir+0x48/0x90
[   29.503500]  [<c01d7a89>] sysfs_create_dir+0x29/0x50
[   29.503510]  [<c02154cf>] kobject_get+0xf/0x20
[   29.503519]  [<c0215993>] kobject_add+0x93/0x1b0
[   29.503533]  [<c0215b41>] kobject_register+0x21/0x50
[   29.503542]  [<c0282041>] bus_add_driver+0x71/0x1e0
[   29.503557]  [<c01507c6>] sys_init_module+0x126/0x19c0
[   29.503593]  [<c031c440>] _spin_lock_irqsave+0x0/0x50
[   29.503611]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[   29.503629]  =======================
[   29.503635] kobject_add failed for pcspkr with -EEXIST, don't try to register things with the same name in the same directory.
[   29.503646] Pid: 2867, comm: modprobe Not tainted 2.6.24-19-generic #1
[   29.503652]  [<c0215a13>] kobject_add+0x113/0x1b0
[   29.503666]  [<c0215b41>] kobject_register+0x21/0x50
[   29.503675]  [<c0282041>] bus_add_driver+0x71/0x1e0
[   29.503688]  [<c01507c6>] sys_init_module+0x126/0x19c0
[   29.503722]  [<c031c440>] _spin_lock_irqsave+0x0/0x50
[   29.503738]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[   29.503754]  =======================
[   30.407591] Synaptics Touchpad, model: 1, fw: 6.1, id: 0xa3a0b3, caps: 0xa04713/0x10008
[   30.452615] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   30.499021] ACPI: PCI Interrupt 0000:00:1b.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   30.499062] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   30.583368] ACPI: AC Adapter [AC0] (off-line)
[   30.970719] ACPI: Battery Slot [BAT0] (battery present)
[   31.295391] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:14/LNXVIDEO:00/input/input8
[   31.326615] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   31.350494] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   31.610423] [fglrx] Maximum main memory to use for locked dma buffers: 928 MBytes.
[   31.610504] [fglrx] ASYNCIO init succeed!
[   31.612705] [fglrx] PAT is enabled successfully!
[   31.622286] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   31.838594] ricoh-mmc: Ricoh MMC Controller disabling driver
[   31.838601] ricoh-mmc: Copyright(c) Philip Langdale
[   31.838664] ricoh-mmc: Ricoh MMC controller found at 0000:06:01.2 [1180:0843] (rev 1)
[   31.838683] ricoh-mmc: Controller is now disabled.
[   31.872287] sdhci: Secure Digital Host Controller Interface driver
[   31.872294] sdhci: Copyright(c) Pierre Ossman
[   31.872356] sdhci: SDHCI controller found at 0000:06:01.1 [1180:0822] (rev 19)
[   31.872389] ACPI: PCI Interrupt 0000:06:01.1[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   31.872415] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   31.872491] mmc0: SDHCI at 0xfeaff400 irq 5 DMA
[   34.247694] lp: driver loaded but no devices found
[   34.444042] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   34.462497] usbcore: registered new interface driver ndiswrapper
[   34.512749] Adding 2048248k swap on /dev/sda6.  Priority:-1 extents:1 across:2048248k
[   39.077538] ip_tables: (C) 2000-2006 Netfilter Core Team
[   39.895124] NET: Registered protocol family 17
[   40.695976] No dock devices found.
[   42.543557] apm: BIOS not found.
[   51.397237] r8169: eth0: link up
[   51.397254] r8169: eth0: link up
[   51.935255] NET: Registered protocol family 10
[   51.935699] lo: Disabled Privacy Extensions
[   52.223406] Bluetooth: Core ver 2.11
[   52.224185] NET: Registered protocol family 31
[   52.224193] Bluetooth: HCI device and connection manager initialized
[   52.224201] Bluetooth: HCI socket layer initialized
[   52.497919] Bluetooth: L2CAP ver 2.9
[   52.497928] Bluetooth: L2CAP socket layer initialized
[   52.660778] Bluetooth: RFCOMM socket layer initialized
[   52.660800] Bluetooth: RFCOMM TTY layer initialized
[   52.660804] Bluetooth: RFCOMM ver 1.8
[   52.924739] ppdev: user-space parallel port driver
[   53.650941] audit(1221347000.141:2): type=1502 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5570 profile="/usr/sbin/cupsd" namespace="default"
[   53.708081] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   56.067151] [fglrx] Reserve Block - 0 offset =  0X1000000 length = 0X5000
[   56.067160] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
[   56.067163] [fglrx] Reserve Block - 2 offset =  0Xffff000 length = 0X1000
[   56.067166] [fglrx] Reserve Block - 3 offset =  0Xffbf000 length = 0X40000
[   56.643287] [fglrx] interrupt source 10000000 successfully enabled
[   56.643303] [fglrx] enable ID = 0x00000008
[   56.643318] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[   57.254699] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26k
[   57.254710] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   57.254883] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   57.254910] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   57.254940] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   57.316456] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   57.318149] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   57.855892] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[   57.872549] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   57.872700] PM: Writing back config space on device 0000:03:00.0 at offset 1 (was 100002, writing 100006)
[   58.234506] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   64.986694] eth0: no IPv6 routers present
[   86.270124] CPU0 attaching NULL sched-domain.
[   86.270136] CPU1 attaching NULL sched-domain.
[   86.281734] CPU0 attaching sched-domain:
[   86.281741]  domain 0: span 03
[   86.281745]   groups: 01 02
[   86.281750]   domain 1: span 03
[   86.281751]    groups: 03
[   86.281754] CPU1 attaching sched-domain:
[   86.281756]  domain 0: span 03
[   86.281759]   groups: 02 01
[   86.281765]   domain 1: span 03
[   86.281768]    groups: 03
[  141.027732] CPU0 attaching NULL sched-domain.
[  141.027739] CPU1 attaching NULL sched-domain.
[  141.053982] CPU0 attaching sched-domain:
[  141.053986]  domain 0: span 03
[  141.053989]   groups: 01 02
[  141.053993] CPU1 attaching sched-domain:
[  141.053994]  domain 0: span 03
[  141.053996]   groups: 02 01
manolo@manolo-laptop:~$

---

### Post by manolomanolo on 2008-09-17
I'd like to add something more to my last post.

I use a [DSL-G624T]("http://www.dlink.it/?go=gNTyP9CgrdFOIC4AStFCF834mptYKO9ZTdvhLPG3yV3oVot8gqltbNlwaaFp6DQoHDrqzCNH+4QADNvg") router. I tried to connect [this wireless adapter]("http://www.dlink.co.uk/?go=gNTyP9CgrdFOIC4AStFCF834mptYKO9ZTdvhLPG3yV3oUop7hqltbNlwaaFp6DQoHDrpzyRC944ABd3h") included into the box and I did was able to connect to my wireless lan installing nothing, configuring nothing: just connecting the adapter to my laptop.

That's the ifconfig and iwconfig I run with both wifi devices turned on. Please note the words in **bold**

manolo@manolo-laptop:~$ **ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:17:31:fb:61:25  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fefb:6125/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12236 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12156 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9066020 (8.6 MB)  TX bytes:2013052 (1.9 MB)
          Interrupt:219 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20902 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20902 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1045100 (1020.6 KB)  TX bytes:1045100 (1020.6 KB)

wlan1     Link encap:Ethernet  HWaddr 00:19:5b:80:26:08  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster1  Link encap:UNSPEC  HWaddr **00-19-5B-80-26-08-00-00-00-00-00-00-00-00-00-00**
[COLOR="Red"](strange MAC address, isn't it???)[/COLOR]
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

manolo@manolo-laptop:~$ **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          **Tx-Power=0 dBm **  
[COLOR="Red"]does this mean it's turned off somehow?!?[/COLOR]
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wmaster1  no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          **Tx-Power=22 dBm **
[COLOR="Red"](does this mean it works, since it does work???)[/COLOR]
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

manolo@manolo-laptop:~$

---

### Post by pytheas22 on 2008-09-17
> Tx-Power=0 dBm
does this mean it's turned off somehow?!?

Yes, that's a good thing to notice.  Perhaps the card's radio is not turned on or something.

I looked through your dmesg output in more detail and still can't find anything that explains what's wrong, unfortunately.  I strongly suspect that it may have something to do with ACPI, however, especially since you say that the wireless light comes on initially but then goes off--there may be an IRQ conflict or something causing the device to go down.

It may help to disable IRQ routing via ACPI.  To do that, run this command (it will edit your grub boot menu, but take a backup first in case there's a problem):
```

cp /boot/grub/menu.lst ~/Desktop/menu.lst.backup
sudo sed 's/ro quiet splash/ro quiet splash pci=routeirq/g' /boot/grub/menu.lst
```

Then try rebooting, and please let us knwo whether the wireless card works.

---

### Post by manolomanolo on 2008-09-18
No, it doesn't work. Sorry.
I'm still making some tests (such as some ifdown/ifup interface). On the other hand I noticed 

manolo@manolo-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:31:fb:61:25  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fefb:6125/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2797 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3473 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2276644 (2.1 MB)  TX bytes:499998 (488.2 KB)
          Interrupt:219 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16111 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16111 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:805687 (786.8 KB)  TX bytes:805687 (786.8 KB)

wlan0     Link encap:Ethernet  HWaddr **00:13:02:ef:81:1f**  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr **00:13:02:ef:81:1f**  
          inet addr:169.254.5.132  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr **00-13-02-EF-81-1F-00-00-00-00-00-00-00-00-00-00**
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Is it normal? I suppose it isn't, sice as I can remember when everything worked properly I didn't see all of those device names associated to the same mac address...
Could it be useful to remove some of them?

Thanks for your time!

PD: should I post some output in order to let you realize the present condition of my system after having applied those modifications you suggested above?
PD2: is [this link]("http://www.ubuntugeek.com/using-ipw3945-instead-iwl3945-in-hardy.html") useful to me?

---

### Post by pytheas22 on 2008-09-18
The information in 'ifconfig,' including the 00:00:00:00... stuff and the wmaster0 interface, is normal.  wlan0 is a virtual interface based off of wmaster0...this is the way that the Linux wireless drivers like to operate now.  So unfortunately, there's nothing in your last post that stands out as indicative of a problem.
> 
PD2: is this link useful to me? 

I'm familiar with that link, which provides instructions for compiling ipw3945, an alternative to your driver which would probably work better.  Unfortunately, I (along with others whom I've tried to help) was never able to get ipw3945 to compile using those instructions--the compiler always died with errors that I couldn't resolve.  There are a few other pages around the Internet with guides that presume to allow you to compile ipe3945 on Ubuntu Hardy, but none of them worked for me.

But you could try those instructions and see if they work.  I never recommended that link before because I'd had such a bad experience with it, but maybe it would work for you and solve the problem.

Please let me know if you have any luck compiling ipw3945 as per that link.

---

### Post by manolomanolo on 2008-09-19
> **manolomanolo said:**
> 
**wlan0**     Link encap:Ethernet  HWaddr **00:13:02:ef:81:1f**  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

**wlan0:avahi** Link encap:Ethernet  HWaddr 00:13:02:ef:81:1f  
          inet addr:169.254.5.132  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

And what about that duplicated wlan0 and wlan0:avahi ? Is it normal too? [AVAHI]("http://avahi.org/"): could this cause any problem in my case?

> 
PD: should I post some output in order to let you realize the present condition of my system after having applied those modifications you suggested above?
Just nothing?

> PD2: is [this link]("http://www.ubuntugeek.com/using-ipw3945-instead-iwl3945-in-hardy.html") useful to me?
Well I suppose those many tries you've been doing so far are enough to me to state it's not a safe and stable try... any other suggestion, please?

Thanks for your time!
Regards.

---

### Post by pytheas22 on 2008-09-19
> PD: should I post some output in order to let you realize the present condition of my system after having applied those modifications you suggested above?
Just nothing?


Sure, I guess it wouldn't hurt to see the output after a fresh reboot of:

dmesg | grep -e adio -e rror -e wlan -e iwl
modinfo iwl3945
> 
Well I suppose those many tries you've been doing so far are enough to me to state it's not a safe and stable try... any other suggestion, please?

You can try that link; maybe it will work for you.  There are several people on that page who say it worked for them in Hardy as late as last July.  It won't make anything worse.  I doubt you'll be able to compile the module but on the off-chance that you can, it's probably worth the time to try.
> 
And what about that duplicated wlan0 and wlan0:avahi ? Is it normal too? AVAHI: could this cause any problem in my case?

xxx:avahi interfaces are created when you can't get a valid IP on your real interface (in your case, wlan0) and you get assigned a 169.254.X.X address instead.  So it's not indicative of a problem, unfortunately (I wish it were so that we'd have something more concrete to chase down).

---

### Post by manolomanolo on 2008-09-19
manolo@manolo-laptop:~$ **dmesg | grep -e adio -e rror -e wlan -e iwl**
[   17.107056] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   17.391889] APIC error on CPU1: 00(40)
[   19.311785] usplash[1246]: segfault at b7ba0000 eip b7f4bdd6 esp bfaf5670 error 7
[   54.141727] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26k
[   54.141735] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   54.141941] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   54.204633] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   54.206841] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   54.772056] ADDRCONF(NETDEV_UP): wlan0: link is not ready
manolo@manolo-laptop:~$ 

manolo@manolo-laptop:~$ **modinfo iwl3945**
filename:       /lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/iwlwifi/iwl3945.ko
license:        GPL
author:         Copyright(c) 2003-2008 Intel Corporation
version:        1.2.26k
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     2E944606B3F00247F86576B
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
alias:          pci:v00008086d00004227sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001044bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001034bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001005bc*sc*i*
depends:        mac80211,cfg80211
vermagic:       2.6.24-19-generic SMP mod_unload 586 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           hwcrypto:using hardware crypto engine (default 0 [software])
 (int)
parm:           debug:debug output mask (int)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           queues_num:number of hw queues. (int)
parm:           qos_enable:enable all QoS functionality (int)

I should also precise something we've been discussing [here]("http://ubuntuforums.org/showpost.php?p=5784305&postcount=30"). The wifi led of my laptop turns off anyhow. I mean it turns ON at the bootstrap and then turns OFF few second before the desktop is loaded taking place of the black screen. Then it turns OFF whether the switch is ON or OFF. Of course this happens with Ubuntu, Window$ doesn't give that kind of problem. I remark this point since we could think about restoring [that stuff]("http://ubuntuforums.org/showpost.php?p=5805999&postcount=32") one day :)

As for [this link]("http://www.ubuntugeek.com/using-ipw3945-instead-iwl3945-in-hardy.html"), I suppose I'll try it after you replying to this post... maybe you can find something significant into that "fresh output"

Many thanks for your help!

---

### Post by pytheas22 on 2008-09-20
Unfortunately, nothing in your output stands out as a problem.  Since you say that the wifi light stays on until just before the desktop loads, however, why don't we try not loading the desktop to see if that does anything?  Maybe when the desktop gets loaded something happens that makes the wireless card turn off.

If you run this command:
```

sudo update-rc.d -f gdm remove
```

and restart your computer, you should boot to a command prompt instead of the graphical login.  Once at the command prompt, login, then run these commands:
```

iwlist scan; iwlist scan
```

Do you see any wireless networks?  And is you wireless light still on at this point?

If you want to login from the command line to a graphical session after you're done testing the wifi stuff, run:
```

sudo /etc/init.d/gdm start
startx
```

and your desktop should load.

Please let me know if preventing the graphical environment from loading has any affect on whether the wifi light stays on.

You might also want to try compiling ipw3945 from that link too, just in case it works.

---

### Post by manolomanolo on 2008-11-08
I upgraded to Ubuntu 8.10 and also tried to change my desktop theme: those thinks solved the problem related to activating the led of my wifi card.

But I'm still unable to make it work. Can you please tell me how to install properly my original 3945ABG wifi drivers, please? Please note I think I still have ndiswrapper installed

---

### Post by pytheas22 on 2008-11-08
What exactly is wrong?  Are you unable to see wireless networks?  Can you see networks but not connect?  Have you tried connecting using [wicd]("http://wicd.sourceforge.net")?

Please also post the output of the following commands so that we can figure out what's going on (i.e. which module is actually driving the card, etc.):
```

lshw -C Network
dmesg | grep -e ndis -e wlan -e iwl
modinfo iwl3945
sudo iwlist scan
```

---

### Post by manolomanolo on 2008-11-08
Running network manager and trying to scan for new networks gives no results.

manolo@manolo-laptop:~$ sudo **lshw -C Network**
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:17:31:fb:61:25
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.3 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:ef:81:1f
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 0a:55:96:ce:cc:38
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

manolo@manolo-laptop:~$ **dmesg | grep -e ndis -e wlan -e iwl**
[   12.385135] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   12.385140] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   12.417553] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.417570] iwl3945 0000:03:00.0: setting latency timer to 64
[   12.417596] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   12.493310] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   12.493847] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   12.879911] iwl3945 0000:03:00.0: PCI INT A disabled
[   13.835488] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   13.837097] usbcore: registered new interface driver ndiswrapper
[   19.948459] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.948609] iwl3945 0000:03:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[   19.948885] firmware: requesting iwlwifi-3945-1.ucode
[   20.098343] Registered led device: iwl-phy0:radio
[   20.098366] Registered led device: iwl-phy0:assoc
[   20.098425] Registered led device: iwl-phy0:RX
[   20.098451] Registered led device: iwl-phy0:TX
[  105.674230] ADDRCONF(NETDEV_UP): wlan0: link is not ready

manolo@manolo-laptop:~$ **modinfo iwl3945**
filename:       /lib/modules/2.6.27-7-generic/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko
license:        GPL
author:         Copyright(c) 2003-2008 Intel Corporation
version:        1.2.26ks
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     5C079549ABD48E07B20F3C7
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
alias:          pci:v00008086d00004227sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001044bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001034bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001005bc*sc*i*
depends:        mac80211,led-class,cfg80211,rfkill
vermagic:       2.6.27-7-generic SMP mod_unload modversions 586 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           hwcrypto:using hardware crypto engine (default 0 [software])
 (int)
parm:           debug:debug output mask (int)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           queues_num:number of hw queues. (int)
parm:           qos_enable:enable all QoS functionality (int)

manolo@manolo-laptop:~$ **sudo iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:19:5B:98:14:D6
                    ESSID:"dlink"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=100/100  Signal level:-20 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=000000476e0121b2
                    Extra: Last beacon: 1416ms ago
          Cell 02 - Address: 00:14:C1:04:23:28
                    ESSID:"USR5451"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/100  Signal level:-88 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000000c5dca3187
                    Extra: Last beacon: 1000ms ago
          Cell 03 - Address: 00:0C:F6:27:6D:A2
                    ESSID:"Sitecom"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/100  Signal level:-86 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000001c2d28fbed
                    Extra: Last beacon: 1076ms ago

pan0      Interface doesn't support scanning.

---

### Post by pytheas22 on 2008-11-08
You're able to see networks from the command line (using the 'sudo iwlist scan' command) with no problem and everything else looks alright based on the output you posted above, so if Network Manager can't see networks, it's probably a problem specific to NM, not your connection.  You would probably be able to connect by installing [wicd]("http://wicd.sourceforge.net") (installation instructions on the site).  Alternatively, if you tell me the name of your wireless network, I can give you commands to connect to it from the command-line (unless you use WPA encryption, in which case it's not worth the hassle of connecting manually, and you should just try wicd instead).

It may also help to reinstall Network Manager by typing:
```

sudo apt-get remove --purge network-manager
sudo apt-get install network-manager-gnome
```

---

### Post by manolomanolo on 2008-11-10
Installing "wicd" solved my problems related to connecting to internet using my wireless card! Thanks a lot!

My last problem related to wifi card is that Ubuntu hangs a bit while "configuring network interfaces" at bot time.
Should I open a different thread or we could go on talking just here?

Thanks!!!

---

### Post by pytheas22 on 2008-11-10
Glad to hear that wicd helped.

As for the hanging at boot, it may be caused by some oddities in your /etc/network/interfaces file.  What is the output of:
```

cat /etc/network/interfaces
```

Also, how long is it hanging (five seconds, ten seconds, a minute...)?

---

### Post by manolomanolo on 2008-11-11
Cannot be very precise about timing, but I suppose at least a minute hanging.

manolo@manolo-laptop:~$ **cat /etc/network/interfaces**
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp

---

### Post by pytheas22 on 2008-11-11
hmmm, nothing out of the ordinary in your interfaces file.

The next time you reboot the machine, please press control-alt-F1 as soon as you see the splash screen with the big orange Ubuntu bar.  This should give you a verbose list of what the machine is doing as it boots (if you don't see a list, try pressing control-alt-F7).  What does it say it's doing on the part where it hangs?  Does it say anything besides 'configuring network interfaces'?  Also, if you have time to record it, which actions come before and after the part where it hangs?

---

