---
title: "Audio and wireless broken after suspend (IBM ThinkPad T30 )"
date: 2009-01-18
forum: Hardware
---

### Post by ikajaste on 2009-01-18
Hi!

I'm using Ubuntu 8.10 on IBM T30 with a PC-card wireless adapter. When I've put the system on suspend and wake it up, my network connection and sound output are broken. When I unplug my WLAN PC-card and plug it back in, wireless connection works again. However to get the audio back I need to restart the computer, so I really appreciate help since I don't want to be restarting all the time!

Is there a way to fix this? Are there any handy scripts or commands I could use to make the system refind my network and audio? Can these scripts be somehow run automatically after system wakeup? (I'm pretty much a beginner when it comes to linux.)

I've tried searching for information on this, and though there seems to be a lot of stuff about suspend problems, I coudn't find any place that would clearly explain what the problem could caused by, how to figure out which is the cause in my case, and how to try fixing it. Also, I found that ThinkPad (all models) is listed on [Recommended Hardware list](https://help.ubuntu.com/community/RecommendedHardware) of community documentation. Does my experience mean that I should go edit the page and add a mention that T30 is not recommended?

[SIZE="1"]For what it's worth, here's some output from **lspci**:
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
07:00.0 Network controller: RaLink RT2561/RT61 rev B 802.11g[/SIZE]

---

### Post by huzzam on 2009-05-18
Did you ever have any luck with this? I have similar issues on my T30.

thanks
peter in oakland california

---

### Post by ikajaste on 2009-05-24
> **huzzam said:**
> Did you ever have any luck with this? I have similar issues on my T30.

Well, here's the lastest info:

I have now upgraded to Ubuntu 9.04, and the problems still remain. In fact, they are worse, since simply replugging my network pc-card doesn't do the trick, I also have to run "**sudo service NetworkManager restart**". Only running the command will *not* restore the network, I need to both run the command and replug my network card.

I also found out I can kind of restore audio by running "**sudo service alsa-utils restart**". The problem is, my audio starts to run at *silghty faster speed* after this! (To be exact, the speed is 110% compared to the original.) This of course makes it unusable for anything other than system alert sounds.


It does feel like this problem is something that could be fixed by restarting the correct services, or running some other command-line voodoo, but unfortunately this is where my skills end. I hope someone from the community could point me towards the right direction.

---

### Post by louieb on 2009-05-24
For what its worth. [IMG]http://louboldt.com/ptwocents.gif[/IMG] Sound does not worked on my T30 when resuming from hibernate or suspend  - been that way for every release I've had on it starting with 7.10 Feisty.  

PC has and Intel pro internal wireless B card - have not had any problems with it reconnecting. 

A search of   [Ubuntu Bugs]("https://bugs.launchpad.net/ubuntu") for **sound after resume**  lists a number of reports, including one for a T21.

---

