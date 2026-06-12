---
title: "64-Bit Edgy Eft on Dell Latitude D620: Report and Problems"
date: 2007-01-09
forum: Hardware &amp; Laptops
---

### Post by MikeBuffer on 2007-01-09
Here's is information on progress and problems in getting 64-bit 6.10 (Edgy Eft) to install on a Dell Latitude D620. You might find this helpful if you're doing something similar, or you might be able to help me with the problems I've noted if you've previously encountered them.

**Summary:** I've got most things working, but a couple of simple things (plugging in/out AC, adjusting the brightness) cause the system to freeze, as listed at the end.

**Hardware:** 

The Latitude D620 is a fine laptop for professional use, especially with the mobile Core2 Duo CPU. With its 85 WHr battery, I get up to 5 hours' use from it. Main specs of my machine:
[LIST]
[*]Core 2 Duo T7400 CPU (2 64-bit 2.16 GHz processors)
[*]WXGA+ screen, 1440*900
[*]Integrated Intel 950 graphics (boring)
[*]2GB RAM
[*]Integrated bluetooth, usual ports and networking
[/LIST]

**Booting from LiveCD:**

[LIST]
[*]Press F6, add **notsc** to kernel command (otherwise, hangs within a few minutes of use)
X server does not start; need to set display properties as below -- aiming for good enough to run partition editor and installer. Still needed extra work to get correct resolution (see later heading)
[*]Kill Gnome Display Manager: 
[B]ps -ax | grep gdm 
sudo kill -9 <id>[/B]
[*]Set the display properties: **sudo dpkg-reconfigure xserver-xorg** and set graphics card to **vesa**
[*]Restart GDM: **sudo /etc/init.d/gdm start**
[*]Wireless network: just enable with System – Administration – Networking, specifying properties. Only issue I noted was that it didn't work if ESSID was not broadcast
[*]Wired network also works
[/LIST]

**Partitioning and Installation:**

[LIST]
[*]Did full backup in advance using Windows Backup to a secondary HD
[*]Partitioned using Gnome Partition Editor (under System menu) from Live CD
[*]Had to defragment drive in Windows and run** chkdsk -f** before I could partition
[*]Reduced the Windows partition (NTFS) and added an extended partition with two logical partitions: an EXT3 partition for root with most of the space, and 4 MB linux-swap partition 
[*]Installation was very straight-forward; nothing to note
[/LIST]

**Post-Installation Configuration:**

