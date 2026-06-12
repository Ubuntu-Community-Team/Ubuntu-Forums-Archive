---
title: "[SOLVED] VirtualBox and Shared Folders"
date: 2008-11-14
forum: General Help
---

### Post by Mardoct909 on 2008-11-14
Despite all my best efforts, I've been unable to set up a shared folder between my Intrepid host and XP guest. Any help would be much appreciated.

---

### Post by evildragon2 on 2008-11-14
Might this be any help?

[http://www.ubuntugeek.com/tools-to-access-linux-partitions-from-windows.html]("http://www.ubuntugeek.com/tools-to-access-linux-partitions-from-windows.html")

---

### Post by Mardoct909 on 2008-11-14
Unfortunately no. The guest OS is completely blind to the host, so it I can't access / like a second hard drive.

---

### Post by jimmy the saint on 2008-11-14
Do you have guest additions installed?  if you do it is simply a matter of creating a folder in you home directory, adding it in the VBox manager as a shared folder, and then mapping as a network drive in XP.  You could add it as a network place, but there is a known bug that makes this act painfully slow.

Edit:  When you map the drive, it will be in the format

\\VBOXSVR\vboxshare

where \\VBOXSRV\ is always the same and "vboxshare" is just the name of the folder.  You don't need to give the path to the folder because Virtualbox will already have that info.  You have to add the folder to virtualbox manager BEFORE you try to map it in XP.

---

### Post by Mardoct909 on 2008-11-14
Ah, there we go. Sort of. If you try to auto-download the file, it's null. You have to download it manually and place it in the correct folder yourself.

---

### Post by WWSmith36 on 2008-11-14
The will need the guest additions to be installed in able to use shared folders.

To install guest additions, open your virtual machine and go to the menu Device-> Guest Additions.

After installation you will need to reboot your machine.  Make sure you specify you shared folders in your machine settings.  Also you will have to enable them will at the command prompt.

---

### Post by jimmy the saint on 2008-11-14
i don't follow.  The CLI is never required to enable shared folders.  You just add them through the manager and map them in the XP guest as networked drives.  No CLI neccessary.

I love the virus detector sig -- very funny because its true!

---

### Post by WWSmith36 on 2008-11-14
I mapped my 2 shared drives named (MEDIA and STORAGE) from the CLI in WINXP with these commands

net use M: \\vboxsvr\MEDIA
net use S: \\vboxsvr\STORAGE

---

### Post by Mardoct909 on 2008-11-14
Ugg. So in order to get the guest features, one needs to manually retrieve the file, rename it, move it as root to VirtualBox's /usr folder and then go through an annoying installation... But it works.

Thanks.

---

### Post by jimmy the saint on 2008-11-15
I think I understand your dilema, but I am not sure.  If I am right, you are creating the shared directory in the the virtualbox /usr folder.  You can just make a folder in your home directory and designate that as a shared folder in the virtualbox manager.  Then you don't need to worry about permissions.  My share is /home/me/vboxshare.  when I map the network drive it is mapped as 
\\VBOXSVR\vboxshare.

---

### Post by luckydeveloper on 2008-12-03
people, i have the same problem, i am not able to set the shared folder in the virtualmachine settings, i use windows guest on ubuntu host. in the shared folder settings, when i choose a folder, the 'ok' button in that 'choose folder' window is not getting enabled for me to click it. i have installed the windows guest additions. 

please help...

---

