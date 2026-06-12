---
title: "Epson Workforce 600 and the shared memory card"
date: 2009-10-08
forum: Hardware
---

### Post by gradysghost on 2009-10-08
I have an Epson Workforce 600 printer which connects to my wireless network in infrastructure mode.  Ubuntu 9.04 Jaunty picks it up and installs the drivers just fine.  That's not a problem at all.  The printer prints perfectly.

But the printer has a function where a memory card in the slot on the printer gets its contents shared out across the network.  My wife's Windows computer has no problems connecting to it.  I reserved the IP for the printer on the network as 192.168.0.199, the printer retains that just fine as it should, and my wife only needs to type

```
//192.168.0.199
```

in Windows to gain access.  However, when I try to connect to the printer via Nautilus using

```
smb://192.168.0.199
```

it tells me it can't find that network location.  I can ping the printer.  I can print to it.  But I can't seem to mount the share used for the memory card.  I don't know what protocol it's using.

I'm about to go try using CIFS on the command line, but I believe it will probably fail as well.  I'm just hoping it gives a better error message or something, not that CIFS has been known to do that...

Any ideas?  For what it's worth, I also cannot seem to find the scanner wirelessly through XSane.  But that's probably another matter entirely.

Also, I have a workaround for now (RDP to wife's box, download files to her computer, mount her HDD to my PC, download files to here), so this isn't a huge important thing that MUST get fixed now.  But I would like to not have to use Windows to use my printer to it's fullest, know what I mean?

Thanks in advance.

---

### Post by gradysghost on 2009-10-16
Just gonna bump this thread.  The problem still exists, though admittedly I have not tried Karmic yet.

---

### Post by mattgyver83 on 2009-12-18
Hey fellow, My setup is a little different so I dont know if this is gonna make any difference for you or not Believe it or not, your post is what got mine setup :X

Karmic 9.10
Epson WorkForce 610
------

Make sure your hitting smb://IP/<Share Name>/ it is hitting the SMB protocol.

On the 610 the share is called MEMORYCARD by default and I think you can change that.  If that doesnt work, read below.. .you might want to read below anyway..

Heres the best way to get it setup.

> 
Print a "Status Sheet" on the printer by following similar options;

Setup> Network Settings> Confirm Network Settings
Press the assigned button (start) to print the status sheet.

That should give you a little more info and you will see a seciton that says

> <MS Network(R)>      Enable
Host Name            EPSOND91F09 (this is probably different for you)
Workgroup Name       WORKGROUP
File Share Name      MEMORYCARD
File Sharing Mode    Full Access

[B][I]Note the Workgroup, File Share Name, and if the Sharing mode is not set as full access set that accordingly (unless you want read only)
[/I][/B]
> Setup> Network> File Sharing Setup> Network > Read/Write

> In Ubuntu go to Places> Network
Select File > Connect to server and use the following Settings;

Service Type: Windows Share
Server: IP address
Share: <File Share Name>
Folder: /
User Name: <Your Ubuntu login>
Domain: <Workgroup Name from Status Sheet>

(if you want you can add a bookmark for quicker access, or just add to your /etc/fstab)

Press Connect

If it prompts you for a password enter your linux users password.

After relentless searching... and talking to tech support who cowered at the first mention of linux, this is how i got it working.  Just another note, they say theres no way to manually change the Workgroup name, which is just stupid but whatever so I think thats why I cant 'Scan to PC' to any of my ubuntu machines, they arent listed but my Win machines are.  Epson blames the third-party drivers, I blame the workgroup name.

Hope this lengthy bit helps you some, or anyone for that matter.

---

### Post by SoFl W on 2010-06-01
mattgyver83,
Can you verify if the is / or \ ?
I am having no luck with this.

EDIT: 

I was able to get it to work.  I had to have at least one file on the SD card and on the original print out of my setup there were several "NONE" fields.  Once I made corrections and scanned to a PDF on the memory card everything worked.

---

