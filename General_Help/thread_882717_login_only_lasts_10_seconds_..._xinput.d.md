---
title: "login only lasts 10 seconds ... xinput.d?"
date: 2008-08-07
forum: General Help
---

### Post by Ian_McCrum on 2008-08-07
Hi, I have installed 8.04 on a number of machines both real and virtual (VMWare). I am in the UK and use british keyboards.

I keep getting errors after a few days that means I cannot login.

I try to login and get a message

"Your session only lasted 10 seconds..."

~/.xsession-errors says...

"/etc/gdm/Xsession: Beginning session setip...
Setting IM through im-switch for locale=en_GB
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
mkdtemp: private socket dir: Permission denied"

I can only login to a safe terminal session.

Any ideas anyone?
tia
Ian McCrum

__
[email]IJ.McCrum@ulster.ac.uk[/email]

---

### Post by Ian_McCrum on 2008-08-07
Upon googling Mkdtemp and Ubuntu it transpires that 

chmod 777 /tmp

fixes this. Wonder why? I have been crosscompling complete linux kernels and filesystems (ramdisk) so maybe I ran out of some resource or other and tmp got broken.

I suspect the sticky bit or something should be set as well...

that's all for now
Regards to all
Ian

__

---

### Post by Vivaldi Gloria on 2008-08-07
> **Ian_McCrum said:**
> I suspect the sticky bit or something should be set as well...


Yes. Use

```
sudo chmod 1777 /tmp
```

---

### Post by Ian_McCrum on 2008-08-07
Thanks, I have just checked an unbroken (as yet) ubuntu and it has permissions rwxrwxrwxt, and the broken versions have rwxr-xr-x so my code is breaking it. (it is from arm.cirrus.com)

I am running a crosscompilation script that does a few funny things like "fakeroot" and chmod. It also creates it's own "/tmp" in the freshly created filesystem image so there is probably a mistake there somewhere.

Bye for now
Ian

__

---

### Post by armenpn on 2009-03-13
I also meet such problem. but my log info is :

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
export: 1: -d: bad variable name

anyone can help me ? thanks.

---

### Post by Ian_McCrum on 2009-03-14
Hi, I hae seen several different error messages caused by the permissions on /tmp being changed.

Is this your problem?

Check by logging in using text mode and running 

```
ls -ld /tmp
```

if the permissions are not drwxrwxrwt then you have my problem.

in the text terminal enter

```
chmod 1777 /tmp
```

logout and login normally

hope that fixes it
good luck
Ian McCrum

__

---

### Post by coldmack on 2009-03-15
I tried what was suggested but nothing happend at all. AN ideas?

---

### Post by bakedbeans4life on 2009-03-15
> **Ian_McCrum said:**
> Thanks, I have just checked an unbroken (as yet) ubuntu and it has permissions rwxrwxrwxt, and the broken versions have rwxr-xr-x so my code is breaking it. (it is from arm.cirrus.com)

I am running a crosscompilation script that does a few funny things like "fakeroot" and chmod. It also creates it's own "/tmp" in the freshly created filesystem image so there is probably a mistake there somewhere.

Bye for now
Ian

__

Why do you need "fakeroot"? The last time I came across this was to enable 32bit programs to work on a 64 bit system. What script are you using and what does it do? It may help others to diagnose your problem. What is this script you mention and where did you obtain it?

---

### Post by coldmack on 2009-03-15
Alright so I am running HP MIE which is Hardy based. So when I try to log in as xclient manager I get the same exact error, but when I log in as gnone the error is gone. Oddly enough they both log me into the same HP MIE interface. And it seems like all my files and sessions settings are the same. So is there any ideas as to why this is so, and how I can get this error fixed? Thank you.


What the exact error says.
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/share/ume-config-common/ume-gui-start: line 11: /usr/lib/sapwood/sapwood-server: No such file or directory
find: /usr/share/autostart: No such file or directory
matchbox-wm: unable to open theme: /usr/share/themes/mobilebasic/matchbox/theme.xml
/usr/share/ume-config-common/ume-gui-start: line 18: /usr/bin/hildon-desktop: No such file or directory
sudo: unable to resolve host alex-umpc
boot-phase ui-started
/usr/share/ume-config-common/ume-gui-start: line 18: exec: /usr/bin/hildon-desktop: cannot execute: No such file or directory


any ideas please?

---

### Post by coldmack on 2009-03-15
Should I be installing hildon because it looks like it is designed for devices like the Nokia Tablet and Linux PDA of the sort. I am starting to notice that loging under gnome, it stuff like Openoffice, firefox and such work a little slower compared to xclient or what not.

