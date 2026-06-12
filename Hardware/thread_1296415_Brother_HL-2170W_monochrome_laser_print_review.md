---
title: "Brother HL-2170W monochrome laser print review"
date: 2009-10-20
forum: Hardware
---

### Post by GiveLove on 2009-10-20
Hello fellow Ubuntu Linux users, :)

Here's my first attempt at a Ubuntu Linux compatible hardware user review. So go easy on me if my writing style needs some improvement. I'm not sure if I have the right forum category, so moderator feel free to move it where you think it should be. 

So my HP LaserJet 1100 monochrome laser printer of the last 13 years or so finally kicked the bucket. Between having driver problems with it in more recent versions of Ubuntu, and the fuser module and toner cartridge failing, I figured I should do the monetary math for me to fix it myself, versus buying a new printer. After a fair amount of research, I chose to buy the Brother HL-2170W. With shipping it would have been close to $125.00 USD (All monetary units in USD from here on)  to replace the fuser module and toner cartridge for the LaserJet 1100. The Brother HL-2170W with shipping included from Newegg.com costs $150.00. To me it made more sense to spend an extra $25 and get a new printer that will be more reliable as it is new, print almost three times as fast (23ppm versus 8ppm),  print at a higher resolution(1200dpi versus 600dpi), and data is transmitted faster to it via 100Mbps built in network interface versus 100Mbps network connection to a small dedicated hardware printer server (Zonet ZPS3603) that translates to a parallel port interface which is much slower. It also has a faster processor, and more memory at 32MB versus 2MB.

And obviously, I wouldn't be posting this here if it's printing functions were not fully supported in Linux. It can be connected to via USB 2.0, wireless B or G, or a 100Mbps wired Ethernet connection. Keep in mind you cannot use both wired and wireless connections at the same time. It's one or the other. So when one network interface is enabled, the other is disabled. Although I find it interesting that it can be connected via USB 2.0 and one of the two network connections at the same time and work properly. I'm not sure why you would do that. But interesting to discover. 

The other options for Linux compatible laser printers would have been HP or Samsung. My reasons for not considering them is that HP's printer division has been reputed to have gone downhill in quality and reliability over the years. In addition, whoever is writing their crappy printer drivers is either ignorant, the marketing division's puppet, or incredibly stupid, and their crazy business decision to make all their money on consumables. Hence ink and toner cartridges tend to be ridiculously expensive. Samsung would have been my next choice, but I've known them for many years now to have a terrible reputation for extremely poor customer service. So if something fails hardware wise under warranty, or you need tech support from a live human... Good luck with that! :P 

I have to say I'm very impressed with the amount of printer you get for $150 these days. Back years ago when HP was the printer king, something like this would have been in the mid end of the office/workgroup category. And would have costed $700, and more if you needed a network connection installed in it. To think my LaserJet 1100 costed $400 when I bought it new. And now $400 in the Brother line of printers gets you a high volume/duty cycle workgroup monochrome laser printer with paper tray options, or a top of the line multifunction monochrome laser printer. And a good thing to note, just from casually glancing at the model names, it appears that all their current printer line up is supported with Linux drivers, including the scanners of the multifunction ones. Which is fantastic, as scanners supported with working stable drivers for Linux via  Sane ( [http://www.sane-project.org](http://www.sane-project.org) ), is patchy at best. The interesting thing is, that the product specifications for the multifunction and inkjet printers say nothing of  Linux drivers for these models. Yet they do have drivers. But Brother officially does not provide customer support for them as I understand it. So they hide this information, and make finding the Linux drivers for them somewhat difficult. The way to find it is NOT to go right into the &#8220;Software Downloads&#8221; in the support section. Instead, under &#8220;More Support Options&#8221;, enter your product category and model. Then beneath that will display a column for &#8220;Drivers & Downloads&#8221;. Click on the last link in that column labeled &#8220;(Your printer model number) Main Download page&#8221;. This will open a new tab in Firefox. In this tab, there is a box on the left side slightly below the top labeled &#8220;Notes/Information&#8221;. At the bottom of this box is the link labeled &#8220;For Linux Users: Click here to get the Linux driver.&#8221; Not the most obvious way of finding it. To save you some time, here is a direct link for USA English users.
[http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html)

