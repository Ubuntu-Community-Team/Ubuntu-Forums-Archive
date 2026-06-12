---
title: "printer driver install"
date: 2021-04-30
forum: Hardware
---

### Post by coley9225 on 2021-04-30
I just purchased a new printer. My previous printer was a Canon pixma MX492, nice, all in one, but no linux drivers. My new printer is a Canon pixma TS3322 all in one. I got this printer because it has linux drivers. I downloaded the drivers, from Canon, as a tar.gz file. After extracting the file, I see there is a ***_i386.deb(I assume for 32 bit systems), a ***_amd64.deb(for 64 bit systems, which I have), and an install.sh script. My question is, should I open the  ***_amd64 file with discover or apt package manager, and let that install the drivers, run the install.sh script and install that way, or both. My thinking is that the install.sh is included for people running a minimal system, with no GUI, but wanted to be sure, so I don't mess up my OS and have to fall back to a back up. As always, thanks in advance, you folks are great and the tips and advice are always much appreciated.

---

### Post by Xian on 2021-04-30
Advise you download the drivers for: "Printer Driver Ver. 5.90 for Linux (debian Packagearchive)"

[https://www.usa.canon.com/internet/portal/us/home/support/details/printers/support-inkjet-printer/ts-series/pixma-ts3322/pixma-ts3322?tab=drivers_downloads](https://www.usa.canon.com/internet/portal/us/home/support/details/printers/support-inkjet-printer/ts-series/pixma-ts3322/pixma-ts3322?tab=drivers_downloads)

Then open a terminal in the download folder and issue the commands below.

After installation a message asking to register the printer is shown. 
Verify the printer is connected and power is on. Then press the Enter key.

Additional setup instructions will follow.

```
tar zxvf cnijfilter2-5.90-1-deb.tar.gz
cd cnijfilter2-5.90-1-deb
sudo ./install.sh
```

---

### Post by brian_p on 2021-05-01
Why us Canon drivers? Here is a modern technique supported by Ubuntu:

[https://wiki.debian.org/CUPSQuickPrintQueues](https://wiki.debian.org/CUPSQuickPrintQueues)

---

### Post by Yellow Pasque on 2021-05-01
Just for fun, I ran the install script in my Xubuntu 20.04 VM. It installed the .deb cleanly and looking at the dependencies, I don't see anything that would cause trouble with apt in the future. I removed the .deb using Synaptic. Here's what installer script looks like:
```
$ sudo ./install.sh
==================================================

Canon Inkjet Printer Driver
Version 5.90
Copyright CANON INC. 2001-2019

==================================================
Command executed = sudo dpkg -iG ./packages/cnijfilter2_5.90-1_amd64.deb
(Reading database ... 253057 files and directories currently installed.)
Preparing to unpack .../cnijfilter2_5.90-1_amd64.deb ...
Unpacking cnijfilter2 (5.90-1) over (5.90-1) ...
Setting up cnijfilter2 (5.90-1) ...
Processing triggers for libc-bin (2.31-0ubuntu9.2) ...

#=========================================================#
#  Register Printer
#=========================================================#
Next, register the printer to the computer.
Connect the printer, and then turn on the power.
To use the printer on the network, connect the printer to the network.
When the printer is ready, press the Enter key.
> 

#=========================================================#
#  Connection Method
#=========================================================#
 1) USB
 2) Network
Select the connection method.[1]

Searching for printers...


#=========================================================#
#  Select Printer
#=========================================================#
Select the printer.
If the printer you want to use is not listed, select Update [0] to search again.
To cancel the process, enter [Q].
-----------------------------------------------------------

```
Seems legitimate to me.

---

### Post by coley9225 on 2021-05-01
Thanks for all the tips. I got it up and running for printing and copying, but can't get scanner to work. I downloaded scangearmp from canon site and installed, but get errors when I try to scan. I tried skanlite, xsane, and gscan2pdf, as well as scangearmp from terminal. The errors range from can't open scanner because it's busy to can't detect a scanner. I still have my old all-in-one, so I can scan with that untill I get the scan issue worked out on the new one.

---

### Post by brian_p on 2021-05-01
Canon does not provide any scanning package that allows working with skanlite, xsane, and gscan2pdf. scangearmp is not supported by Ubuntu. Contact Canon.

[https://wiki.debian.org/Scanner#canon](https://wiki.debian.org/Scanner#canon)

sane-airscan will work with the Canon pixma TS3322.

[https://github.com/alexpevzner/sane-airscan](https://github.com/alexpevzner/sane-airscan)

---

### Post by coley9225 on 2021-06-10
Many thanks to all that have helped me, on this as well as many other issues. It was somewhat of a nightmarish process, having had to restore my system twice( thanks for all those that stress good backups!!), but I finally got my new printer working. The printing half went well, but getting the scanner up and working was another matter altogether. Anyway, everything is working now, thanks all your help. I'm glad too, because I don't want to think how bad it would be to go back to windows.
Again, my sincere thanks to you guys, your the greatest. Now I will mark this thread solved.

---

### Post by him610 on 2021-06-10
@coley9225
That's great. It would be nice if you told us how you got the scanner to work.

---

### Post by coley9225 on 2021-06-11
Hello him610. I tried the cannon drivers, no dice. I tried sane, xsane, etc....again a no-go. I tried to install sane-airscan, and all I found said to add aa line to /etc/apt/sources.list. After updating synaptic, I suddenly had in excess of 1800 packages to update, which broke lubuntu. I restored from timeshift back up and tried again. Another fried system. I was about to start pulling my hair out and ask for help, but decided to do 1 more search.I googled "install sane-airscan", and found terminal commands to add the proper repository, downloaded and install airscan, and all is working well at this point. I apologize for not giving more details.  The nightmare included adding public key through command line, and few other issues, but this pretty well sums up the whole thing. For any other noobs out there, keep fighting and ask the great people in the forums and you'll be able to fix most issues. The forums are our friends and always willing to help. I hope this sheds a little light on my troubles and helps someone else out.

---

### Post by him610 on 2021-06-11
@coley9225
Thanks for sharing that bit of learned experience. I follow the forum on a regular basis, and there are of lots of folks who have problems setting up their multi-function devices. I can usually help them when it comes to Brother devices connected conventionally. The Canon or HP printers, I know very little about. The newer airscan capabilities, I know nothing about.
Glad you addressed your issue satisfactorily.

---

### Post by coley9225 on 2021-06-12
I went through my bash history to find the commands needed.
  echo 'deb [http://download.opensuse.org/repositories/home:/pzz/xUbuntu_20.04/](http://download.opensuse.org/repositories/home:/pzz/xUbuntu_20.04/) /' | sudo tee /etc/apt/sources.list.d/home:pzz.list
 curl -fsSL [https://download.opensuse.org/repositories/home:pzz/xUbuntu_20.04/Release.key](https://download.opensuse.org/repositories/home:pzz/xUbuntu_20.04/Release.key) | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/home_pzz.gpg > /dev/null

After that, you can install sane-airscan, (I used synaaptic). Also note that if your connecting with usb cable you will need to install ipp-usb, also through synaptic. I hope this helps someone with printer and/or scanner issues.

---

### Post by brian_p on 2021-06-14
> **coley9225 said:**
> I went through my bash history to find the commands needed.
  echo 'deb [http://download.opensuse.org/repositories/home:/pzz/xUbuntu_20.04/](http://download.opensuse.org/repositories/home:/pzz/xUbuntu_20.04/) /' | sudo tee /etc/apt/sources.list.d/home:pzz.list
 curl -fsSL [https://download.opensuse.org/repositories/home:pzz/xUbuntu_20.04/Release.key](https://download.opensuse.org/repositories/home:pzz/xUbuntu_20.04/Release.key) | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/home_pzz.gpg > /dev/null

After that, you can install sane-airscan, (I used synaaptic). Also note that if your connecting with usb cable you will need to install ipp-usb, also through synaptic. I hope this helps someone with printer and/or scanner issues.

Hello coley9225,

Glad you have tings sorted. You have given very good advice regarding ipp-usb and sane-airscan. To help other users it would be useful to have what you get for ```
scanimage -L
``` and ```
airscan-discover
```

In addition
```
avahi-browse -rt _ipp._tcp
``` ```
avahi-browse -rt _usan._tcp
``` would be useful too.

---

### Post by gezzer2 on 2021-06-14
> **coley9225 said:**
> Hello him610. I tried the cannon drivers, no dice. I tried sane, xsane, etc....again a no-go. I tried to install sane-airscan, and all I found said to add aa line to /etc/apt/sources.list. After updating synaptic, I suddenly had in excess of 1800 packages to update, which broke lubuntu. I restored from timeshift back up and tried again. Another fried system. I was about to start pulling my hair out and ask for help, but decided to do 1 more search.I googled "install sane-airscan", and found terminal commands to add the proper repository, downloaded and install airscan, and all is working well at this point. I apologize for not giving more details.  The nightmare included adding public key through command line, and few other issues, but this pretty well sums up the whole thing. For any other noobs out there, keep fighting and ask the great people in the forums and you'll be able to fix most issues. The forums are our friends and always willing to help. I hope this sheds a little light on my troubles and helps someone else out.

thanks for that explanation. i managed to get my scanner working using sane-airscan. many thanks Steve ...

---

### Post by brian_p on 2021-06-14
> **gezzer2 said:**
> thanks for that explanation. i managed to get my scanner working using sane-airscan. many thanks Steve ...

Hello Steve,

Please give the same information coley9225 was asked for.

TIA.

---

### Post by coley9225 on 2021-06-15
Hello brian, I ran the code you mentioned. I've never used code tags so if this doesn't work, I'll repost and  just copy/paste the results.
```
charles@coleys-lubuntu:~$ scanimage -Ldevice `airscan:e0:Canon TS3300 series (USB)' is a eSCL Canon TS3300 series (USB) ip=127.0.0.1
charles@coleys-lubuntu:~$ airscan-discover
[devices]
  Canon TS3300 series (USB) = http://127.0.0.1:60000/eSCL/, eSCL
charles@coleys-lubuntu:~$ avahi-browse -rt _ipp._tcp
+     lo IPv4 Canon TS3300 series (USB)                     Internet Printer     local
=     lo IPv4 Canon TS3300 series (USB)                     Internet Printer     local
   hostname = [coleys-lubuntu.local]
   address = [127.0.0.1]
   port = [60000]
   txt = ["air=none" "mopria-certified=2.0" "rp=ipp/print" "priority=50" "kind=document,photo,postcard" "PaperMax=isoC-A2" "URF=V1.4,CP1,PQ4-5,RS600,SRGB24,W8,OB9,OFU0,IS1" "UUID=00000000-0000-1000-8000-0018a2aecfb0" "Color=T" "Duplex=F" "note=" "qtotal=1" "usb_MDL=TS3300 series" "usb_MFG=Canon" "usb_CMD=BJRaster3,NCCe,IVEC,URF" "ty=Canon TS3300 series" "product=(Canon TS3300 series)" "pdl=application/octet-stream,image/jpeg,image/urf,image/pwg-raster" "txtvers=1" "adminurl=http://localhost:60000/index.html?page=PAGE_AAP" "Fax=F" "Scan=T"]
charles@coleys-lubuntu:~$ avahi-browse -rt _usan._tcp
charles@coleys-lubuntu:~$ 



```

I feel good about finally learning linux to the point that I can help others the way I've gotten so much help. I hope the info I provided helps, and if you need any other info, please let me know.

---

### Post by brian_p on 2021-06-15
> **coley9225 said:**
> 
I feel good about finally learning linux to the point that I can help others the way I've gotten so much help. I hope the info I provided helps, and if you need any other info, please let me know.

Hello Charles,

Thanks for the info. Your problems are our problems. Your solutions are our solutions. You have chosen well with sane-airscan.

---

