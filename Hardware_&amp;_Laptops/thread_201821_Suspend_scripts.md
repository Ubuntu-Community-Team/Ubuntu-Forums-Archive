---
title: "Suspend scripts?"
date: 2006-06-22
forum: Hardware &amp; Laptops
---

### Post by luften on 2006-06-22
Hello

I have now been running Ubuntu Dapper (on my Fujitsu P7010) for a few days, and things are starting to look a bit clearer to me.

However, I still have some small problems, like this one:

I want my BT mouse to work after suspend, and figured out, it can be done by running "bluez-utils stop" before suspending, and "bluez-utils start" on resume.

This works fine if I do it manually, but when I add them from a shell script in "/etc/acpi/suspend.d" and "/etc/acpi/resume.d", it is no longer working.

I can see that both scripts are ran, as I added some echoing to a log file.

As well, if I run the command "/etc/acpi/sleep.sh force", my machine will nicely go into sleep (but it is clearly not the same that is run from choosing suspend in ubuntu), and when I resume, my mouse works!

So.. any suggestions where to look?

If I manually run "bluez-utils stop" before clicking suspend, the mouse will work automatically when I resume.. 

Any suggestions are welcome!

---

### Post by luften on 2006-06-23
I did some more testing, and found out that if I manually call the script "/etc/acpi/sleepbtn.sh" I can make the computer sleep in the same way as clicking "suspend" in Ubuntu. But, if I do it this way, my mouse wake's up as it should!

What excatly happens when I click "suspend" in Ubuntu? There must be something strange happening in between before it calls the "sleepbtn.sh" script.

---

### Post by luften on 2006-06-23
And the problem is solved.

It seems that when i linked my "stop_bt" script to "/etc/acpi/suspend.d/04-stop_bt", the mouse was still in use by ubuntu. I changed it to "40-stop_bt" and then it works :)

---

