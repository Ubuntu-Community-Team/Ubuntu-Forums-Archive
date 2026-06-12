---
title: "HOWTO: Kaffeine &amp; (Hauppauge) WinTV-Nova-T Stick [Feisty Fawn]"
date: 2007-08-24
forum: Hardware &amp; Laptops
---

### Post by wieman01 on 2007-08-24
Hello, 

I bought a WinTV-Nova-T Stick (Hauppauge) recently and I must say I am once again impressed. The device is 100% (K)Ubuntu (Feisty Fawn) compatible, the only thing that you need to pay attention to is that you get the latest firmware & Kaffeine.

I have based this HOWTO on information given [here]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-Stick").

_**Important note:**_ You don't need to install any other drivers or 'usbvision' as these are part of the 2.6.20 kernel. So Feisty Fawn is ready to roll.

Connect your device and do this:
> dmesg
Which should result in the following output ([COLOR="Red"]dvb-usb-dib0700-01.fw[/COLOR] is the required & missing firmware file):
> [ 5828.308000] dvb-usb: found a 'Hauppauge Nova-T Stick' in cold state, will try to load a firmware
[ 5828.412000] dvb-usb: did not find the firmware file. ([COLOR="Red"]dvb-usb-dib0700-01.fw[/COLOR]) Please see linux/Documentation/dvb/ for more details on firmware-problems. (-2)

Now let's install the firmware:
> cd /lib/firmware
Download latest piece of firmware:
```
sudo wget http://www.wi-bw.tfh-wildau.de/~pboettch/home/linux-dvb-firmware/dvb-usb-dib0700-03-pre1.fw
```
Rename the firmware file you have just downloaded:
> sudo mv dvb-usb-dib0700-03-pre1.fw [COLOR="Red"]dvb-usb-dib0700-01.fw[/COLOR]
Now plug in the device and run:
> dmesg
Which should yield the following result:
> dvb-usb: Hauppauge Nova-T Stick successfully initialized and connected.
Now install Kaffeine:
> sudo apt-get install kaffeine
You can now happily watch TV with Kaffeine.

---

### Post by mtron on 2007-09-18
fix the random disconnects of this Stick:

> Note: Currently, the Nova-T Stick (70009) is known to suffer from I2C errors. Updating to current Hg drivers and using [new firmware]("http://www.wi-bw.tfh-wildau.de/~pboettch/home/linux-dvb-firmware/dvb-usb-dib0700-03-pre1.fw") should cure this.

---

### Post by wieman01 on 2007-09-18
> **mtron said:**
> fix the random disconnects of this Stick:
I have not had such an issue, because I used the most recent version right from the start. Works great actually. I was quite impressed.

---

### Post by mpmc on 2007-09-28
> **mtron said:**
> fix the random disconnects of this Stick:

My SCAN would fail after locking to one mux. Updating to the firmware above worked a treat!

Thanks! 

You :guitar:

---

### Post by wieman01 on 2007-09-29
> **mpmc said:**
> My SCAN would fail after locking to one mux. Updating to the firmware above worked a treat!

Thanks! 

You :guitar:
Thanks, I have updated the link.

---

### Post by Mr. Mulder on 2007-10-07
Hello there,

