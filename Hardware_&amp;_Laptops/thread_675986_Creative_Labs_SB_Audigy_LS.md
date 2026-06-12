---
title: "Creative Labs SB Audigy LS"
date: 2008-01-23
forum: Hardware &amp; Laptops
---

### Post by kougaru on 2008-01-23
After my old sound card died a bought a new one the replace it. But the only problem is I can't get it to work. Go figure... When I try "lspci -v" Ubuntu finds it and lists it as

```
07:01.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Creative Labs Unknown device 100a
        Flags: bus master, medium devsel, latency 32, IRQ 9
        I/O ports at 1000 [size=32]
        Capabilities: <access denied>
```

But when I try "aplay -l" it only lists the the motherboards integrated sound, and when I go to system ->preferences->sound it's not listed there either so I can't even select it.

Can someone give me some help with this? Any help will be appreciated. I'm running Ubuntu 7.10

Thanks

---

### Post by Brerlapn on 2008-01-24
Bump.

I'm having trouble with stuttering in my sound running 7.10, but I'm not even able to see my Creative sound card in aplay or lspci.  Only the onboard Intel sound shows up.  So far no luck searching the forums.

---

### Post by AlexcGilliland on 2008-01-26
I have the same problem as those above

---

### Post by k.i.s.s. on 2008-01-27
Don`t know about the Creative Labs SB Audigy LS but I have the Creative SBXFi  card and have scoured the web looking for info about how to configure it with ubuntu and/or Puppy linux. Best I can understand is; if you have this card you are out of luck! No sound, no workable drivers(and none expected soon) for linux period.
 I would suspect this to be true of other Creative cards, possibly the "Audigy"?

 Anyone knowing otherwise please post details!
:(:confused::mad:

---

### Post by Brerlapn on 2008-01-29
One bit of information that might help folks here is that I discovered that my soundcard, a Creativelabs Soundblaster Audigy Advanced MB, is not actually a piece of hardware.  My hardware is a Sigmatel STAC9200 HD.  The Audigy is just software that runs on top of that soundcard in Windows presumably to enhance the capabilities of the card.  So if you don't see an Audigy card in your hardware list, but you do see some form of Sigmatel, that's probably why.

Ubuntu doesn't recognize the Sigmatel as a digital sound card, either, but I haven't had time to troubleshoot that particular problem.

---

### Post by k.i.s.s. on 2008-02-02
That`s interesting, Brerlapn! :)

Just one final note on the SBXFi X-treme Music card. I installed the [COLOR="Red"]"Creative Sound Blaster X-Fi series XP Beta Driver 2.14.0001"[/COLOR] found on the Creative web site hoping it just might get my SBXFi into ubuntu. BIG MISTAKE! It crashed windows XP big time! Only way I could get back into windows was in "safe mode". Ended up having to completely uninstall and remove all Creative files and re-install from the CD that came with the card. At least I got it back working on XP but am missing the console or whatever the program is that gives you sound options, etc. and haven`t took the time to see if I can get that back.

:mad:

---

