---
title: "PDF printer not installed in 8.10 heres how to fix"
date: 2008-11-16
forum: Hardware
---

### Post by stinger30au on 2008-11-16
when installed 8.10 i found i could not print pdf files

fire up nautilus and head to your home directory

create a new directory called


PDF


(must be with caps on)

restart pc

now when you print pdf it will do to this directory and all is good

this has also happened to me on installs of 8.04 too

hope someone finds its usefull

---

### Post by mcdragon on 2008-11-20
Hi

I explicitly saw that CUPS PDF printer package was marked as obsolete so I wondered whether Ubuntu has introduced a new was of doing that. I let the installer remove it as I trust the Canonical folks know better than I do. Worse case, I would just have to reinstall the package.

My PDF folder never went away, but there is no universal PDF printer. Firefox has a print to file (PDF). Openoffice has also an in-built one.

So to re-install the old PDF printing:

> sudo apt-get install cups-pdf

---

### Post by stinger30au on 2008-11-21
> **mcdragon said:**
> Hi

I explicitly saw that CUPS PDF printer package was marked as obsolete so I wondered whether Ubuntu has introduced a new was of doing that. I let the installer remove it as I trust the Canonical folks know better than I do. Worse case, I would just have to reinstall the package.

My PDF folder never went away, but there is no universal PDF printer. Firefox has a print to file (PDF). Openoffice has also an in-built one.

So to re-install the old PDF printing:


there definitely is a universal pdf printer option accessible to every program on my 8.10 pc

i just created the PDF directory and restarted and now i can use the pdf print from *ANY* program

i did not add/remove anything pdf related other then create the directory

---

### Post by dinarcon on 2008-11-23
thanks a lot... it worked perfectly!

note: just before creating the "~/PDF" directory, I tried (as suggested by [aggiemarine07]("http://ubuntuforums.org/showpost.php?p=6216706&postcount=18")):
"sudo chmod 0755 /usr/lib/cups/backend/*"
...not quite sure if it helped as well.

(remark: aggiemarine07 did not include sudo as part of the command, but if not present I hadn't permission to modify the files' attributes)

---

### Post by stinger30au on 2008-11-23
> **dinarcon said:**
> thanks a lot... it worked perfectly!

note: just before creating the "~/PDF" directory, I tried (as suggested by [aggiemarine07]("http://ubuntuforums.org/showpost.php?p=6216706&postcount=18")):
"sudo chmod 0755 /usr/lib/cups/backend/*"
...not quite sure if it helped as well.

(remark: aggiemarine07 did not include sudo as part of the command, but if not present I hadn't permission to modify the files' attributes)


glad it worked for you :)

---

