---
title: "Remove Ubuntu from Boot Options"
date: 2008-07-12
forum: General Help
---

### Post by Terrizzle on 2008-07-12
I can't seem to remove "Ubuntu" from the boot options on startup.
For example, I see this:

Windows Xp Media Center Edition
Recovery Console
Ubuntu

I've tried using the recovery console option with a boot disk for XP
by using the "Fixboot" and "fixmbr" command. Didn't work.
Also for some reason, When asked to choose which account to use (in order to 
repair the boot sector) I was given the options:
1. I:\MiniNT
2. C:\WINDOWS
(Never seen the 1st option ever before!) what is it?
Obviously I chose the 2nd option.

I tried "Fixboot" and "Fixmbr" and it's still there on every startup.

how do i remove this?

I've already uninstalled Ubuntu and will be trying Xubuntu next.

---

### Post by rraj.be on 2008-07-12
You can do this if you have Ubuntu installed.

In Ubuntu you have a application known as startup manager

Using that you can specify default os to boot.
[Hope this is actually what you want]

You can -->setup timeouts.
        --> Password for your GRUB
         

and many more.

To install startupmanager type this

```
sudo apt-get install startupmanager
```

After installation you could find it here

```
System --> Administartion -->Start up manager
```

If you just want to hide your OS from appearing in boot menu you can do one more thing

type this in terminal
```

sudo gedit /boot/grub/menu.lst
```

In the file comment the following lines

```

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=013564ad-ebe6-44f0-a7f3-6a80cbcd956a ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet
```

That is, change them as following

```

#title		Ubuntu 8.04, kernel 2.6.24-16-generic
#root		(hd0,6)
#kernel		/boot/vmlinuz-2.6.24-16-generic #root=UUID=013564ad-#ebe6-44f0-a7f3-6a80cbcd956a ro quiet splash
#initrd		/boot/initrd.img-2.6.24-16-generic
#quiet
```

This will make your menu without the commented OS entry.

This is applicable to any O/S entry.

---

