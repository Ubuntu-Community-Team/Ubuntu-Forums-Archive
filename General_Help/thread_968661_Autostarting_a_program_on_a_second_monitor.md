---
title: "Autostarting a program on a second monitor"
date: 2008-11-02
forum: General Help
---

### Post by Kup0man on 2008-11-02
I have two monitors and they are set up as separate X Screens in the nVidia X server settings.

On my second monitor I like to run a full screen vmware with windows.

So my question is, how do I get vmware to autostart (at login) on my second monitor (Screen 1).  I have the command I would like to run (VBoxManage startvm Windows).  I just need to know who to tell ubuntu to run that command on start up, and on my second monitor.

Also is there a VMware switch to tell it to automatically start in fullscreen?

Thank you

---

### Post by sj1410 on 2008-11-02
you need to create a shell script, first set the display

> export DISPLAY=:0.1
<command to run vmware>

go to system-->Preference-->Sessions to add the script to startup at logon 

i am not sure but its -x for fullscreen in vmware

also have a look at 
[http://www.ubuntugeek.com/how-to-set-vmware-resolution-fullscreen-as-your-ubuntu-desktop.html](http://www.ubuntugeek.com/how-to-set-vmware-resolution-fullscreen-as-your-ubuntu-desktop.html)

enjoy :)

---

### Post by Kup0man on 2008-11-02
I'll try that.

And I don't know why I said VMware, **I am using Virtual Box** XD
I have no idea why I constantly said VMware instead of Virtual Box lol

---

### Post by Kup0man on 2008-11-02
Thank you that worked (once I figured out how to get my script to run :P)

Now if it just started fullscreen it would be perfect :D

I should go read some forum rules, but what are the rules related to double posting?

---

### Post by sj1410 on 2008-11-02
try this
```
VBoxSDL -vm "Windows XP" -fullscreen 
```



> **Kup0man said:**
> Thank you that worked (once I figured out how to get my script to run :P)

Now if it just started fullscreen it would be perfect :D

I should go read some forum rules, but what are the rules related to double posting?

---

### Post by Kup0man on 2008-11-02
The -fullscreen switch doesn't quite work like I wanted.  It basically maximizes the window, whereas what I want is the complete cover the entire screen fullscreen (the one you get by pressing <hostkey>+F).

Is there a way I can tell the script to just press ctrl + F?

Also how do I put in a wait in the script?  Is it sleep?

---

### Post by sj1410 on 2008-11-02
yes its sleep 10 for 10 secs.

there should be some way for complete fullscreen, lets google it, if you find it first let me know

> **Kup0man said:**
> The -fullscreen switch doesn't quite work like I wanted.  It basically maximizes the window, whereas what I want is the complete cover the entire screen fullscreen (the one you get by pressing <hostkey>+F).

Is there a way I can tell the script to just press ctrl + F?

Also how do I put in a wait in the script?  Is it sleep?

---

### Post by Kup0man on 2008-11-02
There is a command to send keypresses to the guestOS

```
VBoxManage controlvm VMname keyboardputscancode
```

Unfortunately, this appears to send commands straight to the guestOS, and ignores the host key.  But it is an interesting feature.

---

