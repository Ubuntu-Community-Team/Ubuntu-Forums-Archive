---
title: "[fail] synchronizing clock to ntp.ubuntulinux.org"
date: 2006-01-07
forum: Installation &amp; Upgrades
---

### Post by stroopwafel on 2006-01-07
I'm using:  Breezy Xubuntu (Toshiba Tecra laptop P2)

When starting up my linux I get the following message:
```
synchronizing clock to ntp.ubuntulinux.org 
Error: temporary failure in name resolution [fail]
```

WHat can I do to fix this?

---

### Post by dcstar on 2006-01-07
[QUOTE=stroopwafel]I'm using:  Breezy Xubuntu (Toshiba Tecra laptop P2)

When starting up my linux I get the following message:
```
synchronizing clock to ntp.ubuntulinux.org 
Error: temporary failure in name resolution [fail]
```

WHat can I do to fix this?[/QUOTE]
Edit /etc/default/ntpdate and comment out the entry - then it won't pause when you aren't connected to a network.

---

### Post by stroopwafel on 2006-01-07
[QUOTE=dcstar]Edit /etc/default/ntpdate and comment out the entry - then it won't pause when you aren't connected to a network.[/QUOTE]

I am connected to the network! It doesn't freeze, but it doesn't set my clock either :(

---

### Post by dcstar on 2006-01-07
[QUOTE=stroopwafel]I am connected to the network! It doesn't freeze, but it doesn't set my clock either :([/QUOTE]
The message says it timed out waiting for DNS to work, so either you don't have DNS set up or its taking too long to get it via DHCP at boot.

If its just a timing issue with your DNS, manually add the entry for that site in your hosts file.

---

### Post by stroopwafel on 2006-01-11
[QUOTE=dcstar]The message says it timed out waiting for DNS to work, so either you don't have DNS set up or its taking too long to get it via DHCP at boot.

If its just a timing issue with your DNS, manually add the entry for that site in your hosts file.[/QUOTE]

How do i manually add the entry nps.ubuntulinux.org in my hosts file?

---

### Post by stroopwafel on 2006-01-11
How do I manually change my clock settings (from the CLI, I'm using XFCE and can't find it anywhere in the menu)

OR BETTER: How can I manually force the clock to be synchronized over the network after startup? (since it fails during startup)

---

### Post by dcstar on 2006-01-12
[QUOTE=stroopwafel]How do I manually change my clock settings (from the CLI, I'm using XFCE and can't find it anywhere in the menu)

OR BETTER: How can I manually force the clock to be synchronized over the network after startup? (since it fails during startup)[/QUOTE]
Install the ntp-server package, you can then configure it to go to your selected external time server to keep the machine in sync.

As far as you hosts files goes, you can add the following line to the end of it:

82.211.81.145	ntp.ubuntulinux.org

---

### Post by grsuisse on 2006-04-14
If you are like me your router has problems with IPv6. To overcome this for ntp you need to make a copule of changes.
First ntpdate is called at start up. Its configuration file is /etc/defaults/ntpdate. Adding -4 to the line NTPOPTIONS will force ntpdate to use IPv4. My file looks like this:
# servers to check.   (Separate multiple servers with spaces.)
#NTPSERVERS="pool.ntp.org"
NTPSERVERS="ch.pool.ntp.org"
#NTPSERVERS="ntp.ubuntulinux.org"
#
# additional options for ntpdate
#NTPOPTIONS="-v"
NTPOPTIONS="-u -4"

Note that I have also selected a server closer to me (ch.pool.ntp.org). To find a list of alternative servers go to the following [http://www.pool.ntp.org/]("http://www.pool.ntp.org/")

That should fix your problems at start up. 

There is also a daemon that runs during your session and regularly checks the time. This is turned on from the System menu under Administration - Time and Date. You need to tick the box and then select some servers close to you (you can also add the pool referred to above). 

The daemon ntpd also needs to be forced to use IPv4. To do this edit the file /etc/ntp.conf. On every line that starts with the word "server" you need to put  "-4" between the word "server" and the name of the ntp server.  My file looks like this:
# /etc/ntp.conf, configuration for ntpd

# ntpd will use syslog() if logfile is not defined
#logfile /var/log/ntpd

driftfile /var/lib/ntp/ntp.drift
statsdir /var/log/ntpstats/

statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable


# You do need to talk to an NTP server or two (or three).
#server ntp.your-provider.example

server -4 ch.pool.ntp.org
etc.

---

