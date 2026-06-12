---
title: "Change Screen Resolution From Within The Terminal"
date: 2008-08-08
forum: General Help
---

### Post by ImInYourDreams on 2008-08-08
Posted this on Linux Mint forums also 

> Recently I have changed my screen resolution, and well it didn't turn out to well. My computer boots up fine and everything and once logged into X it does not shut down but it shows a screen where everything is distorted and overlapped. That means I can not see how to change the resolution back to what it originally was. Is there a way to do this while Grub is loading, and or/ is there a way to change the resolution via terminal? If you need to know what my resolution was before it was

800x600

Also if you need to know the distro it is

Linux Mint 4.0 Daryna

Thank you all for your help in advance.

Since Linux Mint is based off of Ubuntu, (Gusty I thin( I think that maybe , notice I say maybe someone will be able to help. 

What I am looking for specifically is to just Set it back to 800x600 resolution while in the ALT-F2 terminal. I do not want an Easy Way Out. I am willing to do what it takes and try the command line but I just am wondering if this is possible because I don't want to have to reinstall my system just to get the resolution back. If that is what I have to do then so be it but for now, please take the time to read and try to help me, you don't have to help, but I'll be infinitely greatful if you would. 

-Dream

---

### Post by cmb11 on 2008-08-08
Full credit to this link:

#
[http://www.perpetualpc.net/srtd_commands_rev.html](http://www.perpetualpc.net/srtd_commands_rev.html)
#

{

xrandr

To change the resolution (monitor display) from the command line ( using a terminal window ) do this: ( when x is running -- don't exit Xwindows just use a terminal window. This is done from the command line. )
[ xrandr ]
this command will bring up information like this:

 SZ:    Pixels          Physical       Refresh
 0   1024 x 768    ( 271mm x 201mm )   75   70   60  
 1    800 x 600    ( 271mm x 201mm )   85   75   72   60   56  
 2    640 x 480    ( 271mm x 201mm )   85   75   72   60  
*3    832 x 624    ( 271mm x 201mm )  *74  
 4    720 x 400    ( 271mm x 201mm )   85  
 5    640 x 400    ( 271mm x 201mm )   85  
 6    640 x 350    ( 271mm x 201mm )   85  
Current rotation - normal
Current reflection - none
Rotations possible - normal 
Reflections possible - none


This will show the resolutions possible on your monitor. The star indicates what is currently being used. To change resolution use a command like this:
[ xrandr -s 1024x760 ]

This will immediately change the resolution; in this case to 1024x760.

To check for xrandr on your system type
[ xdpyinfo ]

(If you see RANDR listed under number of extensions then it should work.) 

Also typing [ xrandr -s ] will give u info on the usage of this command.


}

Good Luck! :)

Let me know if this was helpful.

---

### Post by ImInYourDreams on 2008-08-08
> **cmb11 said:**
> Full credit to this link:

#
[http://www.perpetualpc.net/srtd_commands_rev.html](http://www.perpetualpc.net/srtd_commands_rev.html)
#

{

xrandr

To change the resolution (monitor display) from the command line ( using a terminal window ) do this: ( when x is running -- don't exit Xwindows just use a terminal window. This is done from the command line. )
[ xrandr ]
this command will bring up information like this:

 SZ:    Pixels          Physical       Refresh
 0   1024 x 768    ( 271mm x 201mm )   75   70   60  
 1    800 x 600    ( 271mm x 201mm )   85   75   72   60   56  
 2    640 x 480    ( 271mm x 201mm )   85   75   72   60  
*3    832 x 624    ( 271mm x 201mm )  *74  
 4    720 x 400    ( 271mm x 201mm )   85  
 5    640 x 400    ( 271mm x 201mm )   85  
 6    640 x 350    ( 271mm x 201mm )   85  
Current rotation - normal
Current reflection - none
Rotations possible - normal 
Reflections possible - none


This will show the resolutions possible on your monitor. The star indicates what is currently being used. To change resolution use a command like this:
[ xrandr -s 1024x760 ]

This will immediately change the resolution; in this case to 1024x760. ( it takes about .5 seconds on my system which uses a "Super View 1280" monitor which is actually an Hitachi cm500 as far as specifications go -- I am using RedHat with kernel 2.4.20-6 and Xfree86 version 4.3.0)
To check for xrandr on your system type
[ xdpyinfo ]
(If you see RANDR listed under number of extensions then it should work.) Also typing
[ xrandr -s ]
will give this information:

usage: xrandr [options]
  where options are:
  -display <display> or -d <display>
  -help
  -o <normal,inverted,left,right,0,1,2,3>
            or --orientation <normal,inverted,left,right,0,1,2,3>
  -q        or --query
  -s <size>/<width>x<height> or --size <size>/<width>x<height>
  -r <rate> or --rate <rate>
  -v        or --version
  -x        (reflect in x)
  -y        (reflect in y)
  --screen <screen>
  --verbose


This assumes your (crt) monitor is set up with vertical and horizontal specifications that it can handle. Be aware that you can inadvertently destroy your monitor with the wrong settings.

}

I've tried xrandr but the terminal simply displays the message 

"Can not open display"  

Same thing when I tried  # xrandr -s 800x600 

---
Would me using the Entrance log in manager and the Enlightenment window manager have any thing to do with this that could effect xrandr? (I'm not using gdm) 

Thank you for your help though, I do appreciate it, even if it doesn't work for me. I might be able to help someone else in the future. :)

---

### Post by essence25 on 2010-12-17
Now how can this be done via SSH command? If this is done remotely i get:Can't open display 


How can I pass this command from a SSH terminal from another machine?

Ty in advance!

---

### Post by tredegar on 2010-12-17
**xrandr** is only for X

If you want the ctrl-alt-F1 terminal resolution changing to 800x600 then you need to change the framebuffer resolution by adding **vga=*xyz*** to your kernel boot line. The right number for *xyz*, err, depends.
See here [https://wiki.archlinux.org/index.php/GRUB](https://wiki.archlinux.org/index.php/GRUB) under "Framebuffer Resolution"

---

### Post by tonyburkhart on 2011-05-22
> **cmb11 said:**
> Full credit to this link: [http://www.perpetualpc.net/srtd_commands_rev.html](http://www.perpetualpc.net/srtd_commands_rev.html)


 To change resolution use a command like this:
[ xrandr -s 1024x760 ]

This will immediately change the resolution; in this case to 1024x760.

Good Luck! :)

Let me know if this was helpful.

This was _*very*_ helpful. Thank you!

I have a Vizio VL260M for my test monitor. Normally everything I connect to it auto-adjusts and gets a resolution that I can work with and tweak. For some reason, the Compaq Presario 6420nx I am testing would only boot into 1400x1050 - 60.0, leaving me with a view of the lower right quadrant of the screen and no way to navigate via mouse to system preferences. I used to ALT-F2 to open terminal and this command saved me a load of time. 

Thanks again :)

---

