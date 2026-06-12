---
title: "No cdrom Auto Mount"
date: 2005-01-29
forum: Hardware &amp; Laptops
---

### Post by sharke on 2005-01-29
Hi All
i have warty installed all working fine . I upgraded the kernel to a 686 because i have a pentium4. Before upgrade my 3 drives would automount after nogo. How do i get autmount back.
Regards
Sharke

---

### Post by IdoMcFly on 2005-03-19
I have same problem here, automount used to work but not anymore since either I added a new soudcard or did an update.

Using Hoary Preview Release.

---

### Post by IdoMcFly on 2005-03-21
[QUOTE=sharke]Hi All
i have warty installed all working fine . I upgraded the kernel to a 686 because i have a pentium4. Before upgrade my 3 drives would automount after nogo. How do i get autmount back.
Regards
Sharke[/QUOTE]
 quite old now but I bumped into similar problem : it was a problem with the groups in which the user "hal" was : it has to be in the group of your /dev/hd* 

sudo adduser hal <the group> to add a group to hal user.

Hope it helps

---

