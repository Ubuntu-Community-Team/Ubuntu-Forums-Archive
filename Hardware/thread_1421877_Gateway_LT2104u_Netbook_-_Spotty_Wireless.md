---
title: "Gateway LT2104u Netbook - Spotty Wireless"
date: 2010-03-04
forum: Hardware
---

### Post by PhishShticks on 2010-03-04
Hey guys! I'm running 9.10 NBR on my Gateway netbook and getting extremely spotty wireless connectivity. Sometimes, I'll get randomly disconnected, other times, I won't be able to connect at all. I have a built in Atheros Wireless-N module.

Thanks for any help in advance!

~ PHiSH

---

### Post by PhishShticks on 2010-03-07
3 days and still nothing? I know I'm not the only one having this issue...

ANY assistance would be greatly appreciated!

---

### Post by PhishShticks on 2010-03-14
SERIOUSLY?!? Nobody is going to help me? This is pathetic!

---

### Post by logan042 on 2010-03-22
i have same problem, please help

---

### Post by killerrich on 2010-03-30
I too have a Gateway LT2104u, and have the same problem. Right now, I'm dual-booting Windows7 Starter and 9.10 Netbook Remix. The wireless adapter seems to have weak signal strength compared to when it's running under the windows side (could it possibly be being under/over powered on the linux side of things?) Aside from having to be within 50 feet of an access point, which is frustrating  in itself, if I attempt to download any new, larger packages, the connection fails completely and the wireless icon in the taskbar disappears completely, and I have to reboot to get it back. If I have moderate signal strength and all I'm doing is pulling a few web-pages, then there doesn't seem to be a problem.  I ran Ubuntu on my last laptop (Dell Inspiron 1720), and had no problems whatsoever. I would like to get rid of my Windows partition on my netbook completely, but I am hesitant because of this one issue.  If any of you gurus out there have any ideas, please help.

---

### Post by killerrich on 2010-04-05
Ok, so I stumbled upon a similar issue elsewhere in the forums on an Asus netbook, and noticed that it was running an Atheros chip also. I tried these two commands that were recommended there, and it has corrected the issues with my netbook also. Here are the commands:

sudo apt-get install linux-backports-modules-karmic

sudo apt-get install linux-backports-modules-wireless-karmic-generic


I now get a heck of a lot better signal strength, and no more freezing up or disappearing wireless. I hope this helps.

---

### Post by davesnyd on 2010-04-07
I just installed Ubuntu 10.04 beta 1 on the LT2104 with no problems-- everything appears to work out of the box.

---

### Post by robinc on 2010-06-03
> **PhishShticks said:**
> SERIOUSLY?!? Nobody is going to help me? This is pathetic!


****

---

### Post by RamahX on 2010-06-10
I too have the Gateway lt2104u and lucid, constantly dropping wireless. I have googled and searched and searched for an answer to this to no avail. Help...

---

### Post by faheyd on 2010-08-07
> **RamahX said:**
> I too have the Gateway lt2104u and lucid, constantly dropping wireless. I have googled and searched and searched for an answer to this to no avail. Help...
A possible hack is to change your router to 'G' only instead of 'N'.

---

### Post by killerrich on 2010-08-07
In addition to the wireless dropping occasionally, has anyone seen strange things going on with the battery monitor gauge in the task-panel? Every once in a while, usually in conjunction with the wireless hiccup, my battery gauge will drop from full to empty, warn me, and then a few seconds later, fill back up to where it previously was. Anyone else seeing this? I think there is a kernel bug issue with this model, as I remember seeing an error referencing this once or twice after rebooting for the wireless issue several versions ago. I should have written it down...

---

### Post by sochbat on 2010-09-02
I tried changing the kernels to karmic, but no dice. Same spotty wireless.

I THOUGHT I saw that battery problem happen, but I usually keep my charger plugged in when I'm home.

Spotty Internet always happens at the wrong times. Can't I just watch my pr0n in peace?

---

### Post by killerrich on 2010-09-03
I switched back to 10.04 netbook edition, and I haven't had any problems yet...
Plus, I'm selling the netbook this week anyway.  It's either an iPad or an 11" Alienware next...

---

### Post by sochbat on 2010-09-16
Yea. So that 'battery depleted' prompt came up, but only for a few seconds. After, it went back to the normal 98%. Weird.

Anyone solve the spotty wireless? Its still happening and its always at the worst times.

---

### Post by sochbat on 2010-09-22
No new development, this sucks. Anywho, I guess I'll just install UNR. Others have stated it works out flawlessly. Here's to crossing your fingers.

---

### Post by sochbat on 2010-09-23
Dammit. UNR still does the same disconnecting wireless, just seemingly not as often? MadWifi didn't seem to work on my 10.04 desktop version either.

---

### Post by DonnieP on 2010-11-09
Sorry to be late to the game, but try switching from Network Manager to wicd.  My LT2104u won't work reliably on Windows 7 either wired or wireless.  But I get decent service on Slackware using wicd.

---

