---
title: "How to make Ubuntu machine provide NTP time?"
date: 2008-08-29
forum: General Help
---

### Post by Krupski on 2008-08-29
Hi,

I'm running a NAS box built with Ubuntu Server 64 bit.

Of course, it's running the NTP daemon and synchronizes it's time over the Internet.

What I would like to do is additionally make my NAS box *SERVE* ntp time over my local intranet.

I've searched Google and found a few "how-to" pages... but their procedures didn't work. All involved editing /etc/ntp.conf

I know my NTP clients (i.e. Windows boxes) are working, because they can read and sync to, say, "time-a.nist.gov". But, if I try to sync to "192.168.0.11" (the IP of my NAS box) or it's network name ("storage") it fails.

How can I make my Linux box SERVE it's time to other local clients?

Thanks in advance!

-- Roger

---

### Post by kagashe on 2008-08-30
[Read this]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch24_:_The_NTP_Server").

> 3) If this server is also going to provide time for other computers, such as PCs, other Linux servers and networking devices, then you'll have to define the networks from which this server will accept NTP synchronization requests. You do so with a modified restrict statement removing the noquery keyword to allow the network to query your NTP server. The syntax is:

restrict 192.168.1.0 mask 255.255.255.0 nomodify notrap


In this case the mask statement has been expanded to include all 255 possible IP addresses on the local network. 

kagashe

---

### Post by Seti on 2008-08-30
```
man ntpd
``` will tell you the whole story.

---

### Post by Krupski on 2008-08-31
> **Seti said:**
> ```
man ntpd
``` will tell you the whole story.

Sorry... I've seen those links before (and more). I've tried the examples. They don't work for me. :(

---

### Post by Krupski on 2008-08-31
--nobody--?

C'mon... this should be simple...

---

### Post by Krupski on 2008-09-02
Can anyone help me with this?

I DID read all the suggested links and docs... I DID search Google until I went blind... I tried everything... nada.

All I want to do is make my File Server box (which syncs it's time via NTP) also PROVIDE time to Windows boxes on my local Intranet.

Am I missing a file or package? I only have "NTP" and "NTP-DOC" installed on my server. Do I need something else?

The file server and Windows boxes are all connected to a firewall router. Our local, internal IP addresses are 192.168.0.10 and up. The router itself (as well as the DNS server) is at 192.168.0.1

I'm sure all I need are a few small changes to /etc/ntp.conf... but everything I've tried didn't work.

After each change, I did restart NTP using the command '/etc/init.d/ntp restart'. I also tried completely rebooting the whole server box. Nothing worked.

Any help will be GREATLY appreciated (real help... not "see the docs" *please*).

Thanks.

-- Roger

---

### Post by mellowd on 2008-09-02
ntpd daemon needs to be running.

you then need to configure the windows boxes to get their time off your linux box, and not the internet

---

### Post by Krupski on 2008-09-02
> **mellowd said:**
> ntpd daemon needs to be running.

you then need to configure the windows boxes to get their time off your linux box, and not the internet

NTPD is running:

```

root@storage:/# ps -A | grep -i ntpd
 4965 ?        00:00:00 ntpd

```

Here's my /etc/ntp.conf file (change I made in bold):

```

# /etc/ntp.conf, configuration for ntpd; see ntp.conf(5) for help

driftfile /var/lib/ntp/ntp.drift

# Enable this if you want statistics to be logged.
statsdir /var/log/ntpstats/

statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable


# You do need to talk to an NTP server or two (or three).
[B]server time-a.nist.gov
server time-b.nist.gov[/B]
server ntp.ubuntu.com
**server butler.acsu.buffalo.edu**


# Access control configuration; see /usr/share/doc/ntp-doc/html/accopt.html for
# details.  The web page <http://support.ntp.org/bin/view/Support/AccessRestrictions>
# might also be helpful.
#
# Note that "restrict" applies to both servers and clients, so a configuration
# that might be intended to block requests from certain clients could also end
# up blocking replies from your own upstream servers.

# By default, exchange time with everybody, but don't allow configuration.
restrict -4 default kod notrap nomodify nopeer noquery
restrict -6 default kod notrap nomodify nopeer noquery

# Local users may interrogate the ntp server more closely.
restrict 127.0.0.1
restrict ::1

# Clients from this (example!) subnet have unlimited access, but only if
# cryptographically authenticated.
#restrict 192.168.123.0 mask 255.255.255.0 notrust

# If you want to provide time to your local subnet, change the next line.
# (Again, the address is an example only.)
**broadcast 192.168.0.255**

# If you want to listen to time broadcasts on your local subnet, de-comment the
# next lines.  Please do this only if you trust everybody on the network!
#disable auth
#broadcastclient

```


Other computers on my local Intranet can't get time from the file server. :confused:

---

### Post by Corrupter on 2008-09-26
Krup

```

# Clients from this (example!) subnet have unlimited access, but only if
# cryptographically authenticated.
#restrict 192.168.123.0 mask 255.255.255.0 notrust
```

change the directive to:

```
restrict 192.168.1.0 mask 255.255.255.0 nomodify notrap
```

give it a try.

---

