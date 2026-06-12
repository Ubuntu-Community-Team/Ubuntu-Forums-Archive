---
title: "Enabling duplex printing in Epson l210 MultiFuntional inkjet printer"
date: 2014-05-20
forum: Hardware
---

### Post by nashtrik on 2014-05-20
I am running CUbuntu 14.04 LTS 64 Bit (not KUbuntu..) and have Epson l210 MF inkjet printer installed.With the drivers supplied by Epson (201207w),it performs all the normal jobs but doesn't provide the manual duplex printing facility which the same printer performs perfectly when connected to windows. Does the CUPS provide some equivalent/better printer drivers than the company supplied driver..? Is it possible to modify CUPS configuration to enable manual duplex printing.
                                                                                                                                          Any answers with detailed instructions are most welcome. Thanks.

---

### Post by pdc on 2014-05-20
If you select your printer from the Printer settings box; right-click; you can see in printer options there is a duplex box;

can you alter that? Do the changes stay?

---

### Post by nashtrik on 2014-05-20
I'm sorry buddy,I haven't seen the w

ord 'duplex' in any of the printer dialog boxes.....

---

### Post by pdc on 2014-05-20
if you open a terminal: type terminal in your dash search area if you don't know what it is ...........

paste > [COLOR="#FF0000"]system-config-printer[/COLOR] into the terminal; and hit the enter key: 

if you get: command not found then paste this into the terminal > [COLOR="#FF0000"]sudo apt-get install system-config-printer[/COLOR]

select your Epson by right-click; select Properties with left-click (it will likely be highlighted in blue..........); that opens the dialogue box in the picture I enclosed

go down four options to Printer Options; on my screen, use the scroll function at the right of the dialogue box: Duplex is at the bottom of the list ..

..........any joy?

---

### Post by nashtrik on 2014-05-20
I have autopsied all the available printer options, Duplex option simply doesn't show....I have even opened [http://localhost:631](http://localhost:631) and tried to find the Duplex option,but the result is the same.....I will try to send the screenshots to you...

---

### Post by pdc on 2014-05-24
just seen this; so I think you are showing me that if you scroll down through the Printer Options settings; all the way to the bottom of the list; that there is no duplex setting there

---

### Post by nashtrik on 2014-05-31
Exactly....there is no duplex setting all the way to the bottom of the list. After burning my midnight oil for quite a few days now ,one thing I know for sure is that I will have to copy- paste duplex enabling code from some other compatible ppd file to my printer's ppd file,but I don't know which file and which portion of the code....any Ideas there...?

---

### Post by pdc on 2014-05-31
have a look in the ppd folder that is in /usr/share and you should find your epson ppd file there 

to read it first of all 

> gedit /usr/share/ppd/epsonwhatever.ppd    (some may prefer to do this first as any changes cannot be saved ......so mess with impunity it seems .........)

and then to edit it and save changes; closed gedit and then 

> gksudo gedit /usr/share/ppd/epsonwhatever.ppd

the lines in our Canon ppd that relate to duplex: (our printer does duplex)

> *OpenUI *Duplex/Duplex Printing: PickOne
*DefaultDuplex: None
*Duplex None/OFF: "<</Duplex false>>setpagedevice"
*Duplex DuplexNoTumble/ON (Long Side Stapling): "<</Duplex true/Tumble false>>setpagedevice"
*Duplex DuplexTumble/ON (Short Side Stapling): "<</Duplex true/Tumble true>>setpagedevice"
*CloseUI: *Duplex

---

### Post by nashtrik on 2014-06-02
Okay....so what all copy-pasting the above piece of code to my /etc/cups/ppd/EPSON-L210-Series.ppd did, was only to display the duplex printing options in the printer properties,which by default was off.I toggled it to ON with left side stapling option and had a test print, but the printer did not stop after printing the first page so that I could turn the paper around. It simply continued to print on a fresh page from the tray.
                                                                                                                                                                                           I think some more code has to be added so that the printer pauses after printing the first page to take the manual feed.....The ball is again in your court pal.......

---

