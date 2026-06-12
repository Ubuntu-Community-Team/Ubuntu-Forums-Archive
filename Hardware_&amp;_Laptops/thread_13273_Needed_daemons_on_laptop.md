---
title: "Needed daemons on laptop"
date: 2005-01-30
forum: Hardware &amp; Laptops
---

### Post by tronda on 2005-01-30
I've gotten my laptop up and running on a fairly good level now. Read more details here:

[http://reassess.blogspot.com/2005/01/dell-laptitude-d800-and-ubuntu-linux.html](http://reassess.blogspot.com/2005/01/dell-laptitude-d800-and-ubuntu-linux.html)

During boot I see that several daemons/services start up. Do I need for instance RAID Devices and Enterprise Volume Management to start during boot? Are there any other daemons I typically can disable during boot on a laptop?

Last question. Are there any good GNOME apps for configuring daemons? Will GNOME System Tool app for service/daemon configuration be released with Hoary?

Thanks

---- Trond

---

### Post by mendicant on 2005-01-30
You almost certainly don't need RAID.  You probably don't need the volume management unless you actually know you set it up (and then, you'll definitely need it).  As for other services, it depends what you have.  You don't need a lot if you want a minimal install.  Postfix, you'll probably want to keep at least.  Maybe cupsys, udev and hotplug.  Everything else depends on what you want to use.  One thing to note--for some things (like the volume management and RAID, if you have it, you may break your system if you don't have them running.  You can also go through the list of services being run and see which ones you want.  Also check /etc/init.d for things that run on startup.

---

### Post by tronda on 2005-01-31
I'm a bit confused. I went into the rc3.d rc4.d rc5.d and rc1.d and links for starting daemons were everywhere. 

Say if I want to disable PCMCIA, do I have to remove S20pcmcia from all rcX.d directories where they are present?

So far I've disabled the following daemons (by prefixing the link with disable_):

- apmd (my laptop only supports acpi)
- pcmcia
- fetchmail (doesn't use it)
- mysql (want to start it manually when I need it)
- bluez-utils (haven't started using bluetooth yet)

Considering also disabling cron and at daemons, but they stay for now. 

What are the startup scripts for RAID Devices and Enterprise Volume Management  ?

----- Trond

---

### Post by dave9191 on 2005-01-31
I am a newbie too :) But I read in a guide that if you go to your /etc/init.d folder and type 

sudo chmod -x service_name 

it will disable the service from loading. Thats how ive been stopping them. I havent had the haert to delete them in case i need them :)

To have it starting again use sudo chmod +x service_name.

---

### Post by tronda on 2005-01-31
[QUOTE=dave9191]I read in a guide that if you go to your /etc/init.d folder and type 

sudo chmod -x service_name 

it will disable the service from loading. Thats how ive been stopping them. I havent had the haert to delete them in case i need them :)

To have it starting again use sudo chmod +x service_name.[/QUOTE]
Is this an optimal solution? For instance mysql. I don't want to start mysql on boot, but I would like to do the following when I need to start mysql:

sudo /etc/init.d/mysql start

By removing execute rights on the mysql file I must first make it executable and then remeber to remove executable rights before I close down my laptop.

I wounder what RedHat/Fedora's service configuration tool does.....

----- Trond

---

### Post by mendicant on 2005-01-31
You shouldn't mess with the links in /etc/rc*d.  You should use update-rc.d to disable services from starting up.  This will just remove the links in /etc/rc*d.  Somebody else on these forums recommended using rcconf at one point--never used it, and it seems not to be in main or restricted, so use at your own discretion.
For update-rc.d:
% update-rc.d -f <name> remove
This will remove the links in /etc/rc*d without removing the original file in /etc/init.d/, which allows you to run /etc/init.d/<name> start

---

### Post by mendicant on 2005-01-31
[QUOTE=tronda]
Considering also disabling cron and at daemons, but they stay for now. 

What are the startup scripts for RAID Devices and Enterprise Volume Management  ?
----- Trond[/QUOTE]

You probably want cron for other things, like updating the locate db.  Look at /etc/cron*/ to see what cron is running for you.

For raid, look at mdadm*, and for EVMS, look at evms (also check out lvm).

---

### Post by tronda on 2005-01-31
[QUOTE=mendicant]
For update-rc.d:
% update-rc.d -f <name> remove[/QUOTE]

Thanks. This was exactly what I was looking for.

---- Trond

---

### Post by mirtux on 2005-02-02
[QUOTE=mendicant]You shouldn't mess with the links in /etc/rc*d. You should use update-rc.d to disable services from starting up. This will just remove the links in /etc/rc*d. Somebody else on these forums recommended using rcconf at one point--never used it, and it seems not to be in main or restricted, so use at your own discretion.
   For update-rc.d:
   % update-rc.d -f <name> remove
 This will remove the links in /etc/rc*d without removing the original file in /etc/init.d/, which allows you to run /etc/init.d/<name> start[/QUOTE]
   Hi,
     i'm using **rcconf **and it seems that is working well. Simple interface (see attachment) not nice as *system-config-services *Fedora's distributions, but it's ok! Hoping this will help,
   
  Regards,
   MC

---

