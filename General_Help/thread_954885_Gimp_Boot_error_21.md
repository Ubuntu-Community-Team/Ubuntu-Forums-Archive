---
title: "Gimp Boot error 21"
date: 2008-10-21
forum: General Help
---

### Post by Mowk on 2008-10-21
I have seen topics about error 21, but i think it would be very helpful for some advice to me. The problem is when i got my new external hardrive i decided i would install ubuntu on it(not knowing much)   So it went along and installed grub also. But i guess this changes something in the system. So without the ubuntu disk i cannot boot into anything. they only way i can go into windows is go to ubuntus disk and go to boot from first drive then grub seems to work. So i either want to get my old bootup working(so it boots right into  windows right away)  or get gimp working to give me an option between windows and ubuntu. I think the problem is (from reading other posts) that its not seeing my external drive right away from bootup.   So how could i either get gimp working or windows back to normal bootup. Thanks.

---

### Post by louieb on 2008-10-21
> **Mowk said:**
> .. or windows back to normal bootup. Thanks.
Boot you windows install disk and open up the recovery console. 
at the recovery prompt run **fixmbr**. 

Is this a laptop? Do you keep the external plugged in all the time?  If Ubuntu is install on the external, then the main GRUB program **stage2** is on the external too. Do you get the GRUB menu when the external is plugged in? Do both the Ubuntu and XP entry work?

---

