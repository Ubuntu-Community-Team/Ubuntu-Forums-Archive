---
title: "Monitor/display seriouly distorted"
date: 2013-11-05
forum: Hardware
---

### Post by Xeovke on 2013-11-05
I recently went through the release upgrade and got into an annoying problem. After the reboot, the display is wobbling and very difficult to read. 

The effect is roughly as follows: every line gets horizontally enlarged by a factor t. This factor varies with time and with the height of the line to make nice sine curves out of straight vertical lines. Actually there is a phase difference between even and odd lines. The leftmost part of the screen remains legible as the distortion effect is smaller there but the rightmost part is impossible to read. A straight vertical line looks like sine wave, the frequency and the amplitude of this wave with time, although the amplitude is always increasing linearly as one moves to the right of the screen.

The first tentative to solve the problem was to change some display options with xrandr, but the problem persists independently of resolution or rate. Also tried to purge xorg and reinstall and reconfigure. 

Any ideas what might be wrong?

The computer is a Dell Optiplex 9010. The outpur of "lspci -v | grep -i vga" is

```
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09) (prog-if 00 [VGA controller])
```

And the output of "sudo lshw -enable pci -class display" is

```

*-display               
       description: VGA compatible controller
       product: Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:47 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)

```

The part of the xorg.conf which could be relevant is
```

Section "Monitor"
           Identifier   "Monitor0"
   VendorName   "Monitor Vendor"
   ModelName    "Monitor Model"
EndSection

Section "Device"
   Identifier  "Card0"
   Driver      "intel"
   BusID       "PCI:0:2:0"
EndSection

```

Also here is the most recent log from Xorg (obtained via grep /drivers/ /var/log/Xorg.0.log )

```

[    19.365] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so

```

---

### Post by Dreamer Fithp Apprentice on 2013-11-05
A shot in the dark, but you might try booting in recovery mode and maybe it will be more usable while you explore solutions. I'd try different drivers.

---

### Post by Xeovke on 2013-11-06
Thanks for the reply. I tried booting in recovery mode and failsafe graphics. In both cases, there are a few menus (with various options) which appear (the display is then correct) but somehow the PC freezes before Ubuntu really start (at the end of the list of processes that are started on recovery mode, and on a black screen after failsafe).

In any case, it's possible to boot on console, I just have no idea which other drivers I could try or how to do it (change the xorg.conf?)

---

### Post by Xeovke on 2013-11-06
After playing around for a while, I can now boot in recovery mode with perfectly correct graphics... How do I make the graphic settings of the recovery mode the usual graphic settings?

For the record there are 3 error lines (EE) in the /var/log/Xorg.0.log after a recovery mode boot, here's the section which is presumably related to the video drivers...

