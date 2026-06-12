---
title: "Nvidia Nforce 780i chipset"
date: 2008-01-22
forum: Hardware &amp; Laptops
---

### Post by s1k on 2008-01-22
Hi

Does anyone have experience with this chipset working or not on a linux platform? Unfortunaly I have not been able to find any comments on this anywhere.

Sincerely,
Christian Danielsson

---

### Post by Jaak on 2008-01-22
That is something i like to know!?

Planning to buy:
[IMG]http://www.documentje.nl/uploads/system.jpg[/IMG]

---

### Post by Jaak on 2008-02-12
Anyone with experience by now?

---

### Post by Gestalt73 on 2008-02-13
The short answer is yes, the 780i chipset does work in linux, at least with Gutsy 7.10.  I'm running the EVGA version of the board right now.   

Unfortunately, the longer answer is that you would always need to check if all components are actually supported.  The other chips you'll really want to check out are how the board handles sound and network.  I just happened to luck out and whatever chips are used for both on the evga board are supported in 7.10.  According to other forums the evga board is the way to go for 780i right now, although I wouldn't bother with tri-sli -- its a gimmick.  I haven't had a chance to try out sli yet, my other card should be coming in next week.  

So, I can say authoritatively that if you buy the evga 780i board, that the chipset is supported, sound and network works.

If you're looking at other boards, just make sure the sound and network chips are supported and you should be alright.

As usual, don't worry about "hardware raid" support, just use mdadm.  If you're dual booting, there is a program out there that actually lets you mount linux raid volumes in windows, I don't remember what it was off the top of my head.

Have fun!

Alan

---

### Post by GrokIt on 2008-04-28
I've also got an EVGA 780i motherboard along with an intel E6850 cpu and an 8800 GTS video card.  Everything works pretty damn well in 7.10, but not at first.  You will probably have to manually install the video drivers.  I got no gui at all at first and had to search the forums for what to do.  It's pretty easy once you take the plunge.  See [http://ubuntuforums.org/showthread.php?t=726480]("http://ubuntuforums.org/showthread.php?t=726480") or [http://ubuntuforums.org/showthread.php?t=281823]("http://ubuntuforums.org/showthread.php?t=281823")
Right now I'm having some major problems after I upgraded to 8.04 so I do not suggest you do the same.  I don't know how a fresh install will work, but the way things are (not) going here, I may be able to tell you.

UPDATE: Since I am not too sure what to do, too new to the linux world, I made more problems for myself than I had to.  I did a fresh install of Kubuntu, used envy and it worked well.  Not quite painless, but not bad at all.  It seems that the new version of envy for 8.04 works a lot better, at least for me and this hardware.  I've gone through 3 kernel upgrades with no problems at all.

---

