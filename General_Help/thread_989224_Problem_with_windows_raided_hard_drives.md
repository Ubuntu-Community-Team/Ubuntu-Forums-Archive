---
title: "Problem with windows raided hard drives"
date: 2008-11-21
forum: General Help
---

### Post by Cappy82288 on 2008-11-21
My desktop has 3 hard drives inside of it. One is a SATA and is the main drives where the OS is installed. The other two have been raided in windows. I installed Ubuntu onto my hard drive but I cannot see one of the raided hard drives and the other says that it cannot mount. I typed in sudo fdisk -l and It found the missing hard drive but I cannot see it. Is there some way to get Ubuntu to recognize a windows raid?

---

### Post by fjgaude on 2008-11-21
The normal way is to use a program called **dmraid**. It's in the repository and the **man** pages tell all.

---

### Post by psusi on 2008-11-21
> **fjgaude said:**
> The normal way is to use a program called **dmraid**. It's in the repository and the **man** pages tell all.

No, that is for recognizing hardware fakeraids.  If it is a windows software raid, you're out of luck.

---

### Post by Cappy82288 on 2008-11-21
> **psusi said:**
> If it is a windows software raid, you're out of luck.

Yes it is a windows software raid.  Is there anyway to fix that if I was to reinstall windows or even like dual boot?

---

