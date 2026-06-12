---
title: "new to linux and want to do remote admin"
date: 2008-09-03
forum: General Help
---

### Post by keq on 2008-09-03
i am new to the world of linux and i am slowly working my way into it. but for now i have my desk top running the latest ubuntu and i have my laptop running windows xp, i would like to be able to remote connect to my linux box from my windows laptop to be able to work on it here and there when i have free time and i am not directly sitting in front of it.

is there a way that i can connect cross platform like that?

---

### Post by Bluebell392 on 2008-09-03
Yes, there is. If your laptop is running XP Professional, then use the Terminal Server Client. It's found under the Internet menu. type in the ip address or hostname in the computer field and make sure RDp is selected in the protocol menu, then click connect.

---

### Post by keq on 2008-09-03
and what do i have to do for the linux box to make it able to accept connections?

---

### Post by joenix on 2008-09-03
To make a linux box accept RDP connections, you have to install an RDP server. As far as I know, only xrdp can currently do that. You can check out the xrdp package.

However, xrdp does not seem very stable or as easy to use as Ubuntu's built-in VNC server. I would advice you to just install one of the many VNC clients on the Windows box and enable VNC connections on the Linux box in System -> Preferences -> Remote Desktop.

---

### Post by keq on 2008-09-03
> **joenix said:**
> To make a linux box accept RDP connections, you have to install an RDP server. As far as I know, only xrdp can currently do that. You can check out the xrdp package.

However, xrdp does not seem very stable or as easy to use as Ubuntu's built-in VNC server. I would advice you to just install one of the many VNC clients on the Windows box and enable VNC connections on the Linux box in System -> Preferences -> Remote Desktop.


can you give me a link to a decently easy one to install and learn to use? i did a search and i am not really sure which one to use.

thank you

---

### Post by WRDN on 2008-09-03
> **joenix said:**
> To make a linux box accept RDP connections, you have to install an RDP server. As far as I know, only xrdp can currently do that. You can check out the xrdp package.

However, xrdp does not seem very stable or as easy to use as Ubuntu's built-in VNC server. I would advice you to just install one of the many VNC clients on the Windows box and enable VNC connections on the Linux box in System -> Preferences -> Remote Desktop.

On Ubuntu 8.04 you can no longer select System > Preferences > Remote Desktop.
Depending upon where you are connecting from (i.e. local network or internet), you should add a few layers of security before using VNC. The passwords are sent in plain text, so can easily be sniffed. Thus, you should not use VNC without other measures first, and should NOT start VNC without settings a password.

I personally use "x11vnc" and this suits my need. Install this with the command:

```
sudo apt-get install x11vnc
```

You will also need a VNC Viewer installed on the HOST machine. I use xvnc4viewer. This can be installed using the command:

```
sudo apt-get install xvnc4viewer
```

The X11VNC software acts as the VNC Server. You can start the server straight away by typing "x11vnc" in the Terminal, but I would not advise this.

Instead, set a password first:

```
x11vnc -storepasswd
```

You will not be prompted for the password (twice).

You can now start VNC using the command:

```
x11vnc -forever -usepw
```

The "-forever" directive ensures the VNC server does not shut-down when a client disconnects. The "-usepw" directive ensures you have to use a password to connect.

Now, start SSH (if its not started already), which is already installed:

```
sudo /etc/init.d/ssh start
```

Connect to the SSH server using the software you desire (e.g. Putty can be used). You need to connect to the SSH Server, and forward X11, and port 5900 (and 5901 if you wish). As an example, I will explain using Putty:

- In the host name, enter your IP address (this can be found using the command "ifconfig").
- Click "X11" in the Category menu on the left- this resides under "SSH"
- Select "Enable X11 Forwarding"
- Click Tunnels in the Category menu (also under SSH)
- Add the source port "5901", and for the Destination, put "localhost:5900"
- Finally, click Open to connect to the SSH server

If you are using a Linux machine, you can connect from the Terminal by typing:

```
ssh -X [username]@[IP_Address]
```

The "-X" directive ensures X11 is forwarded. For this to work, you must set "X11Forwarding" to yes in the '/etc/ssh/sshd_config' file. You can edit this using the command:

```
gksudo gedit /etc/ssh/sshd_config
```

Now you are connected to SSH, type:

```
vncviewer
```

