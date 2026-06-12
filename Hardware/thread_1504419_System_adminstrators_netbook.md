---
title: "System adminstrators netbook?"
date: 2010-06-08
forum: Hardware
---

### Post by gopher2x on 2010-06-08
Folks I going to buy a netbook soon, I would like to know what is good for a linux user? I need to have all drivers supported natively in 2.6 Linux, incuding wifi packet injection. No ndis stuff. Must have a long battery life. I would like all power controls supported including suspend, resume, and hibernate. A working Bluetooth device is also neccessary. I would like a core CPU or better, no celeron crap. 10/100 Ethernet , matte finish screen, with 1024 or better resolution. 1394 would be cool but not neccessary. Need at least 80 gigs HD and 1 gig ram..  More would be cool too  . Durability is also important. Doesn't have to be as strong as a toughbook, but better than the pos toshiba Quality I'm used to. Graphic card is not important, as long as Linux drivers work, I really don't even need 3d accelleration. Only using Xorg/twm .  I know this is alot of demands but I want to know what do you fellow ubuntu users reccomend ???? Thanks!

---

### Post by jerenept on 2010-06-08
[System76]("http://www.system76.com")

They come with Ubuntu built in.

---

### Post by farbird on 2010-06-08
i used the msiwind u100plus and i find it quite good.

---

### Post by GSF1200S on 2010-06-09
Asus 1005HA-P is another option. Heres some info about mine currently:

Asus 1005HA-P eeepc (You want the P; the B and V have lesser batteries).
2GB RAM, 667Mhz FSB, 1.66Ghz Intel Atom N280, 160GB hard drive, wireless n/g/b + bluetooth, 2MP webcam, built-in mic
Arch Linux + eeepc netbook kernel (from AUR)
LXDE (+firefox, qualculate-gtk, filezilla, abiword, guayadeque, vlc, gnome-power-manager, conky, pidgin, skype, xchat, links). I could shave some weight by using irssi, a different ssh/ftp client, and possibly a different web browser, but im partial to the programs listed. RAM usage at boot is 59.4 MB, and I average 150MB when browsing the web (Firefox uses more RAM than the kernel and LXDE+conky+X!). While im using Arch on the netbook, you could use an Ubuntu minimal ISO and build a barebones LXDE, openbox, fluxbox, etc desktop that would save CPU and RAM over biggies like KDE, Gnome, and even XFCE. 

Battery life: 9.5-10 hours (im not kidding) idle. 8.5 hours average use. This is with all devices disabled except USB and wifi. With the other devices enabled, shave an hour off the times listed. The eeepc is a fairly good option because there many scripts available that allow you to kill devices on the fly (essentially switching them off in BIOS which lowers power usage).

Bigger batteries are available (more bulk and weight though).

There are many other good netbook options as well, but you would likely enjoy this one.

---

### Post by gopher2x on 2010-06-16
Well I took your advice. I am sitting in front of a brand new 1005HA-P. So far so good. I did a quick wubi install, seems like everything is working so far. Will be wiping the windows 7 off. I have something like 80Gigs free on a 250GB hard drive, out of the box only thing i gotta figure out is why the touchpad click button is so hard to push down... perhaps if i get some time i will do a in depth review of the linux install and usability
thanks again  GSF

---

### Post by GSF1200S on 2010-06-16
> **gopher2x said:**
> Well I took your advice. I am sitting in front of a brand new 1005HA-P. So far so good. I did a quick wubi install, seems like everything is working so far. Will be wiping the windows 7 off. I have something like 80Gigs free on a 250GB hard drive, out of the box only thing i gotta figure out is why the touchpad click button is so hard to push down... perhaps if i get some time i will do a in depth review of the linux install and usability
thanks again  GSF

Ha! And you got the better 250GB drive- I have the 160GB. I think the reason you only have 80GB free is because the hard drive comes stock partitioned into two seperate ntfs partitions. What I ended up doing is wiping the whole drive and partitioning Arch for /boot, swap, /, and /home. However, keep something in mind (I didnt know this until recently)- there is a 8MB EFI partition on the drive- dont remove it unless you dont care about the BootBooster function (where you skip the BIOS screen when you turn the computer on). Remember- due to archaic rules (nothing to do with Windows or Linux), you can only have 4 primary partitions (one of which is the EFI partition), so partition your partitions inside an extended partition.

