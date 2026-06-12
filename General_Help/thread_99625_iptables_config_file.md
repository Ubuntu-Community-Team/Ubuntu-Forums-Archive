---
title: "iptables config file"
date: 2005-12-05
forum: General Help
---

### Post by unclben on 2005-12-05
First question: Does iptables have a config file that stores its settings? I assumed it does, but I can't find one anywhere on my Breezy install. I found a bunch of files under /lib/iptables, but it was all files ending with .so. If there is a config file, where the heck is it?

Second question: How do you folks back up your iptables configuration? I'd like to start keeping backups so I know what my previous setup was if I, for some reason, have to reinstall or otherwise nuke my OS. My original idea was to back up the config file (see question #1, above), but is there a better way? Aside: I intend to configure the firewall using Firestarter. I'm slightly flexible on that, but right now I have bigger fish to fry and would like to stay with what's familiar.

---

### Post by gruepig on 2005-12-06
I've personally adopted the habit of creating /etc/iptables for my iptables config.  (If there's an ubuntu standard location, I don't know it, but I haven't looked that hard.)  I bring it up on boot with 'iptables-restore < /etc/iptables'.  I add this to either /etc/init.d/networking or /etc/network/interfaces (as an up command).

For backing up, I'd just copy this config file.  You can dump the current running config to a file with 'iptables-save > some_file'.

---

### Post by unclben on 2005-12-06
[QUOTE=gruepig]For backing up, I'd just copy this config file.  You can dump the current running config to a file with 'iptables-save > some_file'.[/QUOTE]Thanks for that tip, gruepig. That will work very well for me, and keep my backup method independent of which front-end or script I use to edit iptables.

---

