---
title: "Brother HL-2270DW nightmare; going in circles ..."
date: 2011-05-13
forum: Hardware
---

### Post by Bucky Ball on 2011-05-13
Try this one on.

Brother HL-2270DW mono laser printer plugged into a D-Link 524 router and a couple of wireless laptops (one 10.04 and other 10.10) using that as an access point and a desktop (8.04) plugged into the router.

After spending way too long setting the whole thing up I finally got one of the machines printing at about 4am. Nightmare ride. By 4:30am I had all three printing beautifully; test pages, pdfs, duplex, whatever you like. Life was complete; all three machines printing great on three different Ubuntu releases!

This is the kicker. I get up, switch on my laptop, try to print a test page. Nothing. No response from the printer at all. Click my printer icon and at the end of the job line I get:

> Processing - Printer not connected?... followed shortly thereafter by:
> 
Processing - Printer Warning!
On further investigation, none of the three machines* - all of which were working perfectly the night before - *are printing at all and all have the same error message. They've all dropped the bundle. 

What I can't get is that I'd changed nothing (unless I sleep tweak or the bug goblins did some tweaking in the night). All I did was switch the three machines off, sleep, get up and switch 'em back on again to find printing is dead on the lot. The printer wasn't touched, that was left on overnight. (And will gleefully print a test page when I hit the appropriate button on the printer.)

I am totally sleep deprived, bamboozled, frazzled, frustrated and fairly desperate. I have spent the best part of the day going in circles and can't afford the time (uni student with assignments due which is why I need to print!). Must have spent about ten hours on this!

A word; at least I had things working with Linux, if only briefly. I couldn't get anything working at all with XP or Windows 7, despite the disco printer installer CD. Oh, Brother; oh, so simple ... not!

I would really appreciate it if someone(s) could give me a hand with this. I have tried everything and scoured the internet to no avail. I'm figuring perhaps all three machines have dropped something on reboot today but can't figure what. I will provide whatever info anyone needs to try and fix this. Cheers in advance ...

PS: Cups and lpd drivers installed fine, no issue there. Everything appears to be fine until you actually try and print. The two laptops I have tried to get going but the desktop I haven't touched so I can have the working setup there (even though it is not working now!).

---

### Post by Bucky Ball on 2011-05-13
I will add that in System>Administration>Printers, I click the Brother printer and it gives me the details and tells me:

> Printer state: Idle - Connecting to Printer ...
... and that's it. Maybe the printer is the problem? As mentioned, when I press the appropriate button it has no problem pumping out a page with printer details, etc. but maybe it is tied up on the network somehow so nothing can get through. ?

If I had any idea how to set the printers IP etc it would be a help. It did set itself something but now seems to have no IP again. I could ping it before but not now. I'm stumped. Any help appreciated.

---

### Post by Bucky Ball on 2011-05-13
Any takers? I'm desperate. Starting to think maybe the printer has dropped it's IP. How the heck do I force one in there???

---

### Post by walt.smith1960 on 2011-05-13
> **Bucky Ball said:**
> Any takers? I'm desperate. Starting to think maybe the printer has dropped it's IP. How the heck do I force one in there???

Check the Device URI under printer properties.  I've had something very similar in the past. The device URI started with DNSSD://something.  For whatever reason that address didn't work. I've found that socket://xxx.xxx.xxx.xxx where x=i.p address works most reliably for me.

---

### Post by Bucky Ball on 2011-05-13
Thanks for that. I was using:

lpd://xxx.xxx.xxx.xxx/lp

That did work on all the machines. Then it didn't after I rebooted the machines. I'll give your suggestion a try and let you know. Thanks. ;)

---

### Post by Bucky Ball on 2011-05-13
Okay, in System>Admin>Printing I am using the driver 'Brother HL2270DW for CUPS' and for the device URI I have:

> Device URI: socket://169.254.90.34No difference. I'll keep trying (have no choice!).

PS: I also tried:

> socket://169.254.90.34:9100Nothing.

---

### Post by Bucky Ball on 2011-05-13
The plot thickens. I printed out the Printer Settings to check that the IP address was the same as when it was all working and ... 

