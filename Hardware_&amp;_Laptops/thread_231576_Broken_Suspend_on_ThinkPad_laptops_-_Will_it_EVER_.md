---
title: "Broken Suspend on ThinkPad laptops - Will it EVER be fixed?"
date: 2006-08-07
forum: Hardware &amp; Laptops
---

### Post by Nathaniel on 2006-08-07
I know there are lots of thread about this, but since no one has an answer and nothing is being done about it, here's another.

I've been struggling with the suspend2ram feature forever it seems. It just won't work. Suspend worked perfectly on my ThinkPad T43 (with Intel graphics, not ATi) when running breezy, but was completely and horribly broken on Dapper. It WAS running for a little while in Kubuntu, but going from kernel 2.6.15-23 to 2.6.15-25 (and later 26) seems to have broken it again. It doesn't matter if I reboot and use the old kernel, it's still broken.

Now come on... Something that works perfectly in Breezy but not in Dapper? Works sometimes on some kernels, and not others? Doesn't work on a pure Intel platform, with no weird or exotic hardware whatsoever?

Seriously...

I work in a major swedish university, with well over 5000 students on campus, and quite a large IT departement. Lots of those working there use ThinkPad T-series laptops. Dapper is supposed to be the big enterprise release. My point is that for being such a overhyped release, it doesn't even work on one of the most linux friendly laptops on earth?

If ANYONE could point me to a fix for this, I'd be forever grateful.

ps.
Another mystery is how a standard Debian Etch install with NO customization at all, is way cooler than the same laptop running any version of Ubuntu. It's not even close, with Debian it's barely even breaking a sweat... Again, if anyone has an explanation/fix for this, I'll be forever in your debt :)

---

### Post by BoomAM on 2006-08-07
> **Nathaniel said:**
> 
Another mystery is how a standard Debian Etch install with NO customization at all, is way cooler than the same laptop running any version of Ubuntu. It's not even close, with Debian it's barely even breaking a sweat... Again, if anyone has an explanation/fix for this, I'll be forever in your debt :)
Never heard of that.
What do you mean it doesnt break a sweat? 
Runs cooler? Less memory usage? Less CPU usage?

---

### Post by Nathaniel on 2006-08-07
Yes, I mean it's running way cooler on Debian than on Ubuntu. Naturally it uses less memory, since I'm not even running X (but even when I do, using fluxbox, it barely changes). And less CPU usage is a given, with all the bloat running needlessly on Ubuntu.

Also suspend (s2ram) is several times faster (and works flawlessly) than it is in ubuntu, when running X and having things like Firefox and aterm open.

It just seems to me, that even though Ubuntu is based off of Debian, they've neglected to import the stability and speed of it. Ubuntu is a more complete desktop out-of-the-box, but that's all.

---

### Post by BoomAM on 2006-08-07
> **Nathaniel said:**
> Yes, I mean it's running way cooler on Debian than on Ubuntu. Naturally it uses less memory, since I'm not even running X (but even when I do, using fluxbox, it barely changes). And less CPU usage is a given, with all the bloat running needlessly on Ubuntu.

Also suspend (s2ram) is several times faster (and works flawlessly) than it is in ubuntu, when running X and having things like Firefox and aterm open.

It just seems to me, that even though Ubuntu is based off of Debian, they've neglected to import the stability and speed of it. Ubuntu is a more complete desktop out-of-the-box, but that's all.
Dont take it the wrong way, but have you come on here to ask a question or to rant? Because it seems like the latter?
Prehaps Ubuntu is more 'bloated' because it does 'just work', where as Debian doesnt? Theres a multitude of reasons why it could be classed as bloated, but i suppose you'll have to wait for others to comment, as im far from a Linux expert. :p

---

### Post by Nathaniel on 2006-08-08
Yes, my frustration has caused me to rant a little, that was unintended.

My point for coming here is stated clearly in the very first line of my original post. I want to either know WHY suspend won't work for, seemingly, anyone with any kind of ThinkPad laptop and how to fix it, or make someone in the Ubuntu team acknowledge this as a problem and tell me they're looking into it.

Several forum posts and more bug filings than I could ever link to are already out there, to no avail. This is just my attempt to get something done.

The comparison between debian and ubuntu is just that, a comparison. Why base Ubuntu on Debian, if all they're gonna do is make it less stable and worse, but look prettier?

---

### Post by hil on 2006-08-08
I am using thinkpad t30. My kubuntu 5.10 could not suspend. I had to install software suspend to sleep or hibernate the laptop. I installed dapper. The suspend/sleep function works without additional software installation. Perhaps, you are using a new laptop? You could try [software suspend]("http://www.suspend2.net/") [-o<  Hope that works for you

---

### Post by Nathaniel on 2006-08-08
Thanks for the tip, I'll look into it.

The thing is, suspend DID work using acpi without any additional software, and I'm curious as to why it won't work anymore. There has to be something that's changed somewhere along the line.

---

### Post by shizow on 2006-08-09
there were problems with the 2.6.15-25 kernel with thinkpads, but then it did work, but since some recent update maybe the kernel update from 26-45 to 26-46 did break my suspend again, i have a T43.
the laptop goes to suspend, but then it doesnt really wake up, the suspend light(the moon) blinking

Update:
it seems that my problem is the fglrx 8.27.10 drivers, when using the radeon ati drivers, my suspend works
any suggestions?

---

### Post by Nathaniel on 2006-08-09
I've fixed it, atleast for the intel chipset on T43's.

It seems the pcmcia modules were causing the crashes on suspend wake-up, so I found out which ones and blacklisted them. I now have fully functioning suspend in both 2.6.15-23 and 26 (haven't tried 25).

The modules I added to /etc/modprobe.d/blacklist are:
> rsrc_nonstatic
yenta_socket
pcmcia
pcmcia_core
sony_acpi

sony_acpi doesn't really have anything to do with it, as far as I can tell. I do, however, question it's relevance on an IBM laptop :D

---

### Post by yurtboy on 2006-10-31
Worked for me but no more pcmcia?
Seems extreme

---

### Post by Nathaniel on 2006-11-10
Seems I was mistaken, suspending is not fixed. I just can't figure out what the heck is wrong, and why it won't work out of the box.

And about the pcmcia, I never ever use it anyway. Everything I need is integrated, so the PCMCIA is just wasting resources.

So... Does ANYONE have any tips on how to get i810-based thinkpad T43 to resume properly in Dapper? Or do you know if it works ootb in Edgy?

---

