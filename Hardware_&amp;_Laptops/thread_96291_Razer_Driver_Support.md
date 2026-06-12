---
title: "Razer Driver Support"
date: 2005-11-28
forum: Hardware &amp; Laptops
---

### Post by Tonni on 2005-11-28
hi,

is there a way to emulate the driver for the razer diamondback mouse so that the mouse-speed works as it would do in windows?
will wine or cedega manage to make it run? is there an other way?

thx
Tonni

---

### Post by KingBahamut on 2005-11-28
I dont think wine or cedega will do that as you wish it. I have my Razer configured with the button conf proper for all the buttons, with no accel.

---

### Post by Majlo on 2005-11-29
[QUOTE=KingBahamut]I dont think wine or cedega will do that as you wish it. I have my Razer configured with the button conf proper for all the buttons, with no accel.[/QUOTE]

Hi..

Could you post mouse section from your xorg.conf please ? I also have this mouse.
Thank you

---

### Post by fastb on 2005-12-15
I have the same mouse and I would like to know that too.

---

### Post by zi99y on 2005-12-25
I just got this mouse for Christmas and am wondering the same thing! Any hints would be appreciated

---

### Post by ShapeShifta on 2006-01-01
Yea, I got my razer copperhead 3 days ago and would like any info on how to set it up. I tried once already and got bad results (Gnome wouldn't even load up). :cool:

---

### Post by Pekkalainen on 2006-01-03
Heres my xorg.conf settings for my Diamondback:
```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "7"
        Option          "ZAxisMapping"          "6 7"
        Option          "Resolution"            "1600"
EndSection

```

and change xmodmap to:

```

xmodmap -e "pointer = 1 2 3 6 7 4 5"

```

I dont remember how to make the xmodmap stuff permanent: [www.google.com](www.google.com) :)

Copperhead users might wanna change Resolution to 2000 ;)

---

### Post by stoeptegel on 2006-01-05
Thank you, this is the first code that actually worked on my copperhead.:D

Crap, the wiki only describes howto get the xmodmap configuration running automated on gdm. Someone knows howto do this in kdm?
Thanks.

---

### Post by Shaggman on 2006-01-10
I have Razer Diamondback, but the scroll does'nt work. Is there anyone who knows what I should do?:confused:

---

### Post by stoeptegel on 2006-01-24
@Shaggman
You must run this command in bash as user after you boot into kde, that *should* work.
```
xmodmap -e "pointer = 1 2 3 6 7 4 5"
```

There is a wikipage for this to make automated under GNOME, but for KDE i don't now cause the folders are missing. Personally i just wrote this code on a paper and use it that way

---

### Post by Sp@z on 2006-01-24
[QUOTE=KingBahamut]I dont think wine or cedega will do that as you wish it. I have my Razer configured with the button conf proper for all the buttons, with no accel.[/QUOTE]

I would also like to see your config as I couldn't get the one on this page to work..........Thanx!

---

### Post by Sp@z on 2006-01-29
[QUOTE=Pekkalainen]Heres my xorg.conf settings for my Diamondback:
```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "7"
        Option          "ZAxisMapping"          "6 7"
        Option          "Resolution"            "1600"
EndSection

```

and change xmodmap to:

```

xmodmap -e "pointer = 1 2 3 6 7 4 5"

```

I dont remember how to make the xmodmap stuff permanent: [www.google.com](www.google.com) :)

Copperhead users might wanna change Resolution to 2000 ;)[/QUOTE]

I must say I couldn't get this to work a couple of different times.............I crashed Kubuntu last night , reinstalled and it freekin works this time.....very stange imma post my config.........


##Section "InputDevice"
##    Identifier     "Configured Mouse"
##    Driver         "mouse"
##    Option         "CorePointer"
##    Option         "Device" "/dev/input/mice"
##    Option         "Protocol" "ImPS/2"
##    Option         "Emulate3Buttons" "true"
##    Option         "ZAxisMapping" "4 5"
##EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "7"
        Option          "ZAxisMapping"          "4 5"
        Option          "Resolution"            "2000"

as you can see I just commented out the old section then added the razer section proved earlier in this post......... changed the zaxismapping to "4 5" and changed the resolution to 2000. Seems to work great too! I don't even have to manually enter xmodmap -e "pointer = 1 2 3 6 7 4 5" into the  console.

