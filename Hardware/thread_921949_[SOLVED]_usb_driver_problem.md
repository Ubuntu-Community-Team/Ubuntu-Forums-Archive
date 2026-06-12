---
title: "[SOLVED] usb driver problem"
date: 2008-09-16
forum: Hardware
---

### Post by mefistofeles666 on 2008-09-16
last week my usb drive was working fine and I was able to copy files and everything...now, for some reason it's not working anymore, whenever I try to copy a file to the drive it gives me and error and tells me the file or destination is read only. I know the usb is fine bc it works fine in windows. any ideas what might had happened?

---

### Post by IntuitiveNipple on 2008-09-16
The implication of what you've written is that the file-system on the USB disk is NTFS - if that is correct then it is possible that it is being mounted read-only because a flag on the file-system indicates it needs a file-system check.

That must be done in Windows using:
```

checkdsk /f drive_letter:

```

---

