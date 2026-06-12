---
title: "Installing HP Laser Jet M1005 MFP"
date: 2019-06-03
forum: Hardware
---

### Post by parshwa23 on 2019-06-03
[SIZE=3]Hi,

I have to install "HP Laser Jet M1005 MFP" (printer+scanner) in Ubuntu LTS (bionic). Can one give me step by step instructions for this so that scanner as well as printer starts working.

Thx.

PM[/SIZE]

---

### Post by Autodave on 2019-06-04
Go to software center and install *hplip.*  Connect printer to PC and turn on printer.  'buntu should do the rest.

---

### Post by rbmorse on 2019-06-04
Your device is what we used to call a "winprinter" because it uses a stripped-down driver model that depends on the presence of the Microsoft Windows operating system's GDI.  

Using it under Linux requires the installation of a proprietary binary software blob that supplies the functions normally provided by the Windows GDI.  

See this article before attempting to use this device:[URL="https://developers.hp.com/hp-linux-imaging-and-printing/binary_plugin.html"]

https://developers.hp.com/hp-linux-imaging-and-printing/binary_plugin.html[/URL]

---

### Post by parshwa23 on 2019-06-16
[SIZE=3]Printer is working. But how can I install scanner which is in the same machine. Thx.[/SIZE]

---

### Post by Artim on 2019-06-16
Look for "Add new Hardware" or something like that in your Settings or Main menu, find Scanner and select your printer/copier/scanner from the list that pops up.  Adding **hplip** software will definitely help!  Ubuntu may just automagically detect it (maybe after a reboot, probably not).

---

### Post by parshwa23 on 2019-06-17
[SIZE=3]I looked up and found Device -> Printers in Settings Menu but only printer options are visible and no where scanner or related settings are getting depicted....I guess I have to do something extra.....I don't know....!![/SIZE]

---

### Post by Artim on 2019-06-17
Does Ubuntu use SimpleScan (I use Xubuntu)?  I guess you have tried scanning a picture or document and got an error message, right?  Your scanner may already be recognized and installed, especially if you have added "hplip" to your Ubuntu.

---

### Post by parshwa23 on 2019-06-17
[SIZE=3]Actually I am using 'Ubuntu 18.04.2 LTS' and I searched 'SimpleScan' in software center, no such App is coming in results. May be scanner might have installed (which I don't know if it is installed), but how do I even get an error message? As when I try to scan a paper, from where do I give the scanning command?[/SIZE]

---

### Post by parshwa23 on 2019-06-17
[SIZE=3]Finally with lots of search, I got the link: [https://www.youtube.com/watch?v=NBeJUMkef]("https://www.youtube.com/watch?v=NBeJUMkef_A")_A which works![/SIZE]

---

