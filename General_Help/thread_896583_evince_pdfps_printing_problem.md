---
title: "evince pdf/ps printing problem"
date: 2008-08-21
forum: General Help
---

### Post by Freiburg05 on 2008-08-21
Hi

    First of all, I'm opening a new thread about this issue, despite being some already, because I haven't been able to find a solution. I even read some related bug reports but didn't solve the problem. Here is my problem:


     Evince won't print some pdf or ps files. When I click the print button the dialog appears normally, but after I select the printer and click print the dialog window closes and nothing happens, There is nothing in the printer queue. If I click the "print preview" button the dialog also closes without doing anything.
    
    The printer is a HP 4250 shared printer. I've tried to print to a pdf file, but no file is created.

     It doesn't happen with all the files, and I can't say if the files causing the error share a certain characteristic.

     Another thing I've noticed when running evince in a terminal, is that evince throws the following error/warning several times when opening those files which can not be printed:

           cairo context error: NULL pointer

     Although this warning is thrown there is no other problem apart from printing. Evince won't crash and I can read those files. I really need the printing feature, so I can try another pdf viewer, but I really think this problem should be solved since evince is the default viewer for ubuntu.


     Any help would be appreciated.

     P.S.: Using Hardy in a P4 2,8GHz, fully updated, also cairo and poppler libraries (or at least that's what I think).

---

### Post by kaibob on 2008-08-21
> **Freiburg05 said:**
> ...Evince won't print some pdf or ps files. When I click the print button the dialog appears normally, but after I select the printer and click print the dialog window closes and nothing happens, There is nothing in the printer queue. If I click the "print preview" button the dialog also closes without doing anything...
I've had the same problem, and it's been around for some time. As a workaround, I use lpr to print PDF files that evince won't print. This works every time but is an annoyance. Hopefully someone will have a solution for us.

---

### Post by Freiburg05 on 2008-08-22
Thanks, the old good lpr command works fine. Anyway I hope this problem will be fixed sometime.

---

