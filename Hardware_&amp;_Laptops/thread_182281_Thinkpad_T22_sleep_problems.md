---
title: "Thinkpad T22 sleep problems"
date: 2006-05-25
forum: Hardware &amp; Laptops
---

### Post by shadrack on 2006-05-25
I followed the directions found here:

[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsIBM](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsIBM)

> Modem untested. Needs APM: add acpi=off nolapic to kernel options in /boot/grub/menu.lst, add apm to /etc/modules, and add shpchp and pciehp to /etc/hotplug/blacklist. Changing cs46xx to snd-cs46xx in /etc/hotplug/blacklist.d/alsa-base caused sound to work across sleep cycles.


My problem is: after returning from sleep, everything responds VERY slowly within gnome.  Programs that are already open respond promptly but the gnome interface and program launching interface takes 20x longer then normal.

I (thought) I had disabled ACPI like the above link suggests by following the above suggestions but I still see ACPI start up messages during boot up.  It is not listed in my /etc/modules (where I had to add apm) and I'm not sure where else to look for it.

Any ideas?

Also, adding "snd-cs46xx in /etc/hotplug/blacklist.d/alsa-base" disabled my sound completely.  "cs46xx" was not originally in the file, so I added snd-cs46xx to an uncommented line and after finding that my sound was disabled I removed it.

Also, Also Also....
I've also had some problems coming out of hibernation.  Sometimes it locks up after the loading himem message.  Sometimes it comes back just fine.  It isn't really repeatable for me atm...if i see a pattern maybe I'll post another message on this fine forum :)

Thanks!
-Shadrack

---

### Post by shadrack on 2006-05-25
Ok...I did a few things and I believe that I fixed the Gnome slow downs after coming out of sleep.  For some reason or another, returning from sleep locks up the sound device.  Clicking around in Gnome causes sounds to happen and the computer gets pre-occupied with trying to play that sound.  Ctrl-alt-backspace kills and then restarts the window manager but after logging in the opening theme sound locks you down again.

That would explain why the gnome window manager would come to a serious slow down sometimes, but then already opened applications would respond just fine.

The following steps has made the suspend and hibernate features usable.  All entries should be entered "without the quotes"
====
1. add 'noacpi acpi=off apm=on nolapic' to your kernel options in /boot/grub/menu.lst
2. add 'apm' to /etc/modules
3. add 'shpchp' and 'pciehp' to /etc/hotplug/blacklist (although I'm still not sure what effect this has).
4. Insert the following script:
#######
#!/bin/sh
case "$1" in
resume)
/sbin/modprobe snd-cs46xx
sleep 5
/etc/init.d/alsa start
esd &
;;
suspend)
/usr/bin/killall /usr/lib/gnome-applets/mixer_applet2
/usr/bin/killall esd
/etc/init.d/alsa stop
/bin/sleep 5
/sbin/rmmod snd-cs46xx
;;
esac
####
into /etc/apm/event.d/ as some filename and chmod +x it.  This was posted by MemoryDump and found here: [http://ubuntuforums.org/showthread.php?t=11016](http://ubuntuforums.org/showthread.php?t=11016)
5. reboot
======

Sound will work at first, but after going to sleep (suspend) and coming back up the sound stops working and the volume control gnome panel complains about it not working and I have to close it.  This isn't much of an issue, as I normally have the sound off anyway.  It probably has something to do with the above script.  Is there anyway to output the messages from that script to an output log w/o adding >> filename.out to every line?

I would imagine it has to do with the "sleep 5." I will try increasing that value.

Overall, the suspend and hibernate features seem to be working fine now.  The system is responsive after sleep in all the test I've run (which is about 5 boots worth of testing).

-shadrack

---

### Post by shadrack on 2006-05-25
Ohh..some other notes after following the steps outlined above:

If I am running off of AC power then pressing suspend never goes into complete suspend.  The screen goes blank, but my wireless network card still flashes and the cpu fan is still spinning.  If I unplug from AC power and then hit suspend everything goes as expected and turns off with only the green crescent moon "sleep" indicator on.


Oh, and I've been using the words sleep and suspend interchangeably.

-shad

---

