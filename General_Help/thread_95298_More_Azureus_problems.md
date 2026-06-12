---
title: "More Azureus problems"
date: 2005-11-26
forum: General Help
---

### Post by Skerit on 2005-11-26
I just received my ubuntu cds (yay) and reinstalled breezy (was running the RC and flash didn't work and all, messed a lot of stuff up :))

Anyway, on my previous install azureus worked like a charm. I remember configuring a lot of stuff before I got it too work. But now I'm stuck.

I have a speedtouch 510 (or something like that) and I opened up the 6881 ports in it, I tested those ports in azureus and it gave me an "OK!" but my downloads are still frozen. Even though the "Tracker" part of the "My Torrents" window says "OK" nothing's happening. 

It's really strange because I can see how many seeds and leeches there are ..

I've tried a different port, 4747, but even though I open it up in the modem (by using the 10.0.0.40 ip and tcp port 4747) azureus would tell me there's a NAT error.  (So if I open up port 4747 it does nothing, when I open port 6881 at least it tells me it's ok (when it's not) and when I close that port it also gives a NAT error)

So, I'm completely stuck and I don't know any more places where I can open up ports...

---

### Post by Ocxic on 2005-11-26
[QUOTE=Skerit]
So, I'm completely stuck and I don't know any more places where I can open up ports...[/QUOTE]

Chack to see if you have Firestarter installed, if so run it and open the port in that, even while the firewall prog is closed it seems to still affect the sytem, at least on my machien.   what kind of net connection do you have? are you using a router?

---

### Post by Skerit on 2005-11-26
Hmm, even with firestarter it doesn't work :S

I don't have a router, I have a Alcatel Speedtouch 510...

---

### Post by Ocxic on 2005-11-26
[QUOTE=Skerit]Hmm, even with firestarter it doesn't work :S

I don't have a router, I have a Alcatel Speedtouch 510...[/QUOTE]

is that a sympatico modem???

that sounds like you have a DSL Net connection, not cable or dial-up? am i right?
if so, check and see if you need to setup you conect using PPPoE (Point-to-Point Protocol over Ethernet)
if so that could be the very reason it's not working. I've had the same problem.
Unfortunalty since I've used a router for a very long time I've not had to worry about this in ubuntu, so I have no idea how to go about setting up your net connection that way. Seach the fourms and wiki, I'm sure i saw something that could help you.

---

### Post by Skerit on 2005-11-26
Ow yea sorry,
it's an Alcatel modem :)
I got a ADSL subscription, ethernet modem...

---

### Post by Ocxic on 2005-11-26
yes an ADSL connect requires that you have a PPPoE connetion setup, the reason that you cant use azureus is because the modem will only open port 80, unless your PPPoE is setup, that will let azureus and other programs on your computer to open the ports on your modem and have it work properly, took me 2 week to figure that out with my azureus and ended up using the btdownload that comes with ubuntu. search the forums and wiki, I'm sure there is something in there about seeting up PPPoE connections, and don't forget to reset your modem by pussing the little reset button on the modem so the changes are applied properly and you can re-asign your username and password to your modem. after that it should work fine.

---

### Post by Skerit on 2005-11-26
Hmm, the connection works fine, I never had any problems with it. On my previous install I didn't have to do any ppoeconfig!

Anyway, I followed specific tutorials just for my modem and azureus, even though they worked on my previous install now it yet again, does nothing! Azureus doesn't now what to do and keeps telling me it's "OK!" and then switches back to "NAT-Error" I'll reset the modem and pray

Edit: Well, after reading some other threads about thesame problem (having a lot of seeds/leeches but no actual uploading or downloading) I reinstalled java and that indeed did the trick. I used the version from the resources (the blackdown version or something?)
So I put a lot of energy into a problem with a very simple solution, meh, at least I learned a bit about port forwarding and NAPT and all :)

---

