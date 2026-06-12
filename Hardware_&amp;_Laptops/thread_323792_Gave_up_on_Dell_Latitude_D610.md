---
title: "Gave up on Dell Latitude D610"
date: 2006-12-22
forum: Hardware &amp; Laptops
---

### Post by nicolas314 on 2006-12-22
When I received this new laptop at work more than a year ago, I immediately installed Ubuntu (Breezy), knowing I would feel at home. I upgraded it shortly after to Dapper when it was released and stayed with Dapper until today. Net result: forget it.

The CD/DVD drive is not correctly recognized. CDs are only seen when the machine is booted with them being in the drive, which means a new reboot every time you insert a new media. Not cool. Browsing forums, I found out you have to add libata atapi_enabled=1 to the kernel boot line to make it work, but this only half-worked. The first CD you insert is correctly seen, the second one crashes all processes that try to access it. If I really insist I get kernel oops so will have to reboot anyway. When the CD/DVD is finally recognized, I found out the speed is quite not up to the one observed with the other OS. Tweaking hdparm parameters did not help. Gave up on reading CDs on this laptop.

Wifi support is lame at best. Breezy at least could use WEP, Dapper never worked for me in WEP or WPA mode, and only sometimes did in unencrypted mode. Setting up wireless is always a matter of playing with several utilities and it is definitely not the kind of task I am up to when I want to reach the Net in an airport. Since the latest updates, Wifi support just blacked out on this laptop, even on totally unencrypted networks. The Wifi LED on top of the keyboard has never worked. While it might seem like a superficial feature, having a LED to indicate your wireless status is extremely important on a laptop: I want to know always whether my machine might be subject to wireless attacks by just watching this LED without having to reach for a command-line. Shutting down Wifi is also a good way to stop loosing battery time uselessly.

Bluetooth can be made to work. I spent several hours figuring out how to do it with ample help from Google and friends but all solutions I found required putting together several scripts and pieces which I forgot to document. Next time I wanted to use Bluetooth on that laptop I just gave up.

The hard disk makes this incessant sizzling noise, does not with XP. I found some reports about this issue and applied the given solutions, to no avail. Spending a whole day in front of a noisy machine is tiresome in the end.

The screen has this rather exotic 1400x1050 resolution, for which I had to apply patches to the BIOS and play around with X.org configuration for a while. This worked in the end but it is really an ugly hack. Why is it not possible to boot directly with the correct resolution is beyond me.

Hooking up a second screen to use an extended desktop is far from easy. Tweaking X.org configuration, I could end up with a working setup but Gnome is obviously not programmed to support this. Icons tend to end up on the most unexpected side of the screens, and when you go back to single-monitor configuration you discover that all icons are still on the other (switched off) monitor. Not a bug, but in the end you just do not bother with plugging in another screen.

Fonts have been extremely hard to get right. The screen is rather small and using anti-aliasing on small fonts has just killed my eyes. After switching to huge fonts for everything, I got tired of it and cried for more screen real estate. Took me hours to find out how to deactivate anti-aliasing and get the correct set of fonts to be able to work on this screen all day long. This is not specific to my laptop, but the issue is definitely important for these little machines.

The keyboard has two extra mice: a little button in the middle of the keyboard and a sensitive pad below. None of them works correctly. Might just be my hardware, but it works fine with XP and not at all with X: the cursor keeps slowly reaching for the upper left corner, making it unusable. I had to deactivate these extra mice to be able to use X. Probably nothing serious but adding up to the rest, getting on my nerves a little bit.

Sound support is good. The dedicated buttons on top of the keyboard are working fine. Breezy had trouble with them (they were basically useless) but Dapper works fine.

I did not try infrared.

From a general point of view, a laptop is a machine that is thrown around about all day long and thus needs to be able to hook onto any kind of network, be it wireful or wireless. I found out that overall network support is just a little better than what you got with the previous system obviously aimed for a never-moving desktop, but hardly. In a meeting room I have a choice between booting Ubuntu and spending the next 15 minutes trying to get network parameters right (with several phone calls to IT) or boot XP and get my network up and running without touching a button.

Still from a general point of view, when you work with a bunch of people who are still convinced Microsoft Office is the only possible way to save their business data, you fall behind with OpenOffice support for these documents. I have always been the guy working on Linux, the only one to have trouble opening a document and whose documents cannot be read by anybody in the team. OOO is a great piece of software but until people are educated about proprietary file formats there is no better solution than use the only 100%-compatible tools. Same thing applies to e-mail: corporate wants us to use Outlook and Exchange for e-mail and calendars and Evolution just does not fit the bill. It only tries to imitate Outlook and does a really poor job at it. There is no extra feature worth mentioning, the interface is ugly, exchange support is buggy, documentation is lame, and it takes 3 processes and massive amounts of RAM to just read my e-mails with it. It might get there some day but right now it just does not cut it. One extra point worth mentioning: I need to encrypt all e-mail data and Evolution does not support saving its data to an encfs filesystem (despite the documentation telling the opposite). There are other solutions of course, but Thunderbird did not have trouble doing the same.

Today I totally removed Ubuntu from my laptop. After spending a year struggling with it, I finally had to give up and turn to a more productive solution that does not eat up all of my time. First time ever I uninstall Linux from a PC believe me, but I felt relieved as it disappeared from the disk.

I still have a couple of Ubuntu desktops I can access to if I need to get some real work done anyway. I believe Ubuntu is just no fit for this laptop in a corporate environment. Your mileage may vary.

---

### Post by njreid on 2007-01-05
Hi nicolas314,

