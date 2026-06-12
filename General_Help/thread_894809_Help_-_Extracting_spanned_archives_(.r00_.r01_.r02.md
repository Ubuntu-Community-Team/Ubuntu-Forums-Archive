---
title: "Help - Extracting spanned archives (.r00 .r01 .r02) through samba share"
date: 2008-08-19
forum: General Help
---

### Post by Rafiki123 on 2008-08-19
Hello,

Recently I have been getting problems extracting Spanned archives (.r00 .r01 .r02) from my ubuntu server through a samba share.  When I right click on the actual .rar file it does not say "extract here" even though the icon associated with the .rar file is correct. When I click to open the file the archive manager opens up but there is nothing displayed.  I can copy the files to the computer and extract them just fine but for some reason it won't do it over the samba share.  I want to be able to extract the file from my main computer.  Can anyone help me with this?

Thanks

---

### Post by master.swarky on 2008-08-19
Well, maybe some problems with permissions? Check that you have the rights to write into your share folder.

---

### Post by Rafiki123 on 2008-08-19
when I go into the samba web administration i have read and write permissions. is that what you meant?

---

### Post by master.swarky on 2008-08-19
Well, yes. Anyway, are you able to create new files in your share folder? And, which program are you using for unpacking you rar archives?

---

### Post by Rafiki123 on 2008-08-19
yes, I am able to create files in the share folder.  Im using unrar (non-free version). I read a bit about unrar'ing' archives and there was some discussion about using the free version and the non-free version but I think that was for unraring spanned archives in general.

is there a better way to share files from a linux server to a linux computer over a  network?

---

### Post by Rafiki123 on 2008-08-19
Another thing i just noticed is that when I go to 'Network' in places theres the samba share and then theres 'windows network'.  which when I click on it does not let me view the other computers on my network. Am I not in my the proper network? Im pretty sure that the server is in the right network because when I go to the other windows computer it shows up in the wondows network.  From this command I think im in the right workgroup:

tburke2008@rafiki:~$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.102   RAFIKI         [RAFIKI] [Unix] [Samba 3.0.24]
192.168.1.103   NEBULA        +[RAFIKI] [Unix] [Samba 3.0.22]

---

### Post by master.swarky on 2008-08-20
> **Rafiki123 said:**
> yes, I am able to create files in the share folder.  Im using unrar (non-free version). I read a bit about unrar'ing' archives and there was some discussion about using the free version and the non-free version but I think that was for unraring spanned archives in general.

is there a better way to share files from a linux server to a linux computer over a  network?

I can suggest using the official WinRAR for Windows. It runs just perfectly with Wine from the official repo, and it is able to do much more things than the unrar-nonfree. Moreover, it has a GUI ;)

And about the methods: if you have a linux server and a linux computer you can try NFS (network file system).

---

### Post by Rafiki123 on 2008-08-20
Thanks. I looked at Wine and winrar in wine but just looked.  I think I'll try to get into using it.  

Do you have any good links for a newbie network guide for the sort of thing im looking for here?

---

