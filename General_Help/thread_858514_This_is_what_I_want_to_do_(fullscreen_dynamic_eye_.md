---
title: "This is what I want to do (fullscreen dynamic eye candy)"
date: 2008-07-13
forum: General Help
---

### Post by dimitrioskdimit on 2008-07-13
So i've decided to transform my old laptop into basically a dynamic piece of furniture. I've mounted a flatscreen LCD to a wall with a keyboard and mouse beneath it, all connected to my laptop.

Everyone suggested I install linux to accomplish this, and I installed Ubuntu. So far i'm enjoying it, but have yet to accomplish my goal. 

Basically I want to the screen to display a variety of goodies. For starters, I have installed Rythmbox Musicplayer, which will do me good for the music. When put in party mode it takes up the whole screen and looks really nice.

For more day to day things, I want some type of full-screen calendar, maybe that also displays the daily weather report. It would be nice if the calender was dynamic and I could make alarms  or notes for certain days (Ideally I want to use my computer as my morning alarm clock as well).

First I tried a program called desklets, which was pretty simplistic and not full-screen, and not very attractive. I tried superkaramba, and pretty much had the same problems.

I just tried Screenlets, which was better then the others, but still a bit ugly, not fullscreen, and didn't quite work in the ways I wanted.

Does anyone have any suggestions for ways to accomplish the type of thing I'm looking for?

Thanks a lot!

---

### Post by Sealbhach on 2008-07-13
Maybe Google gadgets?

[http://www.getdeb.net/release.php?id=2798](http://www.getdeb.net/release.php?id=2798)

Have a look on that site, it's got lots of nice apps.


How about Conky? Might take a bit of configuring but you can get a nice display like this guy here has

[See post here]("http://ubuntuforums.org/showpost.php?p=5317726&postcount=2822")



.

---

### Post by squaregoldfish on 2008-07-13
I haven't played with it enough to know if it will cover what you need, but how about running Google Calendar (or similar) in a full-screen web browser?

Steve.

---

### Post by dimitrioskdimit on 2008-07-13
Hey Guys! Thanks for the input.

Google Gadgets was a neat program but It seems that there was no way to make anything full-screen. Plus there was an ugly gray background behind everything. 

I'm still trying to get conky to work, but no luck finding it after installing it. It hasn't appeared in my applications and I can't find it anywhere. :(

I'll give that google calendar a try too, thanks Steve.

---

### Post by forger on 2008-07-13
a) if it's a calendar you're looking for to add events to it, how about using google calendar in full screen firefox? especially in firefox 3.0, which hides the toolbar when you go fullscreen (F11)
[http://www.google.com/calendar](http://www.google.com/calendar)
b) if you want newer, better screenlets, try the backports version :)
[http://packages.ubuntu.com/hardy-backports/all/screenlets/download](http://packages.ubuntu.com/hardy-backports/all/screenlets/download)
Also, check out the rest of the screenlets: [http://screenlets.org/index.php/Category:UserScreenlets](http://screenlets.org/index.php/Category:UserScreenlets)

---

### Post by tuxxy on 2008-07-13
to run conky open terminal and type conky

or you can make a button on your start menu for it using this command, do this in the main menu editor

---

### Post by Sealbhach on 2008-07-13
> **dimitrioskdimit said:**
> 
I'm still trying to get conky to work, but no luck finding it after installing it. It hasn't appeared in my applications and I can't find it anywhere. :(

I'll give that google calendar a try too, thanks Steve.

For Conky to work, you would need to mess with the configuration files a little - it's quite enjoyable though, if you can spare the time.

Start from step 3 in this how-to here:

[http://ubuntuforums.org/showthread.php?t=205865](http://ubuntuforums.org/showthread.php?t=205865)

To start Conky, just type in the terminal

```
conky
```

To stop it

```
killall conky
```

It's quite time consuming to adjust the conky for how you like it but you can get some reaally nice displays:

[http://images.google.co.uk/images?q=conky&um=1&ie=UTF-8&sa=N&tab=wi](http://images.google.co.uk/images?q=conky&um=1&ie=UTF-8&sa=N&tab=wi)


They would look cool on your big screen.

.

---

### Post by forger on 2008-07-13
There's also a conky-like screenlet too, called sysmonitor

By the way, you can scale screenlets, right-click on any of them then select Size > 500% :)

---

