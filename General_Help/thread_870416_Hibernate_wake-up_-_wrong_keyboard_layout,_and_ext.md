---
title: "Hibernate wake-up - wrong keyboard layout, and external HD name change"
date: 2008-07-25
forum: General Help
---

### Post by Rod Hull on 2008-07-25
Using Ubuntu 8.04.1 32-bit with kernel 2.6.24-19-generic with Gnome and UK keyboard layout (set in System - Preferences).

Whenever I wake from hibernate, the keyboard layout automatically changes to US (even though I only have UK layout enabled via System-Preferences).

Also, my external USB WD hard disk re-mounts itself at a different mount point (incrementing a number onto /media/disk - so /media/disk-1, then /media/disk-2 etc.) after each hibernation. The device name alters too, starting from /dev/sdd, to /dev/sde, /dev/sdf etc. each time it wakes from hibernation.

I've tried adding "usb_storage" to MODULES_WHITELIST= of /etc/defaults/acpi-support to force it to not re-plug the device upon wakeup (which as I understand it is correct?), but it doesn't seem to make any difference.

Totally stumped with the keyboard prob, though! Not sure what to try for that!

Can anyone offer any help on the USB or keyboard layout problem?

---

### Post by Rod Hull on 2008-07-26
Bump :)

---

### Post by jkid on 2008-07-26
try to set the settings again....

---

### Post by Rod Hull on 2008-07-26
Well, I did that, but it's no good when it continues to set itself to a USA layout each time it's hibernated...

I'd rather not have to set it back to what it was originally set to each and every time...this kind of thing just shouldn't happen IMO! If there's a valid reason for this behaviour I'd love to know why, and how to alter it (if possible)!

---

### Post by killerwhale65 on 2008-07-27
Hello,

I have the same problem, but on shutdown. The keyboard layout always changes on startup. When i go to the preferences, i see that the correct one is selected (although this does not stroke with the keyboard output), and then when i add a new layout (the same one that is already set), it works, but only untill the next reboot.

Thanks for any help.

Matt

---

### Post by Rod Hull on 2008-07-27
Well, that sounds like exactly the same behaviour as me, although I admit I haven't tested it with shutdown...there's definitely something not right!

The more annoying thing is the USB problem. At least I can re-enable the correct keyboard layout. It really shouldn't be renaming the device each time...thank goodness it doesn't do it with my internal HDs!

Can anyone offer any help on the USB issue? I have spotted an issue similar to this in the past that was reported, and the fix was to add the usb_storage module to the whitelist as I mentioned above. This is NOT working, however.

---

### Post by Rod Hull on 2008-07-30
Bumping - I've found that the keyboard problem is too sporadic for me to worry too much about now - it sometimes happens, sometimes not - totally random.

I suspect that it MAY have been something to do with fast-user switching that I use, my other half's profile only had USA in her keyboard layout the other day (which is odd since I'm sure it was previously set to UK), which I think was causing some problems anyway.

So, the main bug for me is the USB device renaming issue - can anyone help at all with this - it's driving me up the wall, and means that my cron script that uses unison to push files to my external HD is out of use whilst this is going on since it relies on the path not changing each time! I shouldn't have to manually alter it upon every hibernation/wake-up. 

Help!

---

### Post by quirks on 2009-06-20
Sorry for reviving such an old thread, but I had the same problem and found a solution to your USB disk issue. I documented it in a similar thread:

[http://ubuntuforums.org/showpost.php?p=7490840&postcount=3]("http://ubuntuforums.org/showpost.php?p=7490840&postcount=3")

---

### Post by chad.davis on 2010-03-11
The keyboard layout issue still seems unresolved (Ubuntu 9.10 Karmic Koala), namely an unidentified keyboard layout (presumably default USA) is added to the list of layouts after suspend/hibernate.

I just wanted to post my semi-automatic workaround. Rather than edit the keyboard layouts from the dialog after each resume, I just run a simple script.

Once you have your layouts setup the way you like, extract their names with:

```

gconftool --get /desktop/gnome/peripherals/keyboard/kbd/layouts

```

Make a simple script to re-apply this setting after resuming from hibernate/suspend:

```

cat > ~/bin/gnome-keyboard-reset
#!/usr/bin/env bash
gconftool --set /desktop/gnome/peripherals/keyboard/kbd/layouts --type=list --list-type=string '[us	euro,de]'
^D

chmod +x ~/bin/gnome-keyboard-reset

```

Beware of TABs in the output, as these can be contained in the name of some layouts, as they are in my case in "us\teuro".

Of course, you could automate this further, by noting before each suspend/hibernate what the value was, and putting some hooks in place so that you don't have to run the script manually after resuming.

Hope that helps someone.

---

