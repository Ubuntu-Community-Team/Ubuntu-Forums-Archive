---
title: "Satellite L745-S4110 Brightness Keys not working"
date: 2012-12-15
forum: Hardware
---

### Post by mvmacd on 2012-12-15
My brightness keys don't work on Ubuntu 12.10 64-bit, on my Toshiba Satellite L745-S4110.  [FN+F6, FN+F7]
I should mention it works to change brightness via **Brightness and Lock**.  Just the FN hotkeys do not work most of the time [see below].
```

$ uname -a
Linux toshi 3.5.0-19-generic #30-Ubuntu SMP Tue Nov 13 17:48:01 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

Here is syslog after pressing my brightness keys repeatedly:

```

Dec 15 19:29:24 toshi kernel: [  380.417102] atkbd serio0: Unknown key pressed (translated set 2, code 0xee on isa0060/serio0).
Dec 15 19:29:24 toshi kernel: [  380.417106] atkbd serio0: Use 'setkeycodes e06e <keycode>' to make it known.
Dec 15 19:29:24 toshi kernel: [  380.534161] atkbd serio0: Unknown key released (translated set 2, code 0xee on isa0060/serio0).
Dec 15 19:29:24 toshi kernel: [  380.534172] atkbd serio0: Use 'setkeycodes e06e <keycode>' to make it known.
Dec 15 19:29:24 toshi kernel: [  380.602288] atkbd serio0: Unknown key pressed (translated set 2, code 0xee on isa0060/serio0).
Dec 15 19:29:24 toshi kernel: [  380.602298] atkbd serio0: Use 'setkeycodes e06e <keycode>' to make it known.
Dec 15 19:29:24 toshi kernel: [  380.633982] atkbd serio0: Unknown key released (translated set 2, code 0xee on isa0060/serio0).
Dec 15 19:29:24 toshi kernel: [  380.633992] atkbd serio0: Use 'setkeycodes e06e <keycode>' to make it known.
Dec 15 19:29:24 toshi kernel: [  380.692092] atkbd serio0: Unknown key released (translated set 2, code 0x55 on isa0060/serio0).
Dec 15 19:29:24 toshi kernel: [  380.692102] atkbd serio0: Use 'setkeycodes 55 <keycode>' to make it known.

```

I asked over on askubuntu.com 
[http://askubuntu.com/questions/229128/toshiba-satellite-l745-s4110-brightness-keys-not-working#comment282944_229128](http://askubuntu.com/questions/229128/toshiba-satellite-l745-s4110-brightness-keys-not-working#comment282944_229128)
But the suggestions did not work, which is why I'm posting a thread here.

So the strange thing is sometimes it works. out of a couple days, it has worked twice.  Seems to possibly related to Suspend, it has only worked after resuming it seems.

Well I hope someone here knows what's going on and how to fix it.  

Thanks!

---

### Post by Toz on 2012-12-16
> Here is syslog after pressing my brightness keys repeatedly:

Which message relates to the brightness up event and which message relates to the brightness down event?

And what does the following return?
```
xmodmap -pke | grep -i brightness
```

---

### Post by mvmacd on 2012-12-16
> **Toz said:**
> Which message relates to the brightness up event and which message relates to the brightness down event?

And what does the following return?
```
xmodmap -pke | grep -i brightness
```

While testing which one did what message, I discovered pressing "FN" generates 3 lines, by itself:
```

Dec 16 09:31:14 toshi kernel: [  202.129189] atkbd serio0: Unknown key pressed (translated set 2, code 0x55 on isa0060/serio0).
Dec 16 09:31:14 toshi kernel: [  202.129199] atkbd serio0: Use 'setkeycodes 55 <keycode>' to make it known.
Dec 16 09:31:14 toshi kernel: [  202.208211] atkbd serio0: Unknown key released (translated set 2, code 0x55 on isa0060/serio0).
Dec 16 09:31:14 toshi kernel: [  202.208221] atkbd serio0: Use 'setkeycodes 55 <keycode>' to make it known.

```
That is just pressing FN, and releasing.

This is FN+F7 [Brightness up]
```

