---
title: "Need help with MS Trackball Optical"
date: 2006-12-08
forum: Hardware &amp; Laptops
---

### Post by netsurfau on 2006-12-08
G'day,

I've got a 4 button Micro$oft Trackball Optical.
You can see a pic of it here:

[http://www.microsoft.com/uk/retail/product_screens/mice_key/trackball_optical/](http://www.microsoft.com/uk/retail/product_screens/mice_key/trackball_optical/)

The wheel and two main buttons are working, wheel only scrolling about
one line at a time which is annoying.  When using it in XP, I had the 
two extra, smaller buttons set up for copy/paste - these are the functions
I want to get back.  I've done a quick search looking for ideas, a great
deal of success as, I'm still quite a novice on Linux & every trackball
reference I could find was for a Logitech unit.  I also tried a search on 
Google which proved to be a bit confusing (](*,)), with a number of the 
links getting too technical for me or, not really relevant.

I'm getting rather adept at command line in Ubuntu so, should be able to do
a bit through it.  So, any and all help appreciated, just didn't think it
would be as difficult as it's turning out to be.

Regz

---

### Post by netsurfau on 2006-12-19
Isn't there anyone out there willing to help me with this? :confused: 

I said I was a novice and did search the forums, without success,
for help before posting.  All I could find was references to "Logitech"
trackball's and mine doesn't have an equivalent (that I could find)
in the Logitech range. 

This is becoming the only issue remaining from my transfer from XP
to Ubuntu. How about cutting a novice a break?

---

### Post by Greevous on 2006-12-22
Netsurfau, 

    I have the same exact mouse (wouldn't have bought it if I had switched to Ubuntu earlier). Personally, I prefer [Back] and [Forward] when I'm browsing, but I haven't found any solution either. I was hoping to find an answer in these forums as well.
[I]
Edit>> I found [this thread,]("http://ubuntuforums.org/showthread.php?t=28374") hope it helps. [/I]

---

### Post by Greevous on 2006-12-22
Netsurfau, 

I looked in another thread and found a solution to my own problem. As I said, I have the same exact mouse as you do, but the result of this action may be a little different:

When replacing the text in your xorg.conf file, instead of 
```

Section "InputDevice"
Identifier "mouse.usb"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "Buttons" "7"
**Option "ZAxisMapping" "6 7"**
EndSection

```

I used
```

Section "InputDevice"
Identifier "mouse.usb"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "Buttons" "7"
**Option "ButtonMapping" "1 2 3 6 7"**
EndSection

```

---

### Post by netsurfau on 2006-12-22
Thanks Mate,

Now all I need is the reference table for which function is assigned to which number.
Will try a search of previous posts.

---

### Post by netsurfau on 2006-12-23
Those settings helped.  
Now to try and get the two extra side buttons to "copy" & "paste" which is what I normally have then setup to do.

Big Thanks to Greevous

---

### Post by tweedledee on 2006-12-23
> **netsurfau said:**
> Those settings helped.  
Now to try and get the two extra side buttons to "copy" & "paste" which is what I normally have then setup to do.

Big Thanks to Greevous

Try this thread: [http://www.ubuntuforums.org/showthread.php?t=316441](http://www.ubuntuforums.org/showthread.php?t=316441).  The short version is that you need to use xbindkeys and either xvkbd or xte (from xautomation) to send the "ctrl+c" & "ctrl+v" keypresses when you click the mouse button.

---

### Post by blacksol on 2007-08-19
Thanks for the xorg.conf changes. 

It wasn't a deal breaker but a major time-saver.

---

### Post by jijin on 2007-10-30
> **Greevous said:**
> Netsurfau, 

I looked in another thread and found a solution to my own problem. As I said, I have the same exact mouse as you do, but the result of this action may be a little different:

When replacing the text in your xorg.conf file, instead of 
```

Section "InputDevice"
Identifier "mouse.usb"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "Buttons" "7"
**Option "ZAxisMapping" "6 7"**
EndSection

```

I used
```

Section "InputDevice"
Identifier "mouse.usb"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "Buttons" "7"
**Option "ButtonMapping" "1 2 3 6 7"**
EndSection

```

Thanks alot btw. I wish they were still making the trackball.

---

### Post by netsurfau on 2007-11-25
Hi jijin,

Agree, wish M$ was still making this particular trackball.  Haven´t found another that comes as close to comfort and ease of use.

---