I swear I hope this helps someone!

Also some devolpers are working on drivers for the Razer Copperhead mouse. I lost the websight but when I find it I will post it!

---

### Post by Zillion on 2006-04-04
This driver works fine for my Copperhead :)

I found [here]("http://ubuntuforums.org/showthread.php?t=65471&highlight=xmodmap") how to make the xmodmap permanent.

In short :

open console and
```
gedit ~/.Xmodmap
```

enter in that (for me empty new) file
```
pointer = 1 2 3 6 7 4 5
```

run xmodmap to apply these settings
```
xmodmap ~/.Xmodmap
```

> If this is the first time you created a .Xmodmap file then next time you log into gnome it will ask you if you want to automatically load it, add the file and click Ok if this happens.

---

### Post by Zillion on 2006-04-21
Hmm switching between Windows XP and Ubuntu gives me the cold boot in Linux one out of two times... so the mouse doesnt do anything at all. Switching between usb ports and restarting the pc after shut down sometimes helps, not allways. This really pisses me off, anyone got a solution for this?

---

### Post by zi99y on 2006-04-21
Not sure what you mean by "the cold boot in Linux", can you elaborate on the problem?

Have you tried using another mouse? I doubt that it's specific to your copperhead

---

### Post by Zillion on 2006-04-23
[QUOTE=zi99y]Not sure what you mean by "the cold boot in Linux", can you elaborate on the problem?

Have you tried using another mouse? I doubt that it's specific to your copperhead[/QUOTE]

Yes it is specific to the copperhead mouse. It means the mouse doesnt work at all. And its a very known issue for windows users who use the old drivers, however since I updated the mouse firmware and windows drivers to the newest version I have no problem anymore in Windows. If I only boot in Ubuntu it works ok, but as soon as I boot in Ubuntu after I have been in Windows, even when the pc has been shut down, very often the mouse wont work and I need much reboots trying different usb ports before the mouse gets working.

I read somewhere that linux gets confused by this mouse thinking this is a keyboard instead of a mouse. However the solution was not presented and I cant find anymore where I read it.

---

### Post by stoeptegel on 2006-05-14
Looks like someone made an editor for the copperhead :)
[http://www.razerblueprints.net/](http://www.razerblueprints.net/)

I have not tested it myself, so be carefull when you try it.

---

### Post by karlsson88 on 2006-06-10
[QUOTE=stoeptegel]@Shaggman
You must run this command in bash as user after you boot into kde, that *should* work.

```
xmodmap -e "pointer = 1 2 3 6 7 4 5"
```

[/QUOTE]


What "line" do i use to get the button where my thumb is to be "back/forward" in mozilla when i press it? is it like xmodmap -e "pointer = 1 2 3 6 7 4 5"  ??

---

### Post by dk_pa on 2006-06-26
Has anyone tried that Copperhead steup util?  Can you post the Xorg info it made?

---

### Post by s3ppel on 2006-07-05
[QUOTE=karlsson88]What "line" do i use to get the button where my thumb is to be "back/forward" in mozilla when i press it? is it like xmodmap -e "pointer = 1 2 3 6 7 4 5"  ??[/QUOTE]

I am interested in this as well... did u find a solution and if so, could you tell us please?

EDIT: Somehow it just works now in Firefox, however I can now longer scroll with the weel. Though i didn't change anything... strange.

---

### Post by s3ppel on 2006-07-06
ah, finally got it to work! For my Razer Diamondback I needed neither Xmodmap nor NMWheel. I just changed my /etc/X11/xorg.conf section to this:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option          "Buttons"               "7"
        Option          "Resolution"            "1600"
	Option		"ZAxisMapping"		"4 5"
	Option		"ButtonMapping"		"1 2 3 6 7"
	Option		"Emulate3Buttons"	"true"
EndSection

thats all, and it works like a charm!

---

### Post by struess on 2006-07-09
aye, s3ppel's little switch worked for me (with razer diamondback), too.. the /etc/X11/xorg.conf file was the only thing i messed with.  the two left thumb buttons become forward and back (in firefox, at least.. don't seem to do much for nautilus), and the right ones scroll up and down.

