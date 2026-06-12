---
title: "Wireless internet not connecting"
date: 2005-11-23
forum: Hardware &amp; Laptops
---

### Post by DaGGer on 2005-11-23
ok well i had Ubuntu on my computer for a while before and it was great because i was able to use my wireless ineternet and i didn't have to set anything up, it found the card and everything was fine all i had to do was go in and activiate it and there we go.  Now i am trying to install Ubuntu again because i have windows on my computer and when i try to install it, it comes up with a "not using DHCP", it also says "may be slow or some network hardware is not working properly."  Now this is what doesn't make sence, my medem and router are still the same all i have done with those is unplug them a few times and my internet card is the same along with everything else.  Can anyone tell me whats up with this.  btw these are my computer specs

MSI KT880 Motherboard
Amd barton 2800+ processor
512 pqi ram at 400mhz(after christmas will be 1 gig or 1.5 gigs depending)
ATI Radeon 9200 Video card(going to be a Evga 6800 when i get a little more monry)
Sound Blaster sound card
D-link 520+ wireless internet card

and thats about all i can think of.

---

### Post by DaGGer on 2005-11-24
ok well i post in a different section and 30 people have looked it and no one commented so maybe better luck here

ok well i had Ubuntu on my computer for a while before and it was great because i was able to use my wireless ineternet and i didn't have to set anything up, it found the card and everything was fine all i had to do was go in and activiate it and there we go. Now i am trying to install Ubuntu again because i have windows on my computer and when i try to install it, it comes up with a "not using DHCP", it also says "may be slow or some network hardware is not working properly." Now this is what doesn't make sence, my medem and router are still the same all i have done with those is unplug them a few times and my internet card is the same along with everything else. Can anyone tell me whats up with this. btw these are my computer specs

MSI KT880 Motherboard
Amd barton 2800+ processor
512 pqi ram at 400mhz(after christmas will be 1 gig or 1.5 gigs depending)
ATI Radeon 9200 Video card(going to be a Evga 6800 when i get a little more monry)
Sound Blaster sound card
D-link 520+ wireless internet card

and thats about all i can think of.

---

### Post by soulestream on 2005-11-24
does the card show up and just not working 

or 

was it not detected at all?


soule

---

### Post by DaGGer on 2005-11-25
well i think it was detected, i have two diskes.  one is an older version of ubuntu and it finds it and i believe that the newer one fines it too.  It just can't find a wirless point using DHCP.

---

### Post by Randy Sparks on 2005-11-25
It's not clear from your original posting if you're talking about the card not being recognised during installation, or whether it's not recognised when everything is up and running.

I've got a similar PCI wifi card in my PC and it's not recognised when Ubuntu is installing. But once everything is up and running, I can configure it perfectly ALTHOUGH I can't get DHCP to work and must give the card a static IP address (also also manually enter a DNS address - I can enter the address of my DSL router, ie the gateway address, and that works fine). 

This seems to be a bug with Ubuntu 5.10 or, more accurately, with GNOME. Somebody reported the bug on Bugzilla and it was bumped up to the GNOME bugzilla.

But if the problem is simply that the card isn't recognised during install then you've nothing to worry about. Just configure the card post-instalation and do a Synaptic upgrade as soon as you can.

---

### Post by DaGGer on 2005-11-25
ok well the thing is i have had the older version of ubuntu on my machine before and it finds it fine and so does this version of ubuntu,  so i'm saying that it does find it i belive.  Now on the older version and this version it does a search to find a wirless access point so i can get internet, last time i would just go through and and it would find the point i just told it to put names and everything.  Now if someone could help me ou ton putting a static ip address and everthing for the card, and how to do a Synaptic update or what not.

---

### Post by soulestream on 2005-11-25
go to 

Desktop -> Administration -> networking 

enter information for you card


or 

/etc/network/interfaces

soule

---

### Post by DaGGer on 2005-11-26
ok well i'm having a huge problem, i never got to finish my install because i was always just stopping and not finishing it and now i finally finished the install but when i get to the login screen its all scrambled but i still hear the little sound go off.  I don't get it can anyone help me.

---

