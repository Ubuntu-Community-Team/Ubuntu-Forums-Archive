---
title: "old IBM... supported?"
date: 2005-10-11
forum: Hardware &amp; Laptops
---

### Post by Elrohir on 2005-10-11
I have an old IBM ThinkPad (I mean WAAAAAY OLD laptop):

Model: 760ED
HD: 2 GB
Memory: 32 MB (I think)
Processor: ehmm... cant recall... but I believe you all got the idea of how old this laptop is... ;)

actually it has Win95 installed, but I want to install Ubuntu so I can carry my info around... are this kind of specs supported???

---

### Post by codejunkie on 2005-10-11
[quote=Elrohir]I have an old IBM ThinkPad (I mean WAAAAAY OLD laptop):

Model: 760ED
HD: 2 GB
Memory: 32 MB (I think)
Processor: ehmm... cant recall... but I believe you all got the idea of how old this laptop is... ;)

actually it has Win95 installed, but I want to install Ubuntu so I can carry my info around... are this kind of specs supported???[/quote] 
it might work fine doing a server install and then using something like fluxbox or xfce as the desktop manager. i installed xfce on a 266mhz pentium with 64mb of ram it was alright but it was no speed demon. you might also look at damn small linux it's debian based and made for systems with low resources. there also used to be a project ubuntu light or something but i haven't heard much about it these days.

---

### Post by matthew on 2005-10-11
Without knowing more we can't answer you with certainty. I think it is likely with a server install and a light desktop like xfce, but I don't know for sure without a little more info.

EDIT: someone beat me to it

---

### Post by AndrewB on 2005-10-11
I have a 760EL, the specs are a 133 pentium, 96mb ram. Personally, I found ubuntu did not run that great on this pc. After changing to Dillo browser and fluxbox, it was still clunky, but a little quicker. 

I ended up reformatting the HD and doing a frugal install of [Damn Small linux]("http://damnsmalllinux.org"). DSL is a ~50 meg OS

No matter which way you go, you'll need to manually configure your network and sound settings.

Andrew

---

### Post by Elrohir on 2005-10-11
[quote=codejunkie]it might work fine doing a server install and then using something like fluxbox or xfce as the desktop manager. i installed xfce on a 266mhz pentium with 64mb of ram it was alright but it was no speed demon. you might also look at damn small linux it's debian based and made for systems with low resources. there also used to be a project ubuntu light or something but i haven't heard much about it these days.[/quote]I dont mind it not being a speed demon... I just want it to work for office use (handling documents (homework), basically)... I'll check on DSL, have heard it (and read about it) but now it may sound interesting...

---

### Post by Elrohir on 2005-10-11
[quote=AndrewB]I have a 760EL, the specs are a 133 pentium, 96mb ram. Personally, I found ubuntu did not run that great on this pc. After changing to Dillo browser and fluxbox, it was still clunky, but a little quicker. 

I ended up reformatting the HD and doing a frugal install of [Damn Small linux]("http://damnsmalllinux.org"). DSL is a ~50 meg OS

No matter which way you go, you'll need to manually configure your network and sound settings.

Andrew[/quote]nah.. no sound nor network for IBM... just document handling... maybe some picture management, that's as far as I want the laptop to go...

---

### Post by Elrohir on 2005-10-11
ok, been thinking... if I install the base system (server) and have no network configured, how can I install xfce??

btw, CDROM is an oldie too, so max reading speed is lie 6x... not even 4x CDRW (no support)... forgot this part... :(

DSL would be perfect, if ThinkPad had usb ports...

I think I'll wait for my dad to buy his new laptop and then I'll inherit his... :p

---

### Post by AndrewB on 2005-10-11
Dsl found my wired net card fine, and dhcp'd it to my network. I had to manually configure the wireless netcard. It works great.

The 760 series notebook's have cardbus32 pcmcia support, no USB though.

---

