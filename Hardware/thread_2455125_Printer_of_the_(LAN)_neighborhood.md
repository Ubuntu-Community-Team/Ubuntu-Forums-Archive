---
title: "Printer of the (LAN?) neighborhood"
date: 2020-12-12
forum: Hardware
---

### Post by UBUminJ on 2020-12-12
Today, Ubuntu suddenly tells me that it has added a printer.
However, I don't have a printer. 
I am connected to the WWW by a LAN. No idea whose printer it is.

How can I force Ubuntu not to add printers?
If I click on remove this printer, 5 seconds later it has added it again.
What to do?

Thank you.

---

### Post by QIII on 2020-12-12
Is the printer actually being added, or is it being shown as available?  Are you on a wired network or WiFi?  If WiFi, do others share the router?  Do you live in an apartment or dormitory, perhaps?

---

### Post by UBUminJ on 2020-12-13
@QIII
My Ubuntu-PC is connected by wire to an apartment LAN - over 100 parties can connect to the WWW via this LAN.

Since this afternoon, I get the message "Printer added Canon_TS3300_Series". If I check settings, it says "Canon_TS3300_Series Ready".
I tried to print and I could, apparently. No error message came back.

If I delete the printer, a few seconds later, it is back again with the message "Printer added Canon_TS3300_Series".

---

### Post by UBUminJ on 2020-12-13
[https://askubuntu.com/questions/81116/how-do-i-remove-a-printer](https://askubuntu.com/questions/81116/how-do-i-remove-a-printer)
> sudo lpadmin -x printername
Doesn't work - it came back immediately.

[https://askubuntu.com/questions/732594/how-do-i-permanently-delete-networked-printers](https://askubuntu.com/questions/732594/how-do-i-permanently-delete-networked-printers)
> Login to [https://localhost:631/printers/](https://localhost:631/printers/) and delete there. Fast and simple.
Doesn't work - it came back immediately.

Probably, this is the solution: [https://askubuntu.com/questions/345083/how-do-i-disable-automatic-remote-printer-installation](https://askubuntu.com/questions/345083/how-do-i-disable-automatic-remote-printer-installation)
Not yet tested.

---

### Post by Morbius1 on 2020-12-13
The only thing I can think of that does what you describe is cups-browsed AND since you have no local networked printers of your own I would "mask" the process so that it doesn't run:
```
sudo systemctl mask cups-browsed
```
[COLOR=#ff0000]You will need to reboot your ubuntu box.[/COLOR]

If in the future you need to use it again unmask it:
```
sudo systemctl unmask cups-browsed
```

---

### Post by QIII on 2020-12-13
Were I you, I would be worried about more pressing issues than just that you are connecting to a printer somewhere.  If your machine detects and can connect to a printer in someone else's apartment, it is entirely possible that someone else in your building can detect *you* and *your activity*.  What are you doing to protect yourself?

---

### Post by TheFu on 2020-12-13
> **QIII said:**
> Were I you, I would be worried about more pressing issues than just that you are connecting to a printer somewhere.  If your machine detects and can connect to a printer in someone else's apartment, it is entirely possible that someone else in your building can detect *you* and *your activity*.  What are you doing to protect yourself?

^^^^^^^^^^^^^^^^^^^
THIS!!!!

Get a router asap. Put it between the wall ethernet and all your computers.

---