Dec 16 09:33:20 toshi kernel: [  328.280218] atkbd serio0: Unknown key pressed (translated set 2, code 0x55 on isa0060/serio0).
Dec 16 09:33:20 toshi kernel: [  328.280223] atkbd serio0: Use 'setkeycodes 55 <keycode>' to make it known.
Dec 16 09:33:20 toshi kernel: [  328.335855] atkbd serio0: Unknown key pressed (translated set 2, code 0xee on isa0060/serio0).
Dec 16 09:33:20 toshi kernel: [  328.335865] atkbd serio0: Use 'setkeycodes e06e <keycode>' to make it known.
Dec 16 09:33:20 toshi kernel: [  328.407851] atkbd serio0: Unknown key released (translated set 2, code 0xee on isa0060/serio0).
Dec 16 09:33:20 toshi kernel: [  328.407861] atkbd serio0: Use 'setkeycodes e06e <keycode>' to make it known.
Dec 16 09:33:21 toshi kernel: [  328.452864] atkbd serio0: Unknown key released (translated set 2, code 0x55 on isa0060/serio0).
Dec 16 09:33:21 toshi kernel: [  328.452874] atkbd serio0: Use 'setkeycodes 55 <keycode>' to make it known.

```

This is brightness down [FN+F6]
```

Dec 16 09:34:18 toshi kernel: [  385.839300] atkbd serio0: Unknown key pressed (translated set 2, code 0x55 on isa0060/serio0).
Dec 16 09:34:18 toshi kernel: [  385.839310] atkbd serio0: Use 'setkeycodes 55 <keycode>' to make it known.
Dec 16 09:34:18 toshi kernel: [  386.193611] atkbd serio0: Unknown key released (translated set 2, code 0x55 on isa0060/serio0).
Dec 16 09:34:18 toshi kernel: [  386.193615] atkbd serio0: Use 'setkeycodes 55 <keycode>' to make it known.

```

I dunno why pressing brightness down is shorter..

Here is the output of xmodmap
```

matt@toshi:~ $ xmodmap -pke | grep -i brightness
keycode 232 = XF86MonBrightnessDown NoSymbol XF86MonBrightnessDown
keycode 233 = XF86MonBrightnessUp NoSymbol XF86MonBrightnessUp
keycode 237 = XF86KbdBrightnessDown NoSymbol XF86KbdBrightnessDown
keycode 238 = XF86KbdBrightnessUp NoSymbol XF86KbdBrightnessUp

```

---

### Post by Toz on 2012-12-16
> I dunno why pressing brightness down is shorter..
Its not recognizing the brightness down key. Do these responses change after a suspend/resume cycle?

What kernel parameters are you currently using:
```
cat /proc/cmdline
```

Open a terminal window, and run:
```
acpi_listen
```
...then press the brightness up and brightness down keys and post back what returns in the terminal window with each press.


And finally, can you post back the results of:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```
...lets see what backlight interfaces you have available.

---

### Post by mvmacd on 2012-12-16
> **Toz said:**
> Its not recognizing the brightness down key. Do these responses change after a suspend/resume cycle?

What kernel parameters are you currently using:
```
cat /proc/cmdline
```

Open a terminal window, and run:
```
acpi_listen
```
...then press the brightness up and brightness down keys and post back what returns in the terminal window with each press.


And finally, can you post back the results of:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```
...lets see what backlight interfaces you have available.

Yes, I just resumed from hibernation and my brightness keys work.

So I will do everything while brightness keys work, then I will reboot and edit in the results.

```

matt@toshi:~ $ cat /proc/cmdline 
BOOT_IMAGE=/boot/vmlinuz-3.5.0-19-generic root=UUID=94c47be0-9b5a-431d-8bfc-dbe2f5068a15 ro quiet splash vt.handoff=7

```

acpi_listen returns no result while changing brightness [blank output].

```

matt@toshi:~ $ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
/sys/class/backlight/acpi_video0
7
7
/sys/class/backlight/intel_backlight
4648
4648
/sys/class/backlight/toshiba
7
7

