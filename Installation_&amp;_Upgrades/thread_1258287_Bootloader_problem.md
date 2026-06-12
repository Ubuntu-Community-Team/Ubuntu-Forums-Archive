---
title: "Bootloader problem"
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by tired-triclops on 2009-09-04
After uninstalling WUBI, the Ubuntu option has remained an option.  If I select the Ubuntu option, it states that a file in the C:\Ubuntu\ folder is missing and redirects to the select OS screen.  Reinstalling WUBI results in a second Ubunut listing, and both work fine.  Uninstalling after that only removes the second listing.  I am using Windows Vista SP 2.  The WUBI version was 9.04.

If anyone knows how to fix this, I would be extremely grateful.

Thanks in advance.

---

### Post by Partyboi2 on 2009-09-05
Hi you can edit the boot.ini for windows and remove the entry for Ubuntu
> **Edit the Boot.ini File**

  To view and edit the Boot.ini file:  
[LIST=1]
[*]Right-click **My Computer**, and then click **Properties**.   -or- 
     Click **Start**, click **Run**, type sysdm.cpl, and then click **OK**.
[*]On the **Advanced** tab, click **Settings** under **Startup and Recovery**.
[*]Under **System Startup**, click **Edit**.
[/LIST]
remove the entry for wubi/ubuntu.

EDIT: Follow presence's post below.

---

### Post by presence1960 on 2009-09-05
Vista doesn't use boot.ini, it uses BCD. To edit click run from the start menu and type in msconfig. When it opens click the boot tab. highlight the references to Ubuntu and click remove. Reboot & they should be gone

---

### Post by Partyboi2 on 2009-09-05
> **presence1960 said:**
> Vista doesn't use boot.ini, it uses BCD. To edit click run from the start menu and type in msconfig. When it opens click the boot tab. highlight the references to Ubuntu and click remove. Reboot & they should be gone
Opps, I miss read that as Windows Xp SP 2, thanks presence :)

---

### Post by presence1960 on 2009-09-05
> **Partyboi2 said:**
> Opps, I miss read that as Windows Xp SP 2, thanks presence :)

No biggie, we all misread things from time to time. I noticed it and didn't want the OP to think he can't fix it.

If that is the worst thing that happens today we all are fortunate.

---

### Post by tired-triclops on 2009-09-26
> **presence1960 said:**
> Vista doesn't use boot.ini, it uses BCD. To edit click run from the start menu and type in msconfig. When it opens click the boot tab. highlight the references to Ubuntu and click remove. Reboot & they should be gone

I tried opening the boot tab and the only reference was to Windows Vista, but when I rebooted later, it still showed the Ubuntu option on the boot screen.

---

### Post by apparle on 2009-09-26
Try [EasyBCD]("http://neosmart.net/dl.php?id=1")

---

