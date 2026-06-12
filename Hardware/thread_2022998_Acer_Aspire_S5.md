---
title: "Acer Aspire S5"
date: 2012-07-11
forum: Hardware
---

### Post by bradb59 on 2012-07-11
Hey Guys...  
I know I am jumping onto the bleeding edge of sorts, but was wondering if anyone has had any luck with getting Ubuntu running on the new S5 ultrabooks?

The main problem seems to be recognition of the SSD drives and how they are set up.
Based on a lot of the reviews it would seem internally there are 2 SSD drives daisy chained in a Raid-0 configuration and as such on windows it appears as a single 256GB drive, and the benchmarks say I/O is super fast..

Anyhow, I don't care about the benchmarks and marketing hype...
When I run the installer, it does not find any suitable drives at all for me to install on.

When I have a shell and run:
fdisk -l

I see:
root@ubuntu:/mnt# fdisk -l
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x929cf226

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    16779263     8388608   84  OS/2 hidden C: drive
/dev/sda2        16779264    50333695    16777216   27  Hidden NTFS WinRE
/dev/sda3   *    50333696    50538495      102400    7  HPFS/NTFS/exFAT
/dev/sda4        50538496   500127743   224794624    f  W95 Ext'd (LBA)

Disk /dev/sdb: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table


Which pretty much confirms that there are 2 SSD drives in there and that the kernel recognizes them.

So, the question is, how do I get the installer to see them, and why does it say /dev/sdb does not have a valid partition table?  When I check it out in windows on the Drive manager, it shows all the partitions, but again shows both drives as a single drive.

Anyhow, not sure anyone is aware of if the raid of the drives is done in software or hardware, and how do I get around this to get Linux on there.

I'm not overlly concerned about dual booting this machine, so I can wipe it (I also have a factory backup if need be).  Any thoughts?  Should I just go in there and re-write the partition tables and then see if the installer can find the drives?

Any help would be appreciated, and if you need any more info, let me know.
(trying to install 12.04 Desktop btw)
-brad

---

### Post by sonnychee on 2012-08-09
Hey Brad59,

Have you had any further luck with your install?  I'm itching to buy an ACER S5 myself...

---

### Post by pirlouit on 2012-10-10
I got Ubuntu 12.04 installed this way:
1) USE 'Try ubuntu' 
2) run the program 'Disk Utility'
3) select the second 64 GB solid State Disk (ATA LITEONIT CMT 64L3M)
4) format this disk in ext4 and name it 
5) run 'Install Ubuntu 12.04' 
6) it will recognize the disk and partition it 

W7 is still intact in the first 64 GB disk (in case you may want to use it one day);)

enjoy installing your Ubuntu !

---

### Post by riskable on 2012-11-26
I installed Ubuntu 12.04.1 via the alternate install CD...

**NOTE:**  Press F2 at boot to get into the BIOS.

