---
title: "external 500gig NTFS"
date: 2008-04-22
forum: Hardware
---

### Post by sidcypher on 2008-04-22
To start at the beginning, I am a truck driver, so my laptop and external are running off a inverter...

I started up the truck (which low powers the inverter and turns it off).  I came back to find a 40gig folder on my external now missing...kinda

I doesn't show up in nautilus but it does under the terminal. Black background with red letter..

Thinking something was writing to that folder when I started truck, as I HAD my downloads set to auto copy when complete.

I am somewhat of a linux newbie as I have only been running 7.10 since November.  So I have noticed that different files have different colors...but I don't know what the default meanings of them are...I assume since I can't read that directory that black with red letters is bad..

This is what it displays from terminal (and azureus for that matter).
```
james@Satellite:/media/500gig$ cd Torrents
bash: cd: Torrents: Input/output error
james@Satellite:/media/500gig$ 
```

Saw in another thread that fsck doesn't support NTFS. Which is fine cause I don't really know how to use it.

Is there anyway I can fix this? Or am I better off waiting until I am home and have access to a XP machine to run chkdsk or scandisk?

If you need me to post any more info just ask.

Thanks
Cypher

---

### Post by TenPlus1 on 2008-04-22
Check out Synaptic Package Manager in the Admin menu and do a search for NTFSutils...  These are a set of utilities designed to manage NTFS partitions and I dare to helps fix them also...  ou can look at the Files Installed tab to see what it's putting on, what commands are there and in Terminal you can type MAN <progname> for help...

---

### Post by sidcypher on 2008-04-22
didn't find ntfsutils but did find ntfsprogs...so i installed that
also grabbed testdisk since it said it does sector scans...

Try using external on my XP virtual machine (which used to work).
It shows up in Device manager but has "can't start device" error.
If it is mounted in ubuntu and mapped as network drive on virtual box i can browse the files but that one folder is still missing, and it won't let me run scandisk or anything else on network drives.

Will post results of testdisk and see what I need to do with the ntfsprogs package.

---

### Post by sidcypher on 2008-04-22
Ok, testdisk ran..didn't find anything wrong other then it kept telling me my drive was too small less than 1000gig...

I have tried the ntfs tools...can't figure them out..So I will just wait and see if anyone else has suggestions.

Thanks!

---

### Post by sidcypher on 2008-04-22
Ok, testdisk ran..didn't find anything wrong other then it kept telling me my drive was too small less than 1000gig...

I have tried the ntfs tools...can't figure them out..So I will just wait and see if anyone else has suggestions.

Thanks!

---

