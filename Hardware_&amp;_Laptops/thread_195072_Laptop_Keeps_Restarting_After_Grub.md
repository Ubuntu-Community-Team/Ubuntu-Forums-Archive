---
title: "Laptop Keeps Restarting After Grub"
date: 2006-06-12
forum: Hardware &amp; Laptops
---

### Post by Eyez on 2006-06-12
Hi all,
I just tried installing Dapper server onto an older laptop i have at home for the second time. For some reason, after grub loads and begins to load the kernel, right after "savedefault" and "boot" the computer restarts. It just keeps doing this over and over in a loop. I already tried passing the kernel argument acpi=off and it still does not work. Does anyone have any other solutions?

Thanks!

---

### Post by nlippincott on 2006-06-13
I had this same problem installing Dapper Server on an old IBM Aptiva. The thing just kept rebooting.

Although I never got the Server install CD to work, I downloaded the "Alternate" CD image, which has a server install option. That one worked fine. So, apparently, the alternate CD installs a bit differently than the server CD. I would suggest giving that a try. 

Unfortunately, the alternate CD does not include an "Install LAMP Server" option, which I really wanted to try on the Aptiva.

---

### Post by nmuntz on 2006-06-13
Yes, there is something wrong with that Dapper Server cd.  If you use the alternate CD as nlippincott says and do a server install you won't have this problem.

---