> IP Address = 169.254.84.151 (via APIPA) Before, when it actually worked, it was:

> IP Address = 169.254.90.34 (via APIPA)  So, thought I'd found the answer. Add printer from scratch, use the new IP address ... no different. It just keeps processing the job but that's it. I open a terminal and attempt to ping the new address and 'Host Unreachable'. Where to now? I'm at a loss. 

If the thing keeps changing its IP when I switch it off and back on again (which I did this morning) it makes like difficult! How can I jam one in there and make it stick? 

I have tried assigning the printer a static IP by using the mac address of the printer in the DHCP setup of the router but nothin' doing. Ignores it completely. 

Any help? Just ask for any info you might need anybody. ;)

PS: I had no idea what APIPA was so just did a little research and apparently APIPA generates an IP address when a print server isn't present. Therefore, no print server present. Is the router the printer is plugged into the print server? APIPA uses the subnet mask 255.255.0.0 which is different from my LAN subnet mask. 

I'm wondering if I need to have the router serve an IP to the printer through DHCP (DHCP currently off and all machines use static IPs), but of course, this would mean everytime the router and printer reconnect the printer is served a new IP. Impossible situation. 

Where to from here? I stumble on ...

---

### Post by Bucky Ball on 2011-05-13
Just switched printer off, setup a static IP for it in the router using the printer's MAC address, switched the printer back on, printed the Printer Settings info again and this time ... APIPA is enabled but there is no IP address (or subnet mask) set under the printer's IP settings. 

Could this mean there is a print server present - presumably the router - as APIPA is enabled but didn't kick in with an IP? If so, how do I switch APIPA off and get a custom static IP into the damn thing. Frustration ...

---

### Post by walt.smith1960 on 2011-05-14
I'm not familiar with the HL-2270DW but the 2 Brother MFDs I have I can check/set the I.P. address on the printer via the front panel. For the socket:// addressing to work I assigned static I.P. addresses to both printers.  My router DHCP server is set to serve a certain range of I.P. addresses.  In my case it's something like 192.168.1.50  to 192.168.1.100 for example.  One printer is 192.168.1.60 and the other 192.168.1.90.  Same subnet of course.

---

### Post by Bucky Ball on 2011-05-14
Thanks Walt but no can do with setting the IP address from the front panel. The printer has one button in fact! Very basic but suitable for our needs. I have tried a few things but can't get an IP in there.

Not sure if I mentioned but set a static IP for it on the router using the MAC address on the router. Print settings show same as yours; APIPA is enabled but under IP settings there is nothing now. All 0.0.0.0. Still can't connect or ping it.

---

### Post by walt.smith1960 on 2011-05-14
> **Bucky Ball said:**
> Thanks Walt but no can do with setting the IP address from the front panel. The printer has one button in fact! Very basic but suitable for our needs. I have tried a few things but can't get an IP in there.



One button makes it tough.  Are you  able to get to the device via Windows or Mac?  If so, I wonder if there's something in the Brother Windows software that would enable you to view & change your device settings?

---

### Post by Bucky Ball on 2011-05-14
As I mentioned earlier, I did have it working on the network beutifully with all three machines running three different releases (8.04, 10.04,10.10)! As for Windows and the disco CD, I couldn't get it working at all; on the network that is. Maybe I'll try plugging it in to the Windows box via USB rather than the network and see if I can't get an IP in there.

Thanks for your ideas, Walt. ;)

PS: Bucky's offline alter-ego also = 1960. :)

---

### Post by moore.bryan on 2011-05-14
I had a very similar problem with my Brother HL-2170W and found a had to try all possible configurations of any/all drivers possible with any/all printing protocols before I found one that worked...

---

### Post by Bucky Ball on 2011-05-14
> **moore.bryan said:**
> I had a very similar problem with my Brother HL-2170W and found a had to try all possible configurations of any/all drivers possible with any/all printing protocols before I found one that worked...

Yea, thanks Bryan. Know what you mean. I actually had it working on all three machines using the HL-2060 driver! That was the only one that worked. Now I have the HL-2270DW driver there and that doesn't work, but neither does the 2060 anymore!

