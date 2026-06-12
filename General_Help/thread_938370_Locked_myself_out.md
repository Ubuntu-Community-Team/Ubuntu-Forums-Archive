---
title: "Locked myself out?"
date: 2008-10-04
forum: General Help
---

### Post by skyggen on 2008-10-04
Hey. I was playing around with pam_fprint and editing the /etc/pam.d/common-auth to work with my fingerprint scanner. 

Now this happens:

> skyggen@skyggen-laptop:~$ sudo gedit /etc/pam.d/common-auth
Scan right middle finger on AuthenTec AES2501
Sorry, try again.
Scan right middle finger on AuthenTec AES2501
Sorry, try again.
Scan right middle finger on AuthenTec AES2501
Sorry, try again.
sudo: 3 incorrect password attempts

Have i locked myself out, how can i use sudo with normal password again?
or somehow get into editing the common-auth file?

---

### Post by skyggen on 2008-10-04
Someone? i need my sudo :(

---

### Post by jamesrl on 2008-10-04
I've never used a fingerpint scanner before, but if you lost access to sudo due to your fingerprint scan no longer working ... there is a backdoor to reboot the computer into single user mode (which is why BIOS passwords are a good idea in general).  From their you should be able to edit any files that need to be edited to turn off the fingerprint scanner.

I haven't seen anything in forum policy preventing explaining how to get into single user mode (which I just rechecked), so here's basic instructions with grub.  It's also probably pretty good for most users to know about the dangers of allowing password-less reboots (as giving anyone root priveleges).  First reboot and get to the grub menu.  If you have a "recovery mode" or "single user mode" options present, just select that and it should log you in as root.  Otherwise, go over your normal option, press 'e' to edit it, go down to the 'kernel' line, and add the word 'single' to the end of the line, and then  boot this kernel.

---

