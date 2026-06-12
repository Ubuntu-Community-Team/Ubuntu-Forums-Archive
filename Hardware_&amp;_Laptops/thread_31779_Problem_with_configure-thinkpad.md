---
title: "Problem with configure-thinkpad"
date: 2005-05-04
forum: Hardware &amp; Laptops
---

### Post by Geden on 2005-05-04
Hey, I just got ubuntu Hoary on my Thinkpad T30. So far hinbernation, suspend, wireless etc. works like a charm. Only thing I havent been able to get up is the "configure-thinkpad" tool, it compiled and installed without any error messages, was added to the gnome menu, but when I try to run it, it comes up with an error message that says that /dev/thinkpad/thinkpad and /dev/thinkpad doesnt exist.
I got tpctl, thinkpad-base and thinkpad-source through synaptics, which should be the stuff needed to run it. I'm pretty new to linux, so I might have missed something, but I hope you guys can help me out on this one.

Regards,

---

### Post by kvidell on 2005-05-04
[QUOTE=Geden]Hey, I just got ubuntu Hoary on my Thinkpad T30. So far hinbernation, suspend, wireless etc. works like a charm. Only thing I havent been able to get up is the "configure-thinkpad" tool, it compiled and installed without any error messages, was added to the gnome menu, but when I try to run it, it comes up with an error message that says that /dev/thinkpad/thinkpad and /dev/thinkpad doesnt exist.
I got tpctl, thinkpad-base and thinkpad-source through synaptics, which should be the stuff needed to run it. I'm pretty new to linux, so I might have missed something, but I hope you guys can help me out on this one.

Regards,[/QUOTE]
I'm currently running Hoary on a T42p, but I ran it on a T30 before this...
I don't recall ever running that script and I didn't notice any features lacking...

Just curious: If everything's working, what will this script do for you?

---

### Post by Geden on 2005-05-04
Its just a GUI to make everyday use and configuration easier(like suspend when the lid is closed, right now it just turns off the screen). I tried it on a fedora core 3 install, and it seemed quite nice.

---

### Post by kvidell on 2005-05-04
[QUOTE=Geden]Its just a GUI to make everyday use and configuration easier(like suspend when the lid is closed, right now it just turns off the screen). I tried it on a fedora core 3 install, and it seemed quite nice.[/QUOTE]
You can make it suspend on lid-shut in the bios, too.

I might have to look in to it if it's just a simplicity thing :) Dog knows I'm lazy.

---

### Post by Geden on 2005-05-04
Yeah probably, but It would still be nice to get this working.

It might be that I lack the kernel-module-thinkpad, as I get nothing from a "modprobe thinkpad"

---

### Post by kvidell on 2005-05-04
If I can get my hands on the T30 again I'll definately have a look and see what I can come up with to help you...
(I get the IBM lappies through a leasing program at my housemate's employer, Cisco Sys... They only allow one person to have their laptops leases overlapping for several weeks, so I think I have like 4 days before the T30 goes back.)

---

### Post by alastair on 2005-05-04
Check the archives - the following might help (follow links as well) :

[http://ubuntuforums.org/showthread.php?t=26081](http://ubuntuforums.org/showthread.php?t=26081)

This /might/ be a "udev" issue i.e. device creation.

---

### Post by Geden on 2005-05-05
why thank you..  :)  after googling a bit and trying different things, I tried the following to create the thinkpad modules:

  #mkdir --mode=755 /dev/thinkpad
  #mknod --mode=664 /dev/thinkpad/thinkpad c 10 170
  #chown root:thinkpad /dev/thinkpad/thinkpad

(all with sudo from my own user)

now its there, but I dont have permission to run it from X and chmod 755 /dev/thinkpad/thinkpad doesnt do anything (neither does mknod --mode=755).

---

### Post by alastair on 2005-05-05
This looks like the sort of thing you'd want to try in the udev "links.conf" file perhaps.

i.e. /etc/udev/links.conf

Looking at how "links.conf" is read in the udev startup script (/etc/init.d/udev) shows it uses the file :

/etc/udev/permissions.d/udev.permissions

for the device perms.

So :

links.conf :

D thinkpad
M thinkpad/thinkpad  c 10 170

udev.permissions :

thinkpad/thinkpad:root:thinkpad:660

Assuming you are in the "thinkpad" group ....

Careful - I have not tried or tested this!

---

