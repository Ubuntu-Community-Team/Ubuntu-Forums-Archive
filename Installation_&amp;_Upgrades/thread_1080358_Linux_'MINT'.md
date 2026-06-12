---
title: "Linux 'MINT'"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by Hugeangler on 2009-02-25
Cannot install 'mint' on a formatted disc,get 'ntldr is missing' any help appreciated

---

### Post by howefield on 2009-02-25
> **Hugeangler said:**
> Cannot install 'mint' on a formatted disc,get 'ntldr is missing' any help appreciated

Bit more info please ?

ntldr is related to windows installs. Is this a wubi install ?

---

### Post by avtolle on 2009-02-25
How are you trying to install Mint? Using the "mint4win" app, or on a dedicated partition outside Windows?

---

### Post by Hugeangler on 2009-02-25
Am more than a bit green at this but do you mean a new install

---

### Post by Mark Phelps on 2009-02-25
> **Hugeangler said:**
> Cannot install 'mint' on a formatted disc,get 'ntldr is missing' any help appreciated

You would get this if you removed the XP boot files and then tried to invoke XP.  This would happen if you failed to change your Boot order in the BIOS to select the CD/DVD drive.  

I presume you're trying to boot from a Linux Mint CD, so change your Boot order in the BIOS to select the CD/DVD drive, boot from that CD, and follow the menus and prompts.

---

### Post by stchman on 2009-02-25
> **Hugeangler said:**
> Cannot install 'mint' on a formatted disc,get 'ntldr is missing' any help appreciated

Saying "on a formatted disc" indicates that he is using Mint's version of WUBI mint4win.

I recommend doing an install on it's own partition.

---