is there a way to further customize those buttons?  like firefox, the "xev" event tester shows that right-side buttons 4 and 5 are the same as the up-down scroll wheel.. how can you specify their functions?

---

### Post by dk_pa on 2006-07-10
This has been where I've been at for awhile.  I really am not sure how to make the button on the right side do anything other than scroll.  I dont really use it much so it doesn't bother a whole lot but it would be nice to know how to do that...which is really the only reason why I even bothered with teh Razer-Tool gui tool (or at least tried to get it to work).

---

### Post by karlsson88 on 2006-07-10
no i have don't find any solution for this yet.

---

### Post by pernambuco on 2006-07-16
this conf work very good:

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Resolution" "1600"
Option "Buttons" "7"
Option "Device" "/dev/psaux"
Option "Name" "Razer Diamondback Optical Mouse"
Option "Protocol" "auto"
Option "ZAxisMapping" "4 5"
Option "ButtonMapping" "1 2 3 6 7"
Option "Emulate3Buttons" "true"
EndSection

NO need xmodmap command.

Sorry for my bad english & good chance!!!

---

### Post by digi421 on 2006-08-20
I couldn't even install that tool: Dependancy not satisfiable: libusb-0.1-4 though I do have that one.
And my Copperhead is working, I just want to get the left thumb buttons to work like in XP (forward and back).

---

### Post by foureight84 on 2006-12-16
very helpful thread. thanks guys

---

### Post by crav on 2007-04-22
I tried the first method any my buttons were all mapped strangely. The right side top button became left-click, for example.


Any other ideas?

---

### Post by melat0nin on 2007-05-03
These mappings don't work for me either.  One of them did work, until Beryl screwed up on me and my xorg.conf file was changed about a million times.  Any ideas why? Can't live without my scroll wheel!!

---

### Post by Sockerdrickan on 2007-06-04
RAZER DIAMONDBACK:


Section "InputDevice"
    Identifier "Configured Mouse"
    Driver "mouse"
    Option "CorePointer"
    Option "Resolution" "1600"
    Option "Buttons" "9"
    Option "Device" "/dev/psaux"
    Option "Name" "Razer Diamondback Optical Mouse"
    Option "Protocol" "auto"
    Option "ZAxisMapping" "4 5"
    Option "ButtonMapping" "1 2 3 6 7 8 9"
    Option "Emulate3Buttons" "true"
EndSection


OK, now button 4 & 5 work, but what about the 2 on the right side guys?

---

### Post by Leafer on 2007-07-25
> **s3ppel said:**
> ah, finally got it to work! For my Razer Diamondback I needed neither Xmodmap nor NMWheel. I just changed my /etc/X11/xorg.conf section to this:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option          "Buttons"               "7"
        Option          "Resolution"            "1600"
	Option		"ZAxisMapping"		"4 5"
	Option		"ButtonMapping"		"1 2 3 6 7"
	Option		"Emulate3Buttons"	"true"
EndSection

thats all, and it works like a charm!

Since this managed to crash X on boot for me I feel the need to point out that you'll also have to change the ServerLayout section as well. Mine had Mouse0 which should be changed to Configured Mouse. Changed section is in bold.

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "**Configured Mouse**" "CorePointer"
EndSection
```

---

### Post by syn` on 2007-08-12
What about lowering the sensitivity? I could honestly care less about the buttons. I'm an avid gamer, I purchased the mouse for the DPI (Diamondback; never got around to upgrading). The default mouse sensitivity is just WAY too high. 

Any ideas on how to lower the sensitivity? Sorry if it's a.. dumb question, brand new to Linux.

---

