---
title: "My flat screen auto turns off while im watcing a movie.. annoying to say the least."
date: 2007-08-26
forum: Hardware &amp; Laptops
---

### Post by sent17inel on 2007-08-26
My flat screen auto turns off while im watcing a movie.. annoying to say the least. Is this an ubuntu problem or a emachine problem since my flat screen is made by emachine. Is there a way to fix this? plz and thank you.

---

### Post by gilgongo on 2007-08-26
I get this too and it's frugging annoying.

The only thing I've been able to do is set up a small reservoir that drips water into a ballast tank that then uses a pulley system to slowly pulls a lead weight up over the keyboard and then drop it once the ballast gets to a certain weight (tipping the water into a secondary reservoir below). 

For a while I thought I'd invented a perpetual motion machine until I remembered I have to fill the main reservoir up about once every few hours.

I'm sure a software fix would be easier. :(

---

### Post by pbcartwright on 2007-08-26
ever think about adjusting your screensaver to 2 hours or turning it off when you watch a movie??

---

### Post by sent17inel on 2007-08-26
ya i have thought of doing and. I turn off the screensaver permanently and the screen still goes off..  its like a power saving feature on the monitor. Its stupid though cuz the monitor cant tell that im watching a movie or wut?
Its highly irritating......

---

### Post by RageOfOrder on 2007-08-26
It's not a screen saver issue, it's a DPMS (Display Power Management System) issue.  ****** if I know where to find it in GNOME though, so use your temrinal.

Here's a few useful xset options.

```

$ xset -dpms                       # Disable DPMS
$ xset +dpms                        # Enable DPMS
$ xset s off                        # Disable screen blanking
$ xset s 150                        # Blank the screen after 150 seconds
$ xset dpms 300 600 900             # Set standby, suspend, & off times (in seconds)
$ xset dpms force standby           # Immediately go into standby mode
$ xset dpms force suspend           # Immediately go into suspend mode
$ xset dpms force off               # Immediately turn off the monitor
$ xset -q                           # Query current settings

```

---

### Post by sent17inel on 2007-08-26
> **RageOfOrder said:**
> It's not a screen saver issue, it's a DPMS (Display Power Management System) issue.  ****** if I know where to find it in GNOME though, so use your temrinal.

Here's a few useful xset options.

```

$ xset -dpms                       # Disable DPMS
$ xset +dpms                        # Enable DPMS
$ xset s off                        # Disable screen blanking
$ xset s 150                        # Blank the screen after 150 seconds
$ xset dpms 300 600 900             # Set standby, suspend, & off times (in seconds)
$ xset dpms force standby           # Immediately go into standby mode
$ xset dpms force suspend           # Immediately go into suspend mode
$ xset dpms force off               # Immediately turn off the monitor
$ xset -q                           # Query current settings

```

Okay so What i put into the terminal was "xset #" it gave me some options some of which were these. ```
To control Energy Star (DPMS) features:
        -dpms      Energy Star features off
        +dpms      Energy Star features on
         dpms [standby [suspend [off]]]     
              force standby 
              force suspend 
              force off 
              force on 
              (also implicitly enables DPMS features) 
              a timeout value of zero disables the mode 

```
So then i put "xset -dpms"
it didnt look like it did much... but ill keep my fingers crossed... do u think this will work?

