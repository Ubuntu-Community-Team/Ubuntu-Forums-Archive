---
title: "Samsung Series 5 ULTRA NP530U3B"
date: 2012-02-14
forum: Hardware
---

### Post by stlehmann on 2012-02-14
hello everyone,

i recently by this laptop one week ago.

everything is working quite nice and smooth but i have 1 issue.

when i close the lid the laptop is not suspending and yes the setting are correct in the power management menu 

acpi_listen was reporting no output on closing lid

/proc/acpi/button/lid/LID0/state are always reporting that the lid was open.

thanks for any hint 

so long

EDIT: when i plug or unplug AC the status in the change panel takes a while 5min or so

---

### Post by sacapeao on 2012-04-01
got one too!
 
Just istalled Lubuntu on the SSD, it runs so fast

Ran a bit hot with the fan spinning a lot

Battery draining in less than 4hrs consuming like 20W
according to $ upower -i /org/freedesktop/UPower/devices/battery_BAT1

Temperatures higher than 60C according to $ sensors

Read a forum reporting a fix adding i915 boot parameters on other Samsung
$ lsmod | grep i915 reports the module is present. 
In fact, applying that thing works:

3.0.0-17-generic #30-Ubuntu x86_64
$ sudo vi /etc/default/grub
add
GRUB_CMDLINE_LINUX="pcie_aspm=force i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1"
$ sudo update-grub
reboot

After

$ upower -i /org/freedesktop/UPower/devices/battery_BAT1
8.4W

$sensors
48C

more than 5hours battery

---

### Post by sacapeao on 2012-04-01
<Install Ubuntu on 500Gb HDD:>
The normal procedure detects the win os with option to install
alongside. It should be fine installing on the 500Gb disk with the grub on it.

<Install Ubuntu on 16Gb SSD:>
The SSD does not appear on the bios boot settings so the grub bootloader has to be installed on the 500Gb partition to boot the system from the 16Gb SSD, procedure:

Boot Ubuntu installer on a usb stick with and
choose "let me choose myself" to enter the partition screen.

Then just remove all the partitons of both disks and create new ones like ext4.
The main is the ssd disk: create a ext4 partition with mount point / and also a swap space one with more than total memory available (more than 4Gb)

Choosed to install the grub boot loader on the ssd partion
It didnt booted

Boot again from the usb stick

$ sudo -s
# fdisk -l
find the disk where installed Ubuntu (like /dev/sdb the other 500Gb should be /dev/sda)
# mount /dev/sdb1 /mnt
# mount --bind /proc /mnt/proc
# mount --bind /sys /mnt/sys
# mount --bind /dev/ /mnt/dev
# chroot /mnt
# grub-install /dev/sda
# update-grub /dev/sda
should give some errors cause not all the filesystem is binded
Nevermind, reboot

It should boot normally the Ubuntu os from the ssd
then just $ sudo update-grub

thats it :)

---

### Post by fivosz on 2012-04-01
Could you please report the battery life with normal use (wifi: on, brightness 60-100%, browing, mail, some youtube etc.)?

Thanks

---

### Post by Jay_Bee on 2012-04-08
I'm thinking of getting this notebook, can you tell me if suspend on lid close works in 12.04 beta?
I am also interested in battery life

---

