---
title: "CUPS Problems with 7.10"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by tootlet on 2007-10-21
Greetings,
I upgraded to 7.10. This has been smooth except for printing. Under 7.04 I had tried to connect to an OpenSUSE 10.2 computer that I've used with SAMBA as a print server to my Windows boxes. I could never configure Ubuntu to print to it. So I decided to get an HP DirectJet 300x external print server. No trouble configuring the OpenSUSE or Windows boxes but I'm running into difficulties with Ubuntu 7.10. 

When I go to System-Administration-Printing I get an error:
Error There was a problem connecting to the cups server
If I use Firefox and access CUPS by [http://localhost:631](http://localhost:631) I was able to add the printer through the HPDirectJet and print a test page but could never print from any applications. Thought this might be a problem as I hadn't established a root password for CUPS. So I did
sudo lppasswd -g sys -a root. 
Still couldn't get it to print. Then I decided to delete this printer. There was still the printer in CUPS of the failed printer setup with the OpenSUSE box. So I tried to delete this printer in CUPS. Got the message:
Unable to connect - Firefox can't establish a connection to the server @theGurg.home:631
Okay, so I went into /etc/cups and looked at all the files. Nothing about this printer "@the Gurg.home:631" was found. 

Getting desperate. So I tried a suggestion from one of the forums. 
sudo /etc/init.d/cupsys restart 
then
gksudo system-config-printer
and got the good ole Error - there was a problem connecting to the CUPS Server. Yeah! I'm making real progress now! When in doubt, nuke it. So following the suggestions from a different forum post I uninstalled cups.
sudo apt-get remove cupsys cupsys-client
sudo apt-get --purge cupsys cupsys-client
sudo apt-get install cupsys cupsys-client. That should get me back to square one where i can start over....Right?
System-->Administration-->Printing gets me Error - There was a problem connecting to the Cups Server
[http://localhost:631/printers](http://localhost:631/printers) and still the Default Printer is listed as on theGurg.home:631 and won't let me delete it.
I am stymied. Very tempted to do a clean install...after backing up my xorg.conf file as I had trouble getting my Acer AL2216W configured correctly. Any hints, advice or good swear words?
Tom

---

### Post by tootlet on 2007-10-21
Reinstalled 7.10
Administration-->Printing-->HP JetDirect. Put in IP address and she printed. Took all of 20 minutes including install. Sometimes what seems like the hard way is the easy way!

---

