---
title: "Hard Crash on iPod Unmount"
date: 2005-06-21
forum: Hardware &amp; Laptops
---

### Post by Octane on 2005-06-21
My box completely crashes when I try to unmount my iPod.

I have tried: eject /dev/sdb2
kdesu eject /dev/sb2
and right click -> unmount

All produce a hard system freeze.

Any ideas what may be causing this?

Thanks !

---

### Post by !nkubus on 2005-06-21
I have read in the linux magazine that firewire IPOD need to be removed by unloading your driver, so i would suggest  something:

modprobe -r sbp2

but do not forget to reload it  after.

EDIT:
ooops sorry i jsut saw your journal you had the answer

---

### Post by Octane on 2005-06-21
[QUOTE=!nkubus]I have read in the linux magazine that firewire IPOD need to be removed by unloading your driver, so i would suggest  something:

modprobe -r sbp2

but do not forget to reload it  after.

EDIT:
ooops sorry i jsut saw your journal you had the answer[/QUOTE]
Thanks for your help !nkubus

While I would love to be able to unmount it from by right click icon -> unmount... my current work around is to umount manually from a shell

---

### Post by !nkubus on 2005-06-21
To have it automatically mounted or unmounted, with gtkPod uyou have that hability:

there is 2 script

~/.gtkpod/gtkpod.in and    [will be launch when you open gtkPod]
~/.gtkpod/gtkpod.out         [will be launch when you close gtkPod]

in there you can put the script you want, soputting your mount , unmount and unload script.

 hope this helps :)

---

### Post by Octane on 2005-06-25
[QUOTE=!nkubus]To have it automatically mounted or unmounted, with gtkPod uyou have that hability:

there is 2 script

~/.gtkpod/gtkpod.in and    [will be launch when you open gtkPod]
~/.gtkpod/gtkpod.out         [will be launch when you close gtkPod]

in there you can put the script you want, soputting your mount , unmount and unload script.

 hope this helps :)[/QUOTE]
 The problem was that I was letting gtkpod control mounting of the ipod. I unchecked that preference and created my own mounting scripts. See my journal post here: [http://www.ubuntuforums.org/journal.php?do=showjournal&j=142#e343](http://www.ubuntuforums.org/journal.php?do=showjournal&j=142#e343)

---

