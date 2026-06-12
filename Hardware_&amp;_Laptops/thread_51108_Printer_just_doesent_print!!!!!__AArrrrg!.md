---
title: "Printer just doesent print!!!!!  AArrrrg!"
date: 2005-07-22
forum: Hardware &amp; Laptops
---

### Post by ubuntuthinking on 2005-07-22
OK - Ive been at this for a few days and I'm really not thinking straight.  I have Ubunty Hoary on a centrino laptop.  I want to print to a HP932C connected via USB to an XP workstation in my home.  I use a Dlink wireless system.  

I have installed the correct .ppd file for the hp ...but when I send a test page to the printer it does not work.  Checking in localhost:631 shows the following"

Description: DeskJet-932C
Location:
Printer State: processing, accepting jobs.
"Unable to connect to SAMBA host, will retry in 60 seconds...ERROR: Connection failed with error NT_STATUS_ACCESS_DENIED"
Device URI: smb://DELL/HP932C

Someone please save my sanity!!!! ](*,)  ](*,)  ](*,)  ](*,)

---

### Post by ubuntuthinking on 2005-07-22
BUMP - sorry I'm really frustrated :?  :?


This is what I see:

# sudo /usr/bin/smbclient -L DELL
Password:
Domain=[DELL] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
        IPC$            IPC       Remote IPC
        print$          Disk      Printer Drivers
        SharedDocs      Disk
        HP932C          Printer   HP DeskJet 930C/932C/935C
        Printer2        Printer   eFax 4.0
Domain=[DELL] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------

---

### Post by az on 2005-07-22
Do you have samba installed?  By default, Ubuntu can see other computers but cannot talk to them.  To do that, you have to install the samba package.

---

### Post by ubuntuthinking on 2005-07-22
THANKS FOR YOUR REPLY!!

Yes I did install Samba and I can see the Dell with MsHOME as the workgroup.   :|

---

### Post by ubuntuthinking on 2005-07-31
Fixed:
See "Cannot print to HP932C connected to XP box"

---

