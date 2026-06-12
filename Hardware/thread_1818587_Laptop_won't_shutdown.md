---
title: "Laptop won't shutdown"
date: 2011-08-05
forum: Hardware
---

### Post by Mathias1 on 2011-08-05
Hi!

Having a little trouble getting my new Asus laptop to shutdown correctly.
The OS shuts down properly, but the computer hangs on [this screen]("http://db.tt/DA11XgJ")

Anyone who can help? :)

---

### Post by Mathias1 on 2011-08-07
*BUMP*

Anyone? =)

---

### Post by SalHelder on 2011-08-07
What happens when you use the command:

shutdown 00 -h

?

---

### Post by BlueVark on 2011-08-07
Are you using CIFS to auto mount a drive within fstab?  If so, try to unmount the drive manually and then see if the computer will shut down.  If this fixes the problem, you can write a script to automatically unmount the drive during the early part of the shutdown sequence.  I would be glad to show how I fixed this problem, if needed.

---

### Post by Mathias1 on 2011-08-08
> **SalHelder said:**
> What happens when you use the command:

shutdown 00 -h

?

I will try that.
Is there an output somewhere or will it just force-shut the computer?


> **BlueVark said:**
> Are you using CIFS to auto mount a drive within fstab?  If so, try to unmount the drive manually and then see if the computer will shut down.  If this fixes the problem, you can write a script to automatically unmount the drive during the early part of the shutdown sequence.  I would be glad to show how I fixed this problem, if needed.

I don't think so, I don't have anything mounted.
The funny thing is that it worked flawlessly yesterday, so this seems to be an intermittent error.

---

### Post by SalHelder on 2011-08-08
shutdown 00 -h will probably force it to shut down. Just in case, have you ran any updates since yesterday?

---

### Post by IcarusR on 2011-08-08
You need to find out what is causing it to hang. 
Check the system logs.

Edit the boot parameter & remove the 'quiet' option so you can see the text as it boots & shuts down. Then you will be able to see art what point it hangs in shutdown. Then post what you find.

Install startupmanager, it's in the repositories, then you can do the above graphically.

---

### Post by Mathias1 on 2011-08-08
> **IcarusR said:**
> You need to find out what is causing it to hang. 
Check the system logs.

Edit the boot parameter & remove the 'quiet' option so you can see the text as it boots & shuts down. Then you will be able to see art what point it hangs in shutdown. Then post what you find.

Install startupmanager, it's in the repositories, then you can do the above graphically.

What logs should I look for?
Where do I edit the boot parameter? In BIOS?


**Edit:** Typing "shutdown 00 -h" makes it freeze with 3 dots lit (normally 4).
Don't know if it's caused by that or just a random freeze.

---

### Post by Mathias1 on 2011-08-11
Sorry guys..*bump* again..

---

### Post by IcarusR on 2011-08-12
As I said
> Install startupmanager, it's in the repositories, then you can do the above graphically
In Startup-manager there is a box you can check "show text during boot" & one "show boot splash" to uncheck. 
This will allow you to see text on the screen at boot up & shut down & see where it hangs.

---

### Post by Mathias1 on 2011-08-13
> **IcarusR said:**
> As I said

In Startup-manager there is a box you can check "show text during boot" & one "show boot splash" to uncheck. 
This will allow you to see text on the screen at boot up & shut down & see where it hangs.

Thanks, but it didn't help..There is no text at startup or shutdown..

**Edit:** I figured it out! Heres a screenshot of the [shutdown-log]("http://dl.dropbox.com/u/5168704/IMAG0256.jpg")

---

### Post by Mathias1 on 2011-08-17
This thread seems slow. Nobody got the time to look at this? :(

---

