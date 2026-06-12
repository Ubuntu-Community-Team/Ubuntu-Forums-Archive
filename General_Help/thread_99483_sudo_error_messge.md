---
title: "sudo error messge"
date: 2005-12-05
forum: General Help
---

### Post by Thunk on 2005-12-05
Whenever I try to sudo anything it gives me this messege:

"sudo: unable to lookup via gethostbyname()"

Now, I know the problem is probably with my /etc/hosts file but how can I edit it without sudo?

---

### Post by gruepig on 2005-12-06
Hmm ... there might be another way, but the easiest thing that's coming to mind is to boot from an Ubuntu CD and use it as a rescue disk.  Then you should be able to edit /etc/hosts.

---

### Post by cilynx on 2005-12-06
See: [http://ubuntuforums.org/archive/index.php/t-78324.html](http://ubuntuforums.org/archive/index.php/t-78324.html)

This problem was solved there.

---

### Post by Joe_CoT on 2005-12-06
if you don't want to use ubuntu as a rescue disk (i haven't tried it), you can do one of two things to edit the file:

Pop in a Ubuntu live cd (or any other linux livecd), mount your ubuntu hard drive, and edit the file from there

From the grub at startup, choose to boot into recovery mode. That will give you an honest-to-god root shell, and you can edit the files you need. You won't get anything but a console, but just open the file in nano and you should be good to go (just don't go running around rm -rf ing things).

---