I really suggest building a very minimal Linux install. Gnome, KDE, and many heavy programs tax the hard drive often and consume more RAM. Ubuntu Netbook Edition's battery life was not very good for me (way worse than Windows XP), but my current Arch install lasts a good hour and a half longer than my Windows install did (at idle). The things to make sure you have for power savings: Asus Super Hybrid Engine software (controls FSB speeds, etc), cpu frequency scaling, Eeepc acpi scripts for using hotkeys/turning off hardware, laptop-mode tools (an awesome FLEET of powersaving stuff), and Intel's powertop. Go as minimal as you can stand for a desktop environment (trust me- LXDE is AWESOME on a netbook), and try to install programs that have the least amount of dependencies. As I said too, there might be a custom kernel for the 1005HA for Ubuntu, as there is for Arch. You might want to spring for VLC and Firefox as they are very good programs (some like Chrome for netbooks).

If you go Firefox, get the following extensions to maximize screen space:
Hide Caption Titlebar Plus Smart (Eliminates title bar and integrates min/max/close bar into the address bar).
Fission (Make sure to adjust preferences to include connection data and URL goto links).
Compact Classic theme
Compact Classic Options (Set scrollbar to native, set window border to none).
Adblock/NoScript/Flashblock (The less crap you load, the faster the page renders, the less juice you use).
Compact Menu 2 (Eliminates Menu Bar).
Tab Utilities (Does what Tab Mix Plus does, only its lighter).
Tab Group Manager (Optional- allows you to unclutter the tab bar by seperating tabs into different groups).
Remove the bookmarks toolbar, status bar, menu bar.

Id give you the Ubuntu package names for the powersaving stuff, but Im not on Ubuntu at the moment. Here is all of the links for the Arch pacakges so you can go to the homepages/find .debs/find out the repo names:

Eeepc acpi scripts (this allows Super Hybrid Engine as well- in order to tell what its doing, you need a notification system like notify-osd, notification daemon, or dzen2 which is my favorite): [http://aur.archlinux.org/packages.php?ID=23318](http://aur.archlinux.org/packages.php?ID=23318)
Custom Kernel for eeepc: [http://aur.archlinux.org/packages.php?ID=34625](http://aur.archlinux.org/packages.php?ID=34625)
Laptop Mode Tools: [http://www.archlinux.org/packages/extra/any/laptop-mode-tools/](http://www.archlinux.org/packages/extra/any/laptop-mode-tools/)
Intel's Powertop: [http://www.archlinux.org/packages/community/i686/powertop/](http://www.archlinux.org/packages/community/i686/powertop/)
CPU Frequency Scaling Utils: [http://www.archlinux.org/packages/extra/i686/cpufrequtils/](http://www.archlinux.org/packages/extra/i686/cpufrequtils/)
Firefox Branded (Arch runs development versions which may not work with some sites doing a user agent string check- use this package or install User Agent Switcher extension in the version installed- not an issue on Ubuntu at all unless you run a Mozilla PPA): [http://aur.archlinux.org/packages.php?ID=18019](http://aur.archlinux.org/packages.php?ID=18019)

Remember, if you end up trying Arch, these can be installed from the repos, or using an AUR helper like yaourt, bauerbill, or clyde (bauerbill FTW for me). Ubuntu can be very lean and mean if you start with just a kernel and work up. Finally, I give you the Arch Wiki link for the 1005HA, which is useful for setting up Arch or Ubuntu:

[http://wiki.archlinux.org/index.php/Asus_Eee_PC_1005HA](http://wiki.archlinux.org/index.php/Asus_Eee_PC_1005HA)

Keep in mind, Ubuntu might be a bit easier to deal with (as well as easier to grab software on the fly), so that might be a better work option. Hope all this helps :)

**EDIT** As an extreme idea, consider setting up Firefox to store all of its cache data in /tmp, and setup /tmp and /var/log as temporary filesystems running in RAM. Please note, doing this will increase RAM usage slightly (not too big a deal with LXDE), and your logs will dissappear every reboot- only do this if you know you wont want/need those logs. I made a copy of Pacman's (Archs package manager) log file before I set this up, and add to it myself when I install/remove stuff. ANY action that reduces hard drive usage and allows the drive to "sleep" reduces wattage used and increases battery life. Prolly the best way to get insane battery life would be to create a custom PCLinuxOS install on USB drive, and edit its fstab to mount your hard drive for anything you wish to permanently save. PCLOS allows you to load the whole OS into RAM- only do this if you have the 2GB upgrade otherwise youll run out of RAM space.

As a barometer, Im currently using 6.1-6.4 watts (listed in PowerTop) with the screen all the way down (brightness), all devices except wifi and USB disabled, and Super Hybrid Engine powersave mode enabled. I know I can get it lower, but its good enough for me.

**EDIT 2** Just did some more tweaking in the laptop-mode-tools config files- wattage now sits 5.6 to 5.9 watts at idle.

---

