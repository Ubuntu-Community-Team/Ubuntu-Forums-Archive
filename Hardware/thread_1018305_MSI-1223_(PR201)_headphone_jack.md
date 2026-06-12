---
title: "MSI-1223 (PR201) headphone jack"
date: 2008-12-22
forum: Hardware
---

### Post by xjgnsdof on 2008-12-22
I have the MSI-1223 (PR201) whitebook: [http://global.msi.com.tw/index.php?func=downloaddetail&type=driver&maincat_no=135&prod_no=1545](http://global.msi.com.tw/index.php?func=downloaddetail&type=driver&maincat_no=135&prod_no=1545)

I hear sound through the headphone jack and speakers when I have headphones plugged in. Does anyone know how to work around this?

---

### Post by xjgnsdof on 2008-12-30
up

---

### Post by xjgnsdof on 2009-01-04
up

---

### Post by Griz054 on 2009-03-16
I have same issue with my MS-1223 with Jaunty Alpha. 

Speakers are really too weak to use for much and when you plug in headphones, the speakers still put out audio. Any workaround would be great.

---

### Post by jonny2040 on 2009-04-19
Hi,

I also have this laptop. I am running Jaunty beta and have been able to get the headphone socket working slightly by following the advice found here -

[http://ubuntuforums.org/showthread.php?t=806620&highlight=alc888+headphone](http://ubuntuforums.org/showthread.php?t=806620&highlight=alc888+headphone)

The model I ended up going for was - medion

making the whole line -

options snd-hda-intel model=medion

which you want to add to your alsabase.conf file.

I have found that using this option gives you a switch in the volume control gui called headphone. When its ticked volume comes out of speakers and headphones. Unticked it just comes out of headphones. Obviously this is not ideal but its enough to ease some of the troubles. Also I don't have a problem with the volume. The speakers on this laptop are pretty poor but the Jaunty beta has better Alsa drivers I think so the volume is now comparable to windows. 

Finally I might send some info to Alsa to try get this laptops soundcard working better but I can't say for sure if I'll get round to it.

Hope this helps,
Jonny

---

