---
title: "Ubuntu Hardy on Compal JHL90"
date: 2008-08-31
forum: Hardware
---

### Post by wolframarnold on 2008-08-31
I've decided to launch this new thread specifically for users of the Compal JHL90 which is resold under a variety of brands, including PowerPro.

A lot of [discussion has happened on the thread regarding the Intel WiFi Link 5100 card]("http://ubuntuforums.org/showthread.php?t=879134&highlight=jhl90"), and the problem seems to be unresolved for the Compal JHL90 platform.

The other big problem I'm facing is that suspend-to-ram, aka hiberate doesn't work... the unit will not wake up properly, the screen is black and I have to hard reset it.

I want this thread dedicated to problems with Ubuntu specifically around JHL90.

Bring your ideas and questions here.  Note also if you're running 32-bit or 64-bit Ubuntu.  I'm running Kubuntu 8.04 64bit with a custom compiled kernel version 2.6.26-rc4, and still no wireless and no hiberate.

---

### Post by willemse on 2008-09-01
I currently have ubuntu 64 bit/kubuntu 32 bit installed on my compal JHL90. Both standard 2.6.24-19-generic.

I'm not yet an advanced tech guy but i'll tell you what's up with me yet:

- suspend to disk working (hibernate) on kub and ub
- suspend to ram not working (standby) on kub, ok on ub
- wifi worked out of box on ubuntu, after I did a reinstall of network-manager-kde it worked too, but don't have reason for that.
- webcam working fine on kub and ub using GSPCA / SPCA5xx, however slow in some programs, nice in others, don't have reason yet.
- opengl apps working nice with nvidia drivers.

I disabled desktop effects on kde, as it wasn't working nicely, creating bad boots sometimes, no wlan active etc ..., maybe try without desktop effects wolframarnold?

- Fingerprint reader not working. When I do lsusb I get this:
***@***:~$ lsusb
Bus 008 Device 003: ID 04f2:b109 Chicony Electronics Co., Ltd *(webcam)*
Bus 008 Device 001: ID 0000:0000
Bus 007 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 002: ID 147e:1000 *(no description?)*
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 046d:c03d Logitech, Inc. *(usb mouse)*
Bus 003 Device 001: ID 0000:0000

I haven't found much info when googling that device 147e:1000 device ID, anyone got some info on that?

---

### Post by sumwonyuno on 2008-09-01
I'm back on Intrepid Ibex Alpha 4 64-bit on kernel 2.6.27-2-generic.

In lshw -C network, it no longer says DISABLED for the wireless adapter, but I still can't connect to a network.

As for the blank entry in lsusb, it's definitely blank in Intrepid.

Bus 008 Device 004: ID 064e:a115 Suyin Corp. (webcam?)
Bus 008 Device 002: ID 0586:340f ZyXEL Communications Corp. G-220 v2 (USB wireless adapter)
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 147e:1000  
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

However, in lshw...
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.27-2-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12.0MB/s
              *-usb UNCLAIMED
                   description: Generic USB device
                   **product: Fingerprint Sensor**
                   vendor: TouchStrip
                   physical id: 2
                   **bus info: usb@5:2**
                   version: 0.33
                   capabilities: usb-1.00
                   configuration: maxpower=100mA speed=12.0MB/s

So it seems that the blank name is the fingerprint sensor.  I don't know of any program that can recognize it for Linux.

Another issue that I've noticed is that the only temperature I can monitor (via gnome-applets) is for the video card.  CPU and system readings are not available.

---

### Post by wolframarnold on 2008-09-02
> **willemse said:**
> I currently have ubuntu 64 bit/kubuntu 32 bit installed on my compal JHL90. Both standard 2.6.24-19-generic.

- suspend to ram not working (standby) on kub, ok on ub
- wifi worked out of box on ubuntu, after I did a reinstall of network-manager-kde it worked too, but don't have reason for that.

- Fingerprint reader not working. When I do lsusb I get this:

Just to clarify -- your wireless DOES work under 64 bit Ubuntu, but not under 32 bit Kubuntu?  What wireless card do you have?  Can you post the result of "sudo lshw -C network"

