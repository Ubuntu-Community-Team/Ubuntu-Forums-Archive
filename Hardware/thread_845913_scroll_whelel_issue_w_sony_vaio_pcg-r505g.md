---
title: "scroll whelel issue w/ sony vaio pcg-r505g"
date: 2008-07-01
forum: Hardware
---

### Post by littlegreyhell on 2008-07-01
Hello all!

This is my first post and my first time installing a Linux distro, so please be kind :D

I´ve just installed Xubuntu 8.04 on my Sony Vaio PCG-R505GL laptop (1200Mhz 256Mb) and I´m having issues with my scroll wheel.  

When I try to use the scroll wheel to move the space w/in a window (either in a xubuntu app like appfinder and add/remove or using firefox) it will scroll erratically to the bottom of the page and return to the top. If I then try to scroll by manually sliding the bar it will act in the same way.  But if I then hit the middle mouse button, I can manually slide the bar normally.  

I´ve installed Gsymantics Touchpad and manually configured the xorg.conf file to get it working and played around w/ the settings, but haven´t been able to resolve the issue.

I´ve searched the ubuntu help pages and not found any resolution.  Could someone please point me in the right direction?  I eagerly await your replies.  Thank you in advance! :)

---

### Post by littlegreyhell on 2008-07-03
bump

---

### Post by sawdust_prophet on 2008-07-12
I have a similar issue here...running a Toshiba Satellite 2400 w/Xubuntu 8.04, it has a scroll wheel on the touchpad which I have never been able to function.  Any help here would be great.

---

### Post by jippers on 2008-07-30
I've posted with the identical problem with ubuntu 8.04.1.  

My R505GL scrolls erratically in both ubuntu and xubuntu. It was okay though in 7.10.

---

### Post by khaije1 on 2008-08-07
i'm having the exact same problem on my sony pcg-r505gck, which runs quite well aside from this. 

I see that the scrollwheel seems to be disabled by default in hardy but that toggling this option doesn't seem to make a difference.

Has anyone made any progress in fixing, disabling or even just improving this condition?


in my observation it seems like any single scroll wheel event registers as a continuous scroll event. It's out of control but it's not random. A single, in many cases accidental (on my part at least) tap of the scroll wheel will send the page flying to that extreme direction. 

If you try to scroll in the opposite direction to compensate or return to your original place it will continue to go in the opposite extreme. this makes it impossible to return to your original spot and makes many operations frustrating, painful, or impossible.  

I have noticed that a tap click will stop the endless scrolling, almost as if it is distracted or disabled by the related but different input. 

this exact same behaviour has been observed on the two sony pcg-r505 laptops i have access to. This in addition to the fact that other pcg-r505 members reported the exact same behaviour as well as a toshiba owner suggest to me it's not only a hardware problem.

fyi- if i completely avoid the scroll wheel my pc doesn't have this problem and is usable, but it's location and force of habit make ignoring it difficult, additionally many operations and applications require this ability so a fix is needed.

---

### Post by colintivy on 2008-08-07
Hi folks,

While not too close to the earlier posts, I have a similar problem with Hardy and a Genius NetScroll mouse which just does not work. Some very early posts in Archive got near to an explanation but I wonder if there is some common cause? I have not poked around in the innards of Hardy but will value some directions please.

Colintivy:(

---

### Post by jippers on 2008-08-10
I've reverted to ubuntu 7.10 on my PCG-R505GL and this scroll wheel issue is not present. I can scroll to my hearts content.  Still, I would like to use the latest Ubuntu/Xubuntu on this machine.

---

### Post by uncle hammy on 2008-08-11
I can confirm this issue with my Sony Vaio PCG-R505GCP laptop that I am currently in the midst of migrating to Ubuntu Hardy from Windows XP.

---

### Post by patchwillie on 2008-08-14
> **littlegreyhell said:**
> Hello all!

This is my first post and my first time installing a Linux distro, so please be kind :D

I´ve just installed Xubuntu 8.04 on my Sony Vaio PCG-R505GL laptop (1200Mhz 256Mb) and I´m having issues with my scroll wheel.  

When I try to use the scroll wheel to move the space w/in a window (either in a xubuntu app like appfinder and add/remove or using firefox) it will scroll erratically to the bottom of the page and return to the top. If I then try to scroll by manually sliding the bar it will act in the same way.  But if I then hit the middle mouse button, I can manually slide the bar normally.  

I´ve installed Gsymantics Touchpad and manually configured the xorg.conf file to get it working and played around w/ the settings, but haven´t been able to resolve the issue.

I´ve searched the ubuntu help pages and not found any resolution.  Could someone please point me in the right direction?  I eagerly await your replies.  Thank you in advance! :)


