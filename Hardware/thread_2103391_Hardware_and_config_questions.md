---
title: "Hardware and config questions"
date: 2013-01-10
forum: Hardware
---

### Post by HalinQuincy on 2013-01-10
[SIZE=3][FONT=Calibri]So, I started down this path because the 2 Maxtor NAS I have are starting to get full and are just dog slow and not reasonable to back up to. I have an HTPC with everything applicable stored there so I don’t need streaming capabilities on the network from the server.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]I think I've got the Server rig set up. Hardware is Intel P4 3.06 Ghz 1mb cache HT 4gb of ram. I have 4 W.D. RE4 1TB drives on a Sil 3124 PCI raid card. (if this is a bad choice or there is a better option please let me know). There is a PCIe v1x1 slot and a PCIe x16 slot (the docs don’t state whether it is v1 or 2 or if it only works for video) that are open. I’ve run into a couple of boards that would only support video cards. I'd only want to spend the $$ for another card if that is in fact the bottleneck.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]I have the Server installed on a 250GB W.D. Black drive.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]I read somewhere that It would be better to let Ubuntu do the raid work rather than configure the array(s) on the card. True? Comments please. [/FONT][/SIZE]
[SIZE=3][FONT=Calibri]I have in mind to do 0+1 raid. I understand that if I use the card to create the array, I may be able to just replace the card if it goes bad w/o corrupting the arrays themselves. Would this be true if I created the arrays in Ubuntu and lost the card or the drive that Ubuntu was installed on or if the mboard failed?[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]I suspect that 1.5 TB is all I will need for some time. But, if I should need to expand, (Correct me if I've assumed wrongly) I would need to break the raid 0 on one pair of drives, add the extra drive, format and move the data from the mirrored pair to the new trifecta and then add a drive to the mirrored set. Rebuild the mirror. Is there an easier way? Maybe backup to a 2 or 3 TB drive and restore from it? I’d kinda like to have an offline backup of everything anyway.[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]I checked the file server and samba server boxes at install, but have not started any configuration.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]I read that if one might end up wanting LAMP or other server services, best to include in the original install. Adding later creates a lot of configuration work that is automated on the original install. True?[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Should I wipe the install and start over? Is there much additional overhead if I install but don’t use those services? [/FONT][/SIZE]
[SIZE=3][FONT=Calibri]I've added the Ubuntu Desktop so I can feel a little warm and fuzzy while I learn Linux command line. And yes, I've read there isn't much server setup or admin that can be done from the GUI. I may try and remove the desktop later.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]I've worked a little with windows command line and very little with linux command line. I ran across a link to a basic (Ubuntu) command line tutorial but of course I failed to bookmark it. Anybody point me in the right direction?[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]I have a gigabit network. I have assumed that adding an additional gb net card wouldn’t give me better throughput (that’s assuming I could figure out how to configure the 2 cards).[/FONT][/SIZE]
 
[FONT=Calibri][SIZE=3]I have set the static IP according to the server directions but got stopped at:[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]“You need to setup manually DNS servers in resolv.conf file when you are not using DHCP.[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]sudo vi /etc/resolv.conf[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]You need to add look something like this[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]search domain.com[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]nameserver xxx.xxx.xxx.xxx”[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]When I open resolv.conf with the above command it says that I can’t save the edit, that it is set to auto (not the exact words). So right now I don’t have any internet connection but can access everything on the local network, probably because I have everything on the local net using netbios. I've looked at the network app in Desktop settings but the options button is grayed out, not active. Anyway, I could use some direction here since the official server docs aren’t working for me.[/FONT][/SIZE]

---

