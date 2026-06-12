---
title: "Can not open RAR files in 8.04"
date: 2008-09-12
forum: General Help
---

### Post by Brain_of_J on 2008-09-12
I'm attempting to open a series of RAR files with the Archive Manager in Hardy (8.04).
I'm receiving this error:
Could not open "file name.rar"
Archive type not supported.

I've attempted to open these files before (a couple of weeks back) and didn't have any issues...this is a recent development. I've downloaded and installed the recommended updates but that is the only change that I know of...

These files can be opened on a Windows machine using WinRAR so they aren't corrupt.

Ideas?

---

### Post by StOoZ on 2008-09-12
install unrar
> sudo apt-get install unrar

then read the man page for additional info about extracting stuff

---

### Post by benerivo on 2008-09-12
It might need an extra package installed. Open synaptic and search for rar. There will be many, but i think the one you need is simply called rar.

---

### Post by StOoZ on 2008-09-12
installing unrar with apt-get will automatically install all the needed dependencies such as rar , etc..

---

### Post by AllanPoe on 2008-09-12
Or you can install WinRar under Wine.

---

### Post by cariboo on 2008-09-12
Why go to the trouble of installing wine, then configuring programs that may not even run that well under wine when there are better native alternatives. Remember Linux is not windows. If you want to run windows programs, run windows.

Jim

---

### Post by Brain_of_J on 2008-09-13
benerivo:
That worked. Thank you.
Why would it "suddenly" stop working though...that's odd...

---

