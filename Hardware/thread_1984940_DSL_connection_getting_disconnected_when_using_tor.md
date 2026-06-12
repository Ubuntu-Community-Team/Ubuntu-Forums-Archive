---
title: "DSL connection getting disconnected when using torrent"
date: 2012-05-22
forum: Hardware
---

### Post by goodearth on 2012-05-22
Hello,
I am using Ubuntu 11.10 with Gnome 3 interface. The laptop is Dell XPS L502x. I am using a broadband connection(ADSL), where firstly the ethernet is connected automatically, its DNS, gateway, subnet and IP manually configured, and then a second DSL connection with a username and a password is created.

I use Deluge as my torrent client. Every time I open the torrent client and start downloading, both the two wired networks are disconnected within 5 to 10 minutes. No more wired networks are available in the network connections menu. When I restart the computer it works normally again. This happens only when downloading torrents and never anytime else, which has been verified multiple times.

Also another point is that very recently(within one week) torrent sites are supposed to have been blocked in India, but from this connection all the sites can be normally accessed and .torrent files can be downloaded. I am not sure if this has anything to do with the problem(because restarting gives it all back) but thought it would be worth mentioning. As I came home only 4 days ago, I don't know what could have happened at that time if I had used my laptop to download torrents.

Any help regarding this issue is highly appreciated.

Thank you.

---

### Post by papibe on 2012-05-22
Hi goodearth.

A few thoughts:

There are relatively well-know network devices (including DSL routers and modems) that don't work well with the torrent protocol. I would start by researching if yours is one of them (there used to be an updated list on the utorrent site).

Then if that's not the case, consider that the bittorrent protocol can overwhelmed the most trusted devices. I would tone down your Deluge configuration by reducing both the inbound and outbound to 50% of your band's capacity. Also, some clients have the ability to reduce the number of peer connections. Do that too.

If nothing works, I would request support from your ISP.

Regards.

---

### Post by ajgreeny on 2012-05-22
I've never used Deluge, and know nothing about it, but I wonder if it is worth trying to use the default app, transmission, which I have always found to behave impeccably; it's fast and simple.

---

### Post by goodearth on 2012-05-22
Hi papibe,

Most probably the first is not the case, because I have been using the same modem and connection for nearly 6 years, in the main PC, and with xp, vista, ubuntu and mint, well above a year each.

I had set the maximum number of peer connections to 200 in Deluge. I'll set it to 50 next time and report. But I don't want to tone down the bandwidth to half because 6 hours of free usage is all what I get for downloading, that too 2 mbps.

Thank you very much for your help.
Regards.

edit: ajgreeny, I installed Deluge for its better categorization system(I download many torrents at once) and somewhat utorrent like interface which I had been used to for a few years.  It would be best for me if the issue can be solved without removing deluge. Of course, if there is no other option, I'll have to go down that path. Thanks.

---

