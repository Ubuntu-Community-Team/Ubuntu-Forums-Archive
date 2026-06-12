---
title: "Fingerprint nx6320"
date: 2007-12-28
forum: Hardware &amp; Laptops
---

### Post by Wendy_123_2k8 on 2007-12-28
Hi
I have HP nx6320
How to make my fingerprint-reader to work with Ubuntu Feisty

---

### Post by LinuxIsInnovation on 2007-12-28
Check this out:
[http://ubuntuforums.org/showthread.php?p=3935364](http://ubuntuforums.org/showthread.php?p=3935364)


Works for me!! :D

---

### Post by Wendy_123_2k8 on 2007-12-28
Okay.. thank you :)
I will check this out :)

---

### Post by LinuxIsInnovation on 2007-12-28
Youre welcome :)

---

### Post by Wendy_123_2k8 on 2007-12-28
Is the access manager like Verisoft in Windows?

---

### Post by LinuxIsInnovation on 2007-12-28
Not exactly. It asks for fingerprint first and then for the password. When you will open administrative apps like synaptic, your computer will wait without notifying anything until you swipe your finger.
You can enroll fingerprints by:
$fprint_demo

---

### Post by Wendy_123_2k8 on 2007-12-28
I downloaded them, do they work on a 64-bit version?

---

### Post by LinuxIsInnovation on 2007-12-28
Yes.. they do :D

---

### Post by Wendy_123_2k8 on 2007-12-28
What to do now? I installed the three files..

---

### Post by LinuxIsInnovation on 2007-12-28
Now do this:
sudo gedit /etc/pam.d/common-auth

And enter this to the file:
auth    sufficient      pam_fprint.so
auth    required        pam_unix.so nullok_secure

---

### Post by Wendy_123_2k8 on 2007-12-28
Done.. Is it ready to use now?

---

### Post by LinuxIsInnovation on 2007-12-28
No.. you have to enroll your fingerprints now.
Remember, the first finger you enroll will be asked for authentication
To enroll:
$sudo fprint_demo

---

### Post by Wendy_123_2k8 on 2007-12-28
Ok... done!! Thanks :D
By the way, can I remove the password line from common-auth completely so that it just asks for fingerprints but not passwords.??

---

### Post by LinuxIsInnovation on 2007-12-28
Well, you can.. But dont do that.. You may lock yourself from logging in (in case your fprint reader doesnt read the fprint correctly or the enrolled finger gets hurt ;))

---

### Post by Wendy_123_2k8 on 2007-12-28
Ok... thanks for replying so fast :D
Have a nice day.. :)

---

### Post by LinuxIsInnovation on 2007-12-28
Youre Welcome.. :)

I have been sticking to this thread since the last 10mins and dint go anywhere else :D
That explains the fast response ;)

---

