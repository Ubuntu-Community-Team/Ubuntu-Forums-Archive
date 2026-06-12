---
title: "mounting secondary ntfs drive"
date: 2005-12-06
forum: General Help
---

### Post by maobrien on 2005-12-06
hi there, 

new to ubuntu but have a small knowledge with redhat network admin. i have succesfully managed to mount 1 ntfs harddrive(one with windows on - still need it for matlab) however cannot find a thread to add an additional to mount a second ntfs harddrive partition. i think the main problem is not being able to find out partition names. can i anyone help?
also dont spose if i can set up dual monitors in ubuntu>?

thanks
O'B

---

### Post by kosmic on 2005-12-06
to find out the partitions you have in your computer do as root or using sudo :
 
sudo fdisk -l (it's a L uncapitalized )
 
 
For dual monitor look where (if you have a nvidia card)  - [http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html]("http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html")

---

### Post by maobrien on 2005-12-06
perfect managed it now thanks mate!

---

