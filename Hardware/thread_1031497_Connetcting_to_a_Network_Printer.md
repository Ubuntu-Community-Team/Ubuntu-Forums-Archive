---
title: "Connetcting to a Network Printer"
date: 2009-01-05
forum: Hardware
---

### Post by akm3 on 2009-01-05
Hi everybody,
I am trying to connect my Desktop to one of Network Printers in a Network.
I can do it in Windows like this:
> 
Type **\\phoebe.ece.gatech.edu** in address bar
Type Username/Password in the window that appears
You will see a list of available Printers, choose the one you want(say, I choose csiplablpr)

I have tried to do this in Ubuntu under **System->Administration->Printing->New->LPD/LPR Host or Printer**
But I cannot access to a list of printers, plus I'm never asked for a username/password.
Can anybody who has a previous experience on connecting to a network printer on Ubuntu help me?

Thanks.

PS: Here is a reply, I got from our network operator, when I told her about this problem:
> 
We don't support printing from personal UNIX computers. It can still be
done by setting up an LPR connection inside CUPS on your distro to the
printer (e.g., server: phoebe.ece.gatech.edu, queue: csiplablpr), but
you'll have to figure out how to do it on your own. ;)

Try searching the Ubuntu Forums:
 [http://ubuntuforums.org/](http://ubuntuforums.org/)


3nj0iZ! -km


---

### Post by fgh2 on 2010-02-16
Here is how I installed mine. I don't know if it is the best way:

System -> Administration -> Printing
"New" button
choose "network printer" and then "Windows Printer via SAMBA"
"browse" button
Find your lab's printer there. For example I knew that on a Windows system the address was "ece-prnsrv1/PhotonicsLP". Also in "Printers and faxes" you can right-click on your printer and look at addresses under security tab to get some idea where to look for the address. The address I found for my printer in Ubuntu was "GT-COE/ECE-PRNSRV1/PhotonicsLP". 
If you are asked to enter username and password to access any folder, just use "ad\[your GT username]" and your GT account password. You can enter your username and password as above under "set authentication details now".

The rest is pretty straightforward.

---

### Post by fgh2 on 2010-02-16
> **fgh2 said:**
> Here is how I installed mine. I don't know if it is the best way:

System -> Administration -> Printing
"New" button
choose "network printer" and then "Windows Printer via SAMBA"
"browse" button
Find your lab's printer there. For example I knew that on a Windows system the address was "ece-prnsrv1/PhotonicsLP". Also in "Printers and faxes" you can right-click on your printer and look at addresses under security tab to get some idea where to look for the address. The address I found for my printer in Ubuntu was "GT-COE/ECE-PRNSRV1/PhotonicsLP". 
If you are asked to enter username and password to access any folder, just use "ad\[your GT username]" and your GT account password. You can enter your username and password as above under "set authentication details now".

The rest is pretty straightforward.


or equally after getting to  "Windows Printer via SAMBA" you can enter "phoebe.ece.gatech.edu/ece-prnsrv1/PhotonicsLP" in front of "smb://", to access to the above mentioned printer.

---

