---
title: "How to use Laptop mode tools?"
date: 2009-07-20
forum: Hardware
---

### Post by pointyblue on 2009-07-20
Hi,

I'm on a netbook running Ubuntu 9.04. In Synaptic I can see that Laptop mode tools is installed but when I run

```
cat /proc/sys/vm/laptop_mode
```

the returned value is 0 which indicates that Laptop mode tools is not enabled.

Any idea how to enable Laptop mode tools + how to configure it? (Is there a gui?)

Could really use some extra battery life here! ;)

---

### Post by bryonak on 2009-07-20
I haven't checked in Jaunty, but in previous versions laptop mode has been disabled by default because of some bugs on some specific hardware.

First press Alt+F2 and type```
gksudo gedit /etc/laptop-mode/laptop-mode.conf
```
Enter your password, scroll down to ENABLE_LAPTOP_MODE_ON_BATTERY=0 and set it to 1

Then open a terminal and run```
sudo laptop_mode
```once on AC and once on battery. Any difference?

---

### Post by pointyblue on 2009-07-22
Thanks for helping out but I've decided to let it rest for now.

It's not worth it if the system becomes unstable. Was just curious as it's a part of the default install. Pretty weird if it's buggy...

---

### Post by bryonak on 2009-07-23
Hehe, I didn't mean to come over like it's dangerous... for most hardware, it should work flawlessly.
I've activated it on 4 laptops (Lenovo, HP, Asus, Apple) myself, none of which have shown any sign of problems (but a few watts less power usage).

They turned it off by default because in some circumstances on certain hardware, there might be the possibility of problems, yet we want all users to have a stable experience, so to say ;)
If anyone can specify which hardware exactly throws errors, please speak up!

---

### Post by quoob on 2009-08-16
Hi.  I've been struggling with laptop mode and have hit upon something that seems apropos here.  It appears that laptop mode is enabled/disabled in two places: /etc/default/acpi-support and /etc/laptop-mode/laptop-mode.conf.

The first is checked by /etc/init.d/laptop-mode, which refuses to start the laptop mode service at all (or to stop it!) if the env variable ENABLE_LAPTOP_MODE is set to "false", which /etc/default/acpi-support does by default.

The second file is presumably checked by the laptop-mode code itself, though I haven't verified this.

I was, by the way, clued into this by a comment in the man page for laptop_mode: "Note that this will not  do  anything
                 if the laptop-mode service has not been started!"

(The comment referred to the "auto" command, but I was looking for any hint to get me unstuck.)

Enabling laptop mode in /etc/default/acpi-support and restarting the laptop_mode service [sudo /etc/init.d/laptop-mode restart] made it work, but I haven't run with it enabled long enough to be confident I won't run into the mysterious hardware-specific issues (whatever they are).

Hope this helps ...

---

### Post by wily6 on 2009-09-12
reading off of laptop mode tools website they say the ubuntu version isn't enabled.. 

"If you want to use the latest version of laptop mode tools, you can use the [Debian packages]("http://samwel.tk/laptop_mode/packages/debian"), they are compatible enough to work out-of-the-box on Ubuntu. In fact, I would definitely advise using these packages -- the Ubuntu packages are crippled so that some options don't work"

so i just went to synaptics package manager and searched for laptop mode tools and uninstalled it completely... and then went to 

[http://samwel.tk/laptop_mode/packages/debian](http://samwel.tk/laptop_mode/packages/debian)

and downloaded the latest version... and installed it by just double clicking it / opening it with whatever default program it suggested

hope that helps

---

