---
title: "Need diagnostics for a tune up"
date: 2006-09-23
forum: Hardware &amp; Laptops
---

### Post by Langstracht on 2006-09-23
I am a recent convert to Ubuntu, running it (and only it - no dual boot or partitions) on a Toshiba Satellite A60 with a 2.8 Gig cpu and 768 Meg RAM.

I expected that it would fly. Alas that has not been the case. Indeed I am rather disappointed by what I've been experiencing.  For instance booting up Open Office takes 22 seconds!

However, this could be because my expectations are unjustified.

Can anyone recommend software which would rate my machines performance and, hopefully, indicate where any settings could be improved.

Thanks in advance.

---

### Post by xyz on 2006-09-23
Tune OO:
[http://ubuntuforums.org/archive/index.php/t-9925.html](http://ubuntuforums.org/archive/index.php/t-9925.html)
Disable IPV6:
[http://ubuntuforums.org/showthread.php?t=87798](http://ubuntuforums.org/showthread.php?t=87798)
Also in Fierefox, look for network.ipv...something and set it to "true".
Type about:config to get there.

Try that for a start and let un know.

---

### Post by Langstracht on 2006-09-23
First, thanks so much for getting back to me.

Made the OOo changes.  Start up gone down to 7 seconds from 22.  Not fabulous.  But much better.  Thanks for that.

I wasn't really having any issues with Firefox but I made the change anyway.  Hadn't measured it before or after but it might just be a bit faster ...

As for ipv6, the first command (alias net-pf-10 ipv6 off)results in ...

      bash: alias: net-pf-10: not found
      bash: alias: ipv6: not found
      bash: alias: off: not found

Oh that I was bright enough to know what that meant.  In any event, it (the command) didn't work.

Appreciate a nudge in the right direction.  And, thanks again!

---

### Post by xyz on 2006-09-23
How about this! It should clear things up a bit:
[http://www.ubuntuforums.org/showthread.php?t=202838](http://www.ubuntuforums.org/showthread.php?t=202838)

Do you absolutely need OO? If not, try Abiword.

I need to leave the house now; I'll catch up with you later.
Let me know...

---

### Post by Langstracht on 2006-09-23
O.k. I successfully changed the file, saved and re-booted.  But I can't say I detect any difference.  I have high speed so maybe the changes are only more noticeable on dial up.  ???

As for OOo, I was actually only using it as a speed example that I thought others would be able to compare to.  While I thought it was slow I kinda like the way it works, so I really wasn't looking to change to something else.

---

### Post by xyz on 2006-09-24
Well, I don't how fast you expect it to fly. To each his/her own perception of it, I guess. I use a Toshiba Satellite A 40 - 2.8 - 512 RAM and I find it quite "flying!".
If you want more, check these out:
[ Tweak your ext3 filesystem for a performance boost]("http://www.ubuntuforums.org/showthread.php?t=107856&highlight=tuning")
[Speed up ubuntu boot process - the way you can feel it. - updated]("http://www.ubuntuforums.org/showthread.php?t=89491&highlight=tuning")
Also did turn DMA on?

---

### Post by Langstracht on 2006-09-24
Thanks once again for continuing this thread.

As for the links, I can see I have lots to do.  I'll pick away at it and see where it goes.

As for DMA, I had that problem (no DMA) on a PC.  Sorry to say I have no idea how to check for it and/or toggle it in Linux.  Perhaps you'd be kind enough to nudge me yet again.

Thanks so much!

---

### Post by xyz on 2006-09-24
Hey Langstracht, no problem for the help! I get help, too...so...
I also tried the 2nd link I gave you but it's tricky! I often got my box to no good! So be careful and don't disable too many things at once...like I did! Then I could not remember which ones I disabled so as to turn them back on in order to simply boot again!!

About DMA, do the following:
```
th@luser:~$ sudo hdparm -d1 -c1 /dev/hdc
Password:

/dev/hdc:
 setting 32-bit IO_support flag to 1
 setting using_dma to 1 (on)
 IO_support   =  1 (32-bit)
 using_dma    =  1 (on)
th@luser:~$ sudo hdparm -d1 -c1 /dev/hda

/dev/hda:
 setting 32-bit IO_support flag to 1
 setting using_dma to 1 (on)
 IO_support   =  1 (32-bit)
 using_dma    =  1 (on)

```
You'll have guessed that this is how it should look!

so this command: sudo hdparm -d1 -c1 /dev/hdc is for your CD-ROM
that one for your HD: sudo hdparm -d1 -c1 /dev/hda

Let me know how it goes...

---

### Post by Langstracht on 2006-09-24
Did the DMA thing and, sorry to say both are turned on.  Pity!  It would have made a great improvement had it not been so,

As for the others, thanks for the info.  I'll let you know how I get on.

All the best.

---

### Post by tagra123 on 2006-09-24
Swiftfox is firefox custom compiled for the 386, 686, AMD, etc... The speed is improvement is noticeable. It is much faster then the regular firefox.

For OpenOffice I read an article about preloading, but the startup time for it didn't bother mee enough to mess with this.

---

### Post by xyz on 2006-09-24
[Desktop Optimization]("http://gnomefiles.org/app.php?soft_id=1397")
Desktop Optimization contains:
rhythmbox-quickstart
evolution-optimize
gnome-optimize
openoffice-optimize
doc-optimize
gconf-optimize
If you decide to go for it, let me know how it goes!

[Prelinking Guide- Make Ubuntu Feel Faster]("http://ubuntuforums.org/showthread.php?t=74197")

---

