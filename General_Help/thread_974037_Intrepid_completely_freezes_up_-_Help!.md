---
title: "Intrepid completely freezes up - Help!"
date: 2008-11-07
forum: General Help
---

### Post by BigSilly on 2008-11-07
I don't know what's happened. It's been fine since the fresh install last week, but suddenly I'm experiencing these complete freezes of the OS. Nothing responds - I've tried resetting the X server with ctrl-alt-backspace, and also alt-printscreen-REISUB, but nothing other than a hard reset will do. The mouse freezes, the keyboard won't respond, and my little system monitor applet on the panel also freezes. It's quite alarming and I've never seen an Ubuntu do it before.

I have a fairly basic desktop PC connected to the net via ethernet. It's an AMD Sempron 2200+, with 768Mb RAM and a Geforce 6200 256Mb. All I was doing, on the two occasions this happened, was simply browsing the internet. Nothing more.

The only thing I can think of, is that I've recently been given a pretty old Acer flatscreen TFT to replace my old CRT with. As it's the same resolution as my CRT (1024x768), I just swapped them over and everything seemed OK till this. Can this be related? Have I forgot to do something?

Thanks in advance.

---

### Post by josephellengar on 2008-11-07
Yeah.  Intrepid does this.  It has to do with something from java.  It happens with all the browsers and is one reason why I am considering going back to hardy.  I just really don't want to reconfigure the whole system.  Anyway, I have found that epiphany and Konqueror don't do it as much and that disabling plugins and addons doesn't help at all.  To confirm that this is this problem, is your caps lock light blinking when this happens?  That would indicate a kernel panic.  I know there are some threads about this on this forum, but couldn't find them.  Good luck!

---

### Post by BigSilly on 2008-11-07
Thanks for your reply. Is it a known issue then? There might be a fix incoming if so. If anyone can point me to a fix that will do in the meantime I'd be most grateful. I've done a forum search for this issue, but couldn't find anything related. Thanks again.

---

### Post by dabl on 2008-11-07
> **BigSilly said:**
> 

and also alt-printscreen-REISUB

Next time it happens, try it with Ctrl-Alt-SysRq (aka PrntScrn) RSEIUB

;-)

---

### Post by BigSilly on 2008-11-07
Right, very bizarre. 

I dual boot Ubuntu Intrepid with Linux Mint 5 KDE, and was using Mint when I just posted my reply. No sooner had I posted it than that also froze in the same way and I had to do a hard reset. What are the odds of Mint freezing up just like Intrepid? I used Hardy (which is what Mint 5 is based on), for months and it was absolutely great. 

I think something may be wrong with my hardware, but I'm completely at a loss as to what it could be that would make a Linux freeze in this way. Just for your information, I don't get blinking lights on the keyboard, so does that mean it's probably not a kernel panic?

Does anyone have any ideas? Thanks.

---

### Post by BigSilly on 2008-11-07
> **dabl said:**
> Next time it happens, try it with Ctrl-Alt-SysRq (aka PrntScrn) RSEIUB

;-)

Already said I had in my first post. It didn't respond to it.

---

### Post by josephellengar on 2008-11-07
> **BigSilly said:**
> Thanks for your reply. Is it a known issue then? There might be a fix incoming if so. If anyone can point me to a fix that will do in the meantime I'd be most grateful. I've done a forum search for this issue, but couldn't find anything related. Thanks again.

It's well known among the community, but I don't know when a fix is coming.  Anyway, you're not the only person to have it.  The best that I have found is to use konqueror and epiphany.  They seem to have a lot less trouble than some of the other browsers, especially firefox.  I have a thread going on how to 'downgrade' to hardy- if you want to try that.  It's here: [http://ubuntuforums.org/showthread.php?p=6121594#post6121594](http://ubuntuforums.org/showthread.php?p=6121594#post6121594)
but it doesn't look very safe.

---

### Post by dabl on 2008-11-07
While it is running, you can open a console and run ```
top
``` and then put that window down in the corner of your screen and start your browser.  Then, when it has "frozen" you can look at the top window and see which process is hogging all the resources.

---

### Post by BigSilly on 2008-11-07
> **dabl said:**
> While it is running, you can open a console and run ```
top
``` and then put that window down in the corner of your screen and start your browser.  Then, when it has "frozen" you can look at the top window and see which process is hogging all the resources.

Thanks very much for that. I'll be trying that for a while.

I can't help but feel it's something to do with this new monitor. I've unplugged it all and put it back together again, and set the refresh rate to the recommended 60hz rather than the 75hz I'd been using. I'm hoping this fixes it. I'm certain it's not a Linux/Ubuntu issue, and I'm convinced it's a hardware thing now. Ibex had been fine since launch day. Why mess up all of a sudden?

Fingers crossed anyway. :)

---

### Post by BigSilly on 2008-11-07
Well, my change of refresh rate made no difference. It still froze up on me a minute ago. So, frustrated, I've now plugged in the old monitor to see if I get the same problem with that. Could it be anything to do with a faulty lead? The lead that comes with the newer TFT doesn't seem to screw in altogether.

I'm clutching at straws with this aren't I? :biggrin:  Oh well, at least it's eliminating things from the list...

---

### Post by sea_monkey987 on 2008-11-07
when your system freezes up, is your hard drive making a lot of sound?  it happens to me sometimes and the reason is i run out of ram.  also, try running your system with out compiz (go into system -> preferences -> appearance.  go into visual effects tab and select 'none')

---

### Post by BigSilly on 2008-11-07
No, it's not. I especially noted the last time it happened. There was no hard drive activity at all. No noises from the drive, and no flashing drive activity light. Nothing. Plus, I don't use Compiz either. I think it's installed, but I don't use the Compiz 3D effects at all.

