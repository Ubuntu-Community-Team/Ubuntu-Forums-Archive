---
title: "Wacom Tablet + Expresskeys working tutorial"
date: 2007-09-17
forum: Hardware &amp; Laptops
---

### Post by gali98 on 2007-09-17
(UPDATE) For Gusty Please go here....
[http://ubuntuforums.org/showthread.php?t=619967]("http://ubuntuforums.org/showthread.php?t=619967")

Okay this is a new updated tutorial with a bit more organization&#8230;

_**About this tutorial...**_
Okay here we go. This is sort of a mini tutorial that sort of brings together a lot of posts so you can get this working. I am doing this because There is not a real new tutorial that I know of, and I wanted to help new users (like myself) to be able to do this. I will explain things as thoroughly as possible so sorry to all you linux-heads. This all started from a post about the tablets and I didn't want to divert the topic.
[http://ubuntuforums.org/showthread.p...ighlight=wacom](http://ubuntuforums.org/showthread.p...ighlight=wacom)
[B][U]
Some Notes about this tutorial:[/U][/B]
I use a Graphire4 so some of this may not apply, but it should work all around.
As far as I know, the Bamboo is not completely implemented yet and expresskeys does not work at all, but this is just my guess as I have not tested it. But don't worry, it shouldn't be long.
I'm pretty new to Linux and wanted this to be as explanatory as possible, so it may get tedious in some places. Please bear with me.
[B][U]
Installing Expresskeys on Ubuntu Feisty 7.04 to enable pad support[/U][/B]

First make sure you have the newest wacom-tools and xserver-xorg-input-wacom packages installed.(I think they come with feisty but try to install them anyway.) Second make sure you have build-essential, xorg-dev, and libc6-dev and their dependencies installed. (just use apt-get or synaptic to install the three. Of course the dependencies will be installed with it.) Now download expresskeys from
[http://freshmeat.net/projects/wacomexpresskeys/](http://freshmeat.net/projects/wacomexpresskeys/)
extract the tar.gz where ever and cd into it. Do the basic


```
./configure
make
sudo make install
```

now open your xorg.conf

```
sudo gedit /etc/X11/xorg.conf
```

(I suggest backing it up first because it caused me some pain when it messed up and x wouldn't start)
and put this in with the rest of the "wacoms"



```
Section "InputDevice"

Driver "wacom"

Identifier "pad"

Option "Device" "/dev/input/wacom" 

Option "Type" "pad"

EndSection
```


and put this in the Server Layout part



```

InputDevice "pad"
```

okay save that and restart x (CTL+ALT+Backspace)
and log back in

open up that terminal


```
expresskeys -d
```

that starts up the Daemon.
That will let you use the 3 buttons on the pad. They are shift scroll and alt by default. You can change that by editing /home/yourusername/.expresskeys/yourtablet.conf or something close to that.
[U][B]
PressCurve[/B][/U]

Presscurve is to change to curve of the pressure(obviously that's the best way to explain it) as for how it works here it goes...
Okay basically it designing a belzier curve. You have two set points: (0,0) and (100,100)
The four values you choose define the support points. i.e. where you have your four values of presscurve:
"x1,y1,x2,y2"
(x1,y1) is your support point for the set point (0,0) and (x2,y2) is the support point for (100,100)
Therefore you can set the curve of this belzier curve however you want. If you had
Presscurve "0,0,100,100"  this would give you a straight line and even pressure whereas
Presscurve "0,75,25,100"  would give you a very steep curve and a soft pressure feel and
presscurve "75,0,100,25"  would give a very shallow curve and a firm pressure feel. You'll have to experiment to find how you really want it.

_**Scroll Fix**_

Make a file named something useful i.e. wacominversion or whatever..


```

#!/bin/bash
xsetwacom set cursor RelWUp 5
xsetwacom set cursor RelWDn 4
xsetwacom set pad RelWUp 5
xsetwacom set pad RelWDn 4

```
put that in a folder named .wacom in your home folder.
okay now make another file named expresskeysstart or whatever

```


#!/bin/bash
expresskeys -d
```

Put this in the same place. This will start expresskeys as a daemon. See below for how to run it at startup.

**_Cursor Speed_**

You need to put this in your xorg.conf under the "cursor" InputDevice section.

```
Option "Speed" "Rspeed"
```
Where Rspeed is the speed you want. 1.0 is default. 
Higher than 1.0 = Faster
Lower than 1.0 = Slower
Don't put it too close to 0 are some wierd bugs occur.

[U][B]
WacomTools and other helpful tools[/B][/U]

xev - This is a very helpful tool in discovering keycodes.
Just run that command and any key you press will be shown in the command line.

wacdump and xidump - These are both tools to monitor your pad. You can use these to check what keys your pad is sending.

xprop - this is useful for identifying program records for later use with expresskeys. Use
"xprop | grep WM_CLASS | cut -d ',' -f2" for easy usage.

xsetwacom - a very useful tool that sets what your tablet sends the xserver. This is covered below.

_**Xsetwacom**_

This is the command to use to bypass expresskeys. This was used above to correct the scroll.
There are many uses for it. I will try to list all the helpful commands.
xsetwacom -h  This displays the help blurb.
xsetwacom list or xsetwacom list dev  This displays the available events. i.e. pad, stylus, cursor, pad, etc...
xsetwacom list param  This lists all available parameters for each event i.e. button1, button2, RelWUp, RElWDn, etc... and at the bottom it shows how to set up these modifiers.

xsetwacom list mod   This list all special modfiers such as SHIFT, CTL, etc... And also it list special keys such as space, backspace, F1...

xsetwacom get [dev_name] [param]  i.e. xsetwacom get pad button1   This would return what button1 on the pad is set as.   This command is used to find what command a current param is set to.

xsetwacom getdefault [dev_name] [param]  This gives the default value for the specified param.
xsetwacom set [dev_name] [param] [value]  This is used to set the value for a param. This can be a number of things.
If the value was set to a button such as "button 1" or "dblclick 1" or even 5 (without the quotes) then then when pressed this param would return what button one does on your computer.
To set it as one in the list of mods then you would write "core key mod" such as "core key F1" You can do multiple keys.
Then you can set it to return a key "core key /key" such as "core key /W" would write W.
To do a string write "core key quotedbl string here quotedbl" That would return string here.
Note for values with "" you must include them when setting the keycode.

_**How to edit the Expresskeys Configuration File**_

This file is a lot friendlier than xsetwacom but as far as I have been able to try, it lacks some stuff. If you can't get it to work try xsetwacom and see if you can get it to work. One cool thing about this is the special keycodes, especially the Presscurve ones. You can also have a set of keycodes for a certain program.

You will find the configuration file in yourusername/.expresskeys/graphire4.conf1 or someting similar if your tablet is different.

If you mess up your file really bad then just delete it and start expresskeys over again to regenerate it again.

I will go at it section by section.
The first is some information on how to use the file, and what the defaults are for the pad buttons. Do not change these as they affect nothing and can be used for reference later.
Next is about special keycodes of which I will highlight here. Note: Most of this is taken straight form the file.

keycode 999 - Use the value 999 as a keycode to enable stylus mode toggling between
Absolute/Relative mode (this refers to how the cursor works. The mouse is relative and the cursor is absolute.)

keycodes 991, 992, 993, 994, 995, 996, 997 -  Use the values 991 to 997 for simulating mouse buttons 1 to 7.

keycodes 1004, 1005, 1006, 1007, 1008, 1009 - Use the value 1004 to return from a tablet rotation (NONE), 1005 to flip a
 tablet 180 degrees (HALF), 1006 to rotate 90 degrees clock-wise (CW) and
 1007 to rotate 90 degrees counter-clock-wise (CCW). By using 1008 you can
 rotate the tablet endlessly in a clock-wise manner (CW-HALF-CCW-NONE-CW-)
 and 1009 does the same motion counter-clock-wise (CCW-HALF-CW-NONE-CCW-).


keycodes 1001, 1002, 1003 - 1001 will decrease the PressCurve, while 1003 will increase it.
 1002 restores the curve to its default state: "0 0 100 100".

Next is the PressCurve values:

  Values for the stylus 'PressCurve' ie 'sensitivity' can be chosen the easy
 way - copying from how the wacomcpl program writes them, or the hard way -
 by experimenting.. The seven curves picked by wacomcpl are (Soft to Firm):
 1               2               3               4 (default)
 "0 75 25 100" | "0 50 50 100" | "0 25 75 100" | "0 0 100 100"
 5               6               7
 "25 0 100 75" | "50 0 100 50" | "75 0 100 25"


And now the Fun part! Okay now we set all the stuff for each program record.  (okay a brief explanation... Each record i.e. default, gimp, blender... can have its own set of keycodes. You can even add your own which I will show later)

I will go over the default and the rest will follow the same suit.

First we have The ProgramName which here is set to "default"

Next is Stylus1PressCurve and Stylus2PressCurve which are both set to "0 0 100 100"
1 is the normal end and 2 is the eraser. See the PressCurve part of this tutorial above for how to do this.

Next is DelayEachKeycode which is set to 0.0. I recommend leaving it there unless you have special need of it.

Up next is ButtonRepeatAfter and DelayButtonRepeat which are set to 0.5 and 0.1 respectively. These are pretty obvious. The option RepeatLeft or RepeatRight must be set to 1 on the respective button for these options to mean anything.

Next is HandleScrollWheel which is set to 1. This is turn on/off the scroll wheel. No reason to change this.

After that is ScrollWheelUp and ScrollWheelDown which are set to 994 0 and 995 0 respectively. This sets the scroll. Don't change this unless you know what you're doing it for. I'm not quite sure what the zeros do. They are obviously a second keycode. It is probably to say that is the end of that keypress.

Next is LeftButton and RightButton which are set to 50 0 and 64 0 respectively. These obviously set what the right and left buttons do.

And last is RepeatLeft and RepeatRight which are both set to 0. This specifies whether the key should repeat.

_**How to add your own Program Record**_

This is pretty simple. Just paste the default record from the line:

" %%            # <---  ******** BEGIN NEW PROGRAM RECORD *********"

to the line:

"RepeatRight        0    # Switch 1/0 (Press and hold button repeat keys)"

onto the bottom. Next use xprop as shown above to find the record name of the program you want to specify. Put that where default is and then use xev to find the keycodes you want.

_**How to enable all this at startup**_

First of all you should have those files you made up at the top named wacominversion and expresskeys_start or whatever in username/.wacom/
Now make another file in there named wacomstart or something similar. In it put

```
#! bin/bash
/home/username/.wacom/wacominversion
/home/username/.wacom/expresskeys_start
```

with the actual files you created. 
Now save that then go to System>Preferences>sessions
make a new one name Wacom or something useful and for the command put 
/home/username/.wacom/wacomstart
That should do it. And yes you could put all this in one file, but I find it better to do it this way. Don't ask me why...


[U][B]
Some endnotes[/B][/U]
This is my first tutorial, and is definitely not perfect. If you have something you want to contribute or correct or whatever please post or pm me or something. My email is korylp at yahoo dot com if you want to do that.
I hope this helps someone. I know I have learned a lot researching this. I will try to update this whenever some new thing comes out, but I am hard-pressed on time, so Don't expect a whole lot. I want to thank all of the people with mini tutorials and the creators of these programs, y'all (yes, I'm a Texan, get over it.) are great. I guess that is all. Thanks,
Kory

Please note: I am not responsible for you crashing you system. I will try to help to the best of my abilities.

---

### Post by goemonburo on 2008-03-02
This is a great, very useful tutorial...I've wondered if you could add anything about using the Wacom tablet _and_ a mouse simultaneously.  Is that possible?  

In my case, I'd like to use the mouse in my left hand and have the tablet pen in my right.  Can I adjust the "cursor" or "stylus" or "pad" settings in xorg.conf and get both active at the same time?  Or barring that, can I make them hot swappable?  Currently, when I plug in the mouse I have to then go back through Gimp and Inkscape and switch everything to "Disabled" and that's a bit of a pain.

Also, I'm having problems with the Wacom mouse -- the clicks are not particularly accurate and the action is too slow.  Can this be adjusted?

I'm posting here only because I thought perhaps these issues could be added to the Tutorial -- which is very complete as is.  I appreciated your taking the time to spell everything out so clearly.

---

### Post by rylleman on 2008-03-06
Thank you! Your tutorial helped me with the whole installation of expresskeys.
I can't believe not more people have replied to this thread... Anyways, great work.

---

### Post by goemonburo on 2008-03-09
I got the keys to work just fine with the tutorial, but now I'm kind of wondering what's the best way to use them -- just having shift, cntl, alt, and space isn't that useful.  I can hit them on the keyboard if I need to.  I tried setting up a key to be the middle mouse button (so I can easily push a window below the others) but it didn't work...does anyone out there have examples of how to make these keys a useful time-saver?

Also, how do I make modifications to the .expresskeys/intuos3.conf1 file without having to restart X each time?  I've found that X freezes if I make modifications and then play around without leaving X.  Can I "source" the file somehow?

---

### Post by gali98 on 2008-04-11
Okay it has been a long time since I messed with all this stuf. I'm sorry I didn't see this earlier.
I hope the people who posted will see this. Pming me will get me back here faster as I always check my pms.
As far as mouse and pen I don't guess I have your problem. Now actually moving them at the same time will not work. As in having two cursors, but I don't think that is what you're asking.
I can use my pen to draw then move it out of range of the tablet and move the mouse (both my regular mouse or the tablet mouse) and it works.....

When you say plug in the mouse do you mean usb? I have a PS mouse maybe that is the reason. I'm not able to access my computer at this time, but will post later tonight if I can.
As far as the mouse sensitivity I will also post tonight.


On  to the next topic...

What I map to the keys will be different since you have an intuos (lucky :() but basically I map uncommon keys to the buttons (, and .) and the wheel to the two other keys(I can't remember right now. Then I go  into GIMP preferences and map the , and . to scale up and down (the brush) and the scroll wheel to to zoom in and down. This works great for me. 
On the expresskeys editing I don't have that problem. I can change it all I want....
A few tips... 
First right after you change it do ```
expresskeys -r
``` this rereads the file.
if that doesn't work:
Before you change kill the daemon 
```
expresskeys -k
```
change the file
run ```
expresskeys -d
```
If that doesn't work then I don't know... You may have to deal with it. But hardy is coming soon so maybe we won't have to worry about it. I will try and update the tutorial after hardy comes out to reflect any changes.
I'm also beginning to think that some of you problems are because of Intuos. 
My way to do it may not be the best way, but there is no way for me to test it.... (unless you buy me one :))

I will finish this hopefully tonight.... 
Kory

---

### Post by gali98 on 2008-04-11
Taken from the linux-wacom man page:
Option "Speed" "Rspeed"
                   sets the cursor's  relative  movement speed to Rspeed.  The
                   default value is 1.0.  A Rspeed greater than 1.0 will speed
                   up the cursor's  relative movement.  A Rspeed less than 1.0 
                   but greater  than 0 will slow  down the  cursor's  relative 
                   movement. A Rspeed too close to 0 is not recommanded.

How easy.... Hope it helps.... I guess you put it under cursor with the rest of the options.

Kory

---

### Post by ueman on 2008-05-15
hi, meaby this is not the correct post, anyway, i cant configure mi wacom intuos3 into ubuntu hardy, since i upgrated, i cant make expresskeys work, i got this error 

mono64@mono64:~$ expresskeys -d

expresskeys ERROR: Tablet not attached, OR (in case of Cintiq 21UX, Intuos3
and Graphire4) the 'pad' device has not been specified in xorg.conf, OR is
lacking on the command line when using "named devices".

i've found on internet, that i have to change some lines into src-expresskeys/get_device.c, and recompile i, which i've allready did, but nothing, the same problem. anyway the wacom tablet works perfectly with firefox, gnome, but i cant map the pad keys to use it with blender and Gimp. my gimp, its allready configurated, so it's not a gimp problem, i know it's a expresskeys problem, but how to fix it?.

please somebody helpme. if there is a solution there, plese let me know it.

Thanks.

---

### Post by bigdee973 on 2008-05-23
for those with u with hardy heron heres a link of what u have to do...
[http://ubuntuforums.org/showthread.php?p=4774752](http://ubuntuforums.org/showthread.php?p=4774752)

just in case the link is broken what u have to do is download the latest version of expresskeys which is of today 5/23/2008 expresskeys-0.4.1 (the link to get the tar/zip of expresskeys is in the link up there in the first post called "expresskeys" heres the link if its broken just in case...
[http://freshmeat.net/projects/wacomexpresskeys/](http://freshmeat.net/projects/wacomexpresskeys/)
so what u do after u download the tar/zip file is u untar/unzip it into ur home folder...and then u have to is  Change line 462 of the file src-expresskeys/get_device.c from:

 if (xdevice_list[i].use == IsXExtensionDevice) {

 to these two:

 if (xdevice_list[i].use == IsXExtensionDevice ||
     xdevice_list[i].use == IsXExtensionPointer) {

after that, open terminal and copy and paste below...
 
sudo aptitude install xlibs-dev

...this installs the files u need to configure and install express keys...then in terminal...you cd into the directory of the expresskeys folder that u untared/unzipped into your home folder and 

sudo ./configure
sudo make
sudo make install

u restart your computer and then open terminal again and....

expresskeys -d

and ur expresskeys should work play with the strip to see

---

### Post by mallow on 2008-05-25
Hi. I`ve got a problem. Since upgrade to Hardy Heron my Intuos ExpressKeys don`t work right. GIMP just ignores somehow the intuos3.conf1 and ExpressKeys work as default. That`s big issue to me. Beside that, it sometimes stops working and when I try rerun expresskeys deamon, my laptop`s processor starts working 100%. Temperature goes very fast and I have to reboot laptop. What to do? :(

---

