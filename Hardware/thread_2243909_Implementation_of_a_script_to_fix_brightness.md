---
title: "Implementation of a script to fix brightness"
date: 2014-09-12
forum: Hardware
---

### Post by tears of the river on 2014-09-12
I had problems fixing brightness after updating my kernel on Lenovo b570-e however I followed the steps of the following link:

[http://ubuntuforums.org/showthread.php?t=1827810](http://ubuntuforums.org/showthread.php?t=1827810)

I can now change my brightness using the following code:

```
echo 100 > /sys/class/backlight/intel_backlight/brightness
```

and as I understand it this can hotfixed to keys the scripts provided in there namely:
[http://ideone.com/yPlo5](http://ideone.com/yPlo5)

Could someone explain how to use this script and how to hotfix it to the hot keys preferably the fn keys

Any help would be appreciated and thanks in advanced.

---

### Post by vasa1 on 2014-09-12
I think that you'll need to tell people which operating system you're using because the keyboard shortcuts may depend on the window manager.

---

### Post by tears of the river on 2014-09-12
I'm currently using ubuntu 12.04

---

### Post by matt162 on 2014-12-09
> **tears of the river said:**
> I'm currently using ubuntu 12.04

Dear Sir,
 From reading other posts, this seems to a popular topic. 

Some of the HP function keys cease to work after updating. I havn't fully read the on line manual since it's mainly catered for windows users, and I repartioned the whole disk before installing Ubuntu12.

This is using Ubuntu v12.04LTS.

Strangely, some hot keys still work. Namely the increase/decrease sound buttons(F2 F3) and the blank screen button (F9). I sorelry miss the F11F12 brightness controls.

Once on this page I had to test the buttons and now the F11F12 have sparked into life. (I had to check the names of the function keys so as to put them into words.)

Much appricated, but now instead of rewriting these comments, I leave it open to anyone who can give a reason as to why the sudden difference, being that the only modifications were to register for this forum?

Sincerely,
  Matthew 
 
closeclose
[LIST]
[/LIST]

---

### Post by matt162 on 2014-12-09
[QUOTE=matt162;13184092]Dear Sir,
 From reading other posts, this seems to a popular topic. 

Additonally, the hardware locks up whenever the lid is shut, or the rsume option is chosen on the GNOME menu, or the sleep command is given, and I cannot nail down the exact cause.

And, the eight terminals don't have any functional function keys any more, with 8 being the XWindows desktop key.

Would you sugest reinstalling version 12 from scratch, bearing in mind the internet travel involved with the upgrades? I would much prefer to long onto the currenet QNX/BSD boot loader for security reasons.

v14 seems to be far too touch pad oriented.

Tah Tah,


  Matt


closeclose
[LIST]
[/LIST]

---

