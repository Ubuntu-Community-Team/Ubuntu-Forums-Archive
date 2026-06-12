---
title: "hp LaserJet 1000 problems (and a minor rant)"
date: 2005-03-28
forum: Hardware &amp; Laptops
---

### Post by Michael T. Richter on 2005-03-28
I'm trying to get people in my office to slowly switch away from the world of Microsoft.  This has been uphill work mostly because of the truly sad state of affairs on the desktop/end-user front in Linux (the only credible alternative to Windows out there right now).  Indeed I had given up on Linux in any reasonable timeframe and just went back to living with the Microsoft hegemony.

Then I ran into Ubuntu while researching live CDs for a private project.

I was very impressed with Ubuntu at first.  The installer was ugly, but it, you know, worked.  (This is in sharp contrast to, say, Anaconda which looks pretty but does bizarre things that are very off-putting to the average end-user.)  Further, upon installing Ubuntu (4.10), I was impressed by how easily I could find the things most people need from a computer and, further, by how easily I could find and install the things not present out-of-the-box.  I decided to repartition a computer at work and install Ubuntu.

This computer has an hp LaserJet 1000 connected to it via USB.  For long, involved reasons I don't want to get into it wasn't available to me at the time, so Ubuntu went on without me testing the printer.  My coworkers' oohs and ahs were nice as they looked at the system and played with it.  ("You mean this is all free?"  "Every bit of it."  "But it's so fast!"  "Yes, because it's not using all the system's resources to do pointless things."  ...)  Then the day came when the printer was once again available.

Disaster.

I plug in the printer and.... nothing.  Now here begins the slight rant.  If you're a committed "Open Source" fanatic to whom any hint of criticism of the Linux/GNU/whatever world is a personal affront that requires direct attack as a response, this is no longer a message that you will want to read.

Let me explain to you what happens in the Windows world when you get a new piece of hardware based on standard protocols, etc.  (You know, like USB disks, printers, etc.)

Step 1: you plug it in.

Step 2a (optional): if the OS doesn't have native support for the device, you insert a disk.

Step 2b: it works.

This is the way things are in the Windows world barring the pathological cases that spring up here and there.  I can go to the "computer city" here in Wuhan and buy any piece of USB (or Firewire or PCI or PCMCIA or CardBus or whatever) hardware and it follows that model.  I plug it in.  I optionally insert a disk.  It works.

This is the way things are in the Windows world **and this is what the average user expects from their computer**.  You plug it in.  You optionally insert a disk.  it works.

This is not what happened, however, when I plugged in my printer.  I plugged it in and.... nothing.  As far as the system was concerned there was no change to my peripherals.  This was not exactly a surprise to me (considering the utter contempt most programmers seem to hold end-users in), so I was prepared to have to tinker a bit to get things working.

