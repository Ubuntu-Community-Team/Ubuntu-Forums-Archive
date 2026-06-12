---
title: "[SOLVED] Transfer Thunderbird Linux to thunderbird Windows"
date: 2008-08-18
forum: General Help
---

### Post by enchance on 2008-08-18
Hi, I just want to make a back-up of all my Thunderbird Linux emails in my Thunderbird XP. I'd be more comfortable knowing all my emails are saved somewhere. Does anyone know how to do this Linux to XP Thunderbird transfer?

---

### Post by aysiu on 2008-08-18
Copy 

/home/*username*/**.thunderbird**

or 

/home/*username*/**.mozilla-thunderbird**

to 

C:\Documents and Settings\*username*\**Application Data**\Thunderbird

That should do it.

Note: the **bolded** directories are hidden directories.

---

### Post by enchance on 2008-08-18
> **aysiu said:**
> Copy 

/home/*username*/**.thunderbird**

or 

/home/*username*/**.mozilla-thunderbird**

to 

C:\Documents and Settings\*username*\**Application Data**\Thunderbird

That should do it.

Note: the **bolded** directories are hidden directories.

Tried it. I had to fix the location a bit but it worked in
C:\Documents and Settings\[username]\Application Data\Thunderbird\Profiles\[alphanumeric].default

Thanks!

---