It's also interesting to me that suspend-to-ram is working for you under Ubuntu.  What is your BIOS version?  (You can see it on the BIOS screen when you press F2 right after power-on.)

Fingerprint reader:  Take a look at the fprint project and links and comments [herein]("http://lddubeau.com/avaktavyam/linux-on-a-compal-ifl90").

---

### Post by Freiddie on 2008-09-20
I'm having sound problem as well. The sound doesn't work, and there doesn't seem to be a way to find the driver. The TTY also does not work - a blank screen just shows up.

I'm also having the wireless and standby/hibernate issues.

---

### Post by senortighto on 2008-10-21
as far as the the wireless, i already posted in the intel 5100 thread but i installed the latest beta of intrepid ibex and wireless is working flawlessly.  so that's an option to try for you guys who really need the wireless to function like i do.

but as far as the other stuff, i haven't really messed with ibex enough yet (only like 20 mins) to see what else works/doesn't work.

---

### Post by Freiddie on 2008-11-05
Yep. Ibex seems to have fixed the sound and wireless issues for me. Though I still haven't figured out if/whether the microphone works. But at least it's quite an improvement.

Freiddie

---

### Post by wolframarnold on 2008-12-16
I've upgraded to Intrepid 64bit.  Here is my update with regards to the Compal JHL90:

[LIST]
[*]First, I've upgraded my bios to the latest available from Compal 1.10 (I think)
[*]Unrelated to the Compal JHL90: Initially I had installed Kubuntu, but as much as I love KDE, I found KDE 4.1 not ready for prime time, so I switched to Gnome by installing "ubuntu-desktop"
[*]Out of the box, the wireless card worked! Yeah! O:)
[*]Out of the box, the binary Nvidia driver (version 177) was offered (after first boot-up) and worked! Yeah! O:)
[*]The suspend-to-ram didn't work (system didn't wake up)
[*]The suspend-to-disk (hiberate) didn't work either (system didn't wake up)
[*]Sound worked out of the box! Yeah! O:)
[/LIST]

The suspend-to-ram I fixed by commenting out the stuff in /etc/defaults/acpi-support as described here: [https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)

The suspend-to-disk (hiberate) seems to shut the machine down, I'm not sure yet what's going on here.

---

### Post by linbeans on 2009-01-02
Hi wolframarnold,

I'm on exactly the same specs as you are except i'm on Kubuntu. Say, do you have messed graphics and freezing windows?

Sometimes when I start up my machine I get Ubuntu running in low graphics mode warning with a screen split in two halves...

I think the nvidia drivers are to blame...

Please tell me what are your experiences:D

Thanks!

---

### Post by wolframarnold on 2009-01-02
> **linbeans said:**
> 
I'm on exactly the same specs as you are except i'm on Kubuntu. Say, do you have messed graphics and freezing windows?
You know, I'm a big time Kubuntu fan and user.  But I took one look at KDE 4.1, and I decided for myself that it's not ready yet.  I need a desktop that just works and I don't care to tinker with tons of stuff just to get it running.  So I'm on Gnome again for the first time in many years.  You can install both, by the way.  Just run
```
sudo apt-get install ubuntu-desktop
```
and you can try it.

That said, I read somewhere in the Kubuntu 8.10 release notes that there is a graphics performance problem with the Nvidia proprietary driver and that they're waiting for a fix from Nvidia.

I don't have any trouble under Ubuntu (w/ Gnome); I'm using the Nvidia proprietary driver and it's very fast at native resolution. No problems here.

The only thing that required a small tweak (see my previous post) is the suspend settings.

Best of luck.

---

### Post by linbeans on 2009-01-07
Thumbs up for Wolframarnold. Ubuntu is much more smoother than Kubuntu(at least on my Comapl JHL90), altough I still have occasional startup graphics re-configuration problems.

Thanks!:D

---

### Post by andlinux on 2009-01-18
Tomorrow I will have my Compal JHL90 and I will install ubuntu on it just like I had with my previous notebook (Compal CL56).
I have to say that I have chosen the one with the 6 cells battery and the 1280*800 resolution screen.

