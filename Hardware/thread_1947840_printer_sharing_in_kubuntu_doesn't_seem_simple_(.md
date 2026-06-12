---
title: "printer sharing in kubuntu doesn't seem simple :("
date: 2012-03-27
forum: Hardware
---

### Post by norima on 2012-03-27
I set up a kubuntu 11.10 with an Epson TM-T88IV (USB) thermal printer attached to it.  Painstakingly followed whatever tutorial i could find on the web and luckily I managed making the printer shared and published from the server (!!..and it feels good..!!)...  problem is, this shared printer though visible to some other kubuntu 11.10 client (USBPrint@computer_name) it doesn't seem to print any.  

I tried some other alternatives like IPP although printing a testpage works just fine, my java application has no capability recognizing a PrintService residing from a remote computer :(.. Now I stuck with "bonjour" but I coudn't make it work..

Any suggestions or links that can help me get enlightened are highly appreciated..

thank you in advance...

---

### Post by norima on 2012-03-27
Is

dnssd://USBPrint%20%40%20crown-b2-t5._ipp._tcp.local/cups

correct?

is it possible that the 'dash' in computer name causes the malfunction?

---

### Post by s1hr on 2012-03-27
there is also another elegant way to share printer on home network.

simply, probablly u have router, today most of routers have usb , and then just connect ur printer with cable with printer.

what i get from using that, i get that all computers in my home regardless of operating system,most are on Ubuntu, can send print to those printer(actually is printer,scanner,copy machine,fax, 4in1 device..)

then as router is allways on, any computer in home can be swithed off...printing will work.

best thing, to the router some computer use wired conection,and some laptops and tablets are connected by wireless to the router, so i get wireless printer...from printer which not have wireless capability...

how to do that u can find in particular manual of ur router.
 one of the 3 way what i know is to use samba, but basically u just send printing to samba adress of ur printer..its simply.
its network shared printer,..thats it.
just follow how to add network shared printer,here...
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu")

ipp and cups are simple and fine to use if u have just linux,ubuntu computers, but if u wanna that also some windows computer use ur printer together with ubuntu machines,samba is better option!

if yours router dont have usb port or u dont want to use that, basically its same if u connect printer to any of yours computers but for sharing that particular computer logically must be allways ON..otherwise that printer will be not accesibile to others computers and devices on yours network,home network,when u swich-off that computer where is printer connected.....

):P

---

### Post by s1hr on 2012-03-27
try to open this address in your browser:

  [http://localhost:631]("http://localhost:631")

read about network printing with ubuntu ,here on this page in Ubuntu manuals.

  [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu")

as,i saw u r trying to use CUPS..

---

### Post by s1hr on 2012-03-27
if u go that way ,using CUPS, then u will use ipp protocol, what means address of ur printer will start with ipp:/..... ,as i remember..

i use samba, and address in SAMBA is same,difference is that start with smb:/

regardless what method u will choose, best way is to make first printer work alone..as not shared printer.

Then read steps in this link
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu")

seems that u use cups driver for ur printer, so this link is steps which u need to follow

[https://help.ubuntu.com/11.04/serverguide/C/cups.html]("https://help.ubuntu.com/11.04/serverguide/C/cups.html")

if u want to use other method, as i use,samba protocol then this link is right
[https://help.ubuntu.com/11.04/serverguide/C/samba-printserver.html]("https://help.ubuntu.com/11.04/serverguide/C/samba-printserver.html")

all is allready written there,just follow,and good luck, hope all those helps you.):P ):P ):P

---

### Post by norima on 2012-03-27
first of all, id like to thank s1hr for all your replies those are very valuable inputs for me.
okay, weird thing is 'why i get affected with the waving smily' -hope it doesnt concern with my career hehe... 

well, it actually just between kubuntu 11.10 to kubuntu 11.10 printer sharing so definitely i think i wont be needing samba stuff here..  

i proceed to using IPP and here's my setup

Description:	printer
Location:	
Driver:	EPSON TM-T88IV (rastertotmt) (grayscale, 2-sided printing)
Connection:	ipp://192.168.1.37:631
Defaults:	job-sheets=none, none media=om_rp80x297_71.96x296.96mm sides=one-sided

when i did a print test page i encountered an error saying "The printer URI is incorrect or no longer exists" but i'm 100% sure i can ping 192.168.1.37.. how can this be? do i miss/mess something?

printer-21 	Test Page 	anonymous 	1k 	1 	pending since
Wed Mar 28 10:35:04 2012 
"The printer URI is incorrect or no longer exists."

---

### Post by mastablasta on 2012-03-28
> **norima said:**
> well, it actually just between kubuntu 11.10 to kubuntu 11.10 printer sharing so definitely i think i wont be needing samba stuff here.. 

 
 
It was suggested as a solution and i wouldn't dismiss it just like that.

---

### Post by norima on 2012-03-28
indeed im wrong my life gets a lot easier using the samba as print server for my epson tm-t88iv thermal printer in kubuntu... when tested from windows client printing works perfect. but  in kubuntu client it has an error says "usr/lib/cups/backend/epsontm failed" 

what could possibly be wrong? is it perhaps the epson tm driver for linux im using? kubuntu client has trouble recognizing the USB type printer? 

Nevertheless, I know I'm almost there to success!

thank you guys!

---

### Post by mastablasta on 2012-03-29
> **norima said:**
>  is it perhaps the epson tm driver for linux im using?

Could be. hard to say. 
 
so what you are trying to do is use printer that is connected via USB to Kubuntu? and it uses CUPS?
 
> 
kubuntu client has trouble recognizing the USB type printer? 

 
No problems here. using samsung printer/scanner though.

---

### Post by norima on 2012-03-29
okay here's my success story to share!

here's what actually happened... i setup a kubuntu 11.10 machine with an EPSON TM-T88IV receipt printer attached to it via usb... i installed the suggested driver and it was able to work alone with no issue at all.  the real issue is when i had to share the printer from the network.  im a newby in ubuntu so things are really driving me nuts! i did try downgrading my setup from 11.10 to 9.04 to see if it were really an issue in CUPS but the result are just the same. 

praise God for His infinite wisdom that samba has been invented! i able to test why that my windows xp setup can just print to my ubuntu server seamlessly.. doesnt just too weird? so, i dig into the subject of "maybe its actually the driver is failing" hmm.. too much with the reasoning i tested another driver built in the ubuntu i picked the generic postscript printer... things worked! now im done, weird it may be because its not supposedly the driver of my Epson TM-T88IV but it serves my purpose.. CHEERS!!!

thank you guys with out the support here probably i will take another year to figure this out.. :guitar:

---

### Post by mastablasta on 2012-03-29
which means the problem is indeed in the driver. 
 
you can now use the thread tools in top right corner to mark thread as solved so another one with same issue will find your solution.
 
if you feel up to it it might be a good idea to report a bug to launchpad.

---

