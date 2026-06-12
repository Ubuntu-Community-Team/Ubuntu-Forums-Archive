---
title: "Intel AD1981HD - Volume issues"
date: 2007-02-23
forum: Hardware &amp; Laptops
---

### Post by Edowardo on 2007-02-23
This audio problem has been haunting me since I've owned the laptop back in August. After constant research I have come up empty handed. 

_My computer is the following:_
[COLOR="Red"]**IBM T60**[/COLOR]
2GHz Duo
Intel AD1981HD &#8211; HD Audio 1.0 Controller w/ latest ALSA and ESD.
Fully updated Ubuntu Edgy 6.10

The sound card has been an extreme pain. I DO have audio, but there are two problems with it.


[INDENT]1.) Max volume in ALSA makes my audio crackle and I fear it will blow the speakers. ALSA is set to 71% from max to stay safe... 
	[INDENT][I]- I what to fix that code wise, so 100% is actually 100% at a safe and reasonable setting that IBM intended.
[/I][/INDENT]


2.)My volume range, from silent to loudest, is around 55% to 100% on the adjustment bar. ESD has no effect on fixing this since it's merely a software volume controller, ie. GUI. 
	[INDENT][I]- I would like to use the entire volume bar for more accurate volume control, since the jumps in volume are big change.
[/I][/INDENT][/INDENT]


I have been all over google, forums, and on ThinkWiki. The closest I've heard to my problem is the crackle sound of max volume. Being that if you [COLOR="Blue"]&#8220;position_fix=2&#8221;[/COLOR] somewhere in the code, which I don't know how, should solve the max volume problem. Unfortunately I've heard this is a quick fix and is not that good.

---

### Post by Edowardo on 2007-02-24
A little bump, before this post disappears.

---

### Post by Edowardo on 2007-02-28
bump again... for hope.

---

### Post by vkkim on 2007-03-08
I too had similar issues on my X60s (same sound card) until my sound completely died (I'm still trying to figure out why).  I have no idea how to fix it, but you'd think that there would be more documentation about it.

---

### Post by toomin86 on 2007-05-22
I'll vouch my support for this, same problem, same laptop, had the problem on both Edgy 6.10 and Feisty 7.04.  Haven't the foggiest how to fix this.  anyone out there with any help or advice?

---

### Post by AndersMynster on 2008-03-26
Same here, has anyone found just a hint for a solution?

Just found it in

[http://ubuntuforums.org/showthread.php?t=496180&highlight=ALSA+audio+volume]("http://ubuntuforums.org/showthread.php?t=496180&highlight=ALSA+audio+volume")

---

