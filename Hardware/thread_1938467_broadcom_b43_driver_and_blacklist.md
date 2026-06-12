---
title: "broadcom b43 driver and blacklist"
date: 2012-03-09
forum: Hardware
---

### Post by realpsygnosis on 2012-03-09
hi to all, I'm new linux user...
and I'm tring to solve all the problem that I have with my dell studio 1537.

First of all I have ubuntu oneiric, and I've installed the last stable Kernel 3.2.9
With this kernel the wireless stop working so I've installed the b43 driver that I found [HERE]("http//linuxwireless.org/en/users/Drivers/b43#Other_distributions_not_mentioned_above")
I've installed this via apt-get over the ubuntu repository, and everything goes fine...

But everytime I shoutdown the laptop the wireless stop working and I have to give the command:

[CODE]sudo modprobe b43[CODE]

to make the wifi work...

It's really annoying and I'd like that the b43 driver start working on startup...
I think that the broadcom wl driver is loaded by defaul..

How I can blacklist the broadcom wl driver to make the b43 load by default?

thanks to all in advace

---

### Post by ts3 on 2012-03-09
> **realpsygnosis said:**
> It's really annoying and I'd like that the b43 driver start working on startup...
I think that the broadcom wl driver is loaded by defaul..

How I can blacklist the broadcom wl driver to make the b43 load by default? 

Type in terminal 

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

This opens the blacklist.conf file with root privileges (if the "gksudo gedit" command gives you error messages in the terminal about path errors and similar but still opens gedit you can most likely ignore the error messages (or google them for peace of mind)).

Then add the line

```
blacklist wl
```

somewhere in the file.  I think there is a line that blacklists a b43xx driver or something similar so that's probably a good place.

Save and close gedit.  

If the wl driver was your problem this should solve it.

Cheers :)

P.S. You can also use nano to edit blacklist.conf in the terminal but I find the "gksudo gedit" approach less intimidating for a start.

---

### Post by bkratz on 2012-03-09
If it still does not load b43 on boot this is the way we get it to load rather than the 
"sudo modprobe b43"


sudo su 
echo b43 >> /etc/modules 
exit

This adds it to the modules loaded at boot time.

---

