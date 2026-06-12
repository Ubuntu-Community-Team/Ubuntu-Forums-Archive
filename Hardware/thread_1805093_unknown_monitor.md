---
title: "unknown monitor"
date: 2011-07-15
forum: Hardware
---

### Post by jackechanprime on 2011-07-15
Hey guys. I just got a new computer, my old one gave up the ghost at long last. I swapped the hard-drives between them rather then bother reinstalling ubuntu and transferring all my data. Worked like a charm, but ubuntu cant seem to figure out the new monitor.

It's coming up as an "unknown moniter" and basically all of the settings are disabled. resolution is locked at 4:3... although it's a wide-screen. It can swap between 1024x768 and 800x600, but the later shunts 3/4 of the display off screen. In 1024x768 the entire display is stretched laterally, which i would really like to adjust, but i have no idea what to do.

Thanks in advance!
~Q

Edit: Oh, by the way. I've been told that sometimes i don't provide all the necessary info. If this is true at any time, PLEASE just ask. It's not intentional, just an outgrowth of cluelessness. Either i didn't know/remember that it was relevant, or didn't know you could do that.

---

### Post by dandnsmith on 2011-07-16
The Ubuntu version is one of the pieces of information specifically requested in the forum guidelines for posting - and may be extremely relevant here, as things have changed over the last few versions.

---

### Post by jackechanprime on 2011-07-16
Oh, of course; 10.04 lucid lynx. I thought the blurb in my username would be sufficient for that. Ok, so, where to next?

---

### Post by dandnsmith on 2011-07-17
Ok, that's something (not all sigs convey the correct info), so now we need to find out what the system is using, and what it thinks is possible - then it may be possible to get xorg configured manually to do what you want.
Q1 did you manually configure the old hardware installation?
Q2 what does xrandr show?
Q3 what are the graphics hardware?

Comment: there have been quite a number of threads on this resolution problem with various hardware in the last 6 months. You might find some relevant stuff there.

---

### Post by jackechanprime on 2011-07-17
Q1 did you manually configure the old hardware installation?
A) Not that i know of (how do i do that?)
Q2 what does xrandr show?
A) what's xrandr?
Q3 what are the graphics hardware?
A) NVIDIA GeForce GT 520M, Up to 1760 MB turboCache (according to the shiny sticker on the laptop)

Edit: shot-in-the-dark, i put "xrandr" into terminal, this was the output:

Screen 0: minimum 800 x 600, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0* 
   800x600        61.0

---

### Post by gordintoronto on 2011-07-17
What brand and model of monitor?

---

### Post by jackechanprime on 2011-07-17
It's an acer aspire 5750G-6804 Laptop. It's the built-in screen, I'm not techno-wizard enough to tamper with THAT. anything more detailed then that, your gonna have to tell me how to figure out.

---

### Post by dandnsmith on 2011-07-18
As far as I can ascertain, via Google searches:
- native resolution for that model is 1366x768
- there are manufacturer supplied drivers for the 520M (see [here](http://www.nvidia.com/object/linux-display-ia32-275.19-driver.html) for download)
and there may be usable installation instructions for the package [here](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/chapter-01.html) (the version number is different, but should work the same way)

Hope this helps

---

### Post by jackechanprime on 2011-07-18
Ok, the directions tell me to exit the x-server and kill all openGL apps.

Question 1) How do i exit the x-server (which is what again?)

Question 2) How do i identify an openGL application? the instructions note that some may remain online even after the x-server is shutdown.

---