So far I'm very impressed with this new printer. They separated the drum and toner cartridges, unlike my old LaserJet 1100. So toner is less expensive at $46.00 for their high yield 2600 page count cartridge. Although, on the other hand, the drum unit is more expensive at $105 to $70 depending on where you get it, or at $50 if you buy an aftermarket drum unit. But it is only replaced after 12,000 prints. From my reading I've discovered that you can get much more than 2600 page prints from your toner cartridge by placing a piece of black electrical tape over the optical sensor hole on one side of the toner cartridge to fool the printer into thinking it is full of toner.
[http://www.fixyourownprinter.com/forums/laser/39806](http://www.fixyourownprinter.com/forums/laser/39806)
Here's a quote from two separate posts from the above link:

> My 5250DN informed me that I was "out of toner" at a page count of 3050 pages. I applied the fix above and now at the 4880 mark - not bad. I am now getting some "background" dusting / gray that is pretty evenly distributed over the entire printable area page.

Just to make sure there was not something else wrong I put in my new spare cartridge and it prints fine, so I guess at some point even toner still available something else is going on inside the cartridge... I understand there is some type of "toner recycle" mechanism in there that might be causing the dusting, but have never had one of these units apart.

If somebody knows of another way to clear up the background toner dusting let me know eh?

And here's the reply:

> Brother use a system of returning the residual print waste toner from the drum, to the toner supply hopper, via a charge brush which is in contact with the drum and charged differently during the clean cycle of the drum. The charged residual toner is transferred back to the developer roller and dropped back into the supply hopper. This is why most Brother cartridges, unlike most makes, do not have a waste toner hopper in the drum unit. When the toner is getting low, the electronics increase the charge on the developer roller to compensate for the mix of waste and good toner. This process continues until the maximum charge can no longer be accepted by the toner. This results in the charge brush failing to operate properly and hence waste toner is not returned to the toner hopper, but remains on the drum. This causes the backgrounding which appears on the printed page. Even blocking the low toner sensor will not prevent this from happening. This is a brief description of a rather lengthy complicated process. Submitted by Robbo.

A large number of people have reported that they can get many, many more prints (up to 1800 more) because of this, blocking off the toner level optical sensor, and possibly reseting the low toner warning depending on the model. Also, there is apparently a way to reset the drum count when it reaches 12,000 prints, assuming you are still getting good print quality. And there is what is called a primary corona wire on the drum unit that you can slide a plastic device across it multiple times to clean it if the print quality gets dirty. I've never seen this on a laser printer before. So perhaps this also can increase the amount of time that the drum can be used before replacement is necessary. 

And what I've also learned is that you can buy an aftermarket toner refill kit for about $27. But it only works on the high yield toner cartridge. Meaning, that the starter cartridge that comes with the printer cannot be refilled. 
[http://www.tonerangel.us/Brother_TN360_Toner_Refill-details.aspx](http://www.tonerangel.us/Brother_TN360_Toner_Refill-details.aspx)
This is fantastic as it is much less wasteful in resources, and less expensive! Apparently you remove  any old toner first, then just refill it with the new stuff.  This is the way it should be! In my mind, a good company should be pricing the printers higher to make a profit from that hardware, and leave the consumables refillable by the customer and low cost. 

Other nice features I noticed, if your printing thick stock or envelopes, by opening the rear exit door, the manual feed slot in front of the printer provides a straight path for the paper. So no more curled envelopes and cards. Although the manual feed slot is a one at a time thing that you have to hold each one by hand. But for my minimal printing needs that is fine. Also, because the paper lies flat in the pickup bin, I shouldn't have any more problems that the vertical paper bins that the lower end HP LaserJet printers had with the pickup rollers eventually failing and grabbing multiple sheets at once causing major jams. These were very common problems with these type of printers and a number of parts had to be replaced every once in a while to fix it. I only had to do it once during the lifetime of my LaserJet 1100. But it was never used anywhere near it's monthly duty cycle.

As far as initial setup and driver installation goes...
What I found out, was that if you do not use a DHCP server on your LAN such as I do. So that each computer/device has a permanent IP address. You unfortunately may still require a separate piece of Windows software that is not a part of the drivers to change the printer from DHCP to static, and to enter it's permanent IP address. Although it would be easy enough to get around this in Linux by temporarily enabling the DHCP server in your router and enabling DHCP on one computer, just long enough to log into the printer's web based management with your browser, and change the settings there. It's just more of a hassle. I found out the hard way that you cannot install the bare printer driver for Windows XP professional, as the printer firmware updater will not work. The trick was to install the driver from the included CD, which fortunately was the same version as what was available on Brother's web site, but unfortunately it installed a bunch of other stuff that was not needed, such as a status monitor, manuals, toner level check software and an uninstall shortcut. Not a big deal. At least it is not like what I hear HP Windows drivers are like in that it installs all sorts of crap software that most people don't want or need. Once I did this I was able to run the firmware updater, which I find out the firmware is not part of the download, it is just a generic firmware updating software for all their printers and it looks over the Internet for a more recent version, which there were none for mine. I'm not sure this approach is the greatest idea, as it would have saved me a bunch of time if the information as to what is the most current firmware version was placed on the same page as the firmware download. As I already knew what firmware version the printer had from printing out its &#8220;settings&#8221; pages. (Press the &#8220;Go&#8221; button three times quickly) I'm used to updating firmware on CD/DVD writer drives and dedicated hardware routers where the web site tells you what version it is and you download the actual new firmware. So it's simple and quick to compare installed versus new firmware versions without going through the install process. The link for the current firmware revision is in that same &#8220;Notes/Information&#8221; box that the link for the Linux drivers are. I cannot post a direct link, as it is a generic link that depends on the web site knowing which printer model you are looking at in the support section of the web site. 

The only reason I bring up the Windows driver install experience here, is because the firmware updater software for the printer is Windows or Mac OSX only. Which sucks. :( As you technically cannot currently use Linux operating systems only with Brother printers, unless you do not want to update the firmware. Although, the interesting part is that the firmware updater uses Sun's Java runtime environment which can be installed in Linux. So it makes me wonder if perhaps it might still run in Linux if there was a way to extract the jar files from the downloaded exe, or dmg for Apple. At the very least,  hopefully Brother would do so in the future with minimal programming changes since Java programs are supposed to be cross platform. 

So anyways, installing this printer in Ubuntu 9.04 was painless. It found and recognized it almost immediately. There was no choice of driver. It just installed what it had. And it printed just as beautifully as in Windows. Just because I was curious if there would be more features supported, I deleted the printer, downloaded and installed the cupswrapper .deb file from Brother's web site, installed this .deb file, and then reinstalled the printer. It still did not give me a choice of drivers to use. So I'm not sure if it used the new driver I installed, or made a difference. I have no idea if these drivers are open source.  It would certainly be nice if they were. But the fact that Brother is even making their own Linux drivers for their printers is a huge step forward and worth supporting them because of it.

---

### Post by GiveLove on 2009-10-22
Hello People, :)

I thought I would add a few other things that I forgot. 

One nice feature I like that may not seem obvious to other people, is that it actually has a On/Off power switch on the lower right side. And this is a real switch that shuts off complete power. Not a flimsy button that just puts it into a sleep mode, while it still draws power. This is great, as when it comes down to it, I probably print no more than 10 pages a month. Often times less. So the majority of the time there is no reason for the printer to be powered on, even if it is in sleep mode. You may think big deal, a power switch. But all the low end vertical paper bin HP LaserJet's that I've owned, used or setup over the years never even had a power switch. So they always used electricity for no reason when not printing. So unless you make a conscious decision to plug it into a six outlet AC power strip with a power switch on it, so as to keep it shut it off when it is not needed, it's always using some electricity. 

And in my case I had mine plugged into the AC power strip that my computer was plugged into, so when my computer got powered on, so did the printer and it's attached print server, regardless of whether I actually used it or not. Which the majority of the time was never. But it would still go through that initial fuser warm up and readiness cycle when you first turn on the printer, rotating the drum in the cartridge a cycle and basically causing extra wear and tear when it wasn't even used. As my computer gets powered on and off several times a day, and gets used for hours at a time. 

Related to this is it's electrical power usage. It's quite high both in printing and standby. I've noticed at night the lamp by my computer flickers as it starts printing. Which did not happen with my old HP. But I'm guessing this is a trade off to get higher print speeds. Here's the specs:

Printing - Average 460 W at 25 °C (77 °F)
Standby - Average 80 W at 25 °C (77 °F)
Sleep     - Average 8 W

And for comparison, the specs for my old HP LaserJet 1100:

During printing: 200 watts (average)
During standby and power save: 6 watts


The next issue is noise. While it is subjective as I'm not measuring anything, I find this printer to be much noisier when printing than my old HP. I think a lot of this is because it is actively cooled by a fan on the right side, where as the LaserJet 1100 was passively cooled. (Which reminds me, Brother states you need at least four inches of clearance on the right side of the printer to allow for proper cooling. Something to keep in mind if you are trying to keep it in a tight fitting area.)  So while the noise figures for the Brother printer are lower than the HP, I find it a lot louder as the fan has quite a bit of a whine to it in addition to the rest of the motor and mechanical noises during printing. Keep in mind that volume figures don't really tell you a lot when comparing between brands. As they don't tell you under what conditions it was measured, how far away the microphone was positioned, and what the initial noise floor was. So in most cases you cannot compare the data. I can say that I wouldn't want to be around this if it was constantly printing all of the time, as it sits just to the right of my monitor. Fortunately during standby the fan revs down to a barely audible level. And in sleep mode turns off. And I keep mine powered off most of the time as it is not used often. Here's Brother noise specs:

Printing 51 dB (A)
Standby 30 dB (A)

And HP LaserJet 1100 for comparison:

Sound pressure level (operator position): 55 dB
Sound pressure level (bystander position): 47 dB
Silent during standby and sleep mode


That's all I can think off for now. If anyone has any questions on something I did not cover already, feel free to ask.

---

### Post by ethanay on 2010-02-04
Thank you for this review!

I just bought and set one up to work wirelessly.  It was detected and installed flawlessly.  The web interface is VERY comprehensive.

Some additional notes:  

1. Does not work with IPP; use LPD or AppSocket/JetDirect, I suppose:
[http://ubuntuforums.org/showpost.php?p=8424667&postcount=25](http://ubuntuforums.org/showpost.php?p=8424667&postcount=25)

2. Only prints up to 1200 dpi (best quality).  Driver(/firmware; see #3 below) isn't compatible with 2400 dpi yet.  Not a HUGE deal for me.

3. Tried to download and install Brother's printer drivers on one of the computers; did not work. AFAIK, the only options that are missing are paper selection (thick, thin, recycled, transparency, etc) and 2400 dpi printing.  Paper selection is available via the web interface.  Curiously, the web interface says that only 1200dpi is available...

4. Potential problem:  If in sleep mode too long, it may fail to wake(?), requiring an on/off cycle. I think I experienced this once already.  See comments [here]("http://http://www.macintouch.com/readerreports/printing/topic2852.html") (page search: "sleep") re: the HL-5250DN.  Rather than power off/on, pressing the "Continue" button may also work.

---

