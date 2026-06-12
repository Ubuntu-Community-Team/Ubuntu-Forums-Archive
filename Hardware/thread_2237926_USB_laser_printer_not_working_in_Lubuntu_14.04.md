---
title: "USB laser printer not working in Lubuntu 14.04"
date: 2014-08-04
forum: Hardware
---

### Post by Enigma12 on 2014-08-04
I am still quite new to Linux. Have only been using it since March 2014. I had hoped to solve any problems that came up by reading books or reading of others' solutions here on these forums, which I visit almost daily, or Googling for answers. Until yesterday I had been successful with that. No longer so. 

I am trying to get a Lexmark Optra E312L (black only) laser printer working via a USB cable with a Dell Dimension E310 computer running Lubuntu 14.04 that has **no parallel printer port**. This printer was configured easily and worked perfectly via parallel cable to another computer which was also running Lubuntu 14.04. On the E310 it does nothing. 

When I go though the +Add Printer procedure, I am asked to Enter device URI and given two examples below. I've tried both options given. Then I either click Provide PPD file (Lexmark-Optra_E312-Poscript.ppd which I downloaded from some web page) or pick the printer and proceed. When all that is done, I am given the option of printing a test page. When I click OK nothing happens. 

Neither of the books I have or the web pages I've found have resolved this. Frankly, on some of the web pages I feel like I am trying to read hieroglyphics without a Rosetta Stone. Lots of terms and names that are new to me. 

So, can anyone here resolve this for me? Since the printer was configured easily and worked perfectly with that other computer, using parallel port and cable, would the best solution be to just add a parallel port board to this computer and use that? If not, how do I get it to work via the USB? 

Thanks in advance for any advice.

---

### Post by Bucky Ball on 2014-08-04
With the printer plugged in, could you open a terminal and:

lsusb

Please post the output.

---

### Post by Enigma12 on 2014-08-04
That command was mentioned in one of the many web pages I read, so I did it earlier. 

When I did this with the printer plugged in and turned on, I got:

wayne@Slick-Dell:~$ lsusb
Bus 001 Device 004: ID 0644:0200 TEAC Corp. All-In-One Multi-Card Reader CA200/B/S
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00dd Microsoft Corp. Comfort Curve Keyboard 2000 V1.0
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
wayne@Slick-Dell:~$ ^C
wayne@Slick-Dell:~$

Hopefully I did this correctly even though I have had very little experience using Terminal. I don't even see any listing for a printer in this.

---

### Post by Bucky Ball on 2014-08-04
Yes, you did fine. Fascinating! The printer *doesn't* seem to be recognised there at all, which is highly unusual. Time for some thinking music ... :-k

There isn't some switch or tweak you need to do to change the actual printer from para port to USB? It just automagically picks up which is connected I guess? Wild punt ...

Have you tried the USB connection on any other machines/OSs? Have you tried a different USB cable?

---

### Post by Enigma12 on 2014-08-04
Thank you for your effort, Bucky Ball. From having lurked here since right before I actually started using Lubuntu, I know that you are one of the more knowledgeable and helpful people here. I had actually planned on my first post to these forums being one of lauding Lubuntu, Linux, and the forums and members in hopes that any potential newbie would not be scared off by all the reported problems. Until this snag, I had only a couple of verrrrry minor problems. All were solved by either a bit of reading or thinking. 

There is no switch on the printer. According to the PDF of the manual, both parallel and USB are automatically set to whichever is used. Replaced the USB cable with a new one and got the exact same results with the "lsusb" (w/o quote marks, of course) in Terminal. Rather than just trying out a bunch of swapping from computer to computer, I have a next step.

Since this printer DID work fine using the parallel cable with the other computer, my next step will be to get and install a parallel printer card to this computer and try that. If that doesn't work, I'll try for a solution here again. If it does work, I hope I can figure out how to mark the thread solved.

---

### Post by Mike_Walsh on 2014-08-05
Good evening, Wayne.

