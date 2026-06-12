---
title: "install GUI for ubuntu server, hangs"
date: 2009-03-26
forum: Installation &amp; Upgrades
---

### Post by :Dodo on 2009-03-26
Hi all,

First off: I'm not experienced with Linux/Ubuntu.

I've installed Ubuntu 8.04 LTS on a VM. I wanted to have a GUI and with that thread:

[http://ubuntuforums.org/showthread.php?t=1089392&highlight=desktop+or+server](http://ubuntuforums.org/showthread.php?t=1089392&highlight=desktop+or+server)

There is the command supplied to add the GUI:
sudo apt-get install ubuntu-desktop

However, after some time, the system hangs and outputs (last four lines):
```

Processing triggers for initramfs-tools
update-initramfs: Generating /boot/initrd.img-2.6.24-23-server
myuser@mymachine:~$ * Reloading system log daemon...

* Reloading system log daemon...

```

The following thread had the same(?) problems, however there is no reply:
[http://ubuntuforums.org/showthread.php?t=980644](http://ubuntuforums.org/showthread.php?t=980644)

---

### Post by :Dodo on 2009-03-26
I'm unsure, if the installation routine really hangs, due to the following:

On the first console, where I'm installing (with the above output) I can write stuff (however, I'm a bit scared of hitting enter)

I opened the second console, logged in and called "ps -all" to show the processes. Here, tty1 shows up as using only one process, which is the command bash.

So, is the installation routine really hanging, or is there simply something wrong with that output?

---

### Post by :Dodo on 2009-03-26
I dared to hit the Enter button and the standard prompt showed up :)

However, how can I see, that the installation operated correctly :confused:

---

### Post by spcwingo on 2009-03-26
You can try:

```
sudo /etc/init.d/gdm stop && sudo /etc/init.d/gdm start
```

This will only work if you also installed GDM (if you installed ubuntu-desktop it will include GDM).  If you didn't install GDM just type:

```
startx
```

---

### Post by :Dodo on 2009-03-26
Thanks for your reply.

I restarted the system and the Desktop shows up. Updating and installing, changing resolution, everything seems to work. 

So I think this issue ("Reloading system log daemon...") was a non fatal issue, which can be solved by pushing enter.

---

