---
title: "my swap doesn't work !"
date: 2008-08-11
forum: General Help
---

### Post by S.A.A on 2008-08-11
Hello every body ..

here is my problem, i wanted to expand my swap partition, and did this by adding extra space to it, but since that ubuntu couldn't use the swap unless i go to gparted and do sawpOn.

please help me and thanks already !

---

### Post by scragar on 2008-08-11
reopen gparted and check the partition name

run```
gksudo gedit /etc/fstab
```
look for the line mentioning swap

replace the funny string at the start with: /dev/**partition name**
eg: **/dev/sda5**

---

### Post by cdtech on 2008-08-11
You really should replace the block id instead of using /dev

Type "sudo blkid" on a command line to find the correct block id for your "swap"

---

### Post by S.A.A on 2008-08-11
i did what both of you said, but i still have the problem.

here is the output of: gksudo gedit /etc/fstab

# Entry for /dev/sda7 :
UUID=04a8cca0-3565-427e-92c1-60216697fba7 none swap sw 0 0

---

### Post by kpkeerthi on 2008-08-11
Can you post the output of **sudo blkid**?

Did you restart after changing fstab?

---

### Post by cdtech on 2008-08-11
You could just type "sudo mount -a" to remount your fstab file if you want.

---

### Post by S.A.A on 2008-08-11
Hey, i made a mistake while doing the steps, it works now, thank you all.

finally, i have one more question: what is the beneficence of swap ? (except for hibernation or suspend modes), because with all the time i had without swap i didn't notice any performance changes.

---

### Post by pmlxuser on 2008-08-11
swap helps relieve the RAM when programs are running, possibly you didn't notice a difference because you have a bigger RAM (>256 MB). i think if you had a smaller RAM you could have noticed :)

---

