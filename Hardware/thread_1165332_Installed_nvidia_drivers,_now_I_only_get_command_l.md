---
title: "Installed nvidia drivers, now I only get command line at boot"
date: 2009-05-20
forum: Hardware
---

### Post by 147@wzUa£kdh2§NHe on 2009-05-20
I installed the 180 drivers from the Hardware Drivers tool in Ubuntu 9.04. After restarting, I only get the command line. I've tried running nvidia-xconfig, but that didn't help. I then tried editing xorg.conf as described in [this post]("http://ubuntuforums.org/showpost.php?p=7105138&postcount=5"), but to no avail.

I have two 8800 GT and I'm running 64 bit.

What could be wrong, and how can I fix it?

---

### Post by coffeecat on 2009-05-20
I don't know what's wrong, but I would suggest this. Boot up in recovery mode, and when you get to where you are given a selection, choose xfix. This only takes a couple of seconds. It will replace your edited xorg.cong, but will disable the nvidia driver and put you back to the open-source nv driver, so that at least you'll be able to boot into a GUI.

Now choose 'continue to boot into desktop' or whatever the wording is, or reboot.

Once you're back in the desktop, try activating the 173 driver. I had a minor issue with the 180 driver and the 8400GS chipset (on one machine but curiously not on another) which was fixed by using the 173 driver. Your problem is more serious, so this may or may not help. If the xserver breaks again, simply use xfix again, and look for other solutions.

---

### Post by stefangr1 on 2009-05-20
Can you maybe post some errors?

If you login to the console and type "sudo startx" you probably get some.

---

### Post by 147@wzUa£kdh2§NHe on 2009-05-20
Thanks, but nevermind, works perfectly now. Checked the log file, and yep, parse error... Forgot an "EndSection". :P

---

