---
title: "[SOLVED] Is there a way to make the intel 945GM dual display?"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by dysphasi on 2007-10-20
I've had a look around the forums, but can't find a definite answer anywhere about this issue. 

I've got Ubuntu 7.10 installed. Everything looks fine, I even get clone display on my tv (as long as I log in with the svideo cable plugged in). 

But I'm sure that I'm meant to be able to do something in the screen and graphics preferences menu. But no, whilst I can see I've got a cloned display, this menu says that I've got no second display plugged in.

Can anyone offer any help? 

The driver seems to be the intel modesetting driver, I tried to enable the i810 one, but it doesn't seem to save the settings for me.

---

### Post by cayhorstmann on 2007-10-21
I have a similar problem. Some friendly soul suggested this command (in a terminal)

xrandr --output LVDS --auto

That worked like a charm at home. I'll try it with a projector at work next week when I have to give a lecture. 

I complained about the sorry state of affairs on Launchpad, and one of the developers said that they didn't get the Screens and Displays tool up to snuff in time. So, xrandr may be your friend until the next release.

---

### Post by dysphasi on 2007-10-23
Thank you for the advice, unfortunately that line caused my tv screen to flicker but nothing else, no picture was displayed. Are there any other options with vthat line I could try?

---

### Post by dysphasi on 2007-10-23
Well, I changed LVDS to TV and it produced a cloned screen on my tv, at least I don't have to log out and back in now. 

2 Problems though,
1) Ideally I'd like an extended dual screen setup...ie.. move the mouse to the right and it'll move onto the tv screen

2) If I do use a cloned screen, can I stop the ubuntu panel shrinking to fit the smaller width of the tv screen? And is there a way to make sure programs like VLC detect the tv as a second screen and display a full screen picture on the tv but not the laptop (as an overlay I guess).

---

### Post by dysphasi on 2007-10-23
Well, I've done a bit of looking around on xrandr and from what I gather, I'd have thought the following would have worked:

```
 xrandr --output LVDS --left-of TV --auto 
```

However, rather frustratingly all I get is the following,

```
 xrandr: screen cannot be larger than 1280x768 (desired size 2304x768) 
```

What am I doing wrong, and any tips on how to correct it?

---

### Post by dysphasi on 2007-10-23
:lolflag: This does seem to be a bit of a one man conversation doesn't it? Sorry people!

Ok, another step closer, I can get an extended display ALMOST (:mad:) as I want.

This is what I've had to do so far:

(1) In the terminal type,
```
 sudo gedit /etc/X11/xorg.conf 
```

(2) Go to section "Screen" and then to SubSection "Display"

(3) Change,
```
 Virtual	1280	768 
``` 
to 
```
 Virtual	2304	768 
```

(4) Save the changes and return to the terminal.

(5) Type,
```
  xrandr --output TV --right-of LVDS --auto 
```

(6) Et voila!...my TV is an extension to the right of my laptop screen :guitar:

Only problem....
My Ubuntu panel always wants to reside on the TV monitor and not on my laptop screen!!!! #-o

