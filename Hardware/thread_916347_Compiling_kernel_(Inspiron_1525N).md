---
title: "Compiling kernel (Inspiron 1525N)"
date: 2008-09-10
forum: Hardware
---

### Post by galli on 2008-09-10
Hello everybody,

I'm having a drivers issue after compiling the kernel. I hope somebody could give me some light on this.

After compile the kernel and boot from it the following drivers are missing:
    * Sound driver
    * Wireless

My lspci output is the following:

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```

Also, I made a simple python script which compares the modules available (lsmod) in the oficial ubuntu i386 kernel and the modules not available on the new compiled kernel. This is the list of modules which are not available on the kernel compiled by me:
```
nls_iso8859_1
nls_cp437
vfat
fat
af_packet
acpi_cpufreq
mmc_block
compat_ioctl32
videodev
v4l1_compat
v4l2_common
arc4
ecb
blkcipher
iwlwifi_mac80211
cfg80211
led_class
snd_hda_intel
snd_mixer_oss
snd_pcm
snd_page_alloc
snd_hwdep
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
soundcore
tileblit
font
bitblit
softcursor
```

As far as I know my wireless driver comes distributed with the official kernel. The versions I compiled are 2.6.26.5 and 2.6.24 (downloaded from the ubuntu repositories with apt-get install linux-source) and the same behavior is happening. I checked my .config for the kernel compilation and I have all the wireless options checked so I don't know what's wrong with that.

Any help is very much appreciated.

PS: I compiled the kernel 6 times in 2 days testing and testing different options :P.

Thanks, 
Fabián.

---

### Post by ajmorris on 2008-09-10
hi there,
in your kernel config, make sure you enable the Intel HD Audio, and the Intel Wireless.

If you're not sure if they're enabled or not, please post your /usr/src/linux/.config file (make sure /usr/src/linux is pointing to the source you're compiling)

AJ

---

### Post by galli on 2008-09-10
Hi, thanks for the reply.

Actually looking to the config file I found the following:

# CONFIG_IWLWIFI is not set

The point is that I was using the make menuconfig, so I don't know where was that setting.

And for alsa I guess I forgot to enable it as a module, I can compile it separately.

The Webcam does not works. But in this case I don't know which setting is messing up with it. (I Just found the webcam thing).

I downloaded the uvcvideo module and compiled but not luck yet.

Attached is my .config file if you have some recommendations please advice.

Thanks!
Fabián.

---

### Post by Crafty Kisses on 2008-09-10
Have you tried the following for the missing sound?
```
update-modules
/etc/init.d/alsasound restart
```
It could be a problem with alsa too, this happened to me before when I was compiling a kernel, also check what version of alsa is running. The version of ALSA in the currently-running kernel can be shown with:
```
cat /proc/asound/version
```
Or for the kernel in **/usr/src/linux**
```

/usr/src/linux/include/sound/version.h
```

---

### Post by galli on 2008-09-10
> **Codename said:**
> Have you tried the following for the missing sound?
```
update-modules
/etc/init.d/alsasound restart
```
It could be a problem with alsa too, this happened to me before when I was compiling a kernel, also check what version of alsa is running. The version of ALSA in the currently-running kernel can be shown with:
```
cat /proc/asound/version
```
Or for the kernel in **/usr/src/linux**
```

/usr/src/linux/include/sound/version.h
```

Thanks for the tip, but alsa is not even compiled as a module :P. I will compile it now, I think it should work.

---

### Post by Crafty Kisses on 2008-09-10
> **galli said:**
> Thanks for the tip, but alsa is not even compiled as a module :P. I will compile it now, I think it should work.

Glad I could help, that's probably what the issue is, please post back. :)

---

### Post by galli on 2008-09-10
> **Codename said:**
> Glad I could help, that's probably what the issue is, please post back. :)

Well, it didn't worked, however I fixed the webcam (it is normal you fix what you don't touch :P), I compiled the uvcvideo myself and it started to work :). I will try the same with alsa and finally with the wifi.

I will probably need help with the wifi module since I received a couple of errors during the make, I will try to do a couple of things and let you know.

---

### Post by Crafty Kisses on 2008-09-10
Yeah, I can help with the Wifi module, just let me know.

---

### Post by galli on 2008-09-10
> **Codename said:**
> Yeah, I can help with the Wifi module, just let me know.

Thanks for your support.

I will however recompile with the latest stable kernel from kernel.org.

I found a very nice index of the available kernel configuration options: [http://cateee.net/lkddb/web-lkddb/](http://cateee.net/lkddb/web-lkddb/)

I searched for the needed options and I think I'm ready to go :).

Regards,
Fabián.

---

### Post by Crafty Kisses on 2008-09-10
Alright good luck, and yeah you're right that's one good index. :)

---

### Post by galli on 2008-09-11
Ok, I compiled again, the webcam started, the wifi led flashed during the startup, but when the X server should be started the kernel hangs.

I noticed that this happens only when I activate the ALSA module. Any ideas?.

Regards,
Fabián.

---

### Post by galli on 2008-09-12
Hello, I solved everything and now it works like charm :).

Just in case someone gets in the same trouble, if you are compiling your kernel don't select alsa when configuring it because it may cause problems at startup, what I recommend (which worked for me) is to not select ALSA and then compile it from the sources: [http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download)

You main find troubles when running make on the alsa-driver package. What I recommend is to run .configure this way: 

```
./configure --with-cards=hda-intel --prefix=/usr
```
Note: You should have the kernel headers located in /usr/src

Attached is my .config which works quite well.

Regards,
Fabián.

---

