---
title: "Battery drains when power off"
date: 2017-04-30
forum: Hardware
---

### Post by alejandrofig on 2017-04-30
Hello, I am new to the ubuntu comunity, i install ubuntu 16.10 a few weeks ago (i was coming from windows 10) and i noticed that at night , when i turn off the computer the battery is fully charged but in the morning my battery lost 10 % of its charged. I have an HP pavilion 15 notebook. I search a lot online and found this post: [http://www.hecticgeek.com/2012/09/disabling-wake-on-lan-in-ubuntu-might-save-a-tiny-bit-of-power-on-your-laptop/](http://www.hecticgeek.com/2012/09/disabling-wake-on-lan-in-ubuntu-might-save-a-tiny-bit-of-power-on-your-laptop/) but when i follow step 2 this is what happens:
Cannot get device settings: No such device
Cannot get wake-on-lan settings: No such device
Cannot get message level: No such device
Cannot get link status: No such device
However i continued the tutorial and followed the step 5 and 6, but in the end nothing changed. Can anyone give a hand with this, I really don't know what to do. Thanks!

---

### Post by Autodave on 2017-04-30
The "wake on LAN" will be found in the BIOS: assuming that the machine has that option. The other possibility is that you have a battery going bad. The easiest way to check that is to take the battery out overnight and then put it back in and see if it lost power. If it loses it while out of the machine, obviously the battery is going bad.

---

### Post by alejandrofig on 2017-05-01
Ok, yesterday I took off the battery before going to bed and this morning the battery was 100% charged, at this point I must assume that it has something to do with ubuntu. Do you thing that maybe upgrading to 17.04 would change something?

---

### Post by Autodave on 2017-05-01
I doubt it. Get into your BIOS and make sure that "wake on LAN" is shut off.

To get into the BIOS, as soon as you turn the computer on, look to see what the command to enter the BIOS is. If you are lucky, you will be able to catch it. However, most computers are too fast today for you to see it. If that be the case, you need to start repeatedly and quickly hitting the right key to enter. This could be ESCAPE, F10, F12, or DEL. You can only try one at a time. If the first one doesn't work, power down and back on while trying the next one.

---

### Post by alejandrofig on 2017-05-01
Thanks for the advise, today I entered the Bios and enabled the Legacy support, that i have previously disable when I installed ubuntu. I left the computer off for a couple of hours and it seems that it worked, however it were only 2 hours. I will try it tonight and tell you tomorrow!!

---

### Post by alejandrofig on 2017-05-01
I don't have that option in mi Bios, there is no power management menu. I will let you know tomorrow if enabling legacy did the trick.

---

### Post by Autodave on 2017-05-01
You have to look through everything in the BIOS: it could be anywhere.

---

### Post by Yellow Pasque on 2017-05-01
I also have an HP Pavilion laptop and can confirm that there's no Wake on LAN option in the BIOS. The "Insyde" BIOS this thing has is very, very basic.

> but when i follow step 2 this is what happens:
Cannot get device settings: No such device

Then your device may be named something other than 'eth0'
```
sudo ifconfig -a
```

---

### Post by alejandrofig on 2017-05-02
I still have the same problem, I run the comando 
sudo ifconfig -a and this is the result:
eno1: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether a0:48:1c:20:c6:47  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Loopback locale)
        RX packets 16291  bytes 1049611 (1.0 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 16291  bytes 1049611 (1.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlo1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.134  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::4ad4:25a3:3fb6:2125  prefixlen 64  scopeid 0x20<link>
        ether 3c:77:e6:2c:45:0e  txqueuelen 1000  (Ethernet)
        RX packets 5094  bytes 4371193 (4.3 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 4341  bytes 590560 (590.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

 How do I know which is the device's name? Scuse my ignorance

---

### Post by alejandrofig on 2017-05-02
It seems I solve the problem, after installing ethtool y use this comand to find out the name of my device, in my case was called eno1
sudo lshw -class network

After I wrote: sudo ethtool eno1 | grep Wake-on

and I realise that it said Wake one: g

Then I run : sudo ethtool -s eno1 wol d

And it was fix, I reboot the computer a few times and the wake on lan is always off. Thanks everyone for your help!!

---

