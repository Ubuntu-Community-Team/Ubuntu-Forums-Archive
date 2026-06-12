---
title: "Toshiba Satellite S2450-201 - Keyboard Problems"
date: 2005-09-29
forum: Hardware &amp; Laptops
---

### Post by Lizzy on 2005-09-29
Hi, i'm a Linux Newbie and i'm facing problems with my keyboard. No matter which distribution installed (tried, SUSE, Debian), my keyboard behaves weird.

Letters just seem to run of like: r turns into rrrrrrrrrrrrrrrrrrrrrrrrrrrr , or when i'm typing something nothing at all happens, it simply stops, or the space-bar turns wild...aso, aso. One might call it moody, jumpy keys :-). Quiet frustrating when chatting with people, cause i constantly have to correct my writing, otherwise noone knows what i want to say.

This has never been an issue under MS XP :confused: ??? I would realy like to sort it out, cause i realy looooove Ubuntu Linux and i'm not willing to turn back to MS ever again, due to other frustrating reasons. So my question is: Is there something i can do, or do i have to live with it. Is it a typical Toshiba-hardware problem?

Would love some answers.  Anyone help a helpless girl? :D 
Thanks Elisabeth

---

### Post by drewbie on 2005-09-29
I had a similar problem in mandrake 10.1 with my keyboard having a mind of its own, although i haven't had the same problem with ubuntu.

unfortunatly i can't remember exactly what it was i did in the xorg.conf file to solve it.

