---
title: "ATi problems"
date: 2011-07-27
forum: Hardware
---

### Post by OmegaBrett on 2011-07-27
Ubuntu 11.04 (Narwhal)
ATi Mobility Radeon 9000

I recently switched to Ubuntu from Windows XP after getting the most obnoxious rootkit I'd ever seen.  I installed it with no incident and everything was working splendidly.  I picked up on how to enable full 3D acceleration very quickly and found the terminal to be extremely helpful.

About a week after this, though, I started having problems when I tried to get SuperTuxKart to run on my laptop-- it would crash before the window was even able to load.  I tried loading it through the terminal, rather than using the launcher and this happened:
[I]
Irrlicht Engine version 1.8.0-alpha
Linux 2.6.39-020639rc4-generic #201104191410 SMP Tue Apr 19 15:45:56 UTC 2011 i686
Could not load sprite bank because the file does not exist: #DefaultFont
[FileManager] Data files will be fetched from: '/usr/share/games/supertuxkart/'
[FileManager] Addons files will be stored in '/home/brett/.local/share/supertuxkart/addons'.
[translate] Env var LANGUAGE = 'en_US:en'
[translate] Env var LANGUAGE = 'en_US:en', which corresponds to 'English (United States)'
Adding language fallback en
[IrrDriver] Creating NULL device
Irrlicht Engine version 1.8.0-alpha
Linux 2.6.39-020639rc4-generic #201104191410 SMP Tue Apr 19 15:45:56 UTC 2011 i686
Could not load sprite bank because the file does not exist: #DefaultFont
[IrrDriver] Trying OpenGL rendering.
[IrrDriver] Trying to create device with 32 bits
Segmentation fault[/I]

I posted this error message on the STK forums and all they said is that it was a video driver problem and that they couldn't help.  Well, now nothing that uses any type of 3D rendering works (Assault Cube, Alien Arena, and even Kubrick).

If I type "glxinfo" and "glxgears" into the terminal, I get this:

[I]name of display: :0.0
Segmentation fault[/I]

I checked the Ubuntu 11.04 manual and it told me to consult [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually") if I'm having ATI problems.  Everything was going fine until I got to Step 4 (Install .debs) when it gave me this error:

*Errors were encountered while processing:  xorg-driver-fglrx_8.861-0ubuntu1_i386.deb  fglrx-kernel-source_8.861-0ubuntu1_i386.deb  fglrx-amdcccle*


I've tried uninstalling and re-installing the drivers repeatedly and nothing changes.
I don't know about you, but I find it very bizarre that the display drivers would just suddenly decide to disappear, but it appears as though that's what has happened.

Please help, I've been wrestling with this problem non-stop for about an entire week and I'm about ready to rip out my own hair!  Thanks for the help in advance.

---

### Post by jocko on 2011-07-27
Do **NOT** even try to install the fglrx driver for a radeon 9000. Your card is **NOT** supported by fglrx and has not been since 2006 (and the newest version of fglrx that supported your card will not work in any distro released after 2006).
The open source driver that comes preinstalled in ubuntu, and used by default on supported hardware, is the only driver that works with your card.

---

### Post by OmegaBrett on 2011-07-27
So, how do I get that one back?

---

