---
title: "Acer Aspire 5601AWLMi doesn't wake from sleep"
date: 2006-08-02
forum: Hardware &amp; Laptops
---

### Post by Rinnan on 2006-08-02
Hello.  I just bought a new Acer Aspire 5601AWLMi, and it runs Dapper fairly well.  There are a few problems, in this thread I'd like to ask about sleep.

When I click the "log out" icon, I get only a "Hibernate" option (other than the other standard ones, "Log Out", "Switch User", "Lock Screen", "Shut Down", "Restart").  What is "Hibernate" and how is it different from "Sleep"?

Also, although it seems to sleep when I close the lid (screen blacks, all activity seems to stop), it does not wake up.  When it should be coming back up, there is a flurry of activity of the drives (harddrive, cdrom), but it never does turn the screen back on.  I have also tried to reboot the system after giving it some time, to see if it's only the display and the rest of the machine is running (I put it to sleep while in console, then "unslept" it, gave it some time, then typed "reboot" and return into the console (it was already in root via "sudo su"), but no dice.

I've done some searches but nothing seems to apply to my laptop.  One problem is I don't know what part of machine handles sleep, so I'm not sure how to search for help.  For example, if I were having a video problem, I'd probably try searching on the video chipset (for example, nvidia or ati) but I don't know what the "sleep" chipset is, if there is one.

Thanks in advance for any help, this is quite frustrating!

---

### Post by Rexbron! on 2006-08-02
> **Rinnan said:**
> Hello.  I just bought a new Acer Aspire 5601AWLMi, and it runs Dapper fairly well.  There are a few problems, in this thread I'd like to ask about sleep.

When I click the "log out" icon, I get only a "Hibernate" option (other than the other standard ones, "Log Out", "Switch User", "Lock Screen", "Shut Down", "Restart").  What is "Hibernate" and how is it different from "Sleep"?

Also, although it seems to sleep when I close the lid (screen blacks, all activity seems to stop), it does not wake up.  When it should be coming back up, there is a flurry of activity of the drives (harddrive, cdrom), but it never does turn the screen back on.  I have also tried to reboot the system after giving it some time, to see if it's only the display and the rest of the machine is running (I put it to sleep while in console, then "unslept" it, gave it some time, then typed "reboot" and return into the console (it was already in root via "sudo su"), but no dice.

I've done some searches but nothing seems to apply to my laptop.  One problem is I don't know what part of machine handles sleep, so I'm not sure how to search for help.  For example, if I were having a video problem, I'd probably try searching on the video chipset (for example, nvidia or ati) but I don't know what the "sleep" chipset is, if there is one.

Thanks in advance for any help, this is quite frustrating!


To start, sleep/suspend shuts down everything but the ram.

Hibernate - Writes the ram to disk.

If you have trouble resuming with Klaptop, try using Kpowersave.

For my laptop (Aspire 3624), suspend and hibernate work with Klaptop but not Kpowersave. IMO, Kpowersave has a nicer interface than Klaptop.

Try both and post any trouble.

---

