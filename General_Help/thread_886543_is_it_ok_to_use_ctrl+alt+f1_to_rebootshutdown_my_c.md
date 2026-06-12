---
title: "is it ok to use ctrl+alt+f1 to reboot/shutdown my computer when frozen?"
date: 2008-08-11
forum: General Help
---

### Post by SureStandar on 2008-08-11
hi, my pc (hp laptop dv6000, ubuntu 8.04) often freezes when using firefox or attempting to play some video file and there is no way i can make it respond. mouse moves but no response from the GUI.
i read a lot about that problem in these forums, seems most users face it..
is it safe to reboot or shut it down via ctrl+alt+f1 and sudo reboot? or maybe ctrl+alt+backspace works the same?? 
thank you in advance, you all are very helpful. 
:guitar:

---

### Post by Joeb454 on 2008-08-11
Moved to General Help

---

### Post by anotherdisciple on 2008-08-11
If Ctrl+Alt+Backspace works... I would do that... it restarts your graphical stuff... it would take less time than a reboot... and it's probably just what you are looking for.

---

### Post by Archmage on 2008-08-11
CTRL+ALT+F1
top
(look what program is using all your CPU and remember the PDI)
q
kill -15 (now enter here the PDI)
CTRL+ALT+F7

Go on.

(If this wont work, try to redo it with -9 instead of -15.)

---

### Post by timcredible on 2008-08-11
as the other poster said, no reason to reboot, it's just firefox that's stuck, so ctrl-alt-backspace will restart gnome.

---

### Post by SureStandar on 2008-08-11
hhmmm... now i remember that music and video sound keep playing after VLC or mozilla freezes but not even the cpu processor display at my panel operates. it gets stuck at the current point when freezes. so i m pretty sure that is not just firefox. maybe that's where it begins and it messes up the whole thing. i ll try n figure it out next time it happens, hope not soon.. first thing to do ctrl+alt+backspace. then if this doesn't work ctrl+alt+f1 sudo reboot. I mean it's less painful than a forced shutdown  by keeping the power button pressed, right? 

Archmage: can you explain please what is PDI? and what -15 and -9 mean?
do i reach some sort of a "task manager" with the way you described?

thank yous dudes, fresh user here\\:D/

---

### Post by Archmage on 2008-08-12
> **SureStandar said:**
> Archmage: can you explain please what is PDI? and what -15 and -9 mean?
do i reach some sort of a "task manager" with the way you described?

I'm sorry, I did mean PID. This is the number of the "task". The program "top" is some kind of a text only "taksmanager".

---

### Post by SureStandar on 2008-08-12
nope, nothing of the above works guys...:( it happened again couple of hours ago and i had to shutdown via button, (@#$% i hate that  :mad:)
The Freeze seems to happen when i try to rush things, such as closing a window right after i open another one or, opening an .flv from my xp partition with vlc while firefox plays youtube.
...i hate to say that, but my xp used to work more stable. at least when it rarely crashed, i knew for sure that is coming back any minute.. and i also like ubuntu VERY much. the more i use it, the more i lose "it". 
 i m sure your advice will be handy in some other situation. thank you :):guitar:...
Beware, it's... "The Freeze"
p.s. excuse my english, not my native language.

---

### Post by x1a4 on 2008-08-12
Hi,

When an application hangs, the first thing you should try is to close it using xkill.  Press Ctrl+Alt+Esc, your cursor will turn into a cross (or skull & bones depending on your cursor theme), then just click the unresponsive window.  

If that doesn't work, then try the other options, like switching VTs (Ctrl+Alt+F#) and killing the process.  

One way to kill a process is to get its process ID using top, then use the kill tool to kill it, or, if you know the executable of the process, use pkill instead.  For example:
```
pkill -15 firefox
``` will kill all instances of firefox--provided you have permission to do so. 

Try to avoid using Ctrl+Alt+Backspace.  Instead, unless you're running multiple X sessions, switch to another VT and run
```
sudo /etc/init.d/gdm restart
``` which will restart GDM and all X servers and clients it's running.

---

### Post by alzie on 2008-08-12
Having to use the power button for a hard shutdown/reboot is not good for your system.

Ctrl+alt+F1 and the command "shutdown now" should shut down all the processes and allow you to reboot.

I hope this helps

---

### Post by SureStandar on 2008-08-13
thank you for your help, but none of the key combinations that i've tried works. not one.. it is completely unresponsive.
should i try to press them all together??? of course not, i m kidding\\:D/
could it be i've installed the "wrong" .iso? i installed the ubuntu-8.04-desktop-amd64 
my laptop specs:  memory 1gb
                  processor intel core2 t5500 @ 1.66 Ghz

---

### Post by SureStandar on 2008-08-15
it's getting serious now...:confused:

---

### Post by FrizzleFry on 2008-08-15
I think it's safe to say that's the wrong .iso

The *.amd64 is for AMD 64bit processors only from what I've read, even if you have a dual core intel it will not work correctly. I would say format and reload the *.i386 version.

(Correct me if I'm wrong on this, I'm still a newb myself) :)

---

### Post by rbmorse on 2008-08-15
That's not correct.  AMD-64 refers to the instruction set which the 64-bit Intel chips fully support.  The AMD-64 iso works fine on my Intel EP-35 computer with E8400 CPU. 

I do wish they would call it something like PC-64 or something.

---

### Post by SureStandar on 2008-08-15
i'll have to live with it i guess.. let's hope that the coming version of ubuntu will be even better.
thank you all for help :guitar:

---

### Post by alzie on 2008-08-16
Which programs are causing the lockups?  Is it just firefox or are there other programs causing it?

---

### Post by SureStandar on 2008-08-16
hallo alzie, mostly when firefox 3.0 is on for a long time and i try to open a video with VLC. 
would you say i d better had installed the i386 version?

---

### Post by alzie on 2008-08-16
I was wondering if it might be a flash issue?

I was having flash issues (flashplugin-nonfree) until I downgraded from sun-java6 to sun-java5.

Or maybe you might try upgrading to flash 10 and see if it helps.

I'm also running flash-block (thru firefox>tools>plugin) and it helped alot.  I was having issues with bad flash ads messing me up.  Its pretty stable now.  Maybe this will help.  It has to be better than running with a crippled system.

---

### Post by cpetercarter on 2008-08-16
There is a very useful applet which you can place in a panel which you can use to force misbehaving applications to quit. Much easier than using than trying to find the correct terminal command when you are a bit panicked anyway.

---

### Post by SureStandar on 2008-08-16
ok i installed flash-block, let's see what happens..

cpetecarter: i already tried to do so but the WHOLE system is completely stuck. no response at all. that applet is a really good tool but not for this occasion.
could it be because of the vlc multimedia plugin installed on firefox?
:-k

---