My first visit was to Computer->System Configuration->Device Manager to see if the printer was even listed.  Sure enough I have the chain Computer->80821BA/BAM USB (Hub #1)->Intel Corp. 80821BA/BAM USB (Hub #1)->hp LaserJet 1000->USB Printing Interface.  That looked promising, especially the last part of the tree (USB Printing Interface).  (I also inspected all the assorted USB parameters in the Advanced tab for all the relevant devices and found nothing weird or unexpected.)  So onwards I went.

My next visit was to Computer->System Configuration->Printing.  The window opened and I have a "New Printer" icon upon which I double-clicked.  Up comes a "wizard" entitled "Add a Printer".  It lists two printers (the hp and a PDF printer), so I click on the hp LaserJet 1000 and go forward.  Here, peculiarly, despite already having the information on-hand, the system asks me for the manufacturer and model.  (Remember that "utter contempt" thing I was on about earlier?  Can anybody explain to me why the programmers don't **maintain a database of USB device names to manufacturer/model names so this next step isn't needed/!?!?!**)  Shrugging my shoulders I supply the information.  HP as manufacturer, LaserJet 1000 as model.  I select the "recommended" driver, the foo2zjs (at first -- in later experiments I selected the other to no noticable change).  Then I click "Apply".  Happy, happy, joy, joy!  I now have a printer in my Printers folder!

Being the cynic that I am (and not just about the Unix-like world), I want to test the printer.  I double-click the icon and get rewarded with the job list.  Brief experimentation finds me the "Print Test Page" menu entry which I quickly employ.  A dialog box pops up smugly informing me that it's sent an A4 page to the printer.  the first signs of trouble, however, are there: the dialog pops up, but nothing shows up on the jobs list....  And, you can guess by now, nothing ever shows up on the printer.  There's not even a hint that anything got SENT to the printer.

Now I'm worried.  I'm losing face with my colleagues by being stymied by the single most basic function a computer can supply in our world here (education): printing.  There's no point in making presentations, reports, documentation, hand-outs, etc. **if the damnable things can't be printed!**  So much for wowing the natives with Ubuntu!  Desperately I try to figure out what may be going wrong.  I open up the Printer->Properties and look around the settings to see if there's anything that leaps out at me.  Nothing does.  I do fill in the "location" field, however, and close the dialog.  I try to send another test page.  Nothing happens.  I re-open the properties pages and...  Weird: the single, trivial change I made **hasn't been saved**.  I experiment.  I change all of the settings around.  Letter instead of A4 (just for the hell of it).  Location.  Printer description.  I add or modify every field.  I close the dialog.  I re-open.  Back to square one.  Not a single change has been recorded at any point!  (Later experiments that change practically every field in the configuration confirm this: nothing is changed by the properties pages.)

Suspecting that I might have broken something while installing things through Synaptic, I plunk in the Ubuntu 4.10 LiveCD and try again.  Same behaviour as before -- the printer does nothing.

Searching the Ubuntu (and later other) forums has given me zero succour.  My printer sits there like an overpriced and oversized paperweight.  There's no clue whatsoever how to fix this problem.  Any credibility Ubuntu had in my colleagues' eyes as a Windows desktop replacement has evaporated as this unfolded.

And, to be blunt, the credibility has vanished (or at least diminished significantly) in my eyes as well.

Back to the rant that will offend the Open Source fanatics of the world (as opposed to people like me who think there's promise in Open Source that is as yet unfulfilled).  If you **ever** want Linux (or other Open Source projects) to be taken seriously outside the world of fanatics and the choir, you need to start looking at things from the **user** perspective, not the hobby-hacker/system-tinkerer perspective.

It really doesn't take a lot of effort to provide functionality to a software system if you have even a modicum of programming talent.  It **does** however, take a lot of blood, sweat and tears (and taste and empathy and education and a whole host of other characteristics) to make that functionality accessible outside of the hobbyist/tinkerer world.  Whether you like it or not, the average user doesn't want to have his life dominated by tinkering with his computer.  The average user wants...

...what he gets from the Windows world.  You plug it in.  You optionally insert a disk.  It works.

Excuse me, now, while I shut down Ubuntu, switch over to my newly-installed Windows XP SP2, plug in my printer and have it work.  I look forward to the day I can switch back to my Ubuntu partition and use it instead.

---

### Post by mercurus on 2005-03-28
The problem which you have articulated at length is one which Ubuntu has largely been created to address.

Barriers to Ubuntu fulfilling this Plug and Play philosophy:
- the linux kernel: often device support is reliant on kernel development. The newer the device, the less the likelyhood that a kernel hacker has had time to write or port a driver. Ubuntu is fixed to the linux kernel, so there will always be a slight lag there. (That said, for my SB Audigy2 Value card, there was less than a week between my purchase and the release of 2.6.11 and support)
- manufacturers produce devices with drivers for the most commonly used operating systems. Until linux has a BUSINESS userbase that competes with closed source software platforms, the return on support services in that market is neglible, and therefore no support is offered. It isn't economically viable (yet) for manufacturers to support linux.
- access. Because of the economic and time restrictions mentioned above, it is often difficult for kernel hackers to gain access to the information they need to make drivers available for new devices. Without regular, unfettered access to the people designing products and proprietary drivers, it is very difficult to progress in supporting hardware.

These factors, when combined, make a significant hurdle for any operating system. Apple solved it by limiting the hardware for which they need provide driver support. Windows fixed it by gathering a huge home and business user and support market, making it economically essential for any product to be supported. Linux needs to find a new way - and Ubuntu is a bloody good start.

Ubuntu makes much of the nitty gritty happen, while still keeping a smiling face. It keeps the core software as up to date as possible, with a focus on specific packages. Ubuntu's strategy (appears to me to be) a focus on a fixed, core set of applications that do not break. By having a stable core, it is possible to maximise the amount of hardware that works with those applications. Obviously the kernel is still a huge limiting factor, but at least when the kernel is updated - you KNOW the applications will still work.  

It isn't there yet, but it is a bloody good start. My printer is broken at the moment, I'm working on fixing it ... but when it is fixed, it'll work until I break it - not when I make something else work. I'm sorry you've had issues with your printer, I'd be happy to walk you through some of the techniques I've tried with mine ... drop me a message, if you're interested.

Cheers and best of luck
mercurus

---

### Post by Michael T. Richter on 2005-03-28
> **mercurus]The problem which you have articulated at length is one which Ubuntu has largely been created to address.[/QUOTE]

I realise this.  Hence my utter shock at something as mundane as a USB printer failing so dramatically out of the box.  **Everything** else up to that point had worked like a champ.  Then, suddenly, the single basic function required of practically every computer user -- persistent output -- fails in such an intensely frustrating way.  It was dispiriting (to put it mildly).

> Barriers to Ubuntu fulfilling this Plug and Play philosophy:
- the linux kernel: often device support is reliant on kernel development. The newer the device, the less the likelyhood that a kernel hacker has had time to write or port a driver.  Ubuntu is fixed to the linux kernel, so there will always be a slight lag there.

This particular printer has been here in my office in Wuhan for longer, I think, than Ubuntu as a project has been alive.  (I have been here for over a year and a half and it was an old printer when I walked in the first time.)  This is a LaserJet 1000 we're talking about.  I had a LaserJet 1100A (if memory serves) back in Canada over four years ago.  This is not obscure nor bleeding-edge hardware.

Tonight I'm going on the home system that has an Epson colour printer (over two years old) attached -- also via USB -- and doing a trial with the liveCD.  I know what I'm expecting after this dispiriting effort.

> These factors, when combined, make a significant hurdle for any operating system. Apple solved it by limiting the hardware for which they need provide driver support.

And their astonishing growth is nothing short of incredible, isn't it?  said:**
> Linux needs to find a new way - and Ubuntu is a bloody good start.

Amen to the first and a qualified amen to the second.  While Ubuntu's image has been tarnished in my mind with such a fantastic cock-up, it is the only Linux which has actually survived on a system I regularly use for longer than a month.  That is a feat unparalleled in the history of Linux.  Even with this latest development I'm willing to sit back and adopt a "wait and see" attitude instead of shrugging, trashing the partition and returning to Windows for the next year or so before trying out the Linux world again.

So I still view Ubuntu as having some hope.  I'm just a little shocked that something so basic broke so blatantly.

> It isn't there yet, but it is a bloody good start. My printer is broken at the moment, I'm working on fixing it ... but when it is fixed, it'll work until I break it - not when I make something else work. I'm sorry you've had issues with your printer, I'd be happy to walk you through some of the techniques I've tried with mine ... drop me a message, if you're interested.

Thank you for the offer.  Consider it taken up (and take a peek in your PMs).  I'm slowly getting back into software development mode myself, so I may personally address a couple of the issues I have with Ubuntu (like not having a database of printer names to manufacturer/model pairs).

---

### Post by David Haas on 2005-03-28
At present Ubuntu and all other distributions of Linux often require users to do more to set up printers and other devices than one would expect to do in Windows. This takes patience and some study. but don't be hard on the programmers, who are terrific and are coding without remuneration. Linux will surely become more and more user friendly year by year. 

I had to work to get my Epson Stylus C82 operational. Now it runs as well as in Windows. But at first it sat mute (dead to all appearences) even though Linux recognized it as present. The files for your HP laser are almost certainly available in Ubuntu, but need to be installed--I say "almost" because I've had no experience with this printer. I see that the laserjet 1000 and the ppd (postscript printer description) file are available in Ubuntu Warty.

(Turn on your printer before the computer for ease of recognition.)

I recommend that you first work in "Synaptic Package Manager" to make sure that CUPS (common unix printing system) is installed on your computer. To get to Synaptic, click "Computer" at the top menu bar, then "System configuration," and then "Synaptic Package Manager" (type in your password to be in root). In Synaptic, first click "settings" and then "repositories." Enable all the repositories. This will allow you to install via Synaptic the necessary files, if they are not yet installed.

Then go to the cups  packages in Synaptic--It's quickest to set the left column in Synaptic as "alphabetic". Here you'll see "cupsys, cupsys-bsd, cupsys-client, cupsys-driver-gimprint, and cupsys-driver-gimprint-data". If not marked as installed, install all but cupsys-bsd (I'm quite sure that this latter isn't needed--bsd is an old "flavor" of unix) 

Next, make sure that all the "foomatic" packages are installed. This is a big database of filters for almost every printer, including yours. 

Now click "computer > system configuration > printing. If you already have a printer icon there listed as HP Laserjet, right click on it and select properties. If not work to add a printer to "Newprinter." In the properties dialog box, select the Laserjet 1000 (it's listed) and then click "install driver". Here is where you select the PPD file. The ppd file is present in my Warty, but it's listed as HP-Laserjet_1000-foo2zjs.ppd.gz. It's in the directory "/usr/share/cups/model/foomatic-ppds/HP. So it should be selectable within the "printing" GUI. To locate it, you'll need to work through the directory system. Click on "Filesystem". Then select the following directories in order: usr>share>cups>model>foomatic-ppds/HP. In this last one scroll down to HP-Laserjet_1000-foo2zjs.ppd.gz and select this for your PPD file. 

Before I did all this, my Epson stylus C82 was dead (mute). When Ubuntu (or other Linux distros are operational, they are very stable and free from spyware, viruses, and (essentially) crashes. And Ubuntu is free! Preparing a fine meal may be better for you than fast food :)

---

### Post by Michael T. Richter on 2005-03-30
[QUOTE=David Haas]And Ubuntu is free![/QUOTE]

](*,) 

