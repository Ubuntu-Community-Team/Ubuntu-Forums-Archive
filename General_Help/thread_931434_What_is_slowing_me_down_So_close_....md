---
title: "What is slowing me down? So close ..."
date: 2008-09-27
forum: General Help
---

### Post by Bucky Ball on 2008-09-27
I'd like to put a more descriptive title to this post, but can't think of one. Fresh install of Ubuntu on Toshiba Satellite 2410 and I have been at this for 3 days. First up thought it was video drivers but have things running fine on the nv drivers for the moment and finally, boots at a reasonably normal speed. Get to the desktop though, and everything goes to snails pace. There seems like there is something checking the drive or doing some check and getting in the way. Basically, there seems to be something getting in the way. Too slow to open a browser and post much so here is a brief description of 'top':

apt-check
Xorg (at the top of the list and usually on about 7 %cpu)
ktoshkeyd
nm-applet
gnome-netstatus
init (always there - is this normal?)

... to mention a few . The machine seems to be working great apart from the feeling of wading through porridge. I am really hoping this might spark someone's imagination with at least an idea as there have been none forth coming and would hate to give this lappy back with windoze loaded (belongs to a friend who is keen to convert to Ubuntu/Linux), but as Ned Kelly said so eloquently, such is life ... :confused:

ps: just wondering if there is anything coming from the bios that is causing this but have experimented with just about everything at this stage ...
pps: if this is a further clue, only when I open programs do the problems really start. Hitting a drop down menu from the tool bar seems normal. Just takes forever to open any windows or do anything. Net speed seems normal also.

---

### Post by echo314 on 2008-09-27
Its normal for init to be there all the time. Its the process that spawns all the other processes, or something like that. You get the picture :)

---

### Post by Bucky Ball on 2008-09-27
Thanks and fine. Figured that might be the case. So, any idea what is getting in the way? Have checked the logs and nothing really glares at me. Ripping my hair out right about now. :)

In top, along the top, there is a row next to Cpu(s). It reads like this:

9.6%us, 4.2%sy, 0.0%ni, **83.4%id**

There are others but the one in bold doesn't look right. Is it?

---

### Post by sleepingdragon on 2008-09-27
I've just checked a few reviews of the 2410, and from what I've seen it looks like it's fitted with 256Mb of RAM as standard. That would explain why it's so sluggish. 

Ubuntu is happier with 512Mb of RAM - 1Gb is a bonus. Can you confirm your specs?

---

### Post by Bucky Ball on 2008-09-27
512mb. Is second hand and re-jigged 2410.

---

### Post by RequinB4 on 2008-09-27
> **Bucky Ball said:**
> Thanks and fine. Figured that might be the case. So, any idea what is getting in the way? Have checked the logs and nothing really glares at me. Ripping my hair out right about now. :)

In top, along the top, there is a row next to Cpu(s). It reads like this:

9.6%us, 4.2%sy, 0.0%ni, **83.4%id**

There are others but the one in bold doesn't look right. Is it?

Yes.  id = idle

When in top, see if anything is overusing your memory by pressing ```
>
```

---

### Post by Bucky Ball on 2008-09-27
Yep, thanks. Telling me:

Mem: 515452k total  460084 used! 55404 free

Doesn't seem to be anything real hungry in top though, strange.

Not sure what typing this '>' is doing. You do mean 'shift >' yea? :)
\

---

### Post by RequinB4 on 2008-09-27
> **Bucky Ball said:**
> Yep, thanks. Telling me:

Mem: 515452k total  460084 used! 55404 free

Doesn't seem to be anything real hungry in top though, strange.

OK well 55404 is NOT a lot of memory at all so that seems to be your problem.  All i can suggest is start closing programs until something gives - start with the top of the ">" list.

Here is how to use metacity instead of compiz - this'll test whether that helps:
```

metacity --replace

```

---

### Post by Bucky Ball on 2008-09-27
Thing is, this starts at boot. Don't need to be on the desktop so shutting programs doesn't make any difference (very little). This starts from the progress bar and takes ages to get to the desktop. The block that moves back and forward before progress indicator proper goes halfway up the first time then starts to flicker and stutter. The slowness starts from there, way before me booting anything on the desktop. My guess is something is kicking in at this point, something that maybe shouldn't.

(incidentally gets from actual boot to the grub menu in the blink of an eye so everything looking good up to that early stage. Also, windoze works fine and fairly zippy - this speed doesn't compare. Pretty sure it is something beyond meagre specs. Loaded Xubuntu first time round because of this and was no difference at all).

Update: Am looking at terminal with nothing open but the terminal and still telling me 410732k used. Top of the list is Xorg btw. ?

---

### Post by RequinB4 on 2008-09-28
> **Bucky Ball said:**
> Thing is, this starts at boot. Don't need to be on the desktop so shutting programs doesn't make any difference (very little). This starts from the progress bar and takes ages to get to the desktop. The block that moves back and forward before progress indicator proper goes halfway up the first time then starts to flicker and stutter. The slowness starts from there, way before me booting anything on the desktop. My guess is something is kicking in at this point, something that maybe shouldn't.

(incidentally gets from actual boot to the grub menu in the blink of an eye so everything looking good up to that early stage. Also, windoze works fine and fairly zippy - this speed doesn't compare. Pretty sure it is something beyond meagre specs. Loaded Xubuntu first time round because of this and was no difference at all).

Update: Am looking at terminal with nothing open but the terminal and still telling me 410732k used. ?

Ok, this sounds like either a rouge or extra daemon or possible a messed up install, but I know only how to deal with the former:

Is there anything extra in /etc/init.d/ any user scripts that might hang?

Also, it would really help to have a list of all processes running on your box... output (even scroll down) of top is useful.

Finally, try booting into recovery mode once and see if that helps.

---

### Post by Bucky Ball on 2008-09-28
[http://ubuntuforums.org/showthread.php?t=931636](http://ubuntuforums.org/showthread.php?t=931636)

/var/log/messages and /var/log/Xorg.log are posted there from about an hour ago. There is one task running in top and 96 sleeping. Will have a look at /etc/init.d now. Thanks ... :)

Looking at /etc/init.d directory. Not sure what should and shouldn't be there. Will compare with my laptop in awhile.

---

### Post by Bucky Ball on 2008-09-28
I have posted a bunch of info here:

[http://ubuntuforums.org/showthread.php?t=931636](http://ubuntuforums.org/showthread.php?t=931636)

... including top and init.d Cheers. :)

---

### Post by Ptero-4 on 2008-09-28
A shot in the dark I know, but can you try disabling the graphical boot splash (ask around how to do that) to see if it boots faster. Dunno your box, but there are some that won´t boot unless you disable the graphical boot splash.

---

### Post by Bucky Ball on 2008-09-28
[http://www.cyberciti.biz/faq/disable-graphical-grub-splash-screen/](http://www.cyberciti.biz/faq/disable-graphical-grub-splash-screen/)

Following instructions from here, can't find any such file. I have taken out the 'splash' by editing the grub kernel line at boot. No difference. :(

---

