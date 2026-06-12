---
title: "GUI (Gnome.. startx) regularly breaking to CLI (ish)"
date: 2008-10-06
forum: General Help
---

### Post by Phases on 2008-10-06
Hey guys. I'm having some trouble and I'm hoping you can help. I have a few questions really, but my main problem that needs to be solved first is this. I apologize ahead of time if my title or any of this sounds noobish to linux terms etc.. 'cuz that's kinda the case.

So here's the scenario. I have Ubunut 8.04 running. Compiz. Dual Monitors. Regularly have youtube running in a browser listening to some tunes. Clicking around on multiple tabs because at the moment I'm trying to figure out how to get VirtualBox to do what I want, but that's a whole seperate thread (I think?) Have CLI open and also Putty SSH'd into my home box. Pidgin, and a clock widget.

So. Every so often I'll click a window to put it in focus, or the X to close, and BAM, everything goes black for a second and then all I have on the screen is:

*Starting anac(h)ronistic cron anacron
*Starting deferred execution scheduler atd
*Starting periodic command schedular crond
*Checking battery state...
*Running local boot scripts (/etc/rc.local)

and that's it. I can Ctrl Alt 1 (or is it f1? I forget) to have it jump back to CLI, and if I startx from there it just goes to a black screen and I have to do a hard reset as far as I can tell. 

Any ideas? This setup is only a couple days old and it's been doing it since the beginning. But I don't know what could be causing it. I've been working hard with VirtualBox, making/deleting bridges and trying to get stuff to work at startup automatically, or seeing if I can get it to run on a separate dedicated nic without a bridge, but as far as I can tell this is independent of all that experimenting. 

It seems to happen as often as hourly..

Thanks in advance.

---

### Post by justleen on 2008-10-06
the lines you see are the last lines you will see when the system boots.
SO what happens, is that X crashes and dumps you to a terminal - where you see the last  boot msg. If you press enter there you should get a login prompt.

Try to login on this prompt and restart X with ```
 sudo /etc/init.d/gdm restart
``` that shoudl bring you back in X

---

### Post by Phases on 2008-10-06
Thanks for the reply. I will try that when it does it next. Will it be a fresh log in, losing all my unsaved work slash open windows? 

What can I do to try to figure out what's causing it? I've looked at the logs (in the System -> Administration -> System Log) but I don't know that I'm seeing anything that helps. I can't have it randomly kicking me out like this every hour or two. :(

---

### Post by justleen on 2008-10-06
you could check /var/log/Xorg.*.log  (ls -ltr sorts by date!)

and yes, that way you will restart X so you will loose everything that was open..

you could check (after login) to see if X is still running or no.
```
 ps -ef|grep -i gdm 
```

Im guessing its not..

---

### Post by Phases on 2008-10-06
> **justleen said:**
> you could check /var/log/Xorg.*.log  (ls -ltr sorts by date!)

and yes, that way you will restart X so you will loose everything that was open..

you could check (after login) to see if X is still running or no.
```
 ps -ef|grep -i gdm 
```

Im guessing its not..

I looked at Xorg.0.log and Xorg.0.log.old but they were damn lengthy, and no timestamp on anything.

The last thing on .log is "Warning: LookupDrawable()/SecurityLookupDrawable() are deprecated.  Please convert your driver/module to use dixLookupDrawable().
(II) XAA: Evicting pixmaps" 

..but I'm not sure that means jack.

As for seeing if X is still running.. when I type in that command now (course I rebooted after it last happened an hour ago and logged back in) I see:

root      5757     1  0 06:31 ?        00:00:00 /usr/sbin/gdm
root      5758  5757  0 06:31 ?        00:00:00 /usr/sbin/gdm
root      5765  5758  7 06:31 tty7     00:04:51 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
root      5953  5765  0 06:31 tty7     00:00:00 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7

Does that help?

---

### Post by Phases on 2008-10-06
Also, my coworker thinks it might be something with the way my fglrx is setup. He points out in my xorg.conf file there is this:

Section "Device"
        Identifier  "Configured Video Device"
        Driver      "fglrx"
        Option      "DesktopSetup" "horizontal"
        Option      "Capabilities" "0x00000800"
        Option      "PairModes" "0x0+0x0"
        Option      "EnableMonitor" "crt1,crt2"

...he says, compared to his setup, that's a funny way of defining stuff. Says his has some stuff 'set to true' instead. 

We installed our video drivers different, apparently.

---

### Post by Phases on 2008-10-06
Just FYI update, I went through a very painful couple hours of restoring xorg.conf over and over and trying a couple things here and there before I did what I think fixed it. 

I haven't had trouble since. What ended up working

-I uninstalled current video drivers
-made backup of xorg.conf
-followed command listed inside conf to have it rebuilt
-got in X and got envy, and downloaded driver from there.

So far so good anyway. Been a few hours and I've been tryin to give it hell.

Thanks for your help!

---