[LIST=1]
[*]Set SATA to AHCI in the BIOS (you don't want that fake "RAID" option).
[*]Enable the Boot Menu in the BIOS so you can press F12 at boot to select which device to boot from.
[*]When the installer asks if you want to detect software RAID select, "no".  If you select, "yes" it won't detect the drives properly.
[*]You can partition your drives however you like at this point but I deleted all existing partitions (who needs Windows?) and created a RAID 1 (striped set) with two paritions:  One 5GB for swap and the rest went to / (ext4).
[/LIST]

After booting up the first time into 12.04.1 you'll want to add 'acpi_backlight=vendor' to the GRUB_CMDLINE_LINUX_DEFAULT variable in /etc/default/grub so that Linux can control the backlight (LCD brightness).

You'll also want to install some things:

```
sudo apt-get install laptop-mode-tools cpufreqd build-essential powertop
```

Also add the Intel video PPA (has a newer version than what's in Quantal):

```
sudo apt-add-repository ppa:glasen/intel-driver
sudo apt-get update
sudo apt-get upgrade
```

...and enable SNA acceleration by creating the following /etc/X11/xorg.conf (seemed to make the system slightly snappier):

```
# Really, this is all you need in the entire file
Section "Device"                                                                                                                                                                                
        Identifier "Card0&#8243;                                                                                                                                                                      
        Driver "intel"                                                                                                                                                                          
        Option "AccelMethod" "sna"                                                                                                                                                              
EndSection
```

Then copy the following script to a file: /etc/laptop-mode/batt-start/acer_aspire_s5.sh

```
#!/bin/bash
#
# Author: Dan McDougall <YouKnowWho@YouKnowWhat.com>
#
# Description: Enables every power saving feature I know of when on battery
#

# Enable Intel HD Audio power saving
echo 10 > /sys/module/snd_hda_intel/parameters/power_save
echo Y > /sys/module/snd_hda_intel/parameters/power_save_controller
echo 1 > /dev/dsp # Have to make a sound to turn it on
# The following has been commented because it doesn't appear to be working.  Still have to run it by hand as your own user after boot it seems.
#pkill pulseaudio

# Enable WiFi power management
/sbin/iwconfig wlan0 power on

# Enable USB autosuspend for all USB devices
for i in /sys/bus/usb/devices/*; do echo 1 > $i/power/autosuspend; done
for i in /sys/bus/usb/devices/*; do echo auto > $i/power/level; done
```

Don't forget to set it to be executable:

```
sudo chmod 755 /etc/laptop-mode/batt-start/*.sh
```

**NOTE:** There's really no point to creating a script in /etc/laptop-mode/batt-stop/

Now for some tips...

If you upgrade to 12.10 (Quantal) you'll get video corruption after booting.  This can be quickly remedied by putting the laptop to sleep (I just close the lid) and waking it back up.  No idea what causes this but I've filed a bug report:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1082234](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1082234)
(make sure you add a comment saying this problem is also affecting you!)

If 'powertop' shows a realtek sound card at 100% utilization just mute your microphone and it'll go away.  If you have the same problem with the intel audio just execute 'pkill pulseaudio' as your user (it will automatically start itself back up) and that should take care of it.  For some reason I have to do this as my own user every time I go on battery...  Not sure what the deal is with that but I'll see if I can figure it out.

I'm currently investigating ways to fix the "video is corrupt on boot" problem.  I know that there's a patch out there that fixes it but I don't think it will apply cleanly to the kernel in 12.10 (we'll see).  I might also try the 3.7-rc* kernel line since Intel added tons of i915 and HD 3000/4000 improvements...  Hopefully one of those improvements will fix that S5 video problem.

**Another tip:**  If you want to be able to use the touchpad with additional gestures (like a Mac touchpad) you'll need to install Touchegg from source.  If you install the touchegg package in the Ubuntu repos it will crash so there's no point.  There's instructions on doing this here:

