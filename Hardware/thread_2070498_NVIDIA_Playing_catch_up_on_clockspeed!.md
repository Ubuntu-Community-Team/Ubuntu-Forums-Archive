---
title: "NVIDIA Playing catch up on clockspeed!"
date: 2012-10-12
forum: Hardware
---

### Post by themirror178 on 2012-10-12
```
perf=0, nvclock=50, memclock=135, processorclock=101 ; perf=1, nvclock=405,
memclock=324, processorclock=810 ; perf=2, nvclock=405, memclock=1800,
processorclock=810 ; perf=3, nvclock=715, memclock=1800, processorclock=1430
```I'm using gnome 3.5 and when just browsing the web, the graphics card will (as expected) underclock to the lowest performance setting of 50/135/101 MHz. However as soon as I go into overlay mode or anything that requires a bit of gpu grunt, the effects will lag and stutter.

Once the gpu realises I need a higher clock, it's too late and I've already switched windows. The outcome is very rough transitions between windows and applications.

At the same time, I don't want the gpu to be at maximum performance continously.** Is there a way to disable perf0 only** so the minimum clock speed would be 405/324/810 MHz??

Thanks

---

### Post by themirror178 on 2012-10-13
Well I managed to solve this myself while trying to use another method by someone else (which was to put it to performance mode, and underclock the card).

[SIZE=3]***Here's a better solution!***[/SIZE] (only tested with my 'fermi' nvidia card GTX460, but should work for others - use at own risk. MAKE SURE YOU MAKE A BACKUP .ROM OF ORIGINAL FIRMWARE BEFORE FLASHING)

Basically, you follow these two guides to overclock the card, but you change different values. I won't go into detail on how to flash/overclock as these guides are very good.

How to extract and flash BIOS: 
[http://forums.guru3d.com/showthread.php?p=3433513#post3433513](http://forums.guru3d.com/showthread.php?p=3433513#post3433513)

What information to edit with extracted BIOS: 
[http://forums.guru3d.com/showthread.php?t=336117](http://forums.guru3d.com/showthread.php?t=336117)

Scroll down until you see this:

[IMG]http://i914.photobucket.com/albums/ac348/civato/Fermi%20bios%20Guide%203D%20GURU/changingclocks.png[/IMG]

3 => perf0 (basic desktop 2d power saving - I needed to edit these!)
7 => perf1
12 => perf2
15 => perf3 (gaming in 3d - full gpu power)

Read the guide well so you don't screw it up. All I changed was the corresponding Shader/Bumped Shader/Memory Speed **IN THE FIRST "3" ROW NOT THE "15" ROW**!

I doubled the shader to 202 MHz (bumped shader: 539) and memory to 270 MHz.
Also made the minimum fan speed to 0% to be more quiet.

Then flashed the firmware.

Now perf0 reads 101/270/202 MHz and is now smooth!

Hopefully this will help someone, but basically the problem was in the BIOS of the graphics card and not in linux.

---

