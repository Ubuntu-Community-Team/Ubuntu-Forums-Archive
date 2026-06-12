---
title: "Howto: Install Jaunty on Gateway LT3103"
date: 2009-08-18
forum: Hardware
---

### Post by Hal58 on 2009-08-18
Only two of the current "netbooks" (and I include the 11.6" models) have the processing capability to do what I need; Audio editing with Audacity and viewing 720p HDTV mpeg2 streams.  The first is the Samsung NC20 with the Nano CPU, and the Gateway LT31 family with an Athlon64.  These are my notes from an LT3103 installation.

First, I replaced the hard drive with a G.Skill 128 GB Solid-State Disk, connected a USB slimline CD drive, and booted the system.  At the first prompt, select the RAM test and take a break (it takes a while).  After the test completes AT LEAST ONCE with no errors, you are ready to begin.  If any errors are displayed, change the RAM.

When booting after the RAM test, Press F6 at the start, dismiss the presented options and add
```

clock=hpet

```
There is nothing magical here, but I have found it more reliable on other Athlon installations, and it works here.  Let the disk continue to the live desktop then opening a terminal with
```

Applications->Accessories->Terminal

``` 
I prefer to do manual partitioning with fdisk due to the finer level of control than the automatic tools.  In the terminal, enter
```

sudo fdisk /dev/sda

```
Delete the existing partition, and enter your own configuration.  My table for the SSD is:

Disk /dev/sda: 128.2 GB, 128228261888 bytes
255 heads, 63 sectors/track, 15589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa231d92b

   Device Boot  Start         End      Blocks   Id  System
/dev/sda1   *       1          15      120487   83  Linux
/dev/sda2          16         273     2072385   82  Linux swap / Solaris
/dev/sda3         274        1299     8241345   83  Linux
/dev/sda4        1300       15589   114784425   83  Linux

The swap size should be at least as large as the memory installed so that all data can be preserved for "hibernate" or "deep sleep".  At the end, press "w" (write) and "q" (quit) to exit fdisk.

Note that partitioning boundaries (ending cylinder) are adjusted in each case so that there was no "+" after the "Blocks" entry.  I have found this to be a much more reliable configuration with Solid-State Disks, while it doesn't seem to be much of a problem with regular hard drives.

Now double-click on the Install icon on the desktop to begin putting Ubuntu on the disk.  When you come to the partitioning section, select "manual" at the bottom of the screen, and tailor each of the partitions you made previously.  In my case, it is:

 partition   use as   boot    flags     mount point
   sda1        ext2     *     noatime     /boot
   sda2        swap
   sda3        JFS            noatime     /
   sda4        JFS            noatime     /home/hal

The seemingly unusual mount point for sda4 is so that I can preserve my home directory across different installations, versions and tests without problems, and add other users in a like manner while keeping the /home directory within the main root partition.

Finish the installation normally.  When instructed, remove the disk from the CDROM drive (or unplug the USB drive) and reboot.

I prefer a few custom settings of the gnome desktop, and set them up early
in the process.  Skip these if you don't desire them.

System->Preferences->Appearance->Visual Effects --> None
	<lighten the load on the netbook processor>
System->Preferences->Keyboard Preferences->Layouts->Layout Options->
		Ctrl key position --> Make CapsLock an additional Ctrl
	<My left hand is permanently wired for the 'Wordstar Diamond>
System->Preferences->Startup Applications
	/usr/bin/gkrellm
	/usr/bin/gnome-terminal --hide-menubar --geometry=100x24+600+25
	<I absolutely live by Gkrellm data and a terminal>
System->Windows --> Check "Select windows when the mouse moves over them"
	<Save work with no excessive clicking>

One of the first (if not THE first) thing to do after an installation is to update all packages.  From a terminal execute:
```

sudo apt-get update
sudo apt-get dist-upgrade

```
 == reboot now at prompt.

I have become accustomed to several little utilities, and many of my
favorite tools are not installed by default.  So I load them next with many of them pulling in even more.  The basic tools are:

  joe        - Used in the 'jstar' mode gives a usable WordStar editor
  lm-sensors - Give access to hardware sensors for temp, fan and more
  gkrellm    - A useful system monitor which has saved many systems with
			indications of failing parts (heat, fan bearings)
  jfsutils   - Needed since I format Root and Home directories in JFS
  audacious  - My favorite music player since it does CD-Text, flac & ogg
  sshfs      - My favorite method of remotely mounting over a network
  sensors-applet - Another temperature monitor on the top menu bar
  normalize-audio - Great tool to measure/set average and peak levels when
			processing my music files.

Bring them and all dependencies in with the command line:
```

sudo apt-get install joe lm-sensors gkrellm jfsutils audacious sshfs sensors-applet normalize-audio

```

**[SIZE="4"]Hardware Sensors[/SIZE]**

Execute "sudo sensors-detect" in a terminal and answer "yes" to saving the modules in /etc/rc.local at end.  Then manually enter
```

sudo modprobe k8temp

```
to avoid reboot and make the sensors immediately usable.  You can test them in a terminal by simply typing "sensors".

Start the "gkrellm" system monitor in the background with
```

gkrellm&

```
and configure gkrellm as desired by right-clicking on it and navigating through the preferences list.  I add 'temp3' and 'THRM' temperature sensors to the continuous display.

If desired, add the temperature applet (Hardware Sensors) to the top menu bar, then configure which sensors you want displayed by right cliking on the icon and selecting 'Preferences' and then the 'Sensors' tab.

**[SIZE="4"]Wifi[/SIZE]**

By default, nothing seems to be loaded.  To correct this, we obtain some additional modules (backports) by using another command line
```

sudo apt-get install linux-backports-modules-jaunty

```
On the next reboot, the 'ath9k' module will be loaded and wifi will be up and running.  In my case, I use WPA with a big Hex key and entering it at the Network Manager prompt brings the network up.

**[SIZE="4"]Function Keys:[/SIZE]**

The special Function Keys (Holding "Fn" down while pressing another key) seem to partially work.  Here is my list of a preliminary test:

 Fn-Up/Down		Screen brightness Up/Down
 Fn-Right/Left		Volume Up/Down
<Fn-F1>		??
<Fn-F2>		??
<Fn-F3>			<Toggle Bluetooth - N/A>
 Fn-F4			Suspend (any key awakes w/password, USB active)
<Fn-F5>			<Toggle External Monitor??>
 Fn-F6			Blank Screen (any key restores backlight)
 Fn-F7			Disable/Enable Touch Pad (may need twice)
 Fn-F8			Toggle Mute
  <F9 & F10 Unused>
 Fn-F11			Toggle Scroll Lock
 Fn-F12			Toggle Num Lock

I used a Samsung 1680x1050 LCD as an external display, and when connected after the Gateway was on, I was unable to get it to display.  When booting with the external display connected, both it and the internal display were active at an intermediate resolution.  The internal display could be blanked with "Fn-F6" but the expected "Fn-F5" had no effect whatsoever.

**[SIZE="4"]REMAINING PROBLEMS:[/SIZE]**

 1. The CPU will not respond to frequencing scaling.  During bootup, you briefly see the message announcing failure of 'powernowd-k8', so the CPU will remain at 1.2 GHz.

 2. Some Function+Fn Keys do not respond in expected manner and the printed documentation with the unit is of no help.

---

### Post by jcsteele on 2009-08-18
Besides CPU scaling, the wireless connection WILL drop after a period of time...I have yet to see it remained connected overnight on my home network, and when I connect it to my schools network, it drops after about 30 minutes.

---

### Post by Footer on 2009-08-25
Hello,

I'm about 2 days away from purchasing one of these netbooks.  Best Buy has them for $379.99 right now + tax:

[http://www.bestbuy.com/site/olspage.jsp?skuId=9370272&type=product&id=1218093001788#tabbed-customerreviews](http://www.bestbuy.com/site/olspage.jsp?skuId=9370272&type=product&id=1218093001788#tabbed-customerreviews)

I've read here on the Ubuntu forums and in at least one user review about the wi-fi problem.  I'm curious if this is still an issue of if the backports module does indeed fix it.

Also, I'm contemplating 9.04 Kubuntu since I'm a KDE fan.  Anyone else try that on the Gateway LT3103?  How's performance?

Thanks!

---

### Post by Prikolchik on 2009-08-26
I haven't seen anyone mentioning that **it is possible to boot from the built-in card reader**. I've used external CD-rom to install Jaunty 9.04 on SDHC card, enabled F12 boot menu in BIOS, pressed F12 and selected to boot from card reader. Viola! (my BIOS: v1.1303 model: LT3110h).

---

### Post by diffy on 2009-08-26
For me, I recently install Jaunty on my gateway lt 3103 and i have some issues :
- the front mic doesn't work
- the cpu frequency is locked at 1.2 ghz
- the wifi disconnects sometime, but very randomly

I seen on some forums that the alsa driver which is with jaunty has a bug, i tried an update but then i had no sound at all :)

i have no more informations about that bugs.

David

---

### Post by gtwy on 2009-08-26
Battery life painfully short in Ubuntu
=======================================

I have successfully undervolted and underclocked using Rightmark RMClock (windows utility) with P states ranging from [**800 MHz @0.67 V**] to [**1200 MHz @0.7 V**] and have noted a very impressive extension in battery life :cool:

Finally somone was able to underclock the AMD processor under LINUX to 800 Mhz =D>(although not sure @0.67 V):
[http://forum.notebookreview.com/showthread.php?t=393200&page=22](http://forum.notebookreview.com/showthread.php?t=393200&page=22)

Has anyone successfully underclocked to 800MHz @0.67V under Ubuntu Jaunty?:?: Please confirm the steps if yes.

P.S: Is it possible to re-write and test the AMD processor to go to even lower (unsupported) P states? possibly with a multiplier like _3x @600 Mhz_ or even lower for super awesome battery life? [-o<

---

### Post by Prikolchik on 2009-08-30
I've written a [How-to: Getting power management to work on Gateway LT31]("http://ubuntuforums.org/showthread.php?p=7868889"). :)

---

### Post by omniuni on 2009-09-01
Hey all,

Powertop gives me the following suggestions, which increase battery life by about an hour.

> Suggestion: Enable USB autosuspend by pressing the U key or adding
usbcore.autosuspend=1 to the kernel command line in the grub config

Suggestion: increase the VM dirty writeback time from 5.00 to 15 seconds with:
  echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
This wakes the disk up less frequently for background VM activity

Suggestion: Enable SATA ALPM link power management via:
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy

I have also heard that using EXT4 can help.

Any idea where to put those commands so that they execute along with the computer?

As I get more information, I'll update it here.

---

### Post by gtwy on 2009-09-03
To save the battery life even more, is it possible/ worthwhile to run the entire OS off a 8 GB SDHC card (Class 10 with 30 MB/s write speed) I wonder how fast the card reader on this is though. :confused:

**Seagate Momentus 250 GB Power Consumption**
       • **2.0 W (Read)**
      • 1.6 W (Write)
      • **2.0 W (Seek)**
      • 0.6 W (Idle)
      • 0.2 W (Standby)
 
courtesy: [http://www.techarp.com/showarticle.aspx?artno=632](http://www.techarp.com/showarticle.aspx?artno=632)

---

### Post by larry. on 2009-09-15
Thanks so much Hal, great post.  Getting wifi working was becoming an annoying hurdle for first time linux user, but getting back modules fixed right away on restart. Vista is slow as dirt on this gateway, so this was a lifesaver.

---

### Post by AutoStatic on 2009-09-17
> **omniuni said:**
> Hey all,

Powertop gives me the following suggestions, which increase battery life by about an hour.



I have also heard that using EXT4 can help.

Any idea where to put those commands so that they execute along with the computer?

As I get more information, I'll update it here.Hello omniuni, you can leave the first suggestion as it is, that's apparently a [bug]("https://bugs.launchpad.net/ubuntu/+source/powertop/+bug/136549") in powertop. The second suggestion you can add to /etc/sysctl.conf with a line like:
```
vm.dirty_writeback_centisecs = 1500
```
The third suggestion you could add to /etc/rc.local althought that's probably not the best thing to do, there must be a better option.

Edit: and the better option is to install sysfsutils and to add the line
```
class/scsi_host/host0/link_power_management_policy = min_power
``` to /etc/sysfs.conf

---

### Post by AutoStatic on 2009-09-17
> **diffy said:**
> For me, I recently install Jaunty on my gateway lt 3103 and i have some issues :
- the front mic doesn't work
- the cpu frequency is locked at 1.2 ghz
- the wifi disconnects sometime, but very randomly

I seen on some forums that the alsa driver which is with jaunty has a bug, i tried an update but then i had no sound at all :)

i have no more informations about that bugs.

DavidHello David, front mic works with 2.6.30 and 2.6.31 kernels. Best is to try that first instead of updating your alsa drivers because updating alsa is not the best thing to do (as you found out yourself unfortunately). You can find updated kernels here: [https://launchpad.net/~dnjl/+archive/ppa](https://launchpad.net/~dnjl/+archive/ppa)
Or you could try the 2.6.30 kernel I compiled myself with the ACPI fix that is mentioned in [another topic]("http://ubuntuforums.org/showthread.php?t=1253365"). Front mic works with that kernel too. You can get it here: [http://www.autostatic.com/linux/ubuntu/](http://www.autostatic.com/linux/ubuntu/)

---

### Post by jacevedop on 2009-09-17
I installed Kubuntu on my LT31... the network manager doesnt work as expected... so... I went back criying to plain Ubuntu... gnome is not my favorite... but... I can survive... BTW... I installed Dolphin and set it as the default file browser...

---

### Post by jacevedop on 2009-09-17
One thing tough.... does anyone has 3D rendering working in Ubuntu... I would like to try some games and improve video playback... but everytime I try to set a new driver... I end up messing the X Window

---

### Post by AutoStatic on 2009-09-18
Hello jacevedop, 3D works for me with the open source radeon driver.

---

### Post by jacevedop on 2009-09-21
Hi AutoStatic... I have the ati radeon open source driver installed... but when I open Google Earth (eg) the app starts flashing... any ideas?

---

### Post by AutoStatic on 2009-09-22
Unfortunately no, I don't use Google Earth. But do other 3D apps work?

---

### Post by demisgc on 2009-10-05
The wireless has become a pain in the neck. It works for just a few minutes and drops the connection with the access point. I didn't find any information on how to fix that problem. Does anyone know how to keep the atheros chipset working fine?

**[SIZE="4"]Wifi[/SIZE]**

By default, nothing seems to be loaded.  To correct this, we obtain some additional modules (backports) by using another command line
```

sudo apt-get install linux-backports-modules-jaunty

```
On the next reboot, the 'ath9k' module will be loaded and wifi will be up and running.  In my case, I use WPA with a big Hex key and entering it at the Network Manager prompt brings the network up.

---

### Post by jcsteele on 2009-10-05
I believe some of the wifi issues have been resolved in Karmic - but haven't had a chance to really test that theory out yet.  Last time I used Alpha 5, the disconnect issues seemed to have gotten a lot better.

Power management is still (and I always feel will be) a complete miss for the near future.

---

### Post by AutoStatic on 2009-10-06
> **demisgc said:**
> The wireless has become a pain in the neck. It works for just a few minutes and drops the connection with the access point. I didn't find any information on how to fix that problem. Does anyone know how to keep the atheros chipset working fine?No there isn't really. There's a discussion going on if this is a NetworkManager or a driver bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/291760](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/291760)
Hopefully this gets patched in Karmic.
And jcsteele, try my kernel, works wel for me: [http://ubuntuforums.org/showpost.php?p=7938267&postcount=22](http://ubuntuforums.org/showpost.php?p=7938267&postcount=22)

---

### Post by skipstone on 2009-11-01
Something I noticed while debugging in China, was that iwconfig
indicated that my wifi was not correctly associated with the desired AP.
So I made a one-line iwconfig script to load the necessary info and then
the "auto" network manager would get working correctly. Every now and
then with the network manager loses its AP I just goose it with the script.
cheers

---

