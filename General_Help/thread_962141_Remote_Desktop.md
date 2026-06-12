---
title: "Remote Desktop"
date: 2008-10-29
forum: General Help
---

### Post by Bonajokin on 2008-10-29
Hey i was wondering is there anyway possible for me to use my main computer that runs windows xp and be bale to access this computer which runs ubuntu 8.04 via remote desktop and be able to have the same gui and everything like regular remote desktop within windows. Kinda like a PiP screen thing since i only use one monitor for both computers.

---

### Post by alienprdkt on 2008-10-29
nomachine
[http://www.nomachine.com](http://www.nomachine.com)

1) From a terminal window, browse to a directory where you want to download the necessary .deb files on your Linux machine.

2) Then, run the following commands one at a time to download the necessary packages (from the same terminal window of course):

    wget [http://64.34.161.181/download/3.1.0/Linux/nxclient_3.1.0-6_i386.deb](http://64.34.161.181/download/3.1.0/Linux/nxclient_3.1.0-6_i386.deb)
    wget [http://64.34.161.181/download/3.1.0/Linux/nxnode_3.1.0-6_i386.deb](http://64.34.161.181/download/3.1.0/Linux/nxnode_3.1.0-6_i386.deb)
    wget [http://64.34.161.181/download/3.1.0/Linux/FE/nxserver_3.1.0-5_i386.deb](http://64.34.161.181/download/3.1.0/Linux/FE/nxserver_3.1.0-5_i386.deb)


3) Next, we are going to run the the commands to actually install the packages we just downloaded:

    sudo dpkg -i nxclient_3.1.0-6_i386.deb
    sudo dpkg -i nxnode_3.1.0-6_i386.deb
    sudo dpkg -i nxserver_3.1.0-5_i386.deb

---

### Post by ryanhaigh on 2008-10-29
Or you use the vino VNC server that comes provided with your gnome desktop. Just go to system>prefs(or admin can't recall right now)>Remote Desktop, enable remote connections and set a password then install a vnc client on your windows machine, I prefer [http://www.tightvnc.com/](http://www.tightvnc.com/)

---

### Post by Bonajokin on 2008-10-29
I got a couple errors when i tried to installing the no machine which intern ending up corrupting my system i think. 

Ryan idk if theres an extra step to your process, but i couldn't get connected :S

---

### Post by alienprdkt on 2008-10-29
maybe old software versions .. check site ([http://www.nomachine.com](http://www.nomachine.com))
for the new version
so0rry

---

### Post by ad_267 on 2008-10-29
Why install that? Ubuntu comes with everything you need by default.

Just go to System - Preferences - Remote desktop to enable it and then you can view it from Windows or another Linux machine.

You can go to Applications - Internet - Remote Desktop Viewer to control desktops in Ubuntu.

It's very simple. There's a guide here: [http://www.howtogeek.com/howto/ubuntu/allow-remote-control-to-your-desktop-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/allow-remote-control-to-your-desktop-on-ubuntu/)

Also see this for controlling desktops from Ubuntu: [https://help.ubuntu.com/community/Vinagre](https://help.ubuntu.com/community/Vinagre)

---

### Post by alienprdkt on 2008-10-29
> **ad_267 said:**
> Why install that? Ubuntu comes with everything you need by default.

Just go to System - Preferences - Remote desktop to enable it and then you can view it from Windows or another Linux machine.

You can go to Applications - Internet - Remote Desktop Viewer to control desktops in Ubuntu.

It's very simple. There's a guide here: [http://www.howtogeek.com/howto/ubuntu/allow-remote-control-to-your-desktop-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/allow-remote-control-to-your-desktop-on-ubuntu/)

Also see this for controlling desktops from Ubuntu: [https://help.ubuntu.com/community/Vinagre](https://help.ubuntu.com/community/Vinagre)

Just wondering why with this app do I get serious lag, when I am on local lan, and I am connecting from a box running nothing but remote desktop viewer and on other machine (the one I am connected to)?
It cant be because of cpu or ram ... I am running a dual-core intel on one and dual-core amd 64 on the other both have 2GB 677mhz ram

---

### Post by alienprdkt on 2008-10-29
also can connect to ubuntu this that way from another ubuntu box, but not from my mac-mini (remote desktop connection) or my windows box. VNC on mac mini runs terribly slow also. this is why I chose to use NOMACHINE. the client can be installed on all operating systems, plus seems to work alot better, well for me anyways.

---

### Post by ryanhaigh on 2008-10-29
What software are you trying to use on the Windows machine? I have never really worried about speed because I only use it for short periods of time and it always seemed adequate (except when spinning the compiz cube). I don't know if the buit-in server uses compression and being a gnome-app if it's not there by default it's probably not there.

---

### Post by Bonajokin on 2008-10-29
> **alienprdkt said:**
> also can connect to ubuntu this that way from another ubuntu box, but not from my mac-mini (remote desktop connection) or my windows box. VNC on mac mini runs terribly slow also. this is why I chose to use NOMACHINE. the client can be installed on all operating systems, plus seems to work alot better, well for me anyways.


Well i got no machine installed on here and im guessing i need to install it on my windows pc too. After that what do i do to get these things connected where i can control this linux box from the windows one

---

### Post by alienprdkt on 2008-10-29
all you need is nomachine client for windows 
[http://www.nomachine.com/download-client-windows.php](http://www.nomachine.com/download-client-windows.php)

---

