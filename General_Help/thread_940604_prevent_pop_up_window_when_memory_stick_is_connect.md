---
title: "prevent pop up window when memory stick is connected"
date: 2008-10-07
forum: General Help
---

### Post by waxranger on 2008-10-07
hello dear readers

I would like to prevent the pop up window every time a memory stick or an external hard drive is connected. where can I disable this function in ubuntu?

thanks in advance!
regards
fab

---

### Post by geirha on 2008-10-07
Open a nautilus ("explorer") window, go to Edit -> Preferences, and on the last tab, Media, there's a checkbox on whether to automatically browse media when it's inserted.

---

### Post by Sef on 2008-10-07
> Open a nautilus ("explorer") window, go to Edit -> Preferences, and on the last tab, Media, there's a checkbox on whether to automatically browse media when it's inserted.

To open the nautilus window:

Alt + F2 > type this in the box:  ```
gksudo nautilus
``` > Run > insert password > Edit > Preferences > Media > uncheck 'Browse Media When Inserted'.

---

### Post by geirha on 2008-10-07
> **Sef said:**
> To open the nautilus window:

Alt + F2 > type this in the box:  ```
gksudo nautilus
``` > Run > insert password > Edit > Preferences > Media > uncheck 'Browse Media When Inserted'.

No, without (gk)sudo. This is a user setting.

---

### Post by waxranger on 2008-10-07
thats what I was looking for! thanks

---