Current state of play: I'm getting somewhere, hopefully closer to printing something over the network. I plugged into the Windows box, as suggested, and got the BRAdmin Light happening, Brothers tool for setting up the machine online. Trouble is, it doesn't see it. Searches but finds nothing. Yes, all correct Windows print drivers are installed.

So, I figure I will forget the network and plug the ethernet cable directly into the back of the computer. Can't go wrong. Auto-setup with their GUI. Apparently. Again, nothing. Windows XP results:

* Doesn't see or find the printer on the network;
* Doesn't see the printer when plugged directly into the computer;
* Printer faultless when plugged in via USB (that doesn't seem to allow you to then change the USB printer connection to a wired or wireless connection incidentally).

I'm stumped. It did work over the network for about three hours what seems like a lifetime ago. I'm wondering if it might be something dodgy with the printer. The fact that Windows doesn't see the thing either makes me wonder. 

Open to all/any ideas/suggestions ... :( :confused:

---

### Post by Bucky Ball on 2011-05-14
Well, now my mind is completely bent out of shape by this weirdness, it is time for an email to Brother tech support. 

Will post back with any further developments and hopefully I'll be writing a how-to when I eventually get this working so others won't have to live this nightmare.

I have discovered a couple of things:

* My printer is very new and Brother haven't got around to perfecting their Linux install for it yet (and therefore Ubuntu doesn't automagically see it and set it up).
* Brother seem extremely supportive of Linux community and a lot of their older machines install very easily.

I'm hoping that just around the corner there is a fix from them but not holding my breath.

Thanks for people's help and if anyone else has any suggestions, fire away, I'm all ears (and eyes and fingers). ;)

---

### Post by Bucky Ball on 2011-05-15
Friends! I fixed it! 

Post #13 here:

[http://ubuntuforums.org/showthread.php?t=897227&page=2](http://ubuntuforums.org/showthread.php?t=897227&page=2)

... did it for me. Through localhost:163/printers (the CUPS web interface) I modified the printer to read:

lpd/xxx.xxx.xxx.xxx/binary_1

... where xxx.xxx.xxx.xxx is the printer's IP instead of:

lpd/xxx.xxx.xxx.xxx/lp

Clicked 'Print Test Page' and out it pops! Yay. So I moved to another laptop, tried the same trick, and working fine! I can't express this amount of happiness. Networked duplex printing. Now if only I could fix the world's problems over three days!!!

A note: While the System>Admin>Printing option offers the correct driver for the HL-2270DW the CUPS interface does not and I'm therefore using the driver I got it working with in the first place; the one for the 2060. Later I will try doing this on another machine with the Ubuntu printing setup and see if I can't get it cranking with correct driver. I'm now optimistic. Who knows, maybe one of these days I will get the wireless function working!

Another note: I have not been able to assign an IP address but am using the one APIPA has assigned (available by clicking the 'GO' button three times and checking page 3/3 of the printer settings). I will look into this later.

Thanks for ideas and suggestions. I will write this up in a HOWTO when I have time (catch up on uni work now) to help others until the day when the driver and setup for this machine is included in a Ubuntu release and it all happens automagically (in three minutes rather than three days).

Thanks again and happy Ubunteering. ;) :D :cool: ):P :rolleyes:

---

### Post by walt.smith1960 on 2011-05-15
Kudos for your persistence, Bucky. I'm glad you were able to get it to work.  It's curious indeed that Windows didn't see your box.  I do wonder if something is a little bit amiss with your machine or if it's the nature of that model.  I've recommended Brother printers to others who ask about good printer brands for use with Linux.  Your experience has me tempering my enthusiasm.

---

