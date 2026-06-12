---
title: "problems with Remote control / VNC-server"
date: 2005-11-20
forum: General Help
---

### Post by Quacka on 2005-11-20
I don't know how to configure remote control.

In the past I used a windowsXP-machine, that I used as download-pc (run p2p-progs 24h a day). The pc wasn't connected to a monitor or keyboard.
I controlled this pc from my game-pc with VNC Viewer (and server installed at the download-pc). I only needed to push the "ON"-button at the pc.

Now I wanted to use a pc with Kubuntu as download-machine. I installed all necessary p2p-programs.
The only/main problem now is the remote control.

I read a lot of solutions, but none of those helped me.

I tried to install the vnc4server with this HOW-TO: [http://www.ubuntuforums.org/showthread.php?t=76638](http://www.ubuntuforums.org/showthread.php?t=76638)
It didn't help.

I installed Tightvnc. I can run it. It creates a 'new' 'X'-Desktop and created a log-file. When I try to connect to the Ubuntu-pc I get a failure.

The only thing that 'helped' was to use "desktop-sharing" (krfb). When I use this, then I can connect to the Kubuntu-pc with my windows-xp-pc. This isn't a solution because I need to accept the connection at the Kubuntu-pc.

So who can help me with this?

---

### Post by JimmyJazz on 2005-11-20
sudo apt-get x11vnc

---

### Post by JimmyJazz on 2005-11-20
actually that would be sudo apt-get install x11vnc
then run it when you start up kubuntu

---

### Post by Quacka on 2005-11-21
this was the solution:
[http://www.ubuntuforums.org/showthread.php?t=44836&highlight=vnc+grey](http://www.ubuntuforums.org/showthread.php?t=44836&highlight=vnc+grey)

One problem left: 
I still need to login local at this pc and manually start "vncserver".
After that it works.

How can I start this "vncserver" automatically when I startup this pc?
I only want to login from a remote place AND not locally at the pc.

---

### Post by Beestar on 2005-11-21
Great question!  Unfortunately I don't have an answer... :( 

Seriously, I have this problem too and for more than a year have I been searching the Internet.  First, I thought I was the only person having this problem, because there was so little on the Internet about it.

The question is simple: how can I let remote control work exactly as VNC on Windows (XP)?
On Windows I can reboot the machine, and after reboot remotely connect to it, because VNC server runs as a service.
On Kubuntu, after reboot, I have to physically go to the server and log in first.  This is... not so nice.

This post is not meant as a "poor me" story, no way!  I just want Quaka to know he is not alone...

Greetz,


Bee

---

### Post by Quacka on 2005-11-21
exactly, that's the problem.

Maybe someone can help us both :)

---

### Post by gypsy98101 on 2005-11-21
Dang, I just posted a whole lengthy step-by-step for this but it got eaten by the ether-bugs.  Here's the condensed version:
I am using TightVNC on my windows box.  I had to add an entry in the registry under <HKLM:Software:Microsoft:Windows:CurrentVersion:Run> that points to the VNC server excecutable.  There was already one there, but it included some switch that must have prevented an actual server session.  
Then I could connect without having to login on the Win box.

---

### Post by gypsy98101 on 2005-11-21
Ooops.  I may have read this wrong.  If you want to know how to remote control the linux box without loggin in, then my reply doesn't fit.  Mine was for remoting Win box without logging in.

---

### Post by skyboy on 2005-11-21
> The only thing that 'helped' was to use "desktop-sharing" (krfb). When I use this, then I can connect to the Kubuntu-pc with my windows-xp-pc. This isn't a solution because I need to accept the connection at the Kubuntu-pc.

you can configure it to automatically accept remote connection. I use it everyday like that.
Start  Krfb and click configure and set it the way you want.
Or you can also set an invitation.

---

### Post by Quacka on 2005-11-21
[QUOTE=skyboy]you can configure it to automatically accept remote connection. I use it everyday like that.
Start  Krfb and click configure and set it the way you want.
Or you can also set an invitation.[/QUOTE]
The problem is that I first need to login to the kubuntu-pc. Not from remote control, but locally.

I know I can set kubuntu to automaticaly login a specified user, but that's not exactly what I want to do.

I want to use tightvnc/vncserver. 
I want to start this service automatically with the start of the kubuntu-system, so before the login-screen appears. (or at the same moment)
It must be possible, I think. But how?

---

### Post by rcerreto on 2005-11-21
FreeNX allows you not only to connect to an existing session but also to start a new one from remote.
I'm using it on a headless Ubuntu box and it works pretty well: performances are great, while stability is so and so.

Yuo can find a HowTo in the forums:
[]("http://www.ubuntuforums.org/showthread.php?t=1968&highlight=freenx")

HTH

---

### Post by Quacka on 2005-11-21
[QUOTE=rcerreto]FreeNX allows you not only to connect to an existing session but also to start a new one from remote.
I'm using it on a headless Ubuntu box and it works pretty well: performances are great, while stability is so and so.

Yuo can find a HowTo in the forums:
[]("http://www.ubuntuforums.org/showthread.php?t=1968&highlight=freenx")

HTH[/QUOTE]
tightvnc starts also a new session from remote.
I only need to start the service vncserver, before I can open a session from remote.
Thats the problem.
As far as I know it would be the same when I use FreeNX: I first need to start the service at the pc, before I can open a new session from remote.

---

### Post by Beestar on 2005-11-22
Apparently there's some confusion about the problem.  Let me try to clarify.

WHAT WE WANT TO ACCOMPLISH (PART 1)
Imagine a headless, mouseless and keyboardless server, it only has electrical power and Ethernet to your home network, located some where in your basement or attick.  This server does all kinds of usefull stuff, serving webpages or whatever.  Also a remote desktop server (like VNC server) runs on this physical barely reachable server.  You administer this server from your warm and cozy living room via your home network using remote desktop control, say VNC viewer.

Now imagine, that for one reason or the other, the machine needs to be rebooted.  So using VNC viewer you click on the server's desktop Shutdown and Reboot (or something simular).  Shortly hereafter your VNC viewer will give an error message: "Connection to host broken".  Of course, the VNC server doesn run any more. ;) 

Now comes the magic part.  You wait a few minutes, then you start VNC viewer in the living room and voila! you see the WindowsXP's login screen (with all the users' names on it to choose from).  You take your pick and continu working on the stufed away server.

