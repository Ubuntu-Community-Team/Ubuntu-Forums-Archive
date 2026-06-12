---
title: "[SOLVED] Using bittorrent via SSH"
date: 2008-11-11
forum: General Help
---

### Post by ncanna1 on 2008-11-11
I SSH into my home computer from work in order to access files that I've been working on at home.  My home computer is using Ubuntu Intrepid and the work computer is a Windows XP box.  I found a book that I would like to torrent to use at work, but the torrent ports are blocked here, so I figured that I would use bittorrent or bittornado to download the torrent at home and then simply use sftp to get it to here.  There is a problem when I try to access this particular torrent, because the tracker requires registration.  I have an account with the tracker, but I am not sure how to log in to the tracker using only the command line, as this work computer has no way for me to see GUIs.

Is there a way that I can tell bittorrent to provide a username and password to a tracker whenever I try to access it?

---

### Post by ju2wheels on 2008-11-11
If you are having trouble doing it because of lack of GUI, then thats not really a problem. If you have X forwarding enabled on your ssh then you can forward the GUI to the other computer. For example, if your ssh client on your Windows box supports X forwarding then all you have to do is run the following command:

```

ssh -X user:pass@host.com firefox

```

This would launch Firefox on your server but show you the actual Firefox window on the machine you are using, almost like VNC but just for that one window...

---

### Post by ncanna1 on 2008-11-12
The problem is that the client on this work computer doesn't support X forwarding, so there's no way for me to show the GUI.

---

### Post by Portmanteaufu on 2008-11-12
You can get Cygwin and install it in a location that doesn't require admin rights (e.g. My Documents or your Desktop). Then you could run the X server they provide on Windows.

---

### Post by ncanna1 on 2008-11-12
Alright, I installed Cygwin to the desktop, but I can't seem to figure out how to get it to work in conjunction with SSH.  How would I run a program through SSH and get the Cygwin Xserver to display the GUI?

---

### Post by Portmanteaufu on 2008-11-12
Lucky for you, I figured out how to do this two weeks ago. :P

First, edit your /etc/ssh/sshd_config file on the machine you'll be accessing remotely. Have the file include the line 
```
X11Forwarding yes
```

Then, in your cygwin folder on the client machine, (my folder is C:\cygwin\usr\X11R6\bin), look for and run "startxwin.bat". That should start up the X server -- you'll see a black 'X' running in the lower-right-hand system tray.

Run Putty on the client box. In the navigation tree on the left, go to: 

Connection -> SSH -> Tunnels

And make sure that "Enable X11 forwarding" is checked. The X display location field should have "localhost:0:0". If it's blank, fill it in. Then, fill in your normal information and start the connection. If all the planets are aligned properly, you'll be able to type "firefox" and have it open the window on the client machine! (Note: It's probably going to be slow. Always give things a second or two to register.)

Hope that helps!

---

### Post by ncanna1 on 2008-11-12
Alright, that got it working!  Thanks a lot!

---