Same issue r505es

Someone please help, I had to downgrade to 7x .....

---

### Post by colintivy on 2008-09-11
Hi you lot!

This seem to have got to a dead end. Somewhere I seem to remember a discussion about non-working scroll wheels (that is all that does not work with my Genius Netscroll which is accepted by MS Word etc., as a standard, ie no driver disk.) on an Open Office Writer forum. Can anybody remember where and when?

colintivy

---

### Post by scallopedllama on 2008-09-26
So I just got one of these things yesterday. It's pretty boss, everything works flawlessly in linux... except the jog dial.
I'm actually using linux mint here but it's based offa ubuntu so the fix for you peoples should be the same. The culprit is the sony-laptop module.
If you do a 
```
$sudo modprobe -r sony-laptop 
```
Then the jog dial and function keys magically start working correctly!! 
The only problem is that sony-laptop appears to have been the tool that adjusted the backlight of the monitor.

So the situation is that
sonypi handles the jobwheel and hotkeys accurately, but sony-laptop does not.
and sony-laptop can change the cpu and backlight stuff, but sonypi cannot.

I'ma keep working on this.

---

### Post by scallopedllama on 2008-09-26
Solved.

So the problem was completely sony-laptop. It apparently takes control of the back light before sonypi takes over (explaining why the back light controls didn't work after removing the sony-laptop module).

So you need to add sony-laptop to the modprobe blacklist:
```
$sudo gedit /etc/modprobe.d/blacklist
```
Then add the following line to the end of the file:
```
blacklist sony-laptop
```

Now you can use your function keys and jog wheel in a predictable manner.
scolling up and down are fine and if you click the wheel it will do a middle click.
Just an interesting note: the unmarked key next to the sun key increases the back light for me.

There are bound to be some bug reports for this somewhere that should be closed I'm sure. And this is an open bug for sony-laptop since that utility is trying to replace sonypi.

---

### Post by RtVD on 2008-10-04
Thanks so much, this has been driving me crazy (I just installed 8.04 on an old sony PCG-R505DL last night).

scrolling accidentally on the background made the machine unusable.

-RtVD

---

### Post by patchwillie on 2008-10-12
> **scallopedllama said:**
> Solved.

So the problem was completely sony-laptop. It apparently takes control of the back light before sonypi takes over (explaining why the back light controls didn't work after removing the sony-laptop module).

So you need to add sony-laptop to the modprobe blacklist:
```
$sudo gedit /etc/modprobe.d/blacklist
```
Then add the following line to the end of the file:
```
blacklist sony-laptop
```

Now you can use your function keys and jog wheel in a predictable manner.
scolling up and down are fine and if you click the wheel it will do a middle click.
Just an interesting note: the unmarked key next to the sun key increases the back light for me.

There are bound to be some bug reports for this somewhere that should be closed I'm sure. And this is an open bug for sony-laptop since that utility is trying to replace sonypi.


Thanks I am fixed !!!!

---

### Post by RtVD on 2008-10-31
Well, I've updated to 8.10, it doesn't have the jog-dial crazy scroll issue... the jog dial doesn't do anything at all.

re-blacklisted the sony-laptop module, restarted, and it according to lsmod, sony-laptop is still being loaded (though before blacklisting the FN keys weren't working, now they are [except for scroll-lock which has never worked]).

I'm also getting some font corruption, so for now I'll take this with a grain of salt, and probably do a full wipe/reinstall for 8.10 and see if it gets better.

-RtVD

---

### Post by colintivy on 2008-11-10
Hi folks!

Nothing seems to have surfaced in this topic for a long time now. Does this mean evryone except me has found a solution? I no longer find my finger falling on the wheel now but it would be nice to go back and use it. Incidentally my laptop is an old (PentIII) ex Win98SE therefore predates all these nice new Varios etc.,

Colintivy :-/

---

### Post by burneverything on 2008-11-10
> **colintivy said:**
> Hi folks!

Nothing seems to have surfaced in this topic for a long time now. Does this mean evryone except me has found a solution? I no longer find my finger falling on the wheel now but it would be nice to go back and use it. Incidentally my laptop is an old (PentIII) ex Win98SE therefore predates all these nice new Varios etc.,

Colintivy :-/

Just finished installing xubuntu 8.04 on a PCG-871M (old pentium 3 model) and the scrol wheel works fine for me (at least in firefox I haven't tried many applications yet)

---

### Post by RtVD on 2008-11-10
> **colintivy said:**
> Hi folks!

Nothing seems to have surfaced in this topic for a long time now. Does this mean evryone except me has found a solution? I no longer find my finger falling on the wheel now but it would be nice to go back and use it. Incidentally my laptop is an old (PentIII) ex Win98SE therefore predates all these nice new Varios etc.,

Colintivy :-/

the 'blacklist sony-laptop then restart' worked fine for me, how did it go for you?

gotta say though, just clean installed 8.10 on my pcg-r505dl and lsmod | grep sony, shows both sony-laptop and sonypi loaded. the function keys are all working now though.

the scroll/jogger wheel itself does nothing at all though in 8.10, and I have graphical corruption, and the new compiz can't run on an intel 830M graphics chip.

I'm thinking that re-installing 8.04 might be the answer for me.
-RtVD

---

### Post by scallopedllama on 2008-11-14
Well I only *just* upgraded to Ibex last night so I haven't had the time to work out all the issues. I'm currently having a strange problem where my laptop won't get to the gnome desktop, it gets stuck on an orange screen before playing that music.

Anyway, I will be working on this and I'll keep this place updated if I can figure anything out

---

### Post by scallopedllama on 2008-11-14
Getting there...
So I've been playing with this a bunch this afternoon and I *have* been able to get the jogwheel working using the old program sonypid. I don't know if this is how it worked on the old releases (or if this is even any good of a program) but it workes for me.
You need to have sony-laptop blacklisted first

You can get the source for sonypid here: [http://www.linux.it/~malattia/wiki/index.php/Sonypi]("http://www.linux.it/~malattia/wiki/index.php/Sonypi")
It's at the end of the page. Put it somewhere you know and untar it with a 
```
$tar -xjf sonypid-1.9.1.gar.bz2
$cd sonypid-1.9.1
```
You won't be able to compile it until you download the xorg-dev package so
```
$sudo apt-get install xorg-dev
```
then
```
$make
$sudo make install

``` inside the sonypid-1.9.1 directory.

You can test it out real quick with
```
$sudo sonypid
```
You can put an & on the end there after you've already unlocked the sudo for your session. 
If you haven't done a sudo previously, it'll do nothing because sudo needs a password.

Now all you need to do is get it to start on the next boot. 
I'm still trying to get that one sorted out. I tried putting it in the rc.local file.. no dice.

any suggestions?

---

### Post by scallopedllama on 2008-11-14
So I'm looking at this, I it looks like sony-laptop is actually completely capable of handling this laptop.
If you get rid of the sonypi and restart allowing sony-laptop to start, the backlight can be changed using an applet (not the function keys). and if you do a ```
$cat /proc/bus/input/devices
```
you get a long list of stuff that has two entries of interest:
```
I: Bus=0010 Vendor=104d Product=0000 Version=0000
N: Name="Sony Vaio Keys"
P: Phys=
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0b/SNY6001:00/input/input12
U: Uniq=
H: Handlers=kbd event6 
B: EV=13
B: KEY=1f 160f0000 c 0 100000 0 2 0 600b 102400 0 40300400 e0000 0 0 0
B: MSC=10

I: Bus=0010 Vendor=104d Product=0000 Version=0000
N: Name="Sony Vaio Jogdial"
P: Phys=
S: Sysfs=/devices/virtual/input/input13
U: Uniq=
H: Handlers=mouse1 event7 
B: EV=7
B: KEY=40000 0 0 0 0 0 0 0 0
B: REL=100
```

I'm not an xorg.conf wizard or anything, but this might mean that all we need is a couple xorg.conf sections to get this to work.

---

### Post by scallopedllama on 2008-11-16
Ok. I've had it with this stuff. You can get the scrollwheel to work on a per-login basis by using sonypid (I attached a much less annoying version that you can run with a -D option to make it a daemon and it won't print EVERY event to stderr). The only problem is that it requires super-user privileges. I tried to edit my sudoers file to make it so starting sonypid doesn't require a password, but I couldn't get it.

Anyway, You can use the sonypid program I included and add an option to your session startup stuff that's like 
```
/usr/bin/gksu "/usr/local/bin/sonypid -D"
```
which will ask you for your password on every login but it works
Oh, and apparently sonypid breaks the brightness keys :)


(Btw you can install that sonypid just like any other program: make; sudo make install. Just make sure you have the xorg-dev package and its dependencies installed)

As for me, I'm going back to hardy heron. There are just too many problems with ibex for me to stick to this upgrade:
-sonypi/sony-laptop is a pain now
-suspend doesn't work anymore
-my wifi card doesn't work
-compiz fusion crashes
-this corrupt/garbled/erratic font stuff is driving me nuts.

I had no issues with heron, so I'm going back.

---

### Post by jippers on 2008-11-16
> **scallopedllama said:**
> Solved.

So the problem was completely sony-laptop. It apparently takes control of the back light before sonypi takes over (explaining why the back light controls didn't work after removing the sony-laptop module).

So you need to add sony-laptop to the modprobe blacklist:
```
$sudo gedit /etc/modprobe.d/blacklist
```
Then add the following line to the end of the file:
```
blacklist sony-laptop
```

Now you can use your function keys and jog wheel in a predictable manner.
scolling up and down are fine and if you click the wheel it will do a middle click.
Just an interesting note: the unmarked key next to the sun key increases the back light for me.

There are bound to be some bug reports for this somewhere that should be closed I'm sure. And this is an open bug for sony-laptop since that utility is trying to replace sonypi.

Oh man, thanks SO MUCH! My laptop is usable again in 8.04!!!!  :guitar:

---

### Post by scallopedllama on 2009-01-21
Well I'm forced to upgrade to intrepid so I'm back to trying to get this stuff figured out. 
Using sonypi, I'm still clueless as to why the jogdial and all function keys worked in hardy but not intrepid. but it seems that it has always used acpi events to trigger the function key stuff. that's why the audio keys still work in intrepid, there's a bug with the backlight change script..

But I have found the solution to the messed up font stuff. all you need to do is add
```

Option "AccelMethod" "XAA"

```
to the Device section of your xorg.conf file.

---

### Post by scallopedllama on 2009-01-21
also..
It appears that sonypi works just as well as it did in hardy. there are other things that broke along the way.
they way that hardy heron (and intrepid ibex tries to do it this way) with sonypi is that the fn keys are handled with acpi events. The volume keys still work, but either the script to change the backlight intensity or the acpi code changed and thus is no longer calling that script (I don't think this is the case).
The script that tries to change the backlight is looking for a /sys/class/backlight/sony folder that doesn't exist with sonypi in intrepid ibex. What's weird is that the backlight applet in Gnome works properly... so how the crap does that change the backlight? smartdimmer doesn't work.. and the backlight script didn't really change between hardy and intrepid (making them the same does not fix the problem)

The jogdial is handled with xorg and its ability to add devices that HAL tells it is around. In hardy heron, it happily reports a proper mouse for the jogdial that xorg can actually properly set up. However, in Intrepid Ibex, HAL reports that the Jogdial is a one button mouse, so obviously the scroll wheel isn't going to work in any way.

I was working on an even better version of sonypid.. but I stopped and decided that I wanted that to be a last ditch effort to get this working.

I don't know, maybe I'm wrong about this... argh. I just want my scrollwheel and backlight keys to work

---

### Post by scallopedllama on 2009-02-19
So I finally got sonypid figured out. sony-laptop is a waste of time for us PCG-R505GL users. I don't think it can handle the jogwheel at all. In the end you need to use sonypi with sonypid:

First, apply the fix for hardy heron: adding
```
blacklist sony-laptop
```
to your /etc/modprobe.d/blacklist file.

You can snag my version of sonypid [here]("http://www.personal.psu.edu/jbb5044/linux/sonypid-2.0.0.tar.gz"). It's not much different than the 1.9.1 except that you can kill it and re-launch it without any problems, it doesn't dump a ton of messages to stderr by default, and if you scroll the wheel fast, it'll scroll a page fast.
You can install it in the standard way:
```
$ cd [download dir]
$ tar -xvf sonypid-2.0.0.tar.gz
$ cd sonypid-2.0.0
$ make
$ sudo make install
```
This needs to be run as root after X has set the DISPLAY environment variable. You can't just tell it to start in a .xsession file because that doesn't run as root. And you can'd tell it to run in /etc/rc.local because that doesn't have the DISPLAY variable.  My ultimate solution requires that you use gdm, I'm not sure where you'd put this for kde or xfce. 
Add the following to your /etc/gdm/PreSession/Default file before exit 0
```
/usr/local/bin/sonypid -D
```

Restart your computer and the Jogwheel works. Oh, and on my computer, the volume and brightness keys work without any extra fussing. I guess those ACPI events are still being handled correctly.

You can also get my xorg.conf file [here]("http://www.personal.psu.edu/jbb5044/linux/xorg.conf"). It has that garbled font issue fixed in it.

---

### Post by jippers on 2009-05-24
Scallopedllama! Your archive you're linking to is zero bytes! Please upload it again so I can upgrade my laptop to 8.10. Thanks a bunch.

---

