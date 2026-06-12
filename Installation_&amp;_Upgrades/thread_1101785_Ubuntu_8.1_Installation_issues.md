---
title: "Ubuntu 8.1 Installation issues"
date: 2009-03-20
forum: Installation &amp; Upgrades
---

### Post by zrclshn on 2009-03-20
I currently have Vista Media Center, with a rather large DVD collection already ripped to disk.  I have seen demos of Linux MCE, and was impressed at how much better it appeared to be.  I was told that a good place to start was to use the Ubuntu live CD to ensure that my current sustem would work properly before venturing on to Linux MCE.  I followed this advice, and starting up the system with Ubuntu 8.1 gave me the following problems.

1)  No sound
	Sound on the system in Onboard Optical that runs directly to my home theatre receiver.
	Note: Will ALSA drivers fix this?

2)  OverScan
	Samsung 61" HD DLP 1080p connected via DVI to HDMI cable.  Top and bottom edges
	of the screen are not visible, correct resolutions are available.
	Note: I read that it may be possible to use the Nvidia utility that comes with the Nvidia
	drivers to correct this, but am not sure.

3) Bluetooth Mouse must be connected at startup
	Logitech MX5500 Keyboard & mouse, jeyboard works on startup, but mouse must be 
	connected via the Bluetooth utility
	Note:  I am running from the live cd, I do not know  if I have to do this each time.

I would like to know if anyone can address these issues with certainty before I blow away my current installation of Vista, and if anyone has any other pointers or gotchas I need to look out for?
Please keep in mind, where as I am very capable on a Windows box, I have almost no experience with Linux.

Thanks for any and all help

System


Motherboard
	Asus P5N72-T Premium Nvidia nForce 780i SLI Chipset

Disk Drives
	2 TB Raid 0 Striped

Video Card
	Nvidia 9600 GT

Processor
	Intel Core 2 Quad Q6600

Sound
	SoundMAX Integrated Digital HD Audio

---

### Post by lemming465 on 2009-03-21
> No sound
If the live CD doesn't offer sound, it will be probably somewhere between difficult and impossible to fix that after installation.  Your best bet is a newer version of the kernel + pulseaudio, so try either this week's ubuntu 9.04 alpha 6 live CD or next weeks 9.04 beta live CD.  The sound situation might improve.

> OverScan
The odds are fairly good that converting to the nvidia binary closed source proprietary driver after installation will let you improve that.  You will gain performance but may lose stability.  It's difficult to test this on the live CD.

> Bluetooth Mouse must be connected at startup
That can probably be fixed permanently post-install, I think.

> any other ... gotchas
A big horrible one, with the disk layout.  It's fairly likely that Nvidia hasn't produced Linux driver support for their "fakeraid" chipset, so Linux and Vista probably can't share the striped disks as they are currently used.  You can find out by starting the install process up to the disk partitioning stage.  If it sees your NTFS disk partitions, your luck is in.  I'm guessing it won't see the disk drives, much less the partitions. **Be sure to quit rather than continue the installation.** you are probably looking at a "destroy the entire current contents of the disks and change the BIOS settings" scenario before you can install Linux.

If you are lucky enough to see the NTFS disk partitions, what I'd suggest for starters is a "WUBI" install, which uses files inside NTFS for the linux filesystem, and puts an alternate linux boot option into the vista boot loader menu.  This would let you try things out on the linux side without having to remove vista or repartition.  In the long run you might prefer to run in the more conventional way with direct linux partitions on the disk, but in an R&D phase you might prefer the WUBI style.  However, you can't safely do any kind of install, whether WUBI or shrinking an NTFS partition, unless the fake software RAID is supported.

---

### Post by zrclshn on 2009-03-21
Thanks 4 the information...  However, without sound, it certainly will not make for a very good HTPC.  Guess I will stick with Vista.  Seems things are not much further along in the Ubuntu world from the last time I tried to make the switch.  Could not get hardward to work then either...  Such a disappointment, because the display on Linux MCE is very impressive looking.

---

### Post by kanedafx on 2009-03-29
Hello everyone.
I just install Ubuntu Studio 8.10 the instalation was perfect but when the pc reboot and start again I have 1 error.
The error is : Failed to start the X server.
I did something wrong? there is something that I can do?
I'm a noob on Linux.
My pc:
M.B. Asus P5KC
4 GB
Nvidia 9600 GT.

Thank you.

---

### Post by labedra on 2009-04-06
1. login to gnome desktop
2. enable the proprietary drivers
3. reboot
4. x gnome will not start until you do the follwoing (NO NEED TO RELOAD YOUR BOX AGAIN!!!!!!)

sudo nvidia-xconfig --sli=on
lspci | grep -i vga

03:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)
04:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)

sudo nano /etc/X11/xorg.conf
add the following line depending on what the 1st VGA card returns under the "Device Section"

BusID "PCI:3:0:0"

so your "Device Section" looks like this one below or similar. Note since my 1st PCI board returned "03:00.0" I added PCI:3:0:0, the first # is what counts since the rest are zeros.

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9600 GT"
    BusID          "PCI:3:0:0"
EndSection

Save the xorg.conf file and type "startx" or "/etc/init.d/gdm start"

To watch the video [http://www.youtube.com/watch?v=JEvK4fl1jmQ](http://www.youtube.com/watch?v=JEvK4fl1jmQ)

Peace!
Rafael.

---