I bought the stick in question hours ago and could not get it to work in Suse 10.2 so I did some googeling and found this thread, downloaded Kubuntu 7.04, installed it - done what was said in the above posts and no joy :( Reading the Kaffine hand book it says that I should get a DVB window come up when digital TV devices are detected but I just get the standard kaffine window, No pop-ups or notifications appear when I plug in the stick, nothing - any ideas? 

(I'm still a beginner at Linux in general btw) 


........................................................................................
rob@laptop:~$ cd /lib/firmware
rob@laptop:/lib/firmware$ sudo wget [http://www.wi-bw.tfh-wildau.de/~pboettch/home/linux-dvb-firmware/dvb-usb-dib0700-03-pre1.fw](http://www.wi-bw.tfh-wildau.de/~pboettch/home/linux-dvb-firmware/dvb-usb-dib0700-03-pre1.fw)
--17:14:31--  [http://www.wi-bw.tfh-wildau.de/~pboettch/home/linux-dvb-firmware/dvb-usb-dib0700-03-pre1.fw](http://www.wi-bw.tfh-wildau.de/~pboettch/home/linux-dvb-firmware/dvb-usb-dib0700-03-pre1.fw)
           => `dvb-usb-dib0700-03-pre1.fw.1'
Resolving [www.wi-bw.tfh-wildau.de](www.wi-bw.tfh-wildau.de)... 194.95.44.33
Connecting to www.wi-bw.tfh-wildau.de|194.95.44.33|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 33,277 (32K) [text/plain]

100%[====================================>] 33,277       131.50K/s

17:14:31 (131.01 KB/s) - `dvb-usb-dib0700-03-pre1.fw.1' saved [33277/33277]

rob@laptop:/lib/firmware$ dmesg

[  457.116000] usb 4-3: new high speed USB device using ehci_hcd and address 2
[  457.248000] usb 4-3: configuration #1 chosen from 1 choice
[  457.528000] dib0700: loaded with support for 2 different device-types
[  457.532000] dvb-usb: found a 'Hauppauge Nova-T Stick' in cold state, will try to load a firmware
[  457.548000] dvb-usb: did not find the firmware file. (dvb-usb-dib0700-01.fw) Please see linux/Documentation/dvb/ for more details on firmware-problems. (-2)
[  457.552000] usbcore: registered new interface driver dvb_usb_dib0700
[  765.536000] usb 4-3: USB disconnect, address 2
[  768.040000] usb 4-3: new high speed USB device using ehci_hcd and address 3
[  768.172000] usb 4-3: configuration #1 chosen from 1 choice
[  768.172000] dvb-usb: found a 'Hauppauge Nova-T Stick' in cold state, will try to load a firmware
[  768.248000] dvb-usb: did not find the firmware file. (dvb-usb-dib0700-01.fw) Please see linux/Documentation/dvb/ for more details on firmware-problems. (-2)
[ 1007.264000] usb 4-3: USB disconnect, address 3
[ 1018.984000] usb 4-4: new high speed USB device using ehci_hcd and address 4
[ 1019.116000] usb 4-4: configuration #1 chosen from 1 choice
[ 1019.116000] dvb-usb: found a 'Hauppauge Nova-T Stick' in cold state, will try to load a firmware
[ 1019.196000] dvb-usb: did not find the firmware file. (dvb-usb-dib0700-01.fw) Please see linux/Documentation/dvb/ for more details on firmware-problems. (-2)
rob@laptop:/lib/firmware$

---

### Post by wieman01 on 2007-10-07
Ok, it is just a matter of renaming the file now:
> sudo mv /lib/firmware/dvb-usb-dib0700-03-pre1.fw.1 /lib/firmware/dvb-usb-dib0700-01.fw
Is your hardware not detected? If 'dmesg' say so, fire up Kaffeine.

---

### Post by Mr. Mulder on 2007-10-07
Thanks for the speedy reply wieman01, did what you said and got this?

[ 4841.460000] usb 4-3: USB disconnect, address 5
[ 5828.176000] usb 4-3: new high speed USB device using ehci_hcd and address 6
[ 5828.308000] usb 4-3: configuration #1 chosen from 1 choice
[ 5828.308000] dvb-usb: found a 'Hauppauge Nova-T Stick' in cold state, will try to load a firmware
[ 5828.412000] dvb-usb: did not find the firmware file. (dvb-usb-dib0700-01.fw) Please see linux/Documentation/dvb/ for more details on firmware-problems. (-2)
rob@laptop:/lib/firmware$

---

### Post by wieman01 on 2007-10-07
Please try again... just did it using my other computer (Gutsy) and it worked fine:
> cd /lib/firmware
> sudo mv dvb-usb-dib0700-03-pre1.fw dvb-usb-dib0700-01.fw
Then insert the stick and do a 'dmseg'. Now better? Kaffeine should initialize the necessary packages now.

---

### Post by Mr. Mulder on 2007-10-07
Yep that worked perfectly! Thanks for your time and effort wieman01, its greatly appreciated :)

Did you manage to pick up channels straight away in your part of the world? I'm from Lincoln, UK and don't seem to be picking up any - The device settings see it as DiBcom 7000PC and the type as Terrestrial instead of digital? Maybe that's why I can't pick up any channels?

..............................................................

edit: running dmesg again and reading through i seem to have a warning here, could this be why kaffeine see's my device as something different?

[12060.368000] usb 4-3: new high speed USB device using ehci_hcd and address 8
[12060.500000] usb 4-3: configuration #1 chosen from 1 choice
[12060.500000] dvb-usb: found a 'Hauppauge Nova-T Stick' in cold state, will try
 to load a firmware
[12060.780000] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-01.fw'
[12060.972000] dib0700: firmware started successfully.
[12061.476000] dvb-usb: found a 'Hauppauge Nova-T Stick' in warm state.
[12061.476000] dvb-usb: will pass the complete MPEG2 transport stream to the sof
tware demuxer.
[12061.476000] DVB: registering new adapter (Hauppauge Nova-T Stick).



[12061.672000] [COLOR="Blue"]**WARNING** I2C adapter driver [DiBX000 tuner I2C bus] forgot to
specify physical device; fix it!
[12061.728000] DVB: registering frontend 0 ([COLOR="MediumTurquoise"]DiBcom 7000PC[/COLOR])...[/COLOR]




[12061.732000] MT2060: successfully identified (IF1 = 1220)
[12062.164000] Inbound IN=eth0 OUT= MAC=00:06:1b:d8:ab:69:00:09:7b:8e:4c:01:08:0
0 SRC=85.228.122.5 DST=86.9.143.215 LEN=91 TOS=0x00 PREC=0x00 TTL=112 ID=31519 P
ROTO=UDP SPT=62634 DPT=49157 LEN=71
[12062.208000] dvb-usb: Hauppauge Nova-T Stick successfully initialized and conn
ected.

---

### Post by wieman01 on 2007-10-07
> **Mr. Mulder said:**
> Yep that worked perfectly! Thanks for your time and effort wieman01, its greatly appreciated :)

Did you manage to pick up channels straight away in your part of the world? I'm from Lincoln, UK and don't seem to be picking up any - The device settings see it as DiBcom 7000PC and the type as Terrestrial instead of digital? Maybe that's why I can't pick up any channels?
No idea actually. You should be able to find some at least. But it really depends on the reception and physical distance to the broadcast station/antenna.

Glad it worked for you. I really need to update that tutorial for it isn't quite self-explanatory.

---

### Post by Mr. Mulder on 2007-10-07
Has it worked though? As it seems to see my device as a DVB Device 0:0 DiBcom 7000PC? Receptions great in this area too, my neighbour who has the same stick (and recomended it to me) picks up all the available channels in our area on his Vista machine




[http://img216.imageshack.us/img216/8127/snapshot2el7.jpg](http://img216.imageshack.us/img216/8127/snapshot2el7.jpg) instead of something like this in the handbook example [http://img227.imageshack.us/img227/2153/snapshot3dp8.jpg](http://img227.imageshack.us/img227/2153/snapshot3dp8.jpg)

....................................................................

[12060.368000] usb 4-3: new high speed USB device using ehci_hcd and address 8
 [12060.500000] usb 4-3: configuration #1 chosen from 1 choice
 [12060.500000] dvb-usb: found a 'Hauppauge Nova-T Stick' in cold state, will try
 to load a firmware
 [12060.780000] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-01.fw'
 [12060.972000] dib0700: firmware started successfully.
 [12061.476000] dvb-usb: found a 'Hauppauge Nova-T Stick' in warm state.
 [12061.476000] dvb-usb: will pass the complete MPEG2 transport stream to the sof
 tware demuxer.
 [12061.476000] DVB: registering new adapter (Hauppauge Nova-T Stick).
 
 
 
 [12061.672000] **WARNING** I2C adapter driver [DiBX000 tuner I2C bus] forgot to
 specify physical device; fix it!
 [12061.728000] DVB: registering frontend 0 (DiBcom 7000PC)...
 
 
 
 
 [12061.732000] MT2060: successfully identified (IF1 = 1220)
 [12062.164000] Inbound IN=eth0 OUT= MAC=00:06:1b:d8:ab:69:00:09:7b:8e:4c:01:08:0
 0 SRC=85.228.122.5 DST=86.9.143.215 LEN=91 TOS=0x00 PREC=0x00 TTL=112 ID=31519 P
 ROTO=UDP SPT=62634 DPT=49157 LEN=71
 [12062.208000] dvb-usb: Hauppauge Nova-T Stick successfully initialized and conn
 ected.

---

### Post by wieman01 on 2007-10-08
**Mr. Mulder:**

Actually everything looks fine as far as "dmesg" is concerned. And I have tested this both on Gutsy & Feisty yesterday. Both work fine.

You have to extend the antenna and move closer to a window. I suspect reception is bad where you are. The device should pick up broadcast signals itself but I remember that I had to perform several scans myself before it would detect any. Now it works great but reception can be flawed from time to time.

---

### Post by Mr. Mulder on 2007-10-08
Tried it in two different rooms and even outside my front door (looking like a lunatic) and still nothing :( What does kaffeine see your device as? We have the same Nova-T Stick so does it see yours as an DiBcom 7000PC and the type as Terrestrial? :confused:

---

### Post by Mr. Mulder on 2007-10-09
Bump (if that's allowed here?)  :confused:

---

### Post by wieman01 on 2007-10-10
> **Mr. Mulder said:**
> Bump (if that's allowed here?)  :confused:
Sure it is allowed. I meant to post yesterday but I wasn't at home. Let me check tonight once again. I'll post a screenshot.

---

### Post by wieman01 on 2007-10-10
Same here. See attachment.

---

### Post by ugm6hr on 2007-10-25
Just a quick question before I invest in one of these (is the the device we are talking about?)....

[http://www.ebuyer.com/product/128575](http://www.ebuyer.com/product/128575)

Does it allow pre-defined recording onto your HD from Freeview (in Ubuntu)?

---

### Post by wieman01 on 2007-10-27
It seems to be the one we are talking about. I have never used Freeview though, but Kaffeine lets you record stuff, no problem.

---

### Post by kpmaddenuk on 2007-10-31
Wieman01,

Good concise, accurate instructions. Well done.

May I also add to the instructions that if you're using the PCI version of the Nova you need a restart to pick up the firmware. At least I did.

Cheers - K

---

### Post by wieman01 on 2007-10-31
> **kpmaddenuk said:**
> Wieman01,

Good concise, accurate instructions. Well done.

May I also add to the instructions that if you're using the PCI version of the Nova you need a restart to pick up the firmware. At least I did.

Cheers - K
Hello K, 

Did it work for the PCI version as well? Would be nice if you put your instructions here and told us what exact model you have got there. Thanks for letting us know.

---

### Post by telegram.sam on 2007-11-05
Hi

Have got a Nova T Stick on Feisty that works fine on my (administrator's) login but when I try to use it on another login it doesn't work. The DVB menu doesn't appear and the "Digital TV" icon is named "DVB Client". I also have the "can't bind client info" message on the new user, which I understand shouldn't be a problem.

Have searched around but can't find any info on how to fix this.

Have I forgotten to do something user specific that I did on the original installation (and can't remember obviously)?

Any help much appreciated.

T

---

### Post by wieman01 on 2007-11-05
> **telegram.sam said:**
> Hi

Have got a Nova T Stick on Feisty that works fine on my (administrator's) login but when I try to use it on another login it doesn't work. The DVB menu doesn't appear and the "Digital TV" icon is named "DVB Client". I also have the "can't bind client info" message on the new user, which I understand shouldn't be a problem.

Have searched around but can't find any info on how to fix this.

Have I forgotten to do something user specific that I did on the original installation (and can't remember obviously)?

Any help much appreciated.

T
Is the current user an "administrative" user with "sudo" rights"? That could relate to your issue.

---

### Post by johnwillyums on 2007-11-12
Hello wieman, thanks for your reply

I looked at your thread and tried typing "dmesg" into terminal and pressing enter- I take it that's what you intended(?)

Anyway that got me three full screen pages of text:

[ 0.000000] ACPI: IRQ14 used by override.
[ 0.000000] ACPI: IRQ15 used by override.

[ 0.000000] Setting APIC routing to flat
[ 0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[ 0.000000] Using ACPI (MADT) for SMP configuration information
[ 0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[ 0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[ 0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[ 0.000000] swsusp: Registered nosave memory region: 00000000dfef0000 - 00000000dfef3000
[ 0.000000] swsusp: Registered nosave memory region: 00000000dfef3000 - 00000000dff00000
[ 0.000000] swsusp: Registered nosave memory region: 00000000dff00000 - 00000000f0000000
[ 0.000000] swsusp: Registered nosave memory region: 00000000f0000000 - 00000000f2000000
[ 0.000000] swsusp: Registered nosave memory region: 00000000f2000000 - 00000000fec00000
[ 0.000000] swsusp: Registered nosave memory region: 00000000fec00000 - 0000000100000000
[ 0.000000] Allocating PCI resources starting at e0000000 (gap: dff00000:10100000)
[ 0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[ 0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[ 0.000000] Built 1 zonelists. Total pages: 1030952
[ 0.000000] Kernel command line: root=UUID=bd3729dc-e776-4164-b090-b8851f54492a ro quiet splash
[ 0.000000] Initializing CPU#0
[ 0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[ 0.000000] Extended CMOS year: 2000
[ 24.429892] time.c: Detected 2399.978 MHz processor.
[ 24.430988] Console: colour VGA+ 80x25
[ 24.431005] Checking aperture...
[ 24.431014] Calgary: detecting Calgary via BIOS EBDA area
[ 24.431015] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[ 24.431017] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[ 24.467798] Placing software IO TLB between 0x104c000 - 0x504c000
[ 24.504057] Memory: 4049800k/4718592k available (2274k kernel code, 143028k reserved, 1181k data, 296k init)
[ 24.504100] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[ 24.583988] Calibrating delay using timer specific routine.. 4803.92 BogoMIPS (lpj=9607852)
[ 24.584015] Security Framework v1.0.0 initialized
[ 24.584022] SELinux: Disabled at boot.
[ 24.584334] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[ 24.587298] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[ 24.588521] Mount-cache hash table entries: 256
[ 24.588649] CPU: L1 I cache: 32K, L1 D cache: 32K
[ 24.588652] CPU: L2 cache: 4096K
[ 24.588654] CPU 0/0 -> Node 0

I have tried to paste all of it here but can't for some reason. Will try to get the last page,yes here it is:

[ 39.152768] parport_pc 00:09: reported by Plug and Play ACPI
[ 39.152796] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[ 39.222351] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(66)
[ 39.222359] Uniform CD-ROM driver Revision: 3.20
[ 39.224605] hdd: ATAPI 48X DVD-ROM drive, 198kB Cache, UDMA(33)
[ 39.269620] nvidia: module license 'NVIDIA' taints kernel.
[ 39.526645] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[ 39.526650] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [APC5] -> GSI 16 (level, low) -> IRQ 16
[ 39.526658] PCI: Setting latency timer of device 0000:01:00.0 to 64
[ 39.526741] NVRM: loading NVIDIA UNIX x86_64 Kernel Module 100.14.19 Wed Sep 12 14:08:38 PDT 2007
[ 39.551706] usbcore: registered new interface driver xpad
[ 39.551710] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[ 39.694724] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[ 39.694729] ACPI: PCI Interrupt 0000:00:10.1[b] -> Link [AAZA] -> GSI 22 (level, low) -> IRQ 22
[ 39.696800] PCI: Setting latency timer of device 0000:00:10.1 to 64
[ 39.907629] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[ 40.497236] lp0: using parport0 (interrupt-driven).
[ 40.609310] Linux video capture interface: v2.00
[ 40.644858] cx2388x cx88-mpeg Driver Manager version 0.0.6 loaded
[ 40.646435] cx2388x dvb driver version 0.0.6 loaded
[ 40.646437] cx8802_register_driver() ->registering driver type=dvb access=shared
[ 40.717048] Adding 1116476k swap on /dev/sda5. Priority:-1 extents:1 across:1116476k
[ 41.114072] EXT3 FS on sda2, internal journal
[ 42.220269] No dock devices found.
[ 42.227809] input: Power Button (FF) as /class/input/input5
[ 42.227823] ACPI: Power Button (FF) [PWRF]
[ 42.227855] input: Power Button (CM) as /class/input/input6
[ 42.227865] ACPI: Power Button (CM) [PWRB]
[ 43.561795] ppdev: user-space parallel port driver
[ 43.831538] audit(1194889006.416:3): type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5644 profile="/usr/sbin/cupsd"
[ 47.726343] NET: Registered protocol family 10
[ 47.726430] lo: Disabled Privacy Extensions
[ 109.274110] Failure registering capabilities with primary security module.
[ 112.035082] Bluetooth: Core ver 2.11
[ 112.035328] NET: Registered protocol family 31
[ 112.035333] Bluetooth: HCI device and connection manager initialized
[ 112.035336] Bluetooth: HCI socket layer initialized
[ 112.042090] Bluetooth: L2CAP ver 2.8
[ 112.042096] Bluetooth: L2CAP socket layer initialized
[ 112.050216] Bluetooth: RFCOMM socket layer initialized
[ 112.050237] Bluetooth: RFCOMM TTY layer initialized
[ 112.050241] Bluetooth: RFCOMM ver 1.8
[ 114.665024] NET: Registered protocol family 17
[ 189.290116] eth0: no IPv6 routers present
johnwillyums@johnwillyums-desktop:~$

As you can see-no resemblance to what I expected. I read through the missing section and can't see any mention of "dvb" anywhere.
Have I I totally misunderstood?

Thanks, John Williams

my device is slightly different tothe one menioned on page 2. It is a WinTV-NOVA-TD. Looks the same but costs three times as much. Mind you I think I must be misunderstanding your instructions completely. I've got kaffeine installed by the way. J

---

### Post by johnwillyums on 2007-11-12
A further update.
I just tried to configure kaffeine player

If I go to "Enable DVB client" I've got this:

Broadcast address: 192.1.0255

Broadcast port: 1234

Info port: 1235

If I press enable I get a box saying "can't bind info socket !!!"

I'm completely lost.
John Williams

---

### Post by wieman01 on 2007-11-13
> **johnwillyums said:**
> A further update.
I just tried to configure kaffeine player

If I go to "Enable DVB client" I've got this:

Broadcast address: 192.1.0255

Broadcast port: 1234

Info port: 1235

If I press enable I get a box saying "can't bind info socket !!!"

I'm completely lost.
John Williams
I posted on your original thread... Your card has not been recognized yet. Check it out.

---

### Post by johnwillyums on 2007-11-17
Hello wieman, thanks for replying.

I went back to your tutorial and I get the same result as posted above, there is a mention of a dvb device:

[lolflag:[ 40.646435] cx2388x dvb driver version 0.0.6 loaded
[ 40.646437] cx8802_register_driver() ->registering driver type=dvb access=shared
[ 40.717048] Adding 1116476k swap on /dev/sda5. Priority:-1 extents:1 across:1116476k
[ 41.114072] EXT3 FS on sda2, internal journal

This is line 40.646434 onwards for a couple of lines but two thirds of the result are posted above.

I tried disconnecting the device and putting in cd/lib/firmware and I get this:

johnwillyums@johnwillyums-desktop:~$ cd/lib/firmware
bash: cd/lib/firmware: No such file or directory
johnwillyums@johnwillyums-desktop:

There is no mention of a stick in a "cold state" anywhere. As I say the only time dvb is mentioned is as above.

I have downloaded a file called:
dvb-usb-dib0700-03-pre1.fw 

but I don't know what to do with it.

Any suggestions?
thanks, John

---

### Post by wieman01 on 2007-11-17
The folder is there, but you were missing a 'space'... anyway, now do (from the folder to which you have downloaded the firmware file):
> sudo mv dvb-usb-dib0700-03-pre1.fw /lib/firmware/dvb-usb-dib0700-01.fw
Insert the stick and do:
> dmesg
No matter what, please install kaffeine and open it... does it recognize your stick?

---

### Post by johnwillyums on 2007-11-17
Hi wieman, wasn't sure what you meant. The firmware file is on my desktop and wants to open with virus scanner. If I go to other programmes it wants to open in various media applications (players) including kaffeine.

This is what I get if I just type it into terminal:


johnwillyums@johnwillyums-desktop:~$ sudo mv dvb-usb-dib0700-03-pre1.fw /lib/firmware/dvb-usb-dib0700-01.fw 
[sudo] password for johnwillyums:
mv: cannot stat `dvb-usb-dib0700-03-pre1.fw': No such file or directory
johnwillyums@johnwillyums-desktop:~$ 

Should I try opening it in kaffeine?
Also have mythtv frontend and backend but no luck there-see previous post.

Thanks, John

As I already mentioned if I try to configure dvb client in kaffeine I get-"can't bind info socket!!!" J

---

### Post by wieman01 on 2007-11-17
Ok, please open a terminal and change directory to:
> cd Desktop
Then move the file:
> sudo mv dvb-usb-dib0700-03-pre1.fw /lib/firmware/dvb-usb-dib0700-01.fw
And open Kaffeine... I assume that the file is on your Desktop. We have just moved it from there to "/lib/firmware" and renamed it.

Any results? Let me know if that's still not clear enough.

---

### Post by johnwillyums on 2007-11-18
Hi wieman,

Thanks a lot for your continuing support. I got home late last night and saw your suggestion but I think I made a bit of a mess of it and when I looked this morning the folder with the 

`dvb-usb-dib0700-03-pre1.fw'

in it had gone from the desktop so I must have done something right. 
However I opened kaffeine and still got the "can't bind info socket!!!" box when I tried to configure dvb.

So I started again and downloaded another file-dvb-usb-dib0700-03-pre1.fw- to the desktop.

I then tried to follow your instructions-

I opened terminal and put in "cd desktop" and then pressed enter after that I copied and pasted-

sudo mv dvb-usb-dib0700-03-pre1.fw /lib/firmware/dvb-usb-dib0700-01.fw

and pressed enter again. 

This is what I got-

johnwillyums@johnwillyums-desktop:~$ cd Desktop
johnwillyums@johnwillyums-desktop:~/Desktop$ sudo mv dvb-usb-dib0700-03-pre1.fw /lib/firmware/dvb-usb-dib0700-01.fw
mv: cannot stat `dvb-usb-dib0700-03-pre1.fw': No such file or directory
johnwillyums@johnwillyums-desktop:~/Desktop$ 

So no farther forward really. I must be misunderstanding your instruction.
 
However the file `dvb-usb-dib0700-03-pre1.fw' has disappeared from the desktop but when I open kaffeine I get cannot bind info socket and terminal is saying no such file or directory so that's two mysterious disappearances of that file.

I'm missing something basic I feel. 

Thanks, John

---

### Post by wieman01 on 2007-11-18
Don't worry, perhaps I should explain a little more as to what I am trying to achieve...

The "mv" command would move the source file on the Desktop to the directory "/lib/firmware/" and at the same time renames it from "dvb-usb-dib0700-03-pre1.fw" to "dvb-usb-dib0700-01.fw".

We need to copy the file to the said folder and rename it in order for your system to recongize your card. The kernel would look for the appropriate firmware in "/lib/firmware/" first and expects a certain file named "dvb-usb-dib0700-01.fw".

We cannot move any files in that folder without root privileges, hence the "sudo" prefix which gives you administrative rights.

Does that make it a little clearer? So you need to download that file, rename it and move it. Then start up Kaffeine and see if it works.

You can browse that folder with Nautilus and see if the right file is there.

---

### Post by johnwillyums on 2007-11-18
Hi wieman

I think I've followed your instructions to the letter.

I downloaded a fresh "dvb-usb-dib0700-03-pre1.fw" to my desktop and opened File Browser so I could see it.

I then opened terminal (via accessories) and typed in "cd Desktop" and pressed enter.
This gave me the same line with a $  at the end.
I then copied and pasted
"sudo mv dvb-usb-dib0700-03-pre1.fw /lib/firmware/dvb-usb-dib0700-01.fw"
and pressed enter again

This gave me this result in the terminal box:

johnwillyums@johnwillyums-desktop:~$ cd Desktop
johnwillyums@johnwillyums-desktop:~/Desktop$ sudo mv dvb-usb-dib0700-03-pre1.fw /lib/firmware/dvb-usb-dib0700-01.fw
[sudo] password for johnwillyums:
johnwillyums@johnwillyums-desktop:~/Desktop$ 

I should add that I typed my password in on the fourth line and it did not appear. I assume that is normal and correct. 
After that I pressed enter and watched the dvb-usb file disappear from Desktop-File Browser and then the final line appeared. (johnwillyums@johnwillyums-desktop:~/Desktop$)

I then minimised the terminal box and opened kaffeine and tried ,through settings, to configure dvb client.
This gets me a box where I can enable dvb client. I put a cross in the box and get:
  
broadcast address 192.168.0.255
broadcast port 1234
info port 1235
time shifting directory /home/johnwillyums

If I click either ok or apply I get "can't bind info socket!!!" in a box with an ok in it, click that and I'm no further forward.

I assume the file is in there somewhere as I watched it go from File Browser. In fact it's probably in there 2 or 3 times by now.

You mentioned browsing for it with Nautilus. I think I've got that installed but don't know how to access it. I'll make sure and see.

Assuming I can find it what then?

Sorry about this, I did mention I'm a newbie. I'm pretty much a newbie in computers in general so perhaps I've bitten off more than I can chew with this ambitious dual boot with Vista 64x and Gutsy 64x.

Got most things working though so I'm learning. Press on eh?

Thanks so much for your help, John

---

### Post by wieman01 on 2007-11-18
Yes, we won't give up, buddy. :-)

I think you have done every correctly. The mentioned file should now reside in "/lib/firmware".

Could you post a screenshot of Kaffeine right after you have opened it? Just want to see if the adapter is recognized and if you are given a DVB option at all.

You are on 64-bit then? That could be an issue. But let's see,

And what does "dmesg" yield now after inserting the stick?

---

### Post by johnwillyums on 2007-11-18
Hello again.
I just tried what you suggested and got pages of code, The only mention of dvb seems to be around line 50.269305

   49.226907] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   49.435782] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   50.089711] lp0: using parport0 (interrupt-driven).
[   50.205368] Linux video capture interface: v2.00
[   50.242303] cx2388x cx88-mpeg Driver Manager version 0.0.6 loaded
[   50.269305] cx2388x dvb driver version 0.0.6 loaded
[   50.269310] cx8802_register_driver() ->registering driver type=dvb access=shared
[   50.326565] Adding 1116476k swap on /dev/sda5.  Priority:-1 extents:1 across:1116476k
[   50.718419] EXT3 FS on sda2, internal journal
[   53.162042] No dock devices found.

I tried to paste the whole lot in plus 2 screen shots of what happens when I open Kaffeine Player but I got an administrator message saying I had used over 10 images and could only post 8. I went back and deleted the screen shots but it still wouldn't accept it so this is the shortened version.

As soon as I open Kaffeine Player I get the- can't bind info socket!!!- warning. If I okay that I get a small window with options to play, record etc. The sixth box is- DVB Client.
If I click that I get 2 xine messages. The first one tells me that resource cannot be opened because   dvb-usb-dib0700-03-pre1.fw is not there the second one is the same but asks me to check home file.

Hope this is making sense, Cheers, John

---

### Post by wieman01 on 2007-11-18
Ok, last try... Please do this for me:
> sudo cp /lib/firmware/dvb-usb-dib0700-01.fw /lib/firmware/dvb-usb-dib0700-03-pre1.fw
Then insert the stick and fire up Kaffeine. Any better?

---

### Post by johnwillyums on 2007-11-18
Hi wieman

Did as you suggested but got exactly the  same result.

I disconnected the stick and copied and pasted:

sudo cp /lib/firmware/dvb-usb-dib0700-01.fw /lib/firmware/dvb-usb-dib0700-03-pre1.fw

I pressed enter and this got me:

johnwillyums@johnwillyums-desktop:~$ 

I entered my pass
word and this time the type showed (I've deleted it from this post)

And that got me this:

bash:         : command not found
johnwillyums@johnwillyums-desktop:~$ 

So whatever bash is does not recognise my password or is that not what I should have put in?

Don't give up wieman there's got to be something I'm not doing right, John

ps I tried at various stages to open Kafffeine Player and got the same results as before.

also, above, my password comes in between bash and command not found but I deleted it.

---

### Post by wieman01 on 2007-11-18
> **johnwillyums said:**
> So whatever bash is does not recognise my password or is that not what I should have put in?
You have to put in your password once, then it's cached for 15 minutes or so. No problem.

When you do...
> ls -l /lib/firmware
...what's the output?

I'll do a bit more research tomorrow... This is strange.

---

### Post by johnwillyums on 2007-11-18
Hello wieman.
I copied and pasted your suggested command in to terminal, pressed enter (no password) and got this:

johnwillyums@johnwillyums-desktop:~$ ls -l /lib/firmware
total 76
drwxr-xr-x 4 root         root          4096 2007-11-14 07:13 2.6.22-14-generic
-rw-r--r-- 1 johnwillyums johnwillyums 33277 2007-11-18 16:07 dvb-usb-dib0700-01.fw
-rw-r--r-- 1 root         root         33277 2007-11-18 20:10 dvb-usb-dib0700-03-pre1.fw
johnwillyums@johnwillyums-desktop:~$ 


Thanks a lot for sticking with this. I wasn't at all sure about Linux, I barely knew Windows XP and now I'm struggling with Vista 64x., which I've found to be great and rock solid contrary to a lot of posts on various forums.

However I am surprised and amazed at how good Ubuntu is and I'm finding the whole thing fascinating and empowering as well as a steep learning curve.

 So thanks generally. I'm going to bed soon-work tomorrow. No doubt we'll "speak" again then, perhaps the above may throw some light, it looks promising, John

---

### Post by wieman01 on 2007-11-19
Looks fine. Could you post the results of this please (after inserting the stick):
> dmesg | grep dvb
>  ls -l /dev/dvb/adapter*
I also include another link [here]("http://www.wi-bw.tfh-wildau.de/~pboettch/home/linux-dvb-firmware/dvb-usb-dib0700-1.10.fw"). Perhaps these problems are due to an issue with the firmeware, you replacing the one you have downloaded with that one (link) might be a solution. But post your stuff first, we'll see. :-)

Could you also do me a favor and choose another USB port? Maybe the current one is defective, who knows?!

_**EDIT:**_
For my own reference: [http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-Stick]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-Stick")

---

### Post by johnwillyums on 2007-11-19
Good evening wieman.

Thanks for your reply. Sorry but I can't figure out how to do the vertical bar. I can see it on my keyboard- next to number 1 with ¬ and ` on it plus a vertical bar in the bottom right hand corner of the key.
I've tried every combination of keys I can think of but obviously not the right one.

I'll try and look it up on google if I don't hear from you. Cheers, John

---

### Post by johnwillyums on 2007-11-19
Hey Wieman, stupid of me. Can't find how to use that key but have copied and pasted it (doh) and this is the resullt:

johnwillyums@johnwillyums-desktop:~$ dmesg | grep dvb
[   50.316254] cx2388x dvb driver version 0.0.6 loaded
[   50.316256] cx8802_register_driver() ->registering driver type=dvb access=shared
johnwillyums@johnwillyums-desktop:~$ 

I'll try the other command now, Cheers, John

---

### Post by johnwillyums on 2007-11-19
Ok. I added the second command straight after and got this which looks familiar:

johnwillyums@johnwillyums-desktop:~$ dmesg | grep dvb
[   50.316254] cx2388x dvb driver version 0.0.6 loaded
[   50.316256] cx8802_register_driver() ->registering driver type=dvb access=shared
johnwillyums@johnwillyums-desktop:~$ ls -l /dev/dvb/adapter*
ls: /dev/dvb/adapter*: No such file or directory
johnwillyums@johnwillyums-desktop:~$ 

I also changed the usb port as you suggested but bear in mind it works in Vista.

Thanks for your continuing support, John

---

### Post by wieman01 on 2007-11-19
Good evening John, 

This does not look too promising and yet, there is a driver that has been loaded. "ls -l /dev/dvb/adapter*" yields no results at all which is also bad news. 

Now let's try something else (installing 'kdetv'):
> sudo apt-get install kdetv
Then start the application:
> kdetv
That's another TV application. Would this one recognize your device?

By the way... are you on 64-bit?

---

### Post by johnwillyums on 2007-11-19
Hello wieman. 

I just got in and have to sleep now so will wait until tomorrow to try KDE.

In answer to your question yes I am dual booting Vista Home Premium and Ubuntu 7.10 both in 64 bit.

My system is brand new and as follows- Intel Q6600, Asus P5N-E SLI mobo, 4GB DDR2 ram, nVidia 8600GT and 500GB SATA hard drive.

The 64 bit was also a problem in Vista. Basically I could not use Hauppauge supplied software but had to download another driver and I can therefore only use it through Windows Media Centre.

It,s a while back I did it so it's a bit hazy but I do recall it was much simpler than this is. 
I've only had the system about 9 weeks and it's been a busy time. as I said I'm not really techy and did'nt have to be with a XP install on my old machine which had been set up in every way by a friend who has since gone abroad.
 I just did what I needed and didn't really think about any other software. Heard about Linux though and the whole philosophy intrigued me plus it just seems the natural way things are going and reviews and screenshots looked great.
I tried wubi and a live disk install of feisty but it wouldn't boot and after loads of help on the wubi forum the general opinion seemed to be a hardware incompatibilty. This seemed likely as I had had had all sorts of problems with the old recycled machine.
Anyway, have gone into debt to get this new machine and I'm loving it.
I've got most of both Vista and Ubuntu running as I want but there are still glitches in Ubuntu and a few thing I have to go to Vista for but I'm having a great time learning a bit more about computers and I can play music and watch movies.
It would be nice to sack MS altogether and I think I will over the next couple of years but at the moment I need Photoshop and The Gimp looks a bit clunky. Maybe I'll get used to it,
Sorting out the photography side of things will be my next aim after the dvb stuff.

Your support is really apprecciated,John

---

### Post by wieman01 on 2007-11-20
Hello John, 

Yes, making the move to Linux can be a bit of a pain but the effort is well rewarded. I have not touched Windows at home for ages as I found a substitutes for every single piece of software that I used to use. I know Photoshop is a tough one, but Gimp is making progress every day so one day you might get to like it just as much.

Having said that, 64-bit might be the root cause of our problems. Frankly there is not much else I can say or do. You may want to post your request in the 64-bit support section, there are very skilled & nice people there who could join in and help. 

The last resort would be to consider a new DVB adapter such as the one I have got (Hauppauge WinTV-Nova-T Stick). But in that case you would have to spend another 30 EUR or so (what's that in GBP?) and there is no guarantee it will work on a 64-bit system.

If 64-bit gives you much headache you could also consider installing the 32-bit version of Ubuntu which is by all means possible. That way you would avoid a number of issues and could focus on more productive things such as finding the right replacements for beloved Windows programs. :-)

_**EDIT:**_
That's a hell-of-a machine you have got there!

---

### Post by harryman01 on 2007-11-21
> **Mr. Mulder said:**
> Bump (if that's allowed here?)  :confused:

Hi "Mr. Mulder"

I got similar problem, and also I'm in UK, my card and Kafeine don't pickup any signal at all, even if I use a signal booster, and connected to the aerial

so far I'm not usign KDE, I'm using gnome (but really this not is an issue)

also I had to buy other antennas and nothing!!

---

### Post by johnwillyums on 2007-11-23
wie gehts wieman ?( I do hope I am right in assuming you are von Deutschland).

I haven't posted for a few days as I've been away.

Regarding my problem I think you are right. 64 bit is difficult at present, both in Linux and Windows.
However it is blisteringly fast.
My previous pc was no slouch- pentium D, gig of ram, geforce 7900 etc. but the new one was a revelation when I first got it with a 64 bit Vista install.
It seemed to leave the old one in the stone age. Obviously this is a combination of new machine and os but it was incredibly fast.

Now when I go back into Vista from Ubuntu it seems so slow  I think I've got a malware problem or something. I haven't.It's just much slower than 64x Ubuntu.

I am reluctant to give up on either Ubuntu or 64 bit but the problems are endless.

Initially I was using the Firefox browser that comes with the package but couldn't get flash videos to play-my space, metacafe etc.

Then I discovered 64 bit Swiftweasel and it was amazing. Much faster than the regular Firefox and it played flash.
However earlier this week I got a downloadable update from Swiftweasel. Guess what? No more flash.
And so it goes on.
However I am determined not to give up and Ubuntu looks better, works better and is much faster than Vista.

With regard to my stick. The TD version I have cost 80 GBP, the T version you mention costs 30 GBP. This is a rip off in terms of the exchange rate but we are used to that. An item that retails for 200 US Dollars goes for 200 GBP in the UK, it should sell for half that.

Anyway, I can't really afford it at the moment and I'm not sure it would make any difference as I get the feeling that my stick is being recognised as a T anyway

With regard to KDE TV. Do you think it might make  a difference? I'm mostly Gnome at the moment, would it not mean some kind of conversion to Kubuntu?

Most of my apps in Vista are 32 bit and I've got several 32 bit applications in Ubuntu- Firefox 32, Skype 32 and Sun Java6.
Therefore would it make much difference to re-install a 32 bit Ubuntu?
I don't really want to do that anyway and hopefully more 64 bit apps for both Windows and Linux are in the pipeline.

Harryman. Thanks for your input. Are you getting anywhere? I posted on Hauppauge's web forum ages ago (several weeks) and I just checked and nobody has replied at all! So no help there.
Perhaps it just can't be done at the moment.
I don't understand the reference to "Mr Mulder"

I checked out the 64x forum and it all seemed pretty high level stuff. I don't have the heart right now to start over again ,having to go through the whole thing etc. 

I'll probably feel differently in a few weeks and start again on that forum but at the moment I'll just go back to Vista to watch TV.
I have to go back there for my photography anyway as I can't find a way to get a good photo print out of my Canon i9950 in Ubuntu.

Wieman,I very much appreciate the amount of time and thought you have put in to helping me and I quite understand that you gone as far as you can.

So, thanks once again and I hope you and your family have a good Christmas.

Best Wishes, John Williams

---

### Post by wieman01 on 2007-11-23
Hello John, 

Nice to hear from you. Hope weather isn't as awful over there in the UK as it is here. Has been pouring here like there is no tomorrow. Mir geht's sehr gut. :-)

I understand that "downgrading" to 32-bit would be quite a step backwards, and I am sure you will be able to tackle all your problems with a bit of persistence & effort in the end. But be aware of the drawbacks and potential stumbling blocks it might entail. I reckon the 64-bit section is full of such issues.

As for the WinTV device, I have no further advice indeed. But having said that you could still try out KDE-TV which is in the repositories. I don't think there is a need to install KDE for it as Gnome is capable of dealing with KDE apps. Just check it out, you won't break anything. So no, you don't really need to convert to KDE.

Another thought... Why don't you install Ubuntu 32-bit in dual boot mode? Just for testing purposes and to see how you go. Perhaps performance isn't as bad as you think.

Have a nice day, John.

---

### Post by Pigeon. on 2008-01-13
Not working in Gutsy fluxbuntu using the firmware listed earlier in this thread.

dmesg gives:

```
Jan 14 04:41:36 pindix kernel: [24862.164739] usb 3-1: new high speed USB device using ehci_hcd and address 8
Jan 14 04:41:36 pindix kernel: [24862.297673] usb 3-1: configuration #1 chosen from 1 choice
Jan 14 04:41:36 pindix kernel: [24862.298036] dvb-usb: found a 'Hauppauge Nova-T Stick' in cold state, will try to load a firmware
Jan 14 04:41:36 pindix kernel: [24862.414526] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-01.fw'
Jan 14 04:41:37 pindix kernel: [24862.610695] dib0700: firmware started successfully.
Jan 14 04:41:37 pindix kernel: [24863.111834] dvb-usb: found a 'Hauppauge Nova-T Stick' in warm state.
Jan 14 04:41:37 pindix kernel: [24863.111927] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Jan 14 04:41:37 pindix kernel: [24863.112434] DVB: registering new adapter (Hauppauge Nova-T Stick).
Jan 14 04:41:37 pindix kernel: [24863.365197] DVB: registering frontend 0 (DiBcom 7000PC)...
Jan 14 04:41:37 pindix kernel: [24863.368822] MT2060: successfully identified (IF1 = 1220)
Jan 14 04:41:38 pindix kernel: [24863.846444] dvb-usb: Hauppauge Nova-T Stick successfully initialized and connected.

```

But there is a missing frontend1 in /dev/dvb:

```
pigeon@pindix:~/fluxbuntu$ ls -al /dev/dvb
total 0
drwxr-xr-x  3 root root    60 Jan 14 04:05 .
drwxr-xr-x 13 root root 14200 Jan 14 04:05 ..
drwxr-xr-x  2 root root   120 Jan 14 04:05 adapter0
pigeon@pindix:~/fluxbuntu$ ls -al /dev/dvb/adapter0
total 0
drwxr-xr-x 2 root root     120 Jan 14 04:05 .
drwxr-xr-x 3 root root      60 Jan 14 04:05 ..
crw-rw---- 1 root video 212, 4 Jan 14 04:05 demux0
crw-rw---- 1 root video 212, 5 Jan 14 04:05 dvr0
crw-rw---- 1 root video 212, 3 Jan 14 04:05 frontend0
crw-rw---- 1 root video 212, 7 Jan 14 04:05 net0
pigeon@pindix:~/fluxbuntu$ lsusb
Bus 003 Device 007: ID 2040:7060 Hauppauge 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

```

kaffeine gives:

```

/dev/dvb/adapter0/frontend0 : opened ( DiBcom 7000PC )
/dev/dvb/0/frontend1 : : No such file or directory
Loaded epg data : 0 events (13 msecs)
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
DvbCam::probe(): /dev/dvb/adapter0/ca0: : No such file or directory

```

For channels with no signal we get:
```

Using DVB device 0:0 "DiBcom 7000PC"
tuning DVB-T to 402000000 Hz
inv:2 bw:0 fecH:9 fecL:9 mod:6 tm:2 gi:4 hier:4
...............

Not able to lock to the signal on the given frequency
Frontend closed
dvbsi: Cant tune DVB

```

and where there is a signal:

```

Using DVB device 0:0 "DiBcom 7000PC"
tuning DVB-T to 514000000 Hz
inv:2 bw:0 fecH:9 fecL:9 mod:6 tm:2 gi:4 hier:4
. LOCKED.
Transponders: 15/63

Invalid section length or timeout: pid=17

Frontend closed

```

It seems to be the "Invalid section length or timeout: pid=17" which is the killer, and nobody, or at least nobody googleable, seems to have a solution...

and i **NEED** this working by Tuesday evening, there is no way around that requirement, it **HAS** to be working by 9pm on Tuesday evening.

Help please!!!

---

### Post by wieman01 on 2008-01-14
**@Pigeon:**

What version of Nova-T Stick have you got? I think there is a version number printed on the back of the device. Could you check please?

Have you tried any other TV application? Everything should be ok because 'dmseg' says the device has been connected and recognized.

Did Kaffeine install new packages after you had inserted the device?

---

### Post by ebe0 on 2008-01-14
I know this thread is for WinTV-Nova-T Stick, however could you please help me with [COLOR="Blue"]hauppauge WinTV-USB2-Stick[/COLOR] -- [http://www.hauppauge.com.sg/web-content/pages/products/data_usb2Stick.html](http://www.hauppauge.com.sg/web-content/pages/products/data_usb2Stick.html)

Got the following output
lsusb :
Device 004: ID 2040:650a Hauppauge 

dmesg:
usb 3-2: new high speed USB device using ehci_hcd and address 4
usb 3-2: configuration #1 chosen from 1 choice

Is there a driver for this? I'm not able to use this in Kaffeine.
Thanks in advance.

---

### Post by wieman01 on 2008-01-14
I find your device here:

[http://linuxtv.org/v4lwiki/index.php/Hauppauge]("http://linuxtv.org/v4lwiki/index.php/Hauppauge")

*Quoting:*
> Supported by the em28xx driver
The project site with instructions is here (how to install the driver, etc.):

[http://mcentral.de/wiki/index.php5/Em2820]("http://mcentral.de/wiki/index.php5/Em2820")

Please feel free to post here if you run into problems. But try yourself first.

---

### Post by Pigeon. on 2008-01-14
> **wieman01 said:**
> What version of Nova-T Stick have you got? I think there is a version number printed on the back of the device. Could you check please?
The sticker on the back says:

M/R:70009/C1B5 #4807
000DFE3D5CC0         LF

> **wieman01 said:**
> Have you tried any other TV application? Everything should be ok because 'dmseg' says the device has been connected and recognized.

I found a tuning file at [http://linvdr.org/mailinglists/vdr/2004/10/msg00236.html](http://linvdr.org/mailinglists/vdr/2004/10/msg00236.html) containing the following data for my local transmitter, Bromsgrove:

```
T 578000000 8MHz 3/4 NONE QAM16 2K 1/32 NONE
```

along with the advice to experiment if necessary by changing QAM16 to QAM64, and 3/4 to 1/2. So I generated this:

```

T 578000000 8MHz 3/4 NONE QAM16 2K 1/32 NONE
T 578000000 8MHz 3/4 NONE QAM64 2K 1/32 NONE
T 578000000 8MHz 1/2 NONE QAM16 2K 1/32 NONE
T 578000000 8MHz 1/2 NONE QAM64 2K 1/32 NONE

```

Using scan -vvv from dvb-utils with that data **almost always** gives:

```

$ scan -vvv uk-Bromsgrove.expt
scanning uk-Bromsgrove.expt
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
ERROR: invalid enum value '2K'
initial transponder 578000000 0 3 9 1 2 0 0
ERROR: invalid enum value '2K'
initial transponder 578000000 0 3 9 3 2 0 0
ERROR: invalid enum value '2K'
initial transponder 578000000 0 1 9 1 2 0 0
ERROR: invalid enum value '2K'
initial transponder 578000000 0 1 9 3 2 0 0
>>> tune to: 578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE
>>> tuning status == 0x1b
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
>>> tune to: 578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE
>>> tuning status == 0x1a
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
>>> tune to: 578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_1_2:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE
>>> tuning status == 0x1a
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
>>> tune to: 578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_1_2:FEC_AUTO:QAM_64:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE
>>> tuning status == 0x1a
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
dumping lists (0 services)
Done.

```

but on one occasion, which I cannot get it to repeat, I got:

```

$ scan -vvv uk-Bromsgrove.expt
scanning uk-Bromsgrove.expt
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
ERROR: invalid enum value '2K'
initial transponder 578000000 0 3 9 1 2 0 0
ERROR: invalid enum value '2K'
initial transponder 578000000 0 3 9 3 2 0 0
ERROR: invalid enum value '2K'
initial transponder 578000000 0 1 9 1 2 0 0
ERROR: invalid enum value '2K'
initial transponder 578000000 0 1 9 3 2 0 0
>>> tune to: 578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE
>>> tuning status == 0x1a
parse_section:1160: pid 0x00 tid 0x00 table_id_ext 0x9535, 208/15 (version 29)
PAT
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x13cb
WARNING: filter timeout pid 0x1a84
WARNING: filter timeout pid 0x1181
WARNING: filter timeout pid 0x1393
WARNING: filter timeout pid 0x0ae0
WARNING: filter timeout pid 0x1fe1
WARNING: filter timeout pid 0x0d3a
WARNING: filter timeout pid 0x1ed3
WARNING: filter timeout pid 0x0002
WARNING: filter timeout pid 0x0698
WARNING: filter timeout pid 0x1a6b
WARNING: filter timeout pid 0x03a5
WARNING: filter timeout pid 0x14b2
WARNING: filter timeout pid 0x1d15
WARNING: filter timeout pid 0x00ea
WARNING: filter timeout pid 0x0038
WARNING: filter timeout pid 0x03f3
WARNING: filter timeout pid 0x0190
WARNING: filter timeout pid 0x0cf8
WARNING: filter timeout pid 0x11d0
WARNING: filter timeout pid 0x04b5
WARNING: filter timeout pid 0x0a1a
WARNING: filter timeout pid 0x0db5
WARNING: filter timeout pid 0x13a9
WARNING: filter timeout pid 0x127b
WARNING: filter timeout pid 0x1a74
WARNING: filter timeout pid 0x0a84
WARNING: filter timeout pid 0x027c
WARNING: filter timeout pid 0x0618
WARNING: filter timeout pid 0x18cb
WARNING: filter timeout pid 0x0fe4
WARNING: filter timeout pid 0x0010
>>> tune to: 578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE
>>> tuning status == 0x1a
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
>>> tune to: 578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_1_2:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE
>>> tuning status == 0x1a
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
>>> tune to: 578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_1_2:FEC_AUTO:QAM_64:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE
>>> tuning status == 0x1a
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
dumping lists (31 services)
[37a7]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:14247
[ae09]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:44553
[4686]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:18054
[a12f]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:41263
[442c]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:17452
[cf92]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:53138
[b7a1]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:47009
[ab51]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:43857
[87c4]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:34756
[1601]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:5633
[e80e]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:59406
[1586]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:5510
[0bdf]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:3039
[d140]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:53568
[c5ce]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:50638
[ca84]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:51844
[ee84]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:61060
[253a]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:9530
[c0e9]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:49385
[13f0]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:5104
[66b6]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:26294
[7e34]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:32308
[f3b6]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:62390
[8d28]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:36136
[4d8b]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:19851
[8480]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:33920
[9339]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:37689
[54d1]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:21713
[9485]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:38021
[4f32]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:20274
[1800]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:6144
Done.

```

If I stick this data in ~/.kde/share/apps/kaffeine/channels.dvb I now get a list of channels in kaffeine, and console output like this when I try to tune to them:

```

Tuning to: [37a7]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:14247 / autocount: 0
Tuning to: [37a7]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:14247 / autocount: 0
Tuning to: [37a7]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:14247 / autocount: 0
Tuning to: [37a7]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:14247 / autocount: 0
Tuning to: [37a7]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:14247 / autocount: 0
Tuning to: [9485]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:38021 / autocount: 0
Tuning to: [66b6]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:26294 / autocount: 0
Tuning to: [37a7]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:14247 / autocount: 0
Tuning to: [37a7]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:14247 / autocount: 0
Tuning to: [37a7]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:14247 / autocount: 0
Tuning to: [37a7]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:14247 / autocount: 0
Tuning to: [37a7]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:14247 / autocount: 0
Tuning to: [37a7]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:14247 / autocount: 0
Tuning to: [4f32]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:20274 / autocount: 0
Tuning to: [253a]:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:9530 / autocount: 0

```

However I do not get any video output, just a blank black screen.

I have also now got in /var/log/syslog a period of about 30 seconds, apparently corresponding to my attempts to tune into those channels with kaffeine, a bunch of messages "mt2060 I2C read failed". There is nothing of that kind corresponding with my experiments with scan -vvv.


That is my progress up to the point of writing. :)

I have also tried klear but it (a) says it doesn't support scanning and (b) refuses to parse the above channel list, so it's not very helpful.

> **wieman01 said:**
> Did Kaffeine install new packages after you had inserted the device?

No, not a thing.

---

### Post by wieman01 on 2008-01-14
**@Pigeon:**

Please take a look at this site (once again) and check if you have missed something...

[http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-Stick]("http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-Stick")

What does "kernel.log" after you have scanned for channels?

---

### Post by Pigeon. on 2008-01-14
**FIRMWARE** :D :D :D

The file [http://www.wi-bw.tfh-wildau.de/~pboettch/home/linux-dvb-firmware/dvb-usb-dib0700-1.10.fw](http://www.wi-bw.tfh-wildau.de/~pboettch/home/linux-dvb-firmware/dvb-usb-dib0700-1.10.fw) did the trick, once I had symlinked it to dvb-usb-dib0700-01.fw (it wouldn't work under the original filename).

That's about the fourth firmware I've found for this stick but the first one that worked :D - so many references on Google led to wiki pages that had been (most unhelpfully) entirely deleted, others led to dysfunctional firmwares...

In particular I think it may be useful to point out that the firmware linked off the first page of this thread does NOT work.

It may be of use to others to note that most of the wrong firmwares led kaffeine to lie about the signal level and report 99% for any kind of signal above about 8%. Now I've got a working firmware it is giving more realistic readings, around 30% which seems reasonable for the antenna I'm using - home made 8-director Yagi mounted indoors - upgrading to a rooftop antenna is the next step, I think.

It hasn't yet detected Nuts TV, though, which is the raison d'etre of the whole thing - to record Lucy Pinder's debut as a television presenter - will try again after 9pm when it is on air, perhaps it's simply not picking it up because it's in "data channel" mode at the moment? Comments?

If it picks up Nuts TV I will count the project a success :D

There is nothing in any of the kernel log files after scanning.

On several frequencies I'm still getting "LOCKED" followed by "Invalid section length or timeout: pid=17" with no channels detected, but also on those frequencies the signal level is extremely low, which again says to me the next step is to try a rooftop antenna. The frequencies concerned are all in the middle to upper part of the band, and so must be coming from a more distant transmitter than Bromsgrove, perhaps from Sutton Coldfield (which is in more or less the same direction but at about five times the distance and not in line of sight). Or is this firmware still not 100%? Comments?


THANK YOU SO MUCH :D

---

### Post by Pigeon. on 2008-01-14
OK - It does pick up Nuts TV... it just doesn't behave exactly as I expect it to when Nuts TV is off air. With a cheapie Tesco freeview box, when Nuts TV is off air the OSD displays "DATA CHANNEL" and there is a banner on screen informing you that the channel is only on air from 9pm-1am. The kaffeine/WinTV-Nova-T Stick combination does not do this, there is no banner and no OSD. Once Nuts TV goes off air there is only a blank black screen; if you switch to another channel which is still on-air and then back to the off-air Nuts TV, kaffeine displays a frozen image of the last frame it saw of the other channel. I'll try tomorrow with some other apps before it comes on air again.

Also the SNR bargraph in kaffeine's Channels dialog remains resolutely at 0% no matter what, but I can live with that.

Project saved. Thanks again for your help, you have saved my life.

---

### Post by wieman01 on 2008-01-15
> **Pigeon. said:**
> Project saved. Thanks again for your help, you have saved my life.
You are welcome. Although I could not contribute much, sometimes you just need to sit in front of the computer and do stuff on your own. It's close to impossible to judge from here what could be going wrong. 

I installed WinTV-Nova-T Stick on another Feisty system yesterday and it wasn't oh-so smooth at all. Nothing to do with the firmware, etc. but Kaffeine which would display any TV programs because there was a library missing. But I could fix it, despite the fact that it took me an hour or so figuring out what the issue was.

---

### Post by john0dean on 2008-03-08
I just wanted to say that I've used the information in this thread to get my Hauppauge WinTv - Nova T USB Stick working on my Toshiba Laptop running Kubuntu 7.10. Although in Swindon we can't get all the Freeview channels until the digital switch over in 2011, I have managed to pick up the channels that are available in the area from the Oxford transmitter.

It is working really well. 

Thanks  to everyone who has contributed.

---

### Post by nandasunu on 2008-03-13
just want to say thanks! I've got an Elgato EyeTV DVB-T Stick for Mac, it seems to just be a Hauppagge in disguise, this worked great.

---

### Post by wieman01 on 2008-03-13
No problems. Glad this helps someone else. I was not so sure in the beginning... :-)

---

### Post by diego1188 on 2008-03-30
Hi. After following the instructions the Nova-T works perfectly.
Anyway, none of the two webcams that I have, which used to work without problems, now don't work anymore. When I plug them into the usb port, instead of getting some /dev/video0, /dev/video1 devices I get some /dev/usbdev1.**ep0*, and they are not detected by apps that use webcam devices.
The led on the webcam remains lighted up, instead of lighting up just when an application uses the webcam. 
Any suggestion?

---

### Post by chandolin on 2008-05-21
Hi Wieman01, 

you seem to be an expert with the WinTV nova stick, and I would be very grateful if you could help me (please excuse my english: my mother tongue is french). 

I have Ubuntu 8.10, and a nova stick usb 2.0, and if I look at you how-to and do this: 
dmesg
I receive: 

```
[    0.000000] Linux version 2.6.24-16-386 (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 Thu Apr 10 12:50:06 UTC 2008 (Ubuntu 2.6.24-16.30-386)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffd0000 (usable)
[    0.000000]  BIOS-e820: 000000003ffd0000 - 000000003ffde000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ffde000 - 0000000040000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed13000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 262096) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262096
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262096
[    0.000000] On node 0 totalpages: 262096
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32465 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7D40 checksum 0
[    0.000000] ACPI: RSDP 000F7D40, 0014 (r0 MSI   )
[    0.000000] ACPI: RSDT 3FFD0000, 003C (r1 MSI    1032      8012005 MSFT       97)
[    0.000000] ACPI: FACP 3FFD0200, 0084 (r2 MSI    1032      8012005 MSFT       97)
[    0.000000] ACPI: DSDT 3FFD0430, 393E (r1    MSI 1032      8012005 INTL  2002026)
[    0.000000] ACPI: FACS 3FFDE000, 0040
[    0.000000] ACPI: APIC 3FFD0390, 0054 (r1 MSI    1032      8012005 MSFT       97)
[    0.000000] ACPI: MCFG 3FFD03F0, 003C (r1 MSI    1032      8012005 MSFT       97)
[    0.000000] ACPI: OEMB 3FFDE040, 0053 (r1 MSI    1032      8012005 MSFT       97)
[    0.000000] ACPI: MCFG 3FFD3D70, 003C (r1 MSI    1032      8012005 MSFT       97)
[    0.000000] ACPI: SSDT 3FFD3DB0, 03B9 (r1    AMI   CPU1PM        1 INTL  2002026)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:13 APIC version 20
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 260049
[    0.000000] Kernel command line: root=UUID=59cf5b7b-0831-4969-9c8b-26933a1ce493 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1862.621 MHz processor.
[    9.475712] Console: colour VGA+ 80x25
[    9.475716] console [tty0] enabled
[    9.476056] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    9.476485] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    9.502461] Memory: 1026752k/1048384k available (2067k kernel code, 20904k reserved, 968k data, 360k init, 130880k highmem)
[    9.502468] virtual kernel memory layout:
[    9.502469]     fixmap  : 0xfffa6000 - 0xfffff000   ( 356 kB)
[    9.502470]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    9.502472]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    9.502473]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    9.502474]       .init : 0xc03fa000 - 0xc0454000   ( 360 kB)
[    9.502475]       .data : 0xc0304fb4 - 0xc03f73a4   ( 968 kB)
[    9.502476]       .text : 0xc0100000 - 0xc0304fb4   (2067 kB)
[    9.502479] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    9.502516] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    9.582426] Calibrating delay using timer specific routine.. 3728.00 BogoMIPS (lpj=7456013)
[    9.582448] Security Framework initialized
[    9.582455] SELinux:  Disabled at boot.
[    9.582466] AppArmor: AppArmor initialized
[    9.582469] Failure registering capabilities with primary security module.
[    9.582475] Mount-cache hash table entries: 512
[    9.582574] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000 00000000 00000000
[    9.582585] CPU: L1 I cache: 32K, L1 D cache: 32K
[    9.582588] CPU: L2 cache: 2048K
[    9.582590] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002040 00000180 00000000 00000000 00000000
[    9.582596] Compat vDSO mapped to ffffe000.
[    9.582606] CPU: Intel(R) Pentium(R) M processor 1.86GHz stepping 08
[    9.582610] Checking 'hlt' instruction... OK.
[    9.599864] Freeing SMP alternatives: 0k freed
[    9.599962] Early unpacking initramfs... done
[    9.953067] ACPI: Core revision 20070126
[    9.953119] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   10.051602] ENABLING IO-APIC IRQs
[   10.051769] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   10.197708] net_namespace: 64 bytes
[   10.197719] Booting paravirtualized kernel on bare hardware
[   10.198135] Time: 14:27:12  Date: 05/18/08
[   10.198156] NET: Registered protocol family 16
[   10.198308] EISA bus registered
[   10.198329] ACPI: bus type pci registered
[   10.198510] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=4
[   10.198512] PCI: Using configuration type 1
[   10.198513] Setting up standard PCI resources
[   10.208992] ACPI: EC: Look up EC in DSDT
[   10.210577] ACPI: Interpreter enabled
[   10.210580] ACPI: (supports S0 S3 S4 S5)
[   10.210591] ACPI: Using IOAPIC for interrupt routing
[   10.213106] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   10.218873] ACPI: EC: GPE = 0x1d, I/O: command/status = 0x66, data = 0x62
[   10.218876] ACPI: EC: driver started in interrupt mode
[   10.218950] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   10.219360] Force enabled HPET at base address 0xfed00000
[   10.219365] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   10.219369] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   10.219835] PCI: Transparent bridge - 0000:00:1e.0
[   10.219920] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   10.220031] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   10.220091] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[   10.225937] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 5 6 7 *10 11 12 14 15)
[   10.226028] ACPI: PCI Interrupt Link [LNKB] (IRQs *4 5 6 7 10 11 12 14 15)
[   10.226117] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 5 6 *7 10 11 12 14 15)
[   10.226205] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 *5 6 7 10 11 12 14 15)
[   10.226297] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 5 *6 7 10 11 12 14 15)
[   10.226386] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 *5 6 7 10 11 12 14 15)
[   10.226474] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 *5 6 7 10 11 12 14 15)
[   10.226563] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 5 6 7 10 *11 12 14 15)
[   10.226651] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  85, should be 83 [20070126]
[   10.226658] Linux Plug and Play Support v0.97 (c) Adam Belay
[   10.226682] pnp: PnP ACPI init
[   10.226688] ACPI: bus type pnp registered
[   10.227966] pnp: PnP ACPI: found 12 devices
[   10.227968] ACPI: ACPI bus type pnp unregistered
[   10.227971] PnPBIOS: Disabled by ACPI PNP
[   10.228135] PCI: Using ACPI for IRQ routing
[   10.228137] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   10.241559] NET: Registered protocol family 8
[   10.241561] NET: Registered protocol family 20
[   10.241698] hpet clockevent registered
[   10.241703] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   10.241706] hpet0: 3 64-bit timers, 14318180 Hz
[   10.242733] AppArmor: AppArmor Filesystem Enabled
[   10.245531] Time: tsc clocksource has been installed.
[   10.253549] system 00:01: iomem range 0xfed13000-0xfed19fff could not be reserved
[   10.253556] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   10.253558] system 00:08: ioport range 0x800-0x87f has been reserved
[   10.253561] system 00:08: ioport range 0x400-0x41f has been reserved
[   10.253563] system 00:08: ioport range 0x480-0x4bf has been reserved
[   10.253566] system 00:08: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   10.253569] system 00:08: iomem range 0xfed20000-0xfed8ffff has been reserved
[   10.253572] system 00:08: iomem range 0xffb00000-0xffbfffff has been reserved
[   10.253576] system 00:09: iomem range 0xfec00000-0xfec00fff has been reserved
[   10.253579] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
[   10.253582] system 00:09: iomem range 0xd0000-0xdffff could not be reserved
[   10.253584] system 00:09: iomem range 0xfff80000-0xffffffff could not be reserved
[   10.253589] system 00:0a: iomem range 0xe0000000-0xefffffff could not be reserved
[   10.253594] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[   10.253596] system 00:0b: iomem range 0xc0000-0xcffff could not be reserved
[   10.253599] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[   10.253602] system 00:0b: iomem range 0x100000-0x3fffffff could not be reserved
[   10.253604] system 00:0b: iomem range 0x0-0x0 could not be reserved
[   10.283878] PCI: Bridge: 0000:00:01.0
[   10.283880]   IO window: disabled.
[   10.283883]   MEM window: f9000000-fbefffff
[   10.283885]   PREFETCH window: d0000000-dfffffff
[   10.283902] PCI: Bus 3, cardbus bridge: 0000:02:04.0
[   10.283904]   IO window: 0000e000-0000e0ff
[   10.283907]   IO window: 0000e400-0000e4ff
[   10.283911]   PREFETCH window: 50000000-53ffffff
[   10.283914]   MEM window: 54000000-57ffffff
[   10.283918] PCI: Bus 4, cardbus bridge: 0000:02:04.1
[   10.283920]   IO window: 0000ec00-0000ecff
[   10.283923]   IO window: 00001000-000010ff
[   10.283927]   PREFETCH window: 58000000-5bffffff
[   10.283931]   MEM window: 5c000000-5fffffff
[   10.283934] PCI: Bridge: 0000:00:1e.0
[   10.283936]   IO window: e000-efff
[   10.283940]   MEM window: fbf00000-fbffffff
[   10.283943]   PREFETCH window: disabled.
[   10.283956] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   10.283960] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   10.283968] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   10.283979] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 19 (level, low) -> IRQ 17
[   10.283993] ACPI: PCI Interrupt 0000:02:04.1[b] -> GSI 20 (level, low) -> IRQ 18
[   10.284002] NET: Registered protocol family 2
[   10.321469] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   10.321657] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   10.322422] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[   10.322661] TCP: Hash tables configured (established 131072 bind 65536)
[   10.322663] TCP reno registered
[   10.333539] checking if image is initramfs... it is
[   10.744846] Switched to high resolution mode on CPU 0
[   11.030474] Freeing initrd memory: 8090k freed
[   11.031010] audit: initializing netlink socket (disabled)
[   11.031027] audit(1211120832.332:1): initialized
[   11.031174] highmem bounce pool size: 64 pages
[   11.032734] VFS: Disk quotas dquot_6.5.1
[   11.032756] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   11.032890] io scheduler noop registered
[   11.032892] io scheduler anticipatory registered
[   11.032894] io scheduler deadline registered
[   11.032904] io scheduler cfq registered (default)
[   11.032974] Boot video device is 0000:01:00.0
[   11.033067] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   11.033093] assign_interrupt_mode Found MSI capability
[   11.033118] Allocate Port Service[0000:00:01.0:pcie00]
[   11.033300] isapnp: Scanning for PnP cards...
[   11.386545] isapnp: No Plug & Play device found
[   11.408945] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   11.409440] ACPI: PCI Interrupt 0000:00:1e.3[b] -> GSI 20 (level, low) -> IRQ 18
[   11.409448] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[   11.409936] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   11.409997] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   11.410073] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   11.410508] i8042.c: Detected active multiplexing controller, rev 1.1.
[   11.410562] serio: i8042 KBD port at 0x60,0x64 irq 1
[   11.410565] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   11.410567] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   11.410570] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   11.410572] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   11.415946] mice: PS/2 mouse device common for all mice
[   11.416033] EISA: Probing bus 0 at eisa.0
[   11.416039] Cannot allocate resource for EISA slot 1
[   11.416058] EISA: Detected 0 cards.
[   11.416061] cpuidle: using governor ladder
[   11.416186] NET: Registered protocol family 1
[   11.416211] Using IPI Shortcut mode
[   11.416241] registered taskstats version 1
[   11.416328]   Magic number: 8:755:485
[   11.416415] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   11.416417] EDD information not available.
[   11.416607] Freeing unused kernel memory: 360k freed
[   11.419617] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   12.598602] fuse init (API version 7.9)
[   12.619565] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[   12.619570] ACPI: Processor [CPU1] (supports 8 throttling states)
[   12.622627] ACPI Exception (thermal-0471): AE_NOT_FOUND, Invalid active threshold [0] [20070126]
[   12.624268] ACPI: Thermal Zone [THRM] (52 C)
[   12.640412] device-mapper: uevent: version 1.0.3
[   12.640448] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   12.657555] md: linear personality registered for level -1
[   12.662025] md: multipath personality registered for level -4
[   12.666252] md: raid0 personality registered for level 0
[   12.671222] md: raid1 personality registered for level 1
[   12.675349] xor: automatically using best checksumming function: pIII_sse
[   12.693963]    pIII_sse  :  4807.000 MB/sec
[   12.693965] xor: using function: pIII_sse (4807.000 MB/sec)
[   12.695573] async_tx: api initialized (async)
[   12.761960] raid6: int32x1    626 MB/s
[   12.829830] raid6: int32x2    723 MB/s
[   12.897701] raid6: int32x4    641 MB/s
[   12.965591] raid6: int32x8    510 MB/s
[   13.033483] raid6: mmxx1     1780 MB/s
[   13.101385] raid6: mmxx2     2187 MB/s
[   13.169318] raid6: sse1x1    1360 MB/s
[   13.237186] raid6: sse1x2    2251 MB/s
[   13.305105] raid6: sse2x1    2438 MB/s
[   13.372992] raid6: sse2x2    2728 MB/s
[   13.372994] raid6: using algorithm sse2x2 (2728 MB/s)
[   13.372996] md: raid6 personality registered for level 6
[   13.372998] md: raid5 personality registered for level 5
[   13.372999] md: raid4 personality registered for level 4
[   13.403702] md: raid10 personality registered for level 10
[   13.944216] usbcore: registered new interface driver usbfs
[   13.944241] usbcore: registered new interface driver hub
[   13.958546] usbcore: registered new device driver usb
[   13.959596] USB Universal Host Controller Interface driver v3.0
[   13.959654] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[   13.959665] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   13.959669] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   13.959971] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   13.959997] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000dc00
[   13.960125] usb usb1: configuration #1 chosen from 1 choice
[   13.960164] hub 1-0:1.0: USB hub found
[   13.960168] hub 1-0:1.0: 2 ports detected
[   14.003028] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   14.064069] ACPI: PCI Interrupt 0000:00:1d.1[b] -> GSI 19 (level, low) -> IRQ 17
[   14.064081] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   14.064084] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   14.064104] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   14.064131] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000d880
[   14.064227] usb usb2: configuration #1 chosen from 1 choice
[   14.064247] hub 2-0:1.0: USB hub found
[   14.064252] hub 2-0:1.0: 2 ports detected
[   14.104163] SCSI subsystem initialized
[   14.151864] libata version 3.00 loaded.
[   14.167931] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
[   14.167942] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   14.167946] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   14.167966] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   14.167991] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000d800
[   14.168090] usb usb3: configuration #1 chosen from 1 choice
[   14.168110] hub 3-0:1.0: USB hub found
[   14.168115] hub 3-0:1.0: 2 ports detected
[   14.271877] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[   14.271892] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   14.271896] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   14.271917] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   14.275812] ehci_hcd 0000:00:1d.7: debug port 1
[   14.275817] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   14.275824] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xf8fffc00
[   14.291661] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   14.291760] usb usb4: configuration #1 chosen from 1 choice
[   14.291781] hub 4-0:1.0: USB hub found
[   14.291787] hub 4-0:1.0: 6 ports detected
[   14.395725] 8139cp 0000:02:03.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   14.395730] 8139cp 0000:02:03.0: Try the "8139too" driver instead.
[   14.397755] 8139too Fast Ethernet driver 0.9.28
[   14.397801] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 22 (level, low) -> IRQ 21
[   14.398419] eth0: RealTek RTL8139 at 0xe800, 00:10:dc:e8:9d:c1, IRQ 21
[   14.398421] eth0:  Identified 8139 chip type 'RTL-8101'
[   14.398491] ACPI: PCI Interrupt 0000:02:04.2[C] -> GSI 21 (level, low) -> IRQ 22
[   14.451144] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[22]  MMIO=[fbfff000-fbfff7ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   14.465444] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 20
[   14.465475] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   14.465486] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   14.468398] ata_piix 0000:00:1f.1: version 2.12
[   14.468407] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 20
[   14.468426] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   14.469089] scsi0 : ata_piix
[   14.469497] scsi1 : ata_piix
[   14.470664] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   14.470667] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   14.795518] ata1.00: ATA-6: FUJITSU MHT2080AH, 006C, max UDMA/100
[   14.795523] ata1.00: 156301488 sectors, multi 16: LBA 
[   14.795547] ata1.01: ATAPI: HL-DT-ST DVD-RW GWA-4082N, CL02, max UDMA/33
[   14.811395] ata1.00: configured for UDMA/100
[   14.982917] ata1.01: configured for UDMA/33
[   15.149194] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHT2080A 006C PQ: 0 ANSI: 5
[   15.153241] scsi 0:0:1:0: CD-ROM            HL-DT-ST DVD-RW GWA-4082N CL02 PQ: 0 ANSI: 5
[   15.158297] Driver 'sd' needs updating - please use bus_type methods
[   15.158351] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   15.158362] sd 0:0:0:0: [sda] Write Protect is off
[   15.158364] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   15.158376] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   15.158426] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   15.158434] sd 0:0:0:0: [sda] Write Protect is off
[   15.158436] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   15.158447] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   15.158450]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   15.234407]  sda1 sda2 < sda5 >
[   15.262333] sd 0:0:0:0: [sda] Attached SCSI disk
[   15.266608] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   15.266624] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   15.283139] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   15.283144] Uniform CD-ROM driver Revision: 3.20
[   15.283186] sr 0:0:1:0: Attached scsi CD-ROM sr0
[   15.539852] kjournald starting.  Commit interval 5 seconds
[   15.539861] EXT3-fs: mounted filesystem with ordered data mode.
[   15.729669] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc0000c0ecb6]
[   15.733569] Clocksource tsc unstable (delta = -687197323 ns)
[   15.737561] Time: hpet clocksource has been installed.
[   27.622785] Real Time Clock Driver v1.12ac
[   27.628232] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   28.413145] iTCO_vendor_support: vendor-support=0
[   28.457116] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   28.457199] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x0860)
[   28.457237] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   28.503579] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   28.529527] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   28.532795] Linux agpgart interface v0.102
[   28.566774] intel_rng: FWH not detected
[   29.145771] input: Power Button (FF) as /devices/virtual/input/input3
[   29.173665] ACPI: Power Button (FF) [PWRF]
[   29.173751] input: Power Button (CM) as /devices/virtual/input/input4
[   29.205616] ACPI: Power Button (CM) [PWRB]
[   29.205680] input: Lid Switch as /devices/virtual/input/input5
[   29.221640] ACPI: Lid Switch [LID]
[   29.221697] input: Sleep Button (CM) as /devices/virtual/input/input6
[   29.249551] ACPI: Sleep Button (CM) [SLPB]
[   29.609681] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 17 (level, low) -> IRQ 23
[   29.609699] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[   30.184411] nvidia: module license 'NVIDIA' taints kernel.
[   30.541974] ieee80211_crypt: registered algorithm 'NULL'
[   30.544562] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   30.544565] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   30.571568] intel8x0_measure_ac97_clock: measured 58764 usecs
[   30.571571] intel8x0: clocking to 48000
[   30.572152] Yenta: CardBus bridge found at 0000:02:04.0 [1462:0321]
[   30.597644] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   30.597648] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   30.700126] Yenta: ISA IRQ mask 0x0cb8, PCI irq 17
[   30.700131] Socket status: 30000006
[   30.700135] pcmcia: parent PCI bridge I/O window: 0xe000 - 0xefff
[   30.700138] cs: IO port probe 0xe000-0xefff: clean.
[   30.700337] pcmcia: parent PCI bridge Memory window: 0xfbf00000 - 0xfbffffff
[   30.723536] Yenta: CardBus bridge found at 0000:02:04.1 [1462:0321]
[   30.851900] Yenta: ISA IRQ mask 0x0cb8, PCI irq 18
[   30.851904] Socket status: 30000006
[   30.851907] Yenta: Raising subordinate bus# of parent bus (#02) from #04 to #07
[   30.851912] pcmcia: parent PCI bridge I/O window: 0xe000 - 0xefff
[   30.851915] cs: IO port probe 0xe000-0xefff: clean.
[   30.852114] pcmcia: parent PCI bridge Memory window: 0xfbf00000 - 0xfbffffff
[   30.878558] input: PS/2 Mouse as /devices/virtual/input/input7
[   30.911106] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 17 (level, low) -> IRQ 23
[   30.916226] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio2/input/input8
[   30.973002] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   31.343418] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input9
[   31.370424] ACPI: Video Device [NV43] (multi-head: yes  rom: no  post: no)
[   31.778310] ACPI: AC Adapter [ADP1] (on-line)
[   31.913671] ACPI: Battery Slot [BAT1] (battery present)
[   33.203458] ipw2200: Radio Frequency Kill Switch is On:
[   33.203460] Kill switch must be turned off for wireless networking to work.
[   33.448699] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[   33.451369] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
[   33.451426] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   33.451436] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   33.451568] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   33.641794] cs: IO port probe 0x100-0x3af: clean.
[   33.642926] cs: IO port probe 0x3e0-0x4ff: clean.
[   33.643264] cs: IO port probe 0x820-0x8ff: clean.
[   33.643508] cs: IO port probe 0xc00-0xcf7: clean.
[   33.644027] cs: IO port probe 0xa00-0xaff: clean.
[   33.644668] cs: IO port probe 0x100-0x3af: clean.
[   33.645847] cs: IO port probe 0x3e0-0x4ff: clean.
[   33.646172] cs: IO port probe 0x820-0x8ff: clean.
[   33.646416] cs: IO port probe 0xc00-0xcf7: clean.
[   33.646933] cs: IO port probe 0xa00-0xaff: clean.
[   33.931847] NET: Registered protocol family 17
[   34.227576] lp: driver loaded but no devices found
[   34.512881] Adding 3028212k swap on /dev/sda5.  Priority:-1 extents:1 across:3028212k
[   34.824741] EXT3 FS on sda1, internal journal
[   35.268846] NET: Registered protocol family 10
[   35.269013] lo: Disabled Privacy Extensions
[   35.269447] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   35.941815] ip_tables: (C) 2000-2006 Netfilter Core Team
[   37.239539] No dock devices found.
[   40.324026] ppdev: user-space parallel port driver
[   40.984400] audit(1211120876.767:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5212 profile="/usr/sbin/cupsd" namespace="default"
[   41.308155] apm: BIOS not found.
[   41.903489] eth0: no IPv6 routers present
[  106.695169] Marking TSC unstable due to: cpufreq changes.
[  171.225427] usb 4-4: new high speed USB device using ehci_hcd and address 2
[  171.358229] usb 4-4: configuration #1 chosen from 1 choice
[  172.188838] usb 4-4: USB disconnect, address 2
[  172.296742] usb 4-2: new high speed USB device using ehci_hcd and address 3
[  172.429494] usb 4-2: configuration #1 chosen from 1 choice
[  629.158580] usb 4-2: USB disconnect, address 3
[  742.567990] usb 4-2: new high speed USB device using ehci_hcd and address 4
[  742.700844] usb 4-2: configuration #1 chosen from 1 choice
[  778.320009] usb 4-2: USB disconnect, address 4
[  778.351327] usb 4-2: new high speed USB device using ehci_hcd and address 5
[  778.484876] usb 4-2: configuration #1 chosen from 1 choice
[  778.512849] usb 4-2: USB disconnect, address 5
[  334.997551] usb 4-2: new high speed USB device using ehci_hcd and address 6
[  782.526702] usb 4-2: configuration #1 chosen from 1 choice
[  874.711907] usb 4-2: USB disconnect, address 6
[  874.747303] usb 4-2: new high speed USB device using ehci_hcd and address 7
[  874.974997] usb 4-2: device not accepting address 7, error -71
[  876.741287] usb 4-4: new high speed USB device using ehci_hcd and address 9
[  876.874078] usb 4-4: configuration #1 chosen from 1 choice
```

As you can see, the 
> found a 'Hauppauge Nova-T Stick' in cold state, will try to load a firmware
does not appear. 

If I do "lsusb", the stick is recognised as Hauppauge.

What is wrong?

Thanks for your help!

---

### Post by wieman01 on 2008-05-21
A good starting point it this site:

[http://linuxtv.org/]("http://linuxtv.org/")

Sadly I am not quite an expert as far as this field is concerned. Just happen to own a Nova T Stick which works fine on my machine, but that's about it. Follow the above link, I am sure it'll give you an idea.

---

### Post by chandolin on 2008-05-22
> **wieman01 said:**
> A good starting point it this site:

[http://linuxtv.org/]("http://linuxtv.org/")

Sadly I am not quite an expert as far as this field is concerned. Just happen to own a Nova T Stick which works fine on my machine, but that's about it. Follow the above link, I am sure it'll give you an idea.

Ok, thank you anyway. I've found this: 
> The newest WinTV NOVA-T USB2 has a different USB ID. The former devices had 9300 & 9301 (for cold and warm state) and the new devices have 7050, 7070 and perhaps 7051. They work with the newest (May 2008) drivers, you maybe have to compile the current CVS yourself. 

My USB is a 7070, but what does "compile the current CVS yourself" mean?

---

### Post by wieman01 on 2008-05-22
> **chandolin said:**
> Ok, thank you anyway. I've found this: 

My USB is a 7070, but what does "compile the current CVS yourself" mean?
You need to compile these drivers from CVS... Can you point me to the link please? And also the CVS source? I try to guide you through it.

---

### Post by chandolin on 2008-05-22
Hi, thanks for your answer. You don't need to search, because I found the solution here: [http://ubuntuforums.org/showthread.php?t=752968](http://ubuntuforums.org/showthread.php?t=752968)

Thanks for your help!

---

### Post by tequila mambo on 2008-06-30
Hi guys,

I used to have my hauppauge nova-t stick working perfectly in ubuntu feitsy by following the instructions here.

Lately I switched to Hardy with Xfce and I am not able to use the stick. The firmware appears to be fine since the stick is perfectly recognized, getting the following message when typing dmesg:

 Hauppauge Nova-T Stick successfully initialized and connected.

I seems that hardy already comes with the firmware. Nevertheless, when I try to scan the channels in Kaffeine I just can't. Nothing happens, it is as if there was no signal.

I tried also with me-tv and the same story. I also tried installing the latest drivers from as explained here: [http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers](http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers) in section 2 and nothing happens.

Has anybody experienced this issue? Any ideas?

---

### Post by Pigeon. on 2008-06-30
What sounds suspicious to me is "hardy already comes with the firmware". Remembering the number of "latest" versions of the firmware that I tried in order to get it going, most of them with the same result as you are seeing, I would suspect that the hardy version does not suit your stick. I would therefore be inclined to reinstall the version you were using before.

---

### Post by tequila mambo on 2008-07-01
> **Pigeon. said:**
> What sounds suspicious to me is "hardy already comes with the firmware". Remembering the number of "latest" versions of the firmware that I tried in order to get it going, most of them with the same result as you are seeing, I would suspect that the hardy version does not suit your stick. I would therefore be inclined to reinstall the version you were using before.


I see...

But even if I try to get the old firmware, it seems the link to get it is dead.

[http://www.wi-bw.tfh-wildau.de/~pboettch/home/linux-dvb-firmware/dvb-usb-dib0700-03-pre1.fw](http://www.wi-bw.tfh-wildau.de/~pboettch/home/linux-dvb-firmware/dvb-usb-dib0700-03-pre1.fw)

I have searched lots of places for the firmware and I just cannot get it.

---

### Post by Pigeon. on 2008-07-01
That seems to be one of the ones I tried (although it didn't work for me), and I still have a copy.

I have put all the different versions I found on a web page.

[Hauppauge WinTV Nova-T USB Stick firmware](http://pigeonsnest.co.uk/stuff/firmwares/index.html)

---

### Post by wieman01 on 2008-07-02
Odd... my system works with the old driver. Did an upgrade to Hardy recently and never experienced any issues.

---

