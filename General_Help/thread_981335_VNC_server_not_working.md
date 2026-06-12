---
title: "VNC server not working"
date: 2008-11-13
forum: General Help
---

### Post by .zolder on 2008-11-13
Hi,

I wanted to setup a VNC server so I could check on this box when I'm out. I followed [this tutorial](http://www.ubuntugeek.com/how-to-use-remote-desktop-in-ubuntu-810-intrepid-ibex.html) on how to address this. It's a real simple and straightforward tutorial so nothing can go wrong, right? :)

So, I set up the host in accordance to the first three images in the tutorial. Then I proceeded.
When I try to view my remote desktop using the Remote Desktop Viewer, I instantly get an error message stating that the connection to the host has been terminated. Also, when i click on the "Find" button, no host is found.

I tried all this on the same box, just like in the tutorial. In this stage, there is no network involved, hence me starting this thread in the general forums. I seems that the host just isn't running, despite the fact that it should.

Can anyone help me in the right direction troubleshooting?

---

### Post by firemann816 on 2008-11-14
I had the same issue and when i told it not to require a password, i got write in.
:confused:

---

### Post by alecz20 on 2008-11-15
Not entirely sure about Intrepid, but in Hardy, and earlier, there is a bug when you use the password, it is not parsed correctly or something.

You may omit using a password or you may do the following to enter the password correctly:

1) open gconf-editor ```
 gconf-editor
```
2) edit desktop > remote_access > vnc_password
3) Go to [http://www.javazoom.net/services/base64/base64.jsp](http://www.javazoom.net/services/base64/base64.jsp) and have your password encoded to base64
4) Enter the encoded password
5) Quit, Logout and login

Reference: [https://bugs.launchpad.net/ubuntu/+source/vino/+bug/141032](https://bugs.launchpad.net/ubuntu/+source/vino/+bug/141032)

Let me know if this solves your problem, it would be helpful in fixing the bug.

---

### Post by .zolder on 2008-11-16
Thank you for replying. I wanted to edit the pass in the gconf-editor, but it already was the same as the output of the converter on that site. Next, I disabled the need for a pass when connecting, but the problem still persists.
Other ideas?!

---

### Post by alecz20 on 2008-11-16
just to clarify a few things:

are using another computer on the LAN to connect remotely, or a computer from outside the LAN, or the same computer you want to connect to?

secondly, do you have any firewall on the ubuntu machine, or a router (if accessing from outside LAN)?

---

### Post by .zolder on 2008-11-17
I am trying to connect from the same PC. From the same login even. Nevertheless, I did forward the proper port, because connecting from outside was the whole idea. Besides the default Tomato (router-firmware) settings, I don't have a firewall.
I tried connecting to these adresses:
username-desktop:5900
127.0.0.1:5900
192.168.1.100:5900
WAN-IP:5900

---

### Post by .zolder on 2008-11-23
[img]http://www.ricesigns.com/real_pictures/bump_signs.jpg[/img]
can anyone help me out a bit?

---

### Post by alecz20 on 2008-11-23
I just tried the same thing, i.e. connecting from the same PC, but I entered the IP address of the PC.

Don't use the port anywhere.

In my case I just entered 192.168.0.107, in the remote desktop viewer application.

---

### Post by .zolder on 2008-11-26
I don't know whether that should make a difference. It doesn't in my case.

---

### Post by bravebear on 2008-12-29
Had something very similar happening. VNC used to work, then suddenly no connection possible whatsoever, no matter what I tried. It usually said "connection closed" or something like that. Then I remembered that I had installed Firestarter firewall at some point. I had it configured to work with vnc, or so I thought. I removed Firestarter completely and now vnc works again. As simple as that. Who knew? I have no explanation for this, but am also fairly new to ubuntu.

---

