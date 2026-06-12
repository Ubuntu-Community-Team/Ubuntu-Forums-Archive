---
title: "Power management not working on Thinkpad A20m"
date: 2009-08-08
forum: Hardware
---

### Post by silverrope on 2009-08-08
I got xubuntu 9.04 running on a IBM Thinkpad A20m (Pentium III 600 Mhz, 256 MB memory, latest BIOS 1.13). Nearly everything is working (sound, wireless card, etc.) except for the power management. The gnome-power-management icon shows that it is AC-connected, but when I unplug the AC, it does not display the battery usage. The mouseover display continues to say that the "Computer is running on AC power". I have also the gnome panel battery monitor applet displayed and it always show 50% usage even when the battery is nearly drained or full.

Some other inconsistencies. Under the power management preferences, I set it to "Ask me" when the power button is pressed. But the laptop just powers off when I press the power button. For laptop lid closed, I set it to "Do nothing", but when I close the lid, the screen blanks out (power stays on).

Before I go on to more serious testing with suspend or hibernate, I would like to resolve these basic power issues first. Can anyone help or direct me to some info?

Thanks.

---

### Post by Sera88 on 2009-10-11
Just notifying that I have the exact same issue with my Toshiba Satellite Pro 4290. Running Xubuntu 9.04, Gnome 2.26.1, kernel 2.6.28-15-generic. The icon is right now showing I'm using AC power although I'm on battery power.

---

### Post by diesch on 2009-10-11
There is a [mailing list](http://mailman.linux-thinkpad.org/mailman/listinfo/linux-thinkpad) for Linux users on Thinkpads. Maybe you can find some help there.

The [ThinkWiki]("http://www.thinkwiki.org") is often useful, too.

---

### Post by dave2001 on 2010-04-13
Not sure why this thread is marked solved, maybe you found an answer on your own...Anyway, I have a Thinkpad A20m as well. The bios is old, and acpi must be forced on. To get the power management working correctly, I had to do the following.
Bring up your grub configuration file for editing by typing this in terminal.
Code:

$ gksudo gedit /boot/grub/menu.lst

Save the file that opens as menu.lst_old just in case you mess up the one your editing and need to reload it.

Now on the "kernel" line, which tells grub which kernel version to load, you need to add "acpi=force" to the end of the text, so that it looks like this.

kernel        /boot/vmlinuz-2.6.24-27-generic root=sda1 ro quiet splash acpi=force 

Then save the file as /boot/grub/menu.lst. Now go back to the terminal and enter this to be sure the grub boot-loader sees your changes.
Code:

$ sudo update-grub

Then reboot, acpi should now be on, and all your power management should work. I should mention I am running Xubuntu 8.04 LTS rather than your Ubuntu 9.10, so there may be some difference I'm not aware of.

---

