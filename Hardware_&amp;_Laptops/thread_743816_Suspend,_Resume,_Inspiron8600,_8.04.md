---
title: "Suspend, Resume, Inspiron8600, 8.04"
date: 2008-04-03
forum: Hardware &amp; Laptops
---

### Post by NullHead on 2008-04-03
I've installed hardy on my laptop, Dell Inspiron 8600, and when I try to suspend it works just fine, but when I attempt to resume it fails to come through all the way. The power light lights, as if it were turned on, the screen tries to come out of sleep, but it fails to do so. It leaves me sort of stuck in limbo. I have to hold the power button for 10seconds for it to do anything. I have the Nvidia-glx-new restricted driver installed. 

Now I want to know if there is a log I can check to see where the error is when it comes time to resume. Has anyone else has this problem with their Inspiron8600 or with a different machine? 

Any help would be nice!

EDIT: Also when I close the lid and the screen button is pushed it magically tries to resume, but it fails and drains the battery.

EDIT AGAIN: Also Kubuntu suspended and resumed miraculously when I was testing it. I didn't like the KDE part, but it did suspend and resume just fine.

---

### Post by NullHead on 2008-04-03
BUMP

Anyone know of a log I can check to see the errors when I resume from suspend?

---

### Post by NullHead on 2008-04-03
BUMP

Please!!!!! anyone ](*,)

---

### Post by NullHead on 2008-04-03
BUMP

... please ... anyone... a suspend log .... anything that logs suspend?? ... :frown:

---

### Post by NullHead on 2008-04-04
[FONT="Tahoma"]Bump

Ok well I've fixed suspend and resume. It works great now.

There is one more problem. When I open the lid the machine resumes. This is a problem because the button that controls if the screen is turned on or off has issues ... so if I put a little pressure on the top of the lid and then remove the pressure the machine wakes up ... now this has happened before, but I thought I simply didn't get the machine to sleep properly. 

Does [SIZE="3"]ANYONE[/SIZE] know of a way to disable this function? What I mean by this is: can I disable wake when I open the lid?[/FONT]

---

### Post by aidave on 2008-04-04
I have the exact same problem with 7.10 (with or without system upgrades) on Inspiron 1420n.  Seems like Dell ships a faulty laptop.

Only, sometimes it resumes, sometimes it doesnt.  Every, oohhh, 3rd time it resumes, it will just hang like you described.  I will have to hold the power button down for a long time, to turn it "off" then turn it back on.

VERY FRUSTRATING!

How did you fix it?

---

### Post by NullHead on 2008-04-04
I used this guide here: [https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron8600](https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron8600) please note it is intended for an inspiron 8600, but it might work for you too. 

The problem I'm having now is that when the screen's on/off button gets pushed, e.g I put pressure over the part of the screen (when lid is closed) it'll push on the button and wake the computer when I release the pressure. 

So basically the way this is intended to work is it s supposed to resume when you open the lid, but my button is mashed and doesn't hardly work. So it's a real problem when the computer resumes when it's not supposed to.

---

### Post by nick_h on 2008-04-04
If you right-click on the Gnome Power Manager icon and select preferences it will give you the option to "Do Nothing" when the laptop lid is closed.

---

### Post by NullHead on 2008-04-04
I've done what you suggest but the problem remains. This doesn't happen when I simply don't push the button in any sort of way, but I know if the machine is in it's bag it'll be pressed wilt being transported and resume when I don't want it to. 

I like the feature of the screen turning off when I close the lid, but I don't want it to happen when I put the machine into sleep mode.

---