WHAT WE WANT TO ACCOMPLISH (ADVANCED PART (PART 2))
Imagine you are ready with your work on the server.  It runs a program on the desktop that needs to stay open (it calculates pi or whatever). Since you want to go to bed, you close your VNC viewer.

Now comes the (advanced) ultra super turbo magic part. :)
After a few days you are comfortably sitting in your living room and you start your computer and VNC viewer.  You connect to your working-in-the-dark server and Wow! you see the desktop EXACTLY AS YOU LEFT IT a few days before (only with more numbers for pi, of course ;) ).
This is usually referred to as consistent or persistent desktop connection.

THE PROBLEM
Is the above scenario impossible, rocket science or miraculous?

Not at all.

If the server runs Windows (XP for example) and VNC server, this works exactly as described.  In fact, even though I can't remember for sure, this is VNC server's default behaviour.

The problem is you want to run Kubuntu (or Ubuntu or whatever Linux version) on that server.  :D

LINUX' BEHAVIOUR
1. After reboot, you cannot connect to the server with VNC viewer, because VNC server doesn't run yet.  You have to phically go to the server, plug in a keyboard and monitor, log in and start a VNC server.  This is, as you might have guessed, is a real pain in the neck. ;)

2. There are solutions with VNC server starting directly from reboot, however, when you connect to the server, you get presented a NEW desktop each time you connect.  So when you close the VNC viewer, the server's desktop with the pi calculating application is thrown away.
VNC's documentation briefly discusses persistent desktop connections, but I just can't get it to work.


