---
title: "X11vnc as boot loaded service"
date: 2008-11-28
forum: General Help
---

### Post by Cowpoke on 2008-11-28
I have been prowling around the groups here, and not really finding what I want...

I recently got VNC to work on my computer -- I can remote into the machine from anywhere!  That part is great.

However, when I reboot my machine (through the VNC session), the service doesn't auto-start at boot.  This leaves me stranded outside my box, until I can manually login (read: get home).

Bear in mind, I am using Xubuntu.  I have set up X11vnc as a service that starts when I log in.  So I have part of the solution.  How do I get the rest?  Any direction would be appreciated; I want to have my X11vnc script run at boot, rather than when I log in.

Does the Xfce Settings Manager have a boot-time settings manager similar to the Autostarted apps?

TIA!
Cowpoke

---

### Post by krunge on 2008-11-28
Have a look here under section "Continously":

[http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)

---

### Post by Cowpoke on 2009-01-27
Feeling obligated to post my resolution here...
I got X11vnc to work the way I wanted it to.

I loaded my X11vnc server and then setup my account to auto-start the X11vnc service.  This is effected via Applications -> Settings -> Settings Manager -> Autostarted apps in xubuntu. (This helped me once I was able to log in.)

This was fine, as I alluded, so long as I was logged in.  While I was away over the X-mas/New Year's Holiday, I didn't expect to be at my desktop, nor did I have anyone who could log in for me, etc...

The way I remedied that is by setting auto-login for my userid.  *WARNING* This will leave your box vulnerable to casual cyber-bypassers; USE whatever other security you have available to reduce this risk.

This piece was effected via Applications -> Settings -> Login Window.  On the Security tab, check Enable Automatic Login and specify the user to auto-login.  NB:  This user should be the same one for whom you set the Autostarted apps above.

This method, with its referenced insecurity did the trick for me!

;)

---

### Post by rvjr on 2009-02-10
Hey guys, I'm somewhat in trouble here as well: I'm running Kubuntu with KDE4. I put the startup command line of x11vnc into my Xsetup file and I can successfullly connect via VNC and the login screen is presented to me. Problem is now: When I type my user and password and press the login button, the vnc server gets killed. No obvious errors in the log or other messages, it just disconnects the vnc viewer and jumps back to the login (Which is actually weird: it does not log me in, when i look at the real screen...)

Does anybody have a hint what might be wrong here?

thanks
Rainer

-- ok, i just opened a new topic for that --

---

### Post by Myspulin on 2009-08-04
Try this:

/usr/bin/x11vnc -bg -reopen -forever

-bg - is running on the background
-reopen - after you will log in and the x11vnc will be terminated this swich renew x11vnc connection
-forever - after you close vnc client the x11vnc server won't close but keep "running"

But I have a problem. I need to run x11vnc as a service too before I log in but I can't locate the Xsetup file. I have Manddriva 2009.1 with KDE 4.2.4. In /etc I don't have any KDE4 directory.

---

### Post by krunge on 2009-08-04
> 
-reopen - after you will log in and the x11vnc will be terminated this swich renew x11vnc connection

BTW -reopen has only appeared in recent x11vnc (0.9.8?)  The version distributed by ubuntu and debian is still 0.9.3.
> But I have a problem. I need to run x11vnc as a service too before I log in but I can't locate the Xsetup file. I have Manddriva 2009.1 with KDE 4.2.4. In /etc I don't have any KDE4 directory.
Have you used your package manager to list of all of files associated with the kdm package(s)?

Have you run these commands?
```

locate Xsetup
locate kdmrc
locate kdm
etc..

```
Look at the files these listed by these methods. (BTW if you don't have locate(1) configured,  you can use the find(1) command instead.)

---

### Post by krunge on 2009-08-04
> 
locate kdmrc

In particular, if you can find a kdmrc file look for a "Setup=" value in the [X-*-Core] section:
```

# Core config for all displays
[X-*-Core]
...
# A program to run before the greeter is shown. Can be used to start an
# xconsole or an alternative background generator. Subject to word splitting.
# Default is ""
#Setup=

```

BTW, I assume you are running the kdm greeter and not gdm, right?

---

### Post by tranbo2@yahoo.com on 2011-08-04
Work Like A Champ with Xubuntu 1104 ...Thanks everyone for the infos :D

**X11vnc as boot loaded service**                                                                             Try this:

/usr/bin/x11vnc -bg -reopen -forever

-bg - is running on the background
-reopen - after you will log in and the x11vnc will be terminated this swich renew x11vnc connection
-forever - after you close vnc client the x11vnc server won't close but keep "running"

---

### Post by bodhi.zazen on 2011-08-04
Just understand that VNC is by far the most common crack on these forums.

You should tunnel VNC over ssh or use FreeNX.

With that I am going to close this 2 year old thread.

---

