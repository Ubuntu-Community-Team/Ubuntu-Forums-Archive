---
title: "Brightness Changes Randomly"
date: 2008-05-25
forum: Hardware
---

### Post by aelsi on 2008-05-25
Hi there, I've been having a pretty bad problem with my brightness on my new laptop, the Asus U6e. Specifications for it are listed [HERE]("http://www.newegg.com/Product/ProductPrint.aspx?Item=N82E16834220259") if necessary. Now, since thats out of the way let me get more into my problem...

1. When starting a program like MPlayer (but not only MPlayer) the brightness will go down, without me doing anything at all. It is not dimming it, because it doesn't fade it just blinks and then gets darker.
2. To fix this I just do fn+brighter on my keyboard and it fixes the problem instantly with one click even though the brightness looks like its at a level requiring 3 or 4 click to bring it back up to max.
3. The problem happens when it is plugged in or on battery.

Alright, that just about sums it up. Thanks in advance!

---

### Post by aelsi on 2008-05-25
bump

---

### Post by trappo on 2008-05-30
the same happens to me..
asus pro60e

---

### Post by aelsi on 2008-05-30
Okay, since it seems I'm not alone, i added a ticket to the Ubuntu question thing.

[https://answers.launchpad.net/ubuntu/+question/34758](https://answers.launchpad.net/ubuntu/+question/34758)

---

### Post by aelsi on 2008-06-04
For some more info, i found out this happens in Kubuntu as well, and also only changes brightness when you open a video in MPlayer or SMplayer not when you open the program itself. Also, the brightness changes at start up, like the LED back lit display just dims by itself, this does not happen on windows.

---

### Post by rvm4000 on 2008-06-04
In smplayer, edit the file ~/.smplayer/smplayer.ini, look for dont_use_eq_options and set it to true. That should prevent to change the brightness on startup of every video.

---

### Post by aelsi on 2008-06-05
Ahhhh! That works! 

Well, thanks now the problem is mostly gone, but it still happens for some programs like ZSNES, is there any way to set it globally?

---

