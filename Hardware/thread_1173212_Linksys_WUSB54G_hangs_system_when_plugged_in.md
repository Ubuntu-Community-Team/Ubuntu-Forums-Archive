---
title: "Linksys WUSB54G hangs system when plugged in"
date: 2009-05-29
forum: Hardware
---

### Post by hamfletta on 2009-05-29
I am trying to get my linksys wireless 54g (version 1) working but having major issues. My problems are -


[LIST]
[*]When i boot with it plugged in the computer hangs
[*]Computer hangs when i run lsusb when it is plugged in
[*]Can not get drivers working.
[/LIST]

I have tried the following so far -

1) Use the serial monkey drivers (as suggested on these forums)

Will not compile - get the messages 

```
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
make[2]: *** No rule to make target `/home/adam/rt73-cvs-2009041204/Module/sanity.o', needed by `/home/adam/rt73-cvs-2009041204/Module/rt73.o'.  Stop.
make[1]: *** [_module_/home/adam/rt73-cvs-2009041204/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
rt73.ko failed to build!
make: *** [module] Error 1

```
I have installed linux headers and GCC. Could not find any futher advice on this so i tried..

The links from the ubuntu forums i tried were broken but i managed to find it from the website directly. I used the legacy ones so do not know if i grabbed the wrong driver?

2) ndiswrapper

I installed and ran 
```
sudo depmod
sudo modprobe ndiswrapper
ndiswrapper -m
sudo ndiswrapper -i <the inf file for the driver>
ndiswrapper -l 
```

I plugged the device in at this point and woot, it showed up on ndiswrapper -l. I rebooted and then i got even more problems.

Running ndiswrapper -l now hangs the computer (!)
still have the hang on lsusb and on boot if the device is connected.

I tried to repeat the ndiswrapper steps but it now hangs when i modprobe and i get a new warning -

```
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

```

I am out of ideas now! My gut feeling is that if i can get the driver compiled then this will solve the problem. So if anyone has any advice i would be very grateful! 

Adam

---

### Post by hamfletta on 2009-06-01
bump

Anyone help? I tried installing windows to test the adapter and it worked straight away. My problem is that i want to install this computer in a place with no ethernet connection so it has to be wireless.

---

