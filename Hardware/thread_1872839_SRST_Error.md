---
title: "SRST Error"
date: 2011-10-31
forum: Hardware
---

### Post by interacter on 2011-10-31
Hi all

Still having huge issues with the netbook (Acer Aspire One).  Over the weekend, I got Ubuntu 11.10 installed and working - both off the USB and without the USB.

Hurrah, I thought.  Fixed.

However today I get a black screen with a message about the grub failing.  

So I reboot, run a memtest.  100% pass.  Try the "Ubuntu, with Linux 3.0.0-12 generic (recovery mode) option".  No joy there.

And then the following appears:

SRST failed (errnum=-16)

This comes up quite a few times on a black screen then nothing happens.

Have had a google and can't see anything obvious (apart from lots of threads about resetting jumpers - bt I haven't played with anything like that).

Do you have any ideas at all that might help?  It's weird that it was working and now isn't...

Thanks
Neil

---

### Post by interacter on 2011-10-31
Quick update - tried one more reboot "normally" (i.e. not recovery mode or anything).  Great long list of errors:

rm: cannot remove /var/lib/urandom/random-seed : read-only file system
chown: changing ownership of /tmp/.lib/.x11-unix : Read-only file system
screen-dispatcher disabled: edit /etc/default/speech-dispatcher
Checking for running unattended-upgrades:
Starting bluetooth
Pulseaudio configured for per-user sessions (this one has a yellow asterisk next to it)
saned disabled: edit /etc/default/saned
touch: setting times of /var/lib/sudo : Read only file system
touch: setting times of /var/lib/sudo/interacter: Rad only file system
touch: cannot touch /var/lib/sudo/interacter/0 Read Only file system
Checking battery state
/usr/sbin/pm-powersave: 83: cannot create /var/log/pm-powersave.log: read only file system

grub-editenv: err: cannot open the file /boot/grub/grubenv.


And that's it.  That screen is static and nothing moves!

---

### Post by interacter on 2011-10-31
Oh dear. Just turned the netbook on, and it couldn't find the HDD.

Got the BIOS to load set up defaults, and it sort of came back.  Ubuntu Splash screen came on, but then went black and nothing.

Sorry to belabour these points, but any ideas? Anything would be good right now!  

I suspect full HDD collapse...

Neil

---

