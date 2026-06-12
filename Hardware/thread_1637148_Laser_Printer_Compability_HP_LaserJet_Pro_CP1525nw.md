---
title: "Laser Printer Compability: HP LaserJet Pro CP1525nw"
date: 2010-12-04
forum: Hardware
---

### Post by ubuntu27 on 2010-12-04
Hi all! I am looking to buy a new Color Laser Printer.

And so far my eyes are on HP
LaserJet Pro CP1525NW. HP website mentions that it is compatible with Linux. However, this particular model cannot be found at [Linux Foundation]("http://www.linuxfoundation.org/")'s [OpenPrinting Database]("http://www.linuxfoundation.org/collaborate/workgroups/openprinting/database/databaseintro").
As you [can see here]("http://www.openprinting.org/printers/manufacturer/HP"), there is no mention of HP LaserJet Pro CP1525N which makes me worried.

Also, the printer is not listed in [HP Linux imaging and printing]("http://hplipopensource.com/hplip-web/index.html").

**What are your thoughts and do you have experience with this printer? What other Color Laser printer do you recommend?**

The fact that the that printer's specification on HP website says that it is compatible with Linux, yet it is not listed on HPLIP nor in Openprinting makes me nervious.

Thank you all!

---

### Post by Spyderkid on 2010-12-04
Almost all HP printers have drivers on them the computer looks on the printer or internet nd finds it downloads it and installs

I would suggest to get a kodak ESP 5210 and download the driver off souceforge like i have done works a dream

And saves millions on ink it costs over £50 to replace the ink on an HP

and £19 on a kodak

it works really well the driver I can post a link if you want.

---

### Post by Spyderkid on 2010-12-04
[Heres the kodak esp 5000 seriese driver]("http://sourceforge.net/projects/cupsdriverkodak/reviews/")

---

### Post by ubuntu27 on 2010-12-04
Hello Spyderkid. Thank your for your response.

I will mark thsi thread as solved since my mother returned with a "new" printer that she bought from a moving sell. And this printer does work with Linux it seems ( I just made a print test, and it works), thought it is not in OpenPrinting.org


Thank you all!

PS: The printer is HP PSC 1315xi all-in-one

---

### Post by mriendea on 2011-02-14
I have had some preliminary luck with the CP1525NW printer, using the HP -> Laserjet M1522 MFP Series Postscript [en] driver Ubuntu 10.04 64 bit.

---

### Post by ofir_k on 2011-02-19
> **mriendea said:**
> I have had some preliminary luck with the CP1525NW printer, using the HP -> Laserjet M1522 MFP Series Postscript [en] driver Ubuntu 10.04 64 bit.

Hi, I have the CP1525n printer, and I am too unable to find a proper driver.

I contacted HP through the HPLIP website. Here is a summery of the [ticket]("https://answers.launchpad.net/hplip/+question/143563"):
> 
Hello,

I just got my new HP printer. I originally ordered HP Color LaserJet CP1515n, but I was told that there is a newer model and that I should take it. So I took it. The newer model is HP Color LaserJet CP1525n.

