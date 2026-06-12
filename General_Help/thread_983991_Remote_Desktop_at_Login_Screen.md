---
title: "Remote Desktop at Login Screen"
date: 2008-11-16
forum: General Help
---

### Post by Lutrova on 2008-11-16
Very simple question. I need to know how to remotely connect to my Ubuntu box from a Windows box using VNC such that the Ubuntu login screen is there waiting for me to log in..._WITHOUT_ using SSH or using some third party service or software like GoToMyPC. Imagine my surprise the first time I had to reboot Ubuntu for something remotely only to find I could not connect anymore. Windows will at least let RealVNC server run as a service right from the very start and I have a login screen waiting for me. Why not Ubuntu?

I am connecting from work. Every single solution I have found in my searches requires the use of SSH (unacceptable) or some other inconvenient methods that simply will not work for my situation.

Is there a simple, straightforward solution to this? I really would rather not keep running Windows just to be able to remotely connect at my leisure even if I have to reboot.

---

### Post by lovinglinux on 2008-11-16
You should check the Ubuntu box firewall. I have two Ubuntu machines and one of them has Remote Desktop configure to accept connections from the other machine. The remote desktop service runs at boot. All I had to do was to configure it with System >>> Preferences >>> Remote Desktop.

---

### Post by Lutrova on 2008-11-16
I am afraid that it does not when it boots and goes to the login screen. My VNC client does nothing but return "connection refused" errors. The VNC server in Ubuntu does not actually start and/or accept connetions until I log into a desktop session, which is not what I want.

> **lovinglinux said:**
> You should check the Ubuntu box firewall. I have two Ubuntu machines and one of them has Remote Desktop configure to accept connections from the other machine. The remote desktop service runs at boot. All I had to do was to configure it with System >>> Preferences >>> Remote Desktop.

---

### Post by lovinglinux on 2008-11-16
> **Lutrova said:**
> I am afraid that it does not when it boots and goes to the login screen. My VNC client does nothing but return "connection refused" errors. The VNC server in Ubuntu does not actually start and/or accept connetions until I log into a desktop session, which is not what I want.

I see. You are correct. My machine is configure to login automatically, so when I reboot the Remote Desktop is loaded properly.

---

### Post by bodhi.zazen on 2008-11-16
> **Lutrova said:**
> Very simple question. I need to know how to remotely connect to my Ubuntu box from a Windows box using VNC such that the Ubuntu login screen is there waiting for me to log in..._WITHOUT_ using SSH or using some third party service or software like GoToMyPC. Imagine my surprise the first time I had to reboot Ubuntu for something remotely only to find I could not connect anymore. Windows will at least let RealVNC server run as a service right from the very start and I have a login screen waiting for me. Why not Ubuntu?

I am connecting from work. Every single solution I have found in my searches requires the use of SSH (unacceptable) or some other inconvenient methods that simply will not work for my situation.

Is there a simple, straightforward solution to this? I really would rather not keep running Windows just to be able to remotely connect at my leisure even if I have to reboot.

The ability to do this will depend on your vnc server on the Ubuntu box.

The built in vnc server uses a shared desktop. Try vnc4server.

Also I strongly advise you tunnel your vnc session over ssh. There is a nice ssh client available for windows, putty. You then tunnel your VNC connection over ssh.

It is easy to tunnel over ssh:

