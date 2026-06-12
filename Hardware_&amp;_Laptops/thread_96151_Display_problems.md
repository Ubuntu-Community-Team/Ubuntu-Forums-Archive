---
title: "Display problems"
date: 2005-11-28
forum: Hardware &amp; Laptops
---

### Post by Sonique on 2005-11-28
I have just installed from scratch Breezy [ not upgrade ] and when I get to the log in screen I can't see anything properly, it looks like a bit like when you have bad recption for your television, everything is distorted and flickering. You can log in [ without seeing what you are doing ] and sound works fine, I just need to know if there is a way to display ubuntu properly. Hoary did work fine.

---

### Post by mips on 2005-11-28
It sound like frequency of the signal coming from the video card is to high.

Check your laptops display specs for the Horizontal & Vertical Frequency range.

Edit your xorg.conf file to use frequencies within the above specs.

Maybe try and connect to a external monitor just for now while troubleshooting.

---

### Post by Sonique on 2005-11-28
Is there a shortcut to open up the terminal? because I can't see enough to use the mouse to open it up. Also could you tell me what /etc/xorg.conf should look like so i can edit it without seeing what I am doing.

Thanks mips

---

### Post by frodon on 2005-11-28
You could use the virtual terminals, use Ctr+Alt+F1 to go to the first virtual terminal (Ctrl+Alt+F7 is your graphical inetrface).
In command line i advice you to use nano to edit your file : ```
sudo nano /etc/x11/xorg.conf
```Useful link : [http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

---

### Post by Sonique on 2005-11-28
[http://sams.umcus.org/vaio/XF86Config-4]("http://sams.umcus.org/vaio/XF86Config-4")
This is the exact /etc/X11/xorg.conf for my laptop, the thing is that this is for OpenBSD, does that matter? If I copied it exaclty would it work?

---

### Post by frodon on 2005-11-28
Bad idea, run this command in order to reconfigure your video settings, it might work : ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Sonique on 2005-11-28
Problem is that it does not give the resolution I want, I want 1024x480. I have done it by doing it 680x480 [I think it was that] and it did display without flashing, however about 20 pixels worth of the top of the screen was at the bottom instead so it wasn't placed properly, and 680 isn't 1024 so its really streeeeeeeeeeeetched.

:confused:

---

### Post by frodon on 2005-11-28
You just need to put the vertical and horizontal parameters of your screen in your xorg.conf file to increase the resolution but as i said in post #3 all is explained in this HOWTO : [http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

---

### Post by ranf on 2005-11-28
[QUOTE=Sonique][http://sams.umcus.org/vaio/XF86Config-4]("http://sams.umcus.org/vaio/XF86Config-4")
This is the exact /etc/X11/xorg.conf for my laptop, the thing is that this is for OpenBSD, does that matter? If I copied it exaclty would it work?[/QUOTE]
So what Vaio exactly is it that you have? Mine (C1VE) also has 1024x480 resolution.

You could post the output (or relevant parts of it) of `lshw' here.

---

### Post by Sonique on 2005-11-29
I have a C1VE too, though I have a problem with getting the display to show properly. If I edit [COLOR="#ff0000"]/etc/xorg.config[/COLOR] it completely messes up and if I do [COLOR="Red"]sudo dpkg-reconfigure xserver-xorg[/COLOR] then I can't get the monitor size, even if I put the correct vertical and horizontal parameters in [COLOR="#ff0000"]/etc/xorg.conf[/COLOR] then nothing happen changes.

ranf did you have this problem or am I just an unlucky one?

---

### Post by ranf on 2005-11-29
[QUOTE=Sonique]I have a C1VE too, though I have a problem with getting the display to show properly. If I edit [COLOR="#ff0000"]/etc/xorg.config[/COLOR] it completely messes up and if I do [COLOR="Red"]sudo dpkg-reconfigure xserver-xorg[/COLOR] then I can't get the monitor size, even if I put the correct vertical and horizontal parameters in [COLOR="#ff0000"]/etc/xorg.conf[/COLOR] then nothing happen changes.

ranf did you have this problem or am I just an unlucky one?[/QUOTE]
"dpkg-reconfigure xserver-xorg" only uses a list of standard resolutions.
The point is: after editing xorg.conf don't run dpkg-reconfigure. And don't use the GUI resolution switcher.

You can try my settings from xorg.conf:
Monitor section
```

Section "Monitor"
        Identifier      "Standardbildschirm"
        Option          "DPMS"
        Modeline        "1024x480" 42.144 1024 1048 1184 1344 480 489 495 525 +hsync +vsync
#       DisplaySize     206     98
EndSection

```

Screen section:
```

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Rage Mobility P/M"
        Monitor         "Standardbildschirm"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1024x480" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x480" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x480" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x480" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x480" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x480" "640x480"
        EndSubSection
EndSection

```

---

### Post by Sonique on 2005-11-29
Thanks a lot for that code, however, it hasn't solved the problem. I would like to point out that sometimes it doesn't just flicker but instead: it has a bright light in the center that gets smaller and smaller fading to black, it flickers white while this is happening; and when the light disappears totally it just flickers white rapidly over a black background.

Guess my lil laptop sucks, it was fine in Hoary; when you configure Xorg, are any other files edited, because they may be the key to solving this.

Thanks everyone so far ;)

---

### Post by ranf on 2005-11-29
[QUOTE=Sonique]
Guess my lil laptop sucks, it was fine in Hoary; when you configure Xorg, are any other files edited, because they may be the key to solving this.
[/QUOTE]
Not in my case. Just xorg.conf.

---

### Post by Sonique on 2005-11-29
Do you think it is worth risking it and re-installing Hoary and then upgrade? The only thing is that i never got hoary online, but perhaps a fresh install may get it to work.

---

### Post by ranf on 2005-11-30
[QUOTE=Sonique]Thanks a lot for that code, however, it hasn't solved the problem. I would like to point out that sometimes it doesn't just flicker but instead: it has a bright light in the center that gets smaller and smaller fading to black, it flickers white while this is happening; and when the light disappears totally it just flickers white rapidly over a black background.
[/QUOTE]
But the resolution is 1024x480?

If yes then you will only have to find a working "Modeline".

I'll add my C1VE bookmarks:
[http://www-jcsu.jesus.cam.ac.uk/~mma29/c1/](http://www-jcsu.jesus.cam.ac.uk/~mma29/c1/)
[http://www.celifornia.com/documents/sonyvaio.html](http://www.celifornia.com/documents/sonyvaio.html)
[http://wiki.erazor-zone.de/doku.php?id=wiki:projects:linux:c1ve](http://wiki.erazor-zone.de/doku.php?id=wiki:projects:linux:c1ve)
[http://kryz.org/vaio.html](http://kryz.org/vaio.html)

---

### Post by ranf on 2005-11-30
[QUOTE=Sonique]Do you think it is worth risking it and re-installing Hoary and then upgrade? The only thing is that i never got hoary online, but perhaps a fresh install may get it to work.[/QUOTE]
What do you intend to solve this (long) way?

---

### Post by KermitJr on 2005-12-01
I was having trouble with several older video cards and a particular monitor and kept getting 640x480 no matter what I did for modes, etc.  

HOWEVER, when I went back one time and ran
```
sudo dpkg-reconfigure xserver-xorg
```

I entered the actually amount of RAM on the video card (one was 4096 and another 2048) and PRESTO! My Modes line worked as normal with or without monitor on boot.

So try entering in the actual video RAM you have and that should hopefully fix your error.

If not, troubleshoot by looking for the actual error messages in the /var/log/X11/xorg[tab].log file.

Hope this helps!
KermitJr

---

### Post by Sonique on 2005-12-04
Yay! some success! What I did was [COLOR="Navy"]only[/COLOR] copy ranf's modeline into my xorg.config file and now I can see my desktop at the right resolution properly!

Just one problem.. the screen is a shown about 20 pixels too high, so it cuts off the top [actually the top part that is cut off is stuck at the bottom]. Is there anyway in ubuntu to change the position of the screen?

---

### Post by ranf on 2005-12-04
[QUOTE=Sonique]Yay! some success! What I did was [COLOR="Navy"]only[/COLOR] copy ranf's modeline into my xorg.config file and now I can see my desktop at the right resolution properly!

Just one problem.. the screen is a shown about 20 pixels too high, so it cuts off the top [actually the top part that is cut off is stuck at the bottom]. Is there anyway in ubuntu to change the position of the screen?[/QUOTE]
Try the other sites I gave above. They all (or most of them) have their XF86config available. You should only care about their "Modeline".

---

### Post by Sonique on 2005-12-04
Yes! It works! Thanks a lot everyone, and thanks ranf for the final blow in getting this too work!

I did:

```
ModeLine "1024x480" 65.00 1024 1032 1176 1344 480 488 494 560 -hsync -vsync
```

And it looks fine, restarted the laptop to confirm and it still worked.

Cheers :D

---

### Post by ranf on 2005-12-04
Great.

---

