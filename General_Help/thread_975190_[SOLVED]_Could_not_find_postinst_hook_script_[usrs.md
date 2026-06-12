---
title: "[SOLVED] Could not find postinst hook script [usr/sbin/update-grub]"
date: 2008-11-08
forum: General Help
---

### Post by ant1060 on 2008-11-08
Hi everyone :
After hours and hours of research over three weeks, I have finally found a solution to this problem "Could not find postinst hook script [usr/sbin/update-grub]"
which prevented any new kernel (2.6.24-19-generic, 2.6.24-21-generic, and also the new Intrepid Kernel 2.6.27-7-generic) from installing on my machine.

Other symptoms were that sudo dpkg --configure -a and all other attempts such as sudo install -f (kernel-image) all failed...

Simply go to /etc/kernel-img.config and check that on the line
postinst_hook = the symbol "/" is indeed before the path!

Mine said :
postinst_hook = usr/sbin/update-grub
postrm_hook   = usr/sbin/update-grub

Correcting this to :
postinst_hook = /usr/sbin/update-grub
postrm_hook   = /usr/sbin/update-grub
fixed the problem instantly and finally ALL the failing packages installed.

Hope this helps someone else!
:)

---

### Post by wavesailor on 2008-11-10
I had the same problem but my /etc/kernel-img.config looked like this

postinst_hook = update-grub
postrm_hook = update-grub

and the way I solved it was to do this

apt-get install grub

It seems when I updated to 8.10, the update routine removed grub :-(

---

### Post by rrkrr on 2008-12-30
Thanks for the post!  I was tearing my hair out over this one, but this simple fix solved the problem.  I hope the source gets fixed!

---

### Post by rarsa on 2010-06-12
Thank you, your post set me in the right direction.

In my case I don't even have grub2 installed as my installation is an upgrade from 8.04 

The solution was as easy: I had to completelly comment out the postinst_hook and postrm_hook from /etc/kernel-img.conf

---

