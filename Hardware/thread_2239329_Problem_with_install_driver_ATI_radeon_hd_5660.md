---
title: "Problem with install driver ATI radeon hd 5660"
date: 2014-08-13
forum: Hardware
---

### Post by iranony on 2014-08-13
hello guys
i have a laptop (hp pavilion dv6 3300se) with hybrid graphics (intel / ati radeon hd 5660) 
after install a fresh ubuntu 14.04.1 i try to install the graphic ati but after all install i got error "low graphic" or "freez after login"
i test all of method on net all of them but didn't work :(
this is some information:
uname -a:```

3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```
glxinfo | grep OpenGL:
```
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Mobile 
OpenGL version string: 2.1 Mesa 10.1.0
OpenGL shading language version string: 1.20
OpenGL extensions:
```
first graphic card:
```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
```
second graphic card:
```
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Madison [Mobility Radeon HD 5650/5750 / 6530M/6550M]
```
and this is the Xorg log file after install driver:
[http://paste2.org/EU5g5Y9O](http://paste2.org/EU5g5Y9O)
how can i solve this issue  ?! plzzz help me ](*,)

---

### Post by Mark Phelps on 2014-08-13
You can't just simply install AMD drivers when you have Intel/AMD graphics.  See the thread for details: [http://ubuntuforums.org/showthread.php?t=1930450&highlight=switchable+graphics]("http://ubuntuforums.org/showthread.php?t=1930450&highlight=switchable+graphics")

---

### Post by QIII on 2014-08-13
Hello!

With a muxless system, 14.04 is designed to handle Intel/AMD hybrids.  A "MUX" is a multiplexer. 

Unfortunately, with an HD 5000 series GPU yours is almost certainly not muxless.  Even the link above is likely to prove fruitless for you.

You might be better off uninstalling the ATI driver and disabling the ATI GPU in your BIOS.

---

### Post by iranony on 2014-08-14
tnx Mark Phelps for you answer but i use that method but not work for me!

dear QIII my graphics system is hybrid MUXed! in windows when i change the graphic cards my monitor get shutdown and turn on again
and if i disable the ati graphic card in my bios setting i cant play game or .... with my intel chip!

---

### Post by QIII on 2014-08-14
Unfortunately Linux is not Windows and does not get the same level of attention from OEMs (Original Equipment Manufacturers).

Because Windows is the largest segment of the consumer computer market, the manufacturers of the computers and the graphics adapters don't give much thought to the 2% of the market represented by Linux.

If you want to game, there is nothing at all wrong with using Windows.  You might dual boot so you can have both.

---

