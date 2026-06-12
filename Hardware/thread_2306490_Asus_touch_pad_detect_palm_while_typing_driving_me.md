---
title: "Asus touch pad detect palm while typing driving me crazy also scroll problem on track"
date: 2015-12-16
forum: Hardware
---

### Post by jaime3 on 2015-12-16
Hi guy's I have a beautiful Asus G752VL-BHI7N32. Everything seem to  be working. Nothing I want to do but fix the Asus touch pad I don't know real name but under device in Window 10 it say Asus touch pad. Anyways when I type my palm would be read from touch pad then screw up like if i selected somethig. And also what drive me nuts is i wanna use my finger to scroll up or down. How can I get these two things working as how i like? Other then that. BAD POOP Ubuntu 15.10 detect everything. Ty all.

---

### Post by sudodus on 2015-12-16
Click on the icon with the cog wheel and wrench key (System Settings) and select 'Mouse and Touchpad'.

The simplest solution is to click on the switch, to turn it from 'ON' to 'OFF'.

But you can also leave it 'ON' but do some tweaking, for example untick 'Tap to click' and 'Two finger scroll'

---

### Post by jcer93705 on 2016-01-16
hi there isn't a option to disable. And plus much info here a pic.

---

### Post by sudodus on 2016-01-16
Hi jcer93705,

Which version (14.04, ... 15.10) and flavour of Ubuntu (Kubuntu, ... Xubuntu) are you running? You may need specific help for your version and flavour.

-o-

In Lubuntu and Xubuntu you can use the following command lines to turn the touchpad off and on:

```
synclient touchpadoff=1  # turns it off
synclient touchpadoff=0  # turns it on
```

The corresponding window looks like this in standard Ubuntu (see the attachment)! But notice that ***synclient*** and the touchpad selections in the window of standard Ubuntu appear, only if a touchpad is recognized. For example, it will be absent in a desktop computer or if the touchpad in a laptop is not recognized.

---

### Post by jcer93705 on 2016-01-16
I'm running ubuntu 15.10 I don't get those option. And I ran ur code return synclient touchpadoff=1 
Couldn't find synaptics properties. No synaptics driver loaded?
And driver is installed automatic I doubt it's a synaptic touch pad. Here also a pic of the option it give me 
under mouse and touch pad.

---

### Post by sudodus on 2016-01-16
It seems your touchpad is not found (and no driver is loaded).

I think you should ***start an own thread with a good descriptive title*** to attract people who know about your problem, because your problem is pretty much the opposite of the original poster's problem.

(And I don't know the solution for your problem - you need the help of other people.)

---

### Post by jcer93705 on 2016-01-17
> **sudodus said:**
> It seems your touchpad is not found (and no driver is loaded).

I think you should ***start an own thread with a good descriptive title*** to attract people who know about your problem, because your problem is pretty much the opposite of the original poster's problem.

(And I don't know the solution for your problem - you need the help of other people.)

Well seem nobody know solution. Or can't even say something. Atleast you tried.

---

### Post by sudodus on 2016-01-17
As I wrote before, there are probably people who know, but they will not find your question here, because it is in a thread with with a title, which does not fit your problem.

And remember that this is a world-wide forum, so you should wait for replies also from other time zones. You can bump your new thread after 16 and 32 hours if there are no replies. (Write a new post with the single word bump.)

Good luck with an own thread with a good descriptive title :-)

***Edit:*** I just found your new thread: [Hello I'm a noob and so a noob need help on touch pad that isn't detected](http://ubuntuforums.org/showthread.php?t=2310178)

I won't write there, because there is a group of people who are looking specifically for threads without any replies. I think it is better to wait until about 16 hours have passed until you bump it :-)

---

