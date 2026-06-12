---
title: "Nvidia graphics driver on Sony Vaio Z21WN"
date: 2011-01-15
forum: Hardware
---

### Post by kevinchannon on 2011-01-15
Does anyone know which is the correct Nvidia graphics driver to use on this laptop?  Ubuntu 10.04 was working OK, but when I upgraded to 10.10 it doesn't seem to be using the graphics card properly, since the display is quite jerky and scrolling is not smooth at all etc.

I when to System > Administration > Additional Drivers and installed the recommended driver (nvidia-current), however on restarting the X server will not start, the computer boots into a terminal.  Logging on and trying to manually start X with 'startx' fails with the error "no devices found".

If I delete the xorg.conf file created by installing the Nvidia driver and restart then it boots fine, but does not use accelerated graphics.

Just wondering if anyone has got this to work properly in Maverick on this laptop yet?

If not, what's the easiest way to role-back to a previous distribution?

---

### Post by gordintoronto on 2011-01-15
What graphics adapter is in the computer? The Terminal command:
lspci
will show you, on the line that contains "vga."

To revert to an earlier version requires installing from scratch. If you do not have a separate /home partition, it will erase all your data, so you need to save it elsewhere first. Even if you have a separatre /home partition, make sure you have good backup first.

---

### Post by kevinchannon on 2011-01-16
Thanks for the reply, doing ```
lspci | grep "VGA"
``` gives

```
VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
VGA compatible controller: nVidia Corporation G98 [GeForce 9300M GS] (rev a1)
```
I guess that the Intel one is the on-board graphics (which I think is what it's using at the moment) and the nVidia one is the actual graphics card.

I've looked quite hard for reports of the problem, but can't find anything that is the same.  Lots of reports of not being able to control the screen brightness and such, but not complete failure to use the driver at all :(

---

### Post by kevinchannon on 2011-01-16
Thanks for the reply, doing ```
lspci | grep "VGA"
``` gives

```
VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
VGA compatible controller: nVidia Corporation G98 [GeForce 9300M GS] (rev a1)
```
I guess that the Intel one is the on-board graphics (which I think is what it's using at the moment) and the nVidia one is the actual graphics card.

I've looked quite hard for reports of the problem, but can't find anything that is the same.  Lots of reports of not being able to control the screen brightness and such, but not complete failure to use the driver at all :(

---

### Post by kevinchannon on 2011-01-16
Thanks for the reply, doing ```
lspci | grep "VGA"
``` gives

```
VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
VGA compatible controller: nVidia Corporation G98 [GeForce 9300M GS] (rev a1)
```
I guess that the Intel one is the on-board graphics (which I think is what it's using at the moment) and the nVidia one is the actual graphics card.

I've looked quite hard for reports of the problem, but can't find anything that is the same.  Lots of reports of not being able to control the screen brightness and such, but not complete failure to use the driver at all :(

---

### Post by kevinchannon on 2011-01-16
Sorry about the multiple identical posts: browser malfunction!

---

### Post by kevinchannon on 2011-01-16
Sorry about the multiple identical posts: browser malfunction!

---

### Post by kevinchannon on 2011-01-16
Sorry about the multiple identical posts; browser malfunction!

---

### Post by kevinchannon on 2011-01-16
Sorry about the multiple identical posts; browser malfunction!

---

### Post by gordintoronto on 2011-01-16
It's my understanding that the Intel video consumes less power, but the Nvidia one does better/faster graphics. I have seen messages about people being unable to switch between them in Linux (and shut down the Nvidia adapter to conserve battery life), but I don't know if that issue has been resolved.

---

