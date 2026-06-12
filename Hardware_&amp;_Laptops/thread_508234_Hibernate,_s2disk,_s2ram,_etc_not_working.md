---
title: "Hibernate, s2disk, s2ram, etc not working"
date: 2007-07-24
forum: Hardware &amp; Laptops
---

### Post by jon_herr on 2007-07-24
I'm attempting to debug a problem with hibernation...  

The symptoms are - if I initiate hibernation from the menus in gnome then the screen goes black then after a few seconds it comes back to the gnome-desktop login screen.  However, after this I can't do anything - not even ctrl-alt-f1 to another terminal.  Each attempt is rewarded with what looks like a restart of gdm.

If I kill gdm then perform a s2disk the process seems to work - but on recovery I get a black screen and no activity.

The frustrating thing is that this was working until I tried to install kde-desktop.  Is there anything I can do short of a re-install?

Any simple ideas?  

Thanks,
Jon

---

### Post by zgornel on 2007-07-24
Try getting the scripts from here [http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/) and follow the instructions.
It might work.

---

### Post by jon_herr on 2007-07-24
Thanks,
I've followed those instructions to the letter and determined that I can hibernate using s2disk so long as I kill GDM first...  Problem is that when I come out of hibernation I have no gdm and nothing works at all.

Can't start gdm, can't even see a console.

So the problem comes back around to being something with gdm, video driver, or touch screen driver.  I had to compile the touch screen driver myself - the video driver is vesa from ubuntu.

I don't think the touch screen driver can be doing it since I'm using the same set up as a friend of mine.

Oh, and hibernate worked on this box when it was 'born' with vanilla Feisty.

Jon

---

### Post by spupy on 2007-07-24
For me s2ram works correct, but instead of s2disk try this command, might just work: 
Run it as root or after "sudo su":
```
echo -n "disk" > /sys/power/state
```

One more thing: when you restore from hibernate, everything might look ugly and even not look like your desktop at all. Try to switch with Ctrl+Alt+F1 and then switch back to X with Alt+F7.

---

### Post by zgornel on 2007-07-25
Try also taking a look here [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/46064](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/46064) . I remember something with that Option "VBErestore" "true" - it worked for me but on edgy.

---