### Post by AbtZ on 2007-09-12
> **syn` said:**
> What about lowering the sensitivity? I could honestly care less about the buttons. I'm an avid gamer, I purchased the mouse for the DPI (Diamondback; never got around to upgrading). The default mouse sensitivity is just WAY too high. 

Any ideas on how to lower the sensitivity? Sorry if it's a.. dumb question, brand new to Linux.

System > Preferences > Mouse

On the "Motion" tab you will be able to adjust sensitivity and acceleration settings.

---

### Post by pfx on 2007-10-16
> **s3ppel said:**
> ah, finally got it to work! For my Razer Diamondback I needed neither Xmodmap nor NMWheel. I just changed my /etc/X11/xorg.conf section to this:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option          "Buttons"               "7"
        Option          "Resolution"            "1600"
	Option		"ZAxisMapping"		"4 5"
	Option		"ButtonMapping"		"1 2 3 6 7"
	Option		"Emulate3Buttons"	"true"
EndSection

thats all, and it works like a charm!

Ok, I just got this mouse and spent some time with this config. I've figured out the button assignments:
1: Left Click
2: Right Click
3: Middle Click (click scroll wheel)
4: Scroll Up
5: Scroll Down
6: Left Forward
7: Right Forward

Now, I'm more used to having the left forward be forward and left backward in backward instead of the right forward being backward (confusing, no?). Changing the Buttons to 9 didn't help. How do I use the backward side buttons?

---

### Post by MrSpiffdifilous on 2007-10-25
Ok I finally got everything working while reading this thread. I have a Razer Copperhead. heres my config.

> Section "InputDevice"
    Identifier "Configured Mouse"
    Driver "mouse"
    Option "CorePointer"
    Option "Device" "/dev/input/mice"
    Option "Protocol" "ExplorerPS/2"
    Option "Buttons" "7"
    Option "ZAxisMapping" "4 5"
    Option "ButtonMapping" "1 2 3 4 5 6 7"
    Option "Resolution" "2000"
EndSection

> xmodmap -e "pointer = 1 2 3 4 5 6 7"

and thats it. Scroll works, left and right click and the side buttons. well, not the back side buttons but the front side buttons work just fine. hope this helps! Maybe addings buttons 8 and 9 will add functionality to those buttons. Not sure what they would do though. I'll try this and post results.

---

### Post by MrSpiffdifilous on 2007-10-25
just tried to add 8 and 9... not so hot. They don't do anything, the rest of the buttons work just fine but the two buttons toward the back on the sides are still without function. anyone know a way of binding them to actions or something?

---

### Post by MrSpiffdifilous on 2007-11-11
after rebooting Ubuntu non of the side buttons worked again. I reverted to my previous settings from my first post and still no change... any ideas?

EDIT: All set I just had to reboot for the settings to change again heres my Xorg.conf section.

> Section "InputDevice"
        Identifier "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device" "/dev/input/mice"
        Option          "Protocol" "ExplorerPS/2"
        Option          "Buttons" "7"
        Option          "ZAxisMapping" "4 5"
        Option          "ButtonMapping" "1 2 3 6 7"
        Option          "Resolution" "2000"
        Option		"Emulate3Buttons"	"true"
EndSection

---

### Post by cancertoast on 2007-11-29
So does anyone know if this will work with the new Lachesis?

---

### Post by Wamoc on 2008-01-11
I have tried all the configurations in this thread for my diamondback mouse, and I still have a problem of it not doing anything with the two buttons on the left side. Here is my current section of my xorg.conf file

Section "InputDevice"
       Identifier "Configured Mouse"
       Driver "mouse"
       Option "Name" "Razer Diamondback Optical Mouse"
       Option "Device" "/dev/input/mice"
       Option "CorePointer"
       Option "Protocol" "auto"
       Option "Resolution" "1600"
       Option "Buttons" "7"
       Option "Protocol" "ExplorerPS/2"
       Option "ZAxisMapping" "4 5"
       Option "ButtonMapping" "1 2 3 6 7 8 9"
       Option "Emulate3Buttons" "true"
EndSection

Any help would be greatly appreciated.

---

### Post by Crinos512 on 2008-02-05
> **cancertoast said:**
> So does anyone know if this will work with the new Lachesis?

I use this:

```

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "Name" "Razer Lachesis Optical Mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Buttons" "9"
    Option         "Resolution" "4000"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 6 7 8 9"
    Option         "Emulate3Buttons" "true"
EndSection

```

:popcorn:

---

### Post by JD82 on 2008-07-02
The Lachesis works well under Ubuntu, but do not operate the hardware macros configured in Windows: The side buttons function as if they were not configured, for example, the button 5 performs the function Back in Firefox, regardless of the macro configured in the profile from Windows (ALT+F4).

The firmware used is the v1.64.

---

