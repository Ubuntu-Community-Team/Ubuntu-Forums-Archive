---
title: "Managing an X session from SSH?"
date: 2008-11-14
forum: General Help
---

### Post by spectre_25gt on 2008-11-14
Is there any way to manage an X session from SSH? I'm looking to build a kiosk system and I'd like to be able to hook into certain programs and make changes from the back end without actually logging onto the session that's displaying on the console. Better yet, are their any utilities out there that just throw a slideshow out via framebuffer or something like that?

Any input would be much appreciated. Thank you.

---

### Post by bodhi.zazen on 2008-11-14
It should be possible, what are you wanting exactly ?

the -X flag forwards X applications to your computer. If you need to acces X sessions running on the server, that is different.

ssh -X user@server

---

### Post by spectre_25gt on 2008-11-14
Well, I'd like to be able to have X up and running and displaying video on a monitor, but pass commands to that X session from an SSH session. For instance, is it possible to execute a program in a currently running X session from a separate SSH session?

---

### Post by bodhi.zazen on 2008-11-14
Yes it can be done.

You have two (or more) computers. One is the server. You ssh into the server from the client. So long as you have root access you can the do as you wish. Run an X application on the server and forward the output to the client. Run and X application and forward the output to and X session on the server. All this is possible.

If you want to share an X session you can forward a VNC session. Or you can open a separate X session over VNC.

All this is possible, and more.

---

### Post by spectre_25gt on 2008-11-14
"Run an X application on the server and forward the output to the client. Run and X application and forward the output to and X session on the server."

That sounds like what I'm looking to do. I'll go do some research on X forwarding. Thanks!

---

### Post by bodhi.zazen on 2008-11-14
> **spectre_25gt said:**
> "Run an X application on the server and forward the output to the client.

ssh -X user@server

> Run and X application and forward the output to and X session on the server."[http://ubuntuforums.org/showthread.php?&t=411622](http://ubuntuforums.org/showthread.php?&t=411622)

[http://ubuntuforums.org/showthread.php?t=504351](http://ubuntuforums.org/showthread.php?t=504351)


> That sounds like what I'm looking to do. I'll go do some research on X forwarding. Thanks!

---

### Post by spectre_25gt on 2008-11-15
Those links are perfect. Thanks again.

---

