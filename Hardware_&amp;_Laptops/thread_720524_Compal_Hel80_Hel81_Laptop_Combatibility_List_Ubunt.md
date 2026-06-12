---
title: "Compal Hel80 Hel81 Laptop Combatibility List Ubuntu Gutsy 7.10 x86"
date: 2008-03-10
forum: Hardware &amp; Laptops
---

### Post by mlapaglia on 2008-03-10
I've been running Ubuntu Edgy, Feisty, and Gutsy on my Compal Hel80 and Hel81 laptops for a little over two years, and I'd like to help anyone else trying to do the same. The differences between 80 and 81 are the video card, processor, ram, resolution, and hard drive size. I'll differentiate the two. Some of the parts in each laptop overlap, so if something is missing look in at the other model.

**Compatible Harware (Hel81):**
_Intel Core Solo 1.66 GHz Processor:_ Works OOB
_Intel GMA 950 Video Card (1280x800):_ Works OOB
_Intel/Pro Wireless 3945 (a/b/g):_ Works with restricted drivers enabled
_CD/DVD Burner Reader:_ Works OOB
_Gigabit Ethernet Adapter:_ Works OOB
_USB Ports:_ Work OOB
_6-Cell Li-Ion Battery:_ Works with power management system OOB.
_Side Panel Buttons (Play/Stop/Rewind/Fast Forward/etc):_ Works with all multimedia OOB
_Sidewalker Buttons (Internet, Link 1, Email, Link 2, etc):_Works with email clients, firefox OOB
_Sound (headphones, integrated and external microphone):_ Works OOB
_Touchpad:_ Works OOB

**Incompatible Hardware (Hel81):**
_Integrated ENE 3-in-1 Card Reader:_ Only SD card works, Sony memory stick doesn't. no DMESG reports when inserting card, I haven't been able to find anyone who has gotten it to work.
[U]
Microdia Integrated 1.3M Web Cam:[/U] Only drivers that work you have to pay for, and don't offer anywhere near decent quality for usage. There is a google group developing a driver for this camera's chipset, but it isn't anywhere near ready yet.

**Compatible Hardware (Hel80):**
_Intel Core Duo T2500 2.0 GHz Processor:_ Works with power managment OOB
_nVidia Geforce Go 7600 Video Card:_ Works with restricted drivers (and also envy's drivers) and with external output OOB
_15.4" WSXGA+ (1680x1050) LCD Screen:_ Works with brightness changer OOB
_Intel PRO/Wireless 3945 (a/b/g):_ Works with restricted drivers OOB
_2 GB DDR2 Memory:_ Fully utilized OOB
_9-Cell Li-Ion Battery:_ Works with power managment OOB
_Bluetooth Wireless Adapter:_ Works OOB, some issues with bluetooth manager program, I end up using the config file manually every time I install, much much easier and more reliable, but it works fine.
_Combo DL DVD Burner:_ Works OOB
_Fingerprint Scanner:_ Works with additional driver installation and program setup. A bit unusable right now if you don't know what you are doing, but it has the ability to use a fingerprint to login to the computer, and to launch administration abilities. No GUI after initial setup as of this writing, you have to remember to do it when you login or it won't let you. After a successful finger scan setup and veification, all 10 fingers can be used for identification.
_Sound (headphones, audio in/out, integrated microphone):_ Not sure what this computer actually has because I've never had problems with it. Works OOB
_Touchpad (with the slider thing to scroll webpages):_ Works OOB
_Function buttons (Enable wireless, sleep, toggle screen output, brightness up/down, volume up/down, play, stop, pause, etc):_ Works OOB

**Incompatible Hardware (Hel80):**
Same as the Hel81

**Installing Ubuntu**
Everything works normally. The computer has a tendency to spin down the dvd drive during installation, and it has to spin back up before it can be accessed. Not using the laptop during installation speeds up things.
After installation completes sometimes gnome won't start correctly on the first boot. A restart seems to fix this.
Installing updates is quick and painless. Restart your computer, get envy and install the latest nVidia drivers, both the program and the drivers without a problem.
After this I install all my programs/codecs/dvd playback/media players, etc, etc. I've never had any issues.

**If you want to get Compiz-Fusion working with the latest sources,**
I run two scripts that make Ubuntu run under XGL *flawlessly*.
The first script is a bulletproof installer of compiz-fusion, but it doesn't use the latest sources. It does however, install every dependancy, including xgl (which is normally pretty hard to get working for an average user)
[http://disk.jabbim.cz/henrich.gron@jabbim.sk/bp-compiz.tar.gz](http://disk.jabbim.cz/henrich.gron@jabbim.sk/bp-compiz.tar.gz)
or
[http://forum.compiz-fusion.org/attachment.php?attachmentid=583&d=1198656902](http://forum.compiz-fusion.org/attachment.php?attachmentid=583&d=1198656902)

after that is installed, go into synaptic and install the emerald engine. Not sure why this is required, but you won't get window borders without it. restart, uninstall using the script. The script leaves all of the dependencies installed, but removes compiz-fusion.

Now use this script for maintaining compiz-fusion. It has excellent support and is very customizable for people wanting a bit more.
[http://elemongw.exofire.net/projects/linux-section/git4cf-automator/](http://elemongw.exofire.net/projects/linux-section/git4cf-automator/)

After that restart, and everything should be working peachy.
Using the git4cf automater software (google it)


**Other**
Standby and hibernate do not work well on either the Hel80 or Hel81 laptops. the 80 has a 50/50 chance with it's nVidia card, and the 81 doesn't work at all.

I don't have the integrated TV tuner installed, so I can't comment on that.

Overall I'm pleased with Ubuntu on this style of laptop. The non-linux friends love the ease of use, stability, and the comments they get about compiz running on their laptops.

There is a BIOS bug with acpi, currently hasn't been solved, although it hasn't affected me very much.

If anyone has questions about hardware issues or trying to get something working like I have feel free to send me a PM.

---

### Post by rafaelxc on 2008-03-11
Hello,
I have the same laptop. But i'm having some problems.

The wireless card have the restricted driver installed but is not working.
The lshw output shows:
 configuration: driver=pcieport-driver
           *-network UNCLAIMED
                description: Ethernet controller
                product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
                vendor: Atheros Communications, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix cap_list
                configuration: latency=0

And my display is showing a plug and play device which I can only use the native resolution. I cannot change the display resolution. I've changed the xorg.conf but no joy.

I hope someone can help me.

---

### Post by rafaelxc on 2008-03-12
Hey any idea guys?
 
I really need a help on this....:confused:

---

### Post by mlapaglia on 2008-03-24
that isn't the same wireless card as the one i have... take a trip down google lane if you haven't already.

as for your graphics, if you haven't already install envy and put those drivers in, then use nvidia-settings to configure your xorg. the defauly ubuntu one doesn't work very well for me. just don't use both of them, which really causes problems. i set all of my video settings through the nvidia-settings program and its all peaches and cream :)

---

