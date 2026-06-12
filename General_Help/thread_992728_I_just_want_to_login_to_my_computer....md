---
title: "I just want to login to my computer..."
date: 2008-11-25
forum: General Help
---

### Post by nik_nah on 2008-11-25
I just want to login to my computer remotely cause it's a server and it doesn't have a screen.

Here's what I've tried...

* x11vnc, SEGVs as soon as I press a key or mouse button.
[https://bugs.launchpad.net/ubuntu/+source/vnc4/+bug/247669](https://bugs.launchpad.net/ubuntu/+source/vnc4/+bug/247669)

* vino(remote desktop), there's a bug here that causes it to only accept ipv6 connections.  Apparently it's fixed but I'm using 8.04 LTS and the fix isn't here yet...
[https://bugs.launchpad.net/ubuntu/+source/vino/+bug/196675](https://bugs.launchpad.net/ubuntu/+source/vino/+bug/196675)

* I can't use XDMCP because it won't forward over ssh.

* vnc4server, this actually works but various things are not working like the unlock button on all the admin menus are greyed out making most of the admin tools unusable.
[https://bugs.launchpad.net/ubuntu/+source/policykit/+bug/219473](https://bugs.launchpad.net/ubuntu/+source/policykit/+bug/219473)


All I want to do is login to the computer remotely like I do with a normal screen, is this possible?

thanks.

---

### Post by Choad on 2008-11-25
i guess you could try building vino from source for you machine? get the bug fixes without having to update to intrepid

---

### Post by cdtech on 2008-11-25
What do you want to run off of the server? Command line through "ssh" is as simple as "ssh user@yourserverip" if you want to forward "X" just use the ssh **-Y** user@yourserverip "xclock" command.

---

### Post by nik_nah on 2008-11-25
Unfortunately intrepid uses gnome 2.4, 8.04LTS is on 2.2 or something.
I can't compile it unless I upgrade the whole gnome.

I'd like to preferably run the gui admin programs from a windows machine cause it's in an office that only has windows machines.  And see the desktop and browse around the mounted drives, etc.  cause the people in the office aren't technical they would like a gui type interface.

It's kind of sad that there're so many ways to login to the gui remotely (x11vnc, vino, vnc4server) but none of them work 100%

---

### Post by krunge on 2008-11-25
> **nik_nah said:**
> 
* x11vnc, SEGVs as soon as I press a key or mouse button.
[https://bugs.launchpad.net/ubuntu/+source/vnc4/+bug/247669](https://bugs.launchpad.net/ubuntu/+source/vnc4/+bug/247669)

That's not x11vnc, it is something else (realvnc Xorg module).

Have you tried the real x11vnc?  It should work.

---

### Post by nik_nah on 2008-11-25
> **krunge said:**
> That's not x11vnc, it is something else (realvnc Xorg module).

Have you tried the real x11vnc?  It should work.

Thanks very much, it's working now.

---

