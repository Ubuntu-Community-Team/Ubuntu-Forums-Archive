---
title: "suspend issues with docking station on HP elitebooks?"
date: 2010-09-03
forum: Hardware
---

### Post by arsenix on 2010-09-03
I just got a new HP Elitebook 8540w.  In general things have been working pretty smoothly under linux.  I'm running Xubuntu 10.04, 64 bit.  One of the more annoying issues I'm having is that the machine will not wake out of suspend if the docking status changes while it is sleeping.  IE: If I am docked, suspend the machine and then wake it up out of the dock... it does not wake.  Same thing happens if I am undocked and wake it up in the dock.

Anyone else having this issue?

Looking at the kernel logs it looks like the machine is not coming back at all when it fails to resume.  There is nothing in the logs that indicates that the machine woke at all.  The logging from the suspend looks just fine, which makes sense since it suspend/resumes just fine if the docking station isn't involved.

It is possible that this happens under windows as well (I never booted it into windows so I'm not sure), in which case it could be a BIOS bug.  Workaround is eject before suspending... and wake before docking.  Sometimes I forget though (doh).



James

---

### Post by arsenix on 2010-09-07
I made an interesting discovery this morning on this front.  After I dock the machine when it is suspended, the machine powers up but is unresponsive.  If I then undock and redock... the machine wakes up.  It wakes perfectly, but X has been killed and the machine is waiting at the xdm login screen.

No timestamps in the X log file, but this is the last message:
  ddxSigGiveUp: Closing log


James

---

### Post by kc8ipw on 2011-11-27
I spent quite a bit of time looking into this issue (a very educational experience) and finally found an answer.  

I'm not entirely sure of the root cause but I know it's related to the to the ACPI EC interrupt.  I'm not sure if it's an interrupt storm(which I thought the kernel would catch), something causing the interrupt handler to hang, or something else entirely.  I did a lot of work with PM_TRACE tracing through the kernel and the resume process hangs as soon as interrupts are re enabled.  

If the ACPI EC interrupt is disabled before suspend and re enabled after resume the suspend process is successful.  I'm not sure if there are side effects yet as I've not used the system in this configuration very long. 
 
The method I used to disable the interrupt was to put the following in an executable file in /etc/pm/sleep.d/
```

#!/bin/bash
case $1 in
    suspend)
        echo disable > /sys/firmware/acpi/interrupts/gpe16
        ;;
    resume)
        echo enable > /sys/firmware/acpi/interrupts/gpe16
        ;;
esac

```

As this machine (like many from HP) has been known to have a buggy BIOS in the past I suspect this is just another BIOS bug.  I wouldn't normally even be using an HP as I don't want to support a company which does BIOS white listing.  They gave me this machine for work, but let me put whatever OS I wanted on it.  For those thinking of getting this machine, look elsewhere if you can and don't buy HP workstations.

---

