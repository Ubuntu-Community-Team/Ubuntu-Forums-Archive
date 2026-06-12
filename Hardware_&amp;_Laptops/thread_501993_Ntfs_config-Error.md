---
title: "Ntfs config-Error"
date: 2007-07-16
forum: Hardware &amp; Laptops
---

### Post by bigbrovar on 2007-07-16
Please am very new to Linux i have 3 ntsf drives on my system when i tried mounting them two drives mount everything was successfully and i was able to enable read and wirte support.however when i tried the same for the 3rd drive i get an error message "an error occured while trying to configure"please is there any thing i can do to fix this..the particular drive is where all my backups are and i really nead it to work..any help would be appreciated.THanks in advance

---

### Post by merlinus on 2007-07-16
You may want to check that drive for errors.

You can do it from a command line or Run in windows:

chkdsk <driveletter>: /f

-merlin

---

### Post by bigbrovar on 2007-07-16
am currently doing a disk check .if it doesnt work i intend to format the drive in windows then boot into ubuntu and try mounting it again i hope these wont lead to any problem..please advise me

---

### Post by dasan on 2007-07-16
R u using ntfs-3g for mounting the disk ?
If not try by installing tat..
go to synaptic packet manager and search for ntfs-3g

---

### Post by bigbrovar on 2007-07-16
> dasan  	R u using ntfs-3g for mounting the disk ?
If not try by installing tat..
go to synaptic packet manager and search for ntfs-3g

yes that is what am using i just booted into vista,formated the drive,checked for errors and bad sector, windows said there was no problem with the drive .i then booted ubuntu and tried mounting it with ntfs-config ..AGAIN THE SAME ERROR  message "A n error occured  while trying to configure /media/data.retry thnks.
  please what else can i do iam really going desperate can anybody help...please:(:(:(

---

### Post by bigbrovar on 2007-07-16
i finally got it resolved apparently one of my scripts was not properly written....a friend here in NIgera corrected it for me so Crisis averted...must had that it is very sad that i got only one help for my problem..b4 i came to be using Linux i was made to understand that things worked like magic and if ever there was a problem the community would help...there are many newbies out there who don't know their right from left..who have posted their problems here with nobody here to respond and offer help..this is against the spirit of ubuntu..many of them who are not that lucky to have a guru friend like i do end up their Linux adventure only to return to the evil empire..very sad.  i think the gurus in the house should do more to help newbies who are stranded in these amazing new world..so that with time these newbies can live their Ubuntu dream

---

