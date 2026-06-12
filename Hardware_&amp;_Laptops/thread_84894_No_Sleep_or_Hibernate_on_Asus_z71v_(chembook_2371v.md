---
title: "No Sleep or Hibernate on Asus z71v (chembook 2371v)"
date: 2005-11-01
forum: Hardware &amp; Laptops
---

### Post by secundar on 2005-11-01
Recently dist-upgraded to Breezy and the latest 686 kernel. Seems a little more snappy. Everything worked "out of the box" - ALSA, Nvidia 7667 drivers -- but Sleep does not work from the Fn+F1 keyboard command nor when I close the lid. Both Sleep and Hibernate are also not in the logout panel.

Any Asus users have any tips?

Thanks!

---

### Post by lorenco on 2005-11-01
You must enable powermanagement ACPI hibernate / Suspend first...
If you r running KDE you can Right klick on the KLaptop power and configure then add hibernate / suspend in the ACPI section...

You can also configure it in /etc/default/acpi-support

Change 
ACPI_HIBERNATE=true

---

### Post by secundar on 2005-11-01
Thanks.

I'm using gnome so I edited the acpi-support file as you indicated. After a reboot   I still do not have suspend or hibernate in the Log-out window. Fn+F1 doesnt do anything either.

I had suspend in hoary but i do remember doing extra work to get hibernate.

Sorry. I did this stuff about a year ago and didn't take notes :(

---

### Post by Cannedbread on 2005-11-13
i just built myself an asus Z71A machine for breezy. 

i think that:
z71a = z71v - some features

hibernate works without any screwing around.
and to get sleep to work, all i have to do is enable it in that config file, then i can sleep by hitting logoff>suspend.

i havent figured out how to associate the sleep button with this though..

---

### Post by secundar on 2005-11-13
I suppose I could investigate.... I guess a dist-ugrade is bound to cause issues with some things. After a few weeks I now have both Suspend and Hibernate in my log-out window. The Fn+F1 key works also.

---

