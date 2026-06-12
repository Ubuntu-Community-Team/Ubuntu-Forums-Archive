---
title: "Query on installing HP SmartTank printer &amp; software"
date: 2020-04-18
forum: Hardware
---

### Post by Richard_York on 2020-04-18
After useful advice to my earlier query about Ubuntu friendly printers I now have an HP Smart Tank Plus 555. 

I'm stalled at the setting up software stage. Following instruction on the HP Developers site I realised I didn't need to download hplip after all, as I already have it.

Since this computer has no blue-tooth or wifi of its own, the obvious next thing to do is to plug in the USB cable, though the official guidance repeats and stresses that it's important not to plug this in until prompted.

There's nothing now to prompt me or not that I can see. The printer's flashing its WiFI connection hopefully, but that's not going anywhere.

So should I just plug in and see what happens next?

Forgive possibly excess caution, but I don't want to take a step I'll afterwards regret!

Thanks as ever for the patient advice received on this forum, it's very much appreciated.




*(Ubuntu 18.04 , Intel Core i5-2400 CPU @3.10GHz x 4, 7.8GiB memory, 64-bit, Graphics: GeForce GT710/PCle /SSE2)*

---

### Post by ajgreeny on 2020-04-18
I dfon't know that printer at all but assuming it has some sort of display screen, similar to my Envy all-in-one, there will probably be a setup screen available to connect it to your router.

Presumably your network wifi is password protected so you will have to enter that somehow to make the connection live, but once that is sorted you may find that the printer is automatically found and available in print dialogues, as is often the case with HP machines.

