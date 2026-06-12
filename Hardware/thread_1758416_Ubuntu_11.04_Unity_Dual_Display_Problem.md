---
title: "Ubuntu 11.04 Unity Dual Display Problem"
date: 2011-05-14
forum: Hardware
---

### Post by halfstep007 on 2011-05-14
Hi, I upgraded my ubuntu 10.10 to 11.04, now that my interface looks completely different, and its unity, my dual display stops working. 

The 2 monitors are still displayed, but the graphic is really slow, the wallpapers is unable to be displayed either, all i see is lines of incomplete pictures. when i open up a window or application, I have to mouse over the application just see partial display. 

The problem goes away when I use Ubuntu classic without visual effects.

* I use a laptop with external Acer monitor 1680 * 1050. My toshiba laptop is quite old and has a intel onboard graphic card

---

### Post by ghostborg on 2011-05-14
Check this blog out as it has some useful tips. For me the bottom Entry about ATI graphics helped with choppy video and overall slowness. I also enabled Tear Free in the ATI Catalyst control center.

[http://ubuntu4beginners.blogspot.com/]("http://ubuntu4beginners.blogspot.com/")

---

### Post by PhantmKllr on 2011-05-14
> **halfstep007 said:**
> Hi, I upgraded my ubuntu 10.10 to 11.04, now that my interface looks completely different, and its unity, my dual display stops working. 

The 2 monitors are still displayed, but the graphic is really slow, the wallpapers is unable to be displayed either, all i see is lines of incomplete pictures. when i open up a window or application, I have to mouse over the application just see partial display. 

The problem goes away when I use Ubuntu classic without visual effects.

* I use a laptop with external Acer monitor 1680 * 1050. My toshiba laptop is quite old and has a intel onboard graphic card
When you were using 10.10, were you using Compiz? 11.04 now requires Compiz, and your graphics card may not be able to take it that well.

---

### Post by halfstep007 on 2011-05-14
thanks for the replies guys, this is what my screen looks like even after i installed the advanced compiz

[IMG]http://i307.photobucket.com/albums/nn284/thedayidie/Screenshot-1.png[/IMG]

---

### Post by halfstep007 on 2011-05-14
> **PhantmKllr said:**
> When you were using 10.10, were you using Compiz? 11.04 now requires Compiz, and your graphics card may not be able to take it that well.

I am not that familiar with linux yet, so i don't know if i was using compiz in 10.10, all i know was i didn't have any problems with dual display with 10.10 under classic no effect option (never tried the other options). 

My laptop doesn't lag either using unity in single display, but it lags like **** with the dual monitor, so i assume its something with the settings.

---

### Post by PhantmKllr on 2011-05-14
You may be able to fix your problem by using the Compiz-Config Settings Manager (search for it in the software center).

Also, you can still use the classic desktop. Just choose "Ubuntu Classic" at the login prompt (@ the bottom of the screen). If the problem persists, then we know that it's a problem with 11.04. If it doesn't, we know that it's Compiz's fault.

BTW: I'm assuming that you know what Compiz is.

---

### Post by halfstep007 on 2011-05-14
> **PhantmKllr said:**
> You may be able to fix your problem by using the Compiz-Config Settings Manager (search for it in the software center).

Also, you can still use the classic desktop. Just choose "Ubuntu Classic" at the login prompt (@ the bottom of the screen). If the problem persists, then we know that it's a problem with 11.04. If it doesn't, we know that it's Compiz's fault.

BTW: I'm assuming that you know what Compiz is.

yeah i know what you are referring to when you mention compiz, I was able to use the ccsm, but i haven't fiddle with it that much, I can use classic ubuntu with dual display, so i am just going to stick with this. I wanted linux for its simplicity and speed. this is better for me anyways. 

thanks for the help

---

### Post by PhantmKllr on 2011-05-14
Alright... So just for future reference, the problem was likely caused by your graphics card's inability to run Compiz very well.

Glad that everything worked out for you. However, you may want to look into a graphics card upgrade (or a new computer), for the classic desktop will likely be excluded from the next version of Ubuntu (11.10).

---

### Post by reya276 on 2011-05-17
I'm also having issues with my Laptop display but of a different kind. My Ubuntu 11.04 is a new install and when I try to configure my extra display as a dual monitor setup everything works fine until I turn off my laptop. As soon as I boot it up NO dual monitor no Laptop LCD, the only thing I can do is go into CLI which then shows on both displays. Now I tried to edit the /home/<username>/.config/monitors.xml but it does nothing. Why can't they make this thing behave just like 10.04 and even 10.10 where you just ran a command like and BAM your display was totally reset. WTF happen to that. I understand that we need progress BUT keep it simple stupid works just fine. Why are we all of a sudden trying to go the Windows route?:confused:

---

### Post by reya276 on 2011-05-17
> **reya276 said:**
> I'm also having issues with my Laptop display but of a different kind. My Ubuntu 11.04 is a new install and when I try to configure my extra display as a dual monitor setup everything works fine until I turn off my laptop. As soon as I boot it up NO dual monitor no Laptop LCD, the only thing I can do is go into CLI which then shows on both displays. Now I tried to edit the /home/<username>/.config/monitors.xml but it does nothing. Why can't they make this thing behave just like 10.04 and even 10.10 where you just ran a command like and BAM your display was totally reset. WTF happen to that. I understand that we need progress BUT keep it simple stupid works just fine. Why are we all of a sudden trying to go the Windows route?:confused:

Oh yeah by the way all previous versions of Ubuntu run just fine on my Dell XPS MMS 1330 Laptop. So it is not a hardware issue and I'm also running it in Ubuntu Classic mode so no BS Unity issue as far as I'm concern although I could be very wrong.

---

