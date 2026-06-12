---
title: "Epson printer printing same text twice, need driver help?"
date: 2017-03-08
forum: Hardware
---

### Post by crabbyjunior on 2017-03-08
Hello, forgive me as im relatively new to Ubuntu, i recently bought an Epson wf-2630 printer, it copies and scans perfect with no problems but when i print anything this is when the problems start.

If i was to print a page of text in black, it would print it fine but in the background there would be a perfect duplicate of what im printing only it will be 10mm above the original text and also its always in yellow. its like a yellow shadow above the original. 

i contacted Epson support to which they ruled out a problem with the printer and said as they dont make drivers for linux, i was to contact the provider of the drivers. 
I am assuming when i was installing the drivers i probably done it wrong as it was confusing for me. when i tried to install them from the Epson website i kept getting errors and messages saying they were in the wrong format. after a while i finally thought i had it sorted. which i did to an extent but my only problem remaining is this shadow.

has anyone any advice for me? id be very grateful. As i said my knowledge of Ubuntu and using the terminal is limited.

Thanks,
Crabby

---

### Post by SeijiSensei on 2017-03-08
Do you have access to a Windows machine you can use for testing?  If so, see if you get the same output from the printer with Windows.  If so, it's not likely to be a driver problem.

---

### Post by pdc on 2017-03-08
very valuable if you can test as above;

to check what drivers Epson recommend they seem to recommend you have the epson-inkjet-printer-escpr_1.6.12-1lsb3.2_amd64.deb installed; (if you have a 64bit install)

if you open a terminal: the control alt t keys ............... and paste in > [COLOR="#FF0000"]dpkg -l epson*[/COLOR]        ........ that is asking the debian package system (dpkg) to **LIST** any packages installed that have *epson* in the title .............

....... to paste into the terminal; right-click at the prompt ......... from the menu that appears ...... select PASTE ...........

if you tell us what you see ....... also check in your PRINTERS icon for the WF2630 icon; right-click on it; it will select *properties* ..... it should then open on *settings* ........ maybe enlarge the window a little to the right ........ look in **Make & Model**: it should list the driver installed ... should be same as above ..

if we see how things go with Seiji's suggestions and mine ............

---

### Post by crabbyjunior on 2017-03-08
Quick reply to seiji, sorry no this is the only Pc i have access to at the moment i could check this possibly tomorrow if i bring my printer over to work and try it.

as for pdc, iv done what you said pasted that into terminal this is what i got:

qube@The-Qube:~$ dpkg -l epson*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
iU  epson-inkjet-p 1.6.12-1lsb3 i386         Epson Inkjet Printer Driver (ESC/
rc  epson-printer- 1.0.1-1lsb3. i386         Epson Printer Utility for Linux

as for checking the make and model i got this:  Device URI: dnssd://EPSON%20WF-2630%20Series._ipp._tcp.local/?uuid=cfe92100-67c4-11d4-a45f-64eb8c5eb682
                                                                     Make and model: Epson WorkForce 30 - CUPS+Gutenprint v5.2.11

hope this is what you asked for, and thanks to both of you for your swift replies. 
thanks,
crabby

---

### Post by pdc on 2017-03-08
many thanks;

so you have the drivers installed that Epson recommend; but to install a printer, after installing the drivers, one then needs to tell lpadmin (linux printing admin) what to use, when you want files sent to a certain printer ......... there seems to have been a hiccup in stage 2 for you ..

so you have the epson drivers installed, but the system is using [COLOR="#0000FF"]gutenprint[/COLOR], the open source printing system, that is very good and covers a huge range of printers; however it has allocated you the > [COLOR="#0000FF"]Epson WorkForce 30[/COLOR] - [COLOR="#008000"]CUPS+Gutenprint v5.2.11[/COLOR]           ............ and I see the Epson suggestion for the elderly Workforce 30 would be the much older pips-sot30-ubuntu8.04-3.5.0-CG.tgz ......... rather than the epson-inkjet-p 1.6.12-1lsb3

_____---

I would suggest deleting the current icon for your WF from the PRINTERS folder; then click ADD at the top-left of that PRINTERS folder; then you search on network printer; ....... give it a chance to hunt around ............   it should find it .....   hopefully that will allocate the correct driver this time to your WF ..... but you can check the way you have just done ..

under **Make & Model** it would be good to see something next time like > [COLOR="#0000FF"]Epson WF-2630[/COLOR] [COLOR="#008000"]epson-inkjet-p 1.6.12-1lsb3[/COLOR]

---

### Post by crabbyjunior on 2017-03-08
Thank you, thank you, thank you.... It took me three or four tries there but eventually manually searched for it and found the right one, finally that silly shadow is gone on the printed page.

i should have knew that because as soon as you mentioned it, it reminded me that i could not find the exact printer model the first time round. I must have accidentally picked an older model. 

Again a big thanks for all the help and how detailed and patient you were towards an amateur,

---

### Post by pdc on 2017-03-08
delighted to hear all is good, and delighted to help you fix it: one always learns by posting to others!! ..... I'm always learning, so grateful to help: enjoy

...... somewhere in thread tools; top-right, you can edit your thread to say "SOLVED" so if you want to do that; I will edit the title of my post just so folks may also find that

---

