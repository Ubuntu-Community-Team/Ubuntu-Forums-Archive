---
title: "Translation (german)linux-technospeak -&gt; english/german needed!"
date: 2005-06-09
forum: Hardware &amp; Laptops
---

### Post by phen on 2005-06-09
Hello all!


all of a sudden, my laptop did not start X anymore. The errormessage was

could not open /var/log/Xorg.0.log

looking through the bootmessages, i recognized, that no service was able to open/write to its log file.

trying to write on my harddisk returned an I/O Error.

Now, thanks to mr. Knopper, i am checking with e2fsck. I am going to paste the e2fsck's output. Please explain what happend to my harddisk, and if it is a hardware error (because my guarantee is soon running out!)

Thank you very much!

best regards,

kai


```

knoppix@1[knoppix]$ sudo fsck.ext3 -c /dev/hda5
e2fsck 1.37 (21-Mar-2005)
Suche nach defekten Blöcken (Nur-Lesen-Modus):erledigt                     31
Durchgang 1: Prüfe Inodes, Blocks, und Größen
Inode 3064290 ist in Benutzung, aber hat dtime gesetzt.  Repariere<j>? ja

Inode 3064290 hat Imagic-Flag gesetzt.  Bereinige<j>? ja

Gelöscht Inode 3064295 hat "zero dtime".  Repariere<j>? ja

Inodes,  die Teile einer defekten Liste mit verwaisten Links waren.  Repariere<j>? ja

Inode 3064309 war Teil der orphaned Inode Liste.  REPARIERT.
Gelöscht Inode 3064313 hat "zero dtime".  Repariere<j>? ja

Inode 3064316 war Teil der orphaned Inode Liste.  REPARIERT.
Inode 3064317 war Teil der orphaned Inode Liste.  REPARIERT.
Inode 3064867 ist in Benutzung, aber hat dtime gesetzt.  Repariere<j>? ja

Inode 3064868 war Teil der orphaned Inode Liste.  REPARIERT.
Gelöscht Inode 3064870 hat "zero dtime".  Repariere<j>? ja

Inode 3064871 war Teil der orphaned Inode Liste.  REPARIERT.
Gelöscht Inode 3064879 hat "zero dtime".  Repariere<j>? ja

Inode 3064290 hat unzulässigen Block(s).  Bereinige<j>? ja

Nicht zulässig Block #1 (134515920) in Inode 3064290.  BEREINIGT.
Nicht zulässig Block #2 (134534112) in Inode 3064290.  BEREINIGT.
Nicht zulässig Block #-1 (3221225012) in Inode 3064290.  BEREINIGT.
Nicht zulässig Block #1036 (4294967295) in Inode 3064290.  BEREINIGT.
Nicht zulässig Block #1037 (4294967295) in Inode 3064290.  BEREINIGT.
Nicht zulässig Block #1038 (4294967295) in Inode 3064290.  BEREINIGT.
Nicht zulässig Block #1039 (4294967295) in Inode 3064290.  BEREINIGT.
Nicht zulässig Block #1040 (4294967295) in Inode 3064290.  BEREINIGT.
Nicht zulässig Block #1041 (4294967295) in Inode 3064290.  BEREINIGT.
Nicht zulässig Block #1042 (4294967295) in Inode 3064290.  BEREINIGT.
Nicht zulässig Block #1043 (4294967295) in Inode 3064290.  BEREINIGT.
Zu viele unzulässige Blocks in Inode 3064290.
Bereinige Inode<j>? ja

Inode 3064867 hat INDEX_FL flag gesetzt, ist aber kein Verzeichnis.
Bereinige HTree-Index<j>? ja

Inode 3064867, i_size ist 13835006962485801624, sollte sein 0.  Repariere<j>? ja

Inode 3064867, i_Blocks ist 3086842336, sollte sein 0.  Repariere<j>? ja

Inode 3064868, i_size ist 13835007512107024384, sollte sein 0.  Repariere<j>? ja

Inode 3064868, i_Blocks ist 134591136, sollte sein 0.  Repariere<j>? ja

Inode 3064289, i_size ist 577887299920986145, sollte sein 0.  Repariere<j>? ja

Inode 3064289, i_Blocks ist 1818850421, sollte sein 0.  Repariere<j>? ja

Beginne e2fsck neu ...


```

---

### Post by inmate on 2005-06-09
i'll do a quick translation, you'll have to figure the rest...

> 
knoppi@1[knoppix]$ sudo fsck.ext3 -c /dev/hda5 e2fsck 1.37 (21-Mar-2005)

whatever....

> 
Suche nach defekten Blöcken (Nur-Lesen-Modus):erledigt                     31

searching for defective blocks (read-only-mode):completed  31

> 
Durchgang 1: Prüfe Inodes, Blocks, und Größen

Pass 1: testing Inodes, Blocks and Size

> 
Inode 3064290 ist in Benutzung, aber hat dtime gesetzt.  Repariere<j>? ja

Inode ... is being used, but set dtime. repair? yes

