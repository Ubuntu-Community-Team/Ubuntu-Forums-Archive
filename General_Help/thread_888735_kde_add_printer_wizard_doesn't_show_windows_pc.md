---
title: "kde add printer wizard doesn't show windows pc"
date: 2008-08-13
forum: General Help
---

### Post by Jaybird on 2008-08-13
I'm running kubuntu connected to a home network with a shared printer attached to a windows xp machine.  As I go through the kde add printer wizard, add >> add class/printer >> smb shard printer (windows) >> guest account >> scan, it shows the network and beneath it a linux machine that is connected to the network, but no windows machines.  There are in fact two windows machines on the network.  The strangest thing is I had already added this printer previously, but because I had to re-install XP on the machine the printer is attached to, I decided to re-add the printer.  Now this.  I can see folders on this machine using konquerer, dolphin, and smb4k.  I can even see the printer using smb4k.  Any help here?

---

### Post by cmnorton on 2008-08-13
It would be helpful to know what your network settings are and how you are running the Print Wizard. I just ran the KDE add printer wizard and by selecting an SMB printer, I was able to scan to find

1) My domain name and under that heading was

2) Our domain controller, and under that was a list of our printers.

But our domain controller is a server (Microsoft Server 2003); otherwise it could not be a domain controller. That may be where your problem lies.

If you are sharing out a printer from a Windows workstation (non-server) installation, it gets a little more complicated. 

You will need to have a fixed ip address, which you can accomplish by giving the windows system a permanent reservation. Most DHCP servers -- probably part of your router -- will allow to to assign a permananet DHCP address to a client.

Then with the printer shared on the windows side, you can build the connection to it from the Linux side using smbclient.

My connection string is:

smb://our-domain/MYWORKSTATION/lp

where our-domain name is our domain, MYWORKSTATION is my workstation's netbios name in caps, and lp is the shared printer.

---

### Post by Jaybird on 2008-08-13
That is how it is supposed to work, but for me after the scan, the workgroup name is there, but no windows machines.  I have another linux machine on this network with ubuntu installed and it found and added the printer just fine.

---

### Post by Jaybird on 2008-08-14
Must be something wrong with the wizard.  I rebooted using the kubuntu live cd and was able to add the printer.

---

