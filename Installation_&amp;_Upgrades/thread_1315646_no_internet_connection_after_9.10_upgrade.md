---
title: "no internet connection after 9.10 upgrade"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by bergspyder on 2009-11-05
I'm running 2 identical Dell C640s on same router except one runs ubuntu 9.04 & firefox 3.5.1, the other runs ubuntu 9.10 & firefox 3.5.4

Problem is Dell running 9.10 (since upgrade): It recognizes router, ping works, says it's on line etc., but firefox won't launch internet, (all) "web page not found"

Dell running 9.04 working perfectly as always. So I checked all network & firefox settings and as far I see all are identical

Any ideas anyone? Many thanks for looking

---

### Post by Farajamo on 2009-11-05
Yeah, I'm having the same problem too. Any help would be greatly appreciated.

---

### Post by s_raiguel on 2009-11-05
Could it be that the automatic DHCP protocol isn't implemented or isn't working, so it can't resolve internet addresses? Maybe using a working machine, you could find out what your name server's address is and manually configure the network for that name servers.

---

### Post by pdoes on 2009-11-05
Just to check some things could you open a terminal and do the following command:

```
sudo cat /etc/resolv.conf
```

What is the output on both machines?

---

### Post by bergspyder on 2009-11-06
Thanks for reply.
NetworkManagers of both machines show "nameserver 192.168.1.1"

---

### Post by pdoes on 2009-11-06
You said ping works, is that a ping to an IP or to a name?

Will this 
```
dig cnn.com
```

resolve addresses on the machine that's not working?

---

### Post by bergspyder on 2009-11-07
Pinged router IP address. Should I try pinging router name (which I asssume is Auto eth0 in my case)?

$ dig cnn.com produces on working machine 

; <<>> DiG 9.5.1-P2 <<>> cnn.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 20996
;; flags: qr rd ra; QUERY: 1, ANSWER: 6, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;cnn.com.			IN	A

;; ANSWER SECTION:
cnn.com.		52	IN	A	157.166.255.18
cnn.com.		52	IN	A	157.166.226.26
cnn.com.		52	IN	A	157.166.226.25
cnn.com.		52	IN	A	157.166.224.26
cnn.com.		52	IN	A	157.166.224.25
cnn.com.		52	IN	A	157.166.255.19

;; Query time: 86 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Sat Nov  7 09:23:12 2009
;; MSG SIZE  rcvd: 121


$ dig cnn.com returns on machine not working:

; <<>> DiG 9.6.1-P1 <<>> cnn.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 41430
;; flags: qr rd ra; QUERY: 1, ANSWER: 6, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;cnn.com.			IN	A

;; ANSWER SECTION:
cnn.com.		182	IN	A	157.166.224.26
cnn.com.		182	IN	A	157.166.255.18
cnn.com.		182	IN	A	157.166.255.19
cnn.com.		182	IN	A	157.166.224.25
cnn.com.		182	IN	A	157.166.226.25
cnn.com.		182	IN	A	157.166.226.26

;; Query time: 84 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Sat Nov  7 09:34:17 2009
;; MSG SIZE  rcvd: 121

Thanks

---

### Post by murrayhansen on 2009-11-07
Hi,
Just upgraded my Dell laptop from 9.04 to 9.10 (clean install) and same problem.
I can connect to my router and ping web addresses, but no internet traffic via Firefox.
I have a PCMCIA wireless card that worked fine with 9.04.
Just tried with a wired connection and same problem.
Followed the instructions for disabling IPv6 but no luck.
Changed permissions for user to allow connections to internet, but still nothing.
VERY frustrating, and annoying.
Have two other machines running 9.04 but will not upgrade until this issue resolved.
And very sorry to say this, because I am a rock solid Ubuntu  (since version 6) and Linux fan, but this is not good.
Imagine all the newbies downloading Ubuntu for the first time, because of the good reviews of 9.10 and having this problem.

---

### Post by onurdas on 2009-11-07
using AOA 150. Network manager says auto eth0 connected. But firefox  synaptic cannot get connected. Network tools: ping traceroute works. Emphaty is working.

disabling ipv6 solved firefox problem but synaptic stil can't connect.

---

