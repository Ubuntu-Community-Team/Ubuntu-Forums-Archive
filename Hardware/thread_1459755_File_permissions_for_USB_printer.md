---
title: "File permissions for USB printer"
date: 2010-04-21
forum: Hardware
---

### Post by paulsp on 2010-04-21
Hi there,

I have EXACTLY the same problem as this person:
[http://ubuntuforums.org/showthread.php?t=30262](http://ubuntuforums.org/showthread.php?t=30262)

That is, I need to change the permissions of /dev/usb/lp0 in order for my printer to work in my situation. However, I need to chmod at every boot. It would be more convenient to change this udev permissions file... however, I can not find this! It appears that in newer Ubuntu versions this path changed. Anybody knows where I can change the automatic file permissions of /dev/usb/lp0? 

Thanks!
Paul

---

### Post by paulsp on 2010-05-13
Hello,

I am still very stuck with this problem. The printer is automatically mounted with 660 permissions, and I can not change this to something more permissive. I have a temporary solution running a rc.local script at startup with the right permissions, but even during operations the permissions change back to 660. Anybody any idea how to change this?? 

Thank,
Paul

---

### Post by sisco311 on 2010-05-13
Did you add your user to the lp group?
```
sudo gpasswd -a **username** lp
```
Where **username** is your login name. 

NOTE: After adding your user to the group you need to log out and log back in.

---

### Post by paulsp on 2010-05-13
This sounds VERY logical and SHOULD work. But it does NOT :-( 

After login, still the same. Any other ideas? Any idea where I can set a different permission whenever the printer is mounted?

---

### Post by IcarusR on 2010-05-13
Don't know what version of ubuntu you have but in mine 8.10 the udev rules are in /etc/udev/rules.d there is a readme with expanation.

---

### Post by sisco311 on 2010-05-13
Yep, you have to write a udev rule.


Open the file:
```
gksu gedit /etc/udev/rules.d/99-printer.rules
```

Add this line to it:
```
KERNEL=="lp[0-9]", SUBSYSTEM=="usb", GROUP="lp", MODE="0666"
```

Save the file and exit. Run:
```
sudo udevadm control restart
```

Unplug the printer and plug it back in.

---

### Post by paulsp on 2010-05-13
Wow, excellent! What a knowledge... I will be trying this out and will report back later!

Regards,
Paul

---

