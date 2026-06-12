---
title: "Help with a Sabrent TVFM card"
date: 2005-12-07
forum: Hardware &amp; Laptops
---

### Post by chronusdark on 2005-12-07
has anyone been able to get this card 

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1048731&am]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1048731&am")

to work under breezy if so please tell me how

thanks in advance

---

### Post by beartard on 2006-05-04
It's a late response, but I only just got one cheap off ebay myself.  I've managed to get composite to work.  Haven't tried s-video.  I can't seem to get sound or the tuner to work, however.  I'm still tinkering with the driver.

---

### Post by lesemi on 2006-11-17
i have the same exact card.

i have it working with tvtime but no sound

here's my post:
[http://www.ubuntuforums.org/showthread.php?t=279438&highlight=sabrent](http://www.ubuntuforums.org/showthread.php?t=279438&highlight=sabrent)

if you have sound working let me know.

---

### Post by chronusdark on 2006-11-21
i couldnt get the alsa driver to work so i just had to use the line-in cable that cam with it

---

### Post by observative on 2008-01-04
I found this thread while looking for info about the Sabrent SBT-TVFM card, and if it will work on my dual-boot w2k-svr/u7.10. I also, amongst others elsewhere on the net, found this review on the tigerdirect site...

> [SIZE=2]**REVIEW BY: **[I]JoshuaJamZ Reviewed                          Sep 11, 2007 - 4/5 stars
[/I][/SIZE][FONT=Tahoma][SIZE=2]I needed a cheap Tuner that would allow me to play my Playstation 2 on my desktop. This allowed me to do just that. Great price and good performance. I am an Ubuntu Linux (Feisty Fawn 7.04) user, but also have WinXP to dual boot, so was able to test on both. For linux: modprobe saa7134 card=42 tuner=17 Once setup and running, the tuner worked great from both WinXP and Linux, but using TV-Time on Linux was a slight bit better than Win Software. There were some graphical glitches when using the included software on WinXP, that was NOT present on Linux. To sum this up, this seems like a fairly good tuner so far for the price. While it will work with Linux, I still get irritated with the Linux blind-spot that many companies have.[/SIZE][/FONT]
So I would say it's confirmed that the SBT-TVFM card will work in Ubuntu, especially the newer 7.x versions.

Edit: Here is a great install HOWTO that I found, [http://ubuntuforums.org/showthread.php?t=408654](http://ubuntuforums.org/showthread.php?t=408654)
and was quite helpful. Here is a thread, [http://ubuntuforums.org/showthread.php?t=408307](http://ubuntuforums.org/showthread.php?t=408307), that has a newb approach that follows the HOWTO guide, along with other helpful insights.

---

