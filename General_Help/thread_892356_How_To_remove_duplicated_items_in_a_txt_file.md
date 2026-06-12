---
title: "How To remove duplicated items in a txt file?"
date: 2008-08-17
forum: General Help
---

### Post by eHobayyeb on 2008-08-17
Hi,

I have a long list of Arabic words UTF-8 and I want to delete every duplicated word.

Every word in a line.

Thanks

---

### Post by drboontu on 2008-08-17
Hi,

This will remove repeated material, but I'm not sure about single words.

$ cat oldfile.txt | sort | uniq > newfile.txt

Cheers!

---

### Post by ghostdog74 on 2008-08-17
> **drboontu said:**
> Hi,

This will remove repeated material, but I'm not sure about single words.

$ cat oldfile.txt | sort | uniq > newfile.txt

Cheers!

no need for cat.
```

sort file | uniq

```
modern sort has a -u option for checking uniqueness. 
```

sort -u file

```

---

### Post by eHobayyeb on 2008-08-17
Thank you all
It works fine
But is there a software for doing that and other options?

---

