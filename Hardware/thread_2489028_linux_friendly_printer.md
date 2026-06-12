---
title: "linux friendly printer"
date: 2023-07-15
forum: Hardware
---

### Post by oneleded on 2023-07-15
my HP deskjet5150 finally gave up the ghost this year. got it in 2002. was a good 20 years..  so im looking for a replacement. i dont plan on spending a lot of money, dont really need WiFi for the moment, doubt i will, the usb will work just fine. that printer was good on ink, and i'd refill cartridges when necessary. dont want that subscription for ink neither, i hear there are a few work-arounds.
got any suggestions i could use. i've got lubuntu 20.04 for the moment, but use more than one flavor of linux, just got to ad a few again. i thank you for your help.

---

### Post by gezzer2 on 2023-07-16
is this of any help ...

[URL="https://opensource.com/article/18/11/choosing-printer-linux"]https://opensource.com/article/18/11/choosing-printer-linux

[/URL][https://askubuntu.com/questions/102995/what-is-the-best-printer-for-ubuntu](https://askubuntu.com/questions/102995/what-is-the-best-printer-for-ubuntu)

---

### Post by Autodave on 2023-07-16
I've always had great luck with HP.  Brother printers seem to be pretty easy to get working, according to others here.

---

### Post by ian-weisser on 2023-07-16
An authoritative list of tested Linux-friendly printers is at [https://openprinting.github.io/](https://openprinting.github.io/) , maintained by the nice folks of the Open Printing project.

---

### Post by mIk3_08 on 2023-07-16
> **Autodave said:**
> I've always had great luck with HP.  Brother  printers seem to be pretty easy to get working, according to others  here. I agree with Autodave. I have been using this kind of  printers for many years now, so far so good. Scanner work smoothly with  Document scanner and Xsane image scanning application. Regards and  cheers.

---

### Post by oldfred on 2023-07-16
Do you need color? Often a lot more expensive to have color.
Do you need scanner?

My Brother has scanner & Wi-Fi, but I now use phone for most of my scanning and its connected with USB.
But as Black only laser printer was lower cost & lower cost per page.
```
[FONT=monospace][COLOR=#54ff54]**fred@Z170-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ ll /etc/cups/ppd/ [/COLOR]
total 44 
drwxr-xr-x 2 root lp 4096 Jul 16 00:00  [COLOR=#5454ff]**.**[/COLOR][COLOR=#000000]/ [/COLOR]
drwxr-xr-x 5 root lp 4096 Jul 16 12:22  [COLOR=#5454ff]**..**[/COLOR][COLOR=#000000]/ [/COLOR]
-rw-r----- 1 root lp 8942 Jul 16 00:00 'Brother_HL_L2390DW@BRW4023439CAFD6.local.ppd' 
-rw-r----- 1 root lp 8942 Apr 12 00:00  Brother_HL_L2390DW.ppd 
-rw-r----- 1 root lp 8935 Jul 16 00:00  Brother_HL_L2390DW_USB.ppd

[/FONT]
```

---

### Post by oneleded on 2023-07-17
i appreciate the help, and got a bit of studying to do. Thanks again

---

### Post by him610 on 2023-07-17
My thoughts...

I purchased a refurbished B&W laser Brother MFC-7360N (prints, scans, copies, faxes) about 10 years ago for $99 (originally $350.) It has been performing all of those tasks faithfully ever since. Only issue is the LCD panel is a little dim; however, I don't think LCD panels are used anymore on the newer models.

Black & white text is a lot easier to read than colored text. I only had to replace the original toner cartridge last year, I think. I don't do a whole lot of printing.

Brother provides drivers on its website one can download. The instructions are pretty straight forward so you should not have any problems with installation; however, be sure you read and understand the instructions.

I have never experienced any difficulties installing the Brother drivers on Xubuntu LTS releases every two years on each of my computers (clean install.) 

If you use a network connection, assigning a static IP address on your printer will be helpful. Be sure to download all of the supporting documentation for whichever device you decide on -  you never know when you may need to look something up.

Good luck.

---

### Post by TheFu on 2023-07-18
Look for 
[LIST]
[*]Driverless printing
[*]Driverless scanning
[/LIST]
That way, you won't need to worry about drivers for every possible OS, just that the printer has the correct interface type which can be used by any device.

I have 3 devices.
[LIST]
[*]1 laser printer that has been working since 2008 and is just a printer. USB connected to a system that provides a network print server for all the other computers/devices on the network. $70 new, at the time.
[*]1 All-in-One devices printer/scanner/fax which never printed anything after the ink dried. I never intended it to be used for printing. USB connected. $70 new, at the time.
[*]1 negative/slide scanner connected via USB. $100 new, at the time.
[/LIST]
My printer and all-in-one device cannot be bought new for many years now. The laser printer business for my vendor was actually sold to a different company, but the system-printer-config tool "discovers" that printer on the network and sets up any Linux computer BEFORE I do anything. It has worked that easily since 2016. It uses the IPP interface over USB.

Unfortunately, when it comes to peripherals, the only people who know the current models are people also looking or who just bought a new printer/scanner.
I have some simple rules around these types of devices.

For printers, 
[LIST]
[*]Get a laser printer, never an inkjet.  Toner lasts years. Ink dries out in less than 1 yr. Toner is usually $35 for 10,000 pages. I've been using the same toner cartridge for the last 10 yrs.  Ink would have cost me at least $350 over the last 10 yrs.
[*]If you need color, get a color laser
[*]Use driverless printing.  That usually means printers that support IPP, but check the OpenPrinting website for current models.
[*]Avoid wifi or networked printers.  They have a bad habit of "phoning home".  Why would anyone want a printer that reports to a company about what and when it prints?
[/LIST]
There are exceptions if you have specialized print requirements like extremely high quality photos which use special paper and only work well with ink, but be prepared to pay 10x more. Might be cheaper to still get a laser printer and print photos at the local corner drugstore or Wally-World.

For scanners, 
[LIST]
[*]Must have an automatic page feeder.  Scanning 20 pages should be easy.
[*]Should be able to save images to USB/SDHC storage, without any computer connected.
[*]Driverless scanning is just beginning.
[*]If you deal with your govt, maybe you'd like a fax machine capability?  I do.  I strive to never give my govt a voice phone number nor email address.  I prefer to interact with it via snail-mail or in one of the offices, if absolutely required, every 20 yrs.
[*]Scans in gray and color at sufficient resolution. I can't imagine any scanner sold today wouldn't have more resolution than needed for document/diagram scanning. Art/photos could be a different issue. I think 1200 dpi is sufficient for photos for casual users.
[*]I have a separate slide/negative scanner that connects via USB. No drivers for anything except WinXP were available, but now V4L2 drivers work - plugged it in and it "just worked". There are commercial drivers are $50 for all platforms - that's just for the MSFT and Apple people.
[/LIST]

---

### Post by oneleded on 2023-08-01
i been doing some searches, and mostly find, this newer printers are tied down to ink, and they, for the most part dont say, (HP for example), that the ink is only good for so many pages thanks to a smart chip on the machine. it dont matter how much ink ya got left, when the page number comes up, ya gotta buy more ink, even if the cartridge is half full. if ya dont, the printer shuts down. i'm not sure if all company's do this, most of what i've read concerns HP. the printers i'm interested in, are HP Printers, or Brothers. its just the ink subscription, thing could be a trap.
only if, i could get the old HPdeskjet 5150 working of repaired. 
after 20 years, 'dream the impossible dream' comes to mind.. got it in 2002, $120 dollars, and its been a good machine.

---

### Post by oldfred on 2023-08-02
I agree with TheFu.
Do not do ink, do a laser printer that uses toner.
The ink cartridges cost almost as much as a printer.

My last inkjet always dried out. I was sometimes able to use a q-tip and alcohol to clean cartridge & get it working again. But rarely needed color, so went with new Brother B/W laser printer. Cannot be happier.

---

### Post by oneleded on 2023-08-22
i think i will give that a shot. i dont do much color anyway. i want to thank all suggestions.

---

### Post by oneleded on 2023-09-15
i bought a brother hll2350 laser printer. somehow i got the wrong drivers installed. now i cant remove because of install with wrong syntax.

142666983609.jbg  Documents     Music      Public     Videos
BRF               Downloads     nobleNote  snap
Desktop           DSCN3185.png  Pictures   Templates
dav@dav-ms7b79:~$ cd Downloads
dav@dav-ms7b79:~/Downloads$ ls
 hll2350dwpdrv-4.0.0-1.i386.deb
'linux-brprinter-installer-2.2.3-1(1)'
'osdc_cheatsheet-find-2021.8.31.pdf page1'
'Screenshot 2023-09-15 at 15-05-09 Printer Drivers Downloads HL-L2350DW United States Brother.png'
 turboprint_2.54-1_amd64.deb
dav@dav-ms7b79:~/Downloads$ sudo dpkg --purge linux-brprinter-installer-2.2.3-1(1)
bash: syntax error near unexpected token `('
dav@dav-ms7b79:~/Downloads$ 
the right driver is: 
file:///home/dav/Desktop/ "hll2350dwpdrv-4.0.0-1.i386.deb"

(1) was not supposed to be there, its a copy, of the wrong driver, i downloaded more then one
Discover installed the unzipped driver files. before i found out it was the wrong files.
can i force it to uninstall?, so i can install the right driver files.

---

### Post by oneleded on 2023-09-16
bump

---

### Post by SeijiSensei on 2023-09-17
Parentheses have explicit meaning in the bash shell. Wrap the filename in single-quotes like this:

```
 sudo dpkg --purge 'linux-brprinter-installer-2.2.3-1(1)'
```

You can also "escape" special characters with the backslash like "\(", but I prefer to use quotes.

Another option is to type just a few letters of the file name, then hit tab. Bash will offer matching filenames with appropriate escaping.

That said, I have used brprinter-installer with considerable success on Brother printers.

---

### Post by oldfred on 2023-09-17
My Brother printer required no downloads of drivers. It just worked.

---

### Post by TheFu on 2023-09-17
My $0.02. The entire point of "driverless printing" is that no drivers need to be installed.  If the printer requires drivers, the wrong printer was chosen. Take it back, try again.

---

### Post by oneleded on 2023-09-17
> **SeijiSensei said:**
> Parentheses have explicit meaning in the bash shell. Wrap the filename in single-quotes like this:

```
 sudo dpkg --purge 'linux-brprinter-installer-2.2.3-1(1)'
```

You can also "escape" special characters with the backslash like "\(", but I prefer to use quotes.

Another option is to type just a few letters of the file name, then hit tab. Bash will offer matching filenames with appropriate escaping.

That said, I have used brprinter-installer with considerable success on Brother printers.

nevermind, i misread something and what i was going to print isn't necessary.

---

### Post by oneleded on 2023-09-17
well; i dont see the driver any more. i think it was using the parentheses. thanks to everybody for their input.

---

### Post by oneleded on 2023-09-24
> **oldfred said:**
> My Brother printer required no downloads of drivers. It just worked.

what kind of printer do you have? i cant find a brothers printer, using the search term 'driverless printing'. seems i cant install the drivers for what i got. they are not signed. i did go through the list till i got tired of looking.
too many printers. HP and Brothers. i dont need color printer for now, just b&w will work. driver or not.  //ed

---

### Post by oldfred on 2023-09-24
See post #6.

I think when I plugged printer in, it downed the ppd files.

---

### Post by oneleded on 2023-09-25
thanks, guess i had a brain scramble, and didnt register what ya wrote.

---

### Post by oneleded on 2023-10-08
i decided to ship back printer to amozon, and try again. is there something i've not downloaded from muon package manager i need to know, reguarding brothers printers? i guess it would depend on the model anyway. sure do miss the old HP i got in 2002, ink an all.

---

### Post by oneleded on 2023-10-31
i sent back the brother printer i got from amazon, and got another. this time i got the same one as oldfred. it might make it easier for me to have something in common to write about. i already messed up on installing this though, has to do with the settings. i think i reset something in server settings, among other settings. the printer does copy, but does not print. it is not receiving the data, most likely because i didnt set up the path right. who knows what i did, least i dont. i know i didnt have  ppd files checked also. i will post the messages i got while troubleshooting. it will be more clear that i am.

---

### Post by oldfred on 2023-10-31
I think I installed Brother with 20.04. It worked with USB, but I think I had scan issues until I connected it to Internet.
With my main working system, it shows 3 printers, but only one works well. I never installed any drivers. 
Only set up was to add printer to Internet. I think one is USB, one is Internet as my wife prints from her iPad and one just does not work.

I have this in my notes, but do not know when it changed.
ippusbxd is decidedly sub-optimal. Even its author would support your removing it from your system. 
It has been replaced by ipp-usb in later editions of Ubuntu. 

I installed 23.10. It only added one printer which just worked. I did nothing to configure it. But have not used it much.

---

### Post by oneleded on 2023-11-01
@oldfred; thanks for reply. i will eventually mark this solved

---

### Post by oneleded on 2023-11-03
i got this from the mint forum and thought it might help me figure this;; [https://forums.linuxmint.com/viewtopic.php?t=344245](https://forums.linuxmint.com/viewtopic.php?t=344245)
```
dav@dav-ms7b79:~$ avahi-browse -rt _ipp._tcp
+ wlx00c0cab1a9ea IPv6 HL_L2390DW @ dav-ms7b79                       Internet Printer     local
+ wlx00c0cab1a9ea IPv4 HL_L2390DW @ dav-ms7b79                       Internet Printer     local
+     lo IPv4 HL_L2390DW @ dav-ms7b79                       Internet Printer     local
+     lo IPv4 HL-L2390DW                                    Internet Printer     local
= wlx00c0cab1a9ea IPv4 HL_L2390DW @ dav-ms7b79                       Internet Printer     local
   hostname = [dav-ms7b79.local]
   address = [192.168.1.74]
   port = [631]
   txt = ["printer-type=0x9056" "printer-state=5" "Copies=T" "Duplex=T" "TLS=1.2" "UUID=2034966a-bb1d-30cf-5a6c-d5cdd618c6b2" "URF=DM3" "pdl=application/octet-stream,application/pdf,image/jpeg,image/png,image/pwg-raster,image/urf" "product=(Brother HL-L2390DW)" "priority=0" "note=" "adminurl=https://dav-ms7b79.local.:631/printers/HL_L2390DW" "ty=Brother HL-L2390DW, driverless, cups-filters 1.27.4" "rp=printers/HL_L2390DW" "qtotal=1" "txtvers=1"]
=     lo IPv4 HL_L2390DW @ dav-ms7b79                       Internet Printer     local
   hostname = [dav-ms7b79.local]
   address = [127.0.0.1]
   port = [631]
   txt = ["printer-type=0x9056" "printer-state=5" "Copies=T" "Duplex=T" "TLS=1.2" "UUID=2034966a-bb1d-30cf-5a6c-d5cdd618c6b2" "URF=DM3" "pdl=application/octet-stream,application/pdf,image/jpeg,image/png,image/pwg-raster,image/urf" "product=(Brother HL-L2390DW)" "priority=0" "note=" "adminurl=https://dav-ms7b79.local.:631/printers/HL_L2390DW" "ty=Brother HL-L2390DW, driverless, cups-filters 1.27.4" "rp=printers/HL_L2390DW" "qtotal=1" "txtvers=1"]
=     lo IPv4 HL-L2390DW                                    Internet Printer     local
   hostname = [dav-ms7b79.local]
   address = [127.0.0.1]
   port = [60000]
   txt = ["rfo=ipp/faxout" "Fax=T" "Duplex=T" "PaperMax=legal-A4" "URF=W8,CP1,IS4-1,MT1-3-4-5-8,OB10,PQ3-4-5,RS300-600-1200,V1.4,DM1" "pdl=application/octet-stream,image/urf,image/pwg-raster" "product=(Brother HL-L2390DW[en])" "ty=Brother HL-L2390DW[en]" "note=" "Color=F" "kind=document,envelope,label,postcard" "mopria-certified=1.3" "UUID=e3248000-80ce-11db-8000-4cd577b5f2a8" "adminurl=http://127.0.0.1:60000/net/net/airprint.html" "qtotal=1" "txtvers=1" "priority=60" "usb_MDL=HL-L2390DW" "usb_MFG=Brother" "rp=ipp/print"]
= wlx00c0cab1a9ea IPv6 HL_L2390DW @ dav-ms7b79                       Internet Printer     local
   hostname = [dav-ms7b79.local]
   address = [2600:381:ca8b:d6e5:5d61:58d3:ea46:3ee7]
   port = [631]
   txt = ["printer-type=0x9056" "printer-state=5" "Copies=T" "Duplex=T" "TLS=1.2" "UUID=2034966a-bb1d-30cf-5a6c-d5cdd618c6b2" "URF=DM3" "pdl=application/octet-stream,application/pdf,image/jpeg,image/png,image/pwg-raster,image/urf" "product=(Brother HL-L2390DW)" "priority=0" "note=" "adminurl=https://dav-ms7b79.local.:631/printers/HL_L2390DW" "ty=Brother HL-L2390DW, driverless, cups-filters 1.27.4" "rp=printers/HL_L2390DW" "qtotal=1" "txtvers=1"]
dav@dav-ms7b79:~$ avahi-browse -rt _uscan._tcp
+     lo IPv4 HL-L2390DW                                    _uscan._tcp          local                                                                                                       
=     lo IPv4 HL-L2390DW                                    _uscan._tcp          local                                                                                                       
   hostname = [dav-ms7b79.local]                                                                                                                                                             
   address = [127.0.0.1]                                                                                                                                                                     
   port = [60000]                                                                                                                                                                            
   txt = ["txtvers=1" "vers=1.3" "rs=eSCL" "ty=Brother HL-L2390DW" "pdl=application/pdf,image/jpeg" "cs=binary,grayscale,color" "duplex=F" "adminurl=http://127.0.0.1:60000./net/net/airprint.html" "UUID=e3248000-80ce-11db-8000-4cd577b5f2a8" "note=" "representation=http://127.0.0.1:60000./icons/device-icons-128.png"]                                                              
dav@dav-ms7b79:~$ driverless                                                                                                                                                                 
ipp://HL-L2390DW._ipp._tcp.local/                                                                                                                                                            
dav@dav-ms7b79:~$      

```
i dont have all the commands as i have not changed my printer name to the name necessary, in the rest of the commands. i thought to copy this before i lost it, for posterity. as soon as i figure that out, i will get back.
i think what i need for url is;  ipp://192.168.1.74/ipp/printer

---

### Post by oldfred on 2023-11-03
Please use code tags for text or terminal output.

Is your printer connection only network or also USB?

I do not remember installing any of these, but have them:
```
[FONT=monospace][COLOR=#54ff54]**fred@Z170-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$  ll /etc/cups/ppd/ [/COLOR]
total 44 
drwxr-xr-x 2 root lp 4096 Nov  3 00:00  [COLOR=#5454ff]**.**[/COLOR][COLOR=#000000]/ [/COLOR]
drwxr-xr-x 5 root lp 4096 Nov  3 22:46  [COLOR=#5454ff]**..**[/COLOR][COLOR=#000000]/ [/COLOR]
-rw-r----- 1 root lp 8942 Nov  3 00:00 'Brother_HL_L2390DW@BRW4023439CAFD6.local.ppd' 
-rw-r----- 1 root lp 8942 Oct  7 00:00  Brother_HL_L2390DW.ppd 
-rw-r----- 1 root lp 8935 Nov  3 00:00  Brother_HL_L2390DW_USB.ppd
[/FONT]
```

---

### Post by oneleded on 2023-11-07
i thought i had used code tags, guess i still dont understand that yet. the picture i uploaded, mentions cups-browsed. some of the sites i have found, say that cups-browsed can cause a problem, though it is in muon package manager and was preinstalled, and not downloaded with a snap, (snap also being a problem, according to some of the sites i visited).
i copied what you had down, an this is the output;; 
 ll /etc/cups/ppd/ 
total 32
drwxr-xr-x 2 root lp 4096 Nov  5 20:25 ./
drwxr-xr-x 5 root lp 4096 Nov  7 15:51 ../
-rw-r----- 1 root lp 8712 Nov  5 20:25 HL_L2390DW.ppd
-rw-r----- 1 root lp 8712 Nov  5 15:37 HL_L2390DW.ppd.O
dav@dav-ms7b79:~$ 
at the moment i am still trying to use USB, i will try WiFi tonight and tomorrow. i notice your output is way different then mine. 
DSCN.3309 is what i meant to post, perhaps the other picture will help also. muon package manager has (ppa-purge), i dont know if that can help. i am running  Ubuntu 20.04.6 LTS (lubuntu version).
i cant seem to find the ppd files that match this printer.

---

### Post by oneleded on 2023-11-09
i can connect with either usb or wifi. but in the end it doesnt matter because i need the PPD files or the drivers. i will see if brother is of any help, and go from there.

---

### Post by SeijiSensei on 2023-11-09
Modern Brothers can use "driverless printing." I've not had to do anything with recent Ubuntu or Debian offerings. I ran the Printer application in System Settings, chose add a printer, and it discovered my Brother over the network automatically. 

I have an HL-3170CDW.

---

### Post by oneleded on 2023-11-10
my printer was discovered, "no destination host name supplied by cups-browsed for printer HL-L2390DW" was the error,  an error probably by me in configuring. however, i added Sparky linux, and updated lubuntu to my system.
Sparky linux, discovered the printer and it prints without me doing anything. i got a different error on lubuntu 220.4.3 now, printer says the paper is wrong size. i cant seem to correct the error. that being said though, is a different problem. as long as it works with Sparky linux, i can print, so i will mark this solved for now.

---

### Post by oneleded on 2023-11-18
"ADDENDUM" usb live sparky linux, and usb live lubuntu (22.04), both had no problems with the printer. the printer worked well with both, i did not try scan with sparky 7 usb, but did with lubuntu usb, and it also scanned well.
i want to thank you all for trying to set me straight, with my printer problem.

---

