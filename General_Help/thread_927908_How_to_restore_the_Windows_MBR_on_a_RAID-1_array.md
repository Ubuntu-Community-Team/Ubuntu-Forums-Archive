---
title: "How to restore the Windows MBR on a RAID-1 array?"
date: 2008-09-23
forum: General Help
---

### Post by Moon 111 on 2008-09-23
I have been spending the past two days (as in a grand total of 16 hours) trying to install and then remove Ubuntu. I would really appreciate it if someone would explain to me in non-technical terms how to restore the Windows MBR on a RAID-1 array.

Thank you very much,
- Moshe

EDIT: Oh, by the way, I have Windows XP.

---

### Post by Titan8990 on 2008-09-23
The thing with on board RAID sets is that nothing outside of Windows is aware of the RAID sets existence. I'm a firm believer in descrete RAID controller or nothing. 

Out of all the Windows versions Vista is the only on that ships with a utility to rewrite the bootloader to the MBR.


Also, RAID sets are for advanced users. IMO they have no business being anywhere other than the server world.

---

### Post by Moon 111 on 2008-09-23
I'm running XP. What do I do?

---

### Post by Titan8990 on 2008-09-23
It depends. What have you done so far?

Can you get to Windows via the GURB bootloader?

---

### Post by bobbob1016 on 2008-09-23
I'd also suggest going in to #windows on IRC to ask them how to install it.

Just my 2 cents, a raid isn't a basic or average thing, so basic non-technical terms probably won't exist for it.  A person who drives a fancy exotic car, or an old non-standard car doesn't expect to have people spell out how to repair it.  If you're using a non-standard setup the directions won't be easy.

---

### Post by Moon 111 on 2008-09-23
No, I get GRUB error 21. I can't boot anything. I'm using the live CD.

---

### Post by Titan8990 on 2008-09-23
You can try FIXMBR and FIXBOOT from the recovery console. If it does not work I would consider it toast.

---

### Post by Moon 111 on 2008-09-23
How do I get to the recovery console?

---

### Post by Titan8990 on 2008-09-23
By loading your Windows Installation disk and Pressing "R" when at the main menu.

---

