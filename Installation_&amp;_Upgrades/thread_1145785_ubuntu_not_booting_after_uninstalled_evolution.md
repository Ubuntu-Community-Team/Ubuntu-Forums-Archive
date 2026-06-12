---
title: "ubuntu not booting after uninstalled evolution"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by windows-killer on 2009-05-01
I removed evolution by selecting everything related to it from synaptic and all of the sudden my computer froze. I had to reset my computer, I got to the log in screen I entered my username and password, but nothing happens. I just see a black screen.

How can I fix this problem?

---

### Post by jbrown96 on 2009-05-02
> **windows-killer said:**
> I removed evolution by selecting everything related to it from synaptic and all of the sudden my computer froze. I had to reset my computer, I got to the log in screen I entered my username and password, but nothing happens. I just see a black screen.

How can I fix this problem?


Reboot your machine. If you see a prompt to pres Esc to enter the grub menu, do it. From the grub screen choose the recovery version of the most recent kernel (largest version number). Once that boots, choose a root shell. ```
sudo dpkg-reconfigure --xorg-server
``` Then ```
sudo reboot
``` You should be fine now, but if you have a Nvidia or Ati graphics card you will need to reenable the drivers in System-->Admin-->Hardware drivers.

---

### Post by windows-killer on 2009-05-02
> **jbrown96 said:**
> Reboot your machine. If you see a prompt to pres Esc to enter the grub menu, do it. From the grub screen choose the recovery version of the most recent kernel (largest version number). Once that boots, choose a root shell. ```
sudo dpkg-reconfigure --xorg-server
``` Then ```
sudo reboot
``` You should be fine now, but if you have a Nvidia or Ati graphics card you will need to reenable the drivers in System-->Admin-->Hardware drivers.

Thanks for your reply, jbrown96!

I did a google search and I found my answer on the internet.
so the problem was: when I selected everything related to evolution in synaptic. It un-installed the Ubuntu-desktop. so when I reboted my pc, I went to the command line and I typed ```
sudo apt-get install ubuntu-desktop
``` and voila!!! it worked!!!


I wish there was an easier way repairing ubuntu!
It would be cool if ubuntu had something similar to ```
known last configuration
``` or ```
restore to previous working state
```

Do you know if this feature exists btw?
if not, then another easier way without having to deal with the command line? thanks:lolflag:

---

### Post by doas777 on 2009-05-02
actually last known good would not save you in this instance, since programs were uninstalled. Last known good is primarily registry information (stored in hklm/software/microsoft/windows/clonecontrolset if i recall correctly). on sucessful login, the clonecontrolset is copied to currentcontrolset, where it remails until the end of the session when it is written back to the clone. if files are deleted, last know good willnot save you, you must rely on restore/recovery tools in that case.

there is probably a way to snapshot systemstate, but i imagine that would take quite a bit of storage space, if it were to backup every file that was altered or deleted.

---

### Post by windows-killer on 2009-05-02
> **doas777 said:**
> actually last known good would not save you in this instance, since programs were uninstalled. Last known good is primarily registry information (stored in hklm/software/microsoft/windows/clonecontrolset if i recall correctly). on sucessful login, the clonecontrolset is copied to currentcontrolset, where it remails until the end of the session when it is written back to the clone. if files are deleted, last know good willnot save you, you must rely on restore/recovery tools in that case.

there is probably a way to snapshot systemstate, but i imagine that would take quite a bit of storage space, if it were to backup every file that was altered or deleted.

what about a software that takes the snapshot of your os and when you have problems you will select "restore" from the grub menu. The snapshot would be saved on a external hard drive and it would restore your os to the last working state.

is there such a software available for ubuntu? 
*I dont even mind if I have to pay for such a necessary software like that*

---

### Post by doas777 on 2009-05-02
well it sounds like you are looking for backup utilities, or imaging utilities. I'm by no means an expert on this, but check out this page: [https://wiki.ubuntu.com/TimeVault](https://wiki.ubuntu.com/TimeVault)
and if timevault isn't right for you, there is a section that lists some other snapshot systems.

good luck

---

### Post by windows-killer on 2009-05-02
thanks for the link.
I read that timevault is a discontinued project, is that right?

---

