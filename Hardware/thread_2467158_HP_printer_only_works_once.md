---
title: "HP printer only works once"
date: 2021-09-17
forum: Hardware
---

### Post by Autodave on 2021-09-17
HP inkjet will print fine until PC is rebooted.  To get it to print again, I have to remover the printer, reboot, and reinstall the printer.  Then it will work fine until rebooted again.  What to try?

---

### Post by Autodave on 2021-09-17
Some more info since this is not my personal machine.  Running 20.04 and fully updated.  This is a 10 year old machine with 8 gig RAM.  Printer is an HP Deskjet 3630.  Hplip installed.  Hooked by USB cable.  If I delete everything hplip related and reboot and then install hplip again and reboot, printer works fine for as long as PC is left running.  Reboot the PC and printing does not work.  Will sometimes get a message saying that there is a driver missing and offers the internet to get one.  Going to HP's website, there is no HP 3630 listed.  So, you remove everything hplip related, reboot, reinstall, reboot and it works.  I have no ideas on this.

---

### Post by tea for one on 2021-09-17
> **Autodave said:**
> Going to HP's website, there is no HP 3630 listed. 

I found this [https://support.hp.com/gb-en/printer-setup/hp-deskjet-3630-all-in-one-printer-series/7172306](https://support.hp.com/gb-en/printer-setup/hp-deskjet-3630-all-in-one-printer-series/7172306)

Hopefully, it will get the ball rolling.

---

### Post by Autodave on 2021-09-18
Been there and done that.....still can't find the exact printer.  But forgetting about that, just consider that after installing hplip and rebooting, the printer works just fine, so it obviously has a good driver.  The problem comes after you reboot and it won't work until hplip is removed, PC rebooted, hplip reinstalled, PC rebooted.  Then it works.

---

### Post by brian_p on 2021-09-18
Please give ```
dpkg -l ippusbxd
```

---

### Post by Autodave on 2021-09-30
betty@betty-p6-2316s:~$ dpkg -l ippusbxd
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version       Architecture Description
+++-==============-=============-============-==================================
ii  ippusbxd       1.34-2ubuntu1 amd64        Daemon for IPP USB printer support
betty@betty-p6-2316s:~$

---

### Post by Autodave on 2021-10-02
bump

---

### Post by brian_p on 2021-10-02
i**ppusbxd ** is a suboptimal utility and even its author would agree there is a better way of handling a USB-connected device. It has now been removed from Ubuntu and replaced by **ipp-usb**. I suggest:

[LIST]
[*]Switch printer off and disconnect from USB.
[/LIST]
[LIST]
[*]Purge ippusbxd.
[/LIST]
[LIST]
[*]Read [https://github.com/alexpevzner/sane-airscan](https://github.com/alexpevzner/sane-airscan).
[/LIST]
[LIST]
[*]Download and install **ipp-usb** and **sane-airscan** from [https://download.opensuse.org/repositories/home:/pzz/xUbuntu_20.04/amd64/](https://download.opensuse.org/repositories/home:/pzz/xUbuntu_20.04/amd64/).
[/LIST]
[LIST]
[*]Reverse the first step.
[/LIST]

---

### Post by Autodave on 2021-10-04
No good.  I did what you suggested.  As usual, after removing and re-installing the hplip, the printer printed just fine.  Waited a few minutes while I did other things on the machine and tried printing again.  No probs.  Rebooted and tried to print: nothing.  Document is showing as waiting.  I cannot release it.  If I try to print it again I get a message that the printer is not found and it suggests a bad or disconnected cable.  I have tried another cable just to be sure.  

This printer does have wireless capability and I wonder if I would put a wifi card in the PC if that might make it work better?

---

### Post by T6&amp;sfpER35% on 2021-10-04
> [COLOR=#000000]This printer does have wireless capability and I wonder if I would put a wifi card in the PC if that might make it work better?[/COLOR]

or you could connect printer to your home network ( i assume you have a router) , so you won't have to buy a wifi card

---

### Post by Autodave on 2021-10-04
> **3nd said:**
> or you could connect printer to your home network ( i assume you have a router) , so you won't have to buy a wifi card

This is a printer that is located in a relative's home.  I can access it using TeamViewer and rest it, but that is a hassle that I would like to eliminate.

---

### Post by brian_p on 2021-10-04
> **Autodave said:**
> No good.  I did what you suggested.  As usual, after removing and re-installing the hplip, the printer printed just fine.  Waited a few minutes while I did other things on the machine and tried printing again.  No probs.  Rebooted and tried to print: nothing.  Document is showing as waiting.  I cannot release it.  If I try to print it again I get a message that the printer is not found and it suggests a bad or disconnected cable.  I have tried another cable just to be sure. 

The 3630 is a modern printer. The technique  I gave you replaces HPLIP as a manager of printing. In fact, HPLIP may as well be purged from the system. ```
systemctl status ipp-usb
``` should show the service as active. Another check would be to give ```
avahi-browse -rt _ipp._tcp
``` ```
avahi-browse -rt _uscan._tcp
``` 

> 
This printer does have wireless capability and I wonder if I would put a wifi card in the PC if that might make it work better?

Given a sound USB connection (cable, external USB HUB etc), I cannot see it making any dufference.

---

### Post by Autodave on 2021-10-04
> **brian_p said:**
> The 3630 is a modern printer. The technique  I gave you replaces HPLIP as a manager of printing. In fact, HPLIP may as well be purged from the system. ```
systemctl status ipp-usb
``` should show the service as active. Another check would be to give ```
avahi-browse -rt _ipp._tcp
``` ```
avahi-browse -rt _uscan._tcp
``` 



Given a sound USB connection (cable, external USB HUB etc), I cannot see it making any dufference.

The first command did show it as being active.  However, when I went to exit out of the terminal, it said that there was a program running and closing the terminal would terminate the program???

---

### Post by brian_p on 2021-10-04
> The first command did show it as being active. However, when I went to exit out of the terminal, it said that there was a program running and closing the terminal would terminate the program??? 

Pass on that.

How about the result of the other two commands?

---

### Post by Autodave on 2021-10-04
betty@betty-p6-2316s:~$ avahi-browse -rt _ipp._tcp
+     lo IPv4 HP DeskJet 3630 series [452FF8] (USB)         Internet Printer     local
=     lo IPv4 HP DeskJet 3630 series [452FF8] (USB)         Internet Printer     local
   hostname = [betty-p6-2316s.local]
   address = [127.0.0.1]
   port = [60000]
   txt = ["air=none" "rp=ipp/print" "priority=50" "kind=document,envelope,photo,postcard" "PaperMax=legal-A4" "URF=CP1,MT1-2-8-9-10-11,PQ3-4-5,RS300,SRGB24,OB9,OFU0,W8-16,DEVW8-16,DEVRGB24-48,ADOBERGB24-48,IS1,V1.4" "UUID=1c852a4d-b800-1f08-abcd-9457a5452ff8" "Color=T" "Duplex=F" "note=" "qtotal=1" "usb_MDL=DeskJet 3630 series" "usb_MFG=HP" "usb_CMD=PCL3GUI,PJL,Automatic,JPEG,PCLM,AppleRaster,PWGRaster,DW-PCL,802.11,DESKJET,DYN" "ty=HP DeskJet 3630 series" "product=(HP DeskJet 3630 series)" "pdl=application/vnd.hp-PCL,image/jpeg,application/PCLm,image/urf,image/pwg-raster,application/octet-stream" "txtvers=1" "adminurl=http://localhost:60000/#hId-pgAirPrint" "Fax=F" "Scan=T"]
betty@betty-p6-2316s:~$ avahi-browse -rt _uscan._tcp
+     lo IPv4 HP DeskJet 3630 series [452FF8] (USB)         _uscan._tcp          local
=     lo IPv4 HP DeskJet 3630 series [452FF8] (USB)         _uscan._tcp          local
   hostname = [betty-p6-2316s.local]
   address = [127.0.0.1]
   port = [60000]
   txt = ["duplex=F" "is=platen" "cs=color,grayscale" "UUID=1c852a4d-b800-1f08-abcd-9457a5452ff8" "adminurl=http://localhost:60000/#hId-pgAirPrint" "representation=http://localhost:60000/webApps/images/printer-small.png" "pdl=application/octet-stream,application/pdf,image/jpeg" "ty=DeskJet 3630 series" "rs=eSCL" "vers=2.5" "txtvers=1"]
betty@betty-p6-2316s:~$

---

### Post by brian_p on 2021-10-05
The outputs of the two commands look OK to me. From my perspective ipp-usb is functioning correctly and should manage printing before and after a reboot. It shouldn't make any difference, but you could be daring and purge HPLIP.

---

### Post by Autodave on 2021-10-05
HPILP was purged before I installed ipp-usb.  After installing, the printer worked until PC was rebooted.  After reboot, printer failed to work.  I then reinstalled hplip and it worked.......until rebooted.

---

### Post by brian_p on 2021-10-05
> **Autodave said:**
> HPILP was purged before I installed ipp-usb.  After installing, the printer worked until PC was rebooted.  After reboot, printer failed to work.  I then reinstalled hplip and it worked.......until rebooted.

I really haven't any definitive answer to this. It is beginning to look like some fundamental issue. Try backing up cupsd.conf and doing ```
cp /usr/share/cups/cupsd.conf.default /etc/cups/cupsd.conf
``` ```
systemctl restart cups
```

No more ideas now. Apart from trying wireless.

---

### Post by Autodave on 2021-10-05
betty@betty-p6-2316s:~$ cp /usr/share/cups/cupsd.conf.default /etc/cups/cupsd.conf
cp: cannot create regular file '/etc/cups/cupsd.conf': Permission denied

---

### Post by brian_p on 2021-10-05
```
sudo cp /usr/share/cups/cupsd.conf.default /etc/cups/cupsd.conf
```

---

### Post by Autodave on 2021-10-06
Alright.....the plot thickens.  It will still only print until rebooted.  BUT, before, when it wouldn't print, I would go into Settings -> Printers and be able to see that there was a queued item waiting to be printed.  I could NOT release it.  But now, I can release it to be printed and it prints fine.  While this would be OK for me, this computer is being used by a 91 year old women!  There is no way I will be able to show her how to do this and her remember it.

---

### Post by QIII on 2021-10-06
The USB cable may be good, but have you tried experimenting with this as with any generic USB device:  Unplug the USB from the computer or the printer and then plug it back in again?

---

### Post by Autodave on 2021-10-06
> **QIII said:**
> The USB cable may be good, but have you tried experimenting with this as with any generic USB device:  Unplug the USB from the computer or the printer and then plug it back in again?

Too many times to count.  I have been repairing computers and audio equipment for too many years and that is usually the first thing that I try: disconnect everything, turn off and remove any batteries, wait 5 minutes, try again.  It still amazes me how many things can be "fixed" that way.

This problem has really been irritating.  I have never ever had any issue with an HP printer and Linux: they just work.  My Laser printer here was turned on when I installed 20.04 (I never do upgrades: always clean installs) and 20.04 connected WIRELESSLY to it without any input from me whatsoever!  You just can't get any simpler than that!

---

### Post by QIII on 2021-10-07
I've been at this since the '70s myself, but those "unplug it and plug it back in" problems are the ones you really kick yourself over.

Well, since I've always used HP products because they just work, color me as flummoxed as you are on this one.

---

### Post by Autodave on 2021-10-07
Lemme add another chapter to this ongoing saga:

She called last night saying that she couldn't print again.  I logged into her computer and "released" the job that was stuck.  It printed.  I asked her to print something else and it printed just fine with no intervention from me.  So, something happens on reboot that causes it not to print.  Once it is released of the stuck job, it is fine.  Until the next reboot.  Sigh.

---

### Post by brian_p on 2021-10-07
> **Autodave said:**
> Lemme add another chapter to this ongoing saga:

She called last night saying that she couldn't print again.  I logged into her computer and "released" the job that was stuck.  It printed.  I asked her to print something else and it printed just fine with no intervention from me.  So, something happens on reboot that causes it not to print.  Once it is released of the stuck job, it is fine.  Until the next reboot.  Sigh.

USB does not appear to be an issue because printing takes place. The printing filtering system also does not appear to be an issue because, again, printing takes place. The user experiences the problem with HPLIP and driverless printing with ipp-usb.

The only printing services I can think of being involved in a reboot are cups and cups-browsed. Suggestions:

[LIST]
[*]Print. Restart cups. Still  printing?[/LIST]
[LIST]
[*]Print. Restart cups-browsed. Still  printing?[/LIST]
[LIST]
[*]Leave the machine on overnight (or longer). cups is scheduled to restart itself in every 24 hour period. (Check the process ID of cupsd). Still  printing?[/LIST]

---

### Post by Autodave on 2021-10-08
Just saw this posted today......sounds very similar!  [https://ubuntuforums.org/showthread.php?t=2467793](https://ubuntuforums.org/showthread.php?t=2467793)

---

### Post by brian_p on 2021-10-10
> **Autodave said:**
> Just saw this posted today......sounds very similar!  [https://ubuntuforums.org/showthread.php?t=2467793](https://ubuntuforums.org/showthread.php?t=2467793)

If you can get any useful information from this user, you are welcome to try.

---

### Post by Autodave on 2021-10-11
Well, lemme update this.  3 days ago, I had a print job being held......and I was able to release it.  She called yesterday and stated that she had successfully printed something without having to do anything other than hit the PRINT button!  So, at the moment, it is working.  Will update further when I get info.

---

### Post by LarryJor on 2021-10-22
Hi.. I'm having similar problems with my HP 8020.. latest attempt (today) I got from running hp-doctor.  As others have reported with Ubuntu 20.04, I found that the ppd files couldn't be read.  I changed the permissions on those to 664 to correct that, but subsequently running hp-doctor still said it couldn't be read.  In addition, I connect via ip address, so I noticed it didn't have permission to access the address.  You'll get this if you connect with wireless.  If you have a firewall running, you'll need to tell the firewall to allow the computer to talk to the printer.  With 'ufw', that would be something like 'sudo ufw allow to 10.0.0.???' (replace question marks with your correct address).  You will also probably want to do 'sudo allow from ...' to get messages back from the printer (ink status, etc.).  I don't understand why this occurs myself, so hoping someone can add info about it all.  Maybe 'apparmour' interferes along with the firewall?  Hoping all this can be fixed soon.  It's crazy printing once and then needing to reinstall the printer next time I reboot.

---

