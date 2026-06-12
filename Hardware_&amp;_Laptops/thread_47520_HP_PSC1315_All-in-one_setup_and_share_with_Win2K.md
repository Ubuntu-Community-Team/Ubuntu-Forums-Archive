---
title: "HP PSC1315 All-in-one setup and share with Win2K"
date: 2005-07-08
forum: Hardware &amp; Laptops
---

### Post by amohanty on 2005-07-08
Hi All,

After searching and reading through lots of posts, I have finally been able to use my HP PSC-1315 All-in-One USB printer for printing and scanning from Ubuntu and been able to share it with my Win2K & WinXP laptops. Most of the material here has been gleaned from various locations on these forums. My hope is that this might help someone get to a state of eternal bliss asap :grin: 

So here goes:

Part 1. Setup PSC1315 in Ubuntu.
This is a quick and dirty rehash of a pretty nice HowTo [here](https://wiki.ubuntu.com/HpPscHpPhotosmartSeriesAllInOnePrinters):
  a. Add the 'universe' repository. [[How]](http://https://wiki.ubuntu.com/AddingRepositoriesHowto)
  b. Install hpoj package: sudo apt-get install hpoj 
  c. Configure hpoj: sudo /etc/init.d/hpoj setup
        - just run through all the prompts pressing enter... 'It just works(T$M)'
        - if you would like to use a name other than the default one this is the place to do it.
  d. Start hpoj service: sudo /etc/init.d/hpoj start
  e. Restart cupsys service: sudo /etc/init.d/cupsys restart
  f.  Goto System->Administration->Printers & select 'New Printer'
  g. Select 'Use another printer by specifying a port' and select the name starting with 'ptal' from the dropdown underneath it.
   h. Click 'Forward' and select PSC1310, you can get away with this model for most 13xx series printers.
   g. Viola! you are all set and can now print.

Part 2. Sharing with Win2K (XP is pretty much the same)
Parts gleaned from [here](http://www.owlfish.com/thoughts/winipp-cups-2003-07-20.html)
  a. copy /etc/cups/cupsd.conf to /etc/cups/cupsd.conf.orig
  b. edit /etc/cups/cupsd.conf
  c. Add the following line Allow From 192.168.X.* X being the third octet used in your internal network. Usually 0, 1 or 10.
  d. You can use the abbreviated version below. Except the abovementioned line everything else is the default. Just cleaned up:
    
DefaultCharset notused
LogLevel info
Printcap /var/run/cups/printcap
RunAsUser Yes
Port 631
Include cupsd-browsing.conf

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.0.*
</Location>

<Location /jobs>
AuthType Basic
AuthClass User
</Location>

<Location /admin>
AuthType Basic
AuthClass System
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
</Location>
    
  e. Restart cups: sudo /etc/init.d/cupsys restart
  f. Now if you go to http://<your ip here>/printers you should see your printer there.

  g. In windows, now if you go to the URL in (f) you should be able to see the printer there.
  h. Go to Control Panel->Printers->Add Printer
  i. If you dont want to deal with ips and would like to use a hostname:
      - Type <Win><r>
      - Type %SYSTEMROOT%\system32\drivers\etc
      - This will open explorer. Right click on the hosts file and uncheck Read-only.
      - Edit hosts
      - Add line <your ip here>     <your hostname here>
  j. In the 'Add Printer Wizard, Select 'Network Printer'
  k. Click Next
  m. Select 'Connect to printer on the Internet....'
  n. In 'URL' type: http://<your ip or hostname>/printers/<printername as seen in (f)>
  o. Click 'Next' and you will be prompted for drivers. 
  p. Click 'Ok'
  q. In the dialog that comes up on the left select 'Generic' and then on the right select 'MS Publisher Imagesetter'
  r. Click through the rest of the process and you have your networked printer.

Hope you find it useful.

AM

---

