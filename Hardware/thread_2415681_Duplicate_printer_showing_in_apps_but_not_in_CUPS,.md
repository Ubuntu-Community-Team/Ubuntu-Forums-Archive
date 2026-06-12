---
title: "Duplicate printer showing in apps but not in CUPS, how to remove??"
date: 2019-03-29
forum: Hardware
---

### Post by ajm83 on 2019-03-29
Hi,  I have a question about printers, specifically I want to know why a printer is listed twice in the print screen on various programs:

[ATTACH=CONFIG]282884[/ATTACH][ATTACH=CONFIG]282885[/ATTACH]

Yet in the Printers control panel, it is only listed once:
[ATTACH=CONFIG]282887[/ATTACH]

And only once on the CUPS web UI:

[ATTACH=CONFIG]282886[/ATTACH]

And only once in lpstat:

```
lpstat -s
system default destination: HP-LaserJet-CP-1025nw
device for HP-LaserJet-CP-1025nw: ipp://NPI96054C.local:631/printers/HP_LaserJet_CP1025nw

```

The problem is that for whatever reason people clicking the duplicate one, and it does not work.  

Does anybody know where it comes from and how to remove it?  Thanks!!

---

### Post by ajm83 on 2019-03-30
Made some progress! I discovered that lpstat -ev shows the duplicate:

```
lpstat -ev
HP-LaserJet-CP-1025nw
HP_LaserJet_CP_1025nw
device for HP-LaserJet-CP-1025nw: ipp://NPI96054C.local:631/printers/HP_LaserJet_CP1025nw


```

