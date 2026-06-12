---
title: "printing on windows machine on the network"
date: 2005-04-15
forum: Hardware &amp; Laptops
---

### Post by soljp on 2005-04-15
I am very new to linux and getting to like ubuntu 5.04. all the apps seem to work fine but I have been spending a lot of time trying to get the printer installed on my ubuntu 5.04. The printer is installed on an other machine on the windows network. I am not able to "browse" and select it. when I use the gnome-cups-manager and select smb network printer and give the name of the windows m/c as \\name_of_windows_machine and then on the next line the name of the share. its seems to install, but nothing happens. It just doesnt print. I have tried the same by trying to login as root. yet nothing. what can I do??? has any one got the same situation?? Any advice on this please. 

thnx


Soljp

---

### Post by soljp on 2005-04-15
I figured what I was doing wrong.

In the system>administration>printing

I wrote the name of machine, if through DHCP (or static ip of the m/c) where windowss xp has the printer installed

then the name of the printer

and then

THE USER NAME AND PASSWORD OF MY UBUNTU MACHINE.

It works!!!!



(this is where I was screwing things up)

---

