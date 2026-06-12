---
title: "Can't run setup.exe off disc(modem driverinstall)"
date: 2005-01-06
forum: Installation &amp; Upgrades
---

### Post by J.K. on 2005-01-06
I got all excited when i saw that the disc that came with my modem(internal 56k) actually had Linux drivers on it. But that did not last for long because the setup program would not run. In the file folder there are 3 drivers and a setup.exe file.
Double clicking on this and selecting run does'nt seem to work.
Is there another way to install these drivers?

---

### Post by tiiim on 2005-01-06
[QUOTE=J.K.]I got all excited when i saw that the disc that came with my modem(internal 56k) actually had Linux drivers on it. But that did not last for long because the setup program would not run. In the file folder there are 3 drivers and a setup.exe file.
Double clicking on this and selecting run does'nt seem to work.
Is there another way to install these drivers?[/QUOTE]
 i dont think .exe files work on linux because thats a windows extension. see if you can see ur modem in a folder or something if its got linux drivers they will be on the cd somewhere but it wont be via the setup.exe if not email the manafacture.

---

### Post by wallijonn on 2005-01-06
setup.exe is for Windows.

You therefore are probably trying to install the Windows drivers in Linux.

It can't be done.

The only "setup.exe"s I know of that work are those by OpenOffice & Mozilla.

---

### Post by nbliang on 2005-01-06
[QUOTE=J.K.]I got all excited when i saw that the disc that came with my modem(internal 56k) actually had Linux drivers on it. But that did not last for long because the setup program would not run. In the file folder there are 3 drivers and a setup.exe file.
Double clicking on this and selecting run does'nt seem to work.
Is there another way to install these drivers?[/QUOTE]
Yeap, both ***tiiim*** and ***wallijonn*** are correct where not all "exe" files are executable under Linux. You try to look for the file with the extension "tar" or "bin" or "gz" or "rpm" or "deb" because those are the extension executable or compressed under Linux.

Wish you luck...

---

### Post by tAK on 2005-01-06
yeah. or you could check out driverguide.com for linux drivers, im not sure if they have them, but they should.... you could even download the linux drivers from the manufcaturers website.. if they are on the CD then they will be on the net...

the only way to run a ".exe" file under linux is to install wine... though this wont work for drivers (i dont think) and not for directx based games (cedega supports these) the easiest way to install wine (providing that ubuntu supports it, i havent had a chance to try yet) would be the following:

open a new console and type:

apt-get update
apt-get install wine

and it will install wine.... ill leave it upto you to learn more about it,,, i got this far before. but never got the chance to go futher... as far as using it goes (though fault of my own...)

/tAK

---

### Post by az on 2005-01-06
Forget about the exe file.

What kind of modem is it.  If it is a hardware moden, you do not need drivers.  Are you sure that there are no other files on the cd?  What are the files that are there called?

---

### Post by Sensebend on 2005-01-06
The most important part of getting modems to work would be to identify the chipset of it. If it is a hardware modem or external modem it should be well supported.

---

### Post by J.K. on 2005-01-07
Hi All
I have since found out that my modem,(internal 56k) in not supported. Its a winmoden *spit on the ground here* so im off to find an external modem.
I've also discovered that my printer is also not Linux freindly, so I won't be supporting that manufacturor
Many thanks for all the help.

---

