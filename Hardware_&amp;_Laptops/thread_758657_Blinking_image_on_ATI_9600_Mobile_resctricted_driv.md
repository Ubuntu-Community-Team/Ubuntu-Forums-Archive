---
title: "Blinking image on ATI 9600 Mobile resctricted drivers"
date: 2008-04-18
forum: Hardware &amp; Laptops
---

### Post by swoop_ubu on 2008-04-18
I have a strange problem. I'm using ubuntu 8.04 beta on Gateway notebook with ATI Mobility Radeon 9600. Restricted driver just works flawlessly.

The only problem is with games. When playing a game the screen blinks like once per second. Screen goes black for a split of a second and back to normal. The game play is unaffected and it seems like images are send to the card fine just hardware-wise it blinks.

Does anyone encounter this. Any known remedy?
Thanks in advance.

Cheers
ubu

---

### Post by pseudo-random on 2008-04-18
I've had snags with my ATI card also but found some workarounds.
Can you give the output of these commands:
```
xvinfo
```
```
fglrxinfo
```
```
glxgears
``` 
Also post your xorg.conf from /etc/X11/xorg.conf

Have you tried disabling compiz and replacing it with metacity?
```
metacity --replace
```

---

### Post by swoop_ubu on 2008-04-18
pseudo-random:

that was lightning-fast. i'll supply you the info as i'll get home.
thanks, mate.

btw, i think i disabled the desktop effects, but nothing changed.
i'll do the '-- replace' thing.

cheers

---

### Post by swoop_ubu on 2008-04-24
pseudo-random

here comes the data. can you conclude something?

```
fun@funtop:~$ xvinfo
X-Video Extension version 2.2
screen #0
 no adaptors present
```
```
fun@funtop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON 9600/9700 Series
OpenGL version string: 2.1.7412 Release
```
```
fun@funtop:~$ glxgears
10391 frames in 5.0 seconds = 2078.078 FPS
11115 frames in 5.0 seconds = 2222.967 FPS
11317 frames in 5.0 seconds = 2263.323 FPS
11343 frames in 5.0 seconds = 2268.528 FPS
11294 frames in 5.0 seconds = 2258.671 FPS
```
btw, engaging metacity helped. so no blinking.

thanks in advance

ubu

---

