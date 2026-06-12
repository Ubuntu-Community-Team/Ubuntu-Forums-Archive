---
title: "Issues in apt and synaptic connecting to repository on a fresh system"
date: 2009-04-20
forum: Installation &amp; Upgrades
---

### Post by su_list on 2009-04-20
Hi:

I have installed intrepid in my office system. This system is connected to internet and I can browse the net from firefox. But when I am trying to install/update some package through synaptic or apt-get, its failing to connect to the repository. When I try apt-get from the commandline, it says, "couldnt find package". Can you please help me in identifying and resolving the issue. :(

Thanks
Su

---

### Post by kiridude on 2009-04-20
what package are you trying to install?

---

### Post by su_list on 2009-04-20
I am trying to install the telnetd and other inet packages.

---

### Post by kiridude on 2009-04-21
You need to enable the Universe repositories:

```
gksudo gedit /etc/apt/sources.list
```

Then uncomment (delete the # sign at the beginning of the following lines):

deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) intrepid-updates universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe

close the window and chose "save" at the prompt.

You may want to enable Multiverse and other restricted repositories for other programs you may need. A little research will tell you what is where.

---

