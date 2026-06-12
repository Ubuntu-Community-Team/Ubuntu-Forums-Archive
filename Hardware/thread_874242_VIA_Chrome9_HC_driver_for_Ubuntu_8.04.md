---
title: "VIA Chrome9 HC driver for Ubuntu 8.04"
date: 2008-07-29
forum: Hardware
---

### Post by DigitalJedi on 2008-07-29
I just downloaded Ubuntu through wubi, and it works fine, except the screen is fuzzy and has lines through it. I have been told that the problem is with my video card not being supported, or I need a driver for it. Do you know of any Drivers for this gfx card? It is integrated btw. I am on windows right now because it is hard to see anything, when I am on Ubuntu. Also could this be fixed by me bring the screen resolution down? Because right now it is around 1260 x something I forget, thanx in advance.

---

### Post by overdrank on 2008-07-29
> **DigitalJedi said:**
> I just downloaded Ubuntu through wubi, and it works fine, except the screen is fuzzy and has lines through it. I have been told that the problem is with my video card not being supported, or I need a driver for it. Do you know of any Drivers for this gfx card? It is integrated btw. I am on windows right now because it is hard to see anything, when I am on Ubuntu. Also could this be fixed by me bring the screen resolution down? Because right now it is around 1260 x something I forget, thanx in advance.

Hi and welcome, Yes you may be able to adjust the resolution to help. As for a Driver you may look here 
[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)
You may also try and use the alt, F2 keys and enter this command
 ```
gksu displayconfig-gtk
``` there you can adjust your driver and resolution.

---

### Post by ottoshmidt on 2008-10-18
I was having exactly the same problem and solved it the following way:

download an appropriate driver for Ubuntu 8.04 (have know idea yet if it will work for 8.10) from here: [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)

it was chrome9.83-242-u804(18Jun08) (3.8M)[B]

unpack it and Run "vinstall" file in terminal and reboot.[/B]

the visibility was awful but wasn't impossible to do.

---

### Post by tzotzolyno on 2009-04-10
Hello. I'm new in linux world, even if I've instaled Ubuntu since 7.10 vers (2007). Please, tell me if you recomend this driver instead of the openchorme one.

(I use Linux Mint 5 on a Amilo Li 1705 notebook with this kind of via cipset).

Thank you in advance an sorry for my bad english.

L.E. It works: Here is the complete solution for this problem, especially if you own a Fujitsu-Siemens Amilo Li 1705. [http://ubuntuforums.org/showthread.php?t=1124185]("http://ubuntuforums.org/showthread.php?t=1124185")

Have a nice day!

---

### Post by ricardisimo on 2009-04-27
Hopefully this is just the thread I need. Maybe someone can tell me yes or no.

I'm on Jaunty now. I have a VIA Chrome 9 HC VGA compatible controller, running on a Biostar P4M90-M4 Motherboard. In the past Ubuntu had to use the vesa driver in order to get anything meaningful on screen. So I'm happy that Openchrome is working now.

However, no desktop effects are possible, and when I switch users, then switch back, the screen is distorted with vertical lines. The second user's graphics stay pristine unless and until a third user logs in... It would appear, then, that only the most recent user retains full use of the graphics card, or some such problem.

Is this a configuration problem with openchrome? Should I give the via driver a try? Thanks.

---

### Post by dhamith on 2010-07-18
I've tried VIA drivers, on this motherboard with Ubuntu 10.04 but no luck....

---

