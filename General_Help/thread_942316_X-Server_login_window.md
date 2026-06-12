---
title: "X-Server login window"
date: 2008-10-09
forum: General Help
---

### Post by MrPickle12481632 on 2008-10-09
I've done a quick scan of the forums and I think I might be the first to  bring this up. Not really sure if it even counts as a bug or not, but basically I was playing around with the settings of the login box to become more well aquainted with my gnome system and see how everything kind of 'fit' together. I changed one setting for whether the login window was a "greeter" or a "chooser", not stopping to think what the difference was.

Apparently, "chooser" is a great tool to login to remote computers. However, the login window for the chooser gives no ability to login in to the local host at all, and no options for a session type of any kind.

What I'd like to know is where that particular .conf file for the login window is, and which line of code controls that option. Has anyone ever run into a situation like this at all?

---

### Post by MrPickle12481632 on 2008-10-09
I've so far checked nearly every .conf file with a name relating to the x-server, and so far, I'm empty handed. New question: is the setting for the login window (it was referred to as the "launch" in the configuration tool) changed within the application for X or Xorg itself?

---

### Post by EmanresuusernamE on 2008-10-09
If it's not allowing you to connect to the local host, try using this IP address:
127.0.0.1
By default, that's the local machine that you're connected too.

---

### Post by MrPickle12481632 on 2008-10-09
I've tried connecting to the local host and it says that the host is no active or not accepting logins- is it possible i need to enable my machine to accept incoming vpn traffic for that idea to work? If so, how can I enable the vpn host within a terminal?

---

### Post by EmanresuusernamE on 2008-10-12
Yeah, you'd have to enable your system to accept incoming connections for that to work.  However I don't quite no how to do that yet myself.  Have you tried booting into the Recovery Console (second boot option for a default install), and then try Repair X Server?

---

### Post by kablooee87 on 2008-12-17
I'm having this exact problem. Can't get into my system at all. Does anyone know how to change the setting back to greeter from terminal?

---

