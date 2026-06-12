---
title: "Ubuntu Boots Imediatly After Suspending"
date: 2016-08-29
forum: Hardware
---

### Post by harrispartyof3 on 2016-08-29
I've had this problem since 12.04 on only this laptop. The issue is when the laptop tries to suspend everything goes as expected but as soon as it powers off (indicator leds turn off) everything comes right back on and resumes as if the power button was pressed. The only clue to this problem is a low level error message that shows up in tty1 after the computer comes back on.
```

[796.356090] [Firmware Bug]: cpu 0, try to use APIC500 (LVT offset 0) for vector 0xf9, but the register is already in use for vector 0x400 on another cpu
[796.356091] [Firmware Bug]: cpu 0, failed to setup threshold interrupt for bank 4, block 0 (MSR00000413=0xc000000001000000)
[796.356092] [Firmware Bug]: cpu 0, try to use APIC500 (LVT offset 0) for vector 0xf9, but the register is already in use for vector 0x400 on another cpu
[796.356093] [Firmware Bug]: cpu 0, failed to setup threshold interrupt for bank 4, block 1 (MSR00000408=0xc000000001000000)

```
it is clear what the problem is, ubuntu is trying to use something that is already in use by something else. The only other solutions I have found have been:
>install the proprietary drivers
  supposively the problem is caused by the default drivers not accessing the right components to allow a proper suspend, this made sense so I gave it a shot
  the only driver that showed up in the additional drivers was a bullet labeled "Using Processor microcode firmware for AMD CPUs from amd64-microcode (proprietary)"
  the device that this driver was for was labeled as "Unknown: Unknown"
   obviously this did not fix the problem, no noticeable change in anything

>remove the usb devices
  the theory behind this was the usb devices were waking the system, this also made sense
  only issue is there are no connected usb devices other than the internal components of the laptop
   didn't fix the problem since there was nothing to remove

The problem seems to be quite simple but has a solution that is quite complex, and way over my head, any insight or guesses would be appreciated, thanks.

---