I've been running subsequent versions of Ubuntu on a D610 in a corporate environment for about 18 months, and whilst a number of issues you mentioned are real I've found it pretty successful - certainly better than wrestling with XP.

I agree about OO - It's good, but not yet quite good enough for a complete MS Office replacement. You simply can't guarantee that a Word, Excel or Powerpoint document created or modified in OO will look exactly as it does in the equivalent MS application. Sure, it's usually good enough for internal documents, but who wants to send customers documents which aren't going to look professional? 

I typically still fire up MS Office products in a VMWare machine for sensitive editing. Used to use cxoffice, but found it to be not quite rock solid enough.

That said, it's improving by leaps about bounds - Subjective memory consumption, compatibility and general GNOME-ishness in 2.0.4 is a big step up from 2.0.3. 

You mention using Dapper - Did you try Edgy? I'm struggling to recall now, but I'm pretty sure the 915resolution 1400x1050 hack is included by default in Edgy. Also, recent work on the 915 driver means the hack won't be necessary moving forwards.

I also had problems with WiFi, particularly in Dapper as that was the first of the bcm43xx releases, replacing the old crufty approach. Edgy, however, works beautifully with NetworkManager - automatically selects wired or wireless connections, supports both WEP and WPA1; not sure about WPA2 support as I've not needed it yet.

Anyway, just wanted to suggest that you give Edgy a go, at least in dual-boot, to see if it works better for you. 

Nic

---

### Post by nicolas314 on 2007-01-05
Hi njreid,

Thanks for taking the time to answer me on that topic. Cool to know that I was not the only one struggling with that hardware. To answer specifically on the topics you pointed out:

OOO and MS Office: I would *never* send any MS Office document to a customer. Too many untold stories are hidden into these files. You have no idea what was done with history, removed text that is still there but hidden, or things that could be undone in the file  like showing all your attempts at setting a final price for the customer, or showing clearly that the document was cut'n'pasted from another customer you do not want to reveal. I am paranoid and only send PDF files or paper prints to outsiders. Proprietary formats with undocumented features are just too dangerous. And for internal documents, the gig stops as soon as I am the one editing a file in the team so forget it. Either I work or I struggle with file formats, cannot do both.

Granted, I have not tried Edgy on the D610. Edgy has crashed both my home computers (an old PPC and a Sempron) so badly I was really thinking into going back to Debian. I am still facing a large number of issues that make me nervous about installing that at work. Maybe I should have? At least I could have gotten network to work properly, maybe?

My D610 is now permanently damned with XP. I will have to make do with Cygnus stuff.

Thanks again for sharing some thoughts. Wishing I could dual-boot the machine some day.

---

### Post by Invid on 2007-01-14
Posting this from a D610 running Edgy right now. I really think that if you should feel up to it, you should definitely give it a try on your machine. My experience was quite different from yours with all of my hardware working out of the box, save the aforementioned resolution problem. That problem was solved for me by installing the ATI binary driver, which automatically enabled my native resolution and allowed desktop compositing. 

One area where we may differ that has a great influence on usability is wifi. I selected the centrino chipset combo when I configured the machine, and I am certain that had a positive effect on my wireless experience. That said, I do have a desktop at home that sports a broadcom chipset (BCM4306) that has been rock solid after a PITA initial setup.

I guess I am trying to say that hardware support is improving almost daily and Edgy will likely give you a far better experience on your machine than Dapper did. Good luck should you re-install.

---

### Post by nicolas314 on 2007-01-15
Thanks for the warm recommendation, but it does not cut it. I have been patient enough to struggle for one year with this, enough investment! Sorry thing that a brand new laptop has to wait for more than a year to finally get proper support from an experimental distribution (Edgy is experimental, Dapper is supposedly the stable one).

No worry though: among the dozen machines I am managing, this is the only one that suffers from the other OS. With a little bit of luck, Ubuntu might become a D610-ready OS before the machine goes completely obsolete?

Will keep in mind it is not impossible ;-)

---

### Post by Beau D. on 2007-09-16
Interesting thread. I too am running a D610. My results are far better than yours. My wifi works anywhere, my LED works (sure I had to make a couple of tweaks). This is my main computer..for home/work everything. And I have to say Feisty installs like a breeze on this machine, works great out of the box..and does everything quickly (1.8 Pentium M, 1 gig DDR2 533 RAM, Intel 915GM graphics). I have done alot of tweaks to it..for speed, battery life etc. I am 100% happy with it though. Boot time is down to 45 seconds, the wireless is dead reliable..not to mention the gigabit ethernet. Automounts all my devices (ipod, etc)..and does everything better than XP can. I wish you luck down the road..and maybe you can give feisty another try. I'm personally going to forgo the 7.10 upgrade..unless I found out something new..and wait for the next LTS release. Being a full time linux user who doesn't dual boot Windows of any type, and doesn't allow it in his house (lol)..functionality is tops on my list followed by security.   Feisty for me on this machine does all of it in spades. Maybe down the road you can give it another whirl. 

Beau D.

---

### Post by nicolas314 on 2007-09-18
Hi Beau:
Would you mind providing some inputs as for tweaks you had to perform to make Ubuntu fit on this laptop, e.g. for Wifi, LED, CD-ROM, Bluetooth, external screen with extended desktop, multiple pointers (keyboard mice), fonts, battery management? Just in case somebody else runs Ubuntu on such hardware, it would be a real time-saver.
I guess the issue will be less and less important with Dell providing Ubuntu-based laptops in the future.

---

