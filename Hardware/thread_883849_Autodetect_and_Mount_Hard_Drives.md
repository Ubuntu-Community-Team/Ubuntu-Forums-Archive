---
title: "Autodetect and Mount Hard Drives?"
date: 2008-08-08
forum: Hardware
---

### Post by bzaks on 2008-08-08
I am trying to create a script that will go on my customized ubuntu live CD that will automatically detect and mount the hard drives (this is going to be a CLI only CD). I was wondering where I could find the logic that ubuntu uses to autodetect the hard drives in the first place?

If I were to guess on how it works: it would be grepping an ls on /dev/((h|s)d*) 

Then after I find the /dev/((h|s)d*) I could use the flavor ($1, right?) to grab the name of the device to mkdir for a mount?

---

### Post by sisco311 on 2008-08-08
never mind

---

### Post by bzaks on 2008-08-11
So after playing around a bit today, I found I can get my listing using grep, and its really easy to pull what I want into a physical list...

> ls /dev | grep -e "^[s|h]d[0-9]$"

Of course, then the problem is, how do I capture that output into an array or something so I can utilize it and mount it. I'm looking into 'for' in the command line.

---

### Post by sayad on 2008-08-11
TRy this one.

fileName = "auto detect" 
ide1:0.deviceType = "cdrom-raw" floppy0.

---

### Post by bzaks on 2008-08-19
Isn't that configuration lines for VMWare? Or Am I confused?

---

