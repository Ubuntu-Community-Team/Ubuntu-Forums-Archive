---
title: "vnc4server killed xwindows"
date: 2008-07-30
forum: General Help
---

### Post by bakechad on 2008-07-30
I am currently running Xubuntu 7.10

I installed vnc4server and could not get it to work.  I kept getting a .Xuthority locking error.  I looked in the forums and the suggested fix was to chown .Xauthority.  That didn't work, so I changed the permissions to 0755 and that didn't work.  The next suggestion said to delete the file and that didn't work.

Then it gets worse!  Now Xwindows will not start and I get:

> xauth:  creating new authority file /home/chad/.serverauth.5327




X: warning; process set to priority -1 instead of requested priority 0



Fatal server error:

Server is already active for display 0

        If this server is no longer running, remove /tmp/.X0-lock

        and start again.



Xlib: connection to ":0.0" refused by server

Xlib: Invalid MIT-MAGIC-COOKIE-1 key

giving up.

xinit:  unable to connect to X server

xinit:  No such process (errno 3):  Server error.

chad@vectra:~$ 


I then uninstalled vnc4server and Xwindows still doesn't work (same error).  When I try to forward an X app (this server has no monitor), I get the following error:

> chad@vectra:~$ sudo synaptic

X11 connection rejected because of wrong authentication.

The application 'synaptic' lost its connection to the display localhost:10.0;

most likely the X server was shut down or you killed/destroyed

the application.

chad@vectra:~$ 


It keeps recreating ~/.Xauthority and making root the owner everytime, no matter what I do and then gives me the locking error everytime I log in.

Does anyone have any suggestions, I would hate to reinstall the machine.

Thanks

Chad

---

### Post by bakechad on 2008-07-30
**UPDATE:**I just hooked up a monitor and Xwindows and Xfce are running with no problems.

So my outstanding problem is that vnc4server never worked and now I cannot forward any Xwindows applications.

---

### Post by cariboo on 2008-07-31
You don't need the full desktop running to do xforwarding, have a look at this page:

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

Scroll down to Running GUI Programs.

Jim

---

