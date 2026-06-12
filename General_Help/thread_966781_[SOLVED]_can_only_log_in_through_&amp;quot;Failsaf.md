---
title: "[SOLVED] can only log in through &amp;quot;Failsafe Gnome&amp;quot; after 8.10 update"
date: 2008-11-01
forum: General Help
---

### Post by Irishpolyglot on 2008-11-01
Hey guys!
I recently updated to 8.10 and immediately [had an issue]("http://ubuntuforums.org/showthread.php?p=6081573#post6081573") where I couldn't access the GUI at all since it would give me a blue screen (with the mouse usable and command line accessible) after logging in.

I found a temporary work-around by selecting "Failsafe Gnome" from the Options on the login screen and I have full access to the OS and everything seems to be working fine. But I can only get in by doing that. Once inside I saw that my NVIDIA accelerated graphics card needed to be updated and I applied that. But I still go into the blue screen unless I select Failsafe Gnome.

Based on recommendations in threads on trying to solve the blue-screen issue, I ran ```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
``` and rebooted and also tried ```
sudo dpkg-reconfigure xserver-xorg 
sudo /etc/init.d/gdm restart 
``` (after backing up the original, and then restoring it again when this didn't work). I also applied xfix when in recovery mode. I still only get the blue screen unless I log in through Failsafe Mode.

I'm on a DELL Inspiron 9400 with Nvidia 256MB GeForce Go 7900 GS PCI Expressx16 Graphics Card. Everything was working fine in 8.04 before upgrading.

Suggestions appreciated! :)

---

### Post by Irishpolyglot on 2008-11-02
BUMP!
No ideas on this then? Anyone else having the same issue as me?

---

### Post by IanShuttleworth on 2008-11-04
I am also having this problem, no idea what to do.

---

### Post by easoukenka on 2008-11-04
What if you edit /etc/X11/xorg.conf and change the nvidia to nv after driver.  This will turn off your nvidia proprietory drivers and use the standard.  

Not a fix obviously but could point you in the right direction.

---

### Post by Irishpolyglot on 2008-11-08
> **easoukenka said:**
> What if you edit /etc/X11/xorg.conf and change the nvidia to nv after driver.  This will turn off your nvidia proprietory drivers and use the standard.  

Not a fix obviously but could point you in the right direction.

Thanks for the suggestion. I tried that and rebooted but was greeted with the same blank screen unless I selected Failsafe Gnome.
When I press CTRL+Alt+Backspace the terminal displays > Not starting K display manager. It is not the default display manager before I'm back in the log on screen. Not sure if that's relevant.

Any other suggestions? :)

---

### Post by joshsmith on 2008-11-08
log in using gnome safe mode. 
create a new user. 
log out/restart. 
try logging in as that new user (not in gnome safe mode). 
report back if that works

---

### Post by Irishpolyglot on 2008-11-08
> **joshsmith said:**
> log in using gnome safe mode. 
create a new user. 
log out/restart. 
try logging in as that new user (not in gnome safe mode). 
report back if that works

There is no Gnome Safe Mode among my options for logging in. How do I go about having it there? Instead of the default (blank screen) or just Failsafe Gnome mode (everything works perfectly, but I shouldn't have failsafe as my standard log-in) I tried just "GNOME" and it gave me the following error:

> /etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale = en_IE
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/xmodmap: unable to open file '/usr/share/apps/kxkb/ubuntu.xmodmap' for reading
/usr/bin/xmodmap: 1 error encountered, aborting
Unable to create /home/benny/.dbus/session_bus
Couldn't exec /usr/bin/pulse-session: No such file or directory

Then I tried selecting the kde desktop and I got this error instead:
> Xsession: unable to launch /usr/bin/startkde X session ---
/usr/bin/startkde not found; falling back to default session
which gives the blank screen of course.

---

### Post by joshsmith on 2008-11-08
ok failsafe gnome mode, whatever it is called...

try the above steps that i said, and report back.

---

### Post by Irishpolyglot on 2008-11-08
> **joshsmith said:**
> ok failsafe gnome mode, whatever it is called...

try the above steps that i said, and report back.

I created a new user and the conditions are exactly the same for that account. It can only be accessed through Failsafe Gnome.

---

### Post by giacomo.c on 2008-11-11
i'm having a similar problem with my own upgrade... luckily fluxbox isn't really effected by most of the stuff that went sour, just gnome.

so for the dbus error in what you posted, i had that and i did
```
sudo rm -rf ~/.dbus
```
and it fixed that problem, but for the
```
/usr/bin/xmodmap:  unable to open file '/usr/share/apps/kxkb/ubuntu.xmodmap' for reading
```
i have no idea... 
i'm also having troubles with gconf being completely blank :( so i get about a hundred of
```
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Could not send message to gconf daemon: Message did not receive a reply (timeout by message bus))
```
with no real idea of how to fix that either, but it seems you're not quite in as bad of shape as myself.

but from what i can tell, it seems like you have a problem with the new xorg that 8.10 is using...  and for that, i have no idea how to fix.

i'm probably going to install debian in a few minutes after i find no answers and my home directory is finished backing up :)

good luck

---

### Post by motin on 2008-11-19
Bug report: Bug report: [https://bugs.launchpad.net/ubuntu/+bug/300028](https://bugs.launchpad.net/ubuntu/+bug/300028)

---

### Post by yussri on 2008-12-03
I confirm the same problem here , am unable to log to my gnome-session 
with unable to open file /usr/share/apps/kxkb/ubuntu-xmodmap for reading 
however am unable to locate folder /kxkb  (it isn't exist)


also when I tried to login using gnome-failsafe 
I had the following error message 
there is aproblem with the configuration server 
usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256 
this problem just appeared with yesterday update (am not sure which) 

reconfigure xserver  didn't help 
login as other user didn't help either 

and I don't believe it is display driver specific as I have Intel with no restricted driver  

should I report this as a bug , is there any solution or workaround

---

### Post by Irishpolyglot on 2008-12-20
Thanks for reporting that bug! I accepted the minor distro update today and after a reboot the problem no longer exists!

---

### Post by rgonnering on 2009-02-26
I have the same problem. 

I updated to 8.10 using Update Manager. Now I can't get a menu unless I use the default Gnome. I'm not sure if it's related, but I also started getting a message about can't find Human... when I log out.

Can't figure this out. I clearly is NOT SOLVED.

It's probably not for this thread, but there is a big, ugly yellow flower in the login screen.

Thanks for any help

---

