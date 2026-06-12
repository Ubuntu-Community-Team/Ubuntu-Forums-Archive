---
title: "HP Office Jet 4650 no longer recognized by my system"
date: 2018-03-16
forum: Hardware
---

### Post by Jane_Ralph on 2018-03-16
I specifically bought this printer because my old one did not work with Ubuntu, and it worked just fine for months.  But now it stopped.  I am terribly ignorant about using the Terminal and have NO idea what to look for or how to fix this.  Any help sincerely appreciated, even first baby steps to find out WHAT I need to find out...??

Thanks.

---

### Post by him610 on 2018-03-16
If it worked before, then it is probably misconfigured. When you first set it up, did you happen to set a permanent IP address on your printer? If not, then it is possible your router may have assigned a different IP address using DHCP (Dynamic Host Configuration Protocol.) What make and model is your router?

Is this your printer...
[https://www.amazon.com/HP-OfficeJet-Wireless-Printing-F1J03A/dp/B013SKI4X8]("https://www.amazon.com/HP-OfficeJet-Wireless-Printing-F1J03A/dp/B013SKI4X8")

Does this accurately describe your problem?
"You have successfully connected your printer to a wireless network, but the connection drops. When the printer loses its connection, the printer goes offline and you cannot print or scan."

Here is the link to HP's troubleshooting page...
[http://hp.dezide.com/ts/start.jsp?guide=Printer_Does_Not_Maintain_Wireless_Connection.net&as=true&section=ccweb&sfs=sdoc&language=english&lc=en&cc=us&action=step&response=0&step=C39512&session=094a58d9-6c7d-4964-b889-bd8bd1](http://hp.dezide.com/ts/start.jsp?guide=Printer_Does_Not_Maintain_Wireless_Connection.net&as=true&section=ccweb&sfs=sdoc&language=english&lc=en&cc=us&action=step&response=0&step=C39512&session=094a58d9-6c7d-4964-b889-bd8bd1)

If this doesn't help, maybe we can try something else.

---

### Post by pdc on 2018-03-16
hi Jane; ...... now might be the time to try the terminal ....... but do tell us if this is a usb cable connection ........... ?

If you open a terminal; hold the control and alt and t keys down together ....... and type or copy the command ```
lpinfo -v
```     .... that is asking lp (linux printing) to give info about what it sees ...... and the -v asks it to give a full reading (also called verbose)

if you select the text in the terminal; and copy it (instead of control and c as one would use in most programmes, it is three keys again ..... control and shift and c keys ...........) and then if you paste that back here please

---

### Post by Jane_Ralph on 2018-03-17
OK, first yes, that is my printer. 

 Off to try that terminal thing now... OK, that worked, and it also explains why I could never copy anything into or out of the terminal

network ipps
network lpd
network https
network ipp
network http
network socket
network ipp14
network beh
direct hp
network smb
direct hpfax

I've looked all over the printer and all I can see is one cord leading to a regular electric socket.  But I did turn the printer on and try that terminal thing again with slightly different results, posted here:network ipps
network https
network ipp14
network beh
network lpd
network ipp
network socket
network http
direct hp
network smb
direct hpfax
network dnssd://HP%20OfficeJet%204650%20series%20%5BDFB3D7%5D._ipp._tcp.local/?uuid=1c852a4d-b800-1f08-abcd-40b034dfb3d7
network socket://10.0.0.7:9100

---

### Post by ank2 on 2018-03-17
> **Jane_Ralph said:**
> I specifically bought this printer because my old one did not work with Ubuntu, and it worked just fine for months.  But now it stopped.  I am terribly ignorant about using the Terminal and have NO idea what to look for or how to fix this.  Any help sincerely appreciated, even first baby steps to find out WHAT I need to find out...??

Thanks.

Suppose you use CUPS have a look at [http://127.0.0.1:631](http://127.0.0.1:631) to see if all is set up properly.

also have a look into files at /var/log/cups/ to see if the problem is mentioned there.

---

### Post by Jane_Ralph on 2018-03-17
Sorry, Ank2, but I have NO idea how to "use CUPS" to look at anything!

---

### Post by agillator on 2018-03-18
To check CUPS as ank2 suggested, open a browser and go to address 127.0.0.1:631. That will connect you to the CUPS manager on your computer. Once there select 'Printers' in the menu. See if your printer is there. If so, go through both the administration and maintenance menus and see if anything stands out as a problem. Often error messages there will tell you what the problem is.

---

### Post by Jane_Ralph on 2018-03-18
Thanks, I guess ank2 did tell me how to do it, I just didn't make the connection.

I tried to get it to print a test page, and got the error message, "job 37 is not held".

Printer wakes up when computer wakes up, but won't print a page from the computer.  Nor did it print the test page from CUPS.  I am completely stymied.

---

### Post by pdc on 2018-03-18
Hi Jane; 

so > lpinfo -v is seeing your printer ........ that is good .......

_____________________

what about we get you to find the PRINTERS folder; ..... if you type that in the Dash search area, it should find it for you ........

..... then, there is only one icon in the PRINTERS folder for your 4650? 

If you right-click on that, select PROPERTIES and look in the box that says MAKE & MODEL ..........  By chance, we have one and so I enclose a screenshot of what it should show  ... at least, it is what ours says; and it still seems to work ok;

can you copy what MAKE & MODEL  says and paste it back here ..... just so we know what it was saying

___________

As it doesn't work, I would suggest you close the window that showed Properties; then right-click on the 4650 icon; and select DELETE ...... as it isn't working; 

Then I would suggest opening the dreaded terminal: ....... you were an ace the last time!! ............. and typing ```
hp-setup
``` and that should ......... sort of create a new, and working, icon ........

any joy?

---

### Post by oldos2er on 2018-03-18
pdc, a friendly bit of advice: Please try to avoid the use of ellipses in technical support posts. Some of us find them obfuscating rather than enlightening. Thanks.

---

### Post by Jane_Ralph on 2018-03-19
Well this is interesting.  When I right-clicked on the single icon in my Printers folder, it said HP Deskjet 5550.  That is NOT my printer!  But if I left-click on the single icon, I get HP OfficeJet 4650.  I am now more confused than ever.

---