### Post by dandnsmith on 2011-07-19
1) try [this page](http://theos.in/news/ubuntu-linux-shutdown-the-x-server/) - the x-server is the thing which enables all that graphical display you see.
Possibly [this page](http://ubuntuforums.org/showthread.php?t=206960) is better for your purposes

2) assume it's anything which is providing a graphical display on your screen

You may also need to know that you can get to a 'terminal' (not as a window) to log in using Ctrl-Alt-F1, and get back again to the normal display window scene with Ctrl-Alt-F7.

---

### Post by jackechanprime on 2011-07-19
Ack... sounds like this isn't going to be simple. Let me sort through this and give it a shot!

---

### Post by jackechanprime on 2011-07-20
Ok, well, i seem to have failed totally.

I have no idea what i did wrong, or what exactly is going on right now.

I ran these codes:

sudo /etc/init.d/gdm stop

=> got something back about using stop(8 ) and some sort of babbling about initid (i think that's how it was spelled.) had no idea what it meant, so i just ignored it.

cd (the appropriate location)

sh (name of driver).run
it brought up an installer gui, said the pre-run scripts had failed, and asked if i wanted to continue anyway. I said yes, half of the things it did worked, 2 or 3 returned errors.

now x-server is going loopy, and when i try to adjust my screen resolution the tool asks of i want to use the invidia driver, i say yes, then the invidia driver-thing tells me i'm not using the invidia driver. It then tells me to simply run nvidia-xconfig, which does an apparent nothing. I figure if i tinker with this anymore i'm just going to damage something.

:confused::confused::confused::confused::confused::confused:
heeeeeeeeeeeeeeeelp?

---

### Post by jackechanprime on 2011-07-20
Digging around for other errors, I've turned up;

at the startup screen:

module b43 does not exist in /proc/modules
module b44 does not exist in /proc/modules
module ssb does not exist in /proc/modules

All config files need .conf: /etc/modprobe.d/backlist

After this finishes displaying, a error box pops up instead of the login window;

Ubuntu is running in low-graphics mode:

the following error was encountered. you may need to update your configuration file to solve this.

(EE) No devices detected.

then it brings up a troubleshooter; selecting "restart x" gets everything working hunkiedory (minus the new driver actually... well... working.)

it also gives me the option to edit the config file and review the error logs and such.

the error log says:

(EE) no screen found (paraphrasing)

>_< what'd I do?

---

### Post by jackechanprime on 2011-07-22
um... help?

---

### Post by jackechanprime on 2011-07-25
anybody...?

---

### Post by jackechanprime on 2011-07-27
...seriously guys? Did i really **** up hard enough that nobody has any idea how to help me?

---

### Post by jackechanprime on 2011-08-02
well then, i suppose I'll make a new thread about my "new problem" elsewhere. I guess this isn't exactly the preview here anywhere.

p.s. sorry about my language above, merely jargon.

---

### Post by zzdjchris on 2011-08-03
> **jackechanprime said:**
> Q1 did you manually configure the old hardware installation?
A) Not that i know of (how do i do that?)
Q2 what does xrandr show?
A) what's xrandr?
Q3 what are the graphics hardware?
A) NVIDIA GeForce GT 520M, Up to 1760 MB turboCache (according to the shiny sticker on the laptop)

Edit: shot-in-the-dark, i put "xrandr" into terminal, this was the output:

Screen 0: minimum 800 x 600, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0* 
   800x600        61.0

I would like to jump in here, becuase I'm having what sounds like a similar problem, just BIGGER.

xrandr is reporting...

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA-1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
TV-1 disconnected (normal left inverted right x axis y axis)

However, this matters little, as I can't even enable my nVidia Gforce FX 5200 Drivers using the "Additional Drivers" app, as as soon as I do. My Maximum Resolution is a Pitiful 
640x480.
If I don't enable my nVidia's Drivers, then I get as reported above.

I'd like to be able to enable the Propriety drivers, and use my ACER Widescreen LCD monitor also.

If the LCD screen isn't plugged in. I have no problems with the Propriety drivers (that is, using a standard CRT monitor), but if my LCD is plugged in, well... I only get 2 modes... 320x240 or 640x480.

Please help, as I really need both.

Thanks,
  DeeJ.

P.s. How do I reach levels shown by xrandr like the reported 4096 x 4096. I only use the Monitors link under Preferences to change screen modes. 4096 x 4096... What a Dream!

---

### Post by realzippy on 2011-08-03
> **zzdjchris said:**
> I would like to jump in here, because I'm having what sounds like a similar problem, just BIGGER.


...that is threadnapping.Op's problem seems to be installing the nvidia-driver;yours is to get the correct resolution.
Anyway,
I am sure that your problem is solved when editing the
correct Hsync values (depending on your monitor model)
in the "Monitor" section of your xorg.conf file.....
Have a look at post #13 of this thread:
[http://ubuntuforums.org/showthread.php?t=1815604&page=2](http://ubuntuforums.org/showthread.php?t=1815604&page=2)

---

