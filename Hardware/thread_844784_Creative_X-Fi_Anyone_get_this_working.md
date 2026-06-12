---
title: "Creative X-Fi: Anyone get this working?"
date: 2008-06-29
forum: Hardware
---

### Post by joethenoob on 2008-06-29
Obviously I'm having a problem getting my Creative X-Fi working and am hoping somebody figured it out.

I used the OSS tutorial and no luck. Anyone get this thing working?

Thanks in advance.

---

### Post by thideras on 2008-06-30
I think you will receive more assistance if you can give more information than "it doesn't work".

You getting errors?  A certain step not working correctly?  etc

I'll soon be going through these steps for my Auzentech Prelude, hope I don't have many issues :)

---

### Post by joethenoob on 2008-06-30
> **thideras said:**
> I think you will receive more assistance if you can give more information than "it doesn't work".

You getting errors?  A certain step not working correctly?  etc

I'll soon be going through these steps for my Auzentech Prelude, hope I don't have many issues :)

No errors, just not getting any sound. After the OSS setup, I added the custom app launcher for ossxmix. When I launch ossxmix, it shows my sound card properly, but when I go in to sounds and set oss for output and hit test, I get nothing.

If you get it running, lemme know how you did it :)

---

### Post by thideras on 2008-06-30
Hmm, that is strange...

I'll mess with it later tonight and see how far I get :)

---

### Post by stchman on 2008-06-30
Boycott Creative until the fully support Linux with their X-Fi.  It is amazing, the Sound Blaster series works perfectly with Linux, but they refuse to give prompt service to the X-Fi for Linux users.  The X-Fi has been out about 3 years now.

---

### Post by thideras on 2008-06-30
> **stchman said:**
> Boycott Creative until the fully support Linux with their X-Fi.  It is amazing, the Sound Blaster series works perfectly with Linux, but they refuse to give prompt service to the X-Fi for Linux users.  The X-Fi has been out about 3 years now.Not to be rude, but that is probably the worst answer you could give.  He is asking how to fix it, not how this product does.

---

### Post by starcannon on 2008-06-30
Heres a link to a thread the declares X-Fi install success, GL

[http://ubuntuforums.org/showthread.php?t=571656](http://ubuntuforums.org/showthread.php?t=571656)

---

### Post by joethenoob on 2008-06-30
> **stchman said:**
> Boycott Creative until the fully support Linux with their X-Fi.  It is amazing, the Sound Blaster series works perfectly with Linux, but they refuse to give prompt service to the X-Fi for Linux users.  The X-Fi has been out about 3 years now.

Good idea. I'll take the sound card out of my computer and buy something else so I can run a free OS that doesn't run everything I could run in Windows. Every time I see one of the *nix trolls tell us noobs to boycott this or xyz corp is evil, it just makes me want to shine the "community-supported OS" thing all together. I'm not here to join a cult of haters. I just wanted to learn something new.

---

### Post by joethenoob on 2008-06-30
> **starcannon said:**
> Heres a link to a thread the declares X-Fi install success, GL

[http://ubuntuforums.org/showthread.php?t=571656](http://ubuntuforums.org/showthread.php?t=571656)

yeah, I tried the first part of this for the oss and no dice. I was a little weary of the "for advanced users only" link, but I'll give it try. Whats the worst that could happen?

---

### Post by starcannon on 2008-06-30
worse that could happen is you'd have to reinstall, though I doubt that would happen with installing a sound device.

If your into it, I'd suggest learning how to put /home on its own partition, this removes the entire "worst case scenario" well diminishes it greatly anyway, HDD failures are never pretty I don't care what OS your using hehe.

As far as the boycott thing, I don't actually boycott anyone, I do however give preferential treatment to hardware developers who allow me to choose my operating system; I'm not picky if the driver is FOSS or Closed, as long as it works and is maintained. /shrug thats just me though, you have to do what you think is best. I'd also take this time to mention that just because you payed no money for your linux operating system does not mean it has no value. Creative released the paperwork on the X-Fi card, its only a matter of time before it is supported by ALSA by default, I don't know if our version of OSS has X-Fi support in it already, but one could try:

System-->Preferences--Sound

Then set everything to OSS and see if it will work, may require a reboot.

If that doesn't work, then if your motherboard has onboard sound, one could try that for the time being until such time as your X-Fi card is put into the default ALSA.

And while it may not be what you want to hear, at the end of the day the simple solution may be to choose a card from this list:

[http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)

You can get many of these for next to nothing on Ebay.

As you can see, more cards are supported than are not, theres only a handful of hardware developers left that ignore the linux community, and the list is getting shorter every day. 

Creative has gotten better about releasing development info, even VIA is getting better, and actually releasing new and maintained drivers. While that may not seem like much, it is progress.

GL and above all, have fun.

---

### Post by stchman on 2008-06-30
> **joethenoob said:**
> Good idea. I'll take the sound card out of my computer and buy something else so I can run a free OS that doesn't run everything I could run in Windows. Every time I see one of the *nix trolls tell us noobs to boycott this or xyz corp is evil, it just makes me want to shine the "community-supported OS" thing all together. I'm not here to join a cult of haters. I just wanted to learn something new.

I never used the word "evil".  My point is that if a hardware manufacturer does not support the OS I want to run then they are not going to get my money.

The more people like me tell "xyz" that I won't buy their hardware unless they support my OS the more they will support my OS.

I support Nvidia, Intel, AMD(AMD is ACTUALLY making a great effort to support their ATI video cards under Linux), HP, Realtek, VIA, Atheros, etc.  I do know that sometimes hardware manufacturers take about 6 months or so after release to get Linux drivers and I can accept that.  I do not buy the most bleeding edge equipment and stay about 6 months or so behind the hardware curve so I am not usually affected.

The X-Fi is not bleeding edge and can almost be considered legacy.

I do not support Broadcom, Lexmark, or Marvell as they make little effort to support Linux and therefore do not need my money.

I would have said OK if it took 6 months or so after the X-Fi release to get some good drivers, but over 3 years to give beta drivers is down right ridiculous.

I own an Audigy 2 and SBLive cards that work fantastic OOB.  The X-Fi should work OOB with Hardy.

---

### Post by freeloader105 on 2008-07-18
joethenoob, ditch OSS and go the ALSA route: [http://ubuntuforums.org/showpost.php?p=4823915&postcount=675](http://ubuntuforums.org/showpost.php?p=4823915&postcount=675) . It worked for me.

---