Any help which leads to having (K)Ubuntu run on the server is MUCH appreciated.
 

Bee

---

### Post by geo on 2005-11-22
I have a remote VNC connection to a headless ubuntu box, achieved by using this advice:

[http://www.ubuntuforums.org/showthread.php?t=76638&highlight=gdm+vnc]("http://www.ubuntuforums.org/showthread.php?t=76638&highlight=gdm+vnc")

This results in a new GDM login window each time you connect with a VNC client. To make it keep your ubuntu desktop session alive, even when you close the VNC session on your PC, ensure your /etc/xinetd.conf has the **wait = yes**

```
service vnc
{
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = nobody
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -broadcast -geometry 1400x1000 -depth 16 -once -fp /usr/share/X11/fonts/misc -securitytypes=none
}

```

---

### Post by feathers on 2005-11-22
I don't know your exact problem but you can always configure services to start on boot. You must use a script that only start the vnc server ( one line with the startcommand in a textfile which is executable) and place this or a link in /etc/rc.2/. Name the file something like S90-myserver. This should start the vnc server. If this is enough to connect to the computer I do not know. If you do not have a monitor for this computer, you can use ssh to do the configuration.

---

### Post by rcerreto on 2005-11-22
[QUOTE=Beestar]

LINUX' BEHAVIOUR
1. After reboot, you cannot connect to the server with VNC viewer, because VNC server doesn't run yet.  You have to phically go to the server, plug in a keyboard and monitor, log in and start a VNC server.  This is, as you might have guessed, is a real pain in the neck. ;)

Bee[/QUOTE]

That's exactly why I'm using FreeNX. Me too, I'm not happy to attach monitor, keyboard and mouse to my headless ubuntu box whenever I need to reboot it.
I know that's possible to have similar functionalities via gdm+vnc but I tried freenx and it was pretty easy to setup.

Any time you reboot your headless box, nxserver gets restarted (at worse you can restart it from a command line using ssh, but I never had to).
Then you can start a gnome (or kde) session with nxclient.
When exiting, you will be asked whether you want to "terminate" or "suspend" the current session.
When restarting the client you will be able to choose whether to open a new session or to reconnect to an existing one.
Isn't that what you're looking for?

---

### Post by Beestar on 2005-11-27
rcerreto,

that is EXACTLY what I am looking for!  

Thank you, I will look into it.

I will also look into Geo's advice.

Thank you all!!


Bee

---

### Post by wabble on 2005-11-28
[QUOTE=Quacka]I don't know how to configure remote control.

In the past I used a windowsXP-machine, that I used as download-pc (run p2p-progs 24h a day). The pc wasn't connected to a monitor or keyboard.
I controlled this pc from my game-pc with VNC Viewer (and server installed at the download-pc). I only needed to push the "ON"-button at the pc.

Now I wanted to use a pc with Kubuntu as download-machine. I installed all necessary p2p-programs.
The only/main problem now is the remote control.

I read a lot of solutions, but none of those helped me.

I tried to install the vnc4server with this HOW-TO: [http://www.ubuntuforums.org/showthread.php?t=76638](http://www.ubuntuforums.org/showthread.php?t=76638)
It didn't help.

I installed Tightvnc. I can run it. It creates a 'new' 'X'-Desktop and created a log-file. When I try to connect to the Ubuntu-pc I get a failure.

The only thing that 'helped' was to use "desktop-sharing" (krfb). When I use this, then I can connect to the Kubuntu-pc with my windows-xp-pc. This isn't a solution because I need to accept the connection at the Kubuntu-pc.

So who can help me with this?[/QUOTE]

Just enable remote desktop. Also configure automatic log in and enable automatic screensaver (with password requirements to get back in). Then you can just turn the computer on. This is not a secure solution but just as secure as you have used before from what i could read.

I dont remember how to do all of this (not at my kubuntu desktop computer now) but i'm sure you can find it out ;)

---

