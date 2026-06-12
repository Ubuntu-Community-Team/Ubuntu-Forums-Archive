---
title: "asus g60jx backlight issue"
date: 2010-06-24
forum: Hardware
---

### Post by trc on 2010-06-24
I recently bought an ASUS G60JX gaming laptop and am dual booting with Windows 7, everything works pretty well on Ubuntu 10.04 64 bit except I can't figure out a way to turn off the backlit keyboard lighting, the shortcuts work for turning off wireless and raising and lowering sound etc... I just can't find out how to turn off the lighting for the keyboard, which I dont really want on because it wastes power. It also flickers when I go to suspend mode, which makes it pretty unusable at night due to the light show lol

Any suggestions would be much appreciated. ^_^

---

### Post by trc on 2010-06-26
Hey guys, just thought I'd let you all know I found the solution to this problem in this topic here. 

[http://forum.notebookreview.com/linux-compatibility-software/451594-asus-rog-g73-ubuntu-2.html](http://forum.notebookreview.com/linux-compatibility-software/451594-asus-rog-g73-ubuntu-2.html)

---

### Post by gecka on 2010-08-05
Try the attached zip (for lucid only, other versions need to patch asus-laptop module) :

- uncompress
- cd to extracted directory
- run 

```
sudo ./install.sh
sudo service acpid restart
```

---

### Post by gecka on 2010-08-05
Here is an updated version, with an uninstall.sh script so you can switch to [this scripts that support libnotify OSD]("http://ubuntuforums.org/showthread.php?p=9683440#post9683440")
[B]
Note:[/B] For Lucid only and ASUS MODEL G51J (MB VER.: G60JX - G51JX-SZ050V)

---

### Post by Toasticuss on 2010-10-29
> **gecka said:**
> Try the attached zip (for lucid only, other versions need to patch asus-laptop module) :

- uncompress
- cd to extracted directory
- run 

```
sudo ./install.sh
sudo service acpid restart
```

Works perfect for Ubuntu 10.10 (Maverick) 

Thanks =)

---