[http://linux.toshiba-dme.co.jp/linux/eng/qa/input/02385.htm](http://linux.toshiba-dme.co.jp/linux/eng/qa/input/02385.htm) might be the problem, if not try googling or linuxquestions.org i think it is a common problem

---

### Post by Lizzy on 2005-09-29
thx for your reply... I had xkbset installed a month ago, but i can't figure out what all that stuff meens, cause i'm a complete idiot when it comes to technical terms.....

when i write xkbset in the command shell, this comes up:
 xkbset
Usage: To set or unset various options:

  xkbset <options>

where <options> may be all or any of (the '-' switches the feature off,
otherwise it is switched on):

To switch the bell on or off:

    [-]{bell|b}

To switch one key to autorepeat or not:

    [-]{repeatkeys <per_key_repeat>|r <per_key_repeat>}

To send a hex mask for all keys to autorepeat or not

    perkeyrepeat <per_key_repeat>

To switch autorepeat on or off, and optionally set the delay before
the first repeat and the interval between repeats (times in milliseconds):

    [-]{repeatkeys|r} [rate <repeat_delay> [<repeat_interval>]]

To switch mousekeys on or off, and optionally set the default
button (whatever that is):

    [-]{mousekeys|m} [<mk_dflt_btn>]

To switch mousekeys acceleration on or off, and optionally set
the acceleration characteristics:

    [-]{mousekeysaccel|ma} [<mk_delay> <mk_interval> <mk_time_to_max>
      <mk_max_speed> <mk_curve>]

To switch AccessX on (so pressing shift five times starts sticky keys
and pressing the shift key down 8 seconds starts slow keys):

    [-]{accessx|a}

To switch sticky keys on or off, and optionally set or reset:
() two keys pressed at the same time stops sticky keys;
() a modifier pressed twice will be locked:

    [-]{sticky|st} [[-]twokey|[-]latchlock]...

To switch on slowkeys, and optionally set the slow key delay (in
milliseconds):

    [-]{slowkeys|sl} [<slow_keys_delay>]

To switch on bouncekeys, and optionally set the time (in milliseconds) for
which if the key is pressed again in that time it will not work:

    [-]{bouncekeys|bo} [<debounce_delay>]

To switch on audible feedback, and optionally set which features
cause the feedback (note [-]feature means that switching
one of the AccessX features on of off causes feedback):

    [-]{feedback|f} [[-]dumbbell|[-]led|[-]feature|[-]slowwarn|
      [-]slowpress|[-]slowaccept|[-]slowreject|[-]slowrelease|
      [-]bouncereject|[-]stickybeep]...

To switch keyboard overlays 1 or 2 on or off:

    [-]{overlay1|ov1}
    [-]{overlay2|ov2}

To select the group wrap type (now what is that)?

    groupswrap {redirect|clamp|wrap} [<groups_wrap>]

What is this?

    [-]ignoregrouplock

To cause some of the key modifiers (like shift, num-lock=mod2, etc)
to not work:

    nullify [[-]shift|[-]lock|[-]control|[-]mod1|[-]mod2|[-]mod3|[-]mod4|
      [-]mod5]...

What is this?

    ignorelock [[-]shift|[-]lock|[-]control|[-]mod1|[-]mod2|[-]mod3|
      [-]mod4|[-]mod5]...



To set the AccessX expire controls:

  xkbset exp <options>

where <options> may be all or any of (<ax_timeout> is the timeout (in
seconds) after which no user activity on X will cause the expiry; '-'
indicates the feature will be switched off, '=' incicates the feature
will be left unchanged, otherwise it will be switched on):

    <ax_timeout>
    [-|=]{bell|b}
    [-|=]{repeatkeys|r}
    [-|=]{mousekeys|m}
    [-|=]{mousekeysaccel|ma}
    [-|=]{accessx|a}
    [-|=]{sticky|st} [[-|=]twokey|[-|=]latchlock]...
    [-|=]{slowkeys|sl}
    [-|=]{bouncekeys|bo}
    [-|=]{feedback|f} [[-|=]dumbbell|[-|=]led|[-|=]feature|[-|=]slowwarn|
      [-|=]slowpress|[-|=]slowaccept|[-|=]slowreject|[-|=]slowrelease|
      [-|=]bouncereject|[-|=]stickybeep]...
    [-|=]{overlay1|ov1}
    [-|=]{overlay2|ov2}
    [-|=]ignoregrouplock

To see the current values of the controls:

  xkbset q

To see the current values of what controls will expire:

  xkbset q exp

To have these values written as a command line:

  xkbset w [exp]

To print this help message

  xkbset [h]



So??? :confused:  What now?? Don't know what to do with that information, do i have to change something here??? Sorry  for my stupid questions... still learning to understand at least a little bit Linux *lol ;)


PS: Would be nice if there was a Simple, understandable, IDIOT-proof HOWTO for this sort of problem, cause i believe i'm not the only one facing this problem!!

---

### Post by drewbie on 2005-09-29
try typing 
xkbset bo 5
this should set the bounce delay to five millisecond (i.e. you have to hold the key down for 1 sec for it to print more letters) hopefully that should solve it, if not type 
xkbset q
this will display your current settings and then post them back here. Alterenativly you could just remove xkbset, i'm not sure that it is really needed.

---

### Post by Lizzy on 2005-09-30
I tried to write xkbset bo 5, but nothing happened.

But when i wrote xkbset q this came up:

:~$ xkbset q
Audible Bell = On
Repeat Keys = On
Repeat Delay = 349
Repeat Interval = 35
Per Key Repeat =
        00ffffffdffffbbf
        fadfffdfffdfe5ef
        ffffffffffffffff
        ffffffffffffffff
Mouse-Keys = Off
Mouse-Keys Default Button = 1
Mouse-Keys Acceleration = Off
Mouse-Keys Acceleration Delay = 160
Mouse-Keys Acceleration Interval = 40
Mouse-Keys Acceleration Time to Max = 30
Mouse-Keys Acceleration Max Speed = 30
Mouse-Keys Acceleration Curve = 500
Accessibility Features (AccessX) = Off
Sticky-Keys = Off
Two Keys Mask = On
Latch to Lock Mask = On
Slow-Keys = Off
Slow Keys Delay = 300
Bounce-Keys = On
Debounce Delay = 5
AccessX Feedback = Off
Use Fixed Pitch Bell = On
Beep when LED changes = Off
Beep on Controls on/off = Off
Beep if Slow/Bounce-Keys about to be turned off = Off
Beep on Slow-Key Press = On
Beep on Slow-Key Accept = On
Beep on Slow-Key Reject = Off
Beep on Slow-Key Release = Off
Beep on Bounce-Key Reject = On
Beep on Sticky-Key Actions = On
Keyboard Overlay 1 = Off
Keyboard Overlay 2 = Off
Groups Wrap Type = wrap
Groups Wrap Value = 1
Ignore Group Lock = On
Nullify Shift = Off
Nullify Caps-Lock = Off
Nullify Control = Off
Nullify Mod1 = Off
Nullify Mod2 = Off
Nullify Mod3 = Off
Nullify Mod4 = Off
Nullify Mod5 = Off
Ignore Lock of Shift = Off
Ignore Lock of Caps-Lock = Off
Ignore Lock of Control = Off
Ignore Lock of Mod1 = Off
Ignore Lock of Mod2 = Off
Ignore Lock of Mod3 = Off
Ignore Lock of Mod4 = Off
Ignore Lock of Mod5 = Off


And Now??
I'm as clueless as before :D

---

### Post by drewbie on 2005-09-30
well, it seems that you have changed the bounce delay to 5 miliseconds, are you still getting the hyperactive keyboard problem? If you are then i suggest you remove the xkbset package, i don't think it is really needed, i have a toshiba and don't have the package installed. to uninstall type

sudo apt-get remove xkbset

if your still having the problems after that then it has nothing to do with xkbset, so you can reinstall it and have another go at trying to find out what the problem is.

---

### Post by Lizzy on 2005-09-30
Hi Drewbie,  thx for your reply... Well, it must be another problem, because the keyboard was freeky before xkbset was installed, also on the other Linux distributions like Suse and Debian. I will uninstall xkbset since it is no use.

I guess it must be a hardware-problem then ! :( 
It freaks me out that i don't know what the problem is...grrrrrr :(

---

### Post by drewbie on 2005-09-30
Well, sorry i cant be anymore helpful, all i can suggest is searching for any similar problems on [www.google.com/linux](www.google.com/linux) , [www.linuxquestions.org](www.linuxquestions.org) and [www.linux-laptop.net](www.linux-laptop.net) might help too.

i'm sure the answer is out there, somewhere at least.

---

### Post by Lizzy on 2005-09-30
Thank u for the links.... well, there was a lad in the linux.laptop forum who installed Mandrake and there seems to be a bug in X... It's not exactly the same toshiba satellite (S203), but i figure the problem might be the same as with mine.

He says-->
Under X, the keyboard driver has a bug. same characterproblem was solved in 2.4.21 kernel.......................


Does that mean i have to download something to do with the kernel???? Oh my god, that's a little bit too much for a girl who barely understands a thing in linux, not to talk about PC's :D :D :D

---

### Post by drewbie on 2005-09-30
type

uname -r 

to get the linux kernel you are using

---

### Post by Lizzy on 2005-09-30
2.6.10-5-386 

That's the one :D

---

### Post by drewbie on 2005-09-30
well then, you are on a 2.6 kernel  so all the problems should be fixed from the 2.4 kernel
try typing
sudo gedit /etc/X11/xorg.conf
and go down until you find :
Section "InputDevice"
Identifier	"Generic Keyboard"
Driver		"kbd"
Option		"CoreKeyboard"
Option		"XkbRules"	"xorg"
Option		"XkbModel"	"pc105"
Option		"XkbLayout"	"gb"
EndSection
add in 
Option "XkbDisable" "on"
with the other options,
save the file, and restart the X server by hitting Control Alt and Delete at the same time
(or restart the computer)
and still see if you still have the problem.
if it all goes horribly wrong then remove the line and restart the computer
which you may have to do from the command line in nano

---

### Post by Lizzy on 2005-09-30
thank u, i will do that... i get back later with a report :D 

You are realy kind trying to help me out. :D 

thank u for your time

---

### Post by Lizzy on 2005-09-30
HEEELP, i believe i screwed it up.... thank lord for my flat-mates PC... i did what u said, but now i can't boot without getting the message that the X server won't start.. I mean how do i get to restart the PC and get my Desktop back? *lol*

This is what i get when i restarted the computer:

I cannot start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?

Yes      No

What now??? *Cryoutloud

---

### Post by drewbie on 2005-09-30
do control-alt-F1 to get to the command line(if your not already there) and use nano to remove the extra line, control-o saves the file and control-x exits nano i think (the commands are listed at the bottom) and then type startx to get back the gui

---

### Post by Lizzy on 2005-09-30
OK... nano is up...and how do i get the file there??

Jesus... do i learn a lot today..*lool

---

### Post by drewbie on 2005-09-30
well, get back out of nano by typing cntl-x and then type

nano /etc/X11/xorg.conf

edit the file, do control-o and then control-x,

well, at least your learning

---

### Post by Lizzy on 2005-09-30
But there's nothing to edit, since there is nothing on the screen... i don't even know how to read that file... cause it's all bllack and on top grey...

GNU nano 1.2.4       File: /etc/x11/xorg.config


and down there are a lots of shortcuts of what to do...

But how to edit a file when there is no text

i will never ever mess in a command shell gaian *looool*

But it's fun... eventhough i', quite sweaty now...ooohhh..spooky

---

### Post by drewbie on 2005-09-30
i think you have just missed that the X11 has a capital X,

also make sure that you type sudo as well
i.e.
sudo nano /etc/X11/xorg.conf

the word at the bottom tell you the commands that are avaliable to you and the key combinadion to press to get them the ^ stands for the control key

remember, the command shell is your friend readly

---

### Post by Lizzy on 2005-09-30
OK... file edited and saved then there stands: File Name to Write: /etc/X11/xorg.conf... but can't exit with ctrl X.. do i have to press ctrl T ( To Files)??? Or simply press Enter and then ctrl X....???

---

### Post by drewbie on 2005-09-30
yes, hit enter first to confirm the file write, then it will take you back to the file from which you can exit by control-x

then you will be back at the command line, then type 

startx

to start the x server, and it then should all be back the way it was

---

### Post by Lizzy on 2005-09-30
yihaaaaaaaa, it feels good to be back :D :D :D 
It worked out well. Thx ever so much, drewbie...that was fun , allthough i almost peed my pants ;) 
And who knows, i might become a real "linux nerd", just by hanging around in this forum, asking stupid questions, testing and experimenting, screwing up and fixing things with the help of good lads like u :D 

Cheers
Next lesson please... just kidding :D :rolleyes:

---

### Post by drewbie on 2005-09-30
importantly;

DON'T PANIC

there is almost always a solution, try fiddling arround with settings until you find one that works, don't be afraid to screw the system up (provided you do backups first :) ) there is always a way to fix things. its through mistakes that most people learn how their computer works (like me).

when you do find out how to solve your problem just make sure that you tell everyone eles with similar problems

---

### Post by Lizzy on 2005-09-30
thank u drewbie, i'll keep that in mind :)  .
I've learned quite a lot in this forum. My problem is that i don't understand all the technical terms. When someone says do this and do that, i usaly don't get it, cause i lack the simple understanding of software and hardware (like many girls ;)  )

I haven't been a brilliant Windows XP user eighter. But i had to get ridd of MS due to constant viruses and other issues. I'm happy i did it, but it was a jump into cold water. But cold water can be useful.. it's refreshing and wakes u up ;) 

One day i'll figure out what's wrong with my keyboard...odd thing now since i'm writing is that none of the keys behaves weird anymore...well, we'll see for how long!

---

