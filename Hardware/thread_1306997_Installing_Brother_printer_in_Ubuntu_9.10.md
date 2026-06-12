---
title: "Installing Brother printer in Ubuntu 9.10"
date: 2009-10-30
forum: Hardware
---

### Post by Chuq on 2009-10-30
This isn't a support request, it seems to be working, I'm just posting to help others!

My printer is a Brother DCP-330C, it wasn't autodetected after my 9.10 install this morning, so started looking at it...

turned out to be very simple.  Brother have pretty good support on their site at [http://solutions.brother.com/linux/en_us/index.html]("http://solutions.brother.com/linux/en_us/index.html")

Summarised here:

1) run 'sudo aa-complain cupsd'

2) run 'sudo mkdir /usr/share/cups/model'

3) From this page - [http://solutions.brother.com/linux/en_us/download_prn.html]("http://solutions.brother.com/linux/en_us/download_prn.html")
.. find your particular model and download the *.deb files (should be 2)

4) go to the folder and run 'sudo dpkg -i --force-all *'

To verify it worked:

1) Run 'dpkg -l | grep Brother'
Mine gave the output:
ii  dcp330ccupswrapper    1.0.1-1       Brother CUPS Inkjet Printer Definitions
ii  dcp330clpr            1.0.1-1       Brother lpr Inkjet Printer Definitions

2) Check the contents of '/etc/printcap'
Mine was:
DCP330C:\
        :mx=0:\
        :sd=/var/spool/lpd/dcp330c:\
        :sh:\
        :lp=/dev/usb/lp0:\
        :if=/usr/local/Brother/Printer/dcp330c/lpd/filterdcp330c:

3) Check the CUPS web interface at:
     [http://localhost:631/printers](http://localhost:631/printers)

I haven't tested it fully beyond a test page, and I also haven't set up scanning yet, but that's for another day!

Feel free to use this thread for additional support but this is the first time I've set up a printer in Linux (in 10+ years of on-and-off use) so I personally may not be much use!

---

### Post by ricgail on 2009-11-08
Worked like a charm! Thanks mate.

---

### Post by B Crowther on 2009-12-24
Thank you, Chuq, for a very clear, very cool howto.

I am only an intermittent printer user, so I did not discover until this morning how badly screwed up the 64 bit driver in the repos for 9.10 is for the DCP130C: margins are totally banjaxed, so I couldn't print the card I had painstakingly worked on for my wife's Christmas present.

I have had no luck trying to "force architecture" in the past, but your solution sorted the problem very quickly, present was wrapped, card attached, before Her Indoors arose to see what Santa had left. 

Lifesaver!:lol:

---

### Post by kevin.giny on 2009-12-25
Thanks for your useful information.

It might be very useful to us.

Thanks for sharing this information .

I hope you will share more information with us.

Thanks

---

### Post by themadbusdriver on 2010-02-06
you say: 4) go to the folder and run 'sudo dpkg -i --force-all *'

what do you mean (sorry i am NOT a computer literate person) is that in the terminal thing? if so mine didnt work

---

### Post by tcchris on 2010-02-06
he means in the terminal go to the folder you downloaded the deb to (the * is the name of the deb file )
deb is like exe in windows 

Alternatively , if you are using 32 bit os you can probably just browse to it in nautilus , and right click on it , and open with gdebi installer .

---

### Post by Stoneage Kit on 2010-03-16
While this is obviously elementary stuff to many it is deep water to me. I've tried to follow the steps outlined above but came to a dead end after step one. At that point I'm asked for a password. I assumed this was the password needed to open Ubuntu and tried to enter that; no go. I say tried because nothing happens when I type.
I also tried the 32 bit suggestion. The computer finds the printer, sends a test page, the printer indicates it is receiving data, yet produces nothing. 
I would be grateful for any  assistance.

---

### Post by plucky on 2010-03-17
> **Stoneage Kit said:**
> While this is obviously elementary stuff to many it is deep water to me. I've tried to follow the steps outlined above but came to a dead end after step one. At that point I'm asked for a password. I assumed this was the password needed to open Ubuntu and tried to enter that; no go. I say tried because nothing happens when I type.
I also tried the 32 bit suggestion. The computer finds the printer, sends a test page, the printer indicates it is receiving data, yet produces nothing. 
I would be grateful for any  assistance.

@Stoneage Kit.

Is your Brother printer the DCP-330C?

If not, please specify the model of your printer.(possibly start a new thread)

If so,the drivers for this printer is packaged in the **Synaptic Package Manager**

Open **System > Administration > Synaptic Package Manager** and search for **dcp-330c** and it should find ```
brother-cups-wrapper-bh7
brother-lpr-drivers-bh7
``` select cupswrapper driver and it will install both drivers.

Then open **System > Administration > Printing** and select new printer.Go through the install procedure and select the correct driver for your printer.

Good Luck

---

### Post by Stoneage Kit on 2010-03-17
> **plucky said:**
> @Stoneage Kit.

Is your Brother printer the DCP-330C?

If not, please specify the model of your printer.(possibly start a new thread)

If so,the drivers for this printer is packaged in the **Synaptic Package Manager**

Open **System > Administration > Synaptic Package Manager** and search for **dcp-330c** and it should find ```
brother-cups-wrapper-bh7
brother-lpr-drivers-bh7
``` select cupswrapper driver and it will install both drivers.

Then open **System > Administration > Printing** and select new printer.Go through the install procedure and select the correct driver for your printer.

Good Luck
Yes! Worked like a charm. Thanks mate, appreciate your help.

---

