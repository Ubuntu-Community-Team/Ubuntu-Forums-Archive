---
title: "M11X R3 - nVidia issues"
date: 2011-05-07
forum: Hardware
---

### Post by Josh1 on 2011-05-07
So I finally managed to get Ubuntu 11.04 installed on my laptop - ended up using PXE as USB didn't want to install...

Anyway, everything is working perfectly. Ubuntu 11.04 picked up wireless, bluetooth, sound, battery life and everything! Fantastic!

Only issue I'm having now is that Ubuntu doesn't want to work when I install the video card drivers and I think I know why. It's because there is an integrated video card in here, as well as the nVidia 540n. This means that when you try and activate it, it could be using the integrated instead of the nVidia card.

There is no way to disable the video card in the BIOS, does anyone know if there is a way to do this within Ubuntu, so only the nVidia 540n works but not the integrated as this is looking like this is the only option.

But yeah.. if anyone is looking to pick up the M11X R3, I'm dualbooting with Windows and I love this laptop! And it works well with ubuntu - it's just this last niggly little error I am having.

Thanks,
Josh

---

### Post by tahnok on 2011-05-14
You should check out acpi_call and the this thread over here [http://ubuntuforums.org/showthread.php?t=1396552](http://ubuntuforums.org/showthread.php?t=1396552)

---

### Post by PhantmKllr on 2011-05-14
> **Josh1 said:**
> So I finally managed to get Ubuntu 11.04 installed on my laptop - ended up using PXE as USB didn't want to install...

Anyway, everything is working perfectly. Ubuntu 11.04 picked up wireless, bluetooth, sound, battery life and everything! Fantastic!

Only issue I'm having now is that Ubuntu doesn't want to work when I install the video card drivers and I think I know why. It's because there is an integrated video card in here, as well as the nVidia 540n. This means that when you try and activate it, it could be using the integrated instead of the nVidia card.

There is no way to disable the video card in the BIOS, does anyone know if there is a way to do this within Ubuntu, so only the nVidia 540n works but not the integrated as this is looking like this is the only option.

But yeah.. if anyone is looking to pick up the M11X R3, I'm dualbooting with Windows and I love this laptop! And it works well with ubuntu - it's just this last niggly little error I am having.

Thanks,
Josh
Consider downloading the drivers from the Nvidia website. This may solve the problem.

---

### Post by meawoppl on 2011-07-10
Same deal here.  I am experimenting with:
[http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html)

There is support in the tubes, but live switching is def. in beta ATM.  I will keep you all posted how this stuff goes.

---

### Post by eltalpa on 2012-01-10
I've found the solution for disabiling the nvidia card:
1) Install the acpi_call kernel module. Open the terminal and launch this commands (pay attention to modify the 5th command according to your kernel version):

```

sudo apt-get install git
git clone https://github.com/mkottman/acpi_call.git
cd acpi_call
make
sudo mv acpi_call.ko /lib/modules/{YOURKERNELVERSION}/kernel/drivers/acpi/acpi_call.ko
sudo depmod -a

```

open the file /etc/modules as root (sudo gedit /etc/modules) create a new row at the bottom and wirte "acpi_call", save and exit. Reboot the machine.
The  kernel module acpi_call should now be loaded. To verify open a terminal and write:
```

lsmod | grep acpi_call

```
If the module was correctly loaded it should be listed.

now the script to turn off/on the card. Open a terminal:
```

cd ~
touch m11xr3.sh
chmod +x m11xr3.sh
gedit m11xr3.sh

```

Paste all this content in the file:
```

#!/bin/sh
# Based on m11xr2hack by George Shearer

if ! lsmod | grep -q acpi_call; then
    echo "Error: acpi_call module not loaded"
    exit
fi

acpi_call () {
    echo "$*" > /proc/acpi/call
    cat /proc/acpi/call
}


case "$1" in
off)
    echo NVOP $(acpi_call "\_SB.PCI0.PEG0.PEGP.NVOP 0 0x100 0x1A {255,255,255,255}")
    echo _PS3 $(acpi_call "\_SB.PCI0.PEG0.PEGP._PS3")
;;
on)
    echo _PS0 $(acpi_call "\_SB.PCI0.PEG0.PEGP._PS0")
;;
*)
    echo "Usage: $0 [on|off]"
;;
esac

```

Save, quit. You are done! From now on to switch off the nvidia card just open a new terminal and do:
```

sudo ./m11xr3.sh off

```

or to power it back on:
```

sudo ./m11xr3.sh on

```

Remember that you cannot use bumblebee/ironhide with the card powered off, nor the external displays since those are connected only to the nvidia card. Cheers :)

---

### Post by Lekensteyn on 2012-01-10
Just to let you know, Bumblebee 3.0 "Tumbleweed" is in development and includes many improvements including better Power Management support which deprecates acpi_call.
The new PM method bbswitch survives suspend as well. Follow us on Twitter [https://twitter.com/Team_Bumblebee](https://twitter.com/Team_Bumblebee) for getting notified on release.

---

### Post by eltalpa on 2012-01-11
If I may ask, how did you guys managed to handle all the different ACPI calls?

A small question: the alienware m11xr3 has the hdmi and displayport connected to the nvidia card, so using optimus prevents the use of an external display. Are there any plans to enable also gpu switching in bumblebee just to use the external display? thanks guys! ;)

---

### Post by Lekensteyn on 2012-01-24
> **eltalpa said:**
> If I may ask, how did you guys managed to handle all the different ACPI calls?

A small question: the alienware m11xr3 has the hdmi and displayport connected to the nvidia card, so using optimus prevents the use of an external display. Are there any plans to enable also gpu switching in bumblebee just to use the external display? thanks guys! ;)
There are two common methods which can be detected on most machines. The only machines that currently do not work are the Lenovo Y470 and Y570 due to Lenovo's retardness. GPU switching is currently unsupported since Optimus machines do not have a hardware mux, but external monitors is something that we'd like to get working. Note that if you are using an external monitor which is wired to the nvidia card, you cannot save power by disabling the card and must set PmMethod=none

---

