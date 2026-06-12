---
title: "intrepid (base sys) install probs, need chroot advice"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by eilenbeb on 2009-01-30
-----solved, lets close this one.  Thread tools won't let me mark as solved for some reason-------------



Hi.  I have a CLI install of 8.10 Intrepid that needs some help.
Networking and cdrom support broken.  Chrooting from Hardy partition.
I've installed this using both the alternate cd and the minimal (web based) cd, and have had the same probems both times.

I can't seem to get a usable IP address (comes up as 240.0.0.0)  which is NOT what my isp is trying to give me.  So natrually, I'm having tropuble getting apt to work.

I also can't seem to install from a cdrom.  Apt-cdrom refused to acknowledge any cd whatsoever.  My cdrom drive wasn't listed in fstab, so I tried to mount it manually.  Intrepid then tells me that iso9660 isn't a recognized file system type.

So, I decided to try doing some apt- stuff from my Hardy partition.
I used the commands (from within Hardy):
  sudo chroot /media/sdd1
  sudo apt-get update
/media/sdd1 is where my intrepid / is mounted with exec priv's.
Package lists were downloaded, and I then did a:
  sudo apt-get install [everything I need to get synaptic running]

So before I hit 'y' then 'enter' is it safe?
do I need any sys on sys or proc on proc commands?
will apt-get screw my hardy install with intrepid stuff?

Thanks in advance

ps.  there should be some tut's on chrooting and the like somewhere.  the manpages still look like command-line-salad to me.

---

### Post by caljohnsmith on 2009-01-30
In order to successfully use most programs in a chroot environment, you first have to set up the chroot environment more completely before chrooting. Specifically, it would be good to mount the pseudo-file systems in /proc /dev and /sys into your chroot environment, because those file systems are normally only created when you boot into the partition you are trying to chroot into. So how about trying:
```
sudo mount --bind /dev /media/sdd1/dev
sudo mount --bind /proc /media/sdd1/proc
sudo mount --bind /sys /media/sdd1/sys
sudo cp /etc/resolv.conf /media/sdd1/etc/resolv.conf
sudo chroot /media/sdd1
```
The resolv.conf file has a list of your DNS servers, so you normally will need that if you want to access the internet while in your chroot environment. After you've chrooted, try running your commands, and let me know how it goes.

---

### Post by eilenbeb on 2009-01-30
Yes, those are the commands I was looking for.

What I need now (I will run them in a few minutes) is to understand them.
I have never been comfortable chrooting because I don't fully understand what the commands do.

Do you know of any place I could learn more about this process?  My searches have been coming up empty.

Anyways, I'll give them a try and post back.

thanks,
b

---

### Post by eilenbeb on 2009-01-30
Apt-get update gives me a much bigger list this time.  Looks much better.

I'm installing what I need to get into synaptic on my Intrepid partition, so I can poke around and see what's missing/broken.

Hopefuly the resolv.conf fixes my Intrepid IP address problem, will find out in a minute.

---

### Post by eilenbeb on 2009-01-30
During apt-get install, hal and gnome-mount failed to configure.

Booting into my Intrepid install, still no internet connectivity.

Unable to startx, could not merge x-resources, and had no mouse support (couldn't click on the OK on the error message)

Back in Hardy, I chrooted in again and tried to apt-get install hal.

> sudo apt-get install hal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
hal is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 20 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up hal (0.5.11-4ubuntu4) ...
 * Reloading system message bus config...                                                                                                                                                                        Failed to open connection to system message bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
invoke-rc.d: initscript dbus, action "force-reload" failed.
polkit-auth: This operation requires the system message bus and ConsoleKit to be running
polkit-read-auth-helper: needs to be setgid polkituser
polkit-auth: NotAuthorizedToReadAuthorizationsForOtherUsers: uid 0 is not authorized to read authorizations for uid 105 (requires org.freedesktop.policykit.read)
dpkg: error processing hal (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-mount:
 gnome-mount depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing gnome-mount (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 hal
 gnome-mount
E: Sub-process /usr/bin/dpkg returned an error code (1)

Looks like some dep's are broken in Intrepid.  Any ideas?

---

### Post by eilenbeb on 2009-01-30
Well, I think it's time to close this one.

When I was pouring through the output of trying to get into X I came across something interesting.

The build info reports one kernel version, while the report on the installed kernel shows another.

How did I end up with a server kernel, anyways?

Thanks for the advice, but I think it's time to re-install (or revert).

laters,
b

---

