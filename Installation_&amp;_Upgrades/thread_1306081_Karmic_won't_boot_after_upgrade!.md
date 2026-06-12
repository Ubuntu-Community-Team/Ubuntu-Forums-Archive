---
title: "Karmic won't boot after upgrade!"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by pablo180 on 2009-10-30
I upgraded to Karmic from Jaunty yesterday, but although everything seemed to go OK, upon reboot it just stops shortly after:

```
* Starting init crypto disks... [ OK ]
modem-manager: Loaded plugin Option High-Speed
```

It then loads several other plugins. If the internet isn't plugged in, it stops here if it is it does:

```
Stopping NTP Server Done.
Starting NTP Server Done.
```

At which point it stops dead and the hard drive appears to stop spinning. 

I cannot get into a shell, I've tried recovery, but that does the same thing. It appears to be waiting for something but I have no idea what. 

The LiveCD worked fine, and all other upgrades have been fairly painless but this has totally tanked my laptop, does anyone have any ideas on what I can do?

I have a backup so can put everything back, but this is the second attempt at an upgrade with the same result. 

This is on a Dell 1525
1.86GHz CPU
1GB RAM
Intel X3100 Graphics
120GB Samsung SATA HD
Wireless Disabled.

---

### Post by pablo180 on 2009-10-31
I have finally got Karmic working, now I am not sure whether it was something that I did, or whether there has been some bug fixing going on behind the scenes, but the last upgrade worked. 

I thought that I had best post what I did just in case it helps someone else. I had tried the Standard Upgrade, Alternative CD upgrade, the RC upgrade, and all had the problem above, so finally I tried the standard upgrade again through Update Manager. 

This time however I whenever I was offered an option to change a configuration, rather than selecting 'Keep' I chose 'Update to Maintainers Version' (or something like that), including menu.lst. Everything went as before. 

At the end when I was given the option to remove obsolete packages, I kept them, and then restarted. This time things went much better and I got as far as

```
checking battery state....done
```

before the screen started flashing weirdly. I rebooted and started in recovery mode, which worked this time. I first selected:

```
dpkg Repair broken packages
```

That took some time but cleared out all the stuff that I had left previously. Then I selected 

```
grub Update grub bootloader
```

I thought that my flashing screen may be to do with the graphics drivers, I have the Intel X3100 chip, so selected:

```
netroot Drop to root prompt with networking
```

In order to download another Intel driver. Once in the prompt, I wrote:

```
sudo apt-get install xserver-xorg-video-intel
```

That installed. I then selected:

```
resume Resume normal boot
```

And it booted into Karmic!

The graphics were a bit patchy to say the least, probably worse than Jaunty, so I added the PPAs at: [http://launchpad.net/~ubuntu-x-swat/+archive/x-updates](http://launchpad.net/~ubuntu-x-swat/+archive/x-updates) to get the latest updates. I then ran Update Manager, installed the updates and rebooted and everything was then much, much faster and smoother. 

Karmic is quite good so far, but no way was it worth this three day slog of Upgrading > Restoring Backup > Upgrading again > Restoring Backup...

I certainly won't be in any rush to upgrade again.

---

### Post by jstgtpaid on 2009-11-09
I have the flashing screen issue as well.  I am using a Nvidia card, so I suspect the issue may not be your intel drivers.

I tried to fix the issue with new drivers and it only decreased the number of times the screen flashed.  But the problem remained.

I finally decided to just erase the HD and start over, but then I ended up with the NTP problem where it would not log in.  (sigh)

I am going to try another distro to see if I can get it up and running...

---

