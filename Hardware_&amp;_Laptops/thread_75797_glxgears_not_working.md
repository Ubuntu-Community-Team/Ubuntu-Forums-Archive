---
title: "glxgears not working"
date: 2005-10-14
forum: Hardware &amp; Laptops
---

### Post by Myst3K on 2005-10-14
I just removed 5.04 out today, and installed 5.10.  I have been trying to get WoW to work for a while on linux to completely switch over. Installed the nvidia 7667 drivers, I get the nvidia logo and everything seems to work fine with it.  

When I try and run glxgears, I get the error message "Segmentation Fault".  I have ge-force nvidia 6200OC,  after I write this I will be installing WoW with cedega.  We will see how that goes, but if anyone knows what the problem with glxgears could be, help would be appreciated.  Let me know if there is anymore information needed, as I am not sure what to post to help fix the problem.

Thanks!

---

### Post by Myst3K on 2005-10-14
Ok, so I reinstalled Ubuntu 5.10, didnt update anything yet.  Installed the linux-686-smp, the header files, updated to the 7667 nvidia drivers.  glxgears now runs properly, but it doesnt output any information.  Does anyone know how to make it display the fps, I have tried "sudo glxgears", and "glxgears", and neither of them display the fps.  Any ideas?

Thanks

---

### Post by Myst3K on 2005-10-14
figured it out, thanks!

after searching a little bit more through the posts i found the answer, i am at work now, but i will go home and try it 

glxgears -printfps

---

### Post by goslackware on 2006-03-15
current glxgears options:

-display
-info
-stereo
-fullscreen
-iacknowledgethatthistoolisnotabenchmark
-printfps

example:
glxgears -info -fullscreen -printfps

use, ctrl-c to exit glxgears while in fullscreen mode

~goslackware

---

### Post by klahjn on 2006-03-15
[QUOTE=Myst3K]figured it out, thanks!  after searching a little bit more through the posts i found the answer, i am at work now, but i will go home and try it 
glxgears -printfps[/QUOTE]

Cool, thanks for the info.

---

