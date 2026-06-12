---
title: "Weird disk space problems"
date: 2005-06-27
forum: Hardware &amp; Laptops
---

### Post by Krank on 2005-06-27
My Ubuntu-running server has recently begun to act weird.

First, my Internet went down. I checked my firewall's throughput - and discovered that, for some reason, there was an anormous amount of network input/output going on. Normal internet load for me is about 200kb in, 200 kb out - now it was 3-19 mb in/out.

I did some rebooting and blocked off almost every port, and closed down Azureus and aMule - and the problem went away.

I fired up aMule and Azureus again, carefully checking the network load. Finding no problems, I decided it had been just a momentary glitch or something.

Suddenly, the day after this, the hard drive begun acting weird. Free space fell from 4 gb to 0 in just a few seconds. I rebooted, and this too stopped. Now, however, I have the following problem:

The Gnome system monitor reports 3,5 gb free. And yet, both aMule and Azureus show an "insufficient space" error, and when I browse my network shares (samba) from my Windows machine, the Windows machine reports that the server has less than 10 mb free...

Any ideas? 'Cause i'm all out...

---

### Post by Krank on 2005-06-27
Quick update:

Removed one 2 gb file. No effect in either gnome system monitor nor the other checks.

xdiskusage, however, saw the change.

This is getting weirder by the byte...

---

### Post by rockmusic88 on 2005-06-27
Seing as your running services like samba you could well have been hacked.

---

### Post by Krank on 2005-06-27
[QUOTE=rockmusic88]Seing as your running services like samba you could well have been hacked.[/QUOTE]

Yup, that was my first thought as well. Problem is, they shouldn't have been able to come throygh my firewall... Or at least I don't think they shouldn't. The only "open" ports before were 80 (for my webserver - I use Apache), 21 (for FTP - ProFTPd) and two five-number-ports for Azureus and aMule. All other ports are, or should be, blocked.

Although me being hacked isn't such a bad thought after all. These problems didn't occur until I switched from Smoothwall to Windows 2k (with Kerio Personal Firewall).

OK, I just know I'm going to be asked "why", so here it is: For some daft reason, which I could never figure out, Smoothwall sometimes apparently identified itself as a local IP on the "red" interface, thereby wreaking havoc on my ISP's network. I was contacted by my ISP, who were as mystified as I was as to the reasons of Smoothwall acting up, but were also very firm in that I should, if I wanted to continue being online, fix the problem - and fast. I didn't have a hub at home and thus had problems sniffing - and was running out of time. So, I installed Win2k and Kerio personal Firewall, which always served me reasonably well in the past.

Fortunately, I have managed to pick up a hardware firewall real cheap, and I'm currently waiting for it to arrive - should be at most a week.


But, what the heck do I do in the meantime? It seems as if the attacks, if that's what they were, have stopped - at least for the moment. Is there nothing left to do but a complete and utter reinstall? Or is the system salvageable? How do I find out, and is there any way for me to reclaim my disk - and how?

---