Management of the printer may be easier if you install ***hplip-gui*** which can help with nozzle cleaning etc etc, if needed, though most if not all things can also be done using the cups webmin at [http://localhost:631/](http://localhost:631/)

---

### Post by brian_p on 2020-04-18
> **Richard_York said:**
> After useful advice to my earlier query about Ubuntu friendly printers I now have an HP Smart Tank Plus 555. 

I'm stalled at the setting up software stage. Following instruction on the HP Developers site I realised I didn't need to download hplip after all, as I already have it.

What version of HPLIP is on the computer?
> 
Since this computer has no blue-tooth or wifi of its own, the obvious next thing to do is to plug in the USB cable, though the official guidance repeats and stresses that it's important not to plug this in until prompted.

There's nothing now to prompt me or not that I can see. The printer's flashing its WiFI connection hopefully, but that's not going anywhere.

You are not doing yourself any favours by depriving yourself of WiFi.

> So should I just plug in and see what happens next?

Be a devil!

---

### Post by Richard_York on 2020-04-18
Thanks both. 

The printer has a tiny screen, a one liner.  

No wifi in the computer: I may be misunderstanding, not unusual with me &  technology. We have a Wifi router, but this desktop computer is wired into it. It's  about 8 yrs old and has no bluetooth ability of its own. 

Meanwhile
HPLIP version - when I entered dpkg -l hplip into the terminal I got  3.17.10+repa amd64

Good news is that  [https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index](https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index)  shows my printer model is supported.

"Be a devil!"....Plug in USB anyway & see what happens... there's that "Yeah but it says not to, and I don' t know how to climb out if I just dig myself a hole", thinking at work. I've dug myself into technical holes in the past and had hard work climbing out!

More delving in the instructions - shared between leaflets and various HP pages - showed how to press buttons to get diagnostic info from printer.
That gave several approaches.
Of these, using printer panel with WPS to connect gave no joy.
Simply pressing "add printer" on Ubuntu screen's top right hand tells me it's found CUPS-BRF-Printer, though it doesn't talk to it. I don't even know if this is the actual HP printer.

Where/how do I install ***hplip-gui***  please?  (I remain at basic level in all this)

So some progress, but still stuck. And seriously tempted just to stick that USB cable in, it's the only option I can currently see.
So what could go wrong by so doing?

An extra query (sorry!) - the terminal tells me HPLIP is installed, but I have no idea how to access HPLIP in case there's a dialogue there to prompt this USB connection moment. Or does it just sit there and leap into action when required?

Sometimes pen and ink seems a much more sensible option...

---

### Post by Autodave on 2020-04-18
Plug it in.  The " don't do this" stuff is for Windows.  Plug it in and it will work.

Mine is a laser printer, hooked up by wifi.  My PC found it right away and the prompt came up on the printer screen asking me to verify that I wanted it to connect via wifi.  That worked instantly.  Using a USB cable, I plugged into my wife's machine: it instantly was recognized by her PC and was ready to go.

---

### Post by brian_p on 2020-04-18
> **Richard_York said:**
> Thanks both. 

The printer has a tiny screen, a one liner.  

No wifi in the computer: I may be misunderstanding, not unusual with me &  technology. We have a Wifi router, but this desktop computer is wired into it. It's  about 8 yrs old and has no bluetooth ability of its own. 


This wired connection is by ethernet cable, we assume. That's good. You do not need WiFi on the computer. Use the control panel on the printer to connect the router wirelessly to the printer and we will go from there.

> 
Meanwhile
HPLIP version - when I entered dpkg -l hplip into the terminal I got  3.17.10+repa amd64

Good news is that  [https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index](https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index)  shows my printer model is supported.

It is only supported from version 3.19.6. That means you will have to alter the HPLIP version you have. Personally, I will not support you if your endeavours to do this meet with problems. There is a much better way without using HPLIP. But it depends on connecting the printer to the router.

---

### Post by Richard_York on 2020-04-18
> **brian_p said:**
> This wired connection is by ethernet cable, we assume. That's good. You do not need WiFi on the computer. Use the control panel on the printer to connect the router wirelessly to the printer and we will go from there..

Great - I tried again, with new confidence, to make the printer connect to the router, and this time it did.  Thank you!
And it now appears to work, printing both text and picture on demand, and for that I'm most grateful.


> **brian_p said:**
> It is only supported from version 3.19.6. That means you will have to alter the HPLIP version you have. Personally, I will not support you if your endeavours to do this meet with problems. There is a much better way without using HPLIP. But it depends on connecting the printer to the router.

Attempting to alter the HPLIP version is  probably well beyond my skill level anyway!  Given that the machine appears to work, would there be any advantage to altering things? If so, it has now met your condition of being connected to the router.

Likewise, would it still help in any way to add Hplip-gui ?  And if so, what are the steps to getting it?
 
Otherwise, I'll mark this as solved.

---

### Post by Autodave on 2020-04-18
He said previously that it is by USB cable.  

You do not need to worry about all the router tak: you won't be using that.  Plug the cable in and it will work.

---

### Post by Richard_York on 2020-04-18
Thanks, but I wonder if we cross posted here? See my reply  at #7.

---

### Post by brian_p on 2020-04-18
> **Richard_York said:**
> Great - I tried again, with new confidence, to make the printer connect to the router, and this time it did.  Thank you!
And it now appears to work, printing both text and picture on demand, and for that I'm most grateful.

Brilliant; well done. Getting a wireless connection between printer and router was critical. Printing software on the computer can now take over to set up printing for you automatically. Please would you give the output of ```
lpstat -l -e
```

> 
Attempting to alter the HPLIP version is  probably well beyond my skill level anyway!  Given that the machine appears to work, would there be any advantage to altering things? If so, it has now met your condition of being connected to the router.

There is no advantage whatsoever. You are not using HPLIP to print.

> 
Likewise, would it still help in any way to add Hplip-gui ?  And if so, what are the steps to getting it?
 
Otherwise, I'll mark this as solved.

It would not help in any way. To repeat: you are not using HPLIP to print. HPLIP is not required for a modern printer such as yours. I will take a long time for old and new hands to realise this.Mark this as solved. Also, I would appreciate seeing what you get for ```
avahi-browse -rt _ipp._tcp
``` ```
avahi-browse -rt _uscan._tcp
```

---

### Post by Richard_York on 2020-04-18
That's encouraging! I haven't a clue why HPLIP is redundant but would not understand the reply :-)
I realise I still have the USB cable plugged in. Should I discard that? It would be a pity to upset it now!

My remaining problem is that it is not found by the computer as a scanner. No doubt there's some software somewhere, but I'm not finding anything other than the HP Developers site which talks about HPLIP again.

