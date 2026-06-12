---
title: "special character encoding in filenames and directories"
date: 2008-08-08
forum: General Help
---

### Post by kuboaa on 2008-08-08
Music files and directories containing special characters encoded in windows are not accessible to linux apps, for example Rhapsody, Amarok, etc. Files with special chars ripped under linux work fine. 

The files are mounted on a remote Samba share (on a Linkstation running Freelink, if it matters).

ls and Nautilus show special characters as an underscore, for example

bill@ubuntu:/music/Paco de Lucía$ ls Luzia
01 - R_o Del La Miel (Buler_a).flac  05 - Luzia (Siguiriya).flac
02 - La Villa Vieja (Sole_).flac     06 - Manteca Color_ (Rumba).flac
03 - Calle Munici_n (Alegr_a).flac   07 -  El Chorruelo (Buler_a).flac
04 - Me Regal_ (Tangos).flac         08 - Camar_n (Ronde_a).flac

If I manually rename the files and directories with Nautilus, everything is fine, but I have a lot of music and it is tedious. Command line doesn't work for renaming:

cp: cannot open `01 - R_o Del La Miel (Buler_a).flac' for reading: No such file or directory

Do I need to specify encoding in the mount command? Or is the some locale or encoding configuration that needs to be done on my local machine and/or the remote box?

---

### Post by cariboo on 2008-08-08
There are several batch renaming programs, that you can use to rename your files properly, This is probably not waht you really want, but Microsoft, is pretty sloppy about file names and this leads to problems with other operating systems. Go to System-->Administration--Synaptic Package Manager and search for **batch rename** you should be able to find a program that suits your needs.

Jim

---

### Post by kuboaa on 2008-08-08
Unfortunately, the batch renaming programs seem to be powerless against the mystery underscore character. The only way I have been successful at renaming the files is manually through Nautilus.

---