### Post by Bucky Ball on 2011-05-15
Walt, I think this machine might just be so new it is not yet integrated with Ubuntu (read Brother haven't quite completed a foolproof Linux setup for it yet). From what I gleaned while researching this, the earlier models are genuinely plug and play with Linux. Brother have been very supportive of the community so good on them. We should support them I guess. And hey, at the end of the day I couldn't get it setup in Windows but I did get it up in Linux so now I'm going to head back to Windows with my own IP address in the printer and try again. There's a turn up for the books!

Go to Synaptics and do a search for Brother and your see what I mean. There are heaps of drivers in there ready to go. Just not one for my machine ... yet! Sure there will be before long and my HOWTO will be obsolete (perhaps by the time I get around to writing it).

Now I can get into the actual configuration of the machine but typing the IP into the address bar of Firefox I can access everything and am going to attempt to get the wireless happening so I can add that to the HOWTO also. 

Thanks for the kudos; yes, I am persistent. Some people say annoyingly so! lol There have been many threads of mine that are me rambling on to myself for a couple of days until I eventually crack it! But that's fine, good to talk to someone and hopefully someone will get something from my travails and triumphs. ;)

PS: Once the printer was working in the CUPS interface, I went back to System>Admin>Printing, the printer was there, and it was as simple as changing the 2060 driver to the 2270DW driver (which for some reason wasn't available in the CUPS setup). Prints even better now, dead centre of the A4 (was a little to the side with the other driver). I'm a happy Bucky.

---

### Post by jtdunc on 2012-05-03
> **walt.smith1960 said:**
> Check the Device URI under printer properties.  I've had something very similar in the past. The device URI started with DNSSD://something.  For whatever reason that address didn't work. I've found that socket://xxx.xxx.xxx.xxx where x=i.p address works most reliably for me.

URI to socket with IP address worked for me - thanks Walt.

---

### Post by biopower on 2012-12-23
I will weigh in here as someone who has had extensive experience (and frustration) with this exact printer. I have had several long phone conversations with Brother people. Here are a few lessons I've learnt:

*The printer is EXTREMELY SENSITIVE to changes on your router settings! Once I changed the channel from auto to 11 - FAIL. Once I changed the encryption from WPA2 to WPA/WPA2 mixed - FAIL. Some of these things I had even forgotten I did. It is just extremely sensitive to network changes. So it is connected to your network, but your computer can't ping it! That's the worst. 

*Holding the Go button down for ten seconds both prints the network settings page and CHANGES THE NODE TYPE. So if it's 'inactive' it'll go 'active.' This is important! Beware of this. A neutral way to obtain network settings is hitting go Three times, so print out all the settings. 

*In my experience the best way to deal with the situation is simply to put it into ad-hoc mode. Turn it off, hold go, turn it on, wait for the lights, let go of Go, then press Go six times quickly. (NOT SEVEN TIMES! That does something else -- although I'm seeing now that maybe Go five times within 4 seconds prints only WLAN page, which we want.) Anyway, pressing Go six times will RESET THE SETTINGS and put it into Ad Hoc mode. Then you can CONNECT TO IT USING YOUR COMPUTER. It's just called "SETUP." It broadcasts its own network. 

*Wait a minute. Press Go three times, (or five times?? haven't tried, per above). You get the IP. It's something like 168.254.23.78 or whatever. Then you punch that into your browser and bingo, you're IN the printer's admin page. u/p is admin/access. Go to printer settings, wireless config, find your home network, plug in your password etc. etc. (set the printer to Infrastructure mode of course). Then Big Brother is on the network. It boots you out of SETUP (the ad hoc network the printer made) and gives itself an IP. 

*Again, wait a minute and spit out the Printer Settings page again. Find the IP. Ping it to make sure it works. Then get onto it and go back into the printer settings. Now go to wireless settings, TCP/IP. GIVE IT A STATIC IP so it can't screw around. 192.168.0.X, or whatever you're setup at home on. 

*NOW BE REALLY CAREFUL ABOUT ANY CHANGES YOU MAKE TO YOUR HOME ROUTER. You can't mess with the security settings; you can't mess with the channel settings, you can't mess with anything, basically, in my experience, or you risk breaking your printer's ability to print.

*For a long time I kept thinking it was the printer randomly just giving up. Now I realised that much of the time I had made some change to the router and that caused it. 

That's all. Hope this is helpful to some one googling this.

---

### Post by Bucky Ball on 2012-12-23
Thread Closed

Reason: Necromancy. This thread is old and inactive and now asleep for good ...

@ biopower: If a thread has been inactive for two months or more, don't bother posting. Create a new thread. And please, mind your language. People of all ages and cultural backgrounds frequent these forums.

---

