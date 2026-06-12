---
title: "HP 1610, Samba, and Kubuntu"
date: 2008-09-23
forum: General Help
---

### Post by GeneWeber on 2008-09-23
Hi Sef,

I see from your post that you use an HP PSC 1610. I just downloaded and installed Kubuntu 8.0.4 (KDE 3.5.9). I'm using the add printer wizard (KDE Print).  On the “Backend Selection” page I select “SMB shared printer (Windows)”. “User Identification” is set to Anonymous. On the “SMB Printers Setting” page
I search and find HPPSC160 which is my HP PSC 1610 printer. But when I go to the “Printer Model Selection” page an HP PSC 1610 is not one of the listed printers. So I selected a HP PSC 950 (Foomatic + gutenprint-ijs-simplified.5.0). It test prints OK and I sent a page of text from Writer with no problem.

So maybe it's fine, but I was wondering if you had found a driver specifically for the 
PSC 1610?

Thanks,

Gene

---

### Post by wolfen69 on 2008-09-23
go [here]("http://hplipopensource.com/hplip-web/index.html") and download the latest hp drivers. extract the file to your home folder and then open a terminal and: ```
sh hplip-2.8.8.44.run

``` or whatever version # it is. then follow the prompts.

---

### Post by GeneWeber on 2008-09-24
I will give this a try. Thank you.

---

