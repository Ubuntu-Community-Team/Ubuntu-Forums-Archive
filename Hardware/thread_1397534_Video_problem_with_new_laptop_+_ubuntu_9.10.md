---
title: "Video problem with new laptop + ubuntu 9.10"
date: 2010-02-03
forum: Hardware
---

### Post by 18wheeler on 2010-02-03
Seems that I always have graphic (resolution) issues with ubuntu. It is either working fine from beginning or if there was a problem it would be un-solvable.

I just installed 9.10 on a newly purchased gateway NV5927u laptop, which has i5 430m CPU and integrated "intel HD graphics" card. I used safe graphics mode during installation (otherwise there was no graphics on the screen).


After installed, I noticed a few things were not right:

1. the screen cannot be identified. it is shown as 'unknown' screen in the systerm -> preference -> display. and only 1024 x 768 resolution is available. the screen is 1366x768

2. during the process trying to solve it, I found that I cannot access the virtual terminal with ctrl-alt-F1 (or F2-F6). it shows a gray frozen cursor at the top left corner, and wont response. Ctrl-alt-F7 does bring X back.

3. same happens if I try to boot into the safe/recovery mode

4. wont detect external monitor. if external monitor is connected during booting, it wont boot passing (behave like 2 and 3 above)

Please help! :(

---

### Post by 18wheeler on 2010-02-03
a bit more info about the laptop:

```
~$ lshw -c display
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: Arrandale Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 12
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:31 memory:f0000000-f03fffff memory:d0000000-dfffffff(prefetchable) ioport:1800(size=8)

```

---

### Post by 18wheeler on 2010-02-03
Also run the compiz-check script (suggested in the other thread):

```
~/bin$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Arrandale Integrated Graphics Controller (rev 12)
 Driver in use:         vesa
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: vesa driver in use 

Would you like to know more? (Y/n) 

 The vesa driver is not capable of running Compiz, you need to install
 the proper driver for your graphics card. 
```

---

### Post by chewearn on 2010-02-03
I got here from the other thread you posted to: [http://ubuntuforums.org/showthread.php?t=1391857&page=2](http://ubuntuforums.org/showthread.php?t=1391857&page=2)

I found number of webpages, forum threads, etc w.r.t. problems with Intel graphics in Jaunty and Karmic.  However, none explain a definite fix.  I guess the problems and solutions are varied depending on multiple circumstances.

The only advice I could offer right now is, if you have not updated your Karmic install, you should do so now.  But even then, I could not say if it would solve your problem (i.e. bug fixed) or make it worst.

```
sudo apt-get update && sudo apt-get upgrade
```Personally, I have no experience with the new major changes to Xorg and Intel driver since Jaunty (I am still using Intrepid).  In previous versions of Ubuntu, you back-up xorg.conf, then ran:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```But this command is supposedly broken in Karmic.
[https://bugs.launchpad.net/bugs/474455](https://bugs.launchpad.net/bugs/474455)

---

### Post by 18wheeler on 2010-02-03
Thanks for the reply!

I did system update right after installation. I did try the update and upgrade apt-get as you suggested. but it seems to be up to date:

```
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

dpkg-reconfigure did not do anything either.

here is my xorg.conf:

```
$ cat /etc/X11/xorg.conf
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```

---

### Post by 18wheeler on 2010-02-03
found a previous bug about falling back to vesa driver with intel video card:
 
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/379504](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/379504)
 
it talks about that the bug was caused by missing intel.ids file in /usr/share/xserver-xorg/pci. The bug was marked as fix released. 
 
I looked at the folder. there is no intel.ids file (apm, ark, openchrome, s3virge, sis, etc. are there). 
 
how can I get it restored?

---

### Post by chewearn on 2010-02-03
> **18wheeler said:**
> Thanks for the reply!

I did system update right after installation. I did try the update and upgrade apt-get as you suggested. but it seems to be up to date:

```
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```dpkg-reconfigure did not do anything either.

here is my xorg.conf:

```
$ cat /etc/X11/xorg.conf
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "[COLOR=Red]**vesa**[/COLOR]"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```

What happened if you simply change vesa to intel (in **[COLOR=Red]bold-red[/COLOR]** above)?  You can change it back through livecd boot or recovery boot if it failed.

---

### Post by 18wheeler on 2010-02-03
> **chewearn said:**
> What happened if you simply change vesa to intel (in **[COLOR=red]bold-red[/COLOR]** above)? You can change it back through livecd boot or recovery boot if it failed.
 
Just tried it.
 
Good news is that the resolution seems to be right (widescreen instead of 3:4) and external monitor is mirrored
 
Bad news is that the X windows freezes seconds after boot up. sometimes right away, sometime after I move the mouse around for a second or two.

---

### Post by 18wheeler on 2010-02-03
well I thought I found a solution. but it was just a work around:

with 'intel' replace 'vesa' in the device section, I added modeline to the monitor section:
    ```

    Modeline    "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
    Modeline    "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
    Option        "PreferredMode" "1336x768_60.00"
```

and Display subsection to the Screen:
```
    SubSection "Display"
        Depth    24
        Modes    "1280x1024" "1336x768" "1024x768"
    EndSubSection
```

I have to boot in the recovery mode, continue to log in (with first option in the recovery mode) then type 'startx' to start x window. It seems to works fine, as long as I attach the external monitor AFTER I boot up.

If I have external monitor attached during bootup (even in recovery mode), ubuntu would freeze; If I don't use recovery mode, X window freezes soon after boot up.

---

### Post by 18wheeler on 2010-02-03
did a little more experiments and find out the freeze might happened in gdm:
 
when boot in recovery mode when log in and using startx, I got display work perfectly, but my ext hard drive will not automatically connect;
 
if I boot in recovery mode but use 'sudo gdm start' to start X server instead, I got exact same freeze after boot up.
 
Now how to replace gdm with startx or get gdm work ...

---

### Post by 18wheeler on 2010-02-04
I ended up using XFCE desktop. Everything seems to be working fine except I cannot figure out how to enable dual monitor.

---

### Post by merzoukr on 2010-03-07
> **chewearn said:**
> What happened if you simply change vesa to intel (in **[COLOR=Red]bold-red[/COLOR]** above)?  You can change it back through livecd boot or recovery boot if it failed.

Thank you!!!  I have a brand new Dell studio w/ 17" HD screen.  I've been searching for a solution for a week.  Tried everything I've seen, even going back to 8.04.  Changing "vesa" to "intel" did the job (and sooooooo much more simple than anything else I've tried).  Thank you, again!!:D

---

### Post by chewearn on 2010-03-07
> **merzoukr said:**
> Thank you!!!  I have a brand new Dell studio w/ 17" HD screen.  I've been searching for a solution for a week.  Tried everything I've seen, even going back to 8.04.  Changing "vesa" to "intel" did the job (and sooooooo much more simple than anything else I've tried).  Thank you, again!!:D

No problem, glad to know it works for at least one person. :D

---

