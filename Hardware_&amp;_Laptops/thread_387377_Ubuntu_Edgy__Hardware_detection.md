---
title: "Ubuntu Edgy : Hardware detection?"
date: 2007-03-18
forum: Hardware &amp; Laptops
---

### Post by Arma on 2007-03-18
I wanted to have a Linux distro on a flash drive, and installed Ubuntu. That went fine, but automatic hardware detection is not installed when Ubuntu is installed on a harddrive/whatever. Is it possible to allow for automatic hardware detection on Ubuntu Edgy (32bit, that is) during bootup, and change xorg.conf as needed?

Help really appreciated.

---

### Post by kidders on 2007-03-18
Hi there,

Most Linuxes do a quick hardware detection at boot-time, but as you've noticed, they don't tend to actually *do* much with the information they collect (eg xorg.conf rewrites). If getting your X display right is your main concern, you have two main options, afaik.

**Configurationless X**
It's been a while since I've done it, but it is possible to run X without any xorg.conf. What you tend to end up with (and this is the reason I usually don't do it) is a display manager that plays it safe, may not exploit all your hardware to the fullest extent possible, and may on occasion do the wrong thing.

**Multiple xorg.conf files**
Personally, I would prefer this option. Depending on how many computers you wanted your Linux to work on, you could...

[LIST]
[*]Write two or three generic xorg.confs to use as fallbacks, with basic input device configurations, and some specific tweaks targeted at the major display adapter manufacturers.
[*]Write a few more tailored xorg.confs, designed specifically for computers you *know* you want to use. These could make provisions for multibutton mouses, weird keyboards, etc., and would be configured specifically for the graphics cards in use on those machines.
[/LIST]

Now, you could have your system preconfigure X based on some basic knowledge about the system it's running on. You can collect system-specific information in a number of ways...

[LIST]
[*]**uname** might provide all the detail you need ... although probably not.
[*]**lspci** or **lshw** would let you identify computers based their hardware.
[*]**ifconfig** can tell you the ethernet addresses of computers' network cards.
[*]Etc....
[/LIST]

Here's a very oversimplified example of the sort of thing you'd wind up with...

```
#!/bin/bash

ADDR="`cat /sys/class/net/eth1/address`"

# Try to recognise specific computers
if [ "$ADDR" = "11:22:33:44:55:66" ]; then
	XORG="me.conf"
elif [ "$ADDR" = "22:33:44:55:66:77" ]; then
	XORG="lucy.conf"

# Try to identify generic display adapter types
else
	if [ -n "`lspci | grep -i vga | grep Nvidia`" ]; then
		XORG="generic_nvidia.conf"
	elif [ -n "`lspci | grep -i vga | grep ATI`" ]; then
		XORG="generic_ati.conf"
	else
		XORG="dumb_fallback.conf"
	fi
fi
```

By the end of that long list of "if" statements, the value of **$XORG** would tell you which pre-prepared version of xorg.conf you should copy into /etc/X11, before starting X. As long as that particular version of the file is in the right place (and called the right thing) by the time the display manager starts up, you should be able to handle multiple, radically different hardware configurations automagically.

Is that any help?

---

### Post by Arma on 2007-03-18
It was of great help, I'll try it when I'll have some time to work on it. The ideas you gave me are just great, should be a good enough start.

Thanks alot.

---

### Post by kidders on 2007-03-18
Kewl. :-) Let me know if you need help with anything specific.

---

### Post by Arma on 2007-03-22
One question... should I put the file that chooses which config to use instead of the current xorg.conf?

---

### Post by kidders on 2007-03-22
No. If it were me, I would do something like this...

[LIST]
[*]Put a collection of config files (eg xorg.conf.laptop, xorg.conf.james, xorg.conf.nvidia....) somewhere where everyone can see them, like maybe /usr/local/xsetup.
[*]Create a service that "starts" at bootup and "stops" at shutdown. When it starts (which you could do manually with **sudo /etc/init.d/xsetup start**), the correct xorg.conf would be copied to /etc/X11/xorg.conf. When it stops, that file would be replaced with a generic, all-purpose version, so that your graphical server would continue to work despite future failures of your script.
[*]If you wanted to, you could be clever and create a /usr/local/bin/xsetup, that would let people override the automatically chosen xorg.conf.
[/LIST]

Two important things to note:
[LIST]
[*]Modifications to /etc/X11/xorg.conf would no longer be retained. To change X's current settings, you would modify the appropriate source file (eg /usr/local/xsetup/xorg.conf.james in my example) and restart the "xsetup" service. Your changes would then be properly retained across reboots. If you didn't like that, you could simplify things by symlinking (rather than copying) xorg.conf files.
[*]If you're creating files in /usr and /etc/init.d, you need to be _very_ careful with permissions. Always assign the proper file/directory ownerships, and the minimum possible access privileges required to make something work. **Do not** allow anyone but root to modify *anything*.
[/LIST]

---