Have you by any chance considered a USB to parallel converter cable? Take a look at this one (it's just an example; there are lots of them out there on the web):-

[http://www.misco.co.uk/product/110759/Startech-USB-to-Parallel-Interface-Converter](http://www.misco.co.uk/product/110759/Startech-USB-to-Parallel-Interface-Converter)

According to the specs, it will allow any computer that normally prints via USB to convert those signals to a parallel format for older printers.

Regards,

Mike.

---

### Post by Enigma12 on 2014-08-05
Thanks for that suggestion, Mike. Right now I don't know the current currency conversion rate between UK and USA, but I suspect that a parallel printer card and that cable would be about equal in cost. And, since that would continue to leave the printer plugged into a USB slot on the computer, I **may** still have the same problem. 

Perhaps, months or years from now, when I have gotten more competent with command line activity, and Linux in general, I will groan at my current inability to configure hardware in Lubuntu. I was for years (long ago, of course) very proficient with a variety of MS-DOS versions. Linux command line activity may be somewhat or even very similar, but I'm just not that knowledgeable about it today. 

It's interesting that you are also using Lubuntu 14.04. I am totally sold on it so far. When I installed it on my earlier (old) computer, I did so out of necessity due to hardware. Lubuntu is on this newer computer out of choice. I have tried the full Ubuntu and a couple of other distros (see, I'm learning the lingo), but Lubuntu does everything I want and nothing that I don't want. I have, I must admit, though, added a few other programs to it, and I use it daily by preference instead of my Win 7 computer.

---

### Post by Bucky Ball on 2014-08-06
Hey, Wayne, I'm hearing you, and thanks. I can only say that anything I know i know because of standing on the shoulders of giants!

Personally, I just install a minimal and build it from there now days. That way it is the beast I create. Don't love lxde myself, but it's all about taste, and that belongs to every individual. ;)

Recently bought an Odroid for media server on the tele (replaced a Raspberry Pi) and that is running Lubuntu. Okay, but not my cup o' tea. Xfce4 much more configurable.

---

### Post by Enigma12 on 2014-08-06
OK, I installed a parallel port in my new computer, then connected a couple of printers using parallel printer cords in a sequence and this situation has gotten more puzzling. 

First, the Lexmark Optra E312L still does absolutely nothing. Its Data light never flashes when I have AbiWord send it a document and it will NOT print anything. The HP Laserjet 5L prints one line of garbage characters, then spits out that page and does another one line of junk on the top of another page. It acts as though it could trash an entire ream of paper with junk lines. I only load two or three sheets of paper to prevent that. 

Since I still have my older computer, I reconnected it and tried both printers on it. The Lexmark now does nothing on that computer, on which it had printed perfectly earlier. The HP Laserjet, however, prints correctly, just as it did before. The Laserjet 5L was installed identically and easily on both computers. 

Although the computers are different, they are theoretically using the exact same operating system. Below are the relevent System Information readings for both computers.

Kernal                          Linux 3.13.0-32-generic (i686)
Compiled                      #57-Ubuntu SMP Tue Jul 15 03:51:12 UTC 2014
Distribution                   Ubuntu 14.04.1 LTS
Desktop Environment    LXDE (Lubuntu)

And, FWIW, here are the (probably irrelevent) basic specs on both computers: 

Old: Gateway E3600, P4 @ 1.6 GHz, 768 MB RAM, two 40 GB IDE hard drives
New: Dell E310, P4 @ 2.8 GHz, 2 GB RAM, one 80 GB SATA hard drive

My guess is that there are one or more printer files and/or settings on the old computer that are either not on the new computer or are different, but I don't even know what to look for or where to look to find them. 

Maybe, if someone would tell me in detail where to look and what to look for, I could copy the needed stuff from the old one to the new one and have an operable printer on that computer. 

Everything else on the new computer is better than on the old one: HD videos can now keep in sync with the sound, I would have a CD/DVD player/burner and a built-in multi-card reader, and eveything is just faster. Without a usable printer, though, that computer has severely limited usefulness. 

I would prefer having the faster output and better print quality of the Lexmark printer, but I would settle for now with using the HP Laserjet. Maybe in the future, when I have gotten more competent with Linux, I may be able to solve the problems with the Lexmark. 

Thanks in advance for any help in finding a solution to this problem.

---

### Post by Enigma12 on 2014-08-06
I have to admit that I label this problem as "Solved" with some serious reservation. I now have a laser printer that works well with my Lubuntu computer, but I didn't _**solve**_ anything. 

What I did that worked was take my other Lexmark laser printer from my Windows 7 computer and attach it to the Lubuntu computer, then attach the HP 5L to my Windows 7 computer. Both got configured automatically, and both work with their attached computer. 

My reservation comes from not knowing _**why**_ they worked with the switch. I really didn't learn anything in that process. I did NOT reboot either computer when doing the swap, so that as a possible factor can be eliminated. 

If anyone who read these posts hoped to learn how to solve a similar problem they were having, all I can suggest is to swap things around, and maybe you will have the same inexplicable results.

---