Terminal Responses as follows
lpstat -l -e gives: >  HP_Smart_Tank_Plus_550_series_D221C8_ permanent ipp://localhost/printers/HP_Smart_Tank_Plus_550_series_D221C8_ ipps://HP9C7BEFD221C8.local:631/ipp/print

avahi-browse -rt _ipp._tcp : 
> 
+ enp7s0 IPv6 HP Smart Tank Plus 550 series [D221C8]        Internet Printer     local
+ enp7s0 IPv4 HP Smart Tank Plus 550 series [D221C8]        Internet Printer     local
+     lo IPv4 Smart Tank Plus 550 series [CN99N243FJ]       Internet Printer     local
= enp7s0 IPv4 HP Smart Tank Plus 550 series [D221C8]        Internet Printer     local
   hostname = [HP9C7BEFD221C8.local]
   address = [192.168.1.84]
   port = [631]
   txt = ["Fax=F" "mopria-certified=2.0" "Scan=T" "kind=document,envelope,photo,postcard" "URF=CP1,MT1-2-8-9-10-11,PQ3-4-5,RS300-600,SRGB24,OB9,OFU0,W8-16,DEVW8-16,DEVRGB24-48,ADOBERGB24-48,IS1,V1.4,FN3" "PaperMax=legal-A4" "pdl=application/vnd.hp-PCL,image/jpeg,image/urf,image/pwg-raster,application/PCLm" "Duplex=F" "Color=T" "usb_MDL=Smart Tank Plus 550 series" "usb_MFG=HP" "ty=HP Smart Tank Plus 550 series" "product=(HP Smart Tank Plus 550 series)" "UUID=525460f9-288f-5f97-2bfc-c010180caf1d" "rp=ipp/print" "TLS=1.2" "qtotal=1" "priority=20" "note=" "adminurl=http://HP9C7BEFD221C8.local./#hId-pgAirPrint" "txtvers=1"]
= enp7s0 IPv6 HP Smart Tank Plus 550 series [D221C8]        Internet Printer     local
   hostname = [HP9C7BEFD221C8.local]
   address = [192.168.1.84]
   port = [631]
   txt = ["Fax=F" "mopria-certified=2.0" "Scan=T" "kind=document,envelope,photo,postcard" "URF=CP1,MT1-2-8-9-10-11,PQ3-4-5,RS300-600,SRGB24,OB9,OFU0,W8-16,DEVW8-16,DEVRGB24-48,ADOBERGB24-48,IS1,V1.4,FN3" "PaperMax=legal-A4" "pdl=application/vnd.hp-PCL,image/jpeg,image/urf,image/pwg-raster,application/PCLm" "Duplex=F" "Color=T" "usb_MDL=Smart Tank Plus 550 series" "usb_MFG=HP" "ty=HP Smart Tank Plus 550 series" "product=(HP Smart Tank Plus 550 series)" "UUID=525460f9-288f-5f97-2bfc-c010180caf1d" "rp=ipp/print" "TLS=1.2" "qtotal=1" "priority=20" "note=" "adminurl=http://HP9C7BEFD221C8.local./#hId-pgAirPrint" "txtvers=1"]
=     lo IPv4 Smart Tank Plus 550 series [CN99N243FJ]       Internet Printer     local
   hostname = [localhost]
   address = [127.0.0.1]
   port = [60000]
   txt = ["qtotal=1" "txtvers=1" "priority=60" "URF=CP1,IS1,MT1,RS300,SRGB24,W8" "usb_MDL=Smart Tank Plus 550 series" "usb_MFG=HP" "Copies=U" "Duplex=U" "Color=U" "pdl=image/pwg-raster,image/urf,application/PCLm,image/jpeg" "product=(Smart Tank Plus 550 series)" "adminurl=http://localhost:60000/" "ty=HP Smart Tank Plus 550 series" "rp=ipp/print"]

