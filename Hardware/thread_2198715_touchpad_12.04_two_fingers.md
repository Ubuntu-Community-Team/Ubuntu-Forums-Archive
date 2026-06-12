---
title: "touchpad 12.04 two fingers"
date: 2014-01-10
forum: Hardware
---

### Post by jauntyjackalope2 on 2014-01-10
**Dear Ubuntu community,**

[COLOR=#ff0000]**E[SIZE=3]dit:[/SIZE]**[/COLOR][SIZE=3] [COLOR=#ff0000]The problem is solves with the next pointrelease 12.04.[/COLOR][COLOR=#000080]**4**[/COLOR] [COLOR=#ff0000](-:[/COLOR] [COLOR=#000080]Have fun[/COLOR][/SIZE]

[COLOR=#0000ff][I]short: elantech tpouchpad no function with its original modules. works under 13.10, but not with 13.10 modules under 12.04
[/I][/COLOR]
im on a **Acer e-531** with ubuntu **12.04, 3.8.0-35-generic #50-precise1-ubuntu** which has a **ETPS/2 Elantech Touchpad** build in. The Touchpad **isnt working at all**, it just move a few millimeters by chance.
[COLOR=#0000ff]*The "dirty fix" with the modprobe -r psmouse is working for me though, but that let xinput recognise my Touchpad as a PS/2 generic mouse and it lacks of any functions the pad provides as 2 Finger scrolling etc etc.*
[/COLOR]
Now comes the interesting parts (-:
The TP (Touchpad) is fully recognised by xinput, its activated and Xorg.0.log shows no Problems with it at all. But, it wont work. Thats for the module : **xserver-xorg-input-synaptics 1.6.2-1ubuntu6** ! But when i boot with a live-system from [COLOR=#ff0000]**Saucy Salamnder 13.10**[/COLOR], the [COLOR=#ff0000]**TP is working out of the box !!!**[/COLOR] correctly recognised with all its beautifull functions.
So i tryed to install the [COLOR=#ff0000]**xserver-xorg-input-synaptics 1.7.1**[/COLOR] which is the modukle from saucy in precise, but without sucsess cause it needs a metapackage which isnt installable. Theres a bugreport if i remember correct. So i [COLOR=#ff0000]**compiled it **[/COLOR]which worked out pretty nice, because its again fully recognised by xinput, syncl -l shows all values, xorg.0.log is happy with it, all great. But, u may guessed it, its [COLOR=#ff0000]**still not working**[/COLOR] at all (-: same behavior as before, it just moves a few millimeters once and a while if touching the tp intensivly.

So, i investigated the two outputs of xinput -list-props of the working saucy live system and my precise install, both with modul1.7.1, and the only real difference i discovered was :
```
Synaptics Pressure Motion (286):  ... of unknown type CARDINAL
```
at the precise install. So i tried to set the value with xinput but that didnt work, and syncl already showed the right values for pressure : 30, 160.
Playing around with that values wasnt transported to xinput -list-props at all (neither after reboot).

Im at this for 2 days now (fulltime), and believe my i think i read the whole interweb regarding this, incl 20 threads in this forum, i already tryied to install synaptiks too.
[B]Key-points:
[/B][I][COLOR=#0000ff]- what is the difference between the installed xorg-server-input-synaptics1.7.1 between 12.04 and 13.10 ?? why is it working there, not here ?[/COLOR]
[COLOR=#0000ff]- why cant i set the Synaptics Pressure Motion ? maybe that is the source of the error ?[/COLOR][/I]
You wise man of *nix out there, can u give me a hint ?[B] :-)
thank you everybody for your help !!!

[/B]I didnt find a expandable codebox, so i attach all relevant snipplets as files here, hope that the best way.[ATTACH]249353[/ATTACH]

---

