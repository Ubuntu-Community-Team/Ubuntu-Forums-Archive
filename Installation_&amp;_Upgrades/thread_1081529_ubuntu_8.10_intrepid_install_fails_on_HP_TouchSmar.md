---
title: "ubuntu 8.10 intrepid install fails on HP TouchSmart tx2z w/ display server shut down"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by ubuwan on 2009-02-26
How to get ubuntu to finish installing?


Previously installed Vista and Windows 7 partitions, with a 32 GB unallocated partition available for Ubuntu.
Burned a CD with ubuntu-8.10-desktop-i386.iso, and verified md5sums are okay.


Powered on PC to boot from the ubuntu CDROM.  Chose the option to use the unallocated hard drive space.  Installation began and seemed normal until it displayed:  "The display server has been shut down about 6 times in the last 90 seconds.  It is likely that something bad is going on.  Waiting for 2 minutes before trying again on display :0."

ALT-F2 will get me to a bash prompt, which seems to be running fine, but I don't know what to do from here.

Rebooting the PC does not present a boot option for Ubuntu.


These are the specifics of my PC:
- HP TouchSmart tx2z
- Genuine Windows Vista Home Premium with Service Pack 1 (32-bit)
- AMD Turion(TM) X2 Ultra 64 Dual-Core Mobile Processor ZM-82 (2.2GHz)
- 12.1" diagonal WXGA High-Definition HP LED BrightView Widescreen (1280x800)w/Integrated Touch-screen
- 3GB DDR2 System Memory (2 Dimm)
- ATI Radeon(TM) HD 3200 Graphics with 64MB Display Cache Memory
- Western Digital Scorpio Black 320GB 2.5" 16 MB Cache 7200 RPM
- Webcam + Fingerprint Reader with HP Imprint Finish (Reaction)
- Wireless-G Card with Bluetooth
- SuperMulti 8X DVD+/-R/RW with Double Layer Support


Others with the HP tx2z appear to have breezed past this point with no problem:  [http://ubuntuforums.org/showthread.php?t=1038898]("http://ubuntuforums.org/showthread.php?t=1038898")

---

### Post by Vincent_Lin on 2009-02-26
Hi,

I am the one that is frustrated in figuring out why my sound is not working after installing 64bit 8.10.

While messing around and installing multiple times, I had my luck bet on 32bit 8.10.  I burnt the disk after the download, and before actually installing it, I ran that verify the Disk option and made sure the disk is ok.

Well, the disk is ok, and the installation went smoothly before the same message turned up at close to very last steps.

Please note that, AMD64 8.10 installation always succeeds, and I am sure this 32bit x86 disk is ok.  But still...

I would categorize it as an installation process bug.  But it is only me, what do I know.  

I mean, it looks to me that 64 bit 8.10 would work with you through installation.  at least mine does.  Try that to see if it works for you.

Vincent

---

### Post by ubuwan on 2009-02-26
Vincent,

I deleted and unallocated the incomplete installation partitions to prepare for the re-install that you suggested.  Then I installed from the ubuntu-3.10-desktop-amd64.iso, but it resulted in the same failure (display server shut down message).

Thanks for your quick response and suggestion.  Unfortunately, I'm still looking for a solution.

ubuwan

---

### Post by ubuwan on 2009-02-27
I finally got ubuntu 8.10 to finish installing.  First I cleaned up as before (deleted and unallocated the unsuccessful ubuntu install partition) so I was back to the beginning state.

Starting from a dual-boot machine with Vista and Windows 7 partitions and about 32GB of unallocated space:  I booted from the ubuntu-8.10-desktop-amd64.iso CDROM, did not select install, but chose to run ubuntu from the CDROM.  Then from ubuntu's desktop, I selected the install icon.  This method of installing succeeded.

Thanks for your encouragement.

ubuwan

---

### Post by Vincent_Lin on 2009-02-27
Super!

Thanks for letting me know.

Now you can follow this thread to have everything setup

[http://ubuntuforums.org/showthread.php?t=1038898&highlight=tx2z](http://ubuntuforums.org/showthread.php?t=1038898&highlight=tx2z)

Ignore my problems and you should get a working (almost) AMD64 ubuntu on tx2z.

Please also let me know if you are willing to test 

apt-get install tuxpaint 

to see if your sound is still there after this installation.

Vincent

---

### Post by toids on 2009-03-01
I am having the exact same problem, but the 64bit version does not install, even after booting up with the CD.  I ran the CD check on both the 64 and 32 bit install disks prior to installation attempts.  Any ideas?  I always stops after "Checking battery state" and goes to the display server has been shutdown.  I received this touchscreen only a couple of days ago so maybe HP is trying to f people out of installing Ubuntu.

---

### Post by toids on 2009-03-01
looking at the '.xsession-errors' file:

...
seahorse nautilus module initialized
Initializing nautilus-share extension

** (nm-applet:8084): WARNING **: Unable to add monitor: Not supported
x-session-manager[7823]: WARNING: Application 'libcanberra-login-sound.desktop'
failed to register before timeout
Failure: Module initalization<sic> failed

** (nm-applet:8085): WARNING **: No connections defined
evolution-alarm-notify-Message: Setting timeout for 79805 1235952000 1235872195
evolution-alarm-notify-Message:  Mon Mar  2 00:00:00 2009

evolution-alarm-notify-Message:  Sun Mar  1 01:49:55 2009

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing

x-session-manager: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0

---

### Post by dranorter on 2009-03-01
Hi, my brother just installed 8.10 64 bit on his tx2z. He had this problem twice, the second time we were watching and, basically around 60% the screen started to fade like before Ubuntu starts a screensaver. One of us touched the mouse but this did not stop the fade, and after the screen turned black it tried to start X11 several times and then displayed that message, "The display server has been shut down 6 times in the last 90 seconds...".

The third install he started up Ubuntu with the 'try without installing' option, then installed it making sure to move the mouse quite frequently to prevent the screensaver from starting. It worked.

---

### Post by toids on 2009-03-02
Okay, I'll try this tonight and let you know.  Thanks for the reply.

---

### Post by tomlechner on 2009-03-03
I had a similar problem installing 8.10 on my tx2-1020us. Normal install broke down with the "tried to start X 6 times in 90 seconds". I used the (64bit) [text based alternate install]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate"), and it worked smoothly. The basics seemed to work just fine, including sound.. Sound has since broken though.

---