This is irrelevant, largely, and not a good choice of sales techniques if you're trying to sell colleagues on switching away from the Microsoft world.  "Sure, the single most important thing you need from your computer doesn't work right without interminable, badly-documented fiddling, but at least you didn't have to pay for it!"  They didn't pay for Windows either.  The school did.  And hiring someone who is intimately familiar with the traditional UNIX magic incantations is a **hell** of a lot more expensive than is simply buying a few Windows disks.

---

### Post by hashimoto on 2005-03-30
First I must say that I have exactly the same experience with HPLJ 1005. It just doesn't print anything no matter what I do. It is dead as far as Warty is considered. Haven't tested it yet with Hoary.

Yet, looking at [http://linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1005](http://linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1005) it should be "mostly" operational. The same applies to your HPLJ 1000: [http://linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1000](http://linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1000)
The question is why does it not work in Ubuntu at all. Go figure. I don't have the expertise to dig into this but I think there may be something broken in Ubuntu's CUPS.

However, a possible CUPS fault is only half of the problem. You should rather point your finger at HP who does not provide linux drivers to their printers. The ones used are painfully back engineered by volunteers without support from HP. Non-functionality is not the fault of the fine people who provide us with Ubuntu and the drivers. I'm sure they have done their best.

---

### Post by wildfox on 2005-04-12
Hi!
Huh, the Laserjet 1000 is a tough one. First of all setup the printer in Printing.
It has a faulty firmware or something, so the driver has to upload it. Actually in windows everytime you print it does.
In Linux you have to download the sihp1000.img file (try google for it or i can upload it for you also) and then type: "cat sihp1000.img > /dev/usb/lp0" (it might be lp1 you will hear your printer 'working').  You will have to do this on every reboot.
So thats how i got working the printer in warthy. However I upgraded to Hoary (i love it..) but now i can't get the printer working with same method. Any help? 

Btw I'm very angry about hp that they can't provide linux drivers for their printers.

---

### Post by antilog on 2005-07-03
[QUOTE=wildfox]Hi!
Huh, the Laserjet 1000 is a tough one. First of all setup the printer in Printing.
It has a faulty firmware or something, so the driver has to upload it. Actually in windows everytime you print it does.
In Linux you have to download the sihp1000.img file (try google for it or i can upload it for you also) and then type: "cat sihp1000.img > /dev/usb/lp0" (it might be lp1 you will hear your printer 'working').  You will have to do this on every reboot.
So thats how i got working the printer in warthy. However I upgraded to Hoary (i love it..) but now i can't get the printer working with same method. Any help? 

Btw I'm very angry about hp that they can't provide linux drivers for their printers.[/QUOTE]


I get:
sudo cat sihp1000.img > /dev/usb/lp0
bash: /dev/usb/lp0: Permission denied

so i changed the permissions and got
cat sihp1000.img > /dev/usb/lp0
bash: /dev/usb/lp0: Device or resource busy

cycled the power + reconnected the usb and got the same thing

any ideas?

---

### Post by antilog on 2005-07-09
still cannot get this working, have been spending hours on this

---

### Post by antilog on 2005-07-11
i finally got this working, but not directly.

i had to connect the printer to my Windows machine and share it to my Ubuntu machine.

---

### Post by cilynx on 2005-07-17
I can get away with:

$ lpr sihp1000.img 

to upload the firmware.  (as opposed to having to cat to the device.) 

This printer is amazingly stupid, but what do you expect out of a $200 laser printer?  If you try to send it a job (anything at all to print) before you send it the firmware, it locks hard.  The only way to get it back is to power cycle the printer.  However, make sure you flush your print queue first or else once it's back online, it will once again receive the queued print job instead of the firmware it needs first.

As a workaround to proper initialization, you can tack 'lpr sihp1000.img' into your boot scripts somewhere or else find the spot where USB recognizes the thing and try to get it to load the firmware there.  (In this case, the cat method may be better as lpr will just add the firmware to the queue requiring a queue flush as mentioned earlier but 'cat' sends it direct)  Another problem is that if you upload the firmware twice, the printer once again locks hard.  I know this is all hacker-y and not very user-y, but for those of you just trying to get the thing working for your own good, it works.

Still holding out for easy printing...

   -r

---

### Post by S.nazari on 2005-07-25
Hi... I have been having the same problem... could you let me know where you found the file....  :)

---

### Post by antilog on 2005-07-25
[QUOTE=S.nazari]Hi... I have been having the same problem... could you let me know where you found the file....  :)[/QUOTE]


read this

[http://linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1000](http://linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1000)

i couldn't get it to work, but it may work for you.  i had to connect the printer to a windows machine and network to it

---

### Post by tigrez on 2005-09-18
I have the same problems with hp 1005 laserjet, but I have resolved with re-installation of the foo2rjz drivers with Synaptic.

---

### Post by cilynx on 2005-12-05
The meat of the linuxprinting article on the lj1000 is this:

 1. Get new firmware from HP site
   (this is bloat download ~12MB but we need only ~115kB from it)

   [ftp://ftp.hp.com/pub/softlib/software1/lj1488/lj-1145-2/lj1488en.exe](ftp://ftp.hp.com/pub/softlib/software1/lj1488/lj-1145-2/lj1488en.exe)

   2. extract sihp1000.img from it.

   # unzip lj1488en.exe sihp1000.img

   3. power printer and ...

   # cat sihp1000.img > /dev/usb/lp0

Sometimes you just don't want to click another link and dig through more crap...

   -r

---