### Post by aroque on 2012-04-16
I would love to hear more about this laptop, in particular if trackpad and function keys work out of the box or they require some tweaking as for the samsung series 9 (see [http://ubuntuforums.org/showthread.php?t=1737086](http://ubuntuforums.org/showthread.php?t=1737086)). Any other issue? Thanks

---

### Post by t3mujin on 2012-04-16
I just bought one and now I'm having series issues: the install went OK but now I updated to Precise and GRUB messed up and it doesn't boot anymore, I tried to boot from from GRUB2 Rescue console  but I keep getting "error: no such partition" (probably I'm doing things wrong, Rescue Console isn't very intuitive).

And the worst thing is now I can't boot from anything I put on USB, it goes straight to GRUB whatever I change on BIOS...

Any help is welcome...

---

### Post by aroque on 2012-04-17
The French community [wiki]("http://doc.ubuntu-fr.org/liste_portables_samsung") says everything was working out of the box with 11.10. @t3mujin: can you confirm this? 

Concerning the grub issue, on the samsung 9 thread ([http://ubuntuforums.org/showthread.php?t=1737086&page=16](http://ubuntuforums.org/showthread.php?t=1737086&page=16)) they suggest disabling FastBIOS to change boot order. I have no idea if this can fix your problem.

---

### Post by aroque on 2012-04-23
Sort of bumping this... could anybody successfully install/upgrade to 12.04 on this laptop?

---

### Post by donmiguel on 2012-05-02
Hi sacadeo

I have the model NP530U4B which is basically the 14" version.

I have applied the changes to grub, but the power-rate consumption stays the same:

About 18-19W just booted, doing nothing. Also i should mention that I use Ubuntu 12.04 (with kernel 3.2). do you have any idea why this could be

---

### Post by tomasyanez on 2012-05-10
Updated 12.04 with no problems. 
I've had some issues with bluetooth 

Improved battery performance changing values in
**GRUB_CMDLINE_LINUX_DEFAULT**  instead of GRUB_CMDLINE_LINUX

I only charge battery to 80% at that gives me around 4hrs. I'll do more tests. 

I'll try to make a clean install on the 16GB ExpresCache

---

### Post by aroque on 2012-05-10
> **tomasyanez said:**
> Updated 12.04 with no problems. 
I've had some issues with bluetooth 

Improved battery performance changing values in
**GRUB_CMDLINE_LINUX_DEFAULT**  instead of GRUB_CMDLINE_LINUX

I only charge battery to 80% at that gives me around 4hrs. I'll do more tests. 

I'll try to make a clean install on the 16GB ExpresCache

Good to hear, thank you for sharing your experience.

---

### Post by donmiguel on 2012-05-12
Hi, thanks fro sharing tomasyanez


Could be please report how much power your machine is using just after booting up?

You can see this with the tool powertop, which displays the watt use when on battery power.

Thanks a lot

cheers

---

### Post by hpdami on 2012-05-12
Hi everyone!

I've the same laptop and the same issues with it. My battery lasts around 1h and 20 min, compared with the almost 3h in Windows and the energy loss rate is now in 34Wh. 
I've  written the above commands in the GRUB_CMDLINE_LINUX_(DEFAULT), and it doesn't do anything, the problem still stands.

There is another problem that may be related, the device gets really hot, around 80ºC, even with the fan very 'loud'. In windows, with the fan almost silent, it reaches 40ºC, 50ºC. 

Just booted:
acpitz-virtual-0
Adapter: Virtual device
temp1:        +75.0°C  (crit = +99.0°C)
temp2:        +29.8°C  (crit = +99.0°C)

radeon-pci-0100
Adapter: PCI adapter
temp1:        +70.5°C  


Could it be a problem realted with the graphic card? 

I have this one:
 01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Thames [Radeon 7500M/7600M Series]

But I haven't been able to install them, the fglrx drivers doesn't get on well with Gnome Shell (it simply doesn't run).

Any help would be really appreciated! Thank you very much!

---

### Post by modafokaxx on 2012-05-14
If you run ```
sudo lspci | grep -i vga
```
you'll find that there are 2 video cards, not one.
This is one of these hybrid GPU systems, much like nVidia's Optimus (fiasco?).

The idea is neat: have two cards, a light one that takes care of the regular stuff, and a better one that will be used for heavier graphics rendering.

Unfortunately, the way it's been implemented is rather a mess from what I understand, and the end result for us is that both cards run, at the same time, with the Radeon video card drawing full power although it's not even being used. Hence, poor battery.

On the NP530U4B I have here, you can't disable the Radeon GPU from the BIOS either.

So, right now, our best hope is to see the [Bumblebee](http://www.bumblebee-project.org/) project manage AMD/ATI hybrid cards alongside nVidia's Optimus system.


Also, I'm interested, what performances do you get on your SSD partition? (/dev/sdb here)
(the mSATA Sandisk SSD i100 16GB)

I'm quite disappointed by the thing, it has read speeds of 6.5 MB/s and write speeds between 5 and 11 MB/s. The mechanical HDD has a read speed of 87.5 MB/s. :(
The cache and latency is good though, so I'm hoping that it will still make Ubuntu nice and snappy, but still&#8230;

---

### Post by mcarson01234 on 2012-05-17
Has anyone gotten suspend to RAM to work on this hardware with 12.04?  On mine it spins the disk for a few seconds, blanks the screen (but leaves the backlight on) and then just stops.  

Suspend to disk does the same, but when I power cycle it, the restore works.  Based on this, I suspect that suspend is working, except that it's not changing the hardware's actual power state.  Can anyone help point to a way to fix it, or diagnose the issue?

---

### Post by aroque on 2012-05-29
Ok, if I understand correctly the poor battery performance reported above only occurs with the AMD Radeon HD 7550 graphics card shipped on the 14'' version (NP530U4B) but not on the 13'' version which has an Intel graphics card. Otherwise the experience seems to be positive.

P.S.: it would be great if at least some of these information could be gathered in a more consistent way on [https://friendly.ubuntu.com/](https://friendly.ubuntu.com/)

---

### Post by s7dhansh on 2012-07-20
I have the 13 same laptop (u3b). 
1. I installed xubuntu on the 10gb partition of ssd (expresscache). I use windows as well, mostly because of the lack of three finger support and suspend, as of now. I haven't felt any performance decrease (windows) by the absence of expresscache. 
I also use windows bootloader with a bit of help from [http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/) because of the grub issue.
I keep home and var on a hdd partition and tmp on ram. See: [http://forum.xda-developers.com/showthread.php?t=1627197](http://forum.xda-developers.com/showthread.php?t=1627197)

2. The **overheating and battery issue** exists originally because of bad default kernel options.
Heating can be fixed by enabling active state power management and battery issue can be solved by the specific i915 options from [http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1)

In short, what @sacapeao did - 
GRUB_CMDLINE_LINUX_DEFAULT="pcie_aspm=force i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1"
in /etc/default/grub.

Also installing jupiter helped. [http://www.webupd8.org/2012/03/jupiter-applet-officially-switches-to.html](http://www.webupd8.org/2012/03/jupiter-applet-officially-switches-to.html)

3. The **suspend** problem is yet unsolved and would love to get any help. The i915 video drivers seem to be the issue. Hibernate is working perfectly fine though.

4. The touchpad doesn't have three finger option. touchegg doesn't work (segfault). It seems to be a known bug and I hope it gets rectified soon. 

5. While partitioning, I had to shift my recovery partition and in the process I have lost the use of my F4 recovery key. I intend to reclaim it and am in the process of finding a solution.

Any help with suspend, touchpad or recovery is welcome!

---

### Post by s7dhansh on 2012-07-21
Well, the suspend is working now. Thanks to this post - [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)

Create /etc/pm/sleep.d/20_custom-ehci_hcd with the following content
```
#!/bin/sh
#inspired by http://art.ubuntuforums.org/showpost.php?p=9744970&postcount=19
#...and http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug    
# tidied by tqzzaa :)

VERSION=1.1
DEV_LIST=/tmp/usb-dev-list
DRIVERS_DIR=/sys/bus/pci/drivers
DRIVERS="ehci xhci" # ehci_hcd, xhci_hcd
HEX="[[:xdigit:]]"
MAX_BIND_ATTEMPTS=2
BIND_WAIT=0.1

unbindDev() {
  echo -n > $DEV_LIST 2>/dev/null
  for driver in $DRIVERS; do
    DDIR=$DRIVERS_DIR/${driver}_hcd
    for dev in `ls $DDIR 2>/dev/null | egrep "^$HEX+:$HEX+:$HEX"`; do
      echo -n "$dev" > $DDIR/unbind
      echo "$driver $dev" >> $DEV_LIST
    done
  done
}

bindDev() {
  if [ -s $DEV_LIST ]; then
    while read driver dev; do
      DDIR=$DRIVERS_DIR/${driver}_hcd
      while [ $((MAX_BIND_ATTEMPTS)) -gt 0 ]; do
          echo -n "$dev" > $DDIR/bind
          if [ ! -L "$DDIR/$dev" ]; then
            sleep $BIND_WAIT
          else
            break
          fi
          MAX_BIND_ATTEMPTS=$((MAX_BIND_ATTEMPTS-1))
      done  
    done < $DEV_LIST
  fi
  rm $DEV_LIST 2>/dev/null
}

case "$1" in
  hibernate|suspend) unbindDev;;
  resume|thaw)       bindDev;;
esac
```

The ehci_hcd and xhci_hcd are the problem creators and need to be disabled before suspend.

Now eagerly waiting for three-finger support on the system!

---

### Post by mcarson01234 on 2012-07-23
I can confirm suspend is working for me too, with that script.  Oddly, I had tried removing those drives before suspend without success - something wrong with my technique in doing so, I suppose.  Thanks!

---

### Post by harakiri1976 on 2012-08-03
Hi guys!

I bought an NP530U3B (13"). Samsung can not recnognize my USB CD/DVD writer. I can not install Ubuntu.

May you please help?

---

### Post by harakiri1976 on 2012-08-05
Hello guys!

Before starting a new Thread concerning the installation of Ubuntu on the Samsung NP530U3B, can somebody help me how to do it?

The problem is BIOS Boot options are:

[LIST=1]
[*]USB FDD
[*]USB CD
[*]USB HDD
[*]SATA CD
[*]SATA HDD: Hitachi...
[*]NETWORK
[/LIST]


I have tried with a USB CD WRITER without success. And I have tried with a TOSHIBA FLASH USB Pen with UNetbootin install without success either. I'm afraid I can't boot Ubuntu or any other Boot Option other than HD on the notebook with Windows 7 on it. I can't understand how come the boot loader don't recognize the alternative boot options (USC CD-Writer and/or USB Flash Disk).

I don't want this OS. So, before I return this recent bought Notebook and chose another one (HP, ASUS, etc), can somebody tell me how to solve this "mystery"?

---

### Post by stlehmann on 2012-08-19
have you tried to turn off the "Fast Boot" option in the BIOS?

---

### Post by stlehmann on 2012-08-19
ok let me tell you  new thing that happend with my NP530u3b. i have the issue that suspend,reboot and shutdown are not working anymore. when i shutdowm it shows: 
will halt now 
[time] power down.

and nothing more happend i have to shut it complety down with the powerbutton pressing long time.

also if i enter the bios and save and exit the laptop was going off and not as aspected rebooting, strange!

ive treid everything (acpi=force,liveusb stick,and so on....)

iam running the latest BIOS 09XK updated with a windows7PE stick maybe i think this the point that bricks the maschine

---

### Post by harakiri1976 on 2012-08-19
@ stlehmann..

Thanks!

I've found out a couple of days ago. I forgot to REPLY to this message reporting "Problem Solved".

I went in contact with Portuguese Samsung and after sales department. Whether they give me a solution or I would return the Laptop. Problem solved! 

For others with the same problem. It's as simple as that but before you know how to solve it is a big problem.

On BIOS -> FAST BOOT SAFE -> DISABLE


Thanks again Stlehmann.

---

### Post by kinmye on 2012-08-31
Dear all:
I bought the 14 inch one (I think code is NP530U4B), kernel 3.2.0-29, ubuntu 12.04, x64

In general it works ok but I am very concerned with the battery issue. 
I have changed the kernel options according to the previous posts:

```

linux    /vmlinuz-3.2.0-29-generic root=UUID=1e849ec5-41a6-4d79-b100-fba9b45b6351 ro   pcie_aspm=force i915.i915_enable_rc6=1 i915.i915_en
able_fbc=1 i915.lvds_downclock=1

```However, I have not noticed any improvement. 
```

$ upower -i /org/freedesktop/UPower/devices/battery_BAT1  | grep rate
    energy-rate:         33.8106 W

```The computer is hot, the fan is very active.

Other problems:

[LIST]
[*]When I (dis)connect the power cord, there is no change in the battery icon. Now I am working with the battery but the icon is power, and when I click it says "35 min. to charge!".
[*]I cannot change the bright of the screen. It is at the max. The fn-F2 show the icon but do not decrease. In Brightness settings I can move the slider but no effect.
[/LIST]

Thank you for any help! I am very worried with the battery life at current state.

---

### Post by miesogeno on 2012-09-06
> **harakiri1976 said:**
> @ stlehmann..

Thanks!

I've found out a couple of days ago. I forgot to REPLY to this message reporting "Problem Solved".

I went in contact with Portuguese Samsung and after sales department. Whether they give me a solution or I would return the Laptop. Problem solved! 

For others with the same problem. It's as simple as that but before you know how to solve it is a big problem.

On BIOS -> FAST BOOT SAFE -> DISABLE


Thanks again Stlehmann.

Hi harakiri, 
I believe you simply got it wrong, but please confirm this to me:
you meant "fast BIOS mode" and not "fast boot safe" right?

because I'm having a lot of trouble getting this laptop to boot from USB, but I don't have a "fast boot safe" option in BIOS. Could we have different BIOS firmware? and disabling "fast BIOS mode" doesn't work either, thats why I need to confirm this.

cumprimentos de Lisboa!

---

### Post by harakiri1976 on 2012-09-14
Hi Miesogeno!

Yes! I'm sorry. Wrong typing. It is in fact:

[INDENT]Fast BIOS Mode[/INDENT]

Thanks for your question.

Disabling it and also changing your Boot Options Priority to first Boot by USB I am sure you will succeed. Are you sure you have done both? Be sure of that. And be sure you're using a USB Ubuntu ISO.

Cumprimentos do Porto:)

---

### Post by miesogeno on 2012-09-27
Yes, I had done that before, but I later found your "Fast boot mode" option (yes, you saw it somewhere :)) in the Windows program "Samsung Settings" (or something like that).
This program actually changes the BIOS! or at least some of the laptop's core functions.

For instance, I have set it to only allow 80% battery charge to extend battery life, and when I boot on Ubuntu (Elementary, actually), where I found no such option, it only charges to 80%. So, there's more interesting stuff for me to check in there, although its a shame this it will prevent me from totally removing Windows.

Obrigado Harakiri!

Apart from that, can anyone here suspend the laptop just by closing the lid? I read somewhere it was a kernel bug (ACPI related), but I could really use this feature.

---

### Post by Jay_Bee on 2012-10-19
Has anyone tried Ubuntu 12.10 on this laptop? Is suspend working? Are heating problems gone? How is battery life?

---

### Post by Angelo Maldito on 2012-10-22
Hi there folks,

I'm running Ubuntu 12.04 LTS (w/Gnome shell) on my brand new NP530U3B. Tried 12.10 (also UGR) first, but got a persistent kernel panic issue, so I downgraded it for a more stable release and have no major problems so far.

In order to install Ubuntu, I had to upgrade BIOS version using the .exe file from samsung website, then disabled "Fastboot" on BIOS and changed the boot order sequence putting the USB Flash in first place on the list.

Once installed, most things worked well out of the box, including the trackpad and most of the Fn keys, apart from Settings (Fn+F1), Fan (Fn+F11) and Wireless (Fn+F12). The last two were fixed by adding the "Linux on My Samsung" PPA, and then installing 'samsung-tools' and 'samsung-laptop' from there.

The only issue I found and couldn't fix yet is the power status (charging/discharging) on the top panel, as previously reported by *stlehmann.*:

> **stlehmann said:**
> EDIT: when i plug or unplug AC the status in the change panel takes a while 5min or so

In my case, however, instead of taking ~5min, the battery status on the top panel doesn't change at all when I plug/unplug the AC, unless I reboot the device. Does anyone has a fix for this?

Have researched a lot, but no luck so far:confused:

[EDIT]: The Fn Lock key is also dead. Have found that on samsung-tools settings, it's possible to add key combos to enable/disable webcam and bluetooth as well, features which doesn't seems to have been intended for this specific device.

---

### Post by miesogeno on 2012-10-22
Angelo Maldito, can you suspend the computer by closing the lid?

I confirm the battery status problem, haven't found a solution yet.

---

### Post by Angelo Maldito on 2012-10-22
> **miesogeno said:**
> Angelo Maldito, can you suspend the computer by closing the lid?

I confirm the battery status problem, haven't found a solution yet.

No, unfortunately not. I didn't realized before because I'm used to use the "suspend" button on gnome menu instead.

So, I can confirm that there are at least two issues left without a fix yet.

---

### Post by Pott on 2012-10-23
Hi, I just got one of these (with the 500GB disk/hybrid SSD) and I'm running trying out Ubuntu before install (wanted to use GParted to partition the HDD).

However the trackpad isn't recognized at all! The fn + enable/disable trackpad button does, but the pad/buttons do not work at all. I have an external mouse which does, but I don't want to install before figuring out the trackpad issue.

Any ideas..? Thanks! :)

EDIT: using the 64bits version.
I also followed the troubleshooter in [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad) but to no avail. The Kernel is not detecting a mouse at all!

---

### Post by Pott on 2012-10-26
Any ideas? :( I tried to test with the 32bits version as well but for some reason my USB key built with Unetbootin doesn't boot, but installs Wubi... I wasn't able to try it.

---

### Post by Jay_Bee on 2012-10-31
Try making your live usb with pendrive linux tool.
I can't say what's with your touchpad issue. Mine worked fine in the live enviroment.
Only issues I see on 12.10 are that the battery status does not change and that closing the lid does not suspend the laptop.

---

### Post by Jay_Bee on 2012-11-16
Hi everyone!
I received a BIOS update today via samsung update program in Windows, and now I'm trying out 12.10 live USB and battery indicator works as expected and laptop also suspends when I close the lid. I hope that this is the fix we were waiting for, I'll try live USB for few more days to verify the fix is permanent before installing Ubuntu on HDD. :)

---

### Post by Paper Bag on 2012-11-19
What version? On Samsung's support site newest is 1.0.0.2 from 13/12/2011.

Btw, does the 530U3**B** also suffer from the horrible ["UEFI + Ubuntu = brick"]("https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557") firmware bug like 530U3**C** does?

---

### Post by Jay_Bee on 2012-11-22
BIOS Version/Date - Phoenix Technologies Ltd. 11XK, 6.11.2012.

---

### Post by shuverisan on 2013-01-07
I found this thread trying to determine why my NP530U3B suddenly wouldn't boot from anything but the internal SATA drive. I had to flash the BIOS to 11XK which fixed it but I think trying to boot a live USB had something to do with it. UEFI boot was enabled.

In Quantal's live session, I had a kernel panic and it didn't brick the laptop, but the reflash was a pain without Windows on the drive.

But now that it's done with, everything works perfectly. In Precise I had the blank screen suspending from sleep issue and no matter what I did, nothing fixed it permanently. This only happened after I updated the kernel from 3.2.25 to 3.2.35.

Synclient commands will give all the three finger options for the touchpad. I use several and the only way I've found to make them permanent is by creating a startup script. It's given here in what steps to do.
[http://tombuntu.com/index.php/2011/11/06/persistent-touchpad-configuration-in-ubuntu-11-10/](http://tombuntu.com/index.php/2011/11/06/persistent-touchpad-configuration-in-ubuntu-11-10/)

I also spotted this thread about the i915 options.
[http://ubuntuforums.org/showthread.php?t=2102255&highlight=i915](http://ubuntuforums.org/showthread.php?t=2102255&highlight=i915)

I gave it a shot to not load them with Quantal. On battery, I was using between 7.5 and 8.5 watts and the only noise I could hear was from the hard drive. The fan was silent so it seems that they aren't needed anymore? At least for these models.

---

### Post by oldschool013 on 2013-02-20
Hi there!

Recently I adquired this ultrabook (NP530U3B) too, but I'm losing my mind about some things. I REALLY, REALLY REALLY, don't want to go back to Windows, I prefer sell this ultrabook.

The issues:

overheating?

Just firefox opened
```

acpitz-virtual-0
Adapter: Virtual device
temp1:        +71.0°C  (crit = +99.0°C)
temp2:        +29.8°C  (crit = +99.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +70.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +70.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +68.0°C  (high = +86.0°C, crit = +100.0°C)

```I tried the grub default, new kernel (3.8.0-6), others distribuitions ( 12.10, 13.04), jupiter, samsung tools (change mode of fan doesn't work). Some help?

The wireless is TOTALLY unstable and low, even if I stay close to router, it doesn't get the same as Windows (this notebook came with Windows, sorry guys).

Any needs, just say, I'll put the output.


Thanks

---

### Post by oldschool013 on 2013-02-21
Fan works. With the right speed? I don't know.

I tried Ubuntu 12.04, same things, except for wifi, this seems better. I'll take a better look at that. I'll install windows too (sorry) to take a look at temp and fan to compare.

Any ideias?

---

### Post by miesogeno on 2013-02-22
oldschool013,
Don't try to compare Ubuntu with Windows on this computer or you'll get depressed, this computer is completely built to work with Windows, battery time, temperature, startup times after suspend, everything is better on Windows, but its still Windows, which I can't stand to work on (despite all my efforts).

I was about to tell you that in my final attempt, all I did after installing Ubuntu (ElementaryOS, actually) was to install Bumblebee, that solved every problem. **BUT **I then realized I have a different computer (NP530U4C), with an hybrid nVidia card, which you don't have. That alone was responsible for reducing temperature, fan and battery consumption. So, it was a graphic card issue.

In your case, I don't really know whats responsible for those issues, but I can point you to some links I wondered on before I stuck to Bumblebee, some of them made a big difference, check them out **carefully** (you probably already know some of these links) and see what could apply to your case:

[http://www.voria.org/forum/](http://www.voria.org/forum/)
*(Linux on my Samsung Forum, samsung-tools, yada yada... you' may find some Q&A there)*

[http://bgrande.de/chronos7.html](http://bgrande.de/chronos7.html)
[http://openideals.org/2012/04/15/tuning-ubuntu-on-samsung-series-7-laptop/](http://openideals.org/2012/04/15/tuning-ubuntu-on-samsung-series-7-laptop/)
*(some guys quest trying to install linux on a series 7, which has some of the same problems as series 5)*

[http://jablonskis.org/2011/fedora-16-linux-on-samsung-series-9-np900x3a/](http://jablonskis.org/2011/fedora-16-linux-on-samsung-series-9-np900x3a/)
*(another guy trying to install fedora on a series 9... again, some of our problems seam to be the same)*

[http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1)
[I](explanation on some boot arguments you could add to grub.cfg, a recurrent approach on the above links)
[/I]
**Pay special attention to the graphic card related tweaks (this includes changes to grub.cfg)**. That seams to be the problem in most cases. But please, try these at your own risk. I read it all very carefully before trying to apply anything. I hope this helps you.

---

### Post by jnesset on 2013-02-22
Hi,

I have also got this computer and I've tried EVERY suggestion that is on the internet to get better battery life. It has become slightly better, but unfortunately it still sucks... I have enabled all of the kernel parameters suggested by Phoronix, installed CPU-freq, powertop, jupiter, you name it. Can't help getting depressed about only having 2-3 hours of battery life when it's a lot more with windows. Going back to windows is no alternative. Let's hope some things will change with the new distro...

and btw, when using powertop, is it normal that radio device: iwlwifi is using 100 %? When turning the lights down to minimum, the iwlwifi is the only thing using 100 % and maybe that is the reason low battery life? Can't find anything about this on the internet.

J

---

### Post by jnesset on 2013-02-24
I just have to tell you guys, I deleted ubuntu and did a fresh install of Linux Mint 14 instead. Now my battery life is doubled! I've got approximately 4 hours according to powertop.

J

---

### Post by oldschool013 on 2013-02-25
Hello guys,


@miesogeno, 

I think I like being depressed lol, almost a month trying to make it better on Linux. Those links you have passed to me, gorgeous.

I didn't have answered yet because I'll make a full post. My wifi is better than windows, got 5h on battery life, temperature is always dropping to ~60º. I'll keep searching if it's possible to get more battery life and lower temperature.

@jnesset,

What is the temperature of your ultrabook?


Thanks.

---

### Post by jnesset on 2013-02-25
> **oldschool013 said:**
> Hello guys,


@miesogeno, 

I think I like being depressed lol, almost a month trying to make it better on Linux. Those links you have passed to me, gorgeous.

I didn't have answered yet because I'll make a full post. My wifi is better than windows, got 5h on battery life, temperature is always dropping to ~60º. I'll keep searching if it's possible to get more battery life and lower temperature.

@jnesset,

What is the temperature of your ultrabook?


Thanks.


Acpi says that my temperature is 62 degrees. Yesterday, battery life was better, but I think I'm going to try adding a few parameters to the kernel on Mint also to see if it's helping. But does anyone know if wifi using 100 % is normal?

---

### Post by miesogeno on 2013-02-25
> **oldschool013 said:**
> My wifi is better than windows, got 5h on battery life, temperature is always dropping to ~60º. I'll keep searching if it's possible to get more battery life and lower temperature.

You've got 5h battery on linux? You have to teach me how to do that. My battery doesn't go beyond 4h. Thats really something.

One very annoying bug is the problem with the lid not activating suspend, and the battery status not changing immediately when connected/disconnected. I've seen several forums and blogs stating its a problem with the kernel, BIOS, EC, ACPI, etc, people claiming they got it solved, and then just realizing it was temporary. If anyone gets this working, please report here, that would be a great improvement too.

---

### Post by sostacked on 2013-03-03
I've got the NP530U4B (i5, 16GB SSD + 500 GB HD, DVD, HD3000 + ATI 7550, 14"), installed 12.10 (tried 13.04 as well). This thing has brought me nothing but grief.

All the standard items work. WiFi/LAN, display, sound, HDMI, touchpad, etc.

Managed to turn off (hopefully?) the ATI card by blacklisting the driver and switching to IGD at boot. The fan isn't spinning all the time anymore.

Tried installing to the 16 GB internal SSD (sdb). GRUB loader goes onto 500 GB sda, no issues. However, after the install the SSD reads and writes with like 6 MB/s, making it slower than a 2 year old USB flash drive. I create a new partition with Gparted, hdparm says I got 200 MB/s. As soon as I write a single file to it, the speed drops to 6 MB/s and stays so for good. Tried LVM, ext4, ext4, btrfs, no change. So I gave up on it, swapped out the HD with a SSD and I got 4 sec from cryptkey to desktop.

Power management is abysmal. ACPI events aren't registered, unplugging/plugging in power doesn't get registered, hence throttling doesn't occur, lid close is a no-go, suspended laptop drains the battery with breakneck speed. Also, I can't get the power consumption below 16 W. As a result I get 2 hrs battery time when fully charged. That's from a 6000 mAh 8-cell battery. How did you guys manage to achieve single digits and 4+ hrs? 

I've installed laptop tools, powertop, etc., aplied every GRUB switch I could find. Tried 3.8 kernel, all powersave tweaks I could find. Unity, Gnome Shell, Classic. At best I get 16 W, avg is around 18.

Obv windows works as intended, 4+ hrs, expresscache, graphics switching, etc. I'd very much like to keep this cutie, but it looks like our ways are gonna part.

---

### Post by dosyoyas on 2013-03-08
Agree. After reading this I tried linux mint 14 with Cinnamon on my Samsung NP530u4c-A01 (i5, 8gb ram, 1tb hd, hd4000+nvidia gt620m) and everything just works out of the box, except for the fn +f11 and f12 (fan and wifi). Powertop reports 10-11W with wifi on after lowering the screen bright and estimated battery life is the same as in windows. Using bumblebee and running glgears of course increases power consumption but the nvidia is usually off. Suspension on closing the lid works randomly though.

---

### Post by rogue1987 on 2013-03-12
dosyoyas, how is that Samsung running? I've been thinking of getting that very model.

---

### Post by arboziz on 2013-04-16
> **stlehmann said:**
> ok let me tell you  new thing that happend with my NP530u3b. i have the issue that suspend,reboot and shutdown are not working anymore. when i shutdowm it shows: 
will halt now 
[time] power down.

and nothing more happend i have to shut it complety down with the powerbutton pressing long time.

also if i enter the bios and save and exit the laptop was going off and not as aspected rebooting, strange!

ive treid everything (acpi=force,liveusb stick,and so on....)

iam running the latest BIOS 09XK updated with a windows7PE stick maybe i think this the point that bricks the maschine


Hi
Did you solve with the suspend,reboot and shutdown issue?
I'm in the same situation
this is my situation:

-when you give the command to shutdown or suspend computer stuck as you said before with power and wifi led on and heats a lot till the and of battery(or the forced shutdown with long press powerbutton/battery cutoff with pin)
-when you give the command to restart computer stuck as you said before with power and wifi led on for a lot of time and after that the computer shuts down
-same behavior as you when exiting bios
-issue is OS independent,with win7 same behavior
-never enabled uefi
-removing additional memory stick doesn't make changes
-removing drive doesn't make changes
-I'cant figure when these problems began,probably????? after a bios update
-I tried downgrading all version of bios and micom from 13xk to 09xk,but this doesn't seem to make useful changes
-](*,):-k:shock:[-o

---

### Post by jpcarlino on 2013-05-28
Hello,

some months passed since the last message on this thread. I would like to know if you tried the stable release of ubuntu 13.04 and what are the result. I've just bought a similar laptop and i can't boot the live version in graphics mode. Once i manage to sort out this issue i would like to know what comes next :P

Regards

---

### Post by 144 on 2013-09-01
I found that installing the latest AMD proprietary [driver]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx") reduced the power consumption and heating enormously. Installation instructions are on the same website.  The fan hardly ever runs now.  It also fixes the suspend problem whereby resuming from suspend results in a blank screen (it still doesn't sense the lid closing though; you have to suspend from the menu) - none of the other suspend 'cures' on the web worked for me.  I also installed Samsung-tools, to enable me to control the fan speed from Fn-F11.

---

### Post by rockerito99 on 2013-11-17
I found a SOLUTION  [IMG]http://forum.kde.org/images/smilies/smiley.gif[/IMG]  [IMG]http://forum.kde.org/images/smilies/smiley.gif[/IMG] !!!!!!! 
I wrote it up first in: [http://forum.notebookreview.com/samsung/683727-where-lid-closure-sensor-series-5-ultra-np530u3c.html#post9455595](http://forum.notebookreview.com/samsung/683727-where-lid-closure-sensor-series-5-ultra-np530u3c.html#post9455595)

I'm running Ubuntu 13.10 and everything works perfectly (webcam, mic, suspend, etc., etc.). I installed linux to the internal 24GB SSD, with /home mounted in a partition of the 500GB hard drive. Of course, I marked UEFI as DISABLED in the BIOS before installing, and kept it that way. I dual boot with the windows 7 that came with it. I used the free "NeoSmart EasyBCD" utility in windows to add linux to the windows boot menu which sits in the mbr (because the bios cannot boot directly to the SSD).

A few days into heavy use of both linux and windows, suspend with lid stopped working both in windows and linux. I debugged it like crazy, trying everything I could to fix it.

I'll put the solution here below:


**TL;DR:** "**Force a reflash to the BIOS**, _even if you already have the newest BIOS_, and you will be able to suspend on lid close and autodetect unplug/replug"


I bought my Samsung NP530U3C-AB1AR a week ago, and everything was working smoothly, until yesterday, when I noticed two things:


[LIST=1]
[*]Closing the LID was not detected by either Windows or Linux, and it lost the capability to suspend by closing the lid. 
[*]Unplugging  the power supply was not detected anymore by linux. And in windows it  wasn't auto detected, though it detected it several seconds after  unplugging, as if by polling. 
[/LIST]

It was obvious that this was a hardware/bios issue, since both OS's had the symptoms.

The lid sensor was working fine, so it wasn't a purely hardware issue  (you could see the screen turn off when lowering it, and then ON again  when opening the lid).

Clearly, **the BIOS wasn't sending events such as power Unplugged/Replugged or LID closed/opened to the OS.**

Of course, being familiar with the articles that described the bugginess  of this laptop's BIOS, I wasn't surprised. I decided that it was a BIOS  issue. I tried toggling all options I could find sensible to toggle in  the BIOS, to see if the original behaviour was restored. It didn't,  toggling options was useless. 

I decided to reflash the BIOS so that its internal options would be reset to defaults. THIS FIXED ALL ISSUES.

But, but.. it wasn't that easy. This is because I already had the latest  BIOS version, and the update tool refused to update the BIOS saying  that I already had the "latest version or newer".
This didn't stop me.
I found a forum thread by searching for "samsung downgrade bios".
And then I did the following:[INDENT]
1) Open the BIOS update tool from Samsung (go to samsung.com, support,  select your model, and look under Firmware). Click on 'Download' instead  of 'Update'. It offered to save a file named  "ITEM_20130423_1110_WIN_P14AAJ.exe". (My current BIOS version is  "P14AAJ", so it is the same version).

2) Run the file "ITEM_20130423_1110_WIN_P14AAJ.exe". The program decompresses several files to ***"C:\Users\<myuser>\AppData\Local\Temp\__Samsung_Update"*** The program refuses to update the BIOS because it is the latest version, and then deletes the files.
I copy the files before closing the program. They contain the ROM and  the SFlash64.exe utility, and some other files required for flashing.

3) I notice a file there, named "DebugAppLog.txt". That file is not  deleted between runs. In it, it contains the log of the time I updated  the BIOS the day I bought it, and most importantly, the full command  line for the SFlash64.exe utility. Which is:[INDENT]Bios command : SFlash64 /n /s /sa /ips /exit /file P14AAJ.rom[/INDENT]

I try **"SFlash64 -help"** and see the meaning of the flags. I particularly liked **"/n"** which says that it clears bios internal options to factory default, which is what I need.

4) I close all the opened programs. With the task manager, I close  Samsung's "Easy Settings" and all Samsung programs so that they don't  interact with the BIOS while it is flashing.

5) Start a console right clicking and "Run as administrator". Go to the directory where I saved the uncompressed files and run:[INDENT]SFlash64 /n /s /sa /ips /exit /file P14AAJ.rom[/INDENT]

6) Shutdown windows. Start hitting the "F2" key until I get in the BIOS.  Inside the BIOS screen, hit "F9" to load defaults. Fix options to my  liking because they were all default now.

7) Start Windows. Test lid close, It works!!!! 
Start Linux, Test lid close, It Works!!! Test unplug power cord: 
It is detected!!! Also, when unplugging the power cord in windows
it now detects it instantly, instead of several seconds later.[/INDENT]
[B]
PROBLEM SOLVED![/B]


_FINAL NOTES:_ What caused the issue? Will it happen again? I have a  few guesses: 1) The bios might have gotten confused when changing  states, and enabled some internal option to not inform the OS of power  events, perhaps while plugging/unplugging power while in S3 at the wrong  time, who knows, Or 2) Some Samsung software in Windows messed up some  internal option in the BIOS (Samsung software does change bios options,  for example, one can toggle "Battery Life Extension" from windows, and  the option will appear respectively toggled in the BIOS screen.). I  might uninstall all the Samsung software, I won't for the time being, to  see if it happens again. If it happens again, I'll just reflash. Or 3) I  read that these Samsung BIOSes have limited memory for variables (in [Jakob Heinemann: blog]("http://www.jakobheinemann.de/en/blog.html")),  so maybe entering the BIOS screen and saving bios options too many  times is what caused it, which is what one does the first days of setup,  changing boot order, etc (maybe the BIOS stores a backup of changed  options internally until it runs out of space, and things go wrong then,  luckily, reflashing the BIOS seems to restore everything to factory).
  I hope that it doesn't happen again, but I'll pay more attention to what I do, and try to remember what could have caused it. 

I spent the whole saturday debugging this issue, and I'm happy that I can share the solution!
--
Juan Manuel

---

### Post by thohva on 2013-12-15
I have the Intel one, 54 c, and a lot less battery time than windows. So the same problem here i guess.

Sorry, thought i was responding directly to the inlay.

---

### Post by thohva on 2013-12-15
The laptop does hibernate perfectly though, when using the terminal command.

Sorry, thought i was responding directly to the inlay.

---

### Post by thohva on 2013-12-15
Rockverito: I have the 540u3c and i lost my windows product key when formatting the drives and did not notice there was no product key on the laptop..

So how can i reinstall the bios without Windows?

---

### Post by rockerito99 on 2014-02-17
Hi Again!!

I found a much better workaround by reading this thread:

          [https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/971061?comments=all](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/971061?comments=all)

The workaround consists of:

[LIST=1]
[*]Turn off and unplug the laptop. 
[*]With a paper clip, push the button through the small hole in the back (it would be below the touchpad, in the back). Count to two. 
[*]Now plug the laptop, so that it can turn on. 
[/LIST]

After this, the LID close/open events are produced again. So do the AC plug/unplug events.

This is what they recommend to do to reset the "Embedded Controller" which is the motherboard component responsible of detecting LID close/open events, and plug/unplug events, and battery percentage drop/increase. Hitting that small reset button in the back has the same effect as removing the battery would have, in a laptop which has a removable battery.

This also explains why flashing the bios (any bios version), gets the computer out of the "problem state", because the Embedded Controller is reset while flashing any bios.

I also found out, after many, many tests, that the problem happens again when the laptop is suspended and no less than 16 Embedded Controller events would be produced. (% battery drop or increase is one event. Plugging or unplugging produces each two events (so you can unplug or replug 8 times at most, LID close or open is one event).

So, if I leave the laptop suspended with 100% battery, plugged to the wall, and without closing or openinng the lid, then the problem never happens.
If I never suspend the laptop, the problem never happens.

(by "problem state" I mean the state in which the laptop doesn't report LID events anymore, nor AC plug/unplug events, and this state is persistant between reboots and shutdowns).

My guess is that either some internal buffer of the Embedded Controller gets full when it cannot report events to the sleeping OS, or that Linux gets the system into a race condition trying to respond to too many events at a critical stage while the system is resuming from sleep.

If you think you got a fix, and want to try to see if it worked in preventing this issue, the quickest way to reproduce the "problem state" is to:

[LIST=1]
[*]Suspend the computer 
[*]Unplug PSU, plug, unplug, plug, unplug, plug, unplug, plug (8 actions each produces 2 GPE events). 
[*]Resume. Then, you can see that plugging or unplugging the PSU isn't detected, and LID close is ignored. 
[/LIST]


--
Juan Manuel

---

### Post by tempaccount325 on 2014-06-30
> **hpdami said:**
> Hi everyone!

I've the same laptop and the same issues with it. My battery lasts around 1h and 20 min, compared with the almost 3h in Windows and the energy loss rate is now in 34Wh. 
I've  written the above commands in the GRUB_CMDLINE_LINUX_(DEFAULT), and it doesn't do anything, the problem still stands.

There is another problem that may be related, the device gets really hot, around 80ºC, even with the fan very 'loud'. In windows, with the fan almost silent, it reaches 40ºC, 50ºC. 

Just booted:
acpitz-virtual-0
Adapter: Virtual device
temp1:        +75.0°C  (crit = +99.0°C)
temp2:        +29.8°C  (crit = +99.0°C)

radeon-pci-0100
Adapter: PCI adapter
temp1:        +70.5°C  


Could it be a problem realted with the graphic card? 

I have this one:
 01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Thames [Radeon 7500M/7600M Series]

But I haven't been able to install them, the fglrx drivers doesn't get on well with Gnome Shell (it simply doesn't run).

Any help would be really appreciated! Thank you very much!

**The following is for the Samsung NP530U4B ( -S02PT in my case ). It has little to do with NP530U3B.**

I know it has been a while, but this is a serious problem which I had an  immense difficulty dealing with and I can imagine how others have felt.
This solution is for Linux Mint 16 and Ubuntu 13.10 (the ones I've tested this fix on) is modifying **GRUB_CMDLINE_LINUX_DEFAULT=** and installing **TLP**.

The NP530U4B features Hybrid Graphics with a discrete and integrated graphics cards. The cards are an AMD Radeon HD7550M and an Intel Graphics processor HD 3000.
The very nature of Hybrid Graphics implies that in must be governed by the OS.

**NOTES**
I've only tested this on the above Linux branches and it was always on kernel 3.11 and above, which I believe it's the one that integrates the following solution.
The final result is extremely satisfying as the battery rate rivals that of Windows 7.
**Power Statistics (on Ubuntu and Linux Mint) **is your best friend when testing these changes. It tells your very fast the rate of discharge of your battery under the "History Tab".The final consumption rate is about 13 Watts when idle as opposed to the initial, which was anywhere between 20-35 watts.The temperatures go down severely which allows the louder fan to shut off. The trip point seems to be 65ºC.The **BIOS** does not seem to provide much help to this cause, since Samsung refuses to add an option to turn off the radeon card .There are a few interesting settings in the BIOS, but their effect is miniscule.
I did not test video games under these conditions.[B]

GRUB_CMDLINE_LINUX_DEFAULT=[/B] 
You need root permission for both these actions.
- You can edit **/etc/defaul/grub** and change the respective line to **GRUB_CMDLINE_LINUX_DEFAULT="radeon.dpm=1 quiet splash"**.
- Afterwards, you need to run "update-grub" (without the quotes) in order to apply the changes.
The **radeon.dpm=1 **allows power management of the radeon card, which is the one reason that gives the Samsung NP530U4B 1/3 or less of it's expected battery life under windows and the likelihood of overheating. The problem seemed to be that the radeon card was permanently on and at maximum potential doing who knows what. With **radeon.dpm=1 **the processing seems to be allocated as needed between the discrete and integrated graphics card.

[B]TLP
[/B]This programs applies some power saving measures to your system. I have gone through the configuration files of TLP, but did not change anything as it comes configured for the standard user.
I do believe you have to issue a command to start using TLP once installed or you can just reboot your computer.
You can follow the instructions on their site on how to install if it not yet included with more up to date versions of the above OSs.

**Other Programs like TLP**
I did try a few similar programs and Laptop Mode Tools came about in second when watching the power consumption rate under light conditions. However, I did not try messing with anything that is Hardware related such as the CPU frequency. Most of these programs cannot run concurrently with TLP by nature.

**AMD Drivers** and FGLRX( the latter through apt-get and the "Additional Drivers" window.
Absolute waste of time as of 17/02/14. If you do need to manually switch graphics cards it does provide a solution for that with Catalyst Control Center. However, the chances of having something break instantly after reboot or a few reboots after is just too great. That was both with the Beta and Stable drivers. I followed days-worth of guides (including the one provided by AMD) and it only resulted in pain. The one time I thought it was already stable, it ended up breaking after some 10 shutdowns/boot-ups when I had already migrated everything into it. The temperature and battery consumption immediately go down after installing the drivers, but I did not manage to compare to the above procedure.

**--- OTHER THINGS ---**
SSD - I managed to install Linux on the SSD, but not with the instructions on this thread. Since I don't think it very appropriate, it's best if you send me and email (tempaccount325@outlook.com).
Battery Indicator - Sometime it gets stuck at 100% after leaving it charging for while after it has reached that value. This is fixed with a reboot at the very least.
---------
Edit1: Missed a few letters on the email account.
Edit2: Remarks on Gaming.
Edit3: Remarks about Hybrid Graphics.

---

