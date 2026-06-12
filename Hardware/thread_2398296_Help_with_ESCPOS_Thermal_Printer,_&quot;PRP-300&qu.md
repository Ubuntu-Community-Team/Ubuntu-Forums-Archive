---
title: "Help with ESC/POS Thermal Printer, &quot;PRP-300&quot; (I'm resonably familar with GNU/Linux)"
date: 2018-08-10
forum: Hardware
---

### Post by charles-scoville on 2018-08-10
[SIZE=5][SIZE=4]Executive summary.

[/SIZE][/SIZE][SIZE=5][SIZE=4][SIZE=3]"Searching for help getting Point of Sales [/SIZE][/SIZE][/SIZE][SIZE=5][SIZE=4][SIZE=3][SIZE=5][SIZE=4][SIZE=3][SIZE=5][SIZE=4][SIZE=3]FOSS printing receipts via [/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]a PRP-300 thermal printer [/SIZE][/SIZE][/SIZE][SIZE=5][SIZE=4][SIZE=3][SIZE=5][SIZE=4][SIZE=3](alleged ESC/POS protocol)[/SIZE][/SIZE][/SIZE] on[/SIZE][/SIZE][/SIZE][SIZE=5][SIZE=4][SIZE=3] x64 hardware running [SIZE=5][SIZE=4][SIZE=3]some Ubuntu flavor[/SIZE][/SIZE][/SIZE]."[/SIZE][/SIZE][/SIZE][SIZE=5][SIZE=4]

Introduction. [/SIZE][SIZE=1]

[SIZE=2]I am Charles Scoville. My friends call me Charlie, you may do the same. 

I'm reasonably familiar with GNU/Linux[/SIZE][/SIZE][SIZE=2], which should make helping me relatively painless.

I am rebuilding a POS system for my work. The hardware is a purpose built unit powered by an Intel BayTrails SoC... so x64 Intel Atom quad-core, no SMT, no more than 2G of RAM, 64GB SSD. I have a tablet with similar specs, lol.

I would like the OS to be any  modern GNU/Linux, preferably Kubuntu 18.04 LTS. But you can (within reason) tell me  which distro/flavor/version you can best solve this problem for and I will  gladly try that instead.

[SIZE=4]Problem Hardware Details.[/SIZE]

The POS system comes with a thermal printer I intend to use, which most  effectively identifies simply as a "PRP-300." (There are several brands  using this core board/system, so this is the best key word search)

