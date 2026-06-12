---
title: "sharing a printer"
date: 2008-10-18
forum: General Help
---

### Post by laplace/d on 2008-10-18
i'm using xubuntu on one computer and ubuntu on the other one. i wanna share the printer and i have no clue!
help plz!

---

### Post by plucky on 2008-10-18
> **laplace/d said:**
> i'm using xubuntu on one computer and ubuntu on the other one. i wanna share the printer and i have no clue!
help plz!

Which computer is the printer connected to?

Go to **System > administration > Printing > Server Settings** on the computer with the printer attached and tick the boxes that says "share published printers connected to this system".

You should then go to the other system and tick the box that says "show printers shared by other systems".Cups should then try to find your shared printer.

To access the CUPS interface on the system the printer is attached to,open your Browser and input this into the address bar```
http://localhost:631/admin/
``` will allow you to troubleshoot any problems.


Good Luck

---

### Post by flattop1 on 2009-01-21
I've got the same problem..

I have my printer attached to the Ubuntu Desktop computer and I want to print from my laptop which has xubuntu on it...

Everything seems to be going well ..I did everything according to the above instructions....and I can see the printer from the xubuntu rig but when I click print ..nothing happens.
I get this error...

[IMG]http://i58.photobucket.com/albums/g251/keogh557/Non%20Skate%20photos/printer.png[/IMG]

The printer is connected and working  in the other room...I dont get it how xubuntu automatically detects the printer with the ip settings etc and cant connect?

Any help would be greatly appreciated.

---

### Post by flattop1 on 2009-01-23
bump

---

### Post by flattop1 on 2009-01-26
> **flattop1 said:**
> I've got the same problem..

I have my printer attached to the Ubuntu Desktop computer and I want to print from my laptop which has xubuntu on it...

Everything seems to be going well ..I did everything according to the above instructions....and I can see the printer from the xubuntu rig but when I click print ..nothing happens.
I get this error...

[IMG]http://i58.photobucket.com/albums/g251/keogh557/Non%20Skate%20photos/printer.png[/IMG]

The printer is connected and working  in the other room...I dont get it how xubuntu automatically detects the printer with the ip settings etc and cant connect?

Any help would be greatly appreciated.

Is there any chance of an answer to this printer problem or should I start a new thread of my own?

---

### Post by plucky on 2009-01-27
> Is there any chance of an answer to this printer problem or should I start a new thread of my own? 


That error look like a network communication problem between the two computers.Can you ping the IP address of the printer ```
ping -C 5 192.168.2.5
```

What is the model number of the printer,and has the correct driver been installed on the laptop.

Not really sure with HP printers as my printer is a Brother,but from what I have read,you should make sure HPLIP is installed from Synaptic.

Open Firefox and input into the address bar ```
http://localhost:631/admin/
``` and have a look at the error logs for a clue why CUPS isn't communicating between the two computers.


Good Luck.

---

### Post by flattop1 on 2009-01-27
> **plucky said:**
> That error look like a network communication problem between the two computers.Can you ping the IP address of the printer ```
ping -C 5 192.168.2.5
```

What is the model number of the printer,and has the correct driver been installed on the laptop.

Not really sure with HP printers as my printer is a Brother,but from what I have read,you should make sure HPLIP is installed from Synaptic.

Open Firefox and input into the address bar ```
http://localhost:631/admin/
``` and have a look at the error logs for a clue why CUPS isn't communicating between the two computers.


Good Luck.
Hey Thanks for the reply..I'll try that tomorrow..Its a bit late tonight..

My printer is a PSC 1210v HP all in one

---