avahi-browse -rt _uscan._tcp:
> + enp7s0 IPv6 HP Smart Tank Plus 550 series [D221C8]        _uscan._tcp          local
+ enp7s0 IPv4 HP Smart Tank Plus 550 series [D221C8]        _uscan._tcp          local
= enp7s0 IPv4 HP Smart Tank Plus 550 series [D221C8]        _uscan._tcp          local
   hostname = [HP9C7BEFD221C8.local]
   address = [192.168.1.84]
   port = [8080]
   txt = ["mopria-certified-scan=1.2" "duplex=F" "is=platen" "cs=binary,color,grayscale" "pdl=application/octet-stream,application/pdf,image/jpeg" "ty=HP Smart Tank Plus 550 series" "rs=eSCL" "representation=images/printer.png" "vers=2.63" "UUID=525460f9-288f-5f97-2bfc-c010180caf1d" "note=" "adminurl=http://HP9C7BEFD221C8.local." "txtvers=1"]
= enp7s0 IPv6 HP Smart Tank Plus 550 series [D221C8]        _uscan._tcp          local
   hostname = [HP9C7BEFD221C8.local]
   address = [192.168.1.84]
   port = [8080]
   txt = ["mopria-certified-scan=1.2" "duplex=F" "is=platen" "cs=binary,color,grayscale" "pdl=application/octet-stream,application/pdf,image/jpeg" "ty=HP Smart Tank Plus 550 series" "rs=eSCL" "representation=images/printer.png" "vers=2.63" "UUID=525460f9-288f-5f97-2bfc-c010180caf1d" "note=" "adminurl=http://HP9C7BEFD221C8.local." "txtvers=1"]




Thanks again,
Richard

---

### Post by Autodave on 2020-04-18
hplip and hplip-gui will give you the scanning capability.  They are in the Software or synaptic. Or, if you already have an hplip installed, then just update your system and you should be good to go.

---

### Post by brian_p on 2020-04-18
> **Richard_York said:**
> That's encouraging! I haven't a clue why HPLIP is redundant but would not understand the reply :-)

Basically, CUPS is contacting the printer directly and not via HPLIP. You are dealing with the organ grinder, not with the monkey. ;)
> 
I realise I still have the USB cable plugged in. Should I discard that? It would be a pity to upset it now!

Disconnect it and employ it for something more useful.
> 
My remaining problem is that it is not found by the computer as a scanner. No doubt there's some software somewhere, but I'm not finding anything other than the HP Developers site which talks about HPLIP again.


Having an output for *avahi-browse -rt _uscan._tcp* means it is your lucky day. :D. Let's try something that has worked for 100% of users who have used it.                                                  
                                                                                                                         
