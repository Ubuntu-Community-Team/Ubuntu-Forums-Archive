---
title: "k3b will not launch"
date: 2008-08-17
forum: General Help
---

### Post by cchase88 on 2008-08-17
Hey everyone, I've read through a couple of other threads involving a similar problem, but the resolutions from those threads didn't seem to work for me.

Here is what I'm trying to do: I made a backup of a DVD which created .vob files. After searching for an appropriate application that can burn these files I came across k3b. I used the Add/Remove program that is found under the Applications menu on Ubuntu to install k3b. When I navigate to and click k3b from the Sound & Video menu, nothing happens. I try running from the command line and I get this:

```
/usr/bin/iceauth:  creating new authority file /home/cchase88/.ICEauthority
/usr/bin/iceauth: /tmp/dcopPfMg8b:1:  bad "add" command line
/usr/bin/iceauth: /tmp/dcopPfMg8b:2:  bad "add" command line
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
ICE Connection rejected!

DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
DCOPServer self-test failed.
ICE Connection rejected!

iceauth:  creating new authority file /home/cchase88/.ICEauthority
kdeinit: DCOPServer could not be started, aborting.
ERROR: KUniqueApplication: Can't setup DCOP communication.
```

I tried the Windows trick of uninstalling and reinstalling, but I get the same problem. I read in one thread to delete the /.ICEauthority, so I did, restarted and still the same problem.

Any ideas?

---

### Post by cchase88 on 2008-08-18
No one? Really? Don't make me install XP on my second hard drive just to do this! :lolflag:

---

### Post by kuja on 2008-08-18
maybe worth trying, I'm not sure --

```
sudo chown -R $USER:$USER ~
```

---

### Post by cchase88 on 2008-08-18
I'm not really sure what that does, but I' guessing that it adds me to the group that can read that file. I've tried starting k3b using the sudo command, but still get the same error, which I believe would be the same as giving myself read rights to the file.

---

### Post by cchase88 on 2008-08-18
I just tried installing k9copy (another KDE app) to see what happens. It installed correctly, but when I start it it throws errors that the dcopserver isn't running. I read the man pages on both dcop and dcopserver, but didn't find it very useful when it comes to my problem. I think I'm getting closer though. Anyone know how to *start* the dcopserver?:confused:

---

### Post by kuja on 2008-08-18
Well, you could try the "dcopserver" command ...

By the way, starting graphical apps with sudo is a very bad idea.

---

### Post by editrix on 2008-08-19
Sounds like something went wrong with your install. I use KDE, so I can't tell you how to do this in Gnome, but I'm sure you can edit menus somehow. Check what the command to launch K3b is. In my KDE menu, it's 
**k3b %U**

And kuja is quite right. If you feel you must launch a graphical app as root, the command is (I believe) gksudo.

---

### Post by cchase88 on 2008-08-19
> **kuja said:**
> Well, you could try the "dcopserver" command ...

By the way, starting graphical apps with sudo is a very bad idea.
When I enter dcopserver into the command line, I get the same error as if I were to enter k3b. It definitely looks like this is a dcopserver error though, not a k3b one.

[QUOTE=editrix]Sounds like something went wrong with your install.[/QUOTE]
I've uninstalled and reinstalled using both the Add/Remove program and Synaptic Package Manager

[QUOTE=editrix]I use KDE, so I can't tell you how to do this in Gnome, but I'm sure you can edit menus somehow. Check what the command to launch K3b is. In my KDE menu, it's
k3b %U[/QUOTE]

k3b %U is used on my system as well. I get the same error as before.

[QUOTE=editrix]And kuja is quite right. If you feel you must launch a graphical app as root, the command is (I believe) gksudo.[/QUOTE]

Didn't know that. Thanks.

---

### Post by editrix on 2008-08-21
If you're feeling ambitious, search uboontu.com (last link in my sig) for dcopserver. I just did a quickie and it looks like you're not the only one with the problem.

---

### Post by SuperMau on 2009-02-19
In my case the problem was due to my host name having a space in it (main server). I changed it (server) and everything works fine. Hope this helps...

---

