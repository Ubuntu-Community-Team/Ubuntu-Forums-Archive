---
title: "Help! The Dreaded Screensaver Flicker!"
date: 2008-09-18
forum: General Help
---

### Post by kestal on 2008-09-18
I am on a Gateway 7422gx 2.2ghz (dual) laptop, with 1gb of ram and RV350 Mobility Radeon 9600 M10.

My secondary computer is a lot older and it works nicely with screensavers (even using just its onboard).

I tried switching to xscreensaver with little luck. Any ideas?

**lshow -C video**

```

       description: VGA compatible controller
       product: RV350 [Mobility Radeon 9600 M10]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: vga_controller bus_master cap_list
       configuration: driver=fglrx_pci latency=255 mingnt=8 module=fglrx
```

I just want Flurry. It flickers pretty badly. in Gnome-screensaver and in Xscreensaver.

---

### Post by kestal on 2008-09-18
I Should also note that even if I turn off Compiz/desktop effects, the screensavers flicker. (the majority of them).

I tried reinstalling my ATI drivers, I tried xscreensaver, I even tried Envy. Nothing seems to work.

Any ideas?

---

### Post by kestal on 2008-09-18
hmm, I take it until ATI 8.9 becomes part of the distro, chances are I am stuck with this... as I see a lot of ATI users are having a problem with this... :(

Is there no way around this?

---

### Post by kestal on 2008-09-19
I take that as a no..

---

### Post by Bennage on 2008-09-21
The only thing I've found that solves the problem is to turn off Compiz.
Right click desktop -> Change Desktop background -> Visual Effects tab -> none.

Annoying, because I rather like all the funky nonsense.

I get the flicker in Movie Player as well.

---

### Post by kestal on 2008-09-22
> **Bennage said:**
> The only thing I've found that solves the problem is to turn off Compiz.
Right click desktop -> Change Desktop background -> Visual Effects tab -> none.

Annoying, because I rather like all the funky nonsense.

I get the flicker in Movie Player as well.

Thanks for the reply..

Even with Compiz off and the effects set to none,  I get the flicker.

With that said, I do not think it displays my ATI card properly, well it displays it but some of the information seems out of order.

Ie) clock: 66MHz, when in the ATI catalyst program it shows a much higher number. 

I tried to install ATI 8.5.# (I forget which numbers at the moment) and that did not change much.

---

### Post by kestal on 2008-09-24
Also... not sure if this helps anyone or not... but I also have Xubuntu 8.04.1 and the screensaver appear normal... this is beginning to be frustrating. Though as it may be, my flavour of Ubuntu is infact Ubuntu. (mainly because of the extra convenient features).

Though, I know, a screensaver flicker isn't the end of the world, but I more-so came back to Ubuntu because of how 'mainstream' it was becoming. :( I have the same ported Screensaver in XP and it works flawlessly. *coughs* (Flurry).

I guess I can just hope for Intrepid to fix this. I guess this is an OpenGL+ATI problem (as all the OpenGL screensavers have this problem).

On the LiveCD of Xubuntu and Ubuntu, there was no flicker. Note to self. when I get a laptop, get one with Nvidia on it :|

---

### Post by Izek on 2008-11-13
I have screensavers flickering too, but I don't wish to turn off compiz effects. *sighs*

---

### Post by paintbalforjesus on 2008-12-04
I have this same problem.  If I turn off compiz then the screensaver works, but compiz is one of the reasons I switched to Ubuntu and the biggest way I got 3 of my friends to switch in just the 2 weeks I've had the operating system.  Does anyone know what video output the screensaver uses?  I've been able to make all other videos work both full screen and in windows.  The only videos that don't work correctly are the screensavers and if I do a hardware test it shows the same type of flickering video it does if I use screensavers

---

### Post by threetimes on 2008-12-04
I have the same problem, I have the 8.54.3 drivers.
I get flickering in:
 - almost all screensavers
 - all 3d games
 - glxgears
 - divx video's
(no flickering in flash, but I belive flash renders using software)

So I use the Deco screensaver, and for games and video's I'll have to turn compiz off.

Tip: get [fusion-icon]("http://tombuntu.com/index.php/2008/03/25/toggle-compiz-with-fusion-icon-in-ubuntu-804/") if you have to do this often.

---

### Post by Usufruct on 2008-12-04
My situation is a little different.  I'm running the 180.06 nVidia beta driver, and I get the screensaver flicker as well, but *only on my main screen*.  The second monitor never flickers at all.

I noticed this a bunch of revisions back, both in Ubuntu and in nVidia.

---

### Post by Vantrax on 2008-12-04
on the ATI side of things try

sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

might work

Unfortunately ATI lags behind a fair bit on the linux support side of things.

---

### Post by paintbalforjesus on 2008-12-04
I forgot to mention I have an ATI graphics card, but I tried the above fix and it didn't help, actually made the problem worse, if I opened the screen saver box it froze my whole system.  I just fixed it but using 

sudo aticonfig --initial
sudo aticonfig --overlay-type=default

I don't really know how to find out all the specs on my system.  I know I'm using an ATI graphics in a Dell Inspiron 6400 with 2 GB RAM and 1.83 GGHz dual core intel processor.  I'm using the ATI/AMD proprietary FGLRX graphics driver for the graphics card.  Can someone tell me how to find out more please?

---

### Post by Vantrax on 2008-12-04
Cant test this solution because I don't have the flicker problem on any of my test machine but i would suggest you run and give the output of fglrxinfo (so i have a better idea what your using) and take a peak at: [http://ubuntuforums.org/showthread.php?t=895182](http://ubuntuforums.org/showthread.php?t=895182)

---

### Post by paintbalforjesus on 2008-12-04
the output from fglrxinfo:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.1.8087 Release

I looked at that other forum, but I can't figure out how to make a folder in the /bin directory, and I don't have a /bin/bash folder.  If I right click in the that folder make folder is blacked out.  I tried mdir in terminal, but I don't know much about terminal, been a while since I used the mdir command.

---

### Post by Vantrax on 2008-12-04
if you dont have /bin/bash you have a few other problems...

to create a folder in there you have to do it in terminal or a root nautilus.

you can do it by going alt-f2 gksudo nautilus to give yourself access in a gui or you can do sudo mkdir /bin/bash

Id suggest you get a friend to help if your not comfortable with terminal, any way of fixing this would end up using it a fair bit.

---

### Post by paintbalforjesus on 2008-12-04
ok, sorry, there was a /bin folder, I meant that I couldn't create the file, but I got the files created now.

But what command is used to run the screen saver, that guide says to modify any menu entries, but I don't know what to edit to do this for the screensaver.

---

### Post by threetimes on 2008-12-05
> **Usufruct said:**
> My situation is a little different.  I'm running the 180.06 nVidia beta driver, and I get the screensaver flicker as well, but *only on my main screen*.  The second monitor never flickers at all.

I noticed this a bunch of revisions back, both in Ubuntu and in nVidia.
I can remember from my windows times that you only have 3d-acceleration on your main screen. Since that is a part of the cause of all this, I understand why you have the problem only on your main screen.

---