```
daniel@daniel-desktop:~$ xset #
usage:  xset [-display host:dpy] option ...
    To turn bell off:
        -b                b off               b 0
    To set bell volume, pitch and duration:
         b [vol [pitch [dur]]]          b on
    To disable bug compatibility mode:
        -bc
    To enable bug compatibility mode:
        bc
    To turn keyclick off:
        -c                c off               c 0
    To set keyclick volume:
         c [0-100]        c on
    To control Energy Star (DPMS) features:
        -dpms      Energy Star features off
        +dpms      Energy Star features on
         dpms [standby [suspend [off]]]     
              force standby 
              force suspend 
              force off 
              force on 
              (also implicitly enables DPMS features) 
              a timeout value of zero disables the mode 
    To set the font path:
         fp= path[,path...]
    To restore the default font path:
         fp default
    To have the server reread font databases:
         fp rehash
    To remove elements from font path:
        -fp path[,path...]  fp- path[,path...]
    To prepend or append elements to font path:
        +fp path[,path...]  fp+ path[,path...]
    To set LED states off or on:
        -led [1-32]         led off
         led [1-32]         led on
    To set mouse acceleration and threshold:
         m [acc_mult[/acc_div] [thr]]    m default
    To set pixel colors:
         p pixel_value color_name
    To turn auto-repeat off or on:
        -r [keycode]        r off
         r [keycode]        r on
         r rate [delay [rate]]
    For screen-saver control:
         s [timeout [cycle]]  s default    s on
         s blank              s noblank    s off
         s expose             s noexpose
         s activate           s reset
    For status information:  q
daniel@daniel-desktop:~$ xset 
daniel@daniel-desktop:~$ xset -dpms
daniel@daniel-desktop:~$ 

```
the above is my terminal output.

---

### Post by RageOfOrder on 2007-08-26
Yea, you just turned DPMS off. That should stop the monitor blanking now. The only thing that will control your screen is your screensaver now.

---

### Post by sent17inel on 2007-08-26
ya i think it worked! thanks dude! i appreciate it.

---

### Post by RageOfOrder on 2007-08-26
No problem. I think GNOME has a control panel, right? if you look through it, you should find a power management tab somewhere in there. That's your DPMS controls if you ever forget the bash command.

---

### Post by caporaso on 2007-08-30
Hi,
Will "xset -dpms" turn off DPMS permanently, or will I need to run it after restarts and/or logging in/out? If it's not permanent, where would be a good place to put it so that it ran on each log in/reboot? (.bash_profile would only work for a specific user, which would be fine by me, but would require starting a terminal or otherwise invoking bash, correct?)

Thanks!
Greg

---

### Post by RageOfOrder on 2007-08-30
> **caporaso said:**
> 
Thanks!
Greg

I've never really checked, but my guess is you'd have to do it every time. 
In Fluxbox it's as easy as adding "xset -dpms" to the ~/.fluxbox/startup file

In GNOME or KDE you'll need to write a little bash script and then link it to the startup process.

So if you wanted to write a little bash script, open your terminal and type
```

nano -w dpmsoff
#!/bin/bash
# Script to turn off DPMS features
xet -dpms
exit
```
Press ctrl+x and save the file here.
now you can link it with GNOME.

According to Gentoo-Wiki.org:
> 
 GNOME

Programs that you wish to autostart on GNOME startup can be selected by using the Control Center. To do this, open the Control Center and then navigate to Sessions followed by Startup Programs. Click Add and either type the path, or use Browse to select your desired program[s]. If multiple programs are selected, they can be launched in a desired order. 


Just select the script you just wrote and you should be all set.

and for KDE, you're just supposed to stick bash scripts into ~/.kde/Autostart


I should also add for the sake of completeness, you can modify your xorg.conf file to disable DPMS on x startup.

So if you open /etc/X11/xorg.conf and find your Monitor section,
you can add the Option "DPMS" "false" line.
```

Section "Monitor"
#other options can go here
Option "DPMS" "false"
#more stuff here
EndSection

```

I choose to use a startup script because I have other things that start with KDE (kiba-dock, xmodmap, etc)

---

### Post by IanW on 2007-08-30
_How-To for Gnome_

Go to :- System / Preferences / Power Management

On the AC Power tab, move both sliders all the way to the right until you see the word "Never"

Click Close

You're done.

---

### Post by Useff on 2007-09-03
Has this been fixed for you? I fixed mine when I realized I was using XGL so I had to make sure that I was using xset for display 0.

---

### Post by sent17inel on 2007-09-06
great question...i actually found out through just using my computer that it doesnt keep dpms off permantently after reboot or shutdowns.... so we will need to find a way to turn it off permanently.....

---

