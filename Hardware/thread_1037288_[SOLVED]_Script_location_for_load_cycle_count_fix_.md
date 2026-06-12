---
title: "[SOLVED] Script location for load cycle count fix on intrepid"
date: 2009-01-11
forum: Hardware
---

### Post by seemanta on 2009-01-11
Hi,

I have seen ubuntudemon's [***solution***]("http://ubuntuforums.org/showthread.php?t=805570") to the load cycle count issue for Hardy. I have Intrepid installed along with laptop-mode and pm-utils. I read somewhere that if laptop-mode and pm-utils are installed, copying the scripts into the location mentioned in the above thread will not help.

So vis-a-vis laptop-mode and pm-utils can someone please point me to some link which shows how to apply this so that it WORKS on Intrepid!

Shall I uninstall laptop-mode and pm-utils? Also I would be grateful if someone explains to me how laptop-mode, pm-utils and this HD issue are related to each other.

regards,
Seemanta

---

### Post by seemanta on 2009-01-12
Well, it seems the locations 

>  
/etc/acpi/resume.d/
/etc/acpi/start.d/
/etc/acpi/ac.d/
/etc/acpi/battery.d/

As quoted by ubuntudemon in [this original thread]("http://ubuntuforums.org/showthread.php?p=5031046") indeed seems to work for me. I have however, both laptop-mode and pm-utils installed on my system but still that did not interfere with applying this fix. Note that, I never did any fiddling with laptop-mode or pm-utils before and the above 4 locations seemed to work for me.
Actually, I modified ubuntudemon's original script by inserting additional lines like this:


```
#!/bin/bash
if on_ac_power; then
  # on AC so don't do any head parking
  hdparm -B 254 /dev/sda # you might need 255 or a different value
  [COLOR="Red"]**touch /tmp/resume.d.acfile #for debugging**[/COLOR]
else
  # either on battery or power status could not be determined
  # so quickly park the head to protect the disk
  
  # Using 250 for now. Using any value other than 254 causes parking to go mad!!
  hdparm -B 250 /dev/sda
  [COLOR="Red"]**touch /tmp/resume.d.battfile #for debugging**
fi[/COLOR]
```
 
That was the file copied in /etc/acpi/resume.d.

Similarly, I modified the file copied to /etc/acpi/start.d as:
```
#!/bin/bash
if on_ac_power; then
  # on AC so don't do any head parking
  hdparm -B 254 /dev/sda # you might need 255 or a different value
  [COLOR="Red"]**touch /tmp/start.d.acfile #for debugging**[/COLOR]
else
  # either on battery or power status could not be determined
  # so quickly park the head to protect the disk
  
  # Using 250 for now. Using any value other than 254 causes parking to go mad!!
  hdparm -B 250 /dev/sda
 [COLOR="Red"]** touch /tmp/start.d.battfile #for debugging**
fi[/COLOR]
```

I did the same for the files in the other two locations, ac.d and battery.d.

Notice the lines in red. Those lines are marker lines. After powering up/rebooting and resuming from suspend, I went to /tmp and check which file got created. That would tell me which script ran and which part of the if condition got executed.

Of course, you can also check by 
```
'hdparm -iI /dev/sda' 
```

But if you are paranoid like me, then you would want to see some tangible proof that the script did indeed run from the above mentioned 4 locations.
Which is where the above modifications come in handy.

regards,
Seemanta

---

