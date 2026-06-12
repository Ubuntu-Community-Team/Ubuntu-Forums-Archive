---
title: "Touchscreen not working"
date: 2006-11-27
forum: Hardware &amp; Laptops
---

### Post by craftybones on 2006-11-27
Hello,

I have an ELO touchscreen connected via a serial port. I am running Edgy currently, and there happens to be an elo driver that I can modprobe. However, I am unable to actually sense any events. I did modify my xorg.conf and this is what it currently looks like:

```


Section "InputDevice"
    Identifier "TouchScreen"
    Driver "elo"
    Option "AlwaysCore"
    Option "Device"     "/dev/ttyS0"
    Option "MinX"          "300"
    Option "MaxX"          "3700"
    Option "MinY"          "300"
    Option "MaxY"          "3700"
    Option "ScreenNumber"  "0"
    Option "ButtonNumber"  "1"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "TouchScreen" "SendCoreEvents"
#       InputDevice     "stylus" "SendCoreEvents"
#       InputDevice     "cursor" "SendCoreEvents"
#       InputDevice     "eraser" "SendCoreEvents"
EndSection



```


Since that didn't work, I looked up some more online and found that elo provided source drivers that you could compile. Downloaded them, followed the instructions, but am ending up with weird make errors. I don't understand why.

The link to the drivers:

[http://www.elotouch.com/files/unrestricted_drivers/Unified_Serial_v2.zip](http://www.elotouch.com/files/unrestricted_drivers/Unified_Serial_v2.zip)

The driver has instructions that you can follow. Upon following and trying make this is what I get:

```


moonwolf@trantor:~/elodrivers-serial_v2.0/source/elocontrol$ sudo make 
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/moonwolf/elodrivers-serial_v2.0/source/elocontrol modules 
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/moonwolf/elodrivers-serial_v2.0/source/elocontrol/main.o
/home/moonwolf/elodrivers-serial_v2.0/source/elocontrol/main.c:53: error: expected ‘)’ before string constant
/home/moonwolf/elodrivers-serial_v2.0/source/elocontrol/main.c:56: error: expected ‘)’ before string constant
make[2]: *** [/home/moonwolf/elodrivers-serial_v2.0/source/elocontrol/main.o] Error 1
make[1]: *** [_module_/home/moonwolf/elodrivers-serial_v2.0/source/elocontrol] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [default] Error 2



```


I don't understand why these errors are being listed. I've tried everything, installing 386 specific kernel header packages etc, but the same error everytime. I can't quite believe that the driver source is flawed. Can someone provide me hints please?

This is sort of urgent, any immediate help will be really appreciated.

Thank you,

craftybones

---

### Post by craftybones on 2006-11-27
Update:

The drivers finally compiled on Dapper(not on Edgy, still not compiling there). Anyway, inspite of getting the drivers to compile, I haven't been able to get my touchscreen to work.

Can anyone please help?

craftybones

---

### Post by jozini on 2007-01-25
How did you finally compile the driver?

thanks

jozini

---

### Post by CheetahCat on 2007-02-13
> I don't understand why these errors are being listed. I've tried everything, installing 386 specific kernel header packages etc, but the same error everytime. I can't quite believe that the driver source is flawed. Can someone provide me hints please?

Hey,

I had the problem myself, try to do the following:

Modify the file main.c (in ...elodrivers-serial_v2.0/source/elocontrol/) to match this. After the modification it compiled just fine and allowed me to load the module into the kernel.

```

...
//MODULE_PARM(debug, "i");
module_param(debug, uint, 0);
MODULE_PARM_DESC (debug, "Debug print for the device");
//MODULE_PARM(elocontrol_major, "i");
module_param(elocontrol_major, uint, 0);
MODULE_PARM_DESC(elocontrol_major, "Major Number for the data device");
...

```

Let me know if it works.

Cheetah

---

