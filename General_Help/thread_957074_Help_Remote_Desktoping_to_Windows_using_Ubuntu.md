---
title: "Help: Remote Desktoping to Windows using Ubuntu"
date: 2008-10-23
forum: General Help
---

### Post by raiderleaf on 2008-10-23
Hi, i'm trying to use the Remote Desktop login that i normally use in Windows to use in Ubuntu.  I wanted to know if it is possible and if so, what do I need to do so it is like I am using my system that is at the office while I am here at home?

Thank you,

raiderleaf

---

### Post by kmclar on 2008-10-23
raiderleaf,

To do what you are asking, you need a couple of things:  first, to make a vpn connection to a vpn server on your office network, then use a remote desktop client package to actually connect to and run your office computer.

In Windows, you create a vpn connection using the create new connection process, then you use Remote Desktop Connection to connecto to your computer.

In Linux, there are several vpn clients available, and several remote desktop client packages.  You can see these in Synaptic package manager.  

Which vpn client you use depends on the vpn protocol of the vpn server at work.  In my case, I use NetworkManager-pptp, as I am connecting to a pptp vpn server.  Then, I use tsclient as the remote desktop client, but grdesktop is good as well.

Look around on the forum, there is lots of good instruction on how to use these.  If you already are doing this in Windows then you already have the info you need to configure these programs to do it in Linux.

---

