---
title: "Newbie and problem with 3ware 9500s"
date: 2007-05-24
forum: Hardware &amp; Laptops
---

### Post by ksipsi on 2007-05-24
Hello to everybody!
I am a complete newbie, so i ask your sympathy.
I recently installed Ubuntu 7.04 (the desktop version not the server). I had some serious problems trying to operate grub correctly during installation (still i don't get it how grub names the hard drives on my system).
But this is not the problem.
I managed to install Ubuntu after some attempts of try-and-error, i log-in with the account that i created and here comes the problem. Even though ubuntu finds my unit of RAID 5 that is behind 3ware 9500s-12 and displays it when i enter in "My computer" when i click on it in order to access its contents i get this message:
"Cannot display the contents of this folder" and i can't see, neither access, the data that is stored there.
Why do i get this message of error ? Is it a driver problem or something else ?
Please i need some help cause it is vital for me to be able to access the data that is stored in the unit of my 9500s controller.
Thanks and sorry for any syntax errors:oops:

---

### Post by ksipsi on 2007-05-26
Someone ?  :(

---

### Post by ksipsi on 2007-05-31
I installed Kubuntu 7.04 x86 and everything worked OK. I could access my RAID unit. Then i re-installed Ubuntu 7.04 x86. Nothing, no matter what i did i could not access my RAID unit. I even tried mounting-unmounting the unit but nothing.
How is it possible that with Kubuntu 7.04 everything is ok but when i try Ubuntu 7.04 it doesn't work ?
Could this be a bug with Ubuntu ?

---

### Post by Tilo on 2007-05-31
that sounds very odd.. can you post the complete output of 'dmesg' and your '/etc/fstab' ?

---