The [/SIZE][/SIZE][SIZE=2]PRP-300 claims support for the ESC/POS  protocol, and enumerates as a TTY/serial/CDC-ACM device on Ubuntu. (And  Windows... I'm NOT opposed to sniffing this traffic w/ official drivers.)

[SIZE=4]Problem Software Details.[/SIZE]

A third party, "Endless Data," has a Linux driver package which you can get from [HERE]("http://www.edatame.com/drivers/"). This at least contains a PPD file and a filter for raster-to-TYSSO, which may well be raster-to-ESC/POS. 

Additionally, [HERE]("http://github.com/mike42/escpos-php") is a PHP receipt printer library on GitHub, which lists support for this printer. This may be a better option for CUPS. It's certainly a better option for web-based POS software.

If that isn't enough options, [HERE]("https://github.com/klirichek/zj-58") is supposedly a bare minimum CUPS driver for ESC/POS thermal printers.
[SIZE=4]
What I've done.[/SIZE]

I have tried the Endless Data driver package, I cannot get it to work.  In particular, I cannot get the executable binary blob named simply  TYSSO, to produce a GUI, nor does it throw any error. The package has  instructions as a PDF file. The  instructions clearly depict the TYSSO  binary blob launching as a GUI program;  specifically as a GTK+/GNOME  Ubuntu window. I haven't looked into it with anything that might shine  light onto why it's not working, e.g. ELF viewer, hex editor, disassembler, GDB, etc.. 

I have tried using raw mode, and any other printer driver that comes with Ubuntu that makes mention of Epson's [/SIZE][SIZE=5][SIZE=1][SIZE=2]ESC/POS. No luck.

I am not currently using a web-based POS software solution, so I have  not used the PHP library. Perhaps I should? Could this even be used with  CUPS?

I haven't the foggiest idea how to use the [/SIZE][/SIZE][/SIZE][SIZE=5][SIZE=1][SIZE=2][SIZE=2]minimum CUPS driver [/SIZE]option above. It's largely the same as other options, I feel, and I can't get those to work.

[SIZE=4]Other things of note.[/SIZE]
The POS software I have been using is Floreant POS. It's  written in Java and is reportedly Open Source. I haven't been able to  build it, however, the build system is a mess. I am open to suggestions  for different POS soft, so long as it's Open Source.

The OS I  have my heart set on is Kubuntu 18.04 LTS, as KDE/Plasma is the UI I am  most familiar with, and a POS system really needs that LTS. If it makes  your life easier, I am open to suggestions here.

I have a DD  image of the POS' original OS. This was Linux, and so may contain  working Linux drivers for this printer. I believe it was Ubuntu 14.04  LTS.

By "getting it to work" I mean to say, using base Ubuntu tools to to  print a test page with the "Print Test Page" button, print text from a  text editor, or print raster graphics. Anything... really,[B] but I will obviously need to print a receipt with my POS software at some point.

[/B]I am aware of the permission issue of serial ports on some systems, I have added my user to the dialout group for this reason.

Manually Echoing text  to the port (/dev/ttyACM0) will cause the text to  appear on the thermal  paper. Sending the newline char will cause the  printer to feed a line. I have not tried to listen to any responses  using cat for any of the other supposed commands.

The same guy  that has the PHP lib on GitHub has a [Python lib there]("https://github.com/python-escpos/python-escpos") as well. As time  goes on, I'm more and more tempted to try and write something  which can test these printers using this lib. Would be interesting to investigate, as maybe  that can be used as a wrapper/pivot to CPUS or to my POS software.  (Hummm... [Looks like it's not an insane idea.]("http://behind.pretix.eu/2018/01/20/cups-driver/") We may even already have the PPD file with the Endless Data driver package.)

I await requests for more/other information. 
Any help is much appreciated. 
Thanks. -Charlie

[/SIZE][/SIZE][/SIZE][HR][/HR][SIZE=5][SIZE=1][SIZE=2]
[SIZE=5][SIZE=1][SIZE=2]P.S. There could easily be at  least a beer/coffee in this for whoever solves this problem for me. And, by  reading this far, that has a good chance to be you. It's worth up to nearly the price of a new Linux capable thermal printer to  me. [SIZE=5][SIZE=1][SIZE=2][SIZE=5][SIZE=1][SIZE=2]We'll have to PM  payment details, [/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]of course, or you could just have a bitcoin address ready in your signature.[/SIZE][/SIZE][/SIZE] [/SIZE][/SIZE][/SIZE]

---

### Post by nayamina on 2019-03-06
Hey Charlie!

So I found this post in my desperate searches to see if anyone was having the same issues as me.

I've got the printer actually printing at this point, without use of their horrible installer. Did you make it any further along in the past 6 months? I hope you did, but if not I'll leave a few notes here in case anyone else stumbles across this.

The first thing I noticed is that you're still trying to run on /dev/ttyACM0. In the udev rules file they include, you'll see that they run "/etc/fametech.sh". In that script they go through the process of removing the cdc-adm kernel module and then modprobe usbserial to force it over to ttyUSB0. I just did these parts by hand, and it's been a lot smoother going. I adjusted my printers.conf to reflect the new URI.

Also, fun fact, the rastertofametech filter from edatame is an old version (Release 6) and is only compiled in 32bit. Release 9 has both 32 and 64bit if you don't want to have to keep both sets of libraries. I had to get release 9 directly from Fametech support. 

With the the udev rules in place (though I removed the fametech.sh reference since I'll just do that myself), the rastertofametech filter, moving to ttyUSB0, and putting the PPD file into place, I've got it printing now, but with a weird issue. Using the PPD file they provided, I get a vertical strip in the middle of the print job where the text comes out of alignment and creates a kind of stutter making everything but the first several words of each line readable.The reason I say it's the PPD file is because I stole the PPD from a similar printer ( from Epson's tmx-cups, tm-ba-thermal-rastertotmt.ppd) and it prints without the stutter, just with the wrong margins.

Anyhow, if you saw anything similar to mine, please let me know. If not, Hopefully you at least found a solution for your POS printer :)

---

