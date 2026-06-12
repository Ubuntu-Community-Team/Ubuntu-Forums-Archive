---
title: "Laptop Shutdown Issues"
date: 2005-07-30
forum: Hardware &amp; Laptops
---

### Post by leslie on 2005-07-30
Hello people!

Thanks for giving this one a read. I would just like to say I have tried quite a few Linux distributions, Suse, Red Hat, Mandrake and of course Ubuntu and I can confidently say Ubuntu is my favourite. From the free, single disk, iso download to the speed and performance of running straight from the box.

I have just done a standard install on my new laptop, Averatec 3300, and it is quite clearly brilliant. Just one rather minor problem but for that sake of my HDD one I would like to resolve.

My problem is the shutdown and reboot process do not complete and hang after the following out put.

---
System is shutting down, please wait 
---

* Switching to run level: 0
* Sending processes the TERM signal
* Stopping GNOME Display Manager…
* GNOME Display manager not running [ok]
* Stopping periodic command scheduler… [fail]
* Stopping Common Unix Printing System: cupsd [ok]
* Disabling Power Management… 

Can anyone help? 
What is the periodic command scheduler and what could cause it to fail?
And what could prevent the Disabling Power Management process from finishing?

Any help would be greatly appreciated… 

Thanks a lot guys

---

### Post by s_p_a_r_k_y on 2005-07-30
things can fail to turn off if they never strated cleanly. However I don't believe that that is your problem for the shutdown or reboot, as the computer continues to the next task. Seems as though there is some trouble with power management. Have you tried turning off acpi? Look at some of the other threads in this and search for acpi and they will explain how to turn if off.

---

