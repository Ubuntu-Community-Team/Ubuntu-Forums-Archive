---
title: "Boot with no monitor"
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by weirdbeardmt on 2009-05-10
Hi

Sorry n00b question I'm sure but all the stuff I've found refers to earlier versions and I'm not sure how to sort this.

Basically if I start my 9.10 box without a monitor, it gets stuck trying to detect displays and tries to run in low graphics mode. 

How do I tell it to not look for monitors and just boot? I had a snoop around in /etc/x11 and I've got an xorg.conf, xorg.conf.2009.. and an xorg.conf.failsafe

---

### Post by weirdbeardmt on 2009-05-11
bump

---

### Post by Peter09 on 2009-05-11
Does it complete the boot, if so then its ok. If you want to run without a monitor then you can remove gnome.

---

### Post by weirdbeardmt on 2009-05-11
> **Peter09 said:**
> Does it complete the boot, if so then its ok. If you want to run without a monitor then you can remove gnome.

It boots fine with a monitor attached, I just want it to boot in the exact same way without a monitor attached as I'll only ever control this machine via VNC, so I don't want to remove gnome.

---

### Post by Peter09 on 2009-05-11
Whats the problem when you boot without a monitor - have you auto login enabled?

---

### Post by Peter09 on 2009-05-11
Rather than VNC use nxfree -its in the repositories. It allows you to login without a session being active.

---

### Post by weirdbeardmt on 2009-05-11
> **Peter09 said:**
> Whats the problem when you boot without a monitor - have you auto login enabled?

It gets stuck on the boot sequence - because it tries to auto set the display settings but can't work it out without a monitor attached. So it waits on a prompt asking if it should run in low graphics mode or whatever.

---

### Post by Peter09 on 2009-05-11
Yeah - what you want is ok but not the way you are doing it. First stop autologin and then install openssh-server

```
sudo apt-get install openssh-server
```

having done that you will be able to remotely login by

```
ssh -X <username>@<machine name or IP> xterm
```

You can replace the xterm bit by any other command.

To get a desktop you will need to install nxserver, nxnode and nxclient on the headless machine and nxclient on you admin machine.

---

### Post by weirdbeardmt on 2009-05-12
Hi Peter - many thanks, and you're absolutely right that this machine really shouldn't have / doesn't need a gui installed. In fact, I think on this particular machine (which I'm really just using as a webcam/webserver so I can keep an eye on what my animals are doing while I'm at work!) I'm going to start again with the server addition, and just install what I need.

I'm new to linux and still getting to grips with all the fun stuff you can do! 

Question: in your last post you say how to setup ssh on it - presumably I issue that ssh command (i.e., to get an xterm on the ubuntu machine) from the commandline on my Macbook Pro?

---

### Post by Peter09 on 2009-05-12
Assuming that your MacBook supports ssh then yes.

---

### Post by orange-wedge on 2009-05-12
> **weirdbeardmt said:**
> 
Question: in your last post you say how to setup ssh on it - presumably I issue that ssh command (i.e., to get an xterm on the ubuntu machine) from the commandline on my Macbook Pro?

With that ssh command you will be exporting the X11 display to your Macbook, so in order to do that you will need to fire up your X11 server and then open up the xhost on your Ubuntu server.  I would take a look at this article from apple:
[http://developer.apple.com/opensource/tools/runningX11.html](http://developer.apple.com/opensource/tools/runningX11.html)

---

### Post by weirdbeardmt on 2010-02-03
In case anyone finds this and does want to do what I was originally trying to do (i.e., remote desk a client machine), then this worked for me: [http://imthi.com/blog/linux/ubuntu-904-remote-desktop-using-vncserver-without-monitor.php](http://imthi.com/blog/linux/ubuntu-904-remote-desktop-using-vncserver-without-monitor.php)

providing you have SSH access to start vncserver

---

