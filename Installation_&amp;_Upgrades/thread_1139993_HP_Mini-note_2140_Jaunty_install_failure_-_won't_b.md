---
title: "HP Mini-note 2140 Jaunty install failure - won't boot when power supply plugged in"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by chippies on 2009-04-27
Hi Guys,

I've got a really curious problem going on. I'm trying to install the Desktop version of 9.04 on my friends HP 2140 netbook (I know, but he'd like the Desktop version, not the netbook remix). 

He bought a 30GB SSD and wants to install ubuntu (and only ubuntu) on this drive. stuck the SSD in, ran the install off of a USB key, and all was going fine on the first install. My friend then pulled the key fob out prematurely, resulting in a nice text-puke on the screen and a hang.

After a few hours of messing with it, trying to low-level format the SSD in an enclosure on another machine, etc etc etc, we finally got the thing to boot up and work normally. We also noticed that it would ONLY boot if we turned the computer on when the AC cord wasn't plugged in. Now, we could boot the machine, THEN plug in the AC and it'd still work fine, it's just when we'd leave the AC plugged in that it would error out. This would happen booting from the SSD, as well as trying to boot from the 'liveUSB' that we had there for the install...

Does anyone have a clue as to what's going on here? My friend is getting distressed and contemplating going back to XP, and I don't want this to be his first and possibly only experience with Ubuntu...

---

### Post by robllewellyn on 2009-05-09
chippies

I'm a total n00b to ubuntu. I have just installed ubuntu remix on an HP2140 with the exact same situation.

Boot with power in, text puke. Boot with power out, all is well.

I havent worked out where and how to log bugs yet, so I'll work that out and post it with specs.

If you could let me know if you find anything pertaining to this I;d appreciate it.

I;ve also got poor resolution on the HP with quite a few icons being blur'd, regardless of the appearance theme settings. I did read that I needed to to use the Human theme but thats porked as well.

Do you get the same?

Other than this, seems ok tho. Same with you?

Rob

---

### Post by chippies on 2009-05-09
I probably should have posted my findings on this thread sooner, but my friend just installed 8.10 and it seems to work fine. He's been using that since I first posted the thread with next to no problems. We did have to re-map the Super key (windows key), and a few other tiny little configuration things, but nothing crazy.

One thing that might be interesting to try is installing 8.10 then upgrading to 9.04 using the update manager. I suggested this to my friend, but he didn't really want to, his computer was working and that's all he really wanted. 

If you try this method out, let me know how it works and I can report back to my buddy.

---

### Post by robllewellyn on 2009-05-11
SO the power issue has gone away.

I am dual booting Windows 7 and Ubuntu (Win7 went on AFTER Ubuntu)

Now when grub comes up I obviously get my OS load options (after some tweaking with the menu.lst)

What I have noticed now is that I can have the power plugging in all the time, and Ubuntu doesnt spew a load of text at me.

Go figure!

---

### Post by cboteros on 2009-08-20
Hello everyone,

I just bought a HP Mini 2140 yesterday and have exactly the same problem chippies is describing.

I tried with all Ubuntu Jaunty versions I have (Kubuntu, Ubuntu Desktop, Netbook Remix) and the only way I could actually install Ubuntu was with Ubuntu Jaunty Alternative version.

After it installed fully, then I restarted the mini and I was getting error messages when booting, then I just by a chance decided to take the mini with me somewhere else (so it was not plugged to the power cable anymore) and it worked just fine.

This mini has an Intel Atom processor, which I guess behaves diferently when it is connected to the power source than when it isn't.

Also I must say that I tried with other Linux Systems (Mandriva 2009.1 Spring version) and it didn't bring me any error, but I'm more fan of Ubuntu, so I kept trying.

So, so far I'm starting the mini without being plugged and after X starts I then plug the power cord and enjoy the ride.

For details on the error message check these "screen shots" (done with my digital camera ;-) )

Grub screen: [http://files.carlosbotero.webnode.com/system_preview_detail_200000003-9421c951d8-public/DSCN2353.JPG](http://files.carlosbotero.webnode.com/system_preview_detail_200000003-9421c951d8-public/DSCN2353.JPG)

Error trail: [http://files.carlosbotero.webnode.com/system_preview_detail_200000004-71b5b72afb-public/DSCN2354.JPG](http://files.carlosbotero.webnode.com/system_preview_detail_200000004-71b5b72afb-public/DSCN2354.JPG)

---

### Post by chippies on 2009-08-20
Hey cboteros,

It's been a while since I posted this thread, but my friend is STILL running 8.10 with no issues. I've tried to talk him into patch-upgrading to 9.04, but with no luck. Maybe try doing this on your notebook, I'm still curious to see if it would make any difference.

---

### Post by splinterknight on 2009-08-21
Same problem that I'm facing now~~ But any solution now?? Yours reply and help are appreciated :guitar:

---

