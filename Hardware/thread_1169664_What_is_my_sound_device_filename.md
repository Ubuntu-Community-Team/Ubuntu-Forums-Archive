---
title: "What is my sound device filename?"
date: 2009-05-25
forum: Hardware
---

### Post by bluenix on 2009-05-25
Hi all, I'm using Jaunty from the first day of launch. I need to use this metronome software from standard repo called GTick, but it won't run - I guess the problem is with the *sound device filename*. Please help me on how I can find this.

It seems like it wants the device Filename - something in the form of

/dev/dsp

(it was given in the program preference by default but won't work for me).


Is there any command that shows the device filename? Oh mine is the x86-64 version.

---

### Post by sarang on 2009-05-25
Try /dev/audio

Or, try running the program from the commandline and instead of runing 

program_name

try running 

padsp program_name

---

### Post by bluenix on 2009-05-26
/dev/audio as device filename does not work. When I tried from command line:


padsp gtick


... it returns the following message:


/dev/audio: Device or resource busy



Any ideas?

---

### Post by sarang on 2009-05-27
So I installed it, and it seems to run fine if I run it as [FONT="Courier New"]gtick[/FONT]

I think you have a problem with your pulse audio setup. See 

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by kgs_mvs on 2011-02-17
The only way I was able to get it working was with the padsp command from the pulseaudio-utils package.  However, when I actually tried to start the metronome, it complained about permissions:

```
/etc/default$ padsp gtick
/dev/psaux: Permission denied

```
I eventually setup a shortcut to run it with the following command:

```
gksu padsp gtick
```

---

