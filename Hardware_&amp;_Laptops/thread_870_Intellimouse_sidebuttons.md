---
title: "Intellimouse sidebuttons"
date: 2004-10-16
forum: Hardware &amp; Laptops
---

### Post by jeremy on 2004-10-16
I have followed the instructions iat 
[http://www.linuxquestions.org/questions/showthread.php?s=&amp;threadid=108737](http://www.linuxquestions.org/questions/showthread.php?s=&amp;threadid=108737) and have everything working perfectly if I run xmodmap -e "pointer = 1 2 3 6 7 4 5" and imwheel -k -b "67" manually, but I can't make it start automatically with X. It is just a question of finding the right place for the script(s). I have done it before in ubuntu and it does work, I just can't remember where to put the scripts.

---

### Post by jeremy on 2004-10-16
I managed to sort it ot, I am posting the solution in the hope that it will be of use to others.

I created 2 files in the folder, /etc/X11/xsession.d
one called "65mouse" containing the text;
xmodmap -e "pointer = 1 2 3 6 7 4 5"
the other called "70imwheel" containing the text;
imwheel -k -b "67"

permissions on both files are 744

Doing it this way the side buttons work, regardless of which user is logged in.

---

### Post by HungSquirrel on 2004-10-16
To do it on a per-user basis, put the pointer line it in your ~/.Xmodmap file.  That's what I do for mine.  Great mouse by the way.  M$ software may suck, but their input devices aren't half bad.   8)

---

### Post by FLeiXiuS on 2004-10-16
I love my MX-510 :-)  I downloaded MWheel for my kernel and compiled the patch and it successfully initiated my 10 button mouse :-)

---

### Post by Rancoras on 2004-10-16
How about a howto FLeiXiuS?  I also have an MX510 (great mouse).

---

### Post by falconed on 2007-08-12
Hello,

I know this is an old thread, but I wanted to post my configuration for the Microsoft Wireless Laser Mouse 6000.  I was able to get the wheel and back/forward buttons to work with the following settings:

In /etc/X11/xorg.conf: 
```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
EndSection
```

In /etc/X11/Xsession.d/65mouse:
```

xmodmap -e "pointer = 1 2 3 4 5 8 9 6 7"
```

Imwheel is not needed for this solution.  

I haven't yet been able to get the horizontal scroll buttons to work.  Has anyone had success with those?  They don't even show up on  xev, which leads me to believe it's a driver issue.

-Dan

---

### Post by tmac2007 on 2007-08-23
> **falconed said:**
> Hello,

I know this is an old thread, but I wanted to post my configuration for the Microsoft Wireless Laser Mouse 6000.  I was able to get the wheel and back/forward buttons to work with the following settings:

In /etc/X11/xorg.conf: 
```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
EndSection
```

In /etc/X11/Xsession.d/65mouse:
```

xmodmap -e "pointer = 1 2 3 4 5 8 9 6 7"
```

Imwheel is not needed for this solution.  

I haven't yet been able to get the horizontal scroll buttons to work.  Has anyone had success with those?  They don't even show up on  xev, which leads me to believe it's a driver issue.

-Dan


Thanks, tried may fixed this one worked like a champ.

---

### Post by hugomeeuwes on 2007-11-23
I tried a lot and couldn't get it working.
Finally found this link: [http://wiki.serios.net/wiki/Mouse_side_buttons]("http://wiki.serios.net/wiki/Mouse_side_buttons")

It's very different from the usually mentioned approaches, but worked within a minute.

---

### Post by Student Driver on 2007-11-25
> **falconed said:**
> Hello,

I know this is an old thread, but I wanted to post my configuration for the Microsoft Wireless Laser Mouse 6000.  I was able to get the wheel and back/forward buttons to work with the following settings:

In /etc/X11/xorg.conf: 
```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
EndSection
```

In /etc/X11/Xsession.d/65mouse:
```

xmodmap -e "pointer = 1 2 3 4 5 8 9 6 7"
```

Imwheel is not needed for this solution.  

I haven't yet been able to get the horizontal scroll buttons to work.  Has anyone had success with those?  They don't even show up on  xev, which leads me to believe it's a driver issue.

-Dan

I just wanted to add that it worked for me as well, with a Dell Latitude D610 and my old Intellimouse optical.

---

