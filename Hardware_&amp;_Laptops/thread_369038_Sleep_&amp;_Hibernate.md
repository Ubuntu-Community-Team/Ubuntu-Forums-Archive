---
title: "Sleep &amp; Hibernate"
date: 2007-02-24
forum: Hardware &amp; Laptops
---

### Post by Tonren on 2007-02-24
Hi guys.  I'm on an HP Compaq v2565us with 768MB RAM and a 1024MB swap partition.  I'd really love for hibernate to work, but I can't get it running for the life of me.  I've been having trouble with shutdown as well (so I guess hibernate might be too much to ask), but I've been trying.  I've changed POST_VIDEO to "false" in /etc/default/acpi-support, and I've tossed all sorts of nonsense into my boot parameters, but nothing seems to work.

I did "sudo aptitude install hibernate" and then just ran "sudo hibernate".  It spat out a ton of errors on a virtual terminal and then went back to my WM with: 

```
/bin/echo: write error: Cannot allocate memory
```

[This is my syslog](http://inspiranity.com/syslog-partial.log) and [ this is the output of lspci -vv](http://inspiranity.com/lspci-vv.log).

Can anyone give me a hint, perhaps, at what in the world is going on?

Thanks!

---

### Post by kevinlyfellow on 2007-02-24
I haven't read through this yet, but maybe it will help

[http://www.linux.com/article.pl?sid=07/02/02/2117209](http://www.linux.com/article.pl?sid=07/02/02/2117209)

Unfortunately, bios makers don't follow the acpi spec like they should and only make sure that it works for windows.  Its frustrating, but its the world we live in.

---

### Post by Tonren on 2007-02-24
Installing uswsusp and then running that guy's script with "suspend.sh hibernate" ends up with:

```
suspend: Could not stat the resume device file
```

No dice so far.  :\

---

### Post by Tonren on 2007-03-06
Anyone?  I really, really need hibernate.

---

### Post by spacebetween on 2007-03-06
Same problem, here.

I love Ubuntu, but using it right now just is NOT practical without Suspend/Hibernate. I need my laptop on the go with constant use, and shutting it down all the time is not the answer.

Oh, and I'm using a Compaq Presario V2000. I cannot find help with this anywhere! Surely there are other Presario users with the same issue.

---

### Post by plaser on 2007-03-07
Hi peoples!
I have problem with suspend and hibernate state!When I try to put my computer in suspend and hibernate mode he just go on the suspend mode, but very fast he return back to work state, though I don't move the mouse nor any other taster on keyboard!
Is anyone have problem like this or some solution!

I'm using next computer:
-Motherboard: ASUS P4PE2-X 845PE
-Processor: Celeron 4 2.4GHz
-RAM: 256MB DDR 400MHz
-Graphic card: ATI Radeon A9250/TD/128M
-Monitor: Samsung 793DF

---

### Post by spacebetween on 2007-03-08
I'm still looking, and I WILL get this solved somehow. :-)

---

### Post by spacebetween on 2007-03-10
I don't know if any of the previous posters are still looking, but apparently my problem was with Beryl.

I went over to the beryl forums, and sure enough, someone figured out a script to get suspend working.

So, if you're using Beryl and can't get suspend to work properly, go here:
[http://forum.beryl-project.org/viewtopic.php?f=39&t=789&p=26561#p26561](http://forum.beryl-project.org/viewtopic.php?f=39&t=789&p=26561#p26561)

---

### Post by Tonren on 2007-03-13
Okay, so `suspend.sh hibernate` and `sudo hibernate` don't work, but for some reason, clicking "Hibernate" in the KDE Logoff menu **does** appear to work.  What command-line function is this analagous to?

Also, I can't figure out how to get the Shutdown/Restart/Hibernate options to show up when I'm using Beryl on :1.  What's up with that?!

---

### Post by Runico on 2007-03-16
In order to suspend with beryl running I only had to disable sync to vblank in beryl settings

---

### Post by Tonren on 2007-03-16
@Runico:

How do you suspend in Beryl?  Do you click on "Suspend" in the Logout menu?  If so, how did you get the logout menu to include "Suspend"?  (It only says "End Current Session" for me).

---

### Post by Runico on 2007-03-16
Most times I use a special key of my laptop, but I have suspend in logout menu. Do you have ACPI_SLEEP=true in /etc/default/acpi-support?

---

