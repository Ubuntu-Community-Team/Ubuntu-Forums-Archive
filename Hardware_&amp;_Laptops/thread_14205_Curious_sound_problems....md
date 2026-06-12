---
title: "Curious sound problems..."
date: 2005-02-05
forum: Hardware &amp; Laptops
---

### Post by skeporang on 2005-02-05
Well my first post, so i'll say a quick hi. I'm a student at University of Portsmouth in the UK and have got so fed up with Windows XP lately I deleted everything and split my 40gb hard drive down the middle. I've played with linux before but nothing really caught my eye. I installed about four or five (none played nicely with me.. no sound, internet etc.) so I decided to try this new distro I heard of. And I loved it   8-) . As I said on another forum... "Never have I had such an orgasmic experience with an OS". This is one operating system that will be staying on my hard drive. Sound, internet, USB printing and scanning, USB mass storage all worked on its first day.

Now down to why i'm posting in this forum...

It started off with problems getting sound with my Leadtek Winfast DV2000 TV card. I had perfect picture, but as pretty as it was without sound...  I tried a different (Creative PCI 64) sound card, but no luck with the tv, just scratchy sound, so I gave up and whipped it out and replaced the jacks in the on board sound card, which had previously worked fine whilst playing oggs etc.

However nothing came out.  I checked all the connections, rebooted, tried Windows XP. Absolutely nothing came out. I then accidentally plugged the speaker cable into the line **IN** socket. And I heard music. So now I have sound (except TV - ?known problem with the drivers) coming out of my line in socket in Ubuntu; but this is the odd thing, absolutely nothing out of any socket from within XP.

Umm.

I double, triple checked. Sound still comes out of my line in. Is there anyway I; ubuntu; windows; my motherboard could have caused this? I'm thinking I might have plugged the mic into the speaker socket, but would this then cause sound to come out of the line in? I could understand it if no sound came out (as i windows) or is ubuntu just being really clever :lol: ?

Of course if the TV drivers do ever get soughted out sound wise, I currently have nowhere to plug the sound cable in, as it goes in the line in socket...

Specs:

AMD Athlon 64 3000+
ABIT KV8 Pro
512MB RAM
ATI Radeon 9550
Realtek AC'97 Audio for VIA (Standard mic, line in, line out as well as rear and center out)

Is my on board sound *ruined*? I've just found another PCI sound card, Yamaha something, so I will try that. TBH i'm not really bothered if my on board sound is broke, just rather annoyed :evil: considering the price...

Sorry for the long post, and keep up the good work  =D>

---

### Post by macewan on 2005-02-05
sudo setpci -v -s *:* latency_timer=40

as is may or maynot help

---

