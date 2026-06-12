---
title: "Less is more?.. Core 2 Duo vs Celeron, Hardy, NTP, NTPDATE"
date: 2008-08-01
forum: General Help
---

### Post by ruipedroca on 2008-08-01
Hi,

I've got this peculiar situation and I'd like to hear the opinion of someone more experienced in this matters.

1. Previous situation:
Ubuntu 8.04 Desktop 32bits running as a VMWare host
Processor: intel celeron 420 @ 1.6mhz
Ram: 3gb ddr2 667mhz
VMWare guests: two Fedora 7 and one SME Server
Time sincronization: Host and guests running NTPd

2. Present situation:
Ubuntu 8.04 Desktop 64bits running as a VMWare host
Processor: Core 2 Duo @ 2.33mhz
Ram: 6gb ddr2 667mhz
VMWare guests: two Fedora 7 and one SME Server
Time sincronization: THIS IS MY PROBLEM

I've tried the exactly same host and guests NTPd configuration, but it didn't work. 
Motive: it seems that the time synchronization between VMWare hosts and guest are badly aggravated wiht the Core 2 Duo processors.
Attempted alternative solution: guests cron job running ntpdate every minute (and yes, I've stoped the ntp service). 
I know that running this cron job every minute isn't a good solution, but the guests were gainning about 30 seconds every minute!

Everything apparently went smooth, but now some users using samba complaint that some files were missing. At this time, I must say that in that guest running samba there are some more cron jobs ruuning, moving files between some folders and deleting the previous.
In the second guest, running a forum, the forum froze in the next day and I had to restart the server (it never happened before with the first intel celeron server..).
In the third server, mail server, everything seems to be just fine.

Conclusion:
I'm going to return to my previous server, because it always ran perfectly!
But I'm very frustated for having the time, money and effort to built a much more powerful server and being stopped by this litle npt problem!

The reason I'm posting this post is to see if someone else is/was having the same problem!

Any ideas?

---

### Post by c2olen on 2008-08-01
Because you didn't supply the info I have to ask...
Doe you have the VMware Tools daemon running in the guests? The daemon should also help in timing issues. 
Most probably you have the tools installed, so please forgive me if it was redundant.

I myself have a Debian Etch server (Celeron 2,4GHz)  hosting VMware guests (2 x Feisty and W2003) which also seem to have time issues. I run ntpdate every 24 hours. The difference is usually a couple of minutes at the next cycle. So this isn't necesseraly a Core2Duo problem.

So i am also curious what others seem to experience.

---

### Post by ruipedroca on 2008-08-01
Your Celeron 2.4 may be based on C2D but as you problably know the advanced features are disabled by intel and maybe that's enough to make the difference.
I have VMWare tools installed but not running because I didn't need them. 
However, I think that the perfect solution would be the ntpd.

I'm going back to the initial server to stop having problems.
Then, I'll start testing with the C2D and see if a solution appears.

Regards

---

### Post by c2olen on 2008-08-01
> **ruipedroca said:**
> Your Celeron 2.4 may be based on C2D but as you problably know the advanced features are disabled by intel and maybe that's enough to make the difference.

Actually, i didn't know. Thanks for the tip. I'll go look this up, because i do want to know. 

> 
Then, I'll start testing with the C2D and see if a solution appears.


Good luck on that, and keep us posted.

---

### Post by ruipedroca on 2008-08-01
After googling a litle, I've read that "vmware tools should allow a guest with a slow-running clock to catch up, but as far as I can tell it won't slow it down".
It's in this post:
[http://blog.autoedification.com/2006/11/vmware-guest-clock-runs-fast.html](http://blog.autoedification.com/2006/11/vmware-guest-clock-runs-fast.html)

---

### Post by ruipedroca on 2008-08-01
It seems I found the solution in this same link:
[http://blog.autoedification.com/2006/11/vmware-guest-clock-runs-fast.html](http://blog.autoedification.com/2006/11/vmware-guest-clock-runs-fast.html)

In short, I've edited the file /etc/vmware/config and added this lines:
host.cpukHz = 2331000 
host.noTSC = TRUE
ptsc.noTSC = TRUE

note: 2331000 is the speed of my Core 2 Duo processor, which, as the same link says, can be viewed in more than one way, for example, this:
$ cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq 
or or going directly to the folder /sys/devices/system/cpu/cpu0/cpufreq and openning the file cpuinfo_max_freq. 

So far, almost an hour as passed and the difference of time between one virtual machine and the host is less than a second and in another virtual machine only two seconds. The third virtual machine has no gui and I didn't bother checking the time to the second, although I've checked by sending an email to myself and the minute was fine (seconds aren't showed), so I guess problably it's on time also.

However, at the time I'm testing there are no users logged in (I' guess I'm the only one working afterhours..) and I'm a little bit curious to see if this results when the servers are working heavily (although in the same post there's some more information that may help), so I think it's still a little bit early to draw definite conclusions.

I'll post feedback in a few days!

---

### Post by articpenguin on 2008-08-01
celeron 420 is based of the conroe core of core 2 duo.

---

