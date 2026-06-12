---
title: "Logitech G710+ M# and G# keys"
date: 2015-03-14
forum: Hardware
---

### Post by sienile on 2015-03-14
I've been trying for a few weeks to get my macro function keys on my new Logitech G710+ mechanical gaming keyboard to be recognized in Ubuntu 14.04. I've verified that they do work in Windows, so it's not a hardware malfunction. Currently the G# keys report as the number keys instead of their own keycodes, but the M# keys do not report at all.

I've tried to install a driver made by Wattos ([https://github.com/Wattos/logitech-g710-linux-driver](https://github.com/Wattos/logitech-g710-linux-driver)) which several people have reported success with. I keep getting errors when trying to install the kernel modules, but the modules appear to be installed.

```
joe@U14:~/Hardware/G710/logitech-g710-linux-driver-master/src/kernel$ sudo make install[sudo] password for joe: 


make -C /lib/modules/3.13.0-46-generic/build M=/home/joe/Hardware/G710/logitech-g710-linux-driver-master/src/kernel modules_install
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-46-generic'
  INSTALL /home/joe/Hardware/G710/logitech-g710-linux-driver-master/src/kernel/hid-lg-g710-plus.ko
Can't read private key
  DEPMOD  3.13.0-46-generic
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-46-generic'


joe@U14:~/Hardware/G710/logitech-g710-linux-driver-master/src/kernel$ 
```


```
joe@U14:~$ grep -r g710 /lib/modules

Binary file /lib/modules/3.13.0-44-generic/modules.alias.bin matches
Binary file /lib/modules/3.13.0-44-generic/extra/hid-lg-g710-plus.ko matches
Binary file /lib/modules/3.13.0-44-generic/modules.dep.bin matches
/lib/modules/3.13.0-44-generic/modules.alias:alias hid:b0003g*v0000046Dp0000C24D hid_lg_g710_plus
/lib/modules/3.13.0-44-generic/modules.dep:extra/hid-lg-g710-plus.ko: kernel/drivers/hid/hid.ko
Binary file /lib/modules/3.13.0-46-generic/kernel/drivers/hid/hid-lg-g710-plus.ko matches
Binary file /lib/modules/3.13.0-46-generic/modules.alias.bin matches
Binary file /lib/modules/3.13.0-46-generic/extra/hid-lg-g710-plus.ko matches
Binary file /lib/modules/3.13.0-46-generic/modules.dep.bin matches
/lib/modules/3.13.0-46-generic/modules.alias:alias hid:b0003g*v0000046Dp0000C24D hid_lg_g710_plus
/lib/modules/3.13.0-46-generic/modules.dep:kernel/drivers/hid/hid-lg-g710-plus.ko: kernel/drivers/hid/hid.ko
```

But "lsmod | grep g710" comes up empty and not many HID devices show up either. (There should be more since I'm running a G600 gaming mouse that shows as 2 devices also.)

```
joe@U14:~$ lsmod | grep hid

mac_hid                13205  0 
hid_generic            12548  0 
usbhid                 52659  0 
hid                   106148  2 hid_generic,usbhid

```

I'm at a loss at what to do next. Is the private key error preventing the drivers from being properly installed? If so, how do I resolve that issue?
This is my first time going this deep into linux hardware programming, so newb-friendly answers would be much appreciated. ;)

---

### Post by Stephen_Damm on 2015-07-03
I was able to make this work on Ubuntu 14.04 somewhat.

First following your step is fine.
make
sudo make install
sudo depmod -a

You can ignore the private key error.

Now the step you missed is unplugging and replugging the g710+.  By doing this lsmod | grep "hid" shows "hid_lg_g710_plus".

Every time you reboot it will boot up as a generic hid device.  Once booted if you unplug and replug it will show up as the g710_plus.

Now the battle begins.  The g1-6 keys show up as things like mute, touchpad on/off.  They seem unbindable in most apps (ie. I wanted some IDE hot keys set on the G1-6 keys, seems impossible).

---

### Post by timfinley on 2016-05-12
So I kind of struggled with this one for a while.

I know I'm digging up an old post, but I thought I would add to it since I figured it out.

--------On to it then------

After you have installed, you will run the command

```
xmodmap misc/.Xmodmap
```

Cool, but those aren't the keys you want, right?

use your favorite code editor for the following. Mine is vi

```
vi misc/.Xmodmap
```

Change the keys to the ones you want. You will see something that looks like this:

```

keycode 191 = XF86Launch0
keycode 192 = XF86Launch1
keycode 193 = XF86Launch2
keycode 194 = XF86Launch3
keycode 195 = XF86Launch4
keycode 196 = XF86Launch5
keycode 197 = XF86Launch6
keycode 198 = XF86Launch7
keycode 199 = XF86Launch8
keycode 200 = XF86Launch9

```

You just need to change the "XF86Launch" commands to whatever you want. For instance, I used "keycode 191 = less". Now when I press my M1 button it produces the less than (<) symbol. Pretty neat, right?

Now run: 

```
xmodmap misc/.Xmodmap
```

You can find a list of keysyms here:
[http://wiki.linuxquestions.org/wiki/List_of_Keysyms_Recognised_by_Xmodmap](http://wiki.linuxquestions.org/wiki/List_of_Keysyms_Recognised_by_Xmodmap)

Now to make the keys work on startup, 

1. mash the Super Key
2. type "startup"
3. click Startup Applications
4. click "Add"
5. in the name field, give the command a unique name. I used "Map G710 Keys"
6. in the command field type "xmodmap misc/.Xmodmap"
7. click "Add"

and you're done. Now, I realize there is a quicker way to do this, but now you might have a better grasp on what is going on.

I hope this helps some lost user in the future.

---

