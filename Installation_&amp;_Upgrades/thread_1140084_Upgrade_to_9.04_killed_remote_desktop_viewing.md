---
title: "Upgrade to 9.04 killed remote desktop viewing"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by Metallinut on 2009-04-27
Upgraded from 8.10 to 9.04.  I had remote desktop turned on, and used VNC to access (through SSH when not at home, otherwise just vnc directly).

Now anytime I connect, I get a view of my desktop, but the image never refreshes (I have a clock widget that normally ticks away seconds...it's accurate when I initiate the vnc session, but never increments afterwards).  The mouse cursor appears to move, but any action I take (e.g. click to open a terminal) does nothing. UNLESS I close vnc, and reopen...then I see terminal has opened, but typing does not refresh the screen.

So everything appears to be working through VNC, it's just that my screen is not getting refreshed.

VERY frustrating, as now I cannot use my Ubuntu box remotely (which is what I do most times)...

Any known issues/fixes?  Couldn't find anything in this forum...

---

### Post by tjbearman on 2009-04-27
I have exactly the same problem.  I upgraded to 9.04 and
now vnc from a remote client connects to my 9.04 machine OK,
but shows a static screen.  However, keyboard input
and mouse input from the remote client actually DOES
control the 9.04 machine - I can see that when I walk over to
the 9.04 machine and watch its local display.  I just don't see
the desktop refresh on the remote client - not even when I
manually ask for a refresh.
This problem happens with 2 different vnc remote clients, both of
which work properly when connected to a ubuntu 8.10 machine.

TJ O'Donnell

---

### Post by dhanes420 on 2009-04-28
I too have the same issues, on both ubuntu and kubuntu 9.04 after the upgrade.

Go into Preferences, Remote Desktop; make the required changes, add a password, click Close.

Go back to other machine, attempt to vnc in, can access, cannot control. First time I received an authorization notice about multiple users controlling the desktop on the ubuntu machine, set that to always remember the authorization.  Now, it still doesn't work, and if I reboot, the applet doesn't remember the information I put in previously.

---

### Post by Caredhel on 2009-04-28
I too am in the same boat!  I just upgraded my server to 9.04 today and my remote desktop is doing exactly like you guys have said.  My Windows machine isn't refreshing the screen showing what is going on on my Ubuntu machine, however the mouse movement is the only thing that is refreshing.

Help quick on this cause I need VNC access to my server asap!

---

### Post by xadloki on 2009-04-28
Disabling compiz worked for me in the Appearance preferences.
[https://bugs.launchpad.net/ubuntu/+source/vino/+bug/353126](https://bugs.launchpad.net/ubuntu/+source/vino/+bug/353126)

---

### Post by Caredhel on 2009-04-28
Thanks...  I disabled all visual effects and as soon as I did it cleared things right up.  My video card is an ATI btw so it appears that this is a known issue with both nvidia and ATI chipsets.

---

### Post by Metallinut on 2009-04-28
Not much of a fix...I really like my compiz effects!  Saw the bug listed in that link.  Let's hope it's fixed soon!!!

---

### Post by tjbearman on 2009-05-01
I am able to get remote desktop access when I switch off
compiz under Preferences/Appearance.  Thanks for the tip.
Sure would be nice if the Remote Desktop setup would
have some way to automate that.

---

### Post by shabazzk on 2009-05-09
I had this issue also, disabling compiz allowed me to control remote Jaunty machine. :) I can do without it for now, it's a dedicated HTPC with full install of Jaunty:guitar:.

---

### Post by smartmeister on 2009-05-14
thanks for this workaround, works great.

i should have checked this first, somehow i knew this had something to do with compiz :p

---

### Post by jmap82 on 2009-06-09
I wrote a short script to turn compiz off when I'm remotely viewing and back on again when I leave.  I'm no wiz at this stuff, so it may not be the best script ever, but you're welcome to use it if you want.

You can copy and paste from my wiki, [_here_]("http://script.jmap82.com/doku.php?id=jmap82sscripts:monitor").

Hope it helps :)

---