This lead me to this answer to someone with the same problem (and a different brand of printer, mine's HP)
[https://askubuntu.com/questions/676863/how-do-i-get-rid-of-a-ghost-printer-in-gnome](https://askubuntu.com/questions/676863/how-do-i-get-rid-of-a-ghost-printer-in-gnome)

Anyway it looks like some kind of non-functional autodiscovery over the network.  In my case,  disabling bonjour on the printer's web config removes it from the print dialog.

For anyone who finds this via google, the setting in question is found here:
[img]https://i.imgur.com/c7gAS0d.png[/img]

---

### Post by brian_p on 2019-03-30
Please enable Bonjour on the printer and give the outputs of

```
avahi-browse -rt _ipp._tcp
```
```
lpstat -l -e
```

With Bonjour disabled there is probably only one entry shown in the LibreOffice print dialog. Can you  print to it?

---

### Post by brian_p on 2019-03-30
> With Bonjour disabled there is probably only one entry shown in the LibreOffice print dialog. Can you print to it?

I've changed my mind over this. You have

[list]device for HP-LaserJet-CP-1025nw: ipp://NPI96054C.local:631/printers/HP_LaserJet_CP1025nw[/list]
This is an auto-setup configuration by cups-browsed (why CP-1025nw and not CP1025nw?). cups-browsed gets it from Bonjour, so it will not be found if Bonjour on the printer is turned off. Nothing should be shown in the Printers control panel and the CUPS web interface or in any print dialog.

---

### Post by brian_p on 2019-03-31
Irrespective of whether the original query has been completely treated, it would still be very useful for other purposes (troubleshooting in future printing problems, for example) to have the output of

```
avahi-browse -rt _ipp._tcp
```

---

### Post by ajm83 on 2019-04-02
Sorry Brian, I didn't get notified about your replies,  I will re-enable Bonjour on the printer and grab the output tonight from the commands you listed.

> [COLOR=#000000]With Bonjour disabled there is probably only one entry shown in the LibreOffice print dialog. Can you print to it?[/COLOR]

With Bonjour disabled I have one working printer that I think was autodiscovered and shows in the Printers control panel.

With Bonjour enabled, I have that same printer, still working, plus one listed as REJECTING JOBS.  Same as in the post I linked from AskUbuntu.com above.

---

### Post by brian_p on 2019-04-02
Thank you for getting back to us, ajm83.
> 
With Bonjour disabled I have one working printer that I think was autodiscovered and shows in the Printers control panel.

I'll have to think about this; I am unsure whether it is the result of autodiscovery. Please add the output of

```
lpstat -t
```

to the other information you supply.
> 
With Bonjour enabled, I have that same printer, still working, plus one listed as REJECTING JOBS.  Same as in the post I linked from AskUbuntu.com above.

This is shown in the GTK print dialog (used by Firefox and evince). The REJECTING JOBS is the result of a bug in the way the dialog gets an entry for a network printer.

[https://gitlab.gnome.org/GNOME/gtk/issues/1509](https://gitlab.gnome.org/GNOME/gtk/issues/1509)

Turning off Bonjour on the printer is one way of not having a non-working entry, as you have demonstrated. There are drawbacks to that though when it comes to LibreOffice, whose dialog behaves in a different way from FireFox's.

---

### Post by ajm83 on 2019-04-02
As requested:

> avahi-browse -rt _ipp._tcp
```
root@howard:~# avahi-browse -rt _ipp._tcp
+ wlp1s0 IPv4 HP LaserJet CP 1025nw                         Internet Printer     local
= wlp1s0 IPv4 HP LaserJet CP 1025nw                         Internet Printer     local
   hostname = [NPI96054C.local]
   address = [192.168.1.90]
   port = [631]
   txt = ["Staple=F" "Sort=F" "Scan=F" "Punch=0" "PaperCustom=F" "Duplex=F" "Copies=F" "Color=T" "Collate=F" "Bind=F" "Binary=T" "Transparent=T" "UUID=17a8cd2e-c532-5844-90ed-11f2f91cb0f5" "note=Spare Bedroom" "adminurl=http://192.168.1.90" "mac=34:64:A9:96:05:4C" "priority=40" "usb_CMD=ZJ/URF" "usb_MDL=HP LaserJet CP 1025nw" "usb_MFG=Hewlett-Packard" "product=(Hewlett-Packard HP LaserJet CP 1025nw)" "ty=HP LaserJet CP 1025nw" "URF=CP1,IS1,OB10,PQ3-4-5,RS600,W8,SRGB24,MT1-2-3-4-5-6-8-10-11-12" "rp=printers/HP_LaserJet_CP1025nw" "pdl=image/urf,application/PCLm" "qtotal=1" "txtvers=1"]

```

> lpstat -l -e
```
root@howard:~# lpstat -l -e
HP-LaserJet-CP-1025nw permanent ipp://localhost/printers/HP-LaserJet-CP-1025nw ipp://NPI96054C.local:631/printers/HP_LaserJet_CP1025nw
HP_LaserJet_CP_1025nw network none ipp://HP%20LaserJet%20CP%201025nw._ipp._tcp.local/

```

> lpstat -t
```
root@howard:~# lpstat -t
scheduler is running
system default destination: HP-LaserJet-CP-1025nw
device for HP-LaserJet-CP-1025nw: ipp://NPI96054C.local:631/printers/HP_LaserJet_CP1025nw
HP-LaserJet-CP-1025nw accepting requests since Fri 29 Mar 2019 21:36:43 GMT
printer HP-LaserJet-CP-1025nw is idle.  enabled since Fri 29 Mar 2019 21:36:43 GMT

```

---

### Post by brian_p on 2019-04-03
From the avahi-browse output:

[LIST]
[*]rp=printers/HP_LaserJet_CP1025nw
[/LIST]
*rp=* is the Resource Path for the printer. Firefox uses this to put an entry (non-working due to a bug) in its dialog. You can replace this entry by one with the same name with

```
lpadmin -p HP_LaserJet_CP1025nw -v ipp://NPI96054C.local:631/printers/HP_LaserJet_CP1025nw -E -m everywhere
```

This should give a working entry and, with Bonjour operative, the printer will still be visible on the network to other devices and their applications.

---

### Post by ajm83 on 2019-04-03
> **brian_p said:**
> From the avahi-browse output:

[LIST]
[*]rp=printers/HP_LaserJet_CP1025nw 
[/LIST]
*rp=* is the Resource Path for the printer. Firefox uses this to put an entry (non-working due to a bug) in its dialog. You can replace this entry by one with the same name with

```
lpadmin -p HP_LaserJet_CP1025nw -v ipp://NPI96054C.local:631/printers/HP_LaserJet_CP1025nw -E -m everywhere
```

This should give a working entry and, with Bonjour operative, the printer will still be visible on the network to other devices and their applications.

Thanks for this.

There are three bugs here IMO.

1.  Non-operative printer, as discussed.
2.  Non-operative printer not appearing in the Printers control panel therefore unable to be disabled or inspected by a regular computer user who is unfamiliar with the command line.
3.  The same printer appearing twice in the first place. The system should recognise that this is the same printer and show only the best method of connecting to it.

What do you think?

---

### Post by brian_p on 2019-04-03
> **ajm83 said:**
> 
There are three bugs here IMO.

1.  Non-operative printer, as discussed.

Ok.
> 2.  Non-operative printer not appearing in the Printers control panel therefore unable to be disabled or inspected by a regular computer user who is unfamiliar with the command line.

Not a bug. The Printers control panel shows only locally installed print queues. There will be a PPD in */etc/cups/ppd* for them and Firefox will display the local queues. Discovery of IPP printers on the network by Firefox does not use CUPS, so there is no PPD and hence no local queue.

> 3.  The same printer appearing twice in the first place. The system should recognise that this is the same printer and show only the best method of connecting to it.

There is actually only one entry for the printer; the other entry is a queue. As many  different queue destinations (entries in a dialog) as needed can be set up. One for duplex printing, one for single-sided printing etc. If you do not want to see a destination, remove it (*lpadmin -x destination*) and/or purge cups-browsed from the system

---

### Post by ajm83 on 2019-04-03
> **brian_p said:**
> Ok.


Not a bug. The Printers control panel shows only locally installed print queues. There will be a PPD in */etc/cups/ppd*  for them and Firefox will display the local queues. Discovery of IPP  printers on the network by Firefox does not use CUPS, so there is no PPD  and hence no local queue.




Hmmm. Not sure I agree with that.  It may be 'not a bug' as in 'it works  as designed' but then IMO the design ought to tie all this in together.

Let me put it this way - if a printer is appearing in the print window  of a GUI application, it should be manageable in the GUI control  panel. As a user I don't really care how it works behind the scenes or  how it was auto-discovered. I shouldn't even need to know the terms  CUPS, Avahi, and so on to be able to achieve what I would consider to be  very basic administration of the computer. 

The control panel itself even has a tick-box to hide and show  'Discovered Printers' ... ticking/unticking it makes no difference  though. So presumably that is only for printers discovered in The Right  Way.


[IMG]https://i.imgur.com/BlsMQkr.png[/IMG]

> **brian_p said:**
> There is actually only one entry for the  printer; the other entry is a  queue. As many  different queue  destinations (entries in a dialog) as  needed can be set up. One for  duplex printing, one for single-sided  printing etc. If you do not want  to see a destination, remove it (*lpadmin -x destination*) and/or purge cups-browsed from the system

Okay, that makes sense, thanks for the tip.

---

### Post by brian_p on 2019-04-03
> **ajm83 said:**
> Hmmm. Not sure I agree with that.  It may be 'not a bug' as in 'it works  as designed' but then IMO the design ought to tie all this in together.

You can only manage a printer or a print server if you have local control of it; that is, you need a local queue to be set up. system-config-printer is one utility to do this; cups-browsed is another which does it automatically for you. The design enables you to get what *you* want and has been central to CUPS since its inception. s-c-p shows only local queues, as does the CUPS web interface. If you see a remote CUPS server or printer as having a printer service which could be useful to you, you add it as a local queue.

> Let me put it this way - if a printer is appearing in the print window  of a GUI application, it should be manageable in the GUI control  panel. As a user I don't really care how it works behind the scenes or  how it was auto-discovered. I shouldn't even need to know the terms  CUPS, Avahi, and so on to be able to achieve what I would consider to be  very basic administration of the computer.

Print dialogs get their entries for remote printers in different ways. LibreOffice uses CUPS, Firefox doesn't. IMO, it would be better and less confusing for users it the two were aligned. Don't forget that print dialogs construct their entries independently of a user. If he wants to manage what is shown, he needs to control it via a local queue. I gave you an example of that a couple of posts back. In the interests of user friendliness, it shouldn't need to be done.

I can see where you are coming from, but think on. Dispay of destinations and management of them are not the same. (However, the non-working entry in Firefox, which has been about for years, is a pain).

Now look have a read of

[https://wiki.debian.org/DriverlessPrinting#CUPS_2.2.4_and_Driverless_Printing](https://wiki.debian.org/DriverlessPrinting#CUPS_2.2.4_and_Driverless_Printing)

and explore how this is used by LibreOffice.

>  The control panel itself even has a tick-box to hide and show  'Discovered Printers' ... ticking/unticking it makes no difference  though. So presumably that is only for printers discovered in The Right  Way.

I've no idea. The option doesn't do anything for me.

---