This will open the xvnc4viewer you installed earlier. Now, for the VNC Server, enter "localhost" and you should connect to the VNC Server you started before. All data is not encrypted by SSH. Note that, when you start the X11 server, the output will contain "Desktop: N" (where N represents the Desktop number). When connecting to the VNC Server, you can use "localhost" if you did **not** start another instance of the VNC Server (it starts automatically). If you started another instance, then use the desktop number when connecting- "localhost" in the VNC Viewer would become "localhost:N" (N represents desktop number).

---

### Post by keq on 2008-09-03
WOW thank you very much, im going to get to work on this THANK YOU

---

### Post by joenix on 2008-09-03
> **WRDN said:**
> On Ubuntu 8.04 you can no longer select System > Preferences > Remote Desktop.


What do you mean by this? I just booted the Hardy live cd to check it and it is still there. I also have it on my Hardy install and I can't remember ever having to install it.

Anyway, nice job on the tutorial. Some things to note:
- With recent VNC servers, such as vino and x11vnc, passwords are no longer sent in cleartext. The data is sent unencrypted though in vino. The package description of x11vnc even states that it supports SSL encryption. If the traffic does not go over the internet (local network), this seems like a secure enough solution to me. You'll have to judge for yourself what level of security/ease of use you're looking for.
- The client will be running on the linux box as well as the server. Since the entire VNC client window has to be transferred to the connecting co,puter through X11, the bandwidth efficiency of VNC will be negated. A better method would be to tunnel the VNC port through SSH.
- If you're going to connect from the internet, install a firewall and block everything except SSH. Then use tunneling to connect to the VNC server.

---

### Post by keq on 2008-09-03
> **joenix said:**
> What do you mean by this? I just booted the Hardy live cd to check it and it is still there. I also have it on my Hardy install and I can't remember ever having to install it.

Anyway, nice job on the tutorial. Some things to note:
- With recent VNC servers, such as vino and x11vnc, passwords are no longer sent in cleartext. The data is sent unencrypted though in vino. The package description of x11vnc even states that it supports SSL encryption. If the traffic does not go over the internet (local network), this seems like a secure enough solution to me. You'll have to judge for yourself what level of security/ease of use you're looking for.
- The client will be running on the linux box as well as the server. Since the entire VNC client window has to be transferred to the connecting co,puter through X11, the bandwidth efficiency of VNC will be negated. A better method would be to tunnel the VNC port through SSH.
- If you're going to connect from the internet, install a firewall and block everything except SSH. Then use tunneling to connect to the VNC server.

well ill be doing both, the linux box is sitting in a spare room roughly the size of a walk in closet and is the main place for my networking things, so i would like to be able to work on the linux machine without dropping 35 pounds sweating. thus using my laptop to connect. but i would also like to be able to have access to the machine when i am at work or another persons house for various reasons

---

### Post by joenix on 2008-09-03
You can configure your firewall to allow both. If your VNC server is also your gateway to the internet, you can set different firewall rules, depending on where the connection comes from (internet/local).

If your VNC server is sitting behind your firewall, you can allow connections to both the ssh and vnc ports and then have your firewall do port forwarding to only expose the ssh port to the internet.

Check out the new Ubuntu firewall, it's pretty neat in my opinion:
[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

---

### Post by WRDN on 2008-09-03
> **joenix said:**
> **What do you mean by this? I just booted the Hardy live cd to check it and it is still there. I also have it on my Hardy install and I can't remember ever having to install it.**

Anyway, nice job on the tutorial. Some things to note:
- With recent VNC servers, such as vino and x11vnc, passwords are no longer sent in cleartext. The data is sent unencrypted though in vino. The package description of x11vnc even states that it supports SSL encryption. If the traffic does not go over the internet (local network), this seems like a secure enough solution to me. You'll have to judge for yourself what level of security/ease of use you're looking for.
- The client will be running on the linux box as well as the server. Since the entire VNC client window has to be transferred to the connecting co,puter through X11, the bandwidth efficiency of VNC will be negated. A better method would be to tunnel the VNC port through SSH.
- If you're going to connect from the internet, install a firewall and block everything except SSH. Then use tunneling to connect to the VNC server.

On my system, the option isn't available under System > Preferences, but "Remote Desktop Viewer" and "Terminal Server Client" exist under Applications > Internet.
I'm guessing the changes occured between 8.04 and 8.04.1.

---

### Post by rmls on 2008-09-20
Thank you WRDN that is a brilliant quick how-to the only thing I had to add was that ssh was not installed on my clean 8.04 install but a quick:

sudo apt-get install ssh 

sorted that out.

Many thanks
rmls

---

