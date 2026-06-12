---
title: "Intel 915GM and openGL"
date: 2007-11-12
forum: Hardware &amp; Laptops
---

### Post by ericmitz on 2007-11-12
Hello,

Im writing a primitive 3D checkers game for a computer graphics course I am in, but im having some performance problems.

I have a dell d610 with Intel 915GM graphics card.

Everything was going well when i had only the board drawn, but as soon as i implemented the checker peices, the animation slowed to about 3-4fps. the checker peices are M&M shaped (squashed shperes) so they have a lot of surfaces.

I asked about this on [www.gamedev.net](www.gamedev.net) ([http://ubuntuforums.org/showthread.php?t=159640](http://ubuntuforums.org/showthread.php?t=159640)) and someone mentioned that i do not have hardware acceleration for openGL. I was wondering if someone could help me out.

Everything on my system says i have direct rendering:
```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
.
.
.
.
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 7.0.1

```

Looks fine. right?

Iv also read that the mesa DRI drivers are not really hardware accelerated or something like that
> 
For the DRI, this module is basically a software Mesa renderer.


I know this graphics card isnt really fantastic, but it should be able to render a fairly simple checkers game, shouldn't it? here is a screenshot of the game (dont mind the cubes as checker pieces, i just did that for testing. the spheres made everything unbearably slow).
[img]http://i117.photobucket.com/albums/o67/LostShootingStar/Screenshot-4.png[/img]

any help is appreciated!

---

