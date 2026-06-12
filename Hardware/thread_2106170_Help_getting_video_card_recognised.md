---
title: "Help getting video card recognised"
date: 2013-01-18
forum: Hardware
---

### Post by beneix on 2013-01-18
I am a n00b on Linux, so be gentle.

I have an old laptop with little memory and some other hardware limitations, the most relevant for this post being:

Toshiba Portegé 2000
256 MB RAM
USB 1.1, not bootable
No CD*

*) I say "No CD" - actually, I have an external CD-ROM that attaches via PCMCIA and is bootable by DOS and Windows, but all Linux Live CDs I have tried stall somewhere in the boot process so I have given up on a CD-based install.

Because of the memory, I have been trying to install lightweight distros. I previously managed to get Linux Mint XFCE installed and working, but it was very slow so I thought I'd try Xubuntu.  Before landing on Xubuntu, I tried Lubuntu but that didn't work out, probably for a reason similar to what I am about to describe for Xubuntu -- related to the video card not being picked up.

I started the whole process by using the existing Linux Mint's GRUB2 to start an install from files I had put on the USB stick using [Rufus]("http://rufus.akeo.ie/") (the laptop can't boot from the USB, but Linux can access the USB once started by GRUB). Using that method, I have tried so many combinations of graphical and alternate installers,  Lubuntu, Xubuntu and Kubuntu that I have now spent several days on  this.

Finally, the Xubuntu 12.04 Live CD started and gave me a full, 1024x768, pretty ;) desktop.  However, because the USB interface is only 1.1, it was incredibly slow.  The full Live CD desktop took about 30 minutes to appear.  After I clicked on "Install XubuntU", the laptop was ostensibly doing something (and the access light on the USB stick kept flashing) -- but after five hours I gave up and decided to try the alternate installer.  The fact that the live CD seemed to have the right video drivers was promising.

The alternate install went well, but I now only get a text interface, no GUI.  Here are some diagnostic outputs:

lshw -C display
```
  *-display UNCLAIMED
       description: VGA compatible controller
       product: CyberBlade XPAi1
       vendor: Trident Microsystems
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 82
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm vga_controller bus_master cap_list
       configuration: latency=8
       resources: memory:fc000000-fdffffff memory:fbc00000-fbffffff memory:f8000000-f9ffffff memory:f7ff8000-f7ffffff memory:10100000-1010ffff
```lspci -nnk | grep -iA2 vga
```
01:00.0 VGA compatible controller [0300]: Trident Microsystems CyberBlade XPAi1 [1023:8820] (rev 82)
    Subsystem: Toshiba America Info Systems Device [1179:0001]
    Kernel modules: tridentfb
```lsmod
```
video                                   19068  0
```xrandr -q
```
Can't open display
```
So I have spent a couple of days reading up on the Trident CyberBlade XPAi1.  There is a bug in 12.10 for Trident so I tried 12.04. No luck. I have then found no end of posts on the internet with different suggested xorg.conf definitions for this card (see links below). I have tried about a dozen different permutations of these, both placing them in /etc/X11/xorgs.conf (which doesn't exist from scratch on my system but I just used vi to create it), and by creating /usr/share/X11/xorg.conf.d/99-monitor.conf with the same contents.  No luck.  All of these configurations, which others have successfully used with the same card, are for older versions of Ubuntu or other distros -- I haven't found anything for 12.04.

I tried installing xserver-xorg-video-trident.  I have tried editing boot options by pressing "e" in the GRUB2 menu, such as "nomodeset" etc.

All to no avail -- it is almost as if none of the changes I make have _any_ effect.  Perhaps it all comes down to the fact that no display is being picked up, so the changes I make to xorg.conf etc. are moot?

I am now at the end of my tether.  Please, does anyone have ideas?  If the Live CD works fine, why should not the installed system?  As a n00b, am I missing something fundamental -- should I do something after updating xorg.conf/99-monitor.conf, other then reboot?

Some links:
[Known bug - release notes for 12.10]("http://list-archives.org/2012/10/16/lubuntu-users-lists-ubuntu-com/release-notes-for-12-10-some-known-problems-with-video-drivers/f/3550383332")
xorg.conf definitions for the Cyberblade XPAi1: [here]("http://ubuntuforums.org/showthread.php?t=806835"), [here]("http://michaelminn.com/linux/toshiba1800/"), [here]("http://ubuntuforums.org/showthread.php?t=1098092"), and [here]("http://forums.fedoraforum.org/archive/index.php/t-227488.html") (just some of the ones I tried).
[Good note on troubleshooting video]("http://ubuntuforums.org/showthread.php?t=1743535")

---

### Post by dabl on 2013-01-18
Couple of thoughts (in addition to the obvious fact that you are whipping a very aged horse -- he probably can't run anymore ...):

- Bring up the xubuntu live CD again, and when it finally finished loading, take a look in /etc/X11 and see whether there is an xorg.conf file there (there may not be).  Also run ```
lsmod | grep video
``` and see what video driver module(s) is/are loaded.

- try some other linux live CDs.  Even Xfce is quite a load to put on that old GPU.  Try some LXDE Live CDs, for example, the 32-bit siduction LXDE version.  Also the 32-bit Bodhi Linux (E17) is probably worth a shot.

- if you find one that pleases you in live CD mode, then there is a way to [**[color=green]"boot fromiso"[/color]**](http://manual.siduction.org/en/hd-install-opts-en.htm#fromiso), at least for the Debian ones.  I would expect that approach to perform much better than a conventional hdd installation, on your hardware.

BTW, doesn't that Portege 2000 have an SD card reader?  Is it perchance a USB interface?  If yes, then it can boot a "Live CD" ISO installed on the SD card with something like unetbootin.

---

### Post by beneix on 2013-01-21
Thanks dabl for the tips.  Using the BootISO method (great feature of GRUB2, not very well publicised!) I managed to install Lubuntu 10.04 and it worked from the get-go.  I just had to create an xorg.conf file to increase the resolution from 800x600 to 1024x768.

I remain puzzled as to why I can't get 12.04 or 12.10 to work with an identical xorg.conf (or any xorg.conf for that matter).

Lucid will do me for now, but of course it is going to be deprecated fairly soon.

I haven't yet tried siduction or Bodhi, but I did try Archlinux and AntiX -- neither would boot to a GUI.

On a separate topic, I installed Midori as a less RAM-hungry alternative to the included Chromium browser.  Why can't I find Swiftweasel in the repositories?  Would I really need to go through the whole rigmorale of compiling from source if I want to use Swiftweasel on Lubuntu Lucid?

---

### Post by Mark Phelps on 2013-01-21
> **beneix said:**
> ... I remain puzzled as to why I can't get 12.04 or 12.10 to work with an identical xorg.conf (or any xorg.conf for that matter)...

Have you considered that the different Ubuntu versions nearly always have different X-server versions -- and those video drivers simply may not work with newer X-server versions?

Mentioning this because I have a still-current AMD HD 4290 video chipset in my desktop, and the new AMD drivers will not work with it and Ubuntu 12.10 because that uses a newer X-server version than is supported by the driver version that works with that chipset.

---

### Post by beneix on 2013-01-21
> **Mark Phelps said:**
> Have you considered that the different Ubuntu versions nearly always have different X-server versions -- and those video drivers simply may not work with newer X-server versions?
Yes, I had that suspicion also. If that is indeed the case, it is just a shame, as it leaves users with certain equipment a bit stuck with old versions. And - why does it work on the Live CD?!?! (I still need to do some investigation as proposed by dabl above - it just takes such a godawful long time to do with the limitations of my hardware, that it has a low priority right now...)

---

