---
title: "Laptop screen problems"
date: 2008-10-25
forum: Hardware
---

### Post by d34th on 2008-10-25
I'm trying to use ubuntu 8.04 on an Asus X50gl with a 

But I have some problems with the screen, ubuntu sets the resolution to 800x600 instead of 1280x800

The I try to install the nvidia drivers (ubuntu detects that I need restricted drivers for a nvidia card (windows says it is a nvidia MCP79MVL))

When drivers are installed, when I start the system (when the nvidia logo should appear), the screen goes completely black, as it turns off

Any idea?

---

### Post by teaker1s on 2008-10-26
maybe envy needed to install binary drivers direct from nvidia. to restore your display at grub boot safe mode and 
```
sudo dpkg-reconfigure xserver-xorg
```

should this not work then 
```
sudo nano /etc/X11/xorg.conf
```
change driver to nv or failing that vesa

```
sudo reboot
```

---

### Post by d34th on 2008-10-27
I've managet to get display working properly.

I installed ubuntu 8.10(rc) and the installed the nvidia drivers that provided me the restricted driver manager.

I think nvidia binary drivers should work for 8.04.
I've noticed that the X config is much shorter than I was used to (maybe X server didn't detect the display)

---

