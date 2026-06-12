---
title: "So, before I uninstall Ubuntu Breezy 5.10 in a fit of rage..."
date: 2005-12-10
forum: Hardware &amp; Laptops
---

### Post by theMagius on 2005-12-10
...anyone out there have any last-ditch ideas?

I've got a hardware problem.

1)  My scanner does not work in Ubuntu.

Okay, I *know* what you're thinking.  Some idiot installs Ubuntu, doesn't have a clue of what the hell he's doing, and comes on the forums just to yell and scream in a fit of rage.  Well, let me give you some background, and you can decide if that's true or not.


**_The Scanner Problem_**
I have an Epson 636U USB scanner.  Yeah, it's incredibly old, but the xSane webpage says it's 100% compatible with Breezy.

So, I plug the thing in and fire up xSane v0.97.  It hums along for a couple of seconds, and then gives me a Device Selection window that asks me whether I want the epson:libusb:002:002, or the epkowa:libusb:002:002.

Well, unfortunately, it really doesn't matter which one I pick because with *either* option, I get the infamous &#8220;Failed to start scanner: Error during device I/O&#8221; popup.  Now, this appears to be a pretty common hurdle in getting a scanner to work according to the Ubuntu Forums, so I go looking around and find that some folks recommend the following articles on how to troubleshoot this problem:

[Scanning details and troubleshooting](http://hpoj.sourceforge.net/hpoj-0.90/doc/setup-scan-details.html)
[Scanner-HOWTO](http://ldp.rtin.bz/HOWTO/Scanner-HOWTO/troubleshooting.html)

And, of course, after editing and manipulating my sane.d and dll.conf files about fifty times, I've not gotten any closer to determining why Ubuntu hates my guts.

So, um, anyone got any suggestions.  I'm all ears&#8212;really.



It just really shouldn't be this hard, folks.

At my wits' end,
-theMagius

---

### Post by jhnphm on 2005-12-10
Have you run alsamixer and checked if the microphone volume is on (assuming you get any sound in the first place)? 

I can't help you w/ the scanner, never experienced that w/ my poorly supported Umax 2000U (even given the POS that it is).

---

### Post by teaker1s on 2005-12-10
look [here]("http://www.avasys.jp/english/index_e.html") you will most likely need epson driver

remove any sane libs as this will fail otherwise
find your scanner and install Iscan which is the backend for most scanners
download the rpm file and install with alien(use synaptic to fine and install alien)
cd into the download directory
then
sudo alien -di- iscan-1.12.0-1.c2.i386.rpm

terminal
iscan


should run epsons own scanner gui

now for sane
terminal
sane-scanner-find

then edit the sane epkowa.conf file so 0x04b8=epson and the product id from scanner find so it looks similar to this
usb  0x04b8 0x0813

save the file and sane and iscan should hopefully work as for sound open volume control edit preferences tick all boxes and you should be then able to choose all avaliable sound options providing your card has installed correctly

Pm me if your successful or I may be able to suggest more

---

### Post by theMagius on 2005-12-11
[QUOTE=teaker1s]look [here]("http://www.avasys.jp/english/index_e.html") you will most likely need epson driver[/quote]
Unfortunately, that driver is not for my scanner.


> remove any sane libs as this will fail otherwise
find your scanner and install Iscan which is the backend for most scanners
download the rpm file and install with alien(use synaptic to fine and install alien)
cd into the download directory
then
sudo alien -di- iscan-1.12.0-1.c2.i386.rpm
Wierd thing is, I can't seem to find iscan anywhere from within Synaptic, or anywhere on the web (Freshmeat.net, etc.).

I guess it's sort of a moot point, though, seeing as how the epson driver isn't for my scanner, anyways.


> Pm me if your successful or I may be able to suggest more
Thanks for the help, anyways.

-theMagius

---

