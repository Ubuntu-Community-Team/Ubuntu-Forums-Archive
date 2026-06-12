---
title: "thinking of trying ubuntu using wubi."
date: 2008-09-13
forum: General Help
---

### Post by terry_gardener on 2008-09-13
hello 

someone i know is thinking of trying ubuntu. if i installed it for them using wubi will they be able to get all the compiz features. (gpu = geforce 8300 gs) is there any performance decreases with installing using wubi. the computer has a quad core cpu so i am guessing it will automatically download the 64 bit version. if ij downloaded the 32 bit version and place it into the fodler wubi installer it will install 32bit ubuntu instead. 

do you get the full ubuntu experience using wubi compared to dual-boot option. 

thinking of wubi because 
1. user can uninstall it if they dont like it. 
2. dont have to re partition HDD.
3. wont change MBR to grub

---

### Post by DrMelon on 2008-09-13
Wubi allows a full Ubuntu experience! No worries there!

---

### Post by issih on 2008-09-13
As far as I know the only major limitation you run into using wubi is that suspend/hibernate are not useable, mind you, a lot of people have trouble with them even with a normal install, so you aren't losing much...

Hope that helps

---

### Post by Orlsend on 2008-09-13
> **issih said:**
> As far as I know the only major limitation you run into using wubi is that suspend/hibernate are not useable, mind you, a lot of people have trouble with them even with a normal install, so you aren't losing much...

Hope that helps
Yeah the suspend its the only feature notfor Wubi.

---

### Post by god0fgod on 2008-09-13
Compiz should work. It worked for me. You should just need to download a driver.

---

### Post by terry_gardener on 2008-09-13
thanks for the quick replies.

it is a desktop pc so suspend/hibernate modes not needed.

---

### Post by ago on 2008-09-15
Suspend actually works with wubi 8.04 (provided your hardware is compatible), Hibernation does not.

---

### Post by sat_e_llite on 2008-09-15
What is the difference between Suspend and Hibernate?

---

### Post by lswest on 2008-09-15
> **sat_e_llite said:**
> What is the difference between Suspend and Hibernate?

Suspend temporarily stores the information in RAM so the system can be recalled fast and efficiently: Reduces power cost as the only thing still being powered is the RAM modules so it does not wipe the stored info.

Hibernate temporarily stores the information on the hdd (swap) so it can be recalled faster than rebooting, but needs no power to retain the information, thus being a good option when the laptop's battery is very nearly gone.

---

