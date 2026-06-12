---
title: "mount: function not implemented"
date: 2006-10-26
forum: Hardware &amp; Laptops
---

### Post by Anselme- on 2006-10-26
Hey everyone,

I have an ACER 1350, and I am using the Live CD to try Ubuntu before installing over Windows. Everything is fine... expect that I am incapable of mounting any USB Mass storage devices. In the other hand, my USB Logitech Optical mouse works fine.

I have noticed that on the boot on the CD, a strange message appears: *mount: function not implemented*. But I have access to the mount function, its manual, etc...

Of course, when I put my Creative TX FM 512MO nothing happens, and linux doesn't see it at all according to the mount command.

When I start with the MP3 player plugged in, some stranges errors messages appears too:
```
ubuntu@ubuntu:~$ /bin/dmesg | grep usb
[17179577.304000] usbcore: registered new driver usbfs
[17179577.304000] usbcore: registered new driver hub
[17179577.840000] usb 1-3: new high speed USB device using ehci_hcd and address 3
[17179589.384000] usb 1-3: device not accepting address 3, error -110
[17179589.808000] usb 2-2: new low speed USB device using uhci_hcd and address 2
[17179590.236000] usbcore: registered new driver hiddev
[17179590.508000] input: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb -0000:00:10.0-2
[17179590.508000] usbcore: registered new driver usbhid
[17179590.508000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179590.748000] usb 1-3: new high speed USB device using ehci_hcd and address 5
[17179602.292000] usb 1-3: device not accepting address 5, error -110
[17179602.404000] usb 1-3: new high speed USB device using ehci_hcd and address 6
[17179613.948000] usb 1-3: device not accepting address 6, error -110
```

Some people suggested me to see in the BIOS, if I can boot on USB or not, according to my BIOS, I can change the order of devices to boot on(CD ROM, USB, HDD). Of course I put HDD last.

Could you please help me? I have no idea what to do :( ](*,) 
If you need any further informations, please ask.

---

### Post by hearnden on 2006-10-26
You could try to mount it explicitly if you know what USB device corresponde to it (sda1, sdb4, etc.) and what kind of FS it has, e.g.

```

$ sudo mkdir /media/musicplayer
$ sudo mount -t vfat /dev/sda1 /media/musicplayer

```

Then any errors should be fairly explicit.  If not, try looking in /var/log/messages or use "dmesg | tail" to see if any errors are reported in there.

---

### Post by Anselme- on 2006-10-26
But in the mesg just reports the errors messages that keep going on and on and on:

when my USB device is pluged in:

```
ubuntu@ubuntu:/var/log$ dmesg|tail
[17187105.484000] usb 1-1: device not accepting address 75, error -110
[17187105.596000] usb 1-1: new high speed USB device using ehci_hcd and address 76
[17187117.140000] usb 1-1: device not accepting address 76, error -110
[17187117.252000] usb 1-1: new high speed USB device using ehci_hcd and address 77
[17187127.676000] usb 1-1: device not accepting address 77, error -110
[17187127.788000] usb 1-1: new high speed USB device using ehci_hcd and address 78
[17187138.212000] usb 1-1: device not accepting address 78, error -110
[17187138.544000] usb 1-1: new high speed USB device using ehci_hcd and address 79
[17187150.088000] usb 1-1: device not accepting address 79, error -110
[17187150.200000] usb 1-1: new high speed USB device using ehci_hcd and address 80
```

I don't know if those commands could help...

```
ubuntu@ubuntu:~$ sudo lshw -short
...
/0/e0000000/10                     bus            VT82xxxxx UHCI USB 1.1 Controller
/0/e0000000/10/1        usb2       bus            UHCI Host Controller
/0/e0000000/10/1/2                 input          USB Optical Mouse
/0/e0000000/10.1                   bus            VT82xxxxx UHCI USB 1.1 Controller
/0/e0000000/10.1/1      usb3       bus            UHCI Host Controller
/0/e0000000/10.2                   bus            VT82xxxxx UHCI USB 1.1 Controller
/0/e0000000/10.2/1      usb4       bus            UHCI Host Controller
/0/e0000000/10.3                   bus            USB 2.0
/0/e0000000/10.3/1      usb1       bus            EHCI Host Controller
...
```

