---
title: "No ACPI on Travlemate NO LAn neither any USB !"
date: 2005-10-13
forum: Hardware &amp; Laptops
---

### Post by Mashang on 2005-10-13
it was like a poem !
anyhow .. i tried installing breezy and well no luck again .. i have the travelmate 8104 it configures my lan but it cant connect to DHCP network here .. It makes sense if the wireless wont work but not the regular lan or my USB !!!
PLease help me !
Thank you 
Mashiii

=----------- Travelmate 8104
A great Labtop Missing a good OS !!! I WANT UBUNTU !!!!

---

### Post by Mashang on 2005-10-13
OK Well For anyone with htis labtop i have to say there is hope, 
When installing put the "acpi=off" and once the system is up after changing the MONITOR layout add " nolapic noapic " and remove the acpi =off from the kernel in grub and lan works ! next is configuring wifi and so much more ;) I will work on it .. but i am further than before so its all good !

MAshii


My travelmate is working fine

---

### Post by skirkpatrick on 2005-10-13
Anybody remember what functionality you lose with noapic?  I think it's only hibernation and suspend but I'm not sure as I haven't had to do this.

---

