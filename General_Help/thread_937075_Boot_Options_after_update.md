---
title: "Boot Options after update"
date: 2008-10-03
forum: General Help
---

### Post by Nabanna on 2008-10-03
Hi,

After updating(all security updates+selected recommended updates) Ubuntu 8.04, i am now getting two new boot option:
[CODE[B][U]]Ubuntu 8.04, kernel 2.6.24-19-generic
Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)[/U][/B]
Ubuntu 8.04, kernel 2.6.24-16-generic
Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
Ubuntu 8.04, memtest86+[/CODE]

Is it normal?
Does it mean i now have two different versions of Ubuntu kernel(like two diff. OS).????
Please help......

---

### Post by Idefix82 on 2008-10-03
Exactly. You probably only had the older kernel before the updates and now you got the new one. You should try that and if everything works for you then you can safely delete the old kernel.

Edit: It's not like two completely different OSs, since the two probably share your /home folder as well as lots of other things.

---

### Post by howefield on 2008-10-03
Yes, it is normal, you can boot in to either kernel, nothing to worry about. 

If it really bothers you, you can remove the old kernel and or simply edit the grub menu so you don't see it.

---

### Post by Ryadt on 2008-10-03
It's perfectly normal. Ubuntu keeps the old kernel after upgrading to a newer one.
You can delete the old one in synaptic. Search for linux-image-2.6.24-16.

---

### Post by MunkyJunky on 2008-10-03
That's perfectly normal, you've just updated to a newer kernel version. It's nothing to worry about. :)

---

### Post by drs305 on 2008-10-03
Here is a link discussing why this happened and how to tweak your grub menu options using StartUp-Manager:
[URL="http://ubuntuforums.org/showthread.php?t=818177"] HOWTO: Grub Menu Kernel Display Options
[/URL]

---

### Post by Nabanna on 2008-10-03
> **MunkyJunky said:**
> That's perfectly normal, you've just updated to a newer kernel version. It's nothing to worry about. :)

> **Ryadt said:**
> It's perfectly normal. Ubuntu keeps the old kernel after upgrading to a newer one.
You can delete the old one in synaptic. Search for linux-image-2.6.24-16.
Thank you, i was really worried about this, i thought i did something wrong..

does it takes more space,i mean instead of one kernel i now have two of them??
how to delete **Ubuntu 8.04, kernel 2.6.24-16-generic**...???
will it be safe to do so...??

---

### Post by Idefix82 on 2008-10-03
A kernel doesn't take much space. You should test the new kernel thoroughly before deleting the old one.

Edit: Once you definitely decide to delete the old kernel, have a look at this:
[http://ubuntuforums.org/archive/index.php/t-357932.html]("http://ubuntuforums.org/archive/index.php/t-357932.html")

---

### Post by MunkyJunky on 2008-10-03
Yes, check a post higher up. You can remove the older kernel though Synaptic package manager. It's compleately safe to do so.

---

### Post by Ryadt on 2008-10-03
It does take up some space. Deleting it is absolutely safe. Read my post above on how to delete it.

---

### Post by Nabanna on 2008-10-03
> **Ryadt said:**
> It's perfectly normal. Ubuntu keeps the old kernel after upgrading to a newer one.
You can delete the old one in synaptic. Search for linux-image-2.6.24-16.

thanks,,
but there are so many options for 'linux-image-2.6.24-16'
(see the attachment)
which one to delete???


(sorry for late replies, slow connection here)

---

### Post by Idefix82 on 2008-10-03
You only have the one with the green box next to it installed, so that's the only one you need to delete.

---

### Post by howefield on 2008-10-03
> **Nabanna said:**
> thanks,,
but there are so many options for 'linux-image-2.6.24-16'
(see the attachment)
which one to delete???


(sorry for late replies, slow connection here)

empty check box means the package is not installed, solid green means it is, that should help you narrow it down ;)

---

### Post by Ryadt on 2008-10-03
Only the one in with the green check box is installed.

---

### Post by Nabanna on 2008-10-03
ok, so i have to select it and "Mark for removal"...????
it then opens a windows a asking 
'To be removed'
-linux-restricted-modules-2.6.24-16-generic
-linux-ubuntu-modules-2.6.24-16-generic


am i doing it right??

---

### Post by Ryadt on 2008-10-03
> **Nabanna said:**
> ok, so i have to select it and "Mark for removal"...????
it then opens a windows a asking 
'To be removed'
-linux-restricted-modules-2.6.24-16-generic
-linux-ubuntu-modules-2.6.24-16-generic


am i doing it right??
Yeah...;)

---

### Post by Idefix82 on 2008-10-03
Yes, it is removing all the dependencies along with the selected package (meaning those that needed the removed package).

---

### Post by Nabanna on 2008-10-03
Thank You...
(going to do it now...fingers crossed)

---

### Post by Nabanna on 2008-10-03
Done :D ....
Thanks to all :) ....

(it showed 3 items to be removed and notified nearly 125MB will be freed..
after completion i rebooted....then at boot up 'Routine check for drives..' :confused: ....i hope every thing is all right now)

---