```
ubuntu@ubuntu:~$ lspci -v |grep -i usb
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82) (prog-if 20 [EHCI])
```
```

ubuntu@ubuntu:/mnt$ mount
unionfs on / type unionfs (rw)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
ubuntu@ubuntu:/mnt$
```

---

### Post by towsonu2003 on 2006-10-26
Have a look at the faq at [www.linux-usb.org](www.linux-usb.org)

It says
> 
Q:  Why doesn't USB work at all? I get "device not accepting address".

A: This can be one of several problems:

    * High speed devices sometimes have problems with cables used to connect them. They're more sensitive to signal quality issues than older usb 1.1 full or low speed devices. If the device works OK at full speed on the same system, after you "rmmod ehci-hcd", this is likely the problem you're seeing. There are a lot of things you can do to change signal quality.
          o Use a different cable. Some are even marketed specifically for use with high speed devices. Most USB 1.1 cables work just fine at high speed, but the one you're using might be an exception (maybe it's been damaged).
          o Switch to a different USB connector on your computer. Back panel connectors are often right on the motherboard, with much care taken to preserve signal quality. A front panel connector probably doesn't use cabling designed with USB in mind; and its cable could be damaged by bending, baking or something else even when it's not routed through the power supply.
          o Use an external high speed hub. Those hubs have signal conditioning circuitry that may cover up certain flaws.
          o Make sure your device is using its own external power supply, or that its battery is fully charged. 
      You might be able to get the same device to work at high speed on a different machine.
    * You may have some problem with your PCI setup that's preventing your USB host controller from getting hardware interrupts. (Current Linux 2.6 kernels will actually tell you when they notice this problem; see the "dmesg" output.) When Linux submits a request, but never hears back from the controller, this is the diagnostic you'll see. To see if this is the problem, look at /proc/interrupts to see if the interrupt count for your host controller driver ever goes up. If it doesn't, this is the problem: either your BIOS isn't telling the truth to Linux (ACPI sometimes confuses these things, or setting the expected OS to windows in your BIOS), or Linux doesn't understand what it's saying.
    * Sometimes a BIOS fix will be available for your motherboard, and in other cases a more recent kernel will have a Linux fix. You may be able to work around this by passing the noapic boot option to your kernel, or (when you're using an add-in PCI card) moving the USB adapter to some other PCI slot. If you're using a current kernel and BIOS, report this problem to the Linux-kernel mailing list, with details about your motherboard and BIOS.

Various users have had success with some specific strategy. I've collectioned their notes here[*].

[*] below
> 
A user with an AOpen AK73Pro motherboard reported that turning off the BIOS option "Assign IRQ for USB" solved this problem for him. Another mentioned that upgrading from BIOS revision 1.16 to 1.20 fixed it (but he wasn't sure if he had an AK73 or the Pro or some other variant).

Another user had this problem with a Sharp Zaurus until he plugged in the power supply into the docking station.

Yet another user with a Sum Vision flash disk found that inserting the device slowly solved this problem. He suspects it takes it time to become active after it gets power before it can properly respond.

Another suggestion that worked for at least one person was to use either pci-noacpi or acpi=off as a boot option.

Here is an email from another user;

i have a Elite K7s5a Pro mainboard where the USB connectors were not working
at all with kernel 2.4.25. No matter what device i plugged in, i always saw
only "device not accepting address" in dmesg.
I tried all the hints from your FAQ but nothing helped. The driver (usb-uhci)
for the USB connectors shared its interrupt with three other devices. So it
was very hard to say if the USB received interrupts or not.
Because of some other reason i removed the Adaptec 2940 from my system, which
was sharing the interrupt with the USB driver. And now the USB connectors are
working! :-)

And another;

My situation is that I have a Lippert Cool Roadrunner III CPU board,
which uses a VIA VT82C686B south-bridge chip to handle its USB
interfaces. After a USB device has been successfully disconnected and
reconnected to the USB bus a variable number of times, I start seeing
the error that this FAQ question talks about, and thereafter I can no
longer connect any new USB devices. According to /proc/interrupts, no
interrupts arrive from the host controller either, once this
happens. None of the suggestions in FAQ entry had any effect.  However
I then discovered that if I unload and then reload the uhci-hcd
driver, whenever this happens, the USB interfaces will reliably start
working again. My guess is that the uhci-hcd driver resets the
host-controller in the southbridge, whenever it is loaded. Note that
it isn't necessary to unload any other USB drivers before doing
this. Thus the usb-core driver and any high-level USB drivers can all
be left loaded while this is being done.


Also, file a bug at [https://launchpad.net/distros/ubuntu/+bugs](https://launchpad.net/distros/ubuntu/+bugs) to the linux-source-(uname -r) package, if you cannot solve the problem . 

As per playing aroun with BIOS, I think they mean to say this (from the same [FAQ]("http://www.linux-usb.org/FAQ.html")):
> Q: How do I make USB be detected on my machine?

A: If you are sure that you actually have a suitable hardware setup, look for a BIOS option that could be applicable. It might be labelled as USB, or it might be more obscure, discussing Plug-n-Play, or having options for various types of operating systems. You may need to try various combinations. Unless you rely on a USB keyboard or mouse during booting, it's probably safest to disable support for those in your BIOS; lots of BIOS writers seem to get that wrong, making trouble when Linux tries to take over USB. 

You could also use their mailing list to get help after **making sure** you read all their documentation: [http://www.linux-usb.org/mailing.html](http://www.linux-usb.org/mailing.html) (they won't be very friendly if you don't show them that you tried fixing this yourself first)

Finally, try your luck with other kernels (try a couple of other LiveCD distros like Knoppix etc), or with a most recent kernel (you'll have to compile that yourself -guides are available from the ubuntuforums).

---

### Post by Anselme- on 2006-10-26
OK, ok, first I'll try upgrade my BIOS, and then try with another LIVE CD distribution, and try to recompile with a newer kernel (Is it ok with a Live CD?)...

(Allthough if find it strange that my usb mouse is working but neither my ARCHOS 20go nor my logitech 512MO are working)

A long road is ahead of me :(

Thanks for all the informations, at least I know where to look now :)

---

### Post by towsonu2003 on 2006-10-26
> **Anselme- said:**
> OK, ok, first I'll try upgrade my BIOS, and then try with another LIVE CD distribution, and try to recompile with a newer kernel (Is it ok with a Live CD?)...

(Allthough if find it strange that my usb mouse is working but neither my ARCHOS 20go nor my logitech 512MO are working)

A long road is ahead of me :(

Thanks for all the informations, at least I know where to look now :)

try a couple of distros before upgrading the BIOS (easier). knoppix is known for its hardware stuff...

compiling a new kernel won't work in a LiveCD... you have to do it in an installed system bc after compiling and installing a new kernel, you have to boot using it to see if it worked... 

for kernel compilation, see: [http://ubuntuforums.org/showthread.php?t=56835](http://ubuntuforums.org/showthread.php?t=56835) PS. You'll probably fail a couple of times bf compiling successfully...

good luck :)

---

### Post by Anselme- on 2006-10-26
> **towsonu2003 said:**
> try a couple of distros before upgrading the BIOS (easier). knoppix is known for its hardware stuff...

compiling a new kernel won't work in a LiveCD... you have to do it in an installed system bc after compiling and installing a new kernel, you have to boot using it to see if it worked... 

for kernel compilation, see: [http://ubuntuforums.org/showthread.php?t=56835](http://ubuntuforums.org/showthread.php?t=56835) PS. You'll probably fail a couple of times bf compiling successfully...

good luck :)

Well, I have just upgraded my BIOS (BIOS files are very small compare to a full CD ;)) (my internet connections is a bit slow)

And nothing changed regarding the errors messages, and no new options appeared in the BIOS (I went on the acer support web site and downloaded the latest one v3A29 I had the V3A24)

I also did a little comparison when I plug my USB Mouse and my USB mass storage device on the file /proc/interrupts (as said in the FAQ). As for USB Mouse storage the numbers are increased by hundreds, with USB mass storage it is only increased by one to one, every 10 or 20 seconds... So I think there is really no communication between my computer and USB mass storage (except with Windows ^^)

Well, now I'll go download Knoppix as you advised.

---

### Post by Anselme- on 2006-10-27
hmm... Finally, I tested with Knoppix with linux kernel 2.6, and it stills doesn't work, the same error appears: error -110 :(

I don't know if I can try to compile a new kernel, it implies for me to delete windows and install linux over it, but after i won't be able to access to my USB mass storage devices for a while (in the best case)...

I can't take the risk :( So, I think if i want to use Linux on my computer, I will have to buy a new one :)

---

