---
title: "Monitor Help"
date: 2011-02-19
forum: Hardware
---

### Post by Jeffreylb94 on 2011-02-19
I have an ibm thinkpad t30 laptop... I have an external vga monitor plugged up to it... I can dual monitor split easy with xp, but is it possible with ubuntu? I went to system, preferences, and clicked monitors... I found an option that says same image in all monitors... I disabled it, and my screen got really glitchey.I had to restart computer and set both monitors to lowest quality... If my monitor is external monitor is not in the lowest resolution both screens will get glitchey and I can't do anything... What do I do? Can I update my graphics card driver with linux? I know how to with xp, but don't know with linux... I did a test, and this is my graphics card "01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]" When I do this, and select to show different things on each monitor, my computer will freeze, and my monitor looks like [http://i1199.photobucket.com/albums/aa475/Jeffreybrown94/Extra/123_0549.jpg](http://i1199.photobucket.com/albums/aa475/Jeffreybrown94/Extra/123_0549.jpg)

---

### Post by jerrrys on 2011-02-21
this may be what your looking for

[http://www.wahlau.org/ubuntu_hoary_thinkpad_t43_and_xorg_dual_head_display](http://www.wahlau.org/ubuntu_hoary_thinkpad_t43_and_xorg_dual_head_display)

---

### Post by grahammechanical on 2011-02-21
If you can make use of the Monitors utility in the Preferences menu then you are using the standard video driver that comes with a standard Ubuntu install. I have a Nvidia card and I use a Nvidia driver that has its own settings utility under the Administration menu.

Go to Administration>Additional Drivers. You may be offered the option to activate a driver produced by the Video card maker. You need an internet connection for this to work and of course there has to be a driver available from the maker.

Regards.

---

### Post by Jeffreylb94 on 2011-02-21
> **jerrrys said:**
> this may be what your looking for

[http://www.wahlau.org/ubuntu_hoary_thinkpad_t43_and_xorg_dual_head_display](http://www.wahlau.org/ubuntu_hoary_thinkpad_t43_and_xorg_dual_head_display)

I know how to dual split, but if my screens go anything above 640x480 then my computer will crash, is there a way to fix that?

---

### Post by jerrrys on 2011-02-21
do you have enough ram? in an HP i can allocate video ram in bios.  are you running compiz? and graham has a point, what about drivers?

---

### Post by Jeffreylb94 on 2011-02-21
Sorry, here are the specs of my laptop. [http://www.thinkwiki.org/wiki/Category:T30](http://www.thinkwiki.org/wiki/Category:T30) I have the same as all specs, except 1.5 Gigs of RAM, and 100 GB hard drive... I checked the drivers, except when it searches for drivers, when it finishes it says "no proprietary drivers are in use on this system"

---

### Post by jerrrys on 2011-02-21
this caught me attention

[ATTACH]184059[/ATTACH]

found that here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=thinkpad+t30+video+drivers&as_qdr=all&sa=Google+Search&lang=en#881]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=thinkpad+t30+video+drivers&as_qdr=all&sa=Google+Search&lang=en#881")

and i bid you farewell till the morning

---