```

[    27.093] (II) Module intel: vendor="X.Org Foundation"
[    27.093]     compiled for 1.14.3, module version = 2.99.904
[    27.093]     Module class: X.Org Video Driver
[    27.093]     ABI class: X.Org Video Driver, version 14.1
[    27.093] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
[    27.093] (++) using VT number 7
[    27.096] (EE) No devices detected.
[    27.096] (==) Matched intel as autoconfigured driver 0
[    27.096] (==) Matched vesa as autoconfigured driver 1
[    27.096] (==) Matched modesetting as autoconfigured driver 2
[    27.096] (==) Matched fbdev as autoconfigured driver 3
[    27.096] (==) Assigned the driver to the xf86ConfigLayout
[    27.096] (II) LoadModule: "intel"
[    27.096] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    27.096] (II) Module intel: vendor="X.Org Foundation"
[    27.096]     compiled for 1.14.3, module version = 2.99.904
[    27.096]     Module class: X.Org Video Driver
[    27.096]     ABI class: X.Org Video Driver, version 14.1
[    27.096] (II) UnloadModule: "intel"
[    27.096] (II) Unloading intel
[    27.096] (II) Failed to load module "intel" (already loaded, 32623)
[    27.096] (II) LoadModule: "vesa"
[    27.096] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    27.096] (II) Module vesa: vendor="X.Org Foundation"
[    27.096]     compiled for 1.14.1, module version = 2.3.2
[    27.096]     Module class: X.Org Video Driver
[    27.096]     ABI class: X.Org Video Driver, version 14.1
[    27.096] (II) LoadModule: "modesetting"
[    27.096] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    27.096] (II) Module modesetting: vendor="X.Org Foundation"
[    27.096]     compiled for 1.14.1, module version = 0.8.0
[    27.096]     Module class: X.Org Video Driver
[    27.096]     ABI class: X.Org Video Driver, version 14.1
[    27.096] (II) LoadModule: "fbdev"
[    27.096] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    27.096] (II) Module fbdev: vendor="X.Org Foundation"
[    27.096]     compiled for 1.14.1, module version = 0.4.3
[    27.096]     Module class: X.Org Video Driver
[    27.096]     ABI class: X.Org Video Driver, version 14.1
[    27.096] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
[    27.096] (II) VESA: driver for VESA chipsets: vesa
[    27.096] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    27.096] (II) FBDEV: driver for framebuffer: fbdev
[    27.096] (++) using VT number 7
[    27.096] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[    27.096] (WW) xf86OpenConsole: setsid failed: Operation not permitted
[    27.097] (WW) Falling back to old probe method for modesetting
[    27.097] (EE) open /dev/dri/card0: No such file or directory
[    27.097] (WW) Falling back to old probe method for fbdev
[    27.097] (II) Loading sub module "fbdevhw"
[    27.097] (II) LoadModule: "fbdevhw"
[    27.097] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    27.097] (II) Module fbdevhw: vendor="X.Org Foundation"
[    27.097]     compiled for 1.14.3, module version = 0.0.2
[    27.097]     ABI class: X.Org Video Driver, version 14.1
[    27.097] (EE) open /dev/fb0: No such file or directory
[    27.097] (II) Loading sub module "vbe"
[    27.097] (II) LoadModule: "vbe"
[    27.097] (II) Loading /usr/lib/xorg/modules/libvbe.so

```

some more random information: 

1- a part of the output of xdpyinfo is 

```
screen #0:
  dimensions:    1920x1080 pixels (513x289 millimeters)
  resolution:    95x95 dots per inch
  depths (7):    24, 1, 4, 8, 15, 16, 32
  root window id:    0x16d
  depth of root window:    24 planes
  number of colormaps:    minimum 1, maximum 1
  default colormap:    0x20
  default number of colormap cells:    256
  preallocated pixels:    black 0, white 16777215
  options:    backing-store NO, save-unders NO
  largest cursor:    1920x1080
  current input event mask:    0x7b803f

```

2-the output of ddcprobe

```

vbe: VESA 3.0 detected.
oem: Intel(R) Sandybridge/Ivybridge Graphics Chipset Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(R) Sandybridge/Ivybridge Graphics Controller Hardware Version 0.0
memory: 65472kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid: 
edid: 1 3
id: 1111
eisa: MST1111
serial: 00000001
manufacture: 30 2011
input: analog signal.
screensize: 51 29
gamma: 2.200000
dpms: RGB, active off, suspend, standby
dtiming: 1920x1080@68
monitorname: OptiPlex 901
monitorname: 
monitorname: 

```

---

### Post by Dreamer Fithp Apprentice on 2013-11-09
Sorry, but it beats the heck out of me. I know what I'd try though, assuming you have enough drive space. Since it happened to you after a release upgrade, I'd make a partition to install the release that was working correctly and do so. Assuming it works fine again, I'd boot the old release and compare any parts of the two that seem like they might be relevant. Some comparisons you can do with a file browser, etc. Some, you might have to reboot repeatedly alternating systems. It might help to turn any logging options you can find on. I'm particularly suspecting that you might try to install in the new system whatever version of whatever driver was working in the old one. Sorry I can't be more specific, but poking around and trying this and that as it occurs to me is about as sophisticated as I get. I'm not an expert - I just play one on the internet.

