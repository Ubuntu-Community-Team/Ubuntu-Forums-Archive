---
title: "HP Mini 2133, OpenChrome wrong resolution (1024x768 instead of 1024x600)"
date: 2020-03-07
forum: Hardware
---

### Post by yaveton on 2020-03-07
Hi.

I found this probable solution to my problem - [https://bugs.freedesktop.org/show_bug.cgi?id=107412#c3](https://bugs.freedesktop.org/show_bug.cgi?id=107412#c3)

but... I'm not familiar enough with Linux to understand how to do the thing. I'd greatly appreciate help in this matter, thanks.

---

### Post by him610 on 2020-03-07
Hello yaveton,
Please show the results between the code tags...
```

uname -a
lsb_release -a

```

---

### Post by yaveton on 2020-03-08
Linux yaveton 4.15.0-88-generic #88-Ubuntu SMP Tue Feb 11 20:12:47 UTC 2020 i686 i686 i686 GNU/Linux

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.4 LTS
Release:    18.04
Codename:    bionic

---

### Post by him610 on 2020-03-08
What the reference says is that you may have a file located at* /etc/X11/xorg.conf* , and that you can modify it by adding the suggested lines to the file. Just in case you don't have the file, you can still create one. This is how it's done.... (Don't copy the crunch (#) or anything to the right of it)
```

sudo nano /etc/X11/xorg.conf 	# opens the file for editing with superuser - be careful

```
Using your mouse highlight and copy the following lines; paste them inside */etc/X11/xorg.conf*
```

Section "Monitor"
    Identifier      "FP-1"
    Modeline        "1024x600_60.00" 49.00  1024 1072 1168 1312  600 603 613 624 -hsync +vsync
    Option          "UseEdidDpi" "False"
    Option          "PreferredMode" "1024x600_60.00"
EndSection
 
Section "Screen"
    Identifier      "Screen 0"
    Device          "VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC]"
    DefaultDepth    24
    SubSection "Display"
           Depth   24
           Modes   "1024x600" 
    EndSubSection
EndSection

```
```

Ctrl+O    # saves the file
Ctrl+X    # closes the file and exits

```
Recommended reading: [http://linuxcommand.org/tlcl.php]("http://linuxcommand.org/tlcl.php")

---

### Post by yaveton on 2020-03-08
Hi, I did as you've told me. The result is my screen looking like this: [https://imgur.com/a/6pmT0rg](https://imgur.com/a/6pmT0rg)


Compared to 1024x768: [http://imgur.com/a/2saGy0Z](http://imgur.com/a/2saGy0Z)


I don't think it should look like this, and the bottom part of the desktop is going below the screen.
I tried to change the value from 1024x600_60 to 1024x600 and 600x1024, to no effect.

Although I "learned" how to use the laptop with this bug, I'm still looking for answers.

I'm really thankful for your reply and help.

---

### Post by him610 on 2020-03-08
Well, it was worth a try. 
I have an Acer ZG5 netbook about the same age, but my has intel graphics so I never had that issue.

---

### Post by mörgæs on 2020-03-09
Did you use tabs or spaces while creating xorg.conf?

---

### Post by him610 on 2020-03-09
@mörgæs Thanks for pointing this out.
> Did you use tabs or spaces while creating xorg.conf?
I copied the lines of code from the reference in the original post, [https://bugs.freedesktop.org/show_bug.cgi?id=107412#c3]("https://bugs.freedesktop.org/show_bug.cgi?id=107412#c3") then pasted them in an open Mousepad window where I removed the '>' symbols then pasted the lines into the middle code box of Post #4. I then advised the OP to copy and paste those lines. 
I honestly can not tell you if they are tabs or spaces. I sort of knew that yaml files were space sensitive, but I did not realize configuration script files were also.

---

### Post by yaveton on 2020-03-10
Hi @him610 @mörgæs .

I tried copying the commands to xorg.conf from the site itself, to the same result.

I tried to just rewrite the commands, using Enter, then Tab as spacer, and in both cases the result was GUI not loading: [https://imgur.com/a/hrvW1Jo](https://imgur.com/a/hrvW1Jo)

Removing content of xorg.conf using Nano fixes the problem.

Again, thanks for your time.

---

### Post by mörgæs on 2020-03-10
Good. 
I'm not sure that I understand why but anyway: If the problem is solved please mark the thread so.

---

### Post by yaveton on 2020-03-10
Pardon me, phrased it wrong - the GUI not loading was being fixed by removing the rewritten code from xorg.conf

---

### Post by him610 on 2020-03-10
Did you ever try to set your desired resolution using *xrandr* from the terminal?

---

### Post by yaveton on 2020-03-11
Not from the terminal, but I did try it via autostart.conf (or something along the lines, forgot how it's titled), to no effect, too. I have confirmation I wrote it right, because I saw the command in LXSession Startup options.

---

### Post by yaveton on 2020-03-30
Okay, so it didn't post, thanks my ISP. 

I tried using xrandr via the terminal - tried making new mode with instructions from the site I linked, and I did:

 1. xrandr --output FP-1 --mode 1024x768 --scale 1.0x0.78125 

2. xrandr --output FP-1 --mode 1024x600


With the first one there's an error "xrandr: Configure crtc 1 failed"

With the second one the result is the same as with copying the code to xorg.conf

---

