---
title: "Auto log off"
date: 2008-08-07
forum: General Help
---

### Post by Viridia on 2008-08-07
So I just got ubuntu to fill my entire screen (YAYAYAYAY!!!!) but it said I needed to log off for my changes to take effect. I logged off, and tried to log back on. I got on for like 20 seconds, but then it gives me a black screen with some white text. Something about cron. Anyway, then it takes me back to a log in screen. I log in, and it repeats the entire process. Any advice on how to fix this?

Danke

---

### Post by Viridia on 2008-08-08
Oh, this happens every time. As in, I cannot use the computer.

---

### Post by Thyssenkrupp on 2008-08-08
Well, if you dont have much stuff on your computer, it may be wise to consider a full system re installation, i know its not the best thing in the world (hell, ive done it 8 times now =[ ) but if you cant log on for long enough, theres not much you can do?

Maybe a system fixing disc could be an option?

Sorry i couldnt be much help.

Jak

---

### Post by Viridia on 2008-08-08
I would do that, it's just that I'm afraid once I do the full restore, and I fix the screen, it'll just do the same thing.

If you know a way to delete all cron jobs or something, that'd be great, as I think crons are what are killing me.

---

### Post by mali2297 on 2008-08-08
What instructions did you follow before you logged off?

What is the "white text" that you see? Any error messages?

---

### Post by Viridia on 2008-08-08
White text was like "cron" and scheduled, and checking the battery state.

What do you mean by instructions?

---

### Post by mali2297 on 2008-08-08
> **Viridia said:**
> White text was like "cron" and scheduled, and checking the battery state.

What do you mean by instructions?

What did you change before the problem occurred?

---

### Post by WRDN on 2008-08-08
What were the alterations you made to the system before you got the message that you needed to log off, and the problems started occuring.
Also, at the login screen, press Ctrl + Alt + F1, then try logging it without using GDM. If you login sucessfully, type "sudo startx" to restart X.

---

### Post by Viridia on 2008-08-08
> **mali2297 said:**
> What did you change before the problem occurred?

Oh. 

See, the OS was only filling a certain part of my screen, a square in the middle of my laptop screen. I changed the type of monitor from a plug-n-play to something else, I can't remember.

---

### Post by mali2297 on 2008-08-08
> **Viridia said:**
> Oh. 

See, the OS was only filling a certain part of my screen, a square in the middle of my laptop screen. I changed the type of monitor from a plug-n-play to something else, I can't remember.

Can you revert the changes within the 20 seconds gap?

(Then we might look for another fix to the screen problem.)

---

### Post by Viridia on 2008-08-08
Ok, so I did the CTRL-ALT-F1, and logged in succesfully. I executed the command, and it said

"X: warning; process set to priority -1 instead of requested priority 0

Fatal Server error:
Server is already active for display 0
              If this server is no longer running, remove /tmp/ .XO-lock
              and start again/

Invalid MIT-MAGIC-COOKIE-1 keygiving up.
xinit:   Resource temporarily unavailable (errno 11):   unable to connect to X ser
ver
xinit:   No such process (errno 3): Server error."

---

### Post by WRDN on 2008-08-08
Try entering Recovery Mode (option on GRUB menu, unless you removed it), and select "Fix X Server".

---

### Post by Viridia on 2008-08-08
Um... what is the GRUB menu?

When I hit the session button on the login screen, I see last session, run xclient script, secure remote connection, xcfe session, failsafe gnome, and failsafe terminal.

---

### Post by WRDN on 2008-08-08
> **Viridia said:**
> Um... what is the GRUB menu?

When I hit the session button on the login screen, I see last session, run xclient script, secure remote connection, xcfe session, failsafe gnome, and failsafe terminal.

When you boot your PC, the GRUB menu is the screen where you can choose whether to boot Ubuntu, Ubuntu Recovery Mode, Memory Test etc.

---

### Post by Viridia on 2008-08-08
OK, I fixed the X Server in the recovery mode, and I can log into my account and stay there. But it sets it back to where the OS only fills a square in the center of the screen.

---

### Post by Viridia on 2008-08-08
oops, nevermind, replied to the wrong post.

Still, it's not working.

---

### Post by Viridia on 2008-08-08
Oh, something I should mention. THe white text mentions a  file called etc/rc.local. Maybe that has something to do with the issue?

---

### Post by mali2297 on 2008-08-09
> **Viridia said:**
> Oh, something I should mention. THe white text mentions a  file called etc/rc.local. Maybe that has something to do with the issue?

I rather think the problem is related to the graphics driver.

What is your graphics card?
If uncertain, type
```

lspci | grep VGA

```
in the terminal and it should tell you.

---

### Post by Viridia on 2008-08-09
That command gives me these results

I know that is in an integrated Intel card, called an Intel 815. Running the command gksu displayconfig-gtk, and going to the graphics card pane tells me that there is no driver. Should I use ndiswrapper?

(I've used it before, but only in BSD)

Thanks again for all lyour help, I really appreciate it.

---

### Post by mali2297 on 2008-08-10
> **Viridia said:**
> That command gives me these results

I know that is in an integrated Intel card, called an Intel 815. Running the command gksu displayconfig-gtk, and going to the graphics card pane tells me that there is no driver. Should I use ndiswrapper?

(I've used it before, but only in BSD)

Thanks again for all lyour help, I really appreciate it.

The graphics driver should be available in the package [xserver-xorg-video-intel]("http://packages.ubuntu.com/hardy/xserver-xorg-video-intel"); try (re)installing it.

ndiswrapper is for wireless network cards.

---

### Post by Viridia on 2008-08-10
Ah, I always thought that it was for all windows drivers.

Anyway, how would I install that?

Oh, a mistake I need to fix: I'm using xubuntu, not ubuntu, if that makes any difference at all.

EDIT: Erm, which file do I download?

---

### Post by mali2297 on 2008-08-10
The package is available in the repositories (the same for ubuntu and xubuntu) and it should be installed by default.

If you can log in graphically, use Synaptic package manager to find the package and reinstall it.

Otherwise, try to reach a terminal and type
```

sudo apt-get install --reinstall xserver-xorg-video-intel

```

---

### Post by Viridia on 2008-08-10
Thanks. Logging to the failsafe terminal and typing that will work, right?

---

### Post by Viridia on 2008-08-10
OK, I typed that command and it finished. What should I do now?

---

### Post by mali2297 on 2008-08-10
> **Viridia said:**
> OK, I typed that command and it finished. What should I do now?

I assume that it didn't help.

After logging in, open a terminal window and type the following commands:
```

egrep "EE|WW" /var/log/Xorg.0.log
xrandr
cat /etc/X11/xorg.conf

```
Post the output. 

(You can copy/paste the output by highlighting it with the mouse and then move the cursor to the browser and paste with a middle-click.)

EDIT:
You can try regenerate xorg.conf with
```

sudo dpkg-reconfigure -phigh xserver-xorg

```

---

### Post by Viridia on 2008-08-10
It's saying I'm running in low graphics mode now, and displays the earlier mentioned white text several times upon turning on the computer. It works fine. I'll get the output in a sec...

---

