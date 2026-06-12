---
title: "Connect Laptop to my Linux PC at home"
date: 2009-02-05
forum: Hardware
---

### Post by Ice799 on 2009-02-05
Basically what i want to do is to connect my linux laptop with my home computer... I want to be able to access files, media, games, ect... Does any1 know how to do this or and guides that i havent seen around somewhere...

Also if i do/can connect to my Home computer will i be able to run programs right from there? Games, Wine programs, ect... without actually having to move it to my laptop?

---

### Post by sedawk on 2009-02-05
For physical connection from laptop to desktop you might need a cross-over
cable (or configure wireless network for a host-to-host configuration).

Then you have to configure two IPs in the same network, e.g.
10.0.0.100 and 10.0.0.101 or 192.168.1.100 and 192.168.1.101 with
netmask 255.255.255.0.

When the same user (with same numeric ID) exists on both computers
you can login with "ssh -X user@desktop".
This way you can also execute desktop applications on the remote
computer but the display is on the local computer.
Most likely 3D-games will not support this (they need local
3D-hardware hardware).

---

### Post by hotstovejer on 2009-02-05
That's a lot that you want to do! Where do you want to be able to do this from? School, coffee shop, work? 

For being able to remote into my machine at home, I use VNC. It's not super speedy (internet connection will have a lot to do with how fast your experience is), but I can remote in, and use my pc while at work or away. 

As for access to files, you could use FTP to pull the files from your home computer to your laptop.

Tell us a little more as to what it is you want to do!

Thanks!

Jeremy

---

### Post by Ice799 on 2009-02-06
Basically what i want to do is leave my home pc to just download torrents and ect... well i use my laptop to listen to music get files from from my pc at home. 

So if i have internet connection anywhere in the world i can access my home pc... to retive any files have complete access to that hard drive.. so i can send files to and from and listen to music right from.. and i guess for games i could transfer them over but seems to be no way to execute a game right from my PC... 

I got a bunch of Hard drives to format once i get my laptop.. maybe i should turn it into a personal server instead...any one know anything about the linux based servers?

---

