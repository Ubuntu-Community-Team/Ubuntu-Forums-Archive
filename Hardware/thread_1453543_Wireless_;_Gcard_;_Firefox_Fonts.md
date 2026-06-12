---
title: "Wireless ; Gcard ; Firefox Fonts"
date: 2010-04-13
forum: Hardware
---

### Post by bfh on 2010-04-13
Hey im new to this operating system and need some help setting up a few thing.

>im very new so if u can do step by step to help me set up my pc it'd be very nice of you.


1st off my laptop is a: Hp G60-324CA

System Specs;
Or go to link : 
[http://bizsupport2.austin.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&taskId=125&prodSeriesId=3884570&prodTypeId=321957&objectID=c01689792](http://bizsupport2.austin.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&taskId=125&prodSeriesId=3884570&prodTypeId=321957&objectID=c01689792)

**Product Name**   G60-324CA   **Product Number**  NM341UA#ABC  **Microprocessor**  2.10 GHz AMD Athlon X2 QL-64 Dual-Core Processor  **Microprocessor Cache**  1MB L2 Cache  **Memory**  3072MB  **Memory Max**  4096MB  **Video Graphics**  NVIDIA GeForce 8200M  **Video Memory**  Up to 1407MB  **Hard Drive**  250GB (5400RPM)  **Multimedia Drive**  LightScribe SuperMulti 8X DVD±R/RW with Double Layer Support  **Display**  16.0" Diagonal High Definition  HP BrightView Display (1366x768)  **Fax/Modem**  High speed 56k modem  **Network Card**  Integrated 10/100 Ethernet LAN  **Wireless Connectivity**  
[LIST]
[*]802.11a/b/g/n WLAN  (13)
[/LIST]
   **Sound**  Altec Lansing speakers  **Keyboard**  101-key compatible  **Pointing Device**  Touch Pad with On/Off button and dedicated vertical scroll Up/Down pad  **PC Card Slots**     **External Ports**  
[LIST]
[*]5-in-1 integrated Digital Media Reader for Secure Digital cards, MultiMedia cards, Memory Stick, Memory Stick Pro, or xD Picture cards
[*]3 Universal Serial Bus (USB) 2.0
[*]1 Headphone out
[*]1 microphone-in
[*]1 HDMI
[*]1 VGA (15-pin)
[*]1 RJ-11 (modem)
[*]1 RJ -45 (LAN)
[/LIST]
   **Dimensions**  14.88" (L) x 9.9" (D) x 1.38" (min H)/1.61" (max H)  **Weight**  6.52 Ibs  **Security**  
[LIST]
[*]Kensington MicroSaver lock slot
[*]Power-on password
[*]Accepts 3rd party security lock devices
[/LIST]
   **Power**  
[LIST]
[*]65W AC Adapter
[*]6-Cell Lithium-Ion battery
[/LIST]
   **What's In The Box**  HP Webcam with integrated microphone




Well Second off, i'd Like to change my fonts for Firefox, on some sites if lettering is small its hard to read.

>>Step by step please.

Third I'd Like To install my graphics card, i assume its not installed cause i can't change screen resolution from 800x600.


>>system specs above for this part.


Fourth, Id like to get my Pc wireless again, don't know what Wireless card is on pc.
but its a atheros something.



Thank For Reading hopeing to get support soon ^_^

---

### Post by gordintoronto on 2010-04-13
2. You can "zoom in" in Firefox by holding the "Ctrl" key and tapping "+".

3. Have you gone to Administration/Hardware Drivers? 

4. If you open Accessories/Terminal and enter the command:
lspci
you'll get about 20 lines of output. Near the bottom will be your wireless card.  

However, you might not need that information. Perhaps there's a network manager icon near the top-right of your screen, near the volume control. If you right-click it, select "edit connections," click the wireless tab then "add" and you have to enter your router's SSID, encryption type and password.

Oh, and if you are new to Ubuntu, you might not know that most people immediately install the "restricted extras," using Administration/Synaptic Package Manager

---

### Post by bfh on 2010-04-13
> **gordintoronto said:**
> 2. You can "zoom in" in Firefox by holding the "Ctrl" key and tapping "+".

3. Have you gone to Administration/Hardware Drivers? 

4. If you open Accessories/Terminal and enter the command:
lspci
you'll get about 20 lines of output. Near the bottom will be your wireless card.  

However, you might not need that information. Perhaps there's a network manager icon near the top-right of your screen, near the volume control. If you right-click it, select "edit connections," click the wireless tab then "add" and you have to enter your router's SSID, encryption type and password.

Oh, and if you are new to Ubuntu, you might not know that most people immediately install the "restricted extras," using Administration/Synaptic Package Manager



i right clicked it and theres no edit connections option.
2. i did lspci and it says did not reconize my chip (wireless)-

exact thing is said;

Network controller: Atheros Communications Inc. Unknown device 002a (rev 01)



i know about zoom, just on a few sites its very messy font >

---

### Post by bfh on 2010-04-13
still need help.

Screen shots if possible >

i really need wireless to be fixed first ~

---

### Post by gordintoronto on 2010-04-13
> **bfh said:**
> 2. i did lspci and it says did not reconize my chip (wireless)-

exact thing is said;

Network controller: Atheros Communications Inc. Unknown device 002a (rev 01)

I've never seen that before.  Perhaps HP can help you to identify the device.

Is this a dual-boot system? If so, Windows might provide some information.

---

### Post by bfh on 2010-04-14
> **gordintoronto said:**
> I've never seen that before.  Perhaps HP can help you to identify the device.

Is this a dual-boot system? If so, Windows might provide some information.


no i dont got dual boot atm.


wondering if madwifi will help me out in doing this


not sure how to install so, ima do a bit of research and find hp's # and maby give em a call to find out things about my pc.

>>what should i ask for - i know wifi chip but anything else ?



Edit:


Found this link about my pc;

[http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=4062&lc=en&dlc=en&cc=ca&lang=en&product=3925189](http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=4062&lc=en&dlc=en&cc=ca&lang=en&product=3925189)

straight from hp.

couple drivers there should i dl / install these ?

-ps > how would i do this install. (with wine)

or some commands in terminal.

please if i should do this, Leave detailed commands on how to do this ~

thanks



Edit #2:

Sent Hp an email should get information very soon about the exact specs on my wireless card.

---

### Post by bfh on 2010-04-15
K got the model for my wireless card Here is info;


 
 Wireless LAN 802.11a/g/n (Muscat) mini PCI adapter card - Upto 248Mbps data rate, 2.4GHz to 5GHz operating frequency range (Most-of-World)     




any help would  be appreciated, thanks step by step help plz

---

### Post by gordintoronto on 2010-04-15
> **bfh said:**
> K got the model for my wireless card Here is info;
 
 Wireless LAN 802.11a/g/n (Muscat) mini PCI adapter card - Upto 248Mbps data rate, 2.4GHz to 5GHz operating frequency range (Most-of-World)     

Sorry, that information doesn't tell you what chips are in the adapter. The HP link from your earlier message identified it as a Broadcom, but that's like saying "A North American car," when you need to know that it's a 2010 Chevy Camaro with the "3800" V6 engine.

Wine is for running (some) Windows applications under Linux, nothing to do with drivers.

And I'm out of my depth now. I found something that said you should not use Madwifi, which is what I thought the solution would involve.

Is it possible to have a (temporary) wired connection? Administration/Hardware Drivers might be useful.

---

### Post by bfh on 2010-04-16
Getting Close To Fixing ~

---

### Post by bfh on 2010-04-16
[COLOR=#004960]Atheros AR5009 802.11a/g/n wifi adapter


i beleave thats what i got ~

would like to try this;

[http://ubuntuforums.org/showthread.php?t=960962](http://ubuntuforums.org/showthread.php?t=960962)

can u explain how to install these files onto my pc ?

then how to install drivers > then i guess i guess i move onto trouble shoot guide
[/COLOR]

---

### Post by gordintoronto on 2010-04-16
Look at:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) 

especially section 2.2, which tells you how to use some other computer to get things onto your "unconnected" Ubuntu computer. Even though the instructions are old in parts, they are still true.

You can get the Broadcom driver from the HP site, which really simplifies one small part of the instructions.

I fully understand that the process is a huge PITA, and I wish I could somehow simplify it for you. One of the things I'm doing in my life is lobbying to fix this.

In addition to the thread you identified, it has a link to another good thread:
[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

Sorry this is such a hassle.

One approach to fixing this would be to say, "the heck with HP's piece of junk" and buy an adapter that works out of the box. It's not as easy with a laptop as with a desktop.

---

### Post by bfh on 2010-04-16
having trouble installing ndiswrapper


any 1 help with this ?

---

### Post by gordintoronto on 2010-04-16
The first file you got from the Packages site should be called:
ndiswrapper-common_1.54-2ubuntu1_all.deb 

Find it in Nautilus, double-click on it. Done.

---

### Post by bfh on 2010-04-16
Fixed

---

### Post by bfh on 2010-04-16
Fixed This Error

---

### Post by bfh on 2010-04-17
Okay Well i installed all my drivers and stuff I Get This message not sure if its write but i stopped all em errors i had before.





This is my current Screen; using- 
lshw -C Network


  *-network
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ndiswrapper latency=0 module=ndiswrapper

does this look right to any1 ?

also, i cant get my wireless to work (the button, when i click it)

so wondering what to do ~

i did try Function + f2 but it goes to a printer menu.

---

### Post by gordintoronto on 2010-04-17
> **bfh said:**
> also, i cant get my wireless to work (the button, when i click it)

so wondering what to do ~


What button?  Can you right-click on the network manager icon and see "edit connections"?

---

### Post by bfh on 2010-04-18
> **gordintoronto said:**
> What button?  Can you right-click on the network manager icon and see "edit connections"?

theres a button on my laptop that allows u to turn or turn off wifi.

well its not turned on - usually its blue but its orange atm.

-i tried clicking it and it doesnt turn blue.

on vista i know theres a program that disables it even if u try to turn on using the button.

im guessing that whats going on right now>

if u check this link out: [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

part 6 tells u about it, and i tried function + f2 key but it leads me to printer menu.


-any help ? :)

---

### Post by gordintoronto on 2010-04-18
Your manual will tell you what button to use. If it's Fn+F2, I don't know how to change it.  Have you tried Fn and each of the other function keys? Caution: one of them probably cycles your display among: onboard screen, VGA port, both. So if your screen goes black, press it twice more.

---

### Post by bfh on 2010-04-18
> **gordintoronto said:**
> Your manual will tell you what button to use. If it's Fn+F2, I don't know how to change it.  Have you tried Fn and each of the other function keys? Caution: one of them probably cycles your display among: onboard screen, VGA port, both. So if your screen goes black, press it twice more.


well i did try all the f* + fn dont work, ya fn + f2 = print option (like for your printer)

-try rest f5 and f4 make my screen go black ~ tried x2 times more and doesnt do it so had to restart ~ :(

---but any ways ive tried googleing a solution, but i cant think of any more phrases to google.

heres my full network stats using;

lshw -C Network

  *-network               
       description: Ethernet interface
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1d:72:7c:72:06
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=changed my ip here.. .latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ndiswrapper latency=0 module=ndiswrapper





Im guessing my wireless is installed correct cuz no errors on ndiswrapper are reported.
but ima try finding some more drivers for my card ~

-- since fn + f2 = printer, is there another cmd to press, or better yet a cmd i type into terminal to get it to work ?

---

### Post by gordintoronto on 2010-04-19
I'm way out of my depth now. Sorry.

---

### Post by bfh on 2010-04-20
Well if any1 can find me a link or help out plz do ~

still googleing no luck yet ~

---

