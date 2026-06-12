---
title: "acpi problems preventing HD spindown"
date: 2006-09-26
forum: Hardware &amp; Laptops
---

### Post by Argos_Bling on 2006-09-26
I have a Toshiba Satellite Pro 4600, and almost everything works out of the box, with the exception that laptop_mode_tools can't keep the hard drive from spinning. After the drive has spun down, a few seconds later it spins back up again. After a lot of work I have finally tracked down the problem - /var/log/acpid is being updated every 17 seconds ](*,) with the following sequence:
> [Tue Sep 26 15:11:06 2006] received event "battery BAT1 00000080 00000001"
[Tue Sep 26 15:11:06 2006] notifying client 4471[108:108]
[Tue Sep 26 15:11:06 2006] executing action "/etc/acpi/power.sh"
[Tue Sep 26 15:11:06 2006] BEGIN HANDLER MESSAGES
[Tue Sep 26 15:11:06 2006] END HANDLER MESSAGES
[Tue Sep 26 15:11:06 2006] action exited with status 0
[Tue Sep 26 15:11:06 2006] completed event "battery BAT1 00000080 00000001"This occurs with the external power on or off. This constant writing to the log file (hundreds of kbytes long!) causes the drive to spin up and draining the battery badly.

I presume these "events" shouldn't be triggering all these actions - is there a way to either get acpi to handle them correctly, or failing that, to hack it by turning off the logging (which would at least keep the drive spun down)?

---

### Post by Argos_Bling on 2006-09-28
Talking to myself!

For the benefit of anyone searching for a "solution" to this problem, I have finally tracked down something that works for me - to the extent that I can now let my laptop hardrive spin down as it should.

acpid seems to use its own logging (seperate from the kernel and system logging deamons) which I couldn't find how to turn off. However there IS an option to specify the logfile to use, and I was able to set this to /dev/null. In the /etc/init.d/acpid file, change line 10
```
OPTIONS=""
```to```
OPTIONS="-l /dev/null"
```
Now when the system boots up, the acpid logs will now get dropped into /dev/null

Still not sure why this phantom "event" problem happens - it behaved very differently in Breezy, with the "event" being logged in the xorg logfile (which was MUCH easier to prevent hard drive access!).

---

### Post by CWW256 on 2006-10-22
I was having the exact same problem with a Toshiba Satellite.  From a fresh install the hard drive was making the "spinup" sound roughly every 30 sec.

Unlike the OP, I was not getting information logged to /var/log/acpid.

I was able to eliminate the constant spinup with ```
sudo hdparm -S 0 /dev/hda
```

I am not sure that this is the best fix, but it may give others with this problem another place to look.

---

