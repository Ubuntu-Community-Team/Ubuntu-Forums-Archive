---
title: "How to select a different xorg.conf before X startup?"
date: 2009-12-22
forum: Hardware
---

### Post by pjfarley3 on 2009-12-22
Is it possible to set up an init script (or other method) to select different xorg.conf files before X startup?

I have ubuntu 9.04 installed on a portable USB drive (WD Passport 500Gb) and want to be able to use it on both a laptop with:

ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)

and a desktop with nvidia 9400GT.

I can boot to each one by manually changing the xorg.conf file before shutdown on one machine (copy the right one for the next boot to xorg.conf), but ISTM there ought to be somewhere in the startup process where I could present a choice menu to pick which one to use, depending on which machine I am booting on.

Any help/info/RTFM you can provide would be appreciated.

Peter

---

### Post by kidders on 2009-12-23
Hi there,

An init script wouldn't be a bad idea imo. You could use a pre-existing one as a template & set something up to start late in the init sequence, but ahead of X11. A non-interactive script would probably be best, so you could try something like this ...[LIST]
[*]Suppose you had two files called /etc/X11/xorg.conf.nvidia & /etc/X11/xorg.conf.radeon.
[*]Afaik, Nvidia's vendor ID is 0x10de, so you could probably guess which version to use based on a test like **[ -n "`/usr/bin/lspci -d10de`" ]** ... true for Nvidia, false for anything else (ie Radeon).
[*]All that's left is to copy the right file to /etc/X11/xorg.conf.
[/LIST]

One possible addition would be to have your init script copy the file back to xorg.conf.radeon or xorg.conf.nvidia on shutdown, so any changes that got made to the file while X11 was running would be preserved for the next boot.

If you have trouble detecting the graphics hardware, an alternative way of figuring out which computer you're on is by MAC address. For example, **grep -li 00:11:22:33:44:55 /sys/class/net/*/address** would tell you whether any network interface connected to your box has the specified MAC address ... no output = no match.

One quick caveat: You probably know this already, but just in case you're tempted, I wouldn't recommend modifying X's own init script. Doing so would interfere with future software updates. (Even opening it, hitting CTRL+S and closing it again would be enough to create the potential for problems.)

I hope that helps.

---

### Post by pjfarley3 on 2009-12-26
Thanks, I also thought of the lspci automated solution after I posted my question.

Now my question is, where in the init process can I do that?  Or more specifically, where is X started up in the init/upstart process?  I have read that ubuntu is moving away from the classic init script setup and using upstart "events" to execute init scripts.  I looked at the /etc/events.d directory (I think that's what it was called, not on my ubuntu system at the moment), but I could not deceipher where X is started.

I see /etc/init.d/gdm too, but isn't gdm too late?  Isn't X already started when gdm is invoked?

Thanks again for your reply, and TIA for any further help you can provide.

Peter

---

### Post by kidders on 2009-12-27
I'm afraid I don't have a current desktop-edition Ubuntu install to work from at the moment, so I may not be of much help. From what I can gather, it doesn't look like upstart is fully implemented out of the box, so /etc/init.d still seems to be the place to look, but I could be wrong.

I wonder about giving something like this a try...```
#!/bin/sh
### BEGIN INIT INFO
# Provides:          whatever
# Required-Start:    $local_fs
# Required-Stop:     $local_fs
# Default-Start:     S
# Default-Stop:
### END INIT INFO

case "$1" in
  start)
    echo Start service here
  ;;

  restart|reload|force-reload)
    echo Restart service here
  ;;

  stop)
    echo Stop service here
  ;;

  status)
    echo Show service status here
  ;;
  *)
    echo Spit out an error message here
    exit 1
    ;;
esac

exit 0
```

Once you add it to the init sequence, check its position in the start order, by making sure it appears before, say, x11-common in **ls -l /etc/rcS.d**. Assuming it does, you could fill in the blanks in the script, so it does something useful.

---

### Post by pjfarley3 on 2009-12-29
> **kidders said:**
> I'm afraid I don't have a current desktop-edition Ubuntu install to work from at the moment, so I may not be of much help. From what I can gather, it doesn't look like upstart is fully implemented out of the box, so /etc/init.d still seems to be the place to look, but I could be wrong.

<Snipped>

Once you add it to the init sequence, check its position in the start order, by making sure it appears before, say, x11-common in **ls -l /etc/rcS.d**. Assuming it does, you could fill in the blanks in the script, so it does something useful.

Thanks for your continued assistance.  I would use the ubuntu-supplied init skeleton to create the script, but thanks for the example.  I still would like to know for sure just exactly where X is started up in the init scripts.  "x11-common" appears to set up directories for X, but doesn't (unless I just don't see it) actually start X.  Is it still the case that the binary "startx" is what actually starts X?  Or is that a cygwin-ism I am mis-applying to ubuntu (startx is the cygwin startup binary)?

Thanks again for your help.  Is there a more focused forum where X guru's might be hanging out that I could check out?  I didn't see any forum names that seemed focused on the X environment per-se, but then again I could be wrong (as I have been many times before... :)).

Regards,

Peter

Peter

---

### Post by pjfarley3 on 2009-12-31
Thanks again for your help, I just finished finding out that gdm is Gnome's replacement for xdm, the X display manager, so the gdm script /etc/rc2.d is what I have to precede with my selection script.

Regards,

Peter

---

