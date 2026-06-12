---
title: "Konica Minolta Magicolor 2530 DL"
date: 2007-01-26
forum: Hardware &amp; Laptops
---

### Post by Spr0k3t on 2007-01-26
Recently I had some xmas cash in my pocket burning a hole in it and I decided to finally ditch the inkjet type printers.  I purchased a Konica Minolta 2530DL printer.  Keep in mind, this was before I decided to switch over to Linux.  So now I'm a total convert spewing the wholesome greatness of Linux.  Everything in all of my computer systems work like gangbusters with the exception of one wireless card.  Let me get to the point.

I contacted Konica Minolta asking about 64bit support from their Linux drivers they offer (see link below).  The i386 portion of the drivers work perfectly on the i386 install of Ubuntu but will not work with AMD64.  The information I was given is my request isn't the first, and they are looking into creating the needed drivers.

In the interim, I have found an open source 64bit driver in pre-beta form.  I can access the printer but there are still some problems with it.  Read more on this project at [http://foo2lava.rkkda.com/](http://foo2lava.rkkda.com/) if you would like.

Konica Minolta Magicolor 2530 DL site: [http://printer.konicaminolta.com/support/current_printers/mc2530dl_sup.htm](http://printer.konicaminolta.com/support/current_printers/mc2530dl_sup.htm)

My reason for posting this information, I couldn't find anything on the 2530DL and wanted to make sure those interested in this printer using search can find information about it regarding 64bit drivers.  For now, I can print using the drivers from the KM site on i386.

---

### Post by Spr0k3t on 2007-02-03
I've made some headway with the help of the foo2lava developer.  I was able to get black and white to print perfectly in all resolutions available with a minor problem on the offset at 600x600.  Hopefully this will be a well rounded driver once it's done.

---

### Post by Spr0k3t on 2007-02-04
Latest update.  The offset in the B&W 600x600 is now set correctly for letter.  Color is now printing correctly though there is the offset issue once again.  I'm waiting on the latest package to compile and test.

If you are looking for a good cheap laser printer, you really can't go wrong with this one.

---

### Post by msak007 on 2007-03-18
I'm considering one of these printers instead of a B&W laser. Not too crazy about the cost of the printer or the toner, but I'd like the option of color every once in a while and I don't print that much so the toners should last me forever. LinuxPrinting rates it as "Mostly Works", so I'm kind of hesitant because I want something that works 100% (as opposed to the paperweight Linux inkjet I currently have). It's awesome that they provide a Linux driver, so that's definitely a plus. You say it works fine in i386, which is fine because that's what I'm using. Can you explain a little more, like if you were using Dapper or Edgy, how easy it was to install, how configurable the options were, tracking toner levels, etc.? Thanks in advance.

---

### Post by Gadget on 2007-05-15
After *wasting* about four or five hours trying to get this printer to print first *anything*, then something other than a black page, I'm at wit's end.  

I *tried* the foo2zis, foot2lava stuff and that didn't work. I tried solutions from two different Linux books, through cups and *that* didn't work.  

It shouldn't be this #$%^ difficult to install a printer, especially a network printer, considering that I got it done in about ten minutes on the windows partition.  It took longer to load the software than it did to configure the printer on the Windows side.  That worked, so it's *not* a hardware problem.  A basic function such as installing a printer ought to be fall-down simple.

Does *anyone* have a solution that *works* on Ubuntu (Feisty) for this 2530DL?? Rate negotiable...

Your time and assistance are appreciated.

Regards,

---

### Post by lord_alan on 2007-05-29
Hi,

I have a network connected 2530DL on Fiesty (7.04) and it works most of the time... I configured it through CUPS using the KM driver and setting it up using the AppSocket / HP JetDirect device with the Device URI as:  socket://my_printers_ip_address_here:9100.

Install the PPD and driver stuff first. (KM supply a RPM file. I'll let you work out how to get that installed into Ubuntu. Hint - try google for "convert rpm to deb").

Apart from the odd time when it takes about half an hour to start printing (which I am still investigating) it prints fine in colour and B&W.

HTH

Alan

---

### Post by julmuzy on 2007-06-05
I had the same problem on Feisty.  I had it working on Edgy, but the upgrade to Feisty produced all sorts of issues.

Anyway, this worked on three  separate computers on the same network

Get the driver file from Minolta (mine was Magicolor2530DL-2.0.0-1.i386.rpm) and stick it on the desktop.
You can't use this file because it's not in a debian format so you need to use a program from the terminal called alien.  You will have to install this using the synaptics package manager.  Once you've installed it then open a terminal (Applications - Accessories-Terminal).  If you haven't used a terminal before, just make sure that you type everything EXACTLY as shown.  Navigate to your desktop by typing

cd Desktop  (don't forget the capital 'D' in 'Desktop' to a get  prompt ending blah/blah/Desktop$

now type

sudo alien Magicolor2530DL-2.0.0-1.i386.rpm --scripts

(it is vital that you type the name of the folder on your desktop exactly.  It's a long complicated name with dots and hyphens.  I t might be better to rename the file Magicolor.rpm or something.  Use the desktop to do this, not the terminal, it's easier. Also make sure that the extension 'rpm' is in lower case. Alien doesn't recognise upper case file extensions?

This will create a folder on your desktop called the same file name, but with a .deb extension.  It will also have a 'lock on it'.  You need to change permissions for this folder..use

sudo chmod 777 Magicolor2530DL-2.0.0-1.i386.deb

return to your desktop and double click the .deb folder. It will be opened by a package manager and offer you the possibility to install everything. Do so.  The scipt installs everything but falls over at the last hurdle with an error message saying it hasn't worked........but it has !

Make sure that your printer is connected to your network, it has an IP address and is switched on.  (If you don't know how to do this....RTFM)

Load up your browser and type in the address bar

[http://localhost:631](http://localhost:631)

This should bring up the CUPS manager.  If it doesn't then go to Synaptic and load it all in.

In CUPS go to ADD PRINTER

Don't acept the options of installing printers that CUPSYS has found.  They work sometimes, but not always. 
Put the printer name in (no spaces or daft characters) and then continue.  For the Device choose  'AppSocket. HP jet Direct' and in the URL box, type in

socket://10.0.1.18:9100

(I fixed the ip address of the network printer to the above.  I suggest that you do the same thing.  If you have a DHCP server on your network, then you must allocate a fixed IP using either the administration console for your server or TELNETing the commands to your system.  If you don't understand this then there's another learning curve for you to climb.  The basic problem is that you must identify the printer on your network with an ip address.  The above address (10.0.1.18)  is mine for this printer, you will need to put in your own.  Don't forget the port address  :9100)

In the make manufacture box, don't be tempted by the ones on offer.  Browse directly to the PPD file which is located in /usr/share/cups/model/KONICA_MINOLTA/km2530dl.ppd.gz

Hit MODIFY PRINTER and you're done.

Send a test print and it should work.

Good Luck

---

