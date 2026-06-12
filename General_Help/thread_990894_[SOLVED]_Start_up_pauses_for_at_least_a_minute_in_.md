---
title: "[SOLVED] Start up pauses for at least a minute in the middle!"
date: 2008-11-23
forum: General Help
---

### Post by svivian on 2008-11-23
This has happened since I upgraded to Intrepid. When I boot up the computer, it gets to the Ubuntu loading screen, but the progress bar stops about halfway for at least a minute. It doesn't even sound like it's doing anything.

What could be causing this problem? Is it possible to see what it's doing, or not doing as the case may be?

---

### Post by AnoPoli on 2008-11-23
Try to hit escape or Alt+F1 trough Alt+F7 (i don't know the correct combination for you) and see what is happening in the background. Maybe some message help you to figure out the problem causing the delay.

---

### Post by Keith Hedger on 2008-11-23
The pause sounds like it is checking a disk try Alt+F1 as AnoPoli says and see what it is doing

---

### Post by -Zeus- on 2008-11-23
you could try adding the options 'quiet nosplash' to your /boot/grub/menu.lst entries

---

### Post by drs305 on 2008-11-23
Depending on when the delay is occurring, you may be able to see where it is hanging up by looking at the /var/log/dmesg file. That file records what happens during the initial boot process. You can look for "error", "fail" or look at the time line to see where there are significant delays.

---

### Post by svivian on 2008-11-23
Alt+F8 did it for me. It's stopping on *"configuring network interfaces..."* for ages.

Any ideas? I'm sure the network is set up fine, there are no problems with my connection. It's a wireless connection if that helps.

---

### Post by svivian on 2008-11-24
bump

I forgot to mention in my first post that it's only since I upgraded to Intrepid that this has been hppening.

---

### Post by jerrykenny on 2008-11-24
Its maybe cos yer wifi is set to "start at boot" . . . soz, i'm using kde not gnome, but check your wifi settings using the admin tab . . 

Its probably better not to start networking at boot in your case, but to use the gnome network manager to do it after you login

---

### Post by svivian on 2008-11-24
> **jerrykenny said:**
> Its maybe cos yer wifi is set to "start at boot" . . . soz, i'm using kde not gnome, but check your wifi settings using the admin tab . . 

Its probably better not to start networking at boot in your case, but to use the gnome network manager to do it after you login

How would I do that? I can't see any options in Prefs>Network configuration or Admin>Network tools.

---

### Post by svivian on 2008-11-26
I took a look at /etc/network/interfaces and stripped everything out apart from just the stuff to do with my connection, but I'm still getting the same problem.

The file looked like this:
```
auto lo
iface lo inet loopback
#iface eth0 inet dhcp
auto eth2
#iface eth2 inet dhcp
auto wlan0
#iface wlan0 inet dhcp

iface eth1 inet dhcp
auto eth1
iface eth3 inet dhcp
auto eth3

iface ath0 inet dhcp
wireless-key s:XXX
wireless-essid VOYAGER2091-17
auto ath0

iface eth0 inet dhcp
auto eth0
```

Now it looks like this:
```

iface ath0 inet dhcp
wireless-key s:XXX
wireless-essid VOYAGER2091-17
auto ath0

iface eth0 inet dhcp
auto eth0
```
(XXX=wireless key, removed for obvious reasons)

Does this look normal?

---

### Post by svivian on 2008-11-26
bump

---

### Post by eldragon on 2008-11-26
uhh, try the following (i dont know if it will work)

edit the hosts file (/etc/hosts) and add your computer's host name to the 127.0.0.1 and to the same entry concerning ipv6 (dont know its name)

this seems to fix a problem during shudown which hangs the process until timeout. might work for you too

example:
```

127.0.0.1 localhost dragonlaptop

```

EDIT
i know (from personal experience), that if you remove both lines starting with "auto" your problem will be gone. but i dont know if thats an optimal solution. anyway, if you use network manager, it will handle your connections from now on. so theres that, and no harm removing the auto lines in /etc/network/interfaces

---

### Post by rsay on 2008-11-26
I was having this problem and solved it by changing /etc/network/interfaces to the following:

```
auto lo
iface lo inet loopback

```

Then just configure you network in network-manager or whatever you use (I use wicd)

---

### Post by svivian on 2008-11-27
Thank you rsay!! Everything's working perfectly now!

---

