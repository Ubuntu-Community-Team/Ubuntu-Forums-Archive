---
title: "Install TightVNC from terminal window"
date: 2009-04-17
forum: Installation &amp; Upgrades
---

### Post by runnner on 2009-04-17
Who could tell me how to install TightVNC from root terminal window.?

CAN this line work?
apt-get install TightVNC

---

### Post by Tim Sharitt on 2009-04-17
To install TightVNC server you'll

```
sudo apt-get install tightvncserver
```

---

### Post by runnner on 2009-04-20
I use putty to connect to the remote ubuntu server and ran "sudo apt-get install tightvncserver".
Then I start the tightvnc viewer on my windows pc, input the ubuntu IP address and click connect button, but a few seconds late, I get error message:faied to connect to the server ip address.

Where is wrong? Thanks!

---

### Post by runnner on 2009-04-20
WHO could tell me how to work around the problem, thanks!

---

### Post by SR_ELPIRATA on 2009-04-20
Why do u need to install TightVNC? I think Ubuntu has that feature already installed. Not sure if in the server works as it does with the desktop version, but Id have to guess that it should.

I use TightVNC to support my clients and to use my HTPC system on my own network, but its because they use windows. Gonna try and install a VM with the ubuntu server and see if I can help.

---

### Post by runnner on 2009-04-21
> **SR_ELPIRATA said:**
> Why do u need to install TightVNC? 

On my Windows PC, I need istall TightVNC viewer. but the viewer failed connect to remote ubuntu.

---

### Post by lavallie on 2009-04-24
I have TightVNC on my windows machine and can log into Ubuntu no problem.  Be sure to enable this feature on Ubuntu before trying to connect.

Are you connecting locally on your LAN or via a remote connection across the Internet?

If across the INTERNET you may have issues with firewalls and routers at the other end.  

If you can, try it locally first then if it works ok make the big jumb.

---

### Post by runnner on 2009-04-26
> **lavallie said:**
>  Be sure to enable this feature on Ubuntu before trying to connect.


I am not sure if this feature has been turned on on the remote ubuntu server.

> **lavallie said:**
> 
Are you connecting locally on your LAN or via a remote connection across the Internet?

If across the INTERNET you may have issues with firewalls and routers at the other end.  

I connect to the remote ubuntu server via the Internet from my windows PC, and there is firewall software on the Windows and a router connected to the Windows PC, i.e, there is a router  between the Windows PC and Internet.

I don't know which one may cause the TightVNC connection failure.

---

### Post by lavallie on 2009-04-26
I suspect the issue for you revolves around port forwarding.  

If you are not familiar with this requirement, first take a look here:
[http://www.tightvnc.com/faq.html](http://www.tightvnc.com/faq.html)

From here it becomes technical.  Your computer is behind the router, and the router has a public address like 206.229.88.208.  This address is the intenet address for any number of PC's.  So from here you need to set up a way to "hit" a specific pc behind that router.  You do this with port forwarding.

I do not know how much knowledge you have in this area, so I will wait to hear from you.  You can also Google: how too set up port forwarding, there is a lot of information out there.  It is the same for Windows PC's and Ubuntu PC's.

---

### Post by runnner on 2009-04-26
Thank you all for your replies!

---

### Post by SR_ELPIRATA on 2009-04-29
Ubuntu has the remote desktop feature installed, at least the desktop does. To get someone to help you (on in this case for you to connect to your remote pc) you first need to go to System/Preferences/Remote desktop and check those switches that apply to you.

Now, I'm not sure how would be available to the server if for example your using just the console, but if you installed the graphic interface then you should be able to see it in preferences.

If between the Ubuntu server and the internet theres a router you will need to do as lavallie said, setup port forwarding (I think ports will be 5800 and 5900). Another thing you can do is (from the windows PC) ping the ip address your trying to connect, or tracert it. I normally use dynamic dns services, and if you do too, instead of the ip addy just put the assigned address (like ping whatever.dyndns.org).

ELP

---

### Post by lavallie on 2009-04-29
SR_ELPIRATA,

You bring up a good point.  Can you tell me where the port numbers are defined??  In windows it is in ghe regestry but I do not know where in UB...

Regards

---

### Post by SR_ELPIRATA on 2009-04-29
To be honest thats one part I dont know. So far I've connected to my windows clients and my home theather computer but never tried backwards. I would think that by enabling the remote desktop feature it would allow you not only to connect from windows and other ubuntu/linux computers but also make the apropiate changes to the firewall.

With this said, as I'm sort of a advanced noob (lol), I thought we didnt had a firewall in ubuntu :) I can try and put the other machine I have and see if I can connect to her. Will report back.

ELP

---

### Post by mozkill on 2009-04-29
i concerned about the original posters need to connect as the "root" user with the VNC client.  not sure that is possible without hacking the linux system to allow a root remote console...

a picture of what you need:

unix box 192.subnet  <-- port 5900 <-- dlink hub allow 5900 from all hosts and forward to linux box internal 192.x ip  <-- internet wan <--  windows box vnc client

---

### Post by SR_ELPIRATA on 2009-04-29
Enabled remote desktop feature, set to allow remote to control computer, set to not ask for permision but I did set a password if the remote wants to control the computer (you can also do view only).

There was no window or dialog box informing me of the change or if I wanted to do changes to the firewall and all that.

Finding the computer from the LAN is very easy, just use the remote desktop viewer and use the FIND button, it will find it.

Of course, both my ubuntu systems are set to auto eth0, if memory serves me well, this is using the DHCP feature of my router. If you want to connnect to your computer outside the router you will need to setup a static ip address instead. Most of them routers will ask you for the computer's IP to setup the port forwarding, so this is a necesity.

ELP

---

### Post by SR_ELPIRATA on 2009-04-29
Moz, for outside connections to go to the right computer (even if its the only one) you need taht computer to have a fixed ip address, then you will be able to forward traffic to the computer.

Also, if the remote desktop feature is available on the server, its as easy as to tell the system that you allow 'outsiders' to use the system, no need to 'hack' linux, is doable. Of course, this asumes that the remote feature is installed in the server, which I dont know.

ELP

---

### Post by Zoandar on 2009-10-14
Hi,

I wonder if you could tell me if there is a way to have the TightVNC viewer in Ubuntu resize the desktop on the server in Windows XP Home? 

I have access set up between an Ubuntu notebook and my PC, but the PC has large multiple displays. The notebook has only a 12" display, so it is like reading a billboard through a magnifying glass. If I use Windows on both ends, I use LogMeIn free version and it can zoom in or out on the server desktop, so I can make it fit the notebook screen. I'd like to find a way to do that with TightVNC, if it is possible. 

Zoandar

---