[http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

Without tunneling there is a not insignificant security risk. An alternate may be FreeNX

---

### Post by lovinglinux on 2008-11-16
> **bodhi.zazen said:**
> Without tunneling there is a not insignificant security risk.

Is there a risk if I use it only on my local network, if I do not open the port on the router and if have an iptables rule to allow input connections on the vnc port only from local Ip's?

---

### Post by bodhi.zazen on 2008-11-16
> **lovinglinux said:**
> Is there a risk if I use it only on my local network, if I do open the port on the router and if have an iptables rule to allow input connections on the vnc port only from local Ip's?

IMO, You are OK if you are behind a router. Adding a rule to IP tables is probably not necessary, but will not hurt either.

---

### Post by lovinglinux on 2008-11-16
> **bodhi.zazen said:**
> IMO, You are OK if you are behind a router. Adding a rule to IP tables is probably not necessary, but will not hurt either.

Thanks. I guess I'm a little bit paranoid.

---

### Post by Lutrova on 2008-11-16
I'm not concerned about security or anything, and furthermore cannot do any SSH tunneling from work. SSH, as I had mentioned before, is not an acceptable solution. I'm looking for a simple solution as well.

> **bodhi.zazen said:**
> The ability to do this will depend on your vnc server on the Ubuntu box.

The built in vnc server uses a shared desktop. Try vnc4server.

Also I strongly advise you tunnel your vnc session over ssh. There is a nice ssh client available for windows, putty. You then tunnel your VNC connection over ssh.

It is easy to tunnel over ssh:

[http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

Without tunneling there is a not insignificant security risk. An alternate may be FreeNX

---

### Post by bodhi.zazen on 2008-11-16
> **Lutrova said:**
> I'm not concerned about security or anything

You will be once you are cracked (happens frequently with VNC if you do not lock it down, was just a thread in the security section on this).

>  and furthermore cannot do any SSH tunneling from work. SSH, as I had mentioned before, is not an acceptable solution. I'm looking for a simple solution as well.

The "simple solution" is to install vnc4server on ubuntu.

---

### Post by barzam on 2008-11-16
I also think that SSH is the best way to do this (because it encrypts your login on the VNC-server), but if you can't, you can't. 

Did you try vnc4server, as was suggested?

---

### Post by sideshowmel on 2009-05-01
So your work allows outbound VNC connections but not SSH? I'm guessing you are trying to use outbound port 80 for VNC and have your VNC server and your router setup to listen on port 80.  Better option would be to do that same thing, only have ssh listen on port 80 instead.  Then you can tunnel anything through that... vnc, FTP, command-line interface.  Way better and more secure solution...

---

### Post by Brandon Williams on 2009-05-01
I also recommend that you tunnel through SSH. However, since you insist ...

These threads might be helpful:
[http://ubuntuforums.org/showthread.php?t=122402&highlight=vnc+inetd](http://ubuntuforums.org/showthread.php?t=122402&highlight=vnc+inetd)
[http://ubuntuforums.org/showthread.php?t=795036&highlight=vnc](http://ubuntuforums.org/showthread.php?t=795036&highlight=vnc)

They are quite similar. One includes a little bit about fitting SSH into the picture.

I haven't done this myself, but it looks like a bunch of other people have.

---

### Post by bodhi.zazen on 2009-05-01
Tunneling VNC over ssh is very very easy.

[http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

Just secure you ssh server.

You firewall your VNC port (5900)

From the command line you forward the ports over ssh

ssh -L 5900:localhost:5900 user@server

you then, on the client, connect vnc to localhost

---

### Post by Jim Brown UK on 2009-05-03
Hi Folks,
this is my first contribution to the Ubuntu forum and I've a question about VNC.  I've a desktop machine running Hardy Heron and just got a little Acer One notebook which runs Linpus.  I'm trying to use the notebook to access my desktop system but it uses the xfrce desktop which doesn't seem all that friendly to Ubuntu's gnome.

So, I got a usb drive and created a live install for Jaunty Jackelope which starts up all right and runs Terminal Server Client.  However, it only offers me RDP and RDPv5 protocols with VNC, XDMCP and ICA greyed out. I was planning to try to start vnc4server on my desktop but now I'm a bit stuck.

Any ideas anyone?

Cheers,

Jim

---

### Post by bodhi.zazen on 2009-05-03
There are several options for vnc, both server and client.

The default server is vino. 

vino and x11vncserver = shared sessions.

vnc4server = independent sessions.

the default vnc client is vinagre. Other clients include xvncviewer and tightvncviewer


Open synaptic and search "vnc" without quotes.

---

### Post by Jim Brown UK on 2009-05-04
Thanks.  I tried to start the server from the gnome "services" option in the menu but it wasn't there even though I had installed it.  I tried starting from the command line but I suspect it started some screen in the background because I couldn't see any new windows aferwards.  How to I get the server to run at boot?

Cheers,

Jim

---

### Post by bodhi.zazen on 2009-05-04
> **Jim Brown UK said:**
> Thanks.  I tried to start the server from the gnome "services" option in the menu but it wasn't there even though I had installed it.  I tried starting from the command line but I suspect it started some screen in the background because I couldn't see any new windows aferwards.  How to I get the server to run at boot?

Cheers,

Jim

I do not think vnc is installed as a service.

Configuration depends on the vnc server you are using.

See : [uhelp]VNC[/uhelp]

That link reviews the options and configuration and better configuration of your router (if needed) and security.

VNC is probably the most common service I see in these forums as an entry for crackers, so take care to secure this service and consider tunneling over ssh.

---

