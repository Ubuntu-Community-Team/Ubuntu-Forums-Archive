---
title: "Shutting Down and seeing Error Screen Flash"
date: 2008-08-08
forum: General Help
---

### Post by KarmaticStylee on 2008-08-08
Just installed a fresh copy of Ubuntu 8.04.  When I restart or shut down, right before the computer turns off a quick black screen with white text pops and appears to be an error.  It's so quick so as to be unreadable.. so far no problems but just knowing that something is off bothers me

---

### Post by aaronanderson on 2008-08-08
It's probably nothing like you mentioned. One place that you can check is the system log files. The ones that might have something are:
/var/log/syslog
/var/log/messages

You should be able to identify in the file where you computer initially is booting up. Check what is happening right before that.

If the messages are appearing after you filesystem has been unmounted, then there might not be much to do.

In theory you could try using the pause button on the keyboard. Not sure if that really is honored much anymore.

Hope this helps.

---

### Post by KarmaticStylee on 2008-08-08
Looks like SOMETHING is going wrong :\ the following from the syslog

Aug  7 21:34:16 eric-desktop -- MARK --
Aug  7 21:36:04 eric-desktop init: tty4 main process (4556) killed by TERM signal
Aug  7 21:36:04 eric-desktop init: tty5 main process (4557) killed by TERM signal
Aug  7 21:36:04 eric-desktop init: tty2 main process (4559) killed by TERM signal
Aug  7 21:36:04 eric-desktop init: tty3 main process (4562) killed by TERM signal
Aug  7 21:36:04 eric-desktop init: tty6 main process (4563) killed by TERM signal
Aug  7 21:36:04 eric-desktop init: tty1 main process (5510) killed by TERM signal
Aug  7 21:36:05 eric-desktop gdm[5337]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Aug  7 21:36:05 eric-desktop gdm[5337]: WARNING: Request for invalid configuration key xdmcp/Enable=false 
Aug  7 21:36:05 eric-desktop avahi-daemon[5007]: Got SIGTERM, quitting.
Aug  7 21:36:05 eric-desktop avahi-daemon[5007]: Leaving mDNS multicast group on interface eth0.IPv4 with address ***(insert my IP here)***.
Aug  7 21:36:06 eric-desktop kernel: [ 3758.708783] ip6_tables: (C) 2000-2006 Netfilter Core Team
Aug  7 21:36:07 eric-desktop exiting on signal 15
Aug  7 21:37:08 eric-desktop syslogd 1.5.0#1ubuntu1: restart.

---

### Post by aaronanderson on 2008-08-08
I'm not so sure.

The tty processes being killed by the TERM signal is fine. That is just normal shutdown. The TERM signal is the "friendly" way of telling a process to stop.

gdm asserts an error. I wouldn't really concern myself with this since you are shutting down. It's probably attempting to do some cleanup while closing and failed to free some memory or something. Not a big deal since you are rebooting.

avahi-daemon also received the TERM signal and is just stating that it is stopping.

Doesn't looks like there is anything to be concerned about, but maybe other people in the forum may have another opinion.

---

### Post by rocketero2008 on 2008-09-01
> **aaronanderson said:**
> 

gdm asserts an error. I wouldn't really concern myself with this since you are shutting down. It's probably attempting to do some cleanup while closing and failed to free some memory or something. Not a big deal since you are rebooting.
.

 GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed

IT IS A BIG DEAL as it hangs at restarting for one or two minutes witch if you are in a harry is very annoying !

---

