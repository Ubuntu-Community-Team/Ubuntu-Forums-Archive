---
title: "An error occured"
date: 2008-09-28
forum: Hardware
---

### Post by alan030966 on 2008-09-28
G'Day. I have an error message that dpkg was interrupted and tells me to run it manually. When i try to do this nothing happens. Any help would be much appreciated. Cheers. file:///home/alan/Desktop/Screenshot-synaptic.png

---

### Post by lisati on 2008-09-28
From the terminal (it's on the Applications->Accessories menu) type in ```
sudo dpkg --configure -a
```
Enter your password (it won't show for security reasons) and press 'Enter'.

---

### Post by alan030966 on 2008-09-28
Thanks very much. The worked for me. Cheers

---