```


I will edit this in 10 minutes after I reboot and do it again.

--

I've rebooted, brightness keys don't work as ususal.. and everything else is the same. No acpi_listen output, [should have the same kernel parameters] and the same backlight devices.

---

### Post by Toz on 2012-12-16
Can you post back the contents of your pm-suspend.log, dmesg and syslog files after a suspend?

```
pastebinit /var/log/pm-suspend.log
pastebinit /var/log/dmesg
pastebinit /var/log/syslog
```
...and post back the links that are generated. I'd like to see if there is anything there.

Also found these:
- [https://bugs.launchpad.net/linuxmint/+bug/925842]("https://bugs.launchpad.net/linuxmint/+bug/925842")
- [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/934095]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/934095")

---

### Post by mvmacd on 2012-12-16
pm-suspend.log [http://paste.ubuntu.com/1444493/](http://paste.ubuntu.com/1444493/)
dmesg [http://paste.ubuntu.com/1444506/](http://paste.ubuntu.com/1444506/)
syslog [http://paste.ubuntu.com/1444509/](http://paste.ubuntu.com/1444509/)

---

### Post by Toz on 2012-12-17
Here is what I'm thinking. When you suspend, all the modules are unloaded, then on resume they are re-loaded. Something is happening with this reload of the modules that is enabling your function keys. I believe that the toshiba_acpi module is responsible for the function keys.

Can you try, right after a reboot when the function keys aren't working, to manually unload and reload this module:
```
sudo modprobe -r toshiba_acpi
sudo modprobe toshiba_acpi
```
...does this make the brightness function keys work?

Can you also post back the results from:
```
modinfo toshiba_acpi
```

You also have a number of acpi error/warning messages in your dmesg. You might want to check for a bios update.

---

### Post by mvmacd on 2012-12-17
I tried that, removing toshiba_acpi and modprobing it, but that didn't do anything.

```

root@toshi:/home/matt# modinfo toshiba_acpi
filename:       /lib/modules/3.5.0-19-generic/kernel/drivers/platform/x86/toshiba_acpi.ko
license:        GPL
description:    Toshiba Laptop ACPI Extras Driver
author:         John Belmonte
srcversion:     C9FE8AC424A1998413CC2AF
alias:          acpi*:TOS1900:*
alias:          acpi*:TOS6208:*
alias:          acpi*:TOS6200:*
depends:        wmi,sparse-keymap
intree:         Y
vermagic:       3.5.0-19-generic SMP mod_unload modversions

```

Also, the laptop was just bought about 2 weeks ago, brand new.  Do you think the BIOS already has an update?  I've ruined a old sony laptop once by updating the bios, it turned off in the middle of it and basically rendered the motherboard bricked.

---

### Post by Toz on 2012-12-17
How about:
```
sudo modprobe -r toshiba_acpi
sudo modprobe -r sparse_keymap
sudo modprobe -r wmi
sudo modprobe wmi
sudo modprobe sparse_keymap
sudo modprobe toshiba_acpi
```

---

### Post by mvmacd on 2012-12-17
Just tried it, it does not fix it. :(

---

### Post by Toz on 2012-12-17
Hmmm. I'm sorry but I'm out of ideas. Perhaps its best to either create a new bug report or add yourself to this one: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/934095]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/934095").

---

### Post by mvmacd on 2012-12-17
> **Toz said:**
> Hmmm. I'm sorry but I'm out of ideas. Perhaps its best to either create a new bug report or add yourself to this one: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/934095]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/934095").

:( ok, thanks for helping.  I guess I could add to that bug report, but it looks like it hasn't been udpated since March.. And it's a different toshiba model.

The weird thing is my brightness works with "Brightness and Lock" but it's just the hotkeys that don't work upon a fresh reboot.  It seems it might just be button mapping.  But I have no idea how to fix it.  I guess next I will try going to Keyboard Shortcuts, and see if the keys register as hotkeys.  Maybe I can try to make a script to echo a number in the brightness in /sys/ somewhere..

But even then it would just be a workaround and I would rather get it fixed somehow so I have the brightness bubble that pops up. 

Maybe I should try it on my live ubuntu 12.10 flash drive and see if it works there.

---

### Post by M3m3nt0 on 2012-12-17
I suffered a similar problem on my Toshiba Satellite PRO U500...

I was unable to adjust the brightness at all; I resolved adding *acpi_backlight=vendor *to the boot line.

I hope this helps ;)

---

### Post by mvmacd on 2012-12-17
> **M3m3nt0 said:**
> I suffered a similar problem on my Toshiba Satellite PRO U500...

I was unable to adjust the brightness at all; I resolved adding *acpi_backlight=vendor *to the boot line.

I hope this helps ;)

Thanks for the tip, however I have already tried this.  And it doesn't fix it.

---

### Post by mvmacd on 2013-03-26
So I am still suffering from this issue. 

However, I often use hibernate and [when it works,] suspend, and I have created a script to use in my terminal to change the brightness [using **intel_backlight**]
I went to Keyboard shortcuts, and my brightness down button [fn+f6] produces the code 0x78, and the brightness up [fn+f7] does not even register as a hotkey.

---

### Post by Toz on 2013-03-26
Can you try the **acpi_osi=\"!Windows 2012\"** kernel parameter? The relevant line in /etc/default/grub should look like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\"!Windows 2012\""
```

Note the backslash escaping of the quotes.

---