[LIST]
[*]**Widescreen:** Lots of threads about this on UbuntuForums.org; the following one worked for me: [ http://ubuntuforums.org/showpost.php?p=1699507]("http://ubuntuforums.org/showpost.php?p=1699507")
[*]**Suspend, Hibernate, Microphone, Touchpad:** I applied the fixes listed here (though suspend/hibernate are still problematic) [ https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeD620]("https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeD620")
[*]**Bluetooth:** Enabled by default; to connect a bluetooth mouse, I just put it into "find me" mode and run **sudo hidd –search** (set this up as a custom command on the panel for convenience)
[/LIST]

**Accessing My WinXP NTFS Partition:**

[LIST]
[*]NTFS-3G works well, allowing me to read and write to this partition; followed instructions here: [ http://ubuntuforums.org/showpost.php?p=1918655&postcount=1122]("http://ubuntuforums.org/showpost.php?p=1918655&postcount=1122") except that Step 1 is not needed in 64-bit Edgy
[/LIST]

**Current Open Problems:**

My main annoyance is that the system freezes if I use the function keys to adjust the LCD brightness or if I plug in or out the AC adaptor. I don't know how to unfreeze it; I have to power it down every time. 

I've updated the BIOS from A04 to A07(latest version) but it made no difference. Other special buttons like the volume ones work fine. I note that these actions cause freezes from as soon as the monochrome Ubuntu bootup screen is displayed. These are quite a pain, particularly having to shut down my computer because I see that the battery is low and I need to plug in the AC.

Standby and Hibernate are not working correctly either, but I haven't given them much attention.

The external monitor output does not work out of the box either. This is something that I'll need to fix soon, as I like to plug in a full-size keyboard and large monitor when I'm in the office.

---

### Post by falmonte on 2007-01-10
I have the sames issues with my latitude d620. Suspend/hibernation doesn't works and any of Fn's combinations too. I install ubuntu 6.10 with an amd64 linux kernel 2.6.15-27-amd64-generic, this is the 6.06 kernel version. The 6.10 kernel version doesn't work fine.

Laptop:
centrinu duro T5500
2GB of ram
WXGA screen
Integrated Intel 950 graphics

**Problems:**
FN keys (Standby, hibernation, CRT/LCD and brightness )
hibernation/suspend

After do a suspend/hibernation it doesn't come back. I try with this procedure, but the hibernation/suspend doesn't work yet.
[https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeD620](https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeD620)

The rest work fine: keyboard, touch pad, wireless intel 3945abg, ethernet, screen resolution, dual core detected, Serial ATA hard disk.

No tested:
modem
pcmcia
infrared port

Thanks.

---

### Post by ian-johnson on 2007-01-27
Hey Guys.  I gave up installing Edgy on my Dell D620.  But I did manage to get Dapper up and running with only a few issues.  My function keys for LCD brightness work just fine.  No issues with plugging or unplugging AC power.  Wireless didn't need any configuration (a first for me with Ubuntu).  Only problem that I cannot fix is suspend/hibernate.  I can live with this.  I will probably screw this all up by trying an upgrade to Edgy from Dapper to see if it works.

---

### Post by lotus49 on 2007-01-31
It's odd that with the same machines we have had fairly different experiences.

First of all I installed Edgy Eft (6.10) on my Dell Latitude D620.

The X server started up fine in 1024x768.  I haven't tried the widescreen res yet as I'm more interested in my wireless card (see below).

Power works fine in that I can plug/unplug the AC without any problem and it detects the change.

I can change volume and brightness with the keyboard perfectly well (although the screen doesn't automatically dim according to ambient light levels).

Wired network fine.  Wireless network not.  The wireless card is recognised (obvious physically turned on at switch) and I can configure it, but nothing happens.  ifconfig reports that it is up but with no IP address.  When I click on the appropriate wireless network icon in the menu bar it reports that the card is disconnected with 0 signal but the green wi-fi light is flashing away.

PCMCIA also works.

Suspend doesn't, haven't tried hibernate.

The only thing I'm really bothered about is wireless.

---

### Post by shutterbc on 2007-02-01
Well, there are a few other D620 threads going on, but I'll share my experience here.

I have a D620 from my company that's a plain Core Duo (no 64-bit) and NVIDIA Quadro NVS graphics.  I installed Edgy (6.10) and had the following problems:

[LIST]
[*]Sound worked beautifully until I installed a kernel image update, now oss works but alsa doesn't.
[*]Suspend / hibernate didn't work until I implemented suggestions on LaptopTesting wiki.  Also it only works when I use nvidia nonfree drivers and don't use Beryl.
[*]Multiple monitor support doesn't work and I haven't tried to fix it yet
[/LIST]

---

### Post by MikeBuffer on 2007-02-03
Hi all,

Thanks for the comments. 

Lotus, it is indeed odd that we are all having different experiences, though I suppose that in part it is due to the wide range of config options available for the D620.

Lotus, your wireless network problems sound like it's just not configured perfectly for your network -- the light flashes when the card is active but not on a network, and is on steady when connected. Check the settings for SSID, WEP, etc. I found that my machine couldn't connect to the network if the network was configured not to broadcast its SSID. Also, if you have MAC address control on the router and this is a new laptop, the router might be rejecting the connection from it. If you have control over the wireless router, a useful approach for debugging is to disable any form of security and try to connect again. Obviously you won't want to leave your network open for long, but it's a good starting point.

Ian and Lutus, did either of you install the 64-bit version? Obviously you can't have, Shutterbc.

Falmonte, you state that you installed the 64-bit version. Any progress in fixing issues? 

For my own part, I have support for external monitors working, but it's quite a hack: [this script]("http://ubuntuforums.org/showpost.php?p=1419734&postcount=96") rewrites xorg.conf as appropriate for different layouts (dual, xinerama, clone, single) and you have to restart the system after.

Mike.

---

