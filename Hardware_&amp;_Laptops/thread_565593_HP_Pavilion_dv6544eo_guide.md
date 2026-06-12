---
title: "HP Pavilion dv6544eo guide"
date: 2007-10-02
forum: Hardware &amp; Laptops
---

### Post by nawitus on 2007-10-02
This is how I installed Ubuntu 7.04 Feisty Fawn to my laptop.

First, use Partition magic to create 25gb(or how much you want) ext3 partition and 2gb swap. Then, insert Ubuntu live CD and reboot. Press F6 and add two commands "noapic nolapic" and hit install. 
Without these commands the setup will freeze.

If you get squashfs errors, you probably have a corrupted cd, burn it again (I used an old burner which didn't work, but a new cd burner works).

X Server will probably fail, then press ok. Then type following command:
sudo dpkg-reconfigure xserver-xorg
Then, do not select the 'nv' driver, but 'vesa'. Hit ok until you get back to the command line and type
sudo startx
Now, hopefully gnome will start and you can then hit Install and actually install it to the hard drive.

When the laptop restarts remember to remove the cd, and possibly press esc to see a list of OS selections. Press e  and you will see different boot parameters for ubuntu. Press down couple of times and then press 'o' to create a new line. Select the new line and press 'e', and type noapic. Create another line for nolapic. Then press b.

Now, everything should be ok to start setting up your drivers etc.

Ubuntu would fail at boot about 50% of time, which I solved later on by "all_generic_ide" in the boot parameters. You should google for grub editing guide to see how to make those boot parameters permanent.

---