Read [https://github.com/alexpevzner/sane-airscan](https://github.com/alexpevzner/sane-airscan). The link to Ubuntu binaries is at                                                                                                           
                                                                                                                         
  [https://software.opensuse.org//download.html?project=home%3Apzz&package=sane-airscan](https://software.opensuse.org//download.html?project=home%3Apzz&package=sane-airscan)                                   
                                                                                                                         
Just in case that does not work I will give you a direct link to the file you need for Ubuntu 18.04:                                                                                                   
                                                                                                                         
   [https://download.opensuse.org/repositories/home:/pzz/xUbuntu_18.04/amd64/](https://download.opensuse.org/repositories/home:/pzz/xUbuntu_18.04/amd64/)                                                                 
                                                                                                                         
Install (I believe double-clicking on the filename will do this) and test with either the **simple-scan** or **xsane** commands. I am very interested in the outcome.

---

### Post by Richard_York on 2020-04-19
Thanks as always, I will return to this soon. Covid lockdown keeps one surprisingly busy, I find!

---

### Post by Richard_York on 2020-04-19
Not so good this time:
I tried the advice to remove the USB, starting with the computer end, leaving t'other end in the back of the printer where it's harder to reach.
Result - the printer stopped working. The blue WiFi light still shows steady, the connection bars are good.

But the computer stopped talking. After various tries of things I plugged it back in. Settings - Device - Printers leads to the attached screenshot

I also tried pressing the wireless button  + i button on the printer, getting four pages ending with the advice to power off my router and printer for them to reset both, as the printer has an Auto-IP address.
But pressing i alone gets me a report that the printer is connected to my router, naming it correctly .

Now more puzzled than I was before, and can't print - I get as far as the print dialogue box, which names the printer correctly, but pressing OK gets no reaction whatever.

Maybe I need to start all over again?

So to summarise:
 I seemed to have the options of USB connection or WiFi. USB initially appeared easier but didn't work with what I had set up.
WiFi seemed more daunting but with the USB cable still in place, it  then worked fine until the cable was removed and still doesn't.
I'm puzzled as to why it's better for the signal to print to have to go from my computer through the router, when the printer sits next to it and has USB cable within reach.
If it's easy to update HPLIP and install GUI that might seem less daunting, though I am I currently am unsure how to do either,

Personal note - with the remains of Chronic Fatigue Syndrome I tend to lost the plot when tech stuff goes on too long, but very much prefer Ubuntu to Windows so am sticking with it.
So I'm now wondering what the least tiring option is to get this thing going.

Thanks,
Richard

---

### Post by Richard_York on 2020-04-20
A further update: It's now printing again but not yet scanning.

In a very unscientific and undocumented way, I tried going via Synaptic to see if HPLIP would update there, which it did. It also updated associated files of its own choosing. 
Still didn't print.
 Synaptic doesn't find HPLIP-GUI.

Needing to print some material, I tried a reset on the printer and Wifi connection again, with USB still in place even though it's supposedly redundant.

It now prints, has the USB cable connected, and because last time I unplugged this it stopped I'm reluctant to take it out again. I don't know how the combination works, but it does.

I had a look at the first link in #13 above - at first sight it appears beyond my level of understanding, and as I explained, I hit a fatigue wall after a time with these things, I'm sorry.

So I'm grateful for help received, even if I prove unable to follow all the recommendations at present!

I would still find it useful to enable it to scan.

Thanks,
Richard

---

### Post by brian_p on 2020-04-20
> **Richard_York said:**
> A further update: It's now printing again but not yet scanning.

It now prints, has the USB cable connected, and because last time I unplugged this it stopped I'm reluctant to take it out again. I don't know how the combination works, but it does.

Ok, Richard, we will not disturb that arrangement. I also don't know how the combination works but suspect it has something to do with how wireless is set up with your printer model. I am not motivated sufficiently to find out at present.

> I had a look at the first link in #13 above - at first sight it appears beyond my level of understanding, and as I explained, I hit a fatigue wall after a time with these things, I'm sorry.


I understand your feelings. However, let me encourage you to take the following steps. I have tried to reduce the number of steps and to enable you to check the progress of each one of them. All the commands are issued from a terminal.

[LIST]
[*]Download *sane-airscan_0.9.17+54.1_amd64.deb* with ```
wget https://download.opensuse.org/repositories/home:/pzz/xUbuntu_18.04/amd64/sane-airscan_0.9.17+54.1_amd64.deb
```
[/LIST]
[LIST]
[*]Check that the downloaded file is in your present directory by listing it: ```
ls -l sane-airscan_0.9.17+54.1_amd64.deb
```
[/LIST]
[LIST]
[*]Install *sane-airscan_0.9.17+54.1_amd64.deb* with ```
sudo apt install ./*sane-airscan_0.9.17+54.1_amd64.deb*
```
[/LIST]
[LIST]
[*]Check that *sane-airscan* is installed with Synaptic or with the command ```
dpkg -l sane-airscan
```
[/LIST]
[LIST]
[*]After doing all of this, execute ```
scanimage -L
``` and give us the output.
[/LIST]

---

### Post by Richard_York on 2020-04-20
The steps are much appreciated, Brian - just the right size!

The output at the end is:
> ~$ scanimage -L
device `airscan:HP Smart Tank Plus 550 series [D221C8]' is a AirScan HP Smart Tank Plus 550 series [D221C8] eSCL network scanner

And to my great relief, when I opened Simple Scan, which we have already installed, it both recognised the HP correctly and scanned.

So all seems well - we don't know quite how it's doing it, but it's both printing and scanning, and as long as it goes on doing both, I'm happy.

Many thanks to all three who had a hand in getting me there,

Richard

---