I'm utterly dumbfounded, and can only really point at the monitor I recently plugged in. Still though, how can that cause a Linux freeze in this way? Is that even possible?

Using the old CRT now, and so far no freeze up. I'll stick with it for a day or two, then change between them to see if that really is the issue here.

---

### Post by Okuryo on 2008-11-09
I experience this problem as well.

I have Intrepid on three computers, all upgraded from Hardy, and it only happens on one of them. I haven't made any hardware changes for a while, long before I upgraded.
So far, I think it only happened when I was using Firefox. The screen just freezes, nothing helps except for a reset, and the hard disk doesn't sound especially active.
I ran a memtest86+ and it didn't find any errors.

If I don't find a fix in the next few days, I think I'll do a clean install of Hardy again.

---

### Post by Okuryo on 2008-11-11
Alright, I figured out what caused the problem - I installed a wireless network card in my computer, and Network Manager was consuming the CPU's work, eventually freezing Ubuntu.
I got the card out, and it's fine again. I guess I'll do with my wired network.

---

### Post by Squonk07 on 2008-11-11
> **BigSilly said:**
> No, it's not. I especially noted the last time it happened. There was no hard drive activity at all. No noises from the drive, and no flashing drive activity light. Nothing. Plus, I don't use Compiz either. I think it's installed, but I don't use the Compiz 3D effects at all.

I'm utterly dumbfounded, and can only really point at the monitor I recently plugged in. Still though, how can that cause a Linux freeze in this way? Is that even possible?

Using the old CRT now, and so far no freeze up. I'll stick with it for a day or two, then change between them to see if that really is the issue here.

I am having the same problem as you.  I'm on a two year-old Toshiba laptop (Intel GM945 express chipset) and noticed this problem for the first time last week on a clean install of Intrepid.  I've been testing Intrepid since Alpha 3 and I've never seen this problem until now.

For the first week, I had no trouble whatsoever.  Then Intrepid started freezing at random times last week.  And, oddly enough, at first I got the blinking Caps Lock kernel panic light each time the OS froze.  The last few times, however, I have gotten no indication.  The effect seems to be accelerating, too--it happened three times in two hours today.

I've ran memory and hard disk checks and I have no issues.  I'm dual-booting Windows XP and have had no trouble there so it's not a hardware issue.  Plus, like I said, none of the alphas, nor the beta, nor the release candidate of Intrepid caused this problem.

This one's nasty, and if it keeps up I might be forced back to using Windows full-time. :cry:  I'm glad the community is aware of this issue and that it's not just me.  Is there a bug report yet?

---

### Post by BigSilly on 2008-11-13
> **Squonk07 said:**
> I am having the same problem as you.  I'm on a two year-old Toshiba laptop (Intel GM945 express chipset) and noticed this problem for the first time last week on a clean install of Intrepid.  I've been testing Intrepid since Alpha 3 and I've never seen this problem until now.

For the first week, I had no trouble whatsoever.  Then Intrepid started freezing at random times last week.  And, oddly enough, at first I got the blinking Caps Lock kernel panic light each time the OS froze.  The last few times, however, I have gotten no indication.  The effect seems to be accelerating, too--it happened three times in two hours today.

I've ran memory and hard disk checks and I have no issues.  I'm dual-booting Windows XP and have had no trouble there so it's not a hardware issue.  Plus, like I said, none of the alphas, nor the beta, nor the release candidate of Intrepid caused this problem.

This one's nasty, and if it keeps up I might be forced back to using Windows full-time. :cry:  I'm glad the community is aware of this issue and that it's not just me.  Is there a bug report yet?

Have to say, I'm still getting this problem. My original (somewhat crazy) theory about it being something to do with the monitor was completely off base, since it's still doing it with this old CRT. It just freezes up without warning, always just when I'm simply browsing the net. Nothing special.

It's the first time I've had to seriously look at other distros to get a solid system. It's a really worrying problem imho, and it sounds as though it could be pretty widespread too, so I really hope the team fix it as soon as they can. What's worrying me though, is many are saying this was in Hardy too, and still hasn't been fixed. I never had the issue with Hardy, so I might go back to that, but I think first I'll try a clean install of Intrepid and see where that gets me. Not very far I would imagine, but it's worth a shot.

Like you, I've checked the memory out, and the hard drive too, and all is well. The only thing I had changed was the monitor, but I discovered that wasn't the issue either. I'm hearing rumblings about kernel bugs, but I just don't know. Worried, and upset. :(

---

### Post by Squonk07 on 2008-11-13
> **BigSilly said:**
> Have to say, I'm still getting this problem. My original (somewhat crazy) theory about it being something to do with the monitor was completely off base, since it's still doing it with this old CRT. It just freezes up without warning, always just when I'm simply browsing the net. Nothing special.

It's the first time I've had to seriously look at other distros to get a solid system. It's a really worrying problem imho, and it sounds as though it could be pretty widespread too, so I really hope the team fix it as soon as they can. What's worrying me though, is many are saying this was in Hardy too, and still hasn't been fixed. I never had the issue with Hardy, so I might go back to that, but I think first I'll try a clean install of Intrepid and see where that gets me. Not very far I would imagine, but it's worth a shot.

Like you, I've checked the memory out, and the hard drive too, and all is well. The only thing I had changed was the monitor, but I discovered that wasn't the issue either. I'm hearing rumblings about kernel bugs, but I just don't know. Worried, and upset. :(

Check out [this]("http://ubuntuforums.org/showthread.php?p=6174214#post6174214") thread.  There's a solution there that might help (even though you connect to the Internet through Ethernet).  Sadly, I can't see if it works until I go back to my university (where they have 802.11g wireless networks).  Be sure to thank dhbabey if this works for you. :)

---

