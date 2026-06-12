---
title: "Mouse wheel - causes huge lag / renders some 3D games unplayable"
date: 2009-02-11
forum: Hardware
---

### Post by interzoneuk on 2009-02-11
> Specs:-
CPU : Amd64 X2 4600
Motherboard : GA-M55S-S3 (rev. 2.0)
RAM : 2X2GB
GPU : Nvidia Geforce 8500GT (PCI-E)- latest stable driver


This is a really strange one. It is reproducible 100% of the time.

This occurs only in some games- it seems to be the same issue

for example :-

- enemy territory
- legends -> [http://legendsthegame.net/](http://legendsthegame.net/)
- Prey 

Basically in some 3D games when I use the mouse wheel (rapidly move it up and down) the game lags really,really badly for a limited amount of time , the amount of lag seems to depend on the amount of mouse wheel activity...

This occurs in game but - really weirdly - also in the game menus before you have even entered the game !!!!

After mousewheel use the mouse movement will sometimes occur 3-4 seconds aftermoving the mouse rendering the game completely unplayable.

The specs of my machine are o.k (see above) and the games have good speed on my system (until rapid use of the mouse wheel)

I have tried the other following games - just in case there seems something generally wrong with my system - none of these games have the issue.

- Nexuiz
- digital paint2

Games exhibits the same flaw on the following distros:-

Ubuntu 8.10 x86 + amd64
opensuse 11.1

I have tried Prey demo in Windows - this doesn't occur  (was the 1st time i've booted into Windows for ages,,,,,)

Is there some similarities with prey,enemy territory and legends games
- i.e - do they use sdl for mouse control ?

- I have tried other mice and as mentioned the issue doesn't occur in windows (i.e there is not some general hardware issue). 

Has anyone any ideas?

Is there anything I can do to help troubleshoot this issue ?  :confused:

---

### Post by interzoneuk on 2009-02-12
Yey - found a workaround

Now I can play all the best linux games !!

The solution for me was to put

export SDL_VIDEO_X11_DGAMOUSE=0

before playing any of the games I had issues with

They all work fine

Is this an Ubuntu bug ?

---

### Post by interzoneuk on 2009-02-12
Hi.

I have a bug report also.

[https://bugs.launchpad.net/ubuntu/+bug/328204](https://bugs.launchpad.net/ubuntu/+bug/328204)

I haven't marked it as resolved yet (because it isn't) the workaround works but there shouldn't be a workaround....

---

