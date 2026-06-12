---
title: "Starting to lose hope in finding an actual wireless device THAT WORKS!!"
date: 2007-11-26
forum: Hardware &amp; Laptops
---

### Post by Roasted on 2007-11-26
I'm running Ubuntu Gutsy 7.10 on a Toshiba A215-S7422.

The internal wireless card flat out isn't compatible, from what I've read. Okay fine, get a pcmcia card, right? No pcmcia slot... Expresscard? Yep, got that. Any available that are compatible? Nope. Okay... USB. I grabbed a Linksys WUSB54GC, because it was supposedly the "end all be all" of wireless adapters that work with Ubuntu... and it locks up my system after 10 minutes of use. On top of that, I can only get on networks that have zero encryption enabled.


Are there any wireless G devices out there that actually WORK with Ubuntu? Looking for ExpressCard 34/54 or USB... Or perhaps somebody has an idea that'll help out my issues with the Linksys??

---

### Post by 11hjpphty76lkjj on 2007-11-26
I've had great success with several different cards, but you have to do your home work first.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Hope this helps.

A

---

### Post by naja on 2007-11-26
Hi
try using wicq if u think your failur is because networkmanager-SOFTWARE-,but be warned to install wicq you have to remove the networkmanager.
with wicq you can manage your wirelessnetworks,i am using wep now,but it should support wpa1 and wpa2.Its really good,give it a try.
I remember being able to run wireless with Atheros-chip on feisty Liv e-i think-,the system detects it and installs the restricted driver too,it was a USB-Stickform.
i wish you luck

---

### Post by Roasted on 2007-11-26
> **kalosaurusrex said:**
> I've had great success with several different cards, but you have to do your home work first.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Hope this helps.

A

That's just it. I've been using that as my hardware bible.

My usb wireless G WUSB54GC is supposed to work. It's tested. Working. Done. Why does it lock up Ubuntu after 10 minutes of use? Why can't I log onto secure networks with it?

It just seems like wireless is flat out DEAD for Ubuntu. It honestly makes me wonder why I even bothered to install it on a laptop.

---

### Post by Roasted on 2007-11-26
> **naja said:**
> Hi
try using wicq if u think your failur is because networkmanager-SOFTWARE-,but be warned to install wicq you have to remove the networkmanager.
with wicq you can manage your wirelessnetworks,i am using wep now,but it should support wpa1 and wpa2.Its really good,give it a try.
I remember being able to run wireless with Atheros-chip on feisty Liv e-i think-,the system detects it and installs the restricted driver too,it was a USB-Stickform.
i wish you luck

I did a synaptic search for wicq. Where in the world do I get it? I didn't get any results in synaptic.

---

### Post by mperry on 2007-11-27
I think the person is talking about wicd and not wicq. I just tried it on xubuntu and you do indeed have to remove anything else because wicd wants to own.  That being said, it could not bring back up my ipw2200 wifi card on a resume event and wifi-radar always does that for me.  wicd is at [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) if you're interested.  At a personal level, by the time you install, learn how to use, manipulate, run, and do everything else with "some graphical tool" you could have run iwconfig blah 10 times :)

---

### Post by Roasted on 2007-11-27
I just ended up doing some further research on the wireless adapter I chose. The comment by the adapter was "Needs some hacking." Eh.... like I said, I got the thing to work... it just sucks after 5 minutes because it froze my computer. Plus I couldn't log onto encrypted networks.


So I searched around the ubuntu wiki some more and found 3com had a very nice usb wireless G adapter that supposedly supported wep and wpa. Very nice...

I just ordered one off of newegg.com. In a few days I'll report back with how that thing worked. Supposedly the drivers are included, and if not, ndiswrapper can take over.

Has anybody ever had a wireless G Adapter that just worked in Ubuntu with little or no configuration necessary?? If so... please list the model. Just for the sake of me getting more familiar with these things. :)

---

### Post by fastphil123 on 2007-11-27
I tried every method I could find to get my HP Pavilion dv5000 Laptop to go wireless.  None worked.  Then I tried a MyEssentials Wireless G USB AdaptorME1001-USB ver 1000 and it worked perfectly right out of the box!  It is made by Belkin but the Belkin USB didn't work for me.  This one does.

OS 7.10 Gutsy Gibbon

---

### Post by Roasted on 2007-11-27
I've never heard of MyEssentials. Where did you get it?

---

### Post by naja on 2007-11-27
> **Roasted said:**
> I did a synaptic search for wicq. Where in the world do I get it? I didn't get any results in synaptic.
Sorry, typo
now i am using WPA2/PSK, on a realtek 1885 -PCMCIA- using Ndiswrapper,i had to blacklist the rtl1885 driver first. you can use ndisgtk to install drivers-to avoid the cmdlifestyle-.though ndiswrapper in the repository,i ve compiled the ndiswrapper so i can get the latest version (using 1.49).
and it works wonderfully
I wish you luck

---