I will update here...

---

### Post by andlinux on 2009-01-24
I'm 6 six days later because I forgot I had posted here. ;)

I installed ubuntu 8.10 (64bit) and almost everything worked except:

- Wlan didn't worked (not with wpa), without wpa no problem.
- I installed the nvidia restricted drivers 177.82 and I have the same problem as linbeans, sometimes when I boot up I get a screen that's splitted in 2. If I then restart then it's ok.
- If I look at the thermal monitor from nvidia then the gforce is 58°C and in this room is it around 20°C I guess, that's a lot of heat.

I didn't upgrade the BIOS but maybe I'm gonna do that. I already downloaded the files. Oh, and I have not the one with a 1280*800 screen but a 1440*900 screen.

---

### Post by kaar3l on 2009-03-04
Got myself a JHL90 too. :)
Fingerprint reader works fine with login in gdm.
Use this guide to make it work:
[http://rvshiro.wordpress.com/2009/01/14/fingerprinting-under-ubuntu-810-on-asus-n10jc/](http://rvshiro.wordpress.com/2009/01/14/fingerprinting-under-ubuntu-810-on-asus-n10jc/)

I haven't yet got working bluetooth and wifi software switch. :/

---

### Post by andlinux on 2009-03-04
> **kaar3l said:**
> Got myself a JHL90 too. :)
Fingerprint reader works fine with login in gdm.
Use this guide to make it work:
[http://rvshiro.wordpress.com/2009/01/14/fingerprinting-under-ubuntu-810-on-asus-n10jc/](http://rvshiro.wordpress.com/2009/01/14/fingerprinting-under-ubuntu-810-on-asus-n10jc/)

I'm gonna try that :)

---

### Post by kaar3l on 2009-03-09
The restricted nvidia driver 177 2d performance was awful, i installed 180.37 and that super. :)

---

### Post by andlinux on 2009-03-09
> **kaar3l said:**
> The restricted nvidia driver 177 2d performance was awful, i installed 180.37 and that super. :)
Indeed, I'm also using 180.37 and the fingerprint is working, thanks for the info ;)

---

### Post by linbeans on 2009-03-10
> **kaar3l said:**
> The restricted nvidia driver 177 2d performance was awful, i installed 180.37 and that super. :)

Hey! Where did you get the 180.37 driver from?

Thanks

---

### Post by andlinux on 2009-03-10
> **linbeans said:**
> Hey! Where did you get the 180.37 driver from?

Thanks

[http://www.nvnews.net/vbulletin/showthread.php?p=1951107](http://www.nvnews.net/vbulletin/showthread.php?p=1951107)

---

### Post by kaar3l on 2009-04-14
185.13 Beta is ever better. :) I have used it for 3 weeks and its the best.
[ftp://download.nvidia.com/XFree86/Linux-x86/](ftp://download.nvidia.com/XFree86/Linux-x86/)
I haven't tried 185.19 yet. :(

---

### Post by andlinux on 2009-04-15
> **kaar3l said:**
> 185.13 Beta is ever better. :) I have used it for 3 weeks and its the best.
[ftp://download.nvidia.com/XFree86/Linux-x86/](ftp://download.nvidia.com/XFree86/Linux-x86/)
I haven't tried 185.19 yet. :(Why is 185.13 beta better ?

---

### Post by kaar3l on 2009-04-15
> **andlinux said:**
> Why is 185.13 beta better ?
With the 180 when i enabled compiz, it was slower and i got less responsive system, I turned compiz off. With 185 i have always compiz on, and it works faster than 180. :)

---

### Post by kaar3l on 2009-04-15
Holy crap, just found a solution for the wireless select switch problem.
[http://krzemin.iglu.cz/software/compal-laptop-control-en](http://krzemin.iglu.cz/software/compal-laptop-control-en)
After install there's readme:
/usr/share/doc/compal-laptop-control

---

### Post by DarkRaben on 2009-04-23
Hello there,

Did someone has solved problem with lack of sound after suspend?

---

