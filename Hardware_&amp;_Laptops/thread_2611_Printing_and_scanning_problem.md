---
title: "Printing and scanning problem"
date: 2004-10-29
forum: Hardware &amp; Laptops
---

### Post by tazzz on 2004-10-29
Hi all,

Im having problems getting my printers and scanner working.
They were working fine with Mandrake 10 ..
The printers are: Brother 2400C and 1260 (Both LAN), and the scanner is a Canon Lide30 (Usb).
I installed both printers with the recommended drivers (postscript for the 1260 and hl1250 for the 2400c), with ipp and it tells me everything is fine, but when i try to print  it sends the job but nothing happens. Then i also have a windows machine somewhere on the LAN and since the printing is ok from there i checked how it was installed, and i saw it was on port 9100, so i tried to make to printer go to ipp://ip:9100 too, something comes out then but its just a bunch of letters, and then the paper scrolls on and on ..
I also tried with the HP port or share it from a Mandrake machine, through smb, but i have the same problem. (the HP3820 shared on that machine does work from the ubuntu machine)
(Also i cant configure anything from cups http .., its disabled by default in Ubuntu, can i simply reenable it in cups conf file or so ..?)
Its probably either a port or driver problem, does anyone have an idea ?

As for the scanner Canon Lide30, its not recognized, and i looked in the conf files, and tried some stuff i found from google, but nothing seems to work till now. Xsane or kooka just see my webcam (or nothing if i disconnect that one..).
Does anyone know what i could try to make it work ?

I really need the scanning and printing from this computer, and i like ubuntu, it would suck to have to go back to Mandrake because of that !!

I tried the mailing lists, and irc channels, but didnt get much help ..

Thx ..

Tazzzzzzzz

---

### Post by tazzz on 2004-10-29
..I got the Scanner working from the libsane-extras package (I thought i installed it all already!)..and my Canon Lide30 seems to work now ! :)

Now i still have to find a way to make the printers work ..

---

### Post by Joeb on 2004-10-29
Cups through http doesn't work because there isn't a root user or group with cups administration.  It's not really a problem, becaue you can access the printer through the menus Computer==>System Configuration==>Printing.

As for your printing problem, where did you get your drivers from?  Were they from linuxprinting.org or through Synaptic?

---

### Post by tazzz on 2004-10-30
I created a root user though, and i complained about not being able to access through cups admin, cze i was having problems through the gnome admin, and maybe there would be more options, or something i could configure to make it work ..

As for the drivers they came with Ubuntu, it recognized everything, it tells me everything is configured ok, but when i try to print it sends the job and nothing happens. I also tried the .ppd files from linuxprinting.org ..
(I tried the recommended drivers, and also the 2-3 others that it offered ..)

---

### Post by tazzz on 2004-11-04
..I still cant print on the Brother 1260 and 2400c on the LAN ..
Has anyone an idea .. ?

Thx

---

### Post by mattyh on 2004-11-04
Ok through the Gnome Printer Manager can you set it up as a Network printer?  Here is a link to linuxprinting's page for your 1260.  [http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-1260](http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-1260)

Sorry if this is stuff you already know, but I assume you need to go to Computer->System Configuration->Printing and add new printer, select network, CUPS, hit next, and then put in the IP Address on the Lan, or if it is shared on a windows machine, select Windows Share instead of CUPS, and enter the name.

*EDIT* Whoops, didn't see your last post that you had tried that.  You know, I had the same kind of issue w/ my HP PSC 2110v about sending it and nothing happened...I followed the instructions on HP's site which included running: 
killall -HUP cupsd
I disconnected and reconnected the printer and then installed the printer again. i.e. added another one, restarted and then it started working.  So, I'm not sure what in there made it work.

---

### Post by tazzz on 2006-03-28
I used that brother1260 printer for about 1 year through a shared printer on a Mandrake box, where it was working by just installing a 1260 printer. I then got rid of Mandrake for Ubuntu server and then i looked at it a little closer and noticed the 1260 had a HP network card. I then Configured on Ubuntu a 1260 with HP protocol instead of ipp and then it worked ..

I didnt think of that before because the Mandrake box configured that automatically somehow, and it was working without having to configure for a HP network card ..

---

