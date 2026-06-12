---
title: "[SOLVED] Remote Login: Ubuntu to Xubuntu?"
date: 2008-08-26
forum: General Help
---

### Post by bconover on 2008-08-26
So, installing Ubuntu a while ago for the first time, I noticed a buch of options pertaining to "Remote Login". I assumed this meant that one could log into another computer running an Ubuntu system, be that Ubuntu, Kubuntu, or Xubuntu.

Many months later. in the present, my latest set up was that of an older machine that everyone thought had seen it's end long ago. But, I installed Xubuntu (since I have heard and seen that the XFCE desktop is much lighter than GNOME of KDE) on the machine, and it is running so well it could be a new machine!

Now, I decided to test out that "Remote Login" option. I set up both computers following various tips from the interwebs. But when I try to log in via Remote XDMCP on my main Ubuntu machine, the only machine displayed is the local Ubuntu machine itself! I type in the IP of my Xubuntu machine, but no luck, I get a message saying that the machine isn't responding, and that it may not be turned on, or it can not be remote logged into. Like I said, everything looks setup, and I have the Xubuntu machine waiting at the login screen.

I assumed that things would go far smoother since XFCE is closely related to GDM. But I haven't had any luck. I can't even get a VNC server to connect properly (all vnc servers I've tried, like vnc4server and tightvncserver, either give me a gray screen and a console, or a gray screen, an "X" mouse, and no console. The actual running desktop refuses to load no matter what. I got the window manager to work once using risky sudo command, but that just put an XFCE styled window decoration over the console!)

So, how can I set up my Xubuntu machine correctly to actually connect to it. I've seen a few others posting this question: which never really got an answer. I would prefer Remote XDMCP, but if I can just get a VNC server to load the actual XFCE session, I'll be happy too.

P.S.: Also, if possible, how can I set up to connect from my Ubuntu laptop to my Xubuntu machine over the internet? So I can log into from anywhere, not just on my own router. This probably isn't the most secure thing, but I'm not really too worried about security, I'm not sending government secrets or personal info or anything from my Ubuntu machine to my Xubuntu machine. :-$

---

### Post by rbc on 2008-08-26
Can't help you with remoting over the internet. I am still working on that one myself, but as far as the intranet goes, have you allowed the Xubuntu machine to be viewed? In terminal, type "vino-preferences" (without the quotes), and make sure the box for "Allow others to view you desktop" is checked. Sorry if you have already done this, and I am just suggesting something stupid, but it's the first thing that came to mind

---

### Post by bconover on 2008-08-26
I don't think vino is installed. I did sudo apt-get install vino, which installed "vino-preferences", but it doesn't seem to activate any kind of server. Executing the command "vino" only gives me a "command not found" error.

---

### Post by rbc on 2008-08-26
Sorry that didn't work. I installed vino, vinagre, and every other remoting application I could find when trying to figure out how to remote from the internet, so I am probably assuming you have a lot of apps that you may not, plus my Xubuntu laptop is using gnome not xfce. Did you actually type vino-preferences or just vino? Can you ping the Xubuntu machine?

---

### Post by bconover on 2008-08-27
I typed "vino-preferences" in a terminal, which gave me a message saying that vino was not installed, and could be installed via apt-get. So, I used sudo apt-get install vino, which installed. However, the command "vino" simply says "bash:vino:command not found". "vino-preferences" however pops up a window of settings like the one I get through clicking System>Preferences>Remote Desktop in Ubuntu w/ GNOME on my main machine (leading me to believe vino is the default GNOME Remote Desktop app?). However, setting the settings so that I can view and control my desktop remotely does not actually seem to start any kind of server to connect to. I made sure to kill all other VNC/Remote Desktop apps I have installed before doing any of this.

My priorities have somewhat changed. The Xubuntu machine will soon be w/o a monitor (as I need the one I'm using on it for a more important machine). Thus, I need some way to control it from my main machine. I don't so much need internet access to it, as I will desperately need local access to it. The Xubuntu machine is connected wirelessly to a Linksys wired/wireless router, to which all my internet-connected machines are hooked into, including my main Ubuntu machine, which is hardwired to it via Ethernet cable.

I now need to know how to connect to the machine, whether that be over a VNC or Remote XDMCP. It would seem that Remote Login on XDMCP would be faster, so how do I go about setting up my Xubuntu machine to be logged into from my main machine on the local network?

---

### Post by mssever on 2008-08-27
> **bconover said:**
> I now need to know how to connect to the machine, whether that be over a VNC or Remote XDMCP. It would seem that Remote Login on XDMCP would be faster, so how do I go about setting up my Xubuntu machine to be logged into from my main machine on the local network?
I recommend against XDMCP as it's quite insecure. If you want VNC, you can use vino. The server is called vino-server. You need to call that in your login process somewhere so you can use vnc.

I also strongly recommend that you install openssh-server on your server and openssh-client on your client(s). If you enable the ForwardX11 option, then you can run GUI apps on your server, and they'll appear directly on your client. I personally use both SSH and VNC extensively on my server.

---

### Post by bconover on 2008-08-27
Using "vino-server" in a terminal returns a command not found error as well. I'm reinstalling vino to check that everything installed right.

---

### Post by bconover on 2008-08-27
Nothing is linked to "vino-server". How do I call this up at login then?

---

### Post by rbc on 2008-08-27
OK. At the Xubuntu computer, you ran vino-preferences, and set that computer to be viewable? Now go to the Ubuntu computer, and use Remote Desktop Viewer or Terminal Server Client to connect

---

### Post by mssever on 2008-08-27
> **bconover said:**
> Nothing is linked to "vino-server". How do I call this up at login then?
My bad. I should have looked at my startup scripts before answering. vino-server is part of the vino package, but for some reason it isn't on the $PATH. In my IceWM startup file, I call it as ```
/usr/lib/vino/vino-server &
```In Gnome, it gets started automatically for me, without any explicit configuration (unless I did something a long time ago that I no longer remember).

EDIT: If you aren't in Gnome, it's possible that you might have to start gnome-settings-daemon before vino-server (since vino is a Gnome app). But I don't know that for sure.

---

### Post by bconover on 2008-08-27
> **mssever said:**
> My bad. I should have looked at my startup scripts before answering. vino-server is part of the vino package, but for some reason it isn't on the $PATH. In my IceWM startup file, I call it as ```
/usr/lib/vino/vino-server &
```In Gnome, it gets started automatically for me, without any explicit configuration (unless I did something a long time ago that I no longer remember).

EDIT: If you aren't in Gnome, it's possible that you might have to start gnome-settings-daemon before vino-server (since vino is a Gnome app). But I don't know that for sure.

Solved! Thanks a ton. Using this, I have access to the actual desktop. 

I'm not too worried about security, but I'll look into SSH. But as of now this problem is solved.

---