[https://code.google.com/p/touchegg/wiki/CompileSourceCode](https://code.google.com/p/touchegg/wiki/CompileSourceCode)

Just copy & paste the commands as instructed.  I also installed the Touchegg GUI to configure it from here:

[https://github.com/Raffarti/Touchegg-gce](https://github.com/Raffarti/Touchegg-gce)

I have KDE controlling the two and three-finger stuff so I could only get Touchegg to work with four-finger gestures.  I assigned the four-finger swipe left/right gestures as Alt-left and Alt-right, respectively (to go forwards and back in the browser).  Works great.

**How to disable the touchpad while typing:**  Start up syndaemon.  I have the following script in ~/.kde/Autostart (sorry Unity users, no idea how to configure that to start syndaemon on login):

```
#!/bin/bash
syndaemon -k -i 1 -t &
```
Just make sure to run 'pkill syndaemon' before you start up some first-person shooter or you won't be able to move and look with the mouse at the same time :)

---

### Post by riskable on 2012-11-26
I just confirmed that the video corruption problem has been fixed in the latest 3.7 kernel (from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/current/)).  However, the wifi was not working after booting that kernel...  So it isn't usable yet.

Another nice thing I noticed after booting the 3.7 kernel is that xdpyinfo reported correct DPI information for the S5's display.  In the default Ubuntu 12.10 kernel it reports 96x96 DPI which is incorrect.  It's actually more like 119x121 DPI.

I'm going to see if I can figure out the wifi problem while I've got networking again using the old kernel.

---

### Post by sonnychee on 2012-12-18
Hey Riskable,

Thanks for that detailed post.  It was very helpful.  I've had my s5 on 12.04 for the last 3 months and tolerating inexplicable system freezes 2-3 times a day.  Your tip:

> Set SATA to AHCI in the BIOS (you don't want that fake "RAID" option).

solved that problem nicely.

I also ran into the video corruption issue in 12.04 *immediately after* I applied the patches.  I was thinking of upgrading to 12.10, as you mentioned that fixed the issue.  Have you been successful resolving the wifi issue?

---

### Post by riskable on 2012-12-18
> **sonnychee said:**
> Have you been successful resolving the wifi issue?

The only wifi issue was with the newer 3.7 kernel.  I could resolve it by downloading the ath9k drivers and compiling them myself but I don't want to be running an unstable (RC) kernel.  I'll just wait until the next version of Ubuntu is out (or when the beta is ready).  I don't reboot often enough for the display corruption to be more than a minor annoyance.

The wifi is actually working fantastically well:  Been connected at 130MBit/sec for weeks now without issue.

For reference, I have *not* been experiencing any lock-ups, freezes, or any other such troublesome behaviors.  The laptop is running great.

---

### Post by sonnychee on 2012-12-19
Hey Riskable,

Every since I rebuilt my laptop, it's been rock solid. No lockups and freezes.  Have you had any success with the bluetooth mouse?

---

### Post by sonnychee on 2012-12-30
Hey Riskable,

Did you have any luck enabling the Bluetooth mouse?

---

### Post by riskable on 2013-01-23
Sorry about the late reply...  Apparently I'm not getting notification emails on threads I'm subscribed to (I'll be fixing that!).

THE VIDEO CORRUPTION PROBLEM HAS BEEN FIXED.  A recent update (some time in the past month) has resolved the issue.  I don't know when it was because I rebooted for the first time in a month last night (I love Linux :D ) and that's when I noticed.

Anyway, regarding the Bluetooth:  It probably won't work by default until Ubuntu 13.04 but it *can* work in 12.10 if you compile/install the driver yourself.  I don't care enough about Bluetooth to bother but if you want to get it working just follow the instructions in this thread:

[http://ubuntuforums.org/showthread.php?p=12158555](http://ubuntuforums.org/showthread.php?p=12158555)

---

### Post by eranid on 2013-02-09
Hi,

I've had the same problems with Acer Aspire S5:

1. Screen was without colors, with noise, on startup (closing the lid and reopening fixed that temporarily)
2. WiFi was shaky - worked sometimes but disconnected alot.
3. Bluetooth detects no device.

I just updated to Ubuntu 12.10 and 1 and 2 got solved (! thanks guys!),
But the bluetooth is still not working.

The link you gave, Riskable, is to a thread dealing with the WiFi as far as I can see.

Where can I find instructions on compiling and installing the driver for bluetooth? 

Thanks, this thread literally saved my computer, btw. I was going to get rid of it and buy a Dell...

---

### Post by soulnet1 on 2013-03-06
Hi,

Using riskable instructions I was able to get xubuntu up and running without any extra configuration than what he posted. Everything I tried so far worked, including sound, mic, webcam, USB, touchpad with 2 and 3 fingers taps as right and middle click and 2 finger swipe to scroll (I guess XFCE is taking care of it, I did nothing and it was working). The video corruption problem only came out on the first boot and was solved by suspending and coming back, but after doing the automatic updates I did reboot once or twice and it did not happen, so I guess it is corrected without any manual update. Bluetooth was not working and I did not try thunderbolt, but for Bluetooth, I figured I'll just wait until 13.04, and I have no need or use for the Thunderbolt port.

@riskable: First of all, thanks for your instructions, they were life saving and easy to follow. I would recommend that after

> 
[COLOR=#000000]After booting up the first time into 12.04.1 you'll want to add 'acpi_backlight=vendor' to the GRUB_CMDLINE_LINUX_DEFAULT variable in /etc/default/grub so that Linux can control the backlight (LCD brightness).[/COLOR]


You mention that update-grub and reboot are necessary. Also, I don't know weither some other step may need reboot or reinitialization of some daemon of something that I did not notice, but there are a lot of far-from-expert ubuntu-lovers like me out ther whose lives are made much easier with this kind of extra remarks. Luckily I realized I had to do it fast, but its happened to me before that it takes quite a while to figure this kind of details out.

Now, on to **the problem:**

My wifi is not working great. It works, it has good speed (up to 150 Kb/s) and I was able to download several hundreds of software packages. However, I'm getting quite a few disconnects, especially when the signal is not maximum (had been connected without a single disconnection with the same APs and almost the same physical connectino with my previous laptop, and the signal seems high enough for it not be the problem). Its not so much that is unusable, but is annoying being reseted every half an hour on average (it does reconnect fast in most cases, and never took more than a minute of retrying to be back up). When plugged in it seems to work better, although is a different AP (at home vs at the office), I'll try to plug in with the AP at the office to see if it changes.
had anyone else had trouble with this?
Is it possible that the power savings for the wifi in riskable's script are not working 100%? (I have the trouble with the AC connected also, so this is a wild guess)
also, when this computer disconnect, at least some times, my old HP laptop also disconnects (and the HP never disconnects if the aspire is suspended or off).

Any ideas? Maybe other wifi driver I might try? Just wait for 13.04 to resolve everything for me?

Thanks

---

### Post by soulnet1 on 2013-03-07
update: I've been trying to update to 12.10 to fix the wifi disconnection problem, but I'm getting:
[COLOR=#000000][FONT=verdana]E:Unable to correct problems, you have held broken packages.

Not really use why, apt-get update, upgrade, dist-upgrade, -f install, and the like I've tried show no error.

Any help will be appreciated, thanks.[/FONT][/COLOR]

---

### Post by soulnet1 on 2013-03-10
Update: After doing ppa-purge I was able to upgrade to 12.10 (although it took like 12 retries due to the wifi being disconnected while fetching) and now the wifi problem seems to be solved completely. Bluetooth is still not working though.

---

### Post by andberge on 2013-03-16
Hei, anyone else got problems with the "magic flip" just poping open whenever, almost at random. 

Thought first it was an usb problem of some sort, tho all usb devices are in suspend  and auto mode. 
Not really sure what causing this problem, was hoping someone had this encountered this problem and parhaps had an solution.
Or perhaps direct me where the problem might lie.

Running ubuntu 12.04. Laptop-mode has been installed, but other then that more or less out of the box as a standard installation.

---

### Post by soulnet1 on 2013-03-16
> **andberge said:**
> Hei, anyone else got problems with the "magic flip" just poping open whenever, almost at random. 


I have seen this problem being reported for the computer, even in standard windows installation. The hardware is supposed to do that automatically if the computer heats up, to provide additional ventilation. If it is happening when you are heavily using the processor, then it might just be the expected behavior. If it happens at random, I would say its likely that the hardware is misreading the temperature or your processor is being overused due to some misconfiguration. Are the fans always working fast when this happens?

EDIT: To answer the actual question, it has not happened to me, although the couple of times I was installing a lot of upgrades, which was the only processor-intensive task I've done so far, I opened it myself for ventilation (I thought it may make the fans a little more quiet).

---

### Post by andberge on 2013-03-18
Yea that might be what causing the problem, if i now can even call it a problem. Seems to happen around 50 - 60 degrees I believe. Tho so far only happened with the charger plugged in, tho this might be because the laptopmode set the freq. down once on battery mode, so less chance of overheating then. 

Must say tho, this magic flip thing on this computer is rather silly, almost made to be broken at some time, sounds awful too :P

---

### Post by riskable on 2013-04-26
I upgraded to 13.04 (Kubuntu) yesterday and everything is working wonderfully.  **The Bluetooth works now**!  I was able to perform an "hcitool scan" and see my phone and my wife's Mac (which is all the way on the other side of the house--not bad range!).  I wonder if the mouse works...  I may have given it away.  I need to rummage through some drawers.

**In regards to Thunderbolt:**  I just tested plugging in my Thunderbolt ethernet adapter and nothing happened.  Not even a line in [FONT=Lucida Console]dmesg[/FONT].  I'll test coldplug (booting with it plugged in) soon.

---

### Post by riskable on 2013-10-28
I just wanted to chime in to say that I've upgraded to Ubuntu 13.10 and everything is still working fine with the same exact caveats as with 13.04:

[LIST]
[*]The Thunderbolt port only works if you have something plugged in at boot.
[*]The Fn+<left/right arrow keys> keystrokes to control display brightness do not work.
[/LIST]
That last bullet is really quite surprising considering that the display brightness key combos worked fine in Ubuntu 12.04.

---

### Post by mitch-hasbox on 2013-12-06
> **riskable said:**
> I just wanted to chime in to say that I've upgraded to Ubuntu 13.10 and everything is still working fine with the same exact caveats as with 13.04:

[LIST]
[*]The Thunderbolt port only works if you have something plugged in at boot.
[*]The Fn+<left/right arrow keys> keystrokes to control display brightness do not work.
[/LIST]
That last bullet is really quite surprising considering that the display brightness key combos worked fine in Ubuntu 12.04.

Actually the last bullet (controlling the brightness with the Fn keys) works just fine. You need the following in /etc/default/grub

GRUB_CMDLINE_LINUX="quiet splash acpi_osi=Linux acpi_backlight=vendor"

and then just run "update-grub" and reboot.

Everything works just fine with this laptop.

Mitch

---

