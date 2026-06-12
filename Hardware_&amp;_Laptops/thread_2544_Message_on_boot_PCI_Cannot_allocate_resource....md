---
title: "Message on boot: PCI: Cannot allocate resource..."
date: 2004-10-29
forum: Hardware &amp; Laptops
---

### Post by mctavish on 2004-10-29
On boot, the first message I get is

PCI: Cannot allocate resource region 4 of device 0000:00:02.1

The boot continues just fine, and I don't seem to be suffering any nasty effects from it, but I'm curious about what it could mean. I've run a few different 2.6 kernels in the past and never seen it before.

I've had other slight weirdness that could be related, namely

* on install my video card was misdetected. It thought I had an SIS something or other, but I actually have a radeon 9600xt. This was no big deal, I just changed my driver to vesa in xf86config-4. My motherboard uses the SiS746 chipset. There is a bug in bugzilla that seems to match this problem.

* My motherboard is meant to have onboard sound but this apparently wasn't picked up. No big deal because I also have a soundblaster. But could this be the device that couldn't be allocated? (now that I think of it I may have disabled it in bios though??)

As I said, everything is working fine but these things are bugging me (heh heh pun).

---

### Post by cdiorio on 2005-04-02
[QUOTE=mctavish]On boot, the first message I get is

PCI: Cannot allocate resource region 4 of device 0000:00:02.1

The boot continues just fine, and I don't seem to be suffering any nasty effects from it, but I'm curious about what it could mean. I've run a few different 2.6 kernels in the past and never seen it before.

I've had other slight weirdness that could be related, namely

* on install my video card was misdetected. It thought I had an SIS something or other, but I actually have a radeon 9600xt. This was no big deal, I just changed my driver to vesa in xf86config-4. My motherboard uses the SiS746 chipset. There is a bug in bugzilla that seems to match this problem.

* My motherboard is meant to have onboard sound but this apparently wasn't picked up. No big deal because I also have a soundblaster. But could this be the device that couldn't be allocated? (now that I think of it I may have disabled it in bios though??)

As I said, everything is working fine but these things are bugging me (heh heh pun).[/QUOTE]
 Did you ever resolve this issue? I have the same message on boot.

---

### Post by risings0n on 2006-05-18
same message for me, happens only on my laptop computer (core duo ) not on my work pc (P4). any ideas?

---

### Post by J0Sb31R on 2006-06-04
same here, on laptop.. but boots fine :)

---

### Post by OldSeaDog on 2007-01-09
]](*,) Without wishing to sound like a parrot, me too!

My message is slightly different.  It begins by saying
:PCI: JMB36X: Enabling dual function on device 0000:06:00.0
It then reads a message similar to everyone else 4 times for regions 0, 1, 2, and 3.
Finally it says:
"Error while updating region 0000:06:00.0/0 (00008000 != 00000000), trhen has the same error message for region 0000:06:00/2 (00008008 !=00000000)

It seems a lot of people have a smilar problem - does anyone out there in Linuxland have a similar solution?

My system is an ASUS M2N-SLI Deluxe, with a 64X2 AMD 4200+ processor, 2GB of RAM and a 512 MB cache.  I have an EIDE drive (250GB) and a SATA 320GB Drive.  The EIDE drive is from my old machine which died an honourable death in the service of Tux.

BTW, the JMB36X relates to my JMicron EIDE controller I believe.

OlSeaDog, the Geekasaur

---

### Post by MrSoussey on 2007-01-14
this is a core2duo issue, else try a bios update... worked for me...

---

### Post by jazz452 on 2007-01-20
> **mctavish said:**
> On boot, the first message I get is

PCI: Cannot allocate resource region 4 of device 0000:00:02.1

The boot continues just fine, and I don't seem to be suffering any nasty effects from it, but I'm curious about what it could mean. I've run a few different 2.6 kernels in the past and never seen it before.

I've had other slight weirdness that could be related, namely

* on install my video card was misdetected. It thought I had an SIS something or other, but I actually have a radeon 9600xt. This was no big deal, I just changed my driver to vesa in xf86config-4. My motherboard uses the SiS746 chipset. There is a bug in bugzilla that seems to match this problem.

* My motherboard is meant to have onboard sound but this apparently wasn't picked up. No big deal because I also have a soundblaster. But could this be the device that couldn't be allocated? (now that I think of it I may have disabled it in bios though??)

As I said, everything is working fine but these things are bugging me (heh heh pun).

This worked for me no more error messages
Open you GRUB configuration file.

sudo gedit /boot/grub/menu.lst

To proceed, you'll need to know the framebuffer code for your desired resolution:

Code
	

Resolution

vga=785        640x480
	



vga=788        800x600
	



vga=791        1024x768
	



vga=794          1280x1024
	



   1.

      Automatic (and update-proof) GRUB Configuration

Find the line

# defoptions=quiet splash

and add your framebuffer resolution code, e.g. (for 1024x768)

# defoptions=quiet splash vga=791

Save the file, then execute

sudo update-grub

This will now keep even after any future kernel update, unlike the method below. You're all done.

    *

      B.

---

### Post by lamegaptop on 2007-02-07
[SIZE="4"]OK I' stumped. Where does one find the frame buffer value for, say, 1440X900. I'd love to try this on my HP DV8000 that is complaining of the same type of PCI Allocation issues. Web searches for a reference have been useless.

Any help would be appreciated.[/SIZE]

---

### Post by wersdaluv on 2007-03-02
Same message here. 

It's just that, I think I know what it means. 

My USB Card does not work.

Please see [this thread]("http://ubuntuforums.org/showthread.php?t=356269") for more information.

---

### Post by powermoose on 2007-11-17
I get the same thing with 3 different devices that cannot allocate resource.

0000:00:1c.0 regions 7 & 8 (0000:00:1c.0 is my PCI port 1)
0000:00:1c.2 regions 7 & 8 (0000:00:1c.0 is my PCI port 3)
0000:00:06.0 region 0         (0000:00:06.0 is my Wireless interface)

My wireless interface does not work and I have not succeeded in my attempts to   enable it.

Can anyone give insights on devices and resource allocation?

Is this resource allocation problem the reason I cannot enable my wireless interface?

---

### Post by TheHolyDefender on 2007-11-20
I just install Ubuntu 7.10 onto my system and I am having the same issue.  I am using a Pentium M processor, and an ATI video card.  If someone could come up with a fix for this, that would be great because the time to boot is forever with this problem existing.

---

