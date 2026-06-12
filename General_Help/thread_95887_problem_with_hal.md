---
title: "problem with hal"
date: 2005-11-27
forum: General Help
---

### Post by o_fortuna on 2005-11-27
When I start up gnome, I get the message "Internal error     failed to initialize HAL"

Is this a problem? Adding new hardware while the system is running (adding disks, inserting CDs, etc) doesn't seem to be detected automatically anymore, when I put in a CD I have to manually mount it, and the same goes with when I hook up my iPod.
I tried restarting dbus, but it didn't work:
```
~$ sudo /etc/init.d/dbus restart
 * Stopping Hardware abstraction layer:                                  [ ok ]
 * Stopping system message bus... start-stop-daemon: user `messagebus' not found
 (Success)

```
I get the feeling that something funny is going on. Durning installation, it said that some packages "could not be installed," I think, but when I logged in, I couldn't find any packages that were installed wrong. I also tried to reinstall HAL, but that didn't fix the problem.

Finally, on yet another related note, I can't install network-manager because dhcdbd won't install. I put that here because it seems related to the fact that hal isn't working. I get this error message:
```
 Failed to open connection to system message bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
dpkg: error processing dhcdbd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 dhcdbd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Any ideas on why hal isn't working or why there is no 'system message bus'? Any way to fix the problem short of trying to reinstall the operating system?

---

### Post by crispingatiesa on 2005-11-27
I ran into the same problem when plating with the booting options. I dissable the hotplug utilities at boot time. Have you ben playing with the boot manager?

---

### Post by o_fortuna on 2005-11-27
> I ran into the same problem when plating with the booting options. I dissable the hotplug utilities at boot time. Have you ben playing with the boot manager?

Er... what's the boot manager? I doubt I've messed with it since I dont' know what it is;) . If you mean GRUB, yeah, I put a splashimage in, but I don't think that would mess anything up.

Other than that, everything is unchanged; it doesn't say 'failed' next to 'starting hardware abstraction layer' when I start the computer, either.

---

### Post by o_fortuna on 2005-11-27
Well, I found out why it doesn't say 'failed' next to 'Starting Hardware Abstraction Layer' during bootup - it never gets that far. It reaches 'Starting System Message Bus' then ends bootup, without OK or anything; it just starts gdm and I see the login screen.

What does the System Message Bus do? Is its refusal to start problematic for the system? Obviously, it isn't letting dhcdbd install, which is quite annoying, as well as forcing me to manually mount anything I attach to my computer or any discs I insert.

How can I properly install HAL/fix the problem with the system message bus? Does anyone else have this problem? :confused:

---