**Before taking the newer model, I consulted the HP website:**
[http://h10010.www1.hp.com/wwpc/us/en/sm/WF06a/18972-18972-3328060-15077-3328070-4052975.html](http://h10010.www1.hp.com/wwpc/us/en/sm/WF06a/18972-18972-3328060-15077-3328070-4052975.html)
This page says that Ubuntu (and Linux in general) IS supported.

Now, when I try to install the printer, I see that the printer IS NOT supported by HPLIP.

Can someone please explain me why the HP website says something and the HPLIP website says something else?

Ofir
 

> 
Hi,

 I am sorry to inform you that presently we are not supporting HP Color LaserJet CP1525 printer on Linux. We might be supporting in next release but we can not guarantee a fixed timeline.
 If you wish to have a printer that works on Linux, always go to site [http://hplipopensource.com/hplip-web/supported_devices/index.html](http://hplipopensource.com/hplip-web/supported_devices/index.html) and check if it is supported on Linux and you can consider your purchase for the right model type.

 Please wait for next HPLIP release so that your model will be supported.

Thanks and Regards
Ani Balakrishnan


I really hope that the driver for this printer will be included in the next HPLIP release (maybe if more users will contact them through [commenting here]("https://answers.launchpad.net/hplip/+question/143563"), and demanding the driver, it will be released sooner).

---

### Post by tiezemans on 2011-03-02
There is a proper driver for the CP1525nw though. Follow the instructions on this page: [http://h30434.www3.hp.com/t5/Printer-All-in-One-Install-and/cp1525nw-and-mis-leading-selling/td-p/416257](http://h30434.www3.hp.com/t5/Printer-All-in-One-Install-and/cp1525nw-and-mis-leading-selling/td-p/416257)

Works like a charm for me. The test page prints out a nice Ubuntu logo and everything.

---

### Post by tiezemans on 2011-03-02
Might as well print it here. With thanks to odinb from the other forum:

On Ubuntu, Do the following:
Go to "System" > "Administration" > "Printing".
Then from the window that opens up, you choose "Add", then click "Network Printer" and "Find Network Printer", then wait about 5-10 seconds, and you should see the "HP LaserJet CP1525nw" listed twice.
Choose the one that has the IP-address of the printer in round brackets. The one with the Mac address in round brackets will not work.
Click "Forward" and then pick "HP" from the list, click "Forward" again, then pick "Color LaserJet" from the list, and the driver "HP Color LaserJet Series PCL 6 CUPS".
Click "Forward", and "Forward" a second time since we have no duplexer on this unit, and finally chosse a name (or use the pre-filled one if you like) and finally click "Apply". Now you can print a test page, and then you are done!
 
I do not run Suse, so I cannot tell how to do this on Suse, but Suse runs gnome per default if I remember right, and it definitely uses CUPS, which is where the "HP Color LaserJet Series PCL 6 CUPS" driver comes from.

---

### Post by geo316 on 2011-04-20
> **tiezemans said:**
> 
Go to "System" > "Administration" > "Printing".
Then from the window that opens up, you choose "Add", then click "Network Printer" and "Find Network Printer"...

May I add that if you first connect the printer to your router via ethernet, then go to the front panel of the printer, enter the menu by pressing "ok". Then use the right arrow to scroll to "network setup", press ok, then right arrow to scroll to "tcp/ip config". Press "ok" then arrow scroll to "manual". Press "ok" then enter a valid and unused IP address for a device on your network. Press "OK" to save it and "x" to exit the menu.

Then enter that IP address into a web browser on a computer also on your network, you should see a web page generated by the printer. Go to the "networking" tab. There you can change settings for ethernet (ip4) and wireless.

I add these instructions because your printer may not be able to connect to your network right out of the box, which means you won't be able to do the "find printer" step in Ubuntu as described by tiezemans above...

Also if the "find printer" fails, enter the IP address of the printer into the "host" field, then press the "find" button...

Hope this helps.

---

### Post by shadowFlax on 2011-08-01
Beautiful ... worked perfectly. Thanks

---

### Post by buttertoad on 2011-08-02
I just wanted to add that I just installed hplib version 3.11.7 from the website and it does include the CP1525nw now.

---

### Post by aer0usa on 2011-10-11
> **tiezemans said:**
> Might as well print it here. With thanks to odinb from the other forum:

On Ubuntu, Do the following:
Go to "System" > "Administration" > "Printing"...


Thanks for posting this! This (similar) worked great on Hardy Heron!

---

### Post by Vinvilland on 2011-10-19
I cannot get my printer to print more than one page at a time, and it takes a long time. I use CUPS if that helps thank you.

---

### Post by odinb on 2012-01-22
Here is an update to my earlier workaround with the "Color LaserJet" driver to get this printer going.

With this update, it will be a lot speedier printing your pictures and color pages!

Verify what version of HPLIP you have by issuing the following command:
```
apt-cache showpkg hplip
```
or by checking with your package manager.

If not installed, please install it, if you have version 3.11.5 or newer, skip to part B, if not start here:

Part A.
Updating HPLIP to version 3.11.5 or newer:
Run the following command to add the PPA repository for HPLIP:
```
sudo add-apt-repository ppa:hplip-isv/ppa
```

After this, you will want to upgrade your system:
```
sudo aptitude update && sudo aptitude safe-upgrade && sudo apt-get autoclean && sudo apt-get autoremove
```

Once done, you are ready to install the HPLIP Binary Plug-In.

Part B.
The HPLIP Binary Plug-In is needed to get the driver to install properly. To install it, run the following command:
```
sudo hp-setup
```
and follow the prompts to install:

1. Select your connection type and click "Next".

2. Select your printer from "Selected Devices" list and click "Next".

3.  Use the recommended installation method and click "Next".

4.  Check the box to accept with the "Driver Plug-In License Agreement" and click "Next".

5.  Finish the installation of the printer as normal.


[PPA page link.]("https://launchpad.net/~hplip-isv/+archive/ppa")

[HPLIP Binary Plug-In page.]("http://hplipopensource.com/node/309")

Good luck!

---

### Post by mörgæs on 2012-01-22
Thanks for some good advice. 
Moved to the hardware forum.

---

### Post by xianbei on 2012-01-26
My experience:

Ubuntu 11.10

Click System Settings > Printing > Add

Enter address of printer once it has network access (in my case 192.168.1.106)

Click HP Linux Imaging and Printing (HPLIP)

Choose HP > go with recommended (HP 1520 series)

Voila!

---

### Post by jeremy on 2012-04-04
I have followed this and other threads, and got my cp1525nw working perfectly with ubuntu 11.10, using hp1520 series, as in the previous post.
Now I am using ubuntu 12.04, and hp1520 series is not available in the list. Does anyone have any advice, ideas?

---

### Post by odinb on 2012-04-11
To get this printer to work (under 12.04) you need HPLIP 3.12.4 according to HP. But as you have noticed, 12.04 only comes with HPLIP 3.12.2. Problem is, currently you need to compile this from source if you fetch it from HP. HP apparently cannot understand the benefits of a package manager, they keep doing it the windows way by "brute-forcing" stuff onto peoples computers.

The way I solved it was, I ran the following from the command prompt:
```
sudo hp-setup
```

Then follow the prompts until last page, where you see it chose the wrong printer. At this point, point it to the ppd used on your older machine.
It can be found in "/etc/cups/ppd/HP_LaserJet_CP1525nw.ppd".

If you do not have it, I have attached it here also.

Happy printing!


//Odin

---

### Post by jeremy on 2012-04-15
odinb, thanks so much, that did the trick beautifully!

---

### Post by denisk on 2012-11-13
Just wanted to update everyone that this printer works with Kubuntu 12.04 out of the box - no installation needed, printer appears in "Printer Configuration" after being plugged into USB. Takes a while to warm up, but works fine afterwards.

---

