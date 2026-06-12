---
title: "Two final remaining problems with Ubuntu"
date: 2008-11-26
forum: General Help
---

### Post by Duranxl on 2008-11-26
Hi.

I've always been a windows users but have been using ubuntu for some months now.
I've got to the point where i like it a lot more than windows, however i still these 2 problems that REALLY annoy me...it almost makes me go back to windows.

I hope someone can help me out on these problems

1) 
Hibernation takes VERY long. It takes just as long as shutting down/booting my PC..so there's almost no point. In windows hibernation will take 10seconds..
Even with 2GBs of ram fully used (after gaming etc) windows will hibernate substantially faster than ubuntu....:confused:

2) 
I still get the 'grey box' issue with flash..no matter what i try. What happens is that the box will be grey instead of actually playing the video.. Restarting firefox will fix it..but it's very very annoying.

Thanks:]

---

### Post by ohzopants on 2008-11-26
My laptop hibernates fairly quickly, so it might be a settings issue for you (what those settings are exactly, I have no idea. I sort of lucked out with that working so well).

What version of flash are you using?  I recently upgraded to Flash 10 and I find it to be much better (faster, more stable...) than 9.  You should give it a shot.

---

### Post by Duranxl on 2008-11-26
Settings? what settings?

And i'm using Flash 10

Specs:
Vostro 1500
Core2duo T7300
8600M GT 180.08
2GBs of ram
Intrepid 8.10

---

### Post by Duranxl on 2008-11-27
bump

---

### Post by Ralph Falkenburg on 2008-11-27
I also have at least 2 problems with Ubuntu.  Real Audio for one.  And windsze movie player for another, and printer drivers for the last one.

Maybe a lotta Ubuntu users don't like Real Audio, that's ok with me but I have several instructional DVDs that won't work with out it.  And I have a tv with a DVD player but it is of no use for that.
And what about Woodsongs?   They have great archives for music lovers but Ubuntu won't play them.  Or I can't get it to.

And I have 2 printers collecting dust because of no Ubuntu compatible drivers.

Ralph

---

### Post by Duranxl on 2008-11-27
> **Ralph Falkenburg said:**
> balbalbla

Ralph

would you not steal my thread..?

---

### Post by ohzopants on 2008-11-28
I just assumed you were trying to get hibernation to work on a laptop.  Never mind.

Sorry I couldn't be of more help.

---

### Post by Duranxl on 2008-11-28
> **ohzopants said:**
> I just assumed you were trying to get hibernation to work on a laptop.  Never mind.

Sorry I couldn't be of more help.

Hibernation never worked for me on hardy, i had to use s2disk for it to work.
However when i updated to intrepid it worked right away..
Still takes way too long though

---

### Post by soro2005 on 2008-11-28
The grey application windows normally just mean that the application is hanging a little, for whatever reason. Normally, they come back if you wait a few seconds. Others, of course, don't come back.

Hibernation takes it's time. It has to write the entire memory to disk, and verify it's done right. Suspend is getting quicker and quicker, though.

If you want to see whether there's something wrong with your flash, you could start by running "top" in a terminal while flash hangs and observe whether there's anything that's behaving weird.

---

### Post by Duranxl on 2008-11-28
> **soro2005 said:**
> The grey application windows normally just mean that the application is hanging a little, for whatever reason. Normally, they come back if you wait a few seconds. Others, of course, don't come back.

Hibernation takes it's time. It has to write the entire memory to disk, and verify it's done right. Suspend is getting quicker and quicker, though.

If you want to see whether there's something wrong with your flash, you could start by running "top" in a terminal while flash hangs and observe whether there's anything that's behaving weird.

Hi, thanks for your reply
I'm not talking about the grey-application hanging thing..but the flashbox itself turns grey (i know more people with this bug). It will just not load flash..can't right click on the box either etc..

About hibernation, then home come windows can do it ~5x faster (seriously, it hibernates in <10s)..when windows 'sucks'?;p

i'll try the top thing once it gets stuck again (shouldnt be too long xD)

---

### Post by ECPCLINUX on 2008-11-28
Hello, I also get the grey box in flashbox. I have been unable to find the answer myself. Instead of restarting FF I reload the page. Usually within one reload the video starts right up. Just thought it would be better to reload the page than restart FF. As for Hibernation, I also had the problem in Hardy x64 (as mentioned), but in Intrepid Ibex It works well. Sorry I have not been of more help. While searching for the fix, maybe you can reload FF like me.

---

### Post by Duranxl on 2008-11-28
> **ECPCLINUX said:**
> Hello, I also get the grey box in flashbox. I have been unable to find the answer myself. Instead of restarting FF I reload the page. Usually within one reload the video starts right up. Just thought it would be better to reload the page than restart FF. As for Hibernation, I also had the problem in Hardy x64 (as mentioned), but in Intrepid Ibex It works well. Sorry I have not been of more help. While searching for the fix, maybe you can reload FF like me.
Reloading the page fixes the problem only 1/20 times..usually a restart is required:(

---

### Post by impact on 2008-11-28
I used the Flasblock Firefox extension for this very reason (grey square instead of Flash video), but now with the 64-bit Flash, videos seems to work fine.

---

### Post by Duranxl on 2008-11-28
> **impact said:**
> I used the Flasblock Firefox extension for this very reason (grey square instead of Flash video), but now with the 64-bit Flash, videos seems to work fine.

I have flashblock..doesnt change a thing tho
64bit? i guess i have 64bit flash by installing ndiswrapper right?

---

### Post by tattrat on 2008-11-28
For the flash problem, have you tried following the detailed instructions in this thread? 

[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

 It worked for me.

As for hibernate, I can't get that to work at all.:confused:

---

### Post by soro2005 on 2008-11-28
> **Duranxl said:**
> I have flashblock..doesnt change a thing tho
64bit? i guess i have 64bit flash by installing ndiswrapper right?

There is now a 64bit version at Adobe Labs. [Read here](http://blogs.adobe.com/penguin.swf/2008/11/now_supporting_16_exabytes.html). It is Alpha, but it's looking good here. You have to make sure you're getting rid of flashplugin-nonfree and all residues you may have of former installations of flash (and which may be responsible for graying out your flash windows). After you've uninstalled, perhaps also the nspluginwrapper package, go through all /usr/lib/mozilla/plugins, /usr/lib/firefox/plugins and similar directories and make sure there's nothing with libflashplayer.so left. Then, you can download the tarball at the Labs website, untar it, and drop the libflashplayer.so into /usr/lib/mozilla/plugins

Perhaps it helps.

---

### Post by Duranxl on 2008-11-29
@ soro, thanks..i removed the files and installed 64-bit flash from the site.
Lets wait and see:)

---

### Post by Growbag on 2008-11-29
Hibernation works well under Windows because Microsoft demand that all the drivers that the hardware manufacturers produce are given to Microsoft "technicians" to analyse and make Windows work with them.

Linux has no such easy life, most drivers are written by "hackers" who put a lot of their time and effort into reverse engineering a driver in order to give you something for nothing.

Linux is NOT Windows, and is NOT a replacement for Windows.

If a Microsoft operating system suits your needs better, then it might be a wise move to go simply buy one and use that.

Cost of Windows operating system: circa $US 180
Cost of Linux operating system:  circa  $US 0

At least you have a choice :).

---

### Post by Duranxl on 2008-11-30
Well, fingers crossed but the problem hasn't returned yet..:)
thanks soro 2005:d

---

