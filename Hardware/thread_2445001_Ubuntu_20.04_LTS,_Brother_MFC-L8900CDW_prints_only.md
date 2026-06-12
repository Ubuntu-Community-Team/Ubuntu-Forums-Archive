---
title: "Ubuntu 20.04 LTS, Brother MFC-L8900CDW prints only one copy"
date: 2020-06-07
forum: Hardware
---

### Post by esbmast on 2020-06-07
This issue is about the inability to print multiple copies of a document from an Ubuntu 20.04 machine.

Brother MFC-L8900CDW printer is plugged in to ethernet and assigned a static IP number since it's purchase 1.5 years ago.  Works perfectly with existing Macs and Windows boxes.

New install of Ubuntu 20.04 on newly built machine.  I downloaded the drivers from Brother ([https://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfcl8900cdw_all&os=128](https://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfcl8900cdw_all&os=128)) and installed them.

Printing seems to work fine as long as I only want one copy of a document.  If I change the quantity to any more than one, I still only get one copy.

This occurs using the print dialog boxes in all the applications and browsers I've tried so far.
It occurs when I print using the lp command, as in:
lp -n 2  -d MFC-L8900CDW test.txt

I have tried toggling the "collate" option in the print dialog box.
I have tried the following, changing (all copies found) of the MFC-L8900CDW.ppd file as follows:
 *cupsManualCopies: false
to
 *cupsManualCopies: true

Neither of these things helped.

Can anyone help with this?
Thanks,
Evelyn

---

### Post by brian_p on 2020-06-08
Hello Evelyn,

Please give what you get for ```
lpoptions -p MFC-L8900CDW
```

---

### Post by esbmast on 2020-06-08
Hi Brian,
Here's what lpoptions returns:
copies=1  device-uri=ipp://Brother%20MFC-L8900CDW%20series._ipp._tcp.local/  finishings=3 job-cancel-after=10800 job-hold-until=no-hold  job-priority=50 job-sheets=none,none marker-change-time=1591573113  marker-colors=#000000,#00FFFF,#FF00FF,#FFFF00,none,none,none  marker-high-levels=100,100,100,100 marker-levels=-1,-1,-1,-1,-1,95,88  marker-low-levels=10,10,10,10 marker-names='Black\ Toner\  Cartridge,Cyan\ Toner\ Cartridge,Magenta\ Toner\ Cartridge,Yellow\  Toner\ Cartridge,Waste\ Toner\ Box,Belt\ Unit,Drum\ Unit'  marker-types=toner,toner,toner,toner number-up=1  printer-commands=AutoConfigure,Clean,PrintSelfTestPage  printer-info='Brother MFC-L8900CDW series (cups)'  printer-is-accepting-jobs=true printer-is-shared=true  printer-is-temporary=false printer-location  printer-make-and-model='Brother MFC-L8900CDW CUPS' printer-state=3  printer-state-change-time=1591573113 printer-state-reasons=none  printer-type=8523868  printer-uri-supported=ipp://localhost/printers/MFC-L8900CDW

Thanks for any assistance/suggestions you can give.
Evelyn

---

### Post by brian_p on 2020-06-08
> **esbmast said:**
> Hi Brian,
Here's what lpoptions returns:
copies=1  device-uri=ipp://Brother%20MFC-L8900CDW%20series._ipp._tcp.local/  finishings=3 job-cancel-after=10800 job-hold-until=no-hold  job-priority=50 job-sheets=none,none marker-change-time=1591573113  marker-colors=#000000,#00FFFF,#FF00FF,#FFFF00,none,none,none  marker-high-levels=100,100,100,100 marker-levels=-1,-1,-1,-1,-1,95,88  marker-low-levels=10,10,10,10 marker-names='Black\ Toner\  Cartridge,Cyan\ Toner\ Cartridge,Magenta\ Toner\ Cartridge,Yellow\  Toner\ Cartridge,Waste\ Toner\ Box,Belt\ Unit,Drum\ Unit'  marker-types=toner,toner,toner,toner number-up=1  printer-commands=AutoConfigure,Clean,PrintSelfTestPage  printer-info='Brother MFC-L8900CDW series (cups)'  printer-is-accepting-jobs=true printer-is-shared=true  printer-is-temporary=false printer-location  printer-make-and-model='Brother MFC-L8900CDW CUPS' printer-state=3  printer-state-change-time=1591573113 printer-state-reasons=none  printer-type=8523868  printer-uri-supported=ipp://localhost/printers/MFC-L8900CDW

Thanks for any assistance/suggestions you can give.
Evelyn

Thank you for the output. I had an idea, but I do not think it will work out. I suggest you report an issue at

[https://github.com/OpenPrinting/cups-filters/issues](https://github.com/OpenPrinting/cups-filters/issues)

referring this thread. I too am unable to print multiple copies on Debian unstable.

---

### Post by esbmast on 2020-06-26
> **brian_p said:**
> Thank you for the output. I had an idea, but I do not think it will work out. I suggest you report an issue at

[https://github.com/OpenPrinting/cups-filters/issues](https://github.com/OpenPrinting/cups-filters/issues)

referring this thread. I too am unable to print multiple copies on Debian unstable.

I did this, and the problem has been found and fixed with changes to gstoraster and gstopdf.  Please see:
[https://github.com/OpenPrinting/cups-filters/issues/255](https://github.com/OpenPrinting/cups-filters/issues/255)

I am new to Ubuntu and unfamiliar with the process.  How can I petition for this fix to be incorporated into a 20.04LTS update?

Thanks.

---

### Post by esbmast on 2020-07-10
> **esbmast said:**
> I did this, and the problem has been found and fixed with changes to gstoraster and gstopdf.  Please see:
[https://github.com/OpenPrinting/cups-filters/issues/255](https://github.com/OpenPrinting/cups-filters/issues/255)



This is still an issue.  The above-mentioned "fix" turns out to not address this particular problem.

---

### Post by alyana on 2020-10-20
Hi Evelyn,

I can confirm this issue with exactly the same printer and setup (LAN, static IP address). And the same problem on a different machine with an HP OfficeJet 6950, which is also connected via network (WLAN, static IP address). So it does not seem to be Brother related. The HP 6950 prints fine when connected via USB. Seems it's a network printing issue. No matter how many copies it should print, only the first page gets printed and then it stops.

I found out, that in the latest cups filters this bug seems to be fixed (at least from the description), but I don't know how to install those cups filters (and cups 2.3.3) in Ubuntu 20.04. Seems 20.04 is stuck with cups 2.3.1.
Does anybody know how to update cups from 2.3.1 to 2.3.3 to maybe fix this issue?

Thanks
Alyana

---

### Post by alyana on 2020-12-11
Hi again everyone,

today I managed to fix this issue with the exact same printer, the Brother MFC-L8900CDW.

The solution I found comes from here: [https://github.com/OpenPrinting/cups-filters/issues/242](https://github.com/OpenPrinting/cups-filters/issues/242)
 
It's a post from tillkamppeter from July 12 that finally lead me on the right track.

 
Actually all I needed to do was altering the ppd file with root  rights, so no need to change the cups version in my case. Obviously the  ppd file provided by Brother didn't work out correctly.


Here is what I did:

Stop the CUPS daemon:
 ```
sudo systemctl stop cups
``` 

Then edit the ppd file (you need to do this with root rights):
 
```
sudo nano /etc/cups/ppd/MFCL8900CDW.ppd
```
 
You find a line like

 ```
*cupsManualCopies: false
```

near the beginning of the file. Change this line to

 ```
*cupsManualCopies: True
```

Please note it's True, not true (case sensitive). It was mentioned  somewhere else in that thread that it has to be written with capital T.
 
Save the file

```
CTRL+O
```

exit the editor

```
CTRL+X
```

and start CUPS again:

 ```
sudo systemctl start cups
```


 From this point on things have been working fine.

---

### Post by arthurdent22 on 2021-03-03
Having the same problem with a Brother DCP-LP2550DW.
My file /etc/cups/ppd/Brother-DCP-L2550DW-series.ppd had 
*cupsManualCopies: true
After changing it from true to True and restarting cups it works.

---

### Post by tinkeringcaveman2 on 2022-02-05
I have had this problem repeatedly with my Epson Et-3700. 

I have fixed it using the above method for fixing the cupsManual Copies line in the ppd file, only to have the problem recur on reboot. It seems that Ubuntu deletes the ppd and loads a new one on reboot--weird. Maybe that has to do with printer discovery?

 I didn't know how to solve that recurring problem permanenetly. Instead, I did this:
- Found the flawed ppd file, (in my case, it was in etc/cups/ppd),
- Changed the line reading "*cupsManualCopies: [FONT=Liberation Mono, monospace][SIZE=2]true" to "[/SIZE][/FONT]*cupsManualCopies: [FONT=Liberation Mono, monospace][SIZE=2]True"
[/SIZE][/FONT]- Saved the file
- Saved a copy of the file to my Documents directory (in my case I changed the file name a tad so that I would know the difference)
- Wrote a script shell to replace the flawed ppd file with the fixed file whenever I ran the script.
- Saved the shell file to my Desktop 
- Set the shell file permissions to execute as a program

In my case the shell file contains simply one line of script:    	 	 	 	   sudo cp /home/kevin/Documents/EPSON_ET_3700_Series-km.ppd /etc/cups/ppd/EPSON_ET_3700_Series.ppd

  
I named the shell file on the Desktop "EnableMultipleCopies-EpsonPrinter" so that it was fairly obvious what it did

Now whenever I have the need to print multiple copies, I run the shell file first. This saves editing the file manually every time.

Hope this helps others...

I am not a programmer; I learned just enough by Googling to figure this out.

---

