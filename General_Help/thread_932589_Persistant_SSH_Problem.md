---
title: "Persistant SSH Problem"
date: 2008-09-28
forum: General Help
---

### Post by rocketssss on 2008-09-28
This is very similar to this [thread]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=4915285") I found in search, but I couldn't resolve my issue with the advice there.

I am running an Ubuntu desktop without a screen or anything, and I SSH into it. My ISP requires occasional login to keep connected to the internet, so to keep it online so I can SSH in I wrote a firefox greasemonkey script to auto-submit the form for me, and set FF to reload a small webpage once every 10 minutes.

This works fine and dandy, but I need to be able to SSH in, start firefox, and disconnect SSH while leaving firefox running. I tried
```
ssh....
screen
firefox
Ctrl-A d
logout
```
and that hangs on the logout: it must be waiting for firefox to exit. I have also tried, as reccomended:
```
ssh...
nohup firefox &
logout
```
But that also hangs. Any ideas?

Thanks! :D

---

### Post by The Cog on 2008-09-28
I think the problem is that firefox launched from an SSH session can't find an X server to display on.

Using screen to launch a process is a good idea, but I think you prbably need to stick to non-X11 applications. A small script that runs wget or GET or ome other text mode utility will probably do the trick.

---

### Post by rocketssss on 2008-09-28
> **The Cog said:**
> I think you probably need to stick to non-X11 applications.

This means applications that don't have a GUI, right? I have no experience with WGET or similar I'm afraid.

---

### Post by SimonHickling on 2008-09-28
If you have X installed (or install it) on the headless (no display) machine you can use VNC to access graphical applications remotely.

This [link]("http://ubuntu-tutorials.com/2007/06/12/vnc-over-ssh-securing-the-remote-desktop/") explains how to run vnc over ssh if you need to use ssh.

---

### Post by mbeach on 2008-09-28
does the ssh -o option of TCPKeepAlive do what you need?

```
ssh -o TCPKeepAlive=Yes user@yourhost
```

edit:
some more detail at:
[http://pthree.org/2008/04/16/keeping-your-ssh-connection-alive/](http://pthree.org/2008/04/16/keeping-your-ssh-connection-alive/)

---

### Post by The Cog on 2008-09-29
You should be able to SSH to the existing GUI provided that it already has a user logged in. The link SimonHickling provided tells you how to set up the SSH tunnel but not how to set up the VNC server. To set up the VNC server, try this:

Under System -> Administration -> Login Window, go the Security tab and configure automatic login for the user you want.

Log in as that user and under System -> Preferences -> Remote Desktop, allow sharing. Under the Advanced tab, choose to only allow local connections. This means that only connextions tunnelled through SSH can connect.

---

### Post by rocketssss on 2008-09-29
> **The Cog said:**
> You should be able to SSH to the existing GUI provided that it already has a user logged in.

Okay, cool. I think VNC will work better for my purposes anyway, I'm not much of a command-line guy. I have VNC up and running, but the service doesn't start until someone has already logged in locally. Is that a limitation of VNC?

---

### Post by The Cog on 2008-09-29
I think so. That's why I said to configure auto-login.

---

