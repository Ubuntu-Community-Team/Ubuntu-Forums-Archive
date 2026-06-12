---
title: "USB mouse stops respoding"
date: 2008-06-01
forum: Hardware
---

### Post by randomAccess on 2008-06-01
Sometimes usb mouse just stops responding and I have to manually plug/unplug it from the usb port and then it works again. Somewhere I read that this may be up to Firefox (I use ubuntu 8.04 3.05b version). Is there a solution to this problem? It's annoying. :confused:

---

### Post by lisati on 2008-06-01
I had a similar problem on my laptop (Ubuntu 7.04) with the USB mouse and USB keyboard stopping after a few minutes. I don't know if this will work with 8.04 but this is the workaround I used:

From the Terminal (click on Accessories, then terminal) type:
```

sudo gedit /boot/grub/menu.lst

```
Scroll down to where it reads:
> 
# defoptions=quiet splash

Change it to read:
```

# defoptions=quiet splash acpi=force irqpoll

```
Save the file and exit from the editor, and then type at the terminal:
```

sudo update-grub

```
and then restart the computer.
Don't panic if you get asked for your password, this is normal. Don't worry if your password doesn't show when you're typing it, it will still be recognized.

Hope this helps.

---

### Post by randomAccess on 2008-06-01
Hm. I'll give it a try and after a week or so I'll let you know if this helped :)

---

