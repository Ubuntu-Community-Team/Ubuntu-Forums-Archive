---
title: "Assigning IP"
date: 2014-09-24
forum: Hardware
---

### Post by dennis32 on 2014-09-24
I have an old Sun server running Ubuntu. Attached to it is a USB hard drive. I need to assign an IP address to the attached hard drive. Please detail commands needed from terminal within Ubuntu. Thanks!

---

### Post by lisati on 2014-09-24
There are multiple methods, each with its own merits. My preference is to reserve an IP address using my router's control panel. This way, if I take my device elsewhere and temporarily use someone else's network, I am less likely to run into conflicts with IP allocation when someone else decides that they want the exact same IP address for their device.

edit: oh! A hard drive connected to a server that you wish to make available on your network? Apparently I misunderstood.  Again, multiple options are open to you. Have you looked into using tools such as Samba to make the data available?

---

### Post by dennis32 on 2014-09-24
Samba? No, I have not. I prefer the simplest approach. And, yes... it is a hard drive connected to the server (on the network). Note: when I initiate the server, an IP is established through the router and recognized. There's a grub setup within the server launch, where by I can by pass the server w/ Ubuntu and go directly to the attached HD. When the HD is accessed via the network, no IP is recognized. I believe I need to have an IP address on the HD, so when I hit up the address, I can see, access what's on the HD. Thanks for the feedback...

I've been able to find my way to the HD to see that the content I'm looking for is present, which it is.

---

### Post by weatherman2 on 2014-09-24
You cannot assign an IP address to a USB hard drive.

You need to share the files on your USB drive (for example with Samba - or NFS, ssh, etc.), and the IP address is assigned to the server to which the USB drive is connected.

Does your USB drive have an operating system on it?  Maybe that's how you are booting from it.  But the IP address is still not being assigned to the "hard drive," it's being assigned to the network device in the server.

---

### Post by dennis32 on 2014-09-25
When I boot the server it starts to launch to the installed Ubuntu. There's a grub setup that delays the process and permits me to direct to the attached HD, if I desire, otherwise the launch proceeds At that point, the server is running, but I've elected to access the HD - at the login for the HD w/ content. If I try to SSH the server when it directly launches, I see an IP. When I use Ubuntu terminal I see an IP. When it's accessing or has accessed the HD, and I attempt to SSH through the network, I can't find (recognize) the server's network IP.

---

### Post by steeldriver on 2014-09-25
It's kind of hard to follow what you are saying here - so you have a bootable Ubuntu system on the USB HDD? and when you boot to that system instead of the one on the internal HDD, you can't figure out the resulting network configuration of your host?

---

### Post by dennis32 on 2014-09-25
Bootable Ubuntu is only present, installed on the sun server. When one moves through the server start up configuration, then grub election to go to the attached HD, instead of going to the server, one finds content of the attached drive that is powered by Redhat, a disk image content, but no recognizable IP from within the network.

Sorry for the confusion.

---

