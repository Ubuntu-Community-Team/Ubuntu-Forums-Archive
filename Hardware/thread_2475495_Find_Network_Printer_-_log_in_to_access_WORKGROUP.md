---
title: "Find Network Printer - log in to access WORKGROUP?"
date: 2022-05-29
forum: Hardware
---

### Post by pkoukoulis-r on 2022-05-29
I am attempting to add a network printer.
I select "Settings->Printers->Additional Printer Settings->Add Printer->Find Network Printer->Find", but then the following dialog appears:

Username:  xxx
Domain: WORKGROUP
Password:

My Ubuntu password is not accepted and it does not proceed to attempt to find a network printer.

How do I remove this dialog box? How to remove this "WORKGROUP" ? I am unsure where it originates from ?

I removed wine and samba, using "apt --purge", thinking that perhaps it was related to one of these two. 
Rebooted in the hope that it might rid the dialog box, but it hasn't

Any ideas  ?

Thanks

---

### Post by TheFu on 2022-05-29
Adding a printer has become really easy for supported printers since about 2016.  On all my new installs, the printer is basically preconfigured and drivers installed just by 
a) having avahi running
b) using system-config-printer tool

Without Avahi, using system-config-printer I've had to set the printer with a static IP and manually selected the IPP protocol, then the vendor and model of printer.  That is it.

Printers don't require authentication unless you have a Windows box controlling access - i.e. the printer isn't on the network, it is connected via USB to a Windows system.  If the printer is connected to a Linux system via USB, then CUPS can be configured to require authentication. I've not see that.

Just 1 thing to try ... leave the user, workgroup, password fields empty. Does that work?

BTW, is the vendor and model of printer a secret?

---

### Post by pkoukoulis-r on 2022-05-29
Hi, thanks for reply. Printer is a new HP Smart Tank 7605. No USB cable, only network connected. 
I had an old HP 8500 printer WiFi connected, which worked well for over 12 years, but alas, I could no longer find spare parts for the inconsistently working printer, so reluctantly purchased a new one.

I've attempted to connect by directly entering the ip shown on the printers LED screen, but it remains unconnected.

Dialog Box appears as:

[COLOR=#000000]Username: xxx[/COLOR]
[COLOR=#000000]Domain: WORKGROUP[/COLOR]
[COLOR=#000000]Password:

[/COLOR]Cancel OK

If I select OK with a username and ubuntu password, then a further message appears "Not authorised, the password may be incorrect"
If I select OK without a username/password, then same message as previous appears.
If I select Cancel with/without username, then message appears "No printer was found at that address"

I have no windows device on the network, that is what is so baffling about the dialog box appearing.

---

