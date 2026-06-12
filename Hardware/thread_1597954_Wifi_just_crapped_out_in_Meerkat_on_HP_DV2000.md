---
title: "Wifi just crapped out in Meerkat on HP DV2000"
date: 2010-10-15
forum: Hardware
---

### Post by Jugney on 2010-10-15
Hi all,

I've been searching and trying stuff for about an hour, but noticed that since I'm on an old laptop, it's hard to get results that are more recent, so I thought it was worth posting a new threat, since Wifi in Ubuntu has come a long way in the last few years. 

I just installed 10.10 a couple days ago, and my wifi worked by enabling the b43 driver in Additional Drivers. But suddenly last night, it stopped working. I tried the STA driver, but now luck. The hard switch on the laptop is on, but the light stays orange rather than turning blue when it's set to on. 

I'm on a dual-boot with Windows 7, and the wifi still works in Windows. 

Whenever I load Ubuntu now, the wireless is disabled. I right-click the network icon and enable wireless. Then the message becomes "Disconnected" under Wireless Networks in gray.

lspci shows this:

```
Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

```
and rfkill list shows this:

```
0: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
```

Any advice??

PS. I love how much more user-friendly 10.10 has become - in the little things, like the install process. And fsck just ran on one of my boots. I used to get very annoyed by this. But this time I saw a pleasant Ubuntu graphic and the option to cancel the scan if I wanted to in clear wording! Not that I needed to - it was done in about 15 seconds. Well done Ubuntu! Can't wait to see how much more user-friendly things will become.

---

### Post by Jugney on 2010-10-16
bump

---

### Post by Jugney on 2010-10-16
UPDATE: I noticed when I boot into Windows, the light by the Wifi switch starts out orange. I need to turn the hard switch off and back on before it turns blue and detects networks...

The laptop also does get very hot underneath in the area where the Wifi card is. There is a fan that blows straight down there, and in the natural position in my lap, sometimes the vent is obstructed.

The laptop has gone strong for 4+ years...just hoping the Wifi card or motherboard isn't going.

Any advice? As I mentioned, Wifi worked just after installation of Ubuntu, by activating the B43 driver. But 2 days after installation, it just stopped working.

---

### Post by megalodon1970 on 2010-10-16
Even if it is going bad you can get a replacement from a reputable
seller on ebay for about 30 bucks with shipping. I'd actually go
for that if your laptop is still good otherwise.

---

### Post by Jugney on 2010-10-16
That's good to know. 

Are there any tests I can do to verify its condition? I'm on the laptop in Windows right now posting, so it still works in some circumstances...

---

### Post by dontic on 2010-10-21
i have exactly the same problem, it's a hp dv2000,  the orange led the soft blocked and it also works well on windows 7
i don't think that this is a problem with the card
how can we turn on the card?
thanks

---

### Post by zapata131 on 2010-10-21
Got THE answer. Well I've got a Pavillion myself and got the same problem, weird thing, my girlfriend got the problem too while updating to 10.10.

Anyway, the problems seems to be that somehow the SO blocked our wireless adapter off by software, so I tried to turn it on with:

[FONT="Courier New"]ifconfig wlan0 up[/FONT]

But it said i've got some strange rf-kill issue so i googled it and some other guys got the problem in arch: [https://bbs.archlinux.org/viewtopic.php?pid=775217](https://bbs.archlinux.org/viewtopic.php?pid=775217)

So i googed a little more and it turns out you can 'unblock' the wireless card with a tool called rf-kill over here: [http://linuxwireless.org/en/users/Documentation/rfkill#Getting_rfkill](http://linuxwireless.org/en/users/Documentation/rfkill#Getting_rfkill)

You've got to download the rf-kill tool, make the rf-kill and then run something like

[FONT="Courier New"]rfkill unblock <identifier>[/FONT]

the identifier is the number in the name of the wireless card (in my case '0', wlan0)

Let me know if I was any help, good luck!

---

### Post by dontic on 2010-10-22
thank you Zapata,
problem solved, i even had the rfkill tool installed, it was not me.
and this happened after a fresh install of 10.10, before with 10.04 there was no problem 

thanks again

---

### Post by clnv2 on 2010-11-25
Same here, wlan was working fine before upgrading to 10.10.
Got it working again using rfkill.

---

### Post by Vinterbo on 2010-11-29
rfkill did the magic!

If you stop by Stockholm, Sweden; beer is on me - I do no know how many hours I tried everything after upgrading to 10.10!

---

