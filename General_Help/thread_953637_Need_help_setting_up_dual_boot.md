---
title: "Need help setting up dual boot"
date: 2008-10-20
forum: General Help
---

### Post by dlbrando on 2008-10-20
It worked great on my other system but I am having problems on my laptop.  On the desktop it gave me an easy screen with an option of where to boot to.  How do I get back to that now.  After installing XP SP3 it just boots strait to windows.  I have a couple of quick ideas but I do not think they will work

---

### Post by niyonk on 2008-10-20
What were you using to boot into either OS? Were you using Grub or just the windows bootloader.

Anyway, this [link]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") will help 

Cheers! :)

---

### Post by dlbrando on 2008-10-20
looks like exactly what I was looking for but could not find, kind of like my linux live cd.  So I guess I will go make another of those first

---

### Post by niyonk on 2008-10-20
What exactly do you mean? 
You don't have a live CD?

---

### Post by dlbrando on 2008-10-20
instructions say to boot from the linux cd so you can get a terminal and go from there.  I dont have mine.  I have PCSed from NC to Florida since the last time I used it and probably could not place it within a 50 ft circle.  So I am downloading another and will go from there.

I should clarify:  after I loaded windows, It gave me no option to mess with the boot sector, just did it.  So now I need a live CD cause it was the only way I could think of to get back to a terminal and mess with grub

---

### Post by guitsy on 2008-10-20
first you install ur xp .when partition screen comes u leave free space to install ur ubuntu.
ie if u have 40gb
15gb for c:drive
10gb for d:drive and leave the 15gb free for ur ubuntu installation.after installing xp restart and put ur ubuntu cd.
during partition choose to install ubuntu in free space.after installation u will b presented with both os during boot.

NB:When u upgrade ur windows to xp2/xp3 ur system will reboot auto
and during startup windows cd will ask.to setup cd press..
pls dont press any key now.wait few sec and select ur windows from grep menu and ur windows upgrade will start again.:guitar:

---

### Post by dlbrando on 2008-10-20
I have been running ubuntu for most of a year now, I just was given a copy of XP, so I can run rosetta stone, and am trying to dual boot it after installing xp on top.

 used g parted to give windows 50 gigs and linux 95 since it is my main.  everything went well there and I installed windows, now I just need to get it to where it gives me the choice on where to boot to

ran through that link and now I boot to linux, gotta se what to do from here

---

### Post by dlbrando on 2008-10-20
ok so this is not working.  I do have my linux booting first now, and I edited menu.lst like in the tutorial.  But I have no way to select anything when I witch to the boot list on startup (arrow key do not work).  It times out then goes through the long startup for ubuntu.  I seem to have lost some features(wireless)  and when I go through that long boot it gives me the option to repair broken packages.  I have not done this option yet

---

### Post by Monotoko on 2008-10-20
**Ensure that you backup menu.lst**

try editing the menu.lst file from your live CD

change the following
```

timeout 0 (or whatever number, might not be 0)

```

to

```

timeout 10

```

and then add to the bottom
```

title Microsoft Windows XP
root (hd0,1)
savedefault
makeactive
chainloader +1

```
replacing (hd0,1) with whatever windows is installed on (probably (hd0,1) if you only have duel-boot, but ensure you backup before trying this)

---

### Post by dlbrando on 2008-10-20
everything I have has (hd0,0) so I have not changed it.  I also removed hiddenmenu from the file and changed it to 10.  I do nto have save default in the line of code though.

It actually seems to be screwing the system.  Granted everything on this particular computer ha been much harder then on my desktop.  I have no doubt that this would have taken 10min on my desktop.  The Emachines N-10 is a strange animal

---

### Post by dlbrando on 2008-10-20
Ok I think I got everything worked out.  Now I just need to go out and find all the drivers for windows for this thing.  

last question:  On the boot menu screen, is there a way to change the color of the highlited bar to a light color, mine is a shade darker than the screen so it is hard to see

---

