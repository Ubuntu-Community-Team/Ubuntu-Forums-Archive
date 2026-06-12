---
title: "Compaq Evo N600c takes 3 minutes to boot up ubuntu 7.10"
date: 2008-08-24
forum: Hardware
---

### Post by sandman887 on 2008-08-24
Anybody know why? 

It's a Pentium III 1.06 Ghz
512 MB RAM

After it boots, though, it runs great, no problems. But it just takes 3 minutes to boot, and during this time, the screen is entirely black. I had xubuntu 7.10 installed in it before, and it never did that, and in fact, loaded quite fast with 128 MB of RAM before I upgraded to 512 and installed ubuntu. 

It's not a life or death matter, I just would like to know why. 

If anybody has any ideas, I'd appreciate it.

Thanks.

---

### Post by prshah on 2008-08-24
> **sandman887 said:**
> 
After it boots, though, it runs great, no problems. But it just takes 3 minutes to boot, and during this time, the screen is entirely black. 

While ubuntu is booting up (black screen) press ctrl+alt+f8; the screen will be initially blank, but will start filling up with information soon; can you notice if there is any particular statement where a pause occurs (over 8~10 seconds will constitute a pause)? If you find such a statement, post back for details and/or more troubleshooting.

You can also install bootchart, Open a terminal (Applications-Accessories-Terminal) and give the command```
sudo apt-get install bootchart
``` This will produce graphical (png) logs of how much time each process during bootup is taking; the logs are saved as image files (png) in /var/log/bootchart.

Viewing/Posting a recent bootchart may give you/us a clue as to where the holdup is.

3 minutes is too long on these specs.

---

### Post by libra1780 on 2008-08-24
got this too once on a laptop. if i left it there, it lacked around for minutes, but if i pressed CTRL+ALT+F1 ath the beginning of boot process, it took seconds to boot.
in my case it was a video card driver issue..
i fixed it setting up framebuffer driver for the console.
once installed, the bootup screen worked as well

seems like you have the same prob.:lolflag:

---

### Post by sandman887 on 2008-08-25
I tried what you suggested with ctrl-alt-f8, but that did nothing. So I installed bootchart, and then restarted, and that got the chart of my bootup. 

Here is the pic of it:
[IMG]http://i100.photobucket.com/albums/m19/brave_man/aroundhome/laptop/gutsy-20080825-1.png[/IMG]

libra1780, that worked, and my laptop booted up at almost normal speed, but do I have to push ctrl-alt-f1 every time I restart, or just once?

---

### Post by sandman887 on 2008-08-28
So what clues does this give you?

Here is a link to the screenshot:
[http://i100.photobucket.com/albums/m19/brave_man/aroundhome/laptop/gutsy-20080825-1.png](http://i100.photobucket.com/albums/m19/brave_man/aroundhome/laptop/gutsy-20080825-1.png)

Thanks.

---

### Post by prshah on 2008-08-29
> **sandman887 said:**
> 
libra1780, that worked, and my laptop booted up at almost normal speed, but do I have to push ctrl-alt-f1 every time I restart, or just once?

You can turn off the splash screen permanently; Press Alt+F2, then give the command ```
gksudo gedit /boot/grub/menu.lst
``` Look for the line that corresponds to what you normally select during bootup; typically> ```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
```, and following this, you will find a line starting with "kernel"; scroll to the end of the line, and remove the word(s) "quiet splash". Save, exit, and run the terminal command```
sudo update-grub
``` Now you should have the text screen from the next bootup onwards.

> **sandman887 said:**
> So what clues does this give you?

Here is a link to the screenshot:
[http://i100.photobucket.com/albums/m19/brave_man/aroundhome/laptop/gutsy-20080825-1.png](http://i100.photobucket.com/albums/m19/brave_man/aroundhome/laptop/gutsy-20080825-1.png)


Unfortunately the screenshot is unreadable; you should post the bootchart created png file instead.

---

