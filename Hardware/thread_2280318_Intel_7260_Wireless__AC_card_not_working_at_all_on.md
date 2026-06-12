---
title: "Intel 7260 Wireless  AC card not working at all on Ubuntu 15.04"
date: 2015-05-29
forum: Hardware
---

### Post by Rakesh_Das on 2015-05-29
[COLOR=#111111][FONT=Ubuntu]After a fresh install of Ubuntu 15.04, my wifi will not work. I have the Intel 7260 Wireless AC card and my system is saying that the wifi is disabled due to the hardware switch, but I can't turn on the wifi via the keyboard either. M y laptop is the HP ENVY 4-1130us 

I have tried the solution outlined [here]("http://askubuntu.com/questions/331667/no-wireless-for-intel-corporation-7260-version-63").

But, when I run ```
make defconfig-iwlwifi 
```and ```
make
```, I get the errors:
```

Error 2
Makefile:1394: recipe for target '_module_/home/rakesh/intelwifi/backports-3.15-rc1-1' failed
make[4]: *** [_module_/home/rakesh/intelwifi/backports-3.15-rc1-1] Error 2
Makefile.build:6: recipe for target 'modules' failed
make[3]: *** [modules] Error 2
Makefile.real:83: recipe for target 'modules' failed
make[2]: *** [modules] Error 2
Makefile:40: recipe for target 'modules' failed
make[1]: *** [modules] Error 2
Makefile:30: recipe for target 'default' failed
make: *** [default] Error 2
```[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]

After running sudo dmidecode | grep Version, I got:

```
Version: F.13
Version: 0887110000305A00000320100
Version: 72.43
Version: Chassis Version
SBDS Version: 1
Version: Intel(R) Core(TM) i5-3317U CPU @ 1.70GHz
```


I also ran the wireless-info script and attached a wireless-info.txt below.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I'm guessing that the build isn't executing correctly, is there anything I can do to remedy this?
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]
[/FONT][/COLOR][ATTACH]262294[/ATTACH]

---

### Post by jeremy31 on 2015-05-30
You don't need to build any module as the problem is that the wifi says that it is disabled by hardware switch.  If you have a dual boot system, I would see if it can be enabled in Windows otherwise you could try
```
sudo modprobe -r hp_wmi
``````
sudo rfkill unblock all
``` and see if the ```
rfkill list all
``` still shows wifi as hard blocked.  You might get the hard block to clear by entering BIOS and resetting it to defaults

I just read your comment on askubuntu.  Put the original wifi card in and run the wireless script again and post results.  HP could be using a different pin assignment on the wifi cards so that only cards made for HP will work in their laptops

---

### Post by Rakesh_Das on 2015-05-30
Thanks! After running the commands and resetting the BIOS afterwards did the trick!

---

