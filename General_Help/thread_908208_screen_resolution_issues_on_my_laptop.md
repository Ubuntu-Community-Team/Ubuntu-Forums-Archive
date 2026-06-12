---
title: "screen resolution issues on my laptop"
date: 2008-09-02
forum: General Help
---

### Post by nycazncarguy on 2008-09-02
hey, i have a gateway t-6836 laptop, x64 with a integrated intel GMA x3100 graphics card.  Everything runs fine on ubuntu. it works and everything.  I just have a slight problem with the way my screen is detected.  Like, ubuntu supports my resolution, i see the resolution taking up the whole screen (1280x800), but the top menu bar doesnt extend all the way.  Also, my AWN isnt exactly on the bottom.  It's a little higher than the bottom, and detects that as the bottom.  That's where it "docks" to.  I even attached a picture to show you, I think it's easier to see that way.

Thanks alot guys.

---

### Post by nycazncarguy on 2008-09-02
.....anything guys?  im hoping that you guys just missed my thread and not purposely avoided it =(

---

### Post by Jay11 on 2008-09-02
Not sure if you've tried this yet...right click the bar and go to Properties, and make sure Expand is checked.

---

### Post by nycazncarguy on 2008-09-03
it was already expanded. the box is checked. thanks for your suggestion though

Anything else?

---

### Post by nycazncarguy on 2008-09-03
oh, i forgot to mention. my login screen is like that too. You see the login screen like as if it was stuck to a 1280x1024 resolution setting, even though it is set to 1280x800. the outside area of that login screen is just the normal background color. So all these problems are pretty much related, i assume

Any ideas anyone?

---

### Post by nycazncarguy on 2008-09-04
wow.....nobody? nothing at all?

---

### Post by nbayiha on 2008-09-04
Do you have your graphic card driver installed ?
And did you installed correctly awm ? Try this thread , [http://ubuntuforums.org/showthread.php?t=856190&highlight=login+screen](http://ubuntuforums.org/showthread.php?t=856190&highlight=login+screen)

---

### Post by nycazncarguy on 2008-09-04
i know its not my awn because every other program that i make it dock to the bottom docks there too. Also, it was already like this right after a clean install. I figured the drivers would automatically be installed, considering that the resolution settings are there and the fact that this is a typical integrated intel GMA x3100 graphics card.  It's very common, if i recall correctly.

---

### Post by nbayiha on 2008-09-04
try this 
alt + F2 >> sudo displayconfig-gtk
and choose your resolution.

---

### Post by nycazncarguy on 2008-09-04
hey, i think we're getting somewhere =)
cuz i dont see an option for my resolution (1280x800). As for type, it's marked under "plug and play". i checked the widescreen part, and nothing worked after that, so i unchecked it. Then, i went to check out the drivers list and found the one i had (intel 965), but nothing happened when i chose it.  Maybe I didnt do something? I dunno.  But at least we're getting somewhere with that. Thanks~

---

### Post by Ecologger on 2008-09-08
There is a guide on this that solves this any many other problems with the Gateway laptop. [http://ubuntuforums.org/showthread.php?t=881127&highlight=gateway+T-6836]("http://ubuntuforums.org/showthread.php?t=881127&highlight=gateway+T-6836")

---

### Post by nycazncarguy on 2008-09-08
hmmm....i never found that thread for some reason...and i did my fair share of searching too...

oh well....thanks for the link! =)

---