> 
Inode 3064290 hat Imagic-Flag gesetzt.  Bereinige<j>? ja

Inode ... set Imagic-flag. Purge? yes

> 
Gelöscht Inode 3064295 hat "zero dtime".  Repariere<j>? ja

deleted Inode ... had "zero dtime". Repair? yes

> 
Inodes,  die Teile einer defekten Liste mit verwaisten Links waren.  Repariere<j>? ja

(i think this is a grammatic error) Inodes, Parts of a defective list with abandonded links were (??? were what ???). Repair? yes

> 
Inode 3064309 war Teil der orphaned Inode Liste.  REPARIERT.
Gelöscht Inode 3064313 hat "zero dtime".  Repariere<j>? ja

Inode ... was a part of the orphened Inode list. REPAIRED.
Deleted Inode ... had "zero dtime". Repair? yes.
 
> 
Inode 3064316 war Teil der orphaned Inode Liste.  REPARIERT.
Inode 3064317 war Teil der orphaned Inode Liste.  REPARIERT.
Inode 3064867 ist in Benutzung, aber hat dtime gesetzt.  Repariere<j>? ja

Inode ... was a part of the orphened Inode list. REPAIRED.
Inode ... was a part of the orphened Inode list. REPAIRED.
Inode ... is being used, but set dtime. repair? yes

> 
Inode 3064868 war Teil der orphaned Inode Liste.  REPARIERT.
Gelöscht Inode 3064870 hat "zero dtime".  Repariere<j>? ja

Inode ... was a part of the orphened Inode list. REPAIRED.
Deleted Inode ... had "zero dtime". Repair? yes.

> 
Inode 3064871 war Teil der orphaned Inode Liste.  REPARIERT.
Gelöscht Inode 3064879 hat "zero dtime".  Repariere<j>? ja

Inode ... was a part of the orphened Inode list. REPAIRED.
Deleted Inode ... had "zero dtime". Repair? yes.

> 
Inode 3064290 hat unzulässigen Block(s).  Bereinige<j>? ja

Inode ... has non-permitted blocks(s). Purge? yes

> 
Nicht zulässig Block #1 (134515920) in Inode 3064290.  BEREINIGT.
Nicht zulässig Block #2 (134534112) in Inode 3064290.  BEREINIGT.
Nicht zulässig Block #-1 (3221225012) in Inode 3064290.  BEREINIGT.
Nicht zulässig Block #1036 (4294967295) in Inode 3064290.  BEREINIGT.
Nicht zulässig Block #1037 (4294967295) in Inode 3064290.  BEREINIGT.
Nicht zulässig Block #1038 (4294967295) in Inode 3064290.  BEREINIGT.
Nicht zulässig Block #1039 (4294967295) in Inode 3064290.  BEREINIGT.
Nicht zulässig Block #1040 (4294967295) in Inode 3064290.  BEREINIGT.
Nicht zulässig Block #1041 (4294967295) in Inode 3064290.  BEREINIGT.
Nicht zulässig Block #1042 (4294967295) in Inode 3064290.  BEREINIGT.
Nicht zulässig Block #1043 (4294967295) in Inode 3064290.  BEREINIGT.

Non-permitted Block #... (...) in Inode .... PURGED

> 
Zu viele unzulässige Blocks in Inode 3064290.
Bereinige Inode<j>? ja

Too many non-permitted Blocks in Inode ...
Purge Inode? yes

> 
Inode 3064867 hat INDEX_FL flag gesetzt, ist aber kein Verzeichnis.
Bereinige HTree-Index<j>? ja


Inode ... has set INDEX_FL but is not an Account (Catalogue? Index?). 
Purging HTree-Index

> 
Inode 3064867, i_size ist 13835006962485801624, sollte sein 0.  Repariere<j>? ja

Inode 3064867, i_Blocks ist 3086842336, sollte sein 0.  Repariere<j>? ja

Inode 3064868, i_size ist 13835007512107024384, sollte sein 0.  Repariere<j>? ja

Inode 3064868, i_Blocks ist 134591136, sollte sein 0.  Repariere<j>? ja

Inode 3064289, i_size ist 577887299920986145, sollte sein 0.  Repariere<j>? ja

Inode 3064289, i_Blocks ist 1818850421, sollte sein 0.  Repariere<j>? ja

Inode ...., i_size is ..................., but should be 0. Repair? yes
(x many)

> 
Beginne e2fsck neu ...


starting e2fsck again...



i think mr. knoppix should have appended to this output a few choice sentences including the word 'scheiße'!

viels glück!

---

### Post by phen on 2005-06-09
ooops, there was a misunderstanding. i am very sorry, that i did not clearify my needs: i am german, but i need a translation of what happened to my harddisk! 

what is Inode, zero dtime, etc.

briefly, is my hardware causing this error, or is it repairable by software (e2fsck?)

I am sorry, that you took all the time for me to translate, but the translation i am searching is technospeak -> english or german! Thank you very much anyway!

thanks for any help...

kai

---

