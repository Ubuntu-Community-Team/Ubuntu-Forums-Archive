---
title: "accidentally deleted /etc/passwd + hald-Problems"
date: 2008-08-26
forum: General Help
---

### Post by eliazz on 2008-08-26
I did a stupid thing: in some experiments i accidentally deleted the files /etc/passwd and /etc/shadow. 

Fortunately i had a backup of my /etc and restored both files starting from a live-cd. 

but now ubuntu does not boot up correctly. it just freezes at "Starting the hardware abstraction layer hald". 

when i login on a different tty and restart the hald, gdm starts normally - but it rejects me  after login with the message "your last login was shorter than 10sec, there is something wrong with installation"... 

I have no clue about gdm and hald - has someone a hint for me?

---

### Post by Alaric on 2008-08-26
Try 'sudo aptitude reinstall hal libhal1 libhal-storage1'

---

