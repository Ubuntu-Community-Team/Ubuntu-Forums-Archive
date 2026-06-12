---
title: "Acer Aspire 3680 WiFi saga update..."
date: 2007-09-15
forum: Hardware &amp; Laptops
---

### Post by PsycoGeek on 2007-09-15
I too have purchased the Aspire 3680... mine is a 3680-2682, Model #ZR1.  It has an Atheros AR5BXB63 WiFi card in it.  You should be able to find the label for the card on the bottom of the laptop.  Check out this info below on this card...

[http://madwifi.org/wiki/Compatibility/Atheros]("http://madwifi.org/wiki/Compatibility/Atheros")

Looks like for now, if you have this chip you are out of luck with the built in WiFi.  If anyone has gotten it to work, please post your solution here.

Luckily, everything else works fine on Feisty, and I got this laptop on clearance for $398.  It was the display model.  They have no more in the store where I got this one.

---

### Post by pizzutz on 2007-09-17
I used the AR5007EG drivers with ndiswrapper to get mine working.  There some help in this thread [http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

---

### Post by PsycoGeek on 2007-09-19
I now have WiFi enabled on my 3680.  Here is how I did it:

*Disclaimer*  I am an experienced PC repair technician (retired from IT).  If you do not feel comfortable opening up your laptop and replacing components, then don't.  I am not responsible in any way it you laptop is damaged in the process described below, so don't ask me to pay for a new one or for repairs if it fails to work afterwards, M'kay?

**Step one:**  Go to eBay and find a suitable replacement network card.  It must be mini PCI-E, and should have support right out of the box from Ubuntu (do some research on the forums first).  I chose an Intel Pro 3945 ABG card for myself.

**Step two:**  Disconnect the laptop from the power source and remove the battery (I forgot to remove it when I did this).  With the laptop turned over and resting on a soft cloth remove the two screws that secure the cover (screwdriver is pointing to one of the two).  

[IMG]http://i68.photobucket.com/albums/i5/PsycoGeek/IMG_0210.jpg[/IMG]

Gently pry the cover off to reveal the RAM (at the top of the photo),CPU (middle, under the copper heat pipe), and addon cards.  The WiFi card is identified by the screwdriver.

[IMG]http://i68.photobucket.com/albums/i5/PsycoGeek/IMG_0211.jpg[/IMG]

**Step three:**  Remove the two antenna wires from the card gently (just pull them off, they snap on).  Remove the two screws holding the WiFi card in place and gently remove it by lifting up and pulling it out of the socket.  Here is the card removed:

[IMG]http://i68.photobucket.com/albums/i5/PsycoGeek/IMG_0215.jpg[/IMG]

Insert the new WiFi card (in my case the Intel PRO 3945) and secure with the screws.  Re-attach the antenna wires.

[IMG]http://i68.photobucket.com/albums/i5/PsycoGeek/IMG_0221.jpg[/IMG]

**Step four:**  Replace the cover, battery, and flip it over.  Boot up your Aspire 3680 and check the configuration in Network Manager.  This is what I got...

[IMG]http://i68.photobucket.com/albums/i5/PsycoGeek/IMG_0222.jpg[/IMG]

Success!  But alas, no wireless network within range to test it on.  The WiFi button on the front of the laptop also works now.  The light blinks when it is searching for a connection, and appears to turn the wireless card on and off.

---

### Post by ljonesj on 2007-09-26
good write up, but i had always thought the atheros chipsets were ubuntu friendly as i have a netgear wireless 511t card that has an atheros chip in it. i made sure of that as there are several versions of this card if its a 511t its good.

---

### Post by PsycoGeek on 2007-09-26
> **ljonesj said:**
> good write up, but i had always thought the atheros chipsets were ubuntu friendly as i have a netgear wireless 511t card that has an atheros chip in it. i made sure of that as there are several versions of this card if its a 511t its good.

It's only the most recent version of the Atheros chipset that has a problem.  Acer used it on a few models of the 3680, I have an Aspire 3680-2682.  My Ubuntu install could not resolve what card it was, and I was never able to get the NDIS wrapper working.

---

### Post by ljonesj on 2007-09-26
me personally i hate having to use ndis wrapper. lucky i have the 511t card as a secondcard in my windows. it has a broadcom 4318 card which also sucks for ubuntu so thats the reson i got it so it makes having a dual boot system easier, but your way makes it more stealth if you want  kismet to work too

---

### Post by PsycoGeek on 2007-09-26
And my way keeps you one and only PC card slot open for something more important.  Like a TV card!

---

### Post by ljonesj on 2007-09-27
not really interested in the tv card myself but i have heard a lot of people using myth tv as a dvr for their homes. that means thou you will either need an external hard drive that is good size or increase the internal drive in the computer eventually as you would run out of space. how much was that card that you got as i may go that route myself eventualy

---

### Post by PsycoGeek on 2007-09-27
I bought the card from ebay for just under $35 shipped.

---

### Post by ljonesj on 2007-09-27
wow good deal. i heard those cards can be a little high if you buy them other places if you can find them

---

### Post by funnypanks on 2007-09-28
> **PsycoGeek said:**
> I 

[IMG]http://i68.photobucket.com/albums/i5/PsycoGeek/IMG_0221.jpg[/IMG]

Success!  But alas, no wireless network within range to test it on.  The WiFi button on the front of the laptop also works now.  The light blinks when it is searching for a connection, and appears to turn the wireless card on and off.

gj psychogeek, and dont worry, i've been using ubuntu on my 3945abg for a few months now, ALWAYS wireless. FLAWLESS so you are definitley set. my question is off topic a bit, i have a similar lappy and wanted to know what that card next to the pci-e? i noticed it when i added ram and had no clue what it was, and since u were a technitian i couldnt imagine a better person to ask. oh and i find wicd works better than gnome network manager for me, sometimes gnm wouldnt startup when my comp started

---

### Post by PsycoGeek on 2007-09-28
Thanks for the reply funnypanks.

I am using Wicd as well.  I was also able to see both of my neighbors wireless setups, so I went and bought a Linksys WAP, and it is working great.


As for the card mounted next to the network card, I don't really know.  I will be putting a RAM upgrade in soon (next week sometime), so I will pull the card again and see if I can figure out what it is.  The lettering on it is black, and tiny, and on a clear material, so it was really hard to read (I gave up after a few minuets of attempting to read it).  I beleive it may be the modem, but don't quote me on that yet.  The wires looked like they were running in the right direction for that.

---

### Post by PsycoGeek on 2007-09-29
I had to go back to the standard network manager because of autoconnecting to shares.  Wicd was interfering with the autoconnect.

---

### Post by funnypanks on 2007-10-01
im network manager too, not by choice though. latest dist-upgrade installed it again, and ive been too lazy to go get wicd again.

---

### Post by PsycoGeek on 2007-10-06
> **funnypanks said:**
> my question is off topic a bit, i have a similar lappy and wanted to know what that card next to the pci-e?

It looks like the modem.  I can't find anything on it as of yet, but the name on it is Anatel (tel=telephone, a.k.a. modem?)

Anyhow, I just left it be.  Didn't want to experiment to see what would stop working if I removed it.  

On a side note, my 2gigs of Corsair 667mhz RAM are in and working fine. I bumped the video memory settings up to use the max ammount of shared memory, 256mb I beleive, and it is working great.  A bit more snappy than it was before, and so far no lock-ups with Firefox and flashed based embedded video (it would do that before the upgrade).

---

### Post by CapnK on 2007-10-07
I get the feeling that at the Acer factory there is a large bin full of wireless cards of all different makes and manufactures. When they need one for a 3680, they close their eyes and just grab whatever card happens to be under their fingers when they reach into the bin, and stick that into the 3680. :D

Mine is a 3680-2682, purchased less than 3 weeks ago, and has a Dell 1390 w/Bcom chipset wireless card in it.

I *think* that other card next to the wireless is a modem, but only because of the Agere chipset which was in Lucent modems. I may well be wrong, Agere makes a lot of stuff. It could easily be Bluetooth, I guess.

---

### Post by ljonesj on 2007-10-07
could be i noticed that to. i dont have the wireless problems as i have an external card even thou it broke with the latest kernal in 7.10 testing. had to go to the old kernal and use that to download the restricted modules for the new kernal. what a pain but its back working i have this exact laptop. looking to upgrade it to at least a gig in the next few weeks. i hope to give more response in booting and to max the video card as phsycogeek is right about it needing more even thou i have a gig and a half of swap which helps

---

### Post by XGX2007 on 2007-11-03
> **PsycoGeek said:**
> It looks like the modem.  I can't find anything on it as of yet, but the name on it is Anatel (tel=telephone, a.k.a. modem?)

Anyhow, I just left it be.  Didn't want to experiment to see what would stop working if I removed it.  

On a side note, my 2gigs of Corsair 667mhz RAM are in and working fine. I bumped the video memory settings up to use the max ammount of shared memory, 256mb I beleive, and it is working great.  A bit more snappy than it was before, and so far no lock-ups with Firefox and flashed based embedded video (it would do that before the upgrade).

It is the modem, mine says "agere", and I find it funny that the modem in my 3680 runs on the Intel HDA bus. Actually in windows before I installed the driver for it, windows showed it as an unknown HDA audio device, when in fact it was an agere 56k modem.

---

### Post by linuxman410 on 2007-11-08
i have the acer 3680-2682 i am running ubuntu 7.10 and built in wireless is working i downloaded acer acpi and ndiswrapper both and followed the directions on this forum and it worked

---

### Post by TripWire7 on 2007-12-02
I also have an acer aspire 3689.... how ever I have a broadcom 93411bcm wireless card in it.  I can scan for networks and even connect to them.  How ever after about 15 sec on the internet my connection fails.  I'm still using the restricted drivers for it, being I've been working on it for 3 weeks now, with no success..... any ideas?

---

### Post by TripWire7 on 2007-12-02
sorry meant to say 3680,,,,,, sorry for the typo

---

### Post by onekopaka on 2007-12-03
Funny. My Acer Aspire 3680-2682 has a Broadcom, according to Ubuntu, and Windows. Anyone got any ideas on how to get my wifi working with a supposed broadcom card?

---

### Post by phillfri on 2007-12-10
My 3680-2682 has a BCM94311MCG wireless chipset. I'm running PCLinuxOS 2007 (now don't flame me Ubuntu fans :>) Ndiswrapper with the bcmwl5.sys and bcmwl5.if files works fine for me, including wpa. But . . . if you try to add a hostname for your lappy, it will break ndiswrapper. A least that's what's happening to me in PCLOS 2007. So, I'd suggest tying to set up your network connection without a hostname to start out.

---

