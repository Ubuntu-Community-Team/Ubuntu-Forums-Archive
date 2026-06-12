---
title: "Trackpoint Driver on Thinkpad R31"
date: 2006-05-10
forum: Hardware &amp; Laptops
---

### Post by smaug9 on 2006-05-10
I'm running Dapper beta 2 on a Thinkpad R31, but every once in a while the pointer jumps around and lands in a corner. Is there a fix for this. I did a preliminary google search, but didn't come up with anything that I could use.

Thanks,

---

### Post by slimdog360 on 2006-05-10
I have a thinkpad R50e, and mine doesnt do that, although Im not running dapper, but anyway does your middle mouse button on the laptop work. The one which you hold in to scroll, it works in windows but not here.

---

### Post by smaug9 on 2006-05-10
If you want the trackpoint 3rd button to scroll, try going through:
[http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint)

---

### Post by smaug9 on 2006-05-10
I did find this: [http://www.thinkwiki.org/wiki/TrackPoint](http://www.thinkwiki.org/wiki/TrackPoint), which stated that

> Note that the "IMPS/2" driver of the X server is incompatible with most TrackPoints. You'll have to use "PS/2" in the protocol option of your input section if your mouse pointer always jumps to the lower left corner of the screen. This seems to be solved with the T4x generation of ThinkPads.

But that didn't seem to work for me. When the machine started X, I would login, but gnome would not create the panels. I could ctrl+alt+F2 to get to a console, but I couldn't get X to work with the trackpoint.

Anyone have any hints? I'm thinking about going downgrading to breezy, see if that works okay.

---

### Post by smaug9 on 2006-05-10
Got this in my syslog just after the pointer made a couple circles around the screen and ended up in the lower left hand corner.

> May 10 11:07:05 localhost kernel: [4295676.257000] psmouse.c: TrackPoint at isa0060/serio4/input0 lost synchronization, throwing 1 bytes away.

Here is the mouse section of the xorg.conf:

> Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "PS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

I'm wondering if I need to apply the patch from here:
[http://thinkwiki.org/wiki/Trackpoint](http://thinkwiki.org/wiki/Trackpoint)

---

### Post by smaug9 on 2006-05-10
Well I found this:

[http://www.thinkwiki.org/wiki/Problem_with_checking_battery_status](http://www.thinkwiki.org/wiki/Problem_with_checking_battery_status)

seems that it's a problem with the bios & polling the battery. Oi.

I'll keep plugging at it and see if I can get it to stop.

---

### Post by cmassey2005 on 2006-05-10
[QUOTE=smaug9]
[http://www.thinkwiki.org/wiki/Problem_with_checking_battery_status](http://www.thinkwiki.org/wiki/Problem_with_checking_battery_status)
[/QUOTE]

I have an IBM ThinkPad R31 laptop as well and was having this same exact problem.  Apparently it's well known.  The solution I found was similar to the one mentioned in your link, but I did not have to stop querying the battery or remove any battery applets:

[http://www.ubuntuforums.org/showthread.php?t=555&highlight=Thinkpad+R31](http://www.ubuntuforums.org/showthread.php?t=555&highlight=Thinkpad+R31)

Simply followed mgor's simple instructions for passing the necessary parameter to the kernel:

1.) edit /boot/grub/menu.lst and find the line that begins with "# nonaltoptions" and add "i8042.nomux=1" to the end of that line.  Mine looks like this:

"# nonaltoptions=quiet splash i8042.nomux=1"

2.) run update-grub and then reboot.

That took care of it for me.  Hope this fixes your problem.

EDIT: Just wanted to say that I am running Breezy Badger on my IBM Thinkpad R31, in case that makes any difference.

---

### Post by nanofox on 2007-10-21
> **cmassey2005 said:**
> I have an IBM ThinkPad R31 laptop as well and was having this same exact problem.  Apparently it's well known.  The solution I found was similar to the one mentioned in your link, but I did not have to stop querying the battery or remove any battery applets:

[http://www.ubuntuforums.org/showthread.php?t=555&highlight=Thinkpad+R31](http://www.ubuntuforums.org/showthread.php?t=555&highlight=Thinkpad+R31)

Simply followed mgor's simple instructions for passing the necessary parameter to the kernel:

1.) edit /boot/grub/menu.lst and find the line that begins with "# nonaltoptions" and add "i8042.nomux=1" to the end of that line.  Mine looks like this:

"# nonaltoptions=quiet splash i8042.nomux=1"

2.) run update-grub and then reboot.

That took care of it for me.  Hope this fixes your problem.

EDIT: Just wanted to say that I am running Breezy Badger on my IBM Thinkpad R31, in case that makes any difference.


I'm sure that this problem has given many users a major headache in the search for the correct answer. It seems that the answers above couldn't provide me with the relief that the other users were receiving. My search is over and this worked for me! I hope this will help everyone out!


Just use like the earlier posts

sudo gedit /boot/grub/menu.lst

then find the kernel line:

title Ubuntu, kernel 2.6.12-9-386
root (hd0,1)
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro quiet splash i8042.nomux=1
initrd /boot/initrd.img-2.6.12-9-386
savedefault
boot

this line is the default ubuntu booting kernel. Now look at the line start with "kernel". Noticed "i8042.nomux=1"? that's the answer to make the trackpoint come down. just add those to the kernel line, save the file then reboot. That's it!

here's the web page where I found the info [http://www.thinkwiki.org/wiki/Problem_with_checkin](http://www.thinkwiki.org/wiki/Problem_with_checkin) g_battery_status'>Problem with checking battery status - ThinkWiki

i also didn't have to update the grub

---

