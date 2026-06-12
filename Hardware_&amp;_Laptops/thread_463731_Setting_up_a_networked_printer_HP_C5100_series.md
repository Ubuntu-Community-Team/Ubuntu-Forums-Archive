---
title: "Setting up a networked printer HP C5100 series"
date: 2007-06-04
forum: Hardware &amp; Laptops
---

### Post by Bohlio on 2007-06-04
I really need some help here. The printer I am trying to set up is a HP Photosmart C5180 All-in-one. The only other thread I've found on this printer has to do with setting it up when it is directly connected to the computer. With my setup, My Ubuntu PC is wireless, and the Printer connects to the router, where i can access it from anywhere. I read somewhere that there is a general HP driver that will work, I just cant remember what it is, but that isn't the problem. Im having a problem setting up the first step of adding a new printer.

I have the option of Local or detected, and Networked. It doesn't detect the printer so I select Networked. Then it has me choose from 4 different options

-IPP printer or printer on CUPS server (IPP)
       Which asks for the URL

-Windows Printer (SMB)
       Which asks for the Host, Printer, Username, and Password

-Unix Printer (LPD)
       Which asks for the Host, and Queue

-TCP/Socket, HP jetDirect, Raw connection
       Which asks for the Host, and the Port (default of 9100)

I'm really confused here as I don't even know which of the 4 different types to choose from. It would be a great help if someone could tell me what type the printer is, and how to find the information that it asks for.

If anyone has any input it would be greatly appreciated. I'm going to bed now and will check back in the morning. Thanks in advance, This community is great :-)

---

### Post by Bohlio on 2007-06-04
Ok I guess I solved my own problem. I guess this will serve as a guide for anyone else with the same setup as me. What I did was...

1. Woke up my printer so it was detected by my router and found the IP address (192.168.1.1)
2. Went to System>administration>printing and selected "New Printer"
3. Chose "Networked Printer"
4. Chose the 4th option in the drop down menu, TCP/Socket, HP jetDirect, Raw connection
5. Entered the IP address in the host category
6. Kept the port as the default (9100)
7.Selected Manufacturer (HP), Model (Photosmart C5100), and kept the recommended driver (hpijs)
8. For description, I put "Photosmart Printer" and for Location, I didnt quite know if this was something you could make up or not, so I put down the IP address again :-P
9. Hit apply and the printer showed up in the printer area, Printed a nice ubuntu test page, and it worked great.

I hope this helps someone :-D :-D

---

### Post by fireslack on 2007-07-30
Thanks for posting this.  I have an HP Photosmart C5180 on my network.  I had it working in Ubuntu but I had to replace the hard drive and re-install.  As much as I tried I could not figure out how I did it the first time.  Your instructions worked perfectly.

---

### Post by Bohlio on 2007-08-06
Glad I could help :D

---

### Post by CSalat on 2007-08-25
Same works for networked HP Photosmart C7180..

---

### Post by ricardisimo on 2007-09-04
> **Bohlio said:**
> 1. Woke up my printer so it was detected by my router and found the IP address (192.168.1.1)


Where are you finding this address? I'm looking in "Network Tools", but the addresses there don't appears to be helping. Thanks in advance.

---

### Post by ricardisimo on 2007-09-04
<bump>

---

### Post by pizzipie on 2007-10-26
Thanks Bohlio;
I had a problem that turned out to be the wrong location. Thanks to your Post I got things fixed and the printer is Printing !!!!!

RP

---

### Post by Strangerdave on 2007-10-28
Oh Man I have been looking for something like this for a couple of weeks now!  Thanks for posting it, I have a HP Photosmart D7460 and had to choose HP Photosmart 7300, but it seemed to have worked.

Thanks again,

-SD-

---

### Post by mr-kc-sir on 2007-11-04
Thanks for posting this. To often people put "oh I fixed it" and never explain how.

---

### Post by tbedolla on 2007-12-02
To Everyone on this thread,

I'm trying to set up a C4180 on my wireless network, I've got a wireless printserver (Linksys WPSM54G) that I can access via browser ([http://192.168.0.11](http://192.168.0.11)) and for the life of me just can't get this to print wirelessly. Works on my girlfriends Windows laptop, but I can only print when directly connected. I can't seem to let this go and hope someone else on this thread is using a wireless printserver and has had success.

Fingers crossed,

T

---

### Post by neilg4rqn on 2008-03-25
> **Bohlio said:**
> Ok I guess I solved my own problem. I guess this will serve as a guide for anyone else with the same setup as me. What I did was...

1. Woke up my printer so it was detected by my router and found the IP address (192.168.1.1)
2. Went to System>administration>printing and selected "New Printer"
3. Chose "Networked Printer"
4. Chose the 4th option in the drop down menu, TCP/Socket, HP jetDirect, Raw connection
5. Entered the IP address in the host category
6. Kept the port as the default (9100)
7.Selected Manufacturer (HP), Model (Photosmart C5100), and kept the recommended driver (hpijs)
8. For description, I put "Photosmart Printer" and for Location, I didnt quite know if this was something you could make up or not, so I put down the IP address again :-P
9. Hit apply and the printer showed up in the printer area, Printed a nice ubuntu test page, and it worked great.

I hope this helps someone :-D :-D

Yes indeed it did, thanks all involved. BUT has anyone got one to scan from the desktop?

---

### Post by click4851 on 2008-04-24
kudos - again, I now have full functionality of my HP C6180 AIO, saved me from buying a print server.....

...scan from the desktop? say that again?

---

### Post by neilg4rqn on 2008-04-25
Someone asked about the printers network address - it is available (on the 5100 series at least) from the printers own menu on the pop-up screen, look for network settings, you can also then fix the address which does help if it is switched off and on as otherwise it can change. 
I used to be able to remote scan but now can't and I would really like to get it back - any ideas?

---

### Post by pmaconi on 2008-04-25
Another way to set up an HP network printer is to use [HPLIP]("http://hplip.sourceforge.net/"). Just follow the instructions on that website as well as the on-screen prompts and it will be set up for you. The only part of my printer that I cannot get to work is reading the photocard over the network. If anyone knows how, I would greatly appreciate the help.

---