What can I do? Sure I can drag it over, but the same thing happens again if I switch off the TV and set it back up again, which is just a mite frustrating :mad: :(

---

### Post by dysphasi on 2007-10-23
Well, continuing with the one-man-conversation milarky, I do believe I've got it!! 
A big thanks to [color=blue]**cayhorstmann**[/color] (see above) and [[color=red]**tschneiter**[/color]](http://ubuntuforums.org/showthread.php?t=573484&page=2) whose posts I eventually found :)

Basically it seems that xrandr automatically sets the extended display as the primary, so I needed to type the following into the terminal:

```
gconftool --type int --set /apps/panel/toplevels/top_panel_screen0/monitor 1
```

Sooo..... following tschneiter's excellent instructions I was then able to do the following to get this all automated in a simple script:

(1) In the terminal enter: 
```
sudo gedit /usr/bin/toggle-tv.sh
```

(2) Enter the following script:
```

#!/bin/bash
XRANDR_OUT=`xrandr -q`
if echo "$XRANDR_OUT"|grep -q 'TV connected'; then
echo 'Detected TV connected';
if [ `echo "$XRANDR_OUT"|grep '*'|wc -l` -gt 1 ];then
echo 'Turning off TV';
xrandr --output TV --off
else
echo 'Turning on TV';
# set the external to be outside
xrandr --output TV --right-of LVDS --auto
# get the panels back where they ought to be
gconftool --type int --set /apps/panel/toplevels/top_panel_screen0/monitor 1
fi
else
echo 'No TV connected!';
#turning off just incase
xrandr --output TV --off
fi

```

(3) Save and return to the terminal, and to make the script executable enter:
```
sudo chmod +x /usr/bin/toggle-tv.sh
```

(4) All done, all that's left to do is fire up the script in the terminal,
```
toggle-tv.sh
```
....and you're done! :guitar:

The script rather conveniently checks if a connected tv is turned on in dual display mode. If it is, it'll turn the tv-out off. If not, the tv-out will be turned on and set as an extension to the right of the laptop display, with the gnome menu properly residing in its rightful home on the laptop screen :popcorn:

---

### Post by veloce on 2007-10-25
Would you mind posting your full xorg.conf?

I have a similar set up but randr refuses to run - I just get an error when I run xrandr.  I tried adding randr as a module in xorg.conf but x failed and loaded a std vga driver instead of "intel".

If I can copy your system setup, I may be able to get somewhere.

---

### Post by veloce on 2007-10-25
In the spirit of this thread, I'll reply to myself.  I used the (rather extreme) method suggested elsewhere of uninstalling mesa and xorg and reinstalling the ubuntu-desktop.  Worked a charm.

I have now followed these instructions and got dual head working again.  

For some reason only the top menu bar moved back to my LVDS, I'll need to do some research to move the bottom bar across too.

Thanks heaps for the script, I'll be calling it on boot to determine if the external monitor is connected.

Cheers

---

### Post by dysphasi on 2007-10-26
No probs, as I said though, I found it all out in other threads....eventually!

The script will only move the top panel because it's the only one it tells the computer to move. What you need to do is add additional lines for any other panels you use.

To work out all the lines you need to add, first ensure your additional screen isn't plugged (and all your panels are shown as you want on your laptop screen), then from a terminal is type:

```
gconftool --all-dirs /apps/panel/toplevels
```

For example, if I type that script in I might get:

```
 
/apps/panel/toplevels/[color=blue]top_panel[/color]_screen0
/apps/panel/toplevels/[color=blue]bottom_panel[/color]_screen0

```

As you can see (I've highlighted the important bits in blue), this is telling me that I have two panels: top_panel and bottom_panel.

If I were to plug the tv in and run:
```
xrandr --output TV --right-of LVDS --auto
```
Since xrandr sets the additional screen, my tv, to the primary screen, the tv now becomes screen0, and the laptop (LVDS) becomes screen1. 

Both of the panels would subsequently run over to the tv screen (pesky blighters).

To get them back we use:
```

gconftool --type int --set /apps/panel/toplevels/[color=red]**YOUR PANEL GOES HERE**[/color]_screen0/monitor 1

```

So using the example above I would thus need to add two lines to my script as follows:
```

gconftool --type int --set /apps/panel/toplevels/[color=blue]top_panel[/color]_screen0/monitor 1
gconftool --type int --set /apps/panel/toplevels/[color=blue]bottom_panel[/color]_screen0/monitor 1

```

Hope this is of some help, sorry if it's patronising...or indeed confusing ;)

---

### Post by dysphasi on 2007-10-26
If anyone can help however, one artifact of moving panels about like this is that unless both your monitors are the same width, the buttons get messed about with.

I think what's happening is that:
1) Panel is moved from wide laptop screen to narrow TV
2) Panel shrinks to fit TV and buttons get squashed together to fit
3) Panel is moved back to wider laptop
4) Some buttons go back to where they should be, others just stick around where they were on the TV, yet others go for a wonder and go to wherever they want.

Can anyone help me stop this? I've tried locking to panel and not, and a mix of both, nothing works.

What needs to happen is that all buttons left of center need be alligned relative to the far left of the screen and all buttons right of center need to alligned relative to the far right of the screen.

Is there a way to tell them to do this? Or is this a flaw in the gnome panel system?

---

### Post by honeydew on 2007-10-26
I have been trying to figure this out for a few days.. Im going to give this a go tonight.. Ill let you know how it goes.. thanks for the info

---

### Post by andrei.kouznetsov on 2007-11-01
Is it possible to have two independent screens, not a one long screen composed of two displays "glued" together? I can't get it work using the new driver.
It was easy to do with i810.

---

### Post by veloce on 2007-11-03
> **andrei.kouznetsov said:**
> Is it possible to have two independent screens, not a one long screen composed of two displays "glued" together? I can't get it work using the new driver.
It was easy to do with i810.

No, not anymore. Reference:

[http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)  See VI:5

---

### Post by Hyperion_1984 on 2008-01-28
Strangely, when I move back to one monitor, some of my panel applets freeze. I still can use them, but the give outdated info. For example, my window list doesn't update itself and the clock is stopped. Did any one experienced such nuisance?

---

### Post by dysphasi on 2008-01-29
The panel really doesn't seem to like being moved about/resized, it's not v stable at all for me. 

The developers really need to get this dual/extended screen thing sorted for hardy, as stands I'm finding myself using windows more and more (eeek!).

---

