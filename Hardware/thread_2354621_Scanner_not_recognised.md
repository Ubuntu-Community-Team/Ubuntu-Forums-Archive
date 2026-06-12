---
title: "Scanner not recognised"
date: 2017-03-04
forum: Hardware
---

### Post by lila on 2017-03-04
Hello,

my desktop running under ubuntu 16.04 doesn't recognise the scanner of my multi function printer (brother DCP-J562DW).
The printer side of it works fine.
The device does photocopies, so the scanner should work in principle.
Synaptic tells me, all relevant scanner drivers are installed.
Both Simplescan and xsane tell me they can't find the scanner. :-s  

so, apart from the temptation to point at the printer, look scoldingly at the screen and yell "what do you mean you can't find it, it's right there!", any ideas?

I think I'm in for a long night, I really need to fix this thing...

---

### Post by slickymaster on 2017-03-04
*Thread moved to **Hardware**.*

---

### Post by gifford on 2017-03-04
I am going to assume this is a printer you have set up for a network? This is from the Brother site and you need to add manually with the terminal.
The issue you are having is that you need to tell where the scanner is on the network.

[COLOR=#000000][FONT=sans-serif]Install the driver.[/FONT][/COLOR]
[LIST]
[*]Turn on your MFC/DCP and connect the USB cable.
[*]Open the terminal and go to the directory where the driver is.
[*]Install the scanner driver.
**Command (for dpkg) : dpkg -i --force-all  (scanner-drivername)**
[*]Check if the driver is installed.
**Command (for dpkg) : dpkg -l | grep Brother**
[/LIST]
**Then:**[COLOR=#000000][FONT=sans-serif]Add network scanner entry[/FONT][/COLOR]
**Command : Brsaneconfig4 -a name=(name your device) model=(model name) ip=xx.xx.xx.xx**

[COLOR=#000000][FONT=sans-serif]Confirm network scanner entry[/FONT][/COLOR]
[B]Command : brsaneconfig4 -q | grep (name of your device)


[/B]

---

### Post by lila on 2017-03-04
> **gifford said:**
> I am going to assume this is a printer you have set up for a network? This is from the Brother site and you need to add manually with the terminal.
The issue you are having is that you need to tell where the scanner is on the network.

[COLOR=#000000][FONT=sans-serif]Install the driver.[/FONT][/COLOR]
[LIST]
[*]Turn on your MFC/DCP and connect the USB cable.

[/B]

Hmmm. I didn't set it up at all.  It was pre-installed with the computer, which was pre-installed with ubuntu when I bought it.  I asked them to install the printer, because it's the only thing I've ever had serious trouble doing under ubuntu.  I don't know if it's set up for a network.  There's only one computer, and the printer works via wifi.  I don't think that qualifies as a network?  As for your instructions, thanks, but it gets complicated in the first line for me: what is a MFC/DCP, which I'm supposed to turn on?  Sorry, I've been doing all my computing under ubuntu since 2004, but I still only every post in "New to ubuntu" for a reason... My post was moved here.  Please talk slowly...;)

---

### Post by pdc on 2017-03-04
so lila: hi; welcome to the forums again! You are a long-time ubuntu user!

there is a small file; that is to allow access to the Brother scanner for a user: something about linux "permissions" is that the average user may not be granted user access to the scanner: sometimes the default is only using your "administrator" or sudo password gets you to talk to the scanner

Brother provide this file [http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04](http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04) and I know it is intended for usb but I wonder if it is worth installing that too

If you click to download; and select to "open" the file as it is downloaded, the "open" command should let gdebi installer do the installing as it comes down; the file is [COLOR="#0000FF"]brother-udev-rule-type1-1.0.0-1.all.deb[/COLOR] and it is tiny

I would try a reboot after that and see if you get any joy ........

___________

I looked on the Brother driver site, and your printer wasn't listed there but on the Brother UK site it said that if you have a 64bit ubuntu, you should have [COLOR="#0000FF"]brscan4-0.4.4-2.amd64.deb[/COLOR] installed and as Gifford said, it is brscan4; synaptic tells you that this brscan4-0.4.4-2.amd64.deb is installed? 

try a few commands in the terminal to see if your scanner is spotted

> [COLOR="#FF0000"]sane-find-scanner[/COLOR] ....... no response try > [COLOR="#FF0000"]sudo sane-find-scanner[/COLOR]

then try > [COLOR="#FF0000"]scanimage -L[/COLOR] and then > [COLOR="#FF0000"]sudo scanimage -L[/COLOR]

let us know how those things go

---

### Post by kurt18947 on 2017-03-05
If a Brother scanner works when used in the primary account but not by limited accounts and with a USB connection it may be a permissions issue as referenced above. I find the network setup easier; just the single line Brsaneconfig referenced above has been all that has been required.  I haven't done a 'manual' install in a few years. The installer script has been quite reliable for me.

[http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=mfc495cw_all&os=128&dlid=dlf006893_000&flang=4&type3=625](http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=mfc495cw_all&os=128&dlid=dlf006893_000&flang=4&type3=625)

I use the following terminal command in an account with SUDO privileges:

```
sudo bash linux-brprinter-installer-2.1.1-1
```

then specify the model when prompted.  The directions associated with the above link say to include the model as part of the command. I'm sure that works as well. I assume that letter case matters so I use (for example) MFC-J480DW not mfc-j480dw. I'm not sure if it matters but linux commands can be case sensitive so it seems a good habit to get into.

---

### Post by lila on 2017-03-05
> **pdc said:**
> so lila: hi; welcome to the forums again! You are a long-time ubuntu user!

there is a small file; that is to allow access to the Brother scanner for a user: something about linux "permissions" is that the average user may not be granted user access to the scanner: sometimes the default is only using your "administrator" or sudo password gets you to talk to the scanner

Brother provide this file [http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04](http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04) and I know it is intended for usb but I wonder if it is worth installing that too

If you click to download; and select to "open" the file as it is downloaded, the "open" command should let gdebi installer do the installing as it comes down; the file is [COLOR="#0000FF"]brother-udev-rule-type1-1.0.0-1.all.deb[/COLOR] and it is tiny

I would try a reboot after that and see if you get any joy ........

___________

I looked on the Brother driver site, and your printer wasn't listed there but on the Brother UK site it said that if you have a 64bit ubuntu, you should have [COLOR="#0000FF"]brscan4-0.4.4-2.amd64.deb[/COLOR] installed and as Gifford said, it is brscan4; synaptic tells you that this brscan4-0.4.4-2.amd64.deb is installed? 

try a few commands in the terminal to see if your scanner is spotted

 ....... no response try 

then try  and then 

let us know how those things go

Ah, thanks for this answer.  I will try these things as I type...

First, I tried sane-find-scanner
I got this: 
# sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

could not open USB device 0x1d6b/0x0002 at 001:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0003 at 003:001: Access denied (insufficient permissions)
could not open USB device 0x046d/0xc31c at 002:004: Access denied (insufficient permissions)
could not open USB device 0x05e3/0x0608 at 002:003: Access denied (insufficient permissions)
could not open USB device 0x046d/0xc077 at 002:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 002:001: Access denied (insufficient permissions)
  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.


So that sounds like I do indeed have a permissions issue. (and yes, the device is turned on... just saying)
But I am logged in as root....  I'll try with the sudo, here it goes:

# sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.


Unsurprisingly, this then followed: 
scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).


... so, I checked synaptic.  You asked: "synaptic tells you that this brscan4-0.4.4-2.amd64.deb is installed?"
Well, not quite.  Synaptic tells me I have brscan4-0.4.3-3 installed, and also brscan-skey 0.2.4-1

I looked at the brother website.  I think I'll try that next, but since it needs a restart, I'll report back in a few minutes (hopefully), when that is done.

---

### Post by lila on 2017-03-05
I did go to the brother website and installed the little script.  I had big trouble restarting my computer, but that is another issue (which I am pursuing in a separate thread).  
Anyway, the scanner is still not recognised.  

I went back to the website, went to the European section and found my model (which does not exist on the US section).  It told me to download and install the printer driver (though it wasn't talking scanner).  I downloaded it, and the instructions on the site specifically said, it will only work via a command line install.  That and one of the posts above said to "open the terminal and go to the download directory".  I know I should know how to do this.  I may have known at some point.  I tried to find how to in the wiki.  But I've just spent 45 minutes not figuring out how to go to a directory in terminal.  I'm sure I'm looking in the wrong places.  Can you tell me how to do that, and then I can gunzip the file....

Also, should I try to dig out a usb cable somewhere in a back drawer?  I've never tried this printer with a cable.  It works fine otherwise through wifi, would a cable up my chances of being able to scan?

---

### Post by Geoffrey_Arndt on 2017-03-05
I've always have best results when using usb-cable connected printers - - then doing the initial installs.    So, I would try to remove the printer/scanner via the gui System Settings, and then the purge command to remove any remaining drivers on the system (sudo apt purge <driver-name>).   Note, you can also search in Synaptic and also purge using "remove completely".

Then, connect your printer and at first, I would try the initial install via Firefox . . . in URL . . . localhost:631 . . . then use the cups add printer dialog to see if it finds suitable driver file(s) for your Brother.   If it doesn't, next step is to go back to system settings (prior to installing drivers from Brother website) and see if the add process finds and installs the correct driver(s).   Und Lastly . . . if the last step doesn't work - - go back to the Brother website and install the drivers from that source.   Often, Brother provides an initial script that loads all the drivers including the scanner  . . but perhaps that's not the case here.   Also as info, I always check Youtube also, for install methods and steps.   Sometimes that's better than the forums.

I've never had a Brother printer (always used either HP or Epson (the Epson "Workforce" line is excellent) but fileicht (perhaps . . ?) a forum member using a Brother printer will add better input.

---

### Post by pdc on 2017-03-05
so lila;

Brother make an install script; that should ........ get things right ........... if you are happy ..... if you delete the brscan version you have ........... using synaptic ......... and then go here 

[http://support.brother.com/g/b/downloadend.aspx?c=eu_ot&lang=en&prod=dcpj562dw_eu_as&os=128&dlid=dlf006893_000&flang=4&type3=625&dlang=true](http://support.brother.com/g/b/downloadend.aspx?c=eu_ot&lang=en&prod=dcpj562dw_eu_as&os=128&dlid=dlf006893_000&flang=4&type3=625&dlang=true)

and click to download and save this file .......it should end up in your Downloads folder as [COLOR="#0000FF"]linux-brprinter-installer-2.1.1-1.g[/COLOR]z    

if you open a terminal and paste in these commands (right-click at the prompt in the terminal and you should see the paste option ...)

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]gunzip linux-brprinter-installer-2.1.1-1.g[/COLOR]z

maybe at this point you make the terminal full-screen so you can see any questions or queries it has as it runs ............

> [COLOR="#FF0000"]sudo bash linux-brprinter-installer-2.1.1-1 DCP-J562DW[/COLOR]   ....... so that is going to ask you for your sudo password ..............

if we light the blue touchpaper there and stand back and see what happens .....

---

### Post by lila on 2017-03-05
> **Geoffrey_Arndt said:**
> I've always have best results when using usb-cable connected printers - - then doing the initial installs.    So, I would try to remove the printer/scanner via the gui System Settings, and then the purge command to remove any remaining drivers on the system (sudo apt purge <driver-name>).   Note, you can also search in Synaptic and also purge using "remove completely".

Then, connect your printer and at first, I would try the initial install via Firefox . . . in URL . . . localhost:631 . . . then use the cups add printer dialog to see if it finds suitable driver file(s) for your Brother.   If it doesn't, next step is to go back to system settings (prior to installing drivers from Brother website) and see if the add process finds and installs the correct driver(s).   Und Lastly . . . if the last step doesn't work - - go back to the Brother website and install the drivers from that source.   Often, Brother provides an initial script that loads all the drivers including the scanner  . . but perhaps that's not the case here.   Also as info, I always check Youtube also, for install methods and steps.   Sometimes that's better than the forums.

I've never had a Brother printer (always used either HP or Epson (the Epson "Workforce" line is excellent) but fileicht (perhaps . . ?) a forum member using a Brother printer will add better input.

:) I've never had a brother printer before either, I've always had canon.  This happened to be the cheapest available that did everything I wanted and was on sale at the computer store where they sell pre-installed ubuntu.

And I've dug through my cupboards, I'm going through divorce, my (soon to be ex-)husband moved out his stuff 10 days ago, and... there's no usb cable.  It's Sunday night, so no way to get one right now.  This made the decision easy to try pdc's idea first (the one posted just after yours).

---

### Post by lila on 2017-03-05
... this was funny, try if you see what happened here... :lolflag:

```
johnny@johnny-XS35V4:~$ cd Downloads
bash: cd: Downloads: Aucun fichier ou dossier de ce type
johnny@johnny-XS35V4:~$ cd downloads
bash: cd: downloads: Aucun fichier ou dossier de ce type
johnny@johnny-XS35V4:~$ cd téléchargements
bash: cd: téléchargements: Aucun fichier ou dossier de ce type
johnny@johnny-XS35V4:~$ cd Téléchargements
johnny@johnny-XS35V4:~/Téléchargements$ 
```

First I suspected your upper case, then I translated (lower case, which would be normal in French), then tried upper case again.  

It didn't seem to do anything with the gunzip:

```
johnny@johnny-XS35V4:~/Téléchargements$ gunzip linux-brprinter-installer-2.1.1-1.gz 
johnny@johnny-XS35V4:~/Téléchargements$ 
```

I'll try the last line...

OK.  I said yes to several licensing agreements, it did its install script and then asked me this (I said yes more out of "well, no might be wrong"):

(paste from terminal):
```
Will you specify the Device URI? [Y/n] ->y

0: ipp14
1: beh
2: ipp
3: http
4: lpd
5: hp
6: https
7: socket
8: ipps
9: hpfax
10: dnssd://Brother%20DCP-J562DW._ipp._tcp.local/?uuid=e3248000-80ce-11db-8000-7077818797a3
11: lpd://BRW7077818797A3/BINARY_P1
12 (I): Specify IP address.
13 (A): Auto. (dnssd://Brother%20DCP-J562DW._ipp._tcp.local/?uuid=e3248000-80ce-11db-8000-7077818797a3)

select the number of destination Device URI. ->
```

(end of paste)
My wild guess would be 13, because it says "Auto" and has the word brother buried in there, but I'd like a second opinion please! I'll leave the terminal open.

---

### Post by lila on 2017-03-05
It's getting late, I need to work tomorrow so I'm going to bed now.  I'll leave everything open and tell the computer to go into "veille" (what's it called ?  Not quite turned off, just dozing kind of state.  Too tired for English right now.)

---

### Post by pdc on 2017-03-05
dormez bien! dix or treize ....... 10 or 13 should surely be bien!

you are going well ......

---

### Post by gifford on 2017-03-06
lila,
If your printer is connected by wifi, it is a networked printer. The real issue with the scanner is that you need to do the manual install using the command line in the terminal to indicate the correct location on the network, ie., 192.168.0.2. As to you other question about MFC..it just stands for multi function..both printer and scanner.

---

### Post by lila on 2017-03-06
> **pdc said:**
> dormez bien! dix or treize ....... 10 or 13 should surely be bien!

you are going well ......

Merci!
I entered 13 and had to say yes to some more software agreements.  Now it's printing.  And the terminal asks me to enter the IP address for the scanner... ?????
If it's printing it's found it, no?  I don't get that.  And I don't know the IP address, how do I find it out?

---

### Post by lila on 2017-03-06
> **gifford said:**
> lila,
If your printer is connected by wifi, it is a networked printer. The real issue with the scanner is that you need to do the manual install using the command line in the terminal to indicate the correct location on the network, ie., 192.168.0.2. As to you other question about MFC..it just stands for multi function..both printer and scanner.

Thanks gifford, 
... where does that number come from?  Is that the IP address the terminal is asking me for?  I seem to have in the back of my head that IP is Internet Provider (which opens new questions - why do I need an Internet address to be able to use my scanner?).  And in that case, how do you know mine (assuming it is mine)?  If it's not the IP address, if you know the correct location on my network, why doesn't the software (this being its job)?  This leaves me more than confused...

---

### Post by pdc on 2017-03-06
hi lila

to find the IP address of the printer, 

in post #9 in this thread, someone describes the steps on their Brother MFC-9840CDW

 [https://ubuntuforums.org/showthread.php?t=802781](https://ubuntuforums.org/showthread.php?t=802781)

hopefully its menu is similar to your newer DCP ....... it should be in the printer; 

bonne chance

---

### Post by Geoffrey_Arndt on 2017-03-07
Lila . . . the IP address can be found by looking at your printer settings screen (on the printer . . . the little display window) . . . . 

You should see a menu like "setup" or "maintenance" or something similar to that.   Then you should see some sub-menus including "wireless" or "networks" or something like that.   If you select that (usually via the OK button or similar), you should see some info including your wireless address for the printer.    Also, there is usually a report that you can choose to print (from that same menu screen) that will provide a full networking report that also has the IP address.

And no, the other poster DID NOT have your specific printer IP address . . . . it was just an example Lila.

---

### Post by gifford on 2017-03-07
Lila,
Unfortunately, there is really know easy way to find the printer IP address of your printer. Try following the advice in the above post. If the info is not forthcoming, you can install arp-scan which should give you the address. 
Install by running "sudo apt-get install arp-scan" in the terminal. After installing, in your terminal use this command "sudo arp-scan --interface=eth0 --localnet". Leave our the quotation marks in the terminal. Hope this solves your problem.

---

### Post by lila on 2017-03-07
:P
Thank you everyone!  Actually, once I looked in the printer rather than in the computer, it was very easy to find.  I put it in the terminal and the installation process was complete.  

And... drumroll... xsane no longer tells me that there is no device available.  It now tells me there was an error opening it.  A non-valid parameter (paramètre non valable).  Which is progress I guess.  It just doesn't tell me which parameter is invalid.  Good job I'm not totally desperate to use the scanner, only a little bit.  As it is, I still find the whole thing amusing and interesting, rather than frustrating (which happens when I really need something to work and it doesn't).  

So I tried simplescan instead of xsane (you never know).  It first looked fine, but then said "connection to scanning device impossible" (again, my translation).  But simple scan also used to say that there is no scanning device.  So at least they now seem to know it's there.  

Where do I go from here?

---

### Post by lila on 2017-03-07
I posted a reply maybe 20 minutes ago and it's marked that I have on the thread (last post by lila), but it doesn't seem to appear.  Sorry if this a the same thing again.  

So, thank you everyone for all your input.  I found the IP address easily (once I was looking on the printer), and finished the installation without further problems.  

Now both xsane and simple scan no longer tell me they can't find a scanning device.  Instead they tell me they can't connect to it.  Simple scan simply says "Connection impossible", x-sane says something about an invalid parameter.  but it doesn't specify which parameter.  Both say they are trying to connect to DCP-J562DW, so that's progress.  

Now what do I do?

---

### Post by Geoffrey_Arndt on 2017-03-07
Here's another good source of info - - that may be easier to follow than just text based forums.     

Watch each video in turn and take notes.    [https://www.youtube.com/results?search_query=Brother+DCP-J5620DW+Linux](https://www.youtube.com/results?search_query=Brother+DCP-J5620DW+Linux)

---

### Post by pdc on 2017-03-07
so lila we hope some progress is slowly being made;

in post #3 Gifford suggested you try the Brother command in a terminal that is in the format of 

```
Brsaneconfig4 -a name=(name your device) model=(model name) ip=xx.xx.xx.xx
```

so that might look something like ```
Brsaneconfig4 -a name=Lila_scanner model=DCP-J562DW ip=xx.xx.xx.xx
``` ....... where you add the IP address;

_________________

Brother quote the above on this page [http://support.brother.com/g/s/id/linux/en/instruction_scn1b.html?c=us_ot&lang=en&redirect=on](http://support.brother.com/g/s/id/linux/en/instruction_scn1b.html?c=us_ot&lang=en&redirect=on)

bonne chance

(I was hoping the Brother installer tool would be able to issue the above command but it seems valuable to do it manually)

---

### Post by gifford on 2017-03-07
Lila,
Please try the configuration as outlined in the above listing by pdc. Hoping this will fix the issues you are having.
In my experience, using the terminal and command line to install Brother printers and scanners has always worked. Not so with
the Brother installer tool.

---

### Post by Geoffrey_Arndt on 2017-03-07
OK, did some more checking why scanner is being "problematic" (as I think you've done everything right so far).

So, here is another youtube video about Brother Scanner that shows what to do to overcome a "bug" in Ubuntu 16.04 and 16.10.   The problem is a missing file that is required for the scanner to work.

The video shows how to take care of this problem.    Please let us know if the scanner is working after doing this procedure.   (and if so, please mark this thread as "Solved" by using the thread tools in the upper menu).

[https://www.youtube.com/watch?v=Ci0TkfdXGUQ](https://www.youtube.com/watch?v=Ci0TkfdXGUQ)


Danke

GG

---

### Post by pdc on 2017-03-07
good work; well researched Geoffrey; I remember some posts now ........        the little grey cells are failing ............ [https://ubuntuforums.org/showthread.php?t=2343343&highlight=libusb-0.1-4](https://ubuntuforums.org/showthread.php?t=2343343&highlight=libusb-0.1-4)

checking in our install of Mint, I see that it is standard in Mint ....... must be optional for Ubuntu 

if you check Lila if [COLOR="#0000FF"]libusb-0.1-4[/COLOR] is installed; if not, see if that is the magic we all need

---

### Post by lila on 2017-03-08
> **pdc said:**
> so lila we hope some progress is slowly being made;

in post #3 Gifford suggested you try the Brother command in a terminal that is in the format of 



so that might look something like  ....... where you add the IP address;

_________________

Brother quote the above on this page [http://support.brother.com/g/s/id/linux/en/instruction_scn1b.html?c=us_ot&lang=en&redirect=on](http://support.brother.com/g/s/id/linux/en/instruction_scn1b.html?c=us_ot&lang=en&redirect=on)

bonne chance

(I was hoping the Brother installer tool would be able to issue the above command but it seems valuable to do it manually)


Hello everyone, 
thanks again for all your help!
I'll try to work through it all until it's sorted out.  This sounded like it might do the trick.  But when I ran it, it returned: 
Brsaneconfig4*: commande introuvable (Command cannot be found).

Also, REALLY strange, yesterday I did that whole setting up thing where I needed the printer's IP address which you all told me how to find on the printer's display.  And while it was a very memorable (too easy) suite of numbers, just now I wasn't sure about where the dots went, so I looked it up again.  And today, it gives me a completely different (much more random) IP address.  ????? Surely, that's not normal?

Anyway, yesterday I used one IP address, and just now a completely different one.  I'm not surprised it doesn't work.  I've written this one down on a piece of paper.  Just in case it changes again.  I found them both in the same place in the settings menu, I remember the pathway.  It's definitely changed since yesterday.

---

### Post by lila on 2017-03-08
> **pdc said:**
> good work; well researched Geoffrey; I remember some posts now ........        the little grey cells are failing ............ [https://ubuntuforums.org/showthread.php?t=2343343&highlight=libusb-0.1-4](https://ubuntuforums.org/showthread.php?t=2343343&highlight=libusb-0.1-4)

checking in our install of Mint, I see that it is standard in Mint ....... must be optional for Ubuntu 

if you check Lila if [COLOR="#0000FF"]libusb-0.1-4[/COLOR] is installed; if not, see if that is the magic we all need


Yes, according to synaptic, libusb-0.1-4 is installed.  But talking about usb, I still have no cable, so that probably doesn’t make a difference?  I simply haven't had the time to get one during store opening hours. I deal with the computer once my kid is asleep...  Am I wasting everybody's time here in trying to sort the problem without a cable (via wifi)?  If you say yes, I'll go and get one tomorrow lunchtime.

---

### Post by lila on 2017-03-08
> **Geoffrey_Arndt said:**
> OK, did some more checking why scanner is being "problematic" (as I think you've done everything right so far).

So, here is another youtube video about Brother Scanner that shows what to do to overcome a "bug" in Ubuntu 16.04 and 16.10.   The problem is a missing file that is required for the scanner to work.

The video shows how to take care of this problem.    Please let us know if the scanner is working after doing this procedure.   (and if so, please mark this thread as "Solved" by using the thread tools in the upper menu).

[https://www.youtube.com/watch?v=Ci0TkfdXGUQ](https://www.youtube.com/watch?v=Ci0TkfdXGUQ)


Danke

GG

Thanks for that, I watched it, it wants me to install the same libusb that pdc wanted me to go check if I have it.  It's already there. And yes, I will mark this thread as solved in the end... when it is.  I'm confident we'll get there!;)

---

### Post by lila on 2017-03-08
> **Geoffrey_Arndt said:**
> Here's another good source of info - - that may be easier to follow than just text based forums.     

Watch each video in turn and take notes.    [https://www.youtube.com/results?search_query=Brother+DCP-J5620DW+Linux](https://www.youtube.com/results?search_query=Brother+DCP-J5620DW+Linux)

I had a look at those that seemed vaguely relevant (I did leave out stuff like how to thread a brother sewing machine...:D ).  I haven't really found anything new.  Some I didn't get very far with because I didn’t understand the language and they were simply too much talking, not enough visuals.  Maybe I'm not looking closely enough, and I must admit after a while it all sounds so terribly familiar, it's like, I'm sure I've already tried this.  That's the problem with kind of getting to know a subject a little bit, but not really grasping the details.

---

### Post by Geoffrey_Arndt on 2017-03-08
Did you ever get a usb printer cable?

Have you tried scanning using Xsane?

Have you tried scanning from the printer (not the PC)?

---

### Post by pdc on 2017-03-08
lila: my apologies; I copied the brscanconfig4 command from an earlier post; and in that a capital B was used ....... linux is very fussy ........ so it rejects that; my mistake in not spotting that;

you rightly commented on the changing ip address ......... some folks recommend what is called a STATIC IP ADDRESS ...... so it doesn't change .... but if we try the command that I recommended earlier; _with whatever ip address your Brother is currently giving you_ ..

so the format is ```
brsaneconfig4 -a name=(name your device) model=(model name) ip=xx.xx.xx.xx
```

and the command we want is ```
brsaneconfig4 -a name=Lila_scanner model=DCP-J562DW ip=xx.xx.xx.xx
```      ........ if you add in the ip address please ........ if you try that, and see how we do please ...... my apologies for missing the Upper case error

---

### Post by slickymaster on 2017-03-09
@pdc:
I've edit several of your posts in this thread. Please don't use quote tags when posting output code. Output code posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The [use of code tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") makes the post clean, compact and more appealing.

---

### Post by lila on 2017-03-09
> **Geoffrey_Arndt said:**
> Did you ever get a usb printer cable?

Have you tried scanning using Xsane?

Have you tried scanning from the printer (not the PC)?

- No cable yet, but I'll get one tomorrow when I go shopping anyway.

- xsane, yes, both on its own and via gimp. No luck.

- scanning from the printer... no, not tried that yet, hang on... 
ah, option 1: scan to a file on your pc.  Tried that, "No PC is found on your network."
The other options also wanted a connection to my PC.  So the PC can't see the printer properly, and the printer can't see the PC at all.

---

### Post by lila on 2017-03-09
> **pdc said:**
> lila: my apologies; I copied the brscanconfig4 command from an earlier post; and in that a capital B was used ....... linux is very fussy ........ so it rejects that; my mistake in not spotting that;

you rightly commented on the changing ip address ......... some folks recommend what is called a STATIC IP ADDRESS ...... so it doesn't change .... but if we try the command that I recommended earlier; _with whatever ip address your Brother is currently giving you_ ..

so the format is ```
brsaneconfig4 -a name=(name your device) model=(model name) ip=xx.xx.xx.xx
```

and the command we want is ```
brsaneconfig4 -a name=Lila_scanner model=DCP-J562DW ip=xx.xx.xx.xx
```      ........ if you add in the ip address please ........ if you try that, and see how we do please ...... my apologies for missing the Upper case error

OK... So, I've tried this, and in the terminal nothing happened.  I got no return message I mean, just a new prompt.  So I tried to scan via xsane... and, progress, it opened with the xsane logo and gave me the option between two printers, DCP-J562DW and lila_Scanner.  I tried both, but both have the same error message of no connection possible as before.  But I think my printer may now be installed twice.  Which is not a problem.  If only one of them worked properly... ;)

---

### Post by Geoffrey_Arndt on 2017-03-09
Once your printer is connected via USB "printer cable" . . . chances for detection and proper operation increase greatly.
-------------------------------------------------------------------------------------------------------------------------------

Also, does your printer have a port for SD card or usb-flash stick?   If it does, then that is a device the manual scan from the printer will see and offer to scan the output to.
-------------------------------------------------------------------------------------------------------------------------------

---

### Post by gifford on 2017-03-10
Lila,

The line should have been:
```

brsanconfig4 a name=SCANNER model=DCP-J562DW ip=xx.xx.xx.xx

```

---

### Post by pdc on 2017-03-11
Lila:

is your system 32bit please? you can tell by typing ```
uname -a
``` into a terminal

---

