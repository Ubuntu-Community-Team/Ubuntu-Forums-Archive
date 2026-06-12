---
title: "ubuntu 8.10 startup without bluetooth"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by jellynite on 2009-02-20
After downloading/installing Ubuntu 8.10 with WUBI, I restarted my desktop XP (home edition with SP3). I am presented with a menu choice of booting WindowsXP or Ubuntu. When I select Ubuntu the Linux OS startup process begins with file systems/drivers/processes etc, started OK, but the startup process stops at "Starting Bluetooth". CTRL-ALT-DEL stops the Linux processes, but again stops at "Stopping Bluetooth" - I have to power down my desktop to get back to menu. So any ideas - why does it try to start the bluetooth process (bluetooth is not installed on the desktop) ??

---

### Post by CKDewey on 2009-02-20
To disable bluetooth:

- Log in to the console by holding down <Cntl> + <Alt> and pressing 'F2' and then input your username and password
- Install sysv-rc-conf utility (you'll be asked for the password again):

```
$ sudo apt-get install sysv-rc-conf
```- Run the utility and disable blutooth for runlevels 2 through 5; use the arrow keys to move around, space bar to remove the 'X' and 'q' to quit: 

```
$ sudo sysv-rc-conf
```- Reboot (you may press the power button if nothing else works)

---

### Post by Galifron on 2009-04-12
Hope it's ok to continue with this thread as I'm having the same problem, and jellynite hasn't said if it was successful.

I have Ubuntu 8.10 on a usb flash drive; and have the same 'stopping at bluetooth' problem. I tried the code:

$ sudo apt-get install sysv-rc-conf

but receive the following:

Reading package lists... Done
Building dependency tree
Reading state information... Done
Package sysv-rc-conf is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source.
E: Package sysv-rc-conf has no installation candidate.

Does the E: refer to the flash drive, as that is F. 
(E is a CD Drive).

Thanks for any assistance.

- Chris

---