### Post by murrayhansen on 2009-11-07
have disabled ipv6 via:
[FONT=Verdana] 
in terminal
[COLOR=#000000] Code:[/COLOR]
gksu gedit /etc/sysctl.conf
and add this line
net.ipv6.conf.all.disable_ipv6=1
[/FONT]
And in firefox via config:about

That has allowed me to connect to the internet via firefox.

But still no connection via synaptic or the software centre.

checked entries in /etc/resolv.conf
and all looks fine.
Gave laptop a static IP address but no difference.

this is wasting far too much of my time.

---

### Post by DiogoFC on 2009-11-07
I have the same problem. Would appreciate some help, too.

---

### Post by DiogoFC on 2009-11-07
Well, actually now it is working, but after trying a lot of solutions I don't which of them is responsible for that.

Probably it was forcing the following jaunty packages: network-manager, network-manager-gnome, libnm-glib0 and pptp-linux.

But only after two restarts [?] it did take effect, so maybe it was something else I did.

---

### Post by bergspyder on 2009-11-08
I agree with murrayhansen, particularly concerning Linux reputation
I'm giving up & going back to 9.04 (but not Windows)
Thanks to all for your help

---

### Post by bergspyder on 2009-11-11
> **bergspyder said:**
> I agree with murrayhansen, particularly concerning Linux reputation
I'm giving up & going back to 9.04 (but not Windows)
Thanks to all for your help


So, after ubuntu 9.10 internet connection failure, tried reinstalling 9.04 but get error message "[   3.679595] IO APIC resources could not be allocated." Reburned DVD with ubuntu-9.04-desktop-i386.iso several times & rebooted but always same result. Can anyone help on this one?

---

### Post by bwdease on 2009-11-11
[PHP] Re: no internet connection after 9.10 upgrade
Well, actually now it is working, but after trying a lot of solutions I don't which of them is responsible for that.

Probably it was forcing the following jaunty packages: network-manager, network-manager-gnome, libnm-glib0 and pptp-linux.

But only after two restarts [?] it did take effect, so maybe it was something else I did.[/PHP]

Ok!  I think I may have stumbled across something here.  I found this on another sight, so here goes....
-open firefox
-"about:config" in the address bar
-click "I'll be careful.  I promise."
-in filter type "network.dns.disableIPv6"
-make it "true"
-close firefox and try again.

I noticed a difference right away in my browser.  Worth a try for others who are experiencing the say problems.  I did still have internet though, but reallllllll slow.  After this change,  It's now normal speed for me.  Good luck!!!

---

### Post by toxicpoison on 2009-11-12
about:config" in the address bar
-click "I'll be careful.  I promise."
-in filter type "network.dns.disableIPv6"
-make it "true"
-close firefox and try again.


this works for getting online with firefox .  But still no connection via synaptic or the software centre.I also havesame prob. aseveryone else everything seems fine with my connection , but ain't. I also am goung back to 9.04. Totally fed up with this prob. If anyone has a solution please post or messager or email me thanks

---

### Post by barkhat on 2009-11-13
I just installed 9.10 on a new computer with Vista installed. I can't get a connection to the Internet. I have other computers which are connecting just fine, including this one on the Vista portion. It's wireless (and so are the others) including one using Linux Mint and a Mac OS. I can't figure out what to do.  

Trying to follow what some have said here I tried the "cat /etc/resolv.conf" command and get No such file or directory. Of all the things on a computer that I think I understand networking isn't one of them.

How can I get connected to the Internet? All other computers are working just fine. I'd appreciate some help. Thank you.

---

### Post by Justin Pentecost on 2009-11-13
I'm pretty sure this is a DNS related problem .. 

I've take the advice here and disabled the ipv6  .. 

The only thing I haven't done is to turn off the ipv6 at boot time .. 

There is some code to put into the Grub file to do this .. But I don't have grub file (Either I have no grub or no config file for it this is 9.10 running on it's own ..)

Should I create a grub file or is there another file that runs on startup I could put the code in ?

---

### Post by khaktus on 2009-11-18
The same issue for me on DSL. I was working on 9.04 for a few months without problem, now absolutely no internet connection on 9.10 - neither in Mozilla, nor in Synaptic. However, as I run dual boot with XP, on Windows, network connection is fine. Lucky me...

There are so many bugs launched and so many forums with dozens of workarounds for experts, creating new bugs... Can somebody write a step by step solution for newbie?

[COLOR=Red]0. The network is **not** working. (Don't tell me to download something).
1. What to do/rewrite/edit/launch to make a temporary workaround - network somehow working (mozilla, synaptic, or whatever)
2. What to do to download/get somehow some official fix (not creating new bugs) ... if it already exists.[/COLOR]

I'm not satisfied with answers like "upgrade NM with ppa" or "try pppoeconf"... it doesn't tell me much.
[B]
Please, someone, make a clear summary. [/B]

Do not send me another links to read endless forums... I have spent hours reading them... I'm used to the plurality of responses and solutions while working with Ubuntu, but having such a major problem, I'm loosing my patience. It is a major issue and newbies are not able to spend days reading forums, that offer so many workarounds, that need to be topped by other workarounds... I need to see what to do right now and not to read what hundreds of people tried... Where is Ubuntu's official solution? They should have a step by step fix on the first page of their web.

---

### Post by michael.barnes on 2010-02-04
I know this is an old thread, but I didn't see a final answer.
I ran into a similar problem.  I upgraded from 9.04 to 9.10.  Some things worked, some did not, like dig, host, etc.  I checked /etc/resolv.conf and found:

nameserver 10.33.8.11 10.33.4.136

I changed it to:

nameserver 10.33.8.11
nameserver 10.33.4.136

and all was well.

Michael

---

### Post by roeghar on 2010-02-04
Well I'm glad I didn't get as far as some of you and loose my internet connection with 9.10. When I tried several times today to upgrade via the Update Manager, I couldn't get past the setting new software channels part. Some where near the end of that section, but before getting new packages I got this message: 

[COLOR="DarkRed"]W:Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/karmic/Release](http://ports.ubuntu.com/ubuntu-ports/dists/karmic/Release)  Unable to find expected entry  partner/binary-powerpc/Packages in Meta-index file (malformed Release file?)
, E:Some index files failed to download, they have been ignored, or old ones used instead.[/COLOR]

Well fortunately it returned to 9.04 which is working well. Guess the only thing to do is wait until the malformed release file or whatever gets fixed.

---

