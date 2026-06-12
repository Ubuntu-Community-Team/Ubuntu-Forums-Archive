---
title: "enable Nvidia sli on ubuntu 10.04"
date: 2010-08-01
forum: Hardware
---

### Post by Rody on 2010-08-01
ok enabling SLI was pretty easy.

sudo nvidia-xconfig --sli=AFR

reboot

everything seems to be fine until i start a game then it flashes at me I can play the game but it is like it is dropping lots of frames. SLI works just fine in windows so I am fairly sure that i don't have a problem with my vid card.

I think there must be some other command or switch that I am missing and so few people run sli much less sli and linux that getting good info is kind of hard.

any help would be appreciated.

rody

---

### Post by Rody on 2010-08-01
ok after playing with some more settings, I found that if I uncheck the allow flipping option in the opengl settings in the nvidia control panel that the blinking goes away, but the performance is very bad, with lots of stutering.

I relize that one gtx480 is more that enough to play most games that are avalable in linux and all I am really trying to play atm is World of warcraft, but I think one of my favorite games is can I make it work on linux. :) so I will play with more settings and see.

rody

new drivers 256.44 [http://www.nvnews.net/vbulletin/showthread.php?t=153575](http://www.nvnews.net/vbulletin/showthread.php?t=153575) seem to fix most issues, still have to uncheck allow flipping and it seems to work great, I also turned on vsync which seems to have smoothed things out even more.

---

