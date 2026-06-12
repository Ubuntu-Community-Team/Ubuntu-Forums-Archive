---
title: "how to remote control into another ubuntu computer over internet?"
date: 2008-09-21
forum: General Help
---

### Post by da.tiger on 2008-09-21
Can anyone please tell me as to how I remote into another ubuntu computer?

---

### Post by Predator106 on 2008-09-21
I use VNC. To enable it in Ubuntu, go to System->Settings->Remote Desktop, and check enable, etc. Make sure you have a password and that you have ask for confirmation off (what's the point of allowing remote access if you have to be at the workstation to allow it, heh.)

To control it from another Ubuntu computer, I use krdp (I think that's the package name), it's the best one, has only a few features but it's all you need really. Works fine for me. If you are using windoze to control it, use TightVNC, or RealVNC, doesn't really matter I guess.

If they are on the same network, you will have to know the internal IP of the server, and I recommend setting it to static through your router, otherwise every time your router assigns (assuming it's a DHCP server) new IP's, you will have to check to see what the IP is again.

If you are controlling it from the "outside" i.e. another outside network, through the internet, google for your WAN IP and connect to that. Also, you may have to unblock port 5900 on your router i.e. forward that port.

---

### Post by da.tiger on 2008-09-21
thanks , I ll try that and post if it works

---