---

### Post by Xeovke on 2013-11-09
Thanks for the idea! I haven't tried to downgrade the whole system to an older version yet. Changing drivers was to no avail. After a while I decided to reinstall the distro from scratch. It turns out the problem with the display is already present when one boots to install Ubuntu from the USB stick... 

From the (perhaps superficial) similiraty of the errors I get in the Xorg.0.log and some other problems, my current "theory" is that during "normal" boot some process locks the video card and prevents the driver to configure correctly. Presumably, this process does not happen (or happens later) in recovery mode, so that the driver works fine.

There are many of these computers at the office, so I'll also try to see if the display is always distorted on any newer (USB) boot and not on an older one...

---

### Post by Xeovke on 2013-11-11
After trying 7 computers, the upshot is that old distros boot correctly, with working displays. The new 13.10 distro doesn't work on 3 computers...

[The rest of the current post is a duplicate of [this post]("http://ubuntuforums.org/showthread.php?t=2186873&p=12844845#post12844845")]

I had the opportunity to test (booting from a USB stick) 7 Dell Optiplex  9010 today. 4 display correctly and 3 don't. I kept the lshw, lspci,  xdpyinfo, ddcprobe and Xorg.0.log of all these 7 boots. Here are the  main differences in the files (except the Xorg.0.log which are not so  handy to compare as the beginning of lines are always different).

I guess that the most telling is the following line from ddcprobe. For non-correctly-displaying computers:

```
dtiming: 1920x1080@68
```

For correctly-displaying computers:

```
dtiming: 1920x1080@60
```

Is there anyway to try to force xorg to use some specific values? For  the record, there is no other ctiming or dtiming line in the output of  ddcprobe.

The configuration are otherwise strikingly similar. The only other  differences which seemed of significance (i.e. not mentionning hard  drives paritions and serial numbers) is that uncorrectly working  computers have the following extra line in lspci

```
00:16.3 Serial controller: Intel Corporation 7 Series/C210 Series Chipset Family KT Controller (rev 04)
```

Correspondingly, the lshw of these computers have the following extra section:

```

        *-communication:1
             description: Serial controller
             product: 7 Series/C210 Series Chipset Family KT Controller
             vendor: Intel Corporation
             physical id: 16.3
             bus info: pci@0000:00:16.3
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi 16550 bus_master cap_list
             configuration: driver=serial latency=0
             resources: irq:19 ioport:f0e0(size=8) memory:f7d3a000-f7d3afff

```

Lastly, in the *-pci section. Also, the *-memory *-bank:n (for n an  integer) are not of the same vendor (Samsung or Nanya technologies for  correctly-displaying computers and Hynix/Hyundai for  non-correctly-displaying ones).

I'd gladly put these 35 files somewhere easy to download if I were told how.

Should this be reported as a bug? If so how should I proceed?

---