When I type it ls -ld /tmp it shows drwxrwxrwt 13 root root 4096 time /tmp in green. This is suppose to be normal right? I tired what was suggested to do next but I get this message.
chmod: changing permission of `/tmp':Operation not permitted 
I am the main/root user and I did this under the sudo command, but yet I get the error. Any ideas?



Alright I tired to install hildon and it worked but this is the message I get now. 
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/share/ume-config-common/ume-gui-start: line 11: /usr/lib/sapwood/sapwood-server: No such file or directory
find: /usr/share/autostart: No such file or directory
matchbox-wm: unable to open theme: /usr/share/themes/mobilebasic/matchbox/theme.xml
sudo: unable to resolve host alex-umpc
boot-phase ui-started

** (hildon-desktop:9870): WARNING **: Could not load default background: No such file or directory

(harbour-launcher:9983): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


** (harbour-launcher:9983): WARNING **: Only handling menu item entries in sub-menus.

** (harbour-launcher:9983): WARNING **: Only handling menu item entries in sub-menus.

** (harbour-launcher:9983): WARNING **: Only handling menu item entries in sub-menus.

** (harbour-launcher:9983): WARNING **: Only handling menu item entries in sub-menus.

(harbour-launcher:9983): Gtk-CRITICAL **: gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

** (hildon-desktop:9870): WARNING **: Error reading file '/usr/share/applications/hildon-control-panel'

---

### Post by lesbaker on 2009-03-16
reinstal the os?

---

### Post by Ian_McCrum on 2009-03-16
Hmmm, this thread is getting crowded; Is Armenpn's problem ok?

(1) re BakedBeans4Life's question. I am compiling a complete kernel and filesystem for an embedded ARM board - the board comes with a nicely setup set of scripts, makefiles etc in many nested directories to build hundreds of executables as well as getting parceled up with a initial compressed flash image that can be downloaded and unpacked into RAM on the target board. To understand the scripts I would need to study autoconfigure and automake and this would take a distractingly long time. My workaround will work for me for the immediate future so it is peripheral to the current thread (the start of the thread was a very specific problem - "When I log in I get bumped out within 10 seconds" and changing the permission of /tmp fixes this for me). The complete development environment is at [http://arm.cirrus.com](http://arm.cirrus.com). If you still want to play with it, email me and we'll start a fresh thread. I can copy it to the ARM Cirrus forum...

(2) re ColdMack your problem is different. - 

Starting an X session and having lots of missing files. Coldmack do the following files exist?

/usr/lib/sapwood/sapwood-server
/usr/bin/hildon-desktop
/usr/share/autostart
/usr/share/themes/mobilebasic/matchbox/theme.xml
/usr/share/applications/hildon-control-panel

It also looks like you need to add an entry for the host alex-umpc - maybe in etc/hosts?

You have not given enough detail, or at least, I am not familiar with what you are trying to do. You should start a new thread and give a couple of pages description about what you are doing.

Kind regards
Ian McCrum

__

---

### Post by lesbaker on 2009-03-16
No, I think he gave a good amount of info, granted it lookes like he installed Hildon which is the GUI for MID and internet tablets. Because in that first post I don't see anything relating to control panel. I do see something about en_GB thought that maybe causing the issue? Then again I am just a simple noob, looking at it through the eyes of someone who is pretty good with the OTHER unix based os.

---

### Post by coldmack on 2009-03-16
I uninstalled Hildon so I am pretty much back to the first issue again. So, none of those files exist and for some odd reason or another(made a thread about this) I am not able to get root Nautilus access to add, change or delete files. I read that I should use konqueror instead, but I have yet to try it. Thank you though.

---

### Post by timch on 2009-03-23
I have a very similar problem to the original post. If I login then I get a warning mesdsage about a 10sec login and can examine .xsession-errors. This says
/etc/gdm/Xsession: Beginning session startup...
Setting IM through im-switch for locale=en_GB
Start IM though /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.

That's it though. Nothing else. 
I using 8.10 and have just done an update (23/Mar/09) which required a restart and then this.
I can login as another user so it is not system wide - just my login is messed up.

Any help appreciated
Tim

---

### Post by coldmack on 2009-03-23
Have you thought about just backing all your files up and doing a clean install?

---

### Post by timch on 2009-03-24
Solved the problem.
The sysadmin had created a fiel ".xsession" which contained one line "umask 002". This was setting the umask for acess to the main server. However on updating ubuntu, the version of gnome chnaged and in later version the .xsession file is used to define the session. So removing the .xsession file solved the problem.

---

### Post by guarinc on 2009-09-14
I have the same problem as timch above, however, there is one additional line in the error "bind: Permission denied"
I did the "chmod 1777 /tmp" suggested above to no avail.  There is no ".xsession" file anywhere on my system.  I changed the permission of the "/etc/X11/xinit/xinput.d/default" file to match that of "...all_ALL" also to no avail.  I have no other logons to check...
HELP!

---

### Post by sirius1 on 2010-06-12
> **Ian_McCrum said:**
> Hi, I have installed 8.04 on a number of machines both real and virtual (VMWare). I am in the UK and use british keyboards.

I keep getting errors after a few days that means I cannot login.

I try to login and get a message

"Your session only lasted 10 seconds..."

~/.xsession-errors says...

"/etc/gdm/Xsession: Beginning session setip...
Setting IM through im-switch for locale=en_GB
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
mkdtemp: private socket dir: Permission denied"

I can only login to a safe terminal session.

Any ideas anyone?
tia
Ian McCrum

__
[email]IJ.McCrum@ulster.ac.uk[/email]

Perfect description . . . did you ever get a logical fix for the above, without having to rebuild the watch? (As in clock)

I'm just delving into this, this morning, but it seems like deleting one of these files should fix it:

.gconfd
.gconf
.gnome2
.gnome2_private
.config

Yes/No?

---

