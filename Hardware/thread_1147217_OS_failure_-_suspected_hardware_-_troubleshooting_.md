---
title: "OS failure - suspected hardware - troubleshooting help"
date: 2009-05-03
forum: Hardware
---

### Post by dannyboy1121 on 2009-05-03
Hi Folks .. I need some suggestion for an approach to troubleshoot an issues I have with a home server.

I have a VIA Artigo - Pico ITX (basically a mini computer) which PXE boots across the network from my NSLU2 NAS (which I've hacked to provide NFS). Overnight, rsync backs up the changes from disk to disk in case of failure. If you've never seen the VIA Artigo - it's small enough to fit in drive bay - mine sits on a shelf with the rest of my home IT kit. It has no monitor or keyboard attached as it's supposed to be hidden out of the way.

This server does everything for me:
DNS, MAIL SERVER, LDAP for contacts and credentials, Sockso media server, Mediatomb for UPNP, MYSQL, LIGHTTPD web server, SSL VPN ..etc etc).

This thing has been running in one form or another without issue for ages but over the last couple of days it seems to keel over roughly every 12 hours and I can't figure out why.

I've hit the logs .. messages / syslog / debug etc .... and nothing. No panic messages ... everything cuts off dead. The next thing in the logs is the reboot info.

Visually, everything is illuminated .. and the raid0 flashdrive array I've set up is blinking away as if nothing is wrong - just no network access.

I fully intend to get hold of a monitor to see what's happening on screen - but I could do with some help for finding the root cause. It kind of looks like the thing is losing sight of the disk ... that would explain why nothing gets written to the logs perhaps.

I'm looking for a good way of troubleshooting the issue and would appreciate any ideas. Are there any logs that I can set up to trap problems? Are there any hardware testing utilities to stress components?

Keeping in mind that it's a diskless box using PXE to boot from the NAS so I can't go to things like memtest from GRUB.

Peace.

---

### Post by dannyboy1121 on 2009-05-03
Just one other question - is anyone aware of a good monitoring tool that would gather environmental stats on a rolling basis? Power / temp etc?

---