### Post by Dreamer Fithp Apprentice on 2013-11-14
> **Xeovke said:**
>  it's possible to boot on console, I just have no  idea which other drivers I could try or how to do it (change the  xorg.conf?)Boot the distro that worked fine. I think you could do this with the live disk. Open synaptic. Install it if it isn't already there. Search likely terms like the brand name of your video card (for instance, "nvidia"), "video driver", "graphics driver", etc, It's there somewhere. Use the search, not the filter. Click on the column head for the column that shows whether they are installed or not to bring all the installed ones to the first. The answer should be in there somewnhere.> **Xeovke said:**
> After trying 7 computers . . .I salute your industry. You've been a busy fellow.> **Xeovke said:**
> I'd gladly put these 35 files somewhere easy to download if I were told how.Easy enough. Put them in a folder, zip, rar, tar, 7zip, or otherwise turn them into one archive. There are lots of free upload-and-download-it services, commonly called "file lockers", at least by the BigBrother-loving sycophants that demonize them. [http://depositfiles.com/](http://depositfiles.com/) is a popular one. I see Wikipedia has a great big list of them under the more neutral name "[SIZE=2]file hosting services[/SIZE]". Go to the page of one of them and it will be obvious what to do. Save the url you get after uploading and post it here.> **Xeovke said:**
> Should this be reported as a bug?I think so.> **Xeovke said:**
> If so how should I proceed?[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

If you still want to use 13.10 *  I can think of 2  othe ways you might try if you get tired of waiting for a more correct answer:

Install an earlier version that works and then upgrade to 13.10 with the gui upgrade tool. You might have to do it in more than 1 step (for example, if you install 12.10 you might have to upgrade to 13.04 and then to 13.10). I've done this sucessfully a couple of times when I couldn't get a new release to install properly from the standard installation media. It seemed slower than reinstallation but not inordinately so, and as I didn't time it I might be mistaken anyway. Most importantly, it worked.

The other possibility is to expand the iso of 13.10, fiddle with it's innards to correct the problem, re-compress it into an iso, burn a disk or usb stick or even use grml if you can get it to work (I never have) and install from that. If that approach appeals to you, investigate UCK. the Ubuntu Customization Kit. I never did that as looking at UCK documentation made it seem to me like a super-size pot of work. Also that approach would mean you STILL have to figure what's wrong with the standard iso before you can proceed.

Good luck.
---------------------------------------------------------------------------------------
* I'm thinking of ditching it in favor or 12.04 Precise myself - after all it has a way to go before support ends; the only ap I know of that doesn't work as well or better in 12.04 than in later editions is pcmanfm because you're stuck with a pre-1.0 version; there are several things that work better; I'm beginning to feel like a masochist useing pcmanfm anyway, even in the better versions. Thunar is SO much better and not much heavier.

---

### Post by Xeovke on 2013-11-15
Thanks for all the help Dreamer!

It turned out the bug lies in the kernel and not the drivers... Indeed, the (temporary, I hope) solution was to uninstall all linux kernels with version >=3.10 and install the kernel 3.9 (the deb files can be downloaded directly from [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9.11-saucy/")).

I put the log files there, if anyone is interested:  [http://dfiles.eu/files/njfpo8b4k](http://dfiles.eu/files/njfpo8b4k)

yeah... I'm also thinking of reverting to Precise and just install the newer versions of the programs I really need by hand. I'm not extremely satisfied with PCmanFM myself (I reinstalled Lubuntu somewhere in between the posts), I'll try Thunar in a short while. The next LTS is not so far away, so I might also just save efforts and stay with the temporary solution until then...

Thanks for everything again!

---

### Post by Dreamer Fithp Apprentice on 2013-11-15
Glad you figured it out.> **Xeovke said:**
> ... I'm also thinking of reverting to Precise and just install the newer versions of the programs I really need by hand.I'd suggest backing up the system with fsarchiver (especially handy if you have an alternate partition to boot from and the one(s) you're backing up are ext3) or Clonezilla (maybe better if your alternative boot is a CD or thumb, and I believe it deals ok with ext4) before installing newer versions by hand. I tried that with pcmanfm on Precise and borked it thoroughly. I'm not sure why. I forget, but I think maybe I installed a binary. Might have better luck compiling it locally.

---

### Post by Gerardo_Martin on 2014-04-18
Hi Xeovke, I have the same desktop model and started having the same issue when I upgraded from 13.04 to 13.10. Had to install precise and thought of upgrading to 14.04 when it came out, hoping that the problem would've been solved. Turns out that the problem is still there with 14.04, just wonrdering if you've found a workaround for this problem? Unfortunately I'm not a linux expert, but because your history exactly matches mine thought the problem must be the same.

Cheers

G

---

### Post by drwhoelse on 2014-04-23
Hi all...  I have the same problem with all 13.x and 14.04 based distro, (Xubuntu, Gnome Ubuntu, etc).  My solution was to go ahead and install 14.04, and then install and boot to older version of Ubuntu kernel-- v3.9.11-saucy

Download and install three files from Ubuntu's kernel website... [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9.11-saucy/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9.11-saucy/)

install command:   sudo dpkg -i  (three filenames)

for 64-bit system:
linux-headers-3.9.11-030911-generic_3.9.11-030911.201307202035_amd64.deb
linux-headers-3.9.11-030911_3.9.11-030911.201307202035_all.deb
linux-image-3.9.11-030911-generic_3.9.11-030911.201307202035_amd64.deb

for 32-bit system:
linux-headers-3.9.11-030911-generic_3.9.11-030911.201307202035_amd64.deb
linux-headers-3.9.11-030911_3.9.11-030911.201307202035_all.deb
linux-image-3.9.11-030911-generic_3.9.11-030911.201307202035_amd64.deb


Reboot and choose version 3.9.11.xx in GRUB boot manager

---

### Post by drwhoelse on 2014-04-25
Correction:

[COLOR=#000000]for 32-bit system:[/COLOR]
[COLOR=#000000]linux-headers-3.9.11-030911-generic_3.9.11-030911.201307202035_i386.deb[/COLOR]
[COLOR=#000000]linux-headers-3.9.11-030911_3.9.11-030911.201307202035_all.deb[/COLOR]
[COLOR=#000000]linux-image-3.9.11-030911-generic_3.9.11-030911.201307202035_i386.deb[/COLOR]

---

### Post by mtornos on 2014-06-07
Any news about this? I've got the same Dell 9010 AIO and have the same issue. Living with a 2-years-old kernel is not a pretty thing... :'(

---

### Post by eric-daniel-decarvalho on 2014-06-18
Yes, I replicate the error 3 times on new instalations, and a simple FSCK in recovery mode solves the problem on a model Optiplex AIO 9010.

---

### Post by mtornos on 2014-06-18
> **eric-daniel-decarvalho said:**
> Yes, I replicate the error 3 times on new instalations, and a simple FSCK in recovery mode solves the problem on a model Optiplex AIO 9010.
What do you mean exactly?


[LIST=1]
[*]To entry in recovery on every boot, to make an fsck and continue boot?
[*]Doing the same just one time makes the display works forever?
[*]What's the relation between an fsck (file system check) and the wrong dtiming kernel detection?
[/LIST]

Thanks.

---

### Post by eric-daniel-decarvalho on 2014-06-18
> **mtornos said:**
> What do you mean exactly?


[LIST=1]
[*]To entry in recovery on every boot, to make an fsck and continue boot?
[*]Doing the same just one time makes the display works forever?
[*]What's the relation between an fsck (file system check) and the wrong dtiming kernel detection?
[/LIST]

Thanks.

1. enter in recovery every boot solve the problem because the recovery use an other kernel.
2. sadly this method don't work forever exept if you install an old kernel.
3. nothing (sorry I made a hasty conclusion and I'm off topic).

---

### Post by mtornos on 2014-07-05
Working! Just installing latest 3.15 kernel (I tried 3.15 RC8 and 3.15.3 from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/).


It works like a charm!


files to download 3.15.3 for 64-bit system:


 - linux-headers-3.15.3-031503-generic_3.15.3-031503.201407010040_amd64.deb
 - linux-headers-3.15.3-031503_3.15.3-031503.201407010040_all.deb
 - linux-image-3.15.3-031503-generic_3.15.3-031503.201407010040_amd64.deb


files to download 3.15.3 for 32-bit system:


 - linux-headers-3.15.3-031503-generic_3.15.3-031503.201407010040_i386.deb
 - linux-headers-3.15.3-031503_3.15.3-031503.201407010040_i386.deb
 - linux-image-3.15.3-031503-generic_3.15.3-031503.201407010040_i386.deb


Type in terminal:


    sudo dpkg -i *.deb

---

