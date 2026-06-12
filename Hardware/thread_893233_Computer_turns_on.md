---
title: "Computer turns on"
date: 2008-08-18
forum: Hardware
---

### Post by kimmelj on 2008-08-18
Hi,

Because my Windows Desktop computer ran verry slow, I decided to start using Ubuntu. Wow, this runs great on an older machine.

There is one issue to which I am not familiar.
Suddenly unexpected during the day my computer turns on. Even when I am not at home.

I am not that familiar with Ubuntu/Linux to dig deeper on this issue but I suspect it has something to do with Wake up On LAN. 

How to nail down this problem?

Regards,

Jasper Kimmel

---

### Post by jualin on 2008-08-18
Check the BIOS option "Wake up On Lan"

---

### Post by kimmelj on 2008-08-18
Jualin,

Thanks for the reply. I am sorry that I did nog mention this before but I already checked the BIOS. No such option there.

Also remind that I am suspection WOL. I am absolutely not sure if this is the cause.

---

### Post by jualin on 2008-08-18
Usually when a computer turns on by itself Wake up on Lan is related. Maybe someone else on the forum can confirm this.

---

### Post by finito on 2008-08-18
Some motherboards have a wake up alarm, like Wake up at 10:00 am everyday.

but you to set it up, 

Some computers have wake on Power Out. Basically if there is a sudden power outage and power comes back again to wake up. This seems to wake the machine up even if it was not switched on before.

One easy way to check for this is, to basically pull the AC wire from behind the Power supply and replug it.

Hope this helps.

---

### Post by spacedoggy on 2008-08-18
also check bios for serial devices, modems and wake a pc also

---

### Post by kimmelj on 2008-08-19
Thanks all. Rechecked the BIOS and disabled the internal modem, just to be sure. Also found a setting about how to react when a power faillure occurs. This was set to Power Off, so this is not the case either.

Let see how it reacts now.

---

### Post by jualin on 2008-08-22
Keep us posted.

---

### Post by kimmelj on 2008-09-14
Hi,

I found out that the computer only turns unexpectedly on when it is powered down by Ubuntu via the shutdown button in the top right corner of the screen.

Ofcourse, when holding the power button for 10 seconds while Ubuntu is running turns the computer also off. When I do this, the computer never turned on by itself so far.

Regards,

Jasper

---

### Post by carrotski on 2008-09-15
Hi,

I also seem to have the same problem since installing ubuntu at the weekend. I've checked the bios settings and nothing seems to be set to auto power on. I haven't tried shutting down from windows since but will try tonight and see if the problem re-occurs.

---

### Post by skymera on 2008-09-15
Unplug it

---

### Post by kimmelj on 2008-09-15
With all due of respect, what do you mean by Unplug it?

Unplug the power cord?

---

### Post by kimmelj on 2008-09-15
> **carrotski said:**
> Hi,

I also seem to have the same problem since installing ubuntu at the weekend. I've checked the bios settings and nothing seems to be set to auto power on. I haven't tried shutting down from windows since but will try tonight and see if the problem re-occurs.

Although I never had this problem with Windows on the same machine before, I am looking forward to the results of your tests.

Thanks.

---

### Post by Sillywombat on 2008-09-15
> **kimmelj said:**
> Although I never had this problem with Windows on the same machine before, I am looking forward to the results of your tests.

Thanks.

Same, please keep us posted on this.
Been having this problem for a while. Comming back home and getting a pc waiting for me. Will be eager to see how one will deal with this.

---

### Post by carrotski on 2008-09-16
Well I shut down from windows last night and the PC was still off this morning so it would seem this problem is related to ubuntu.

---

### Post by kimmelj on 2008-09-16
> **carrotski said:**
> Well I shut down from windows last night and the PC was still off this morning so it would seem this problem is related to ubuntu.

I totaly agree with this one.

---

### Post by carrotski on 2008-09-17
I think I may have found a fix. This thread [http://ubuntuforums.org/showthread.php?t=683530](http://ubuntuforums.org/showthread.php?t=683530) suggests entering the following at the terminal:

sudo sh -c "echo '2030-01-01 01:01:01' > /proc/acpi/alarm"

This should set it to wake a long way in the future. I tried this myself last night and the PC was still off this morning.

---

### Post by kimmelj on 2008-09-30
> **carrotski said:**
> I think I may have found a fix. This thread [http://ubuntuforums.org/showthread.php?t=683530](http://ubuntuforums.org/showthread.php?t=683530) suggests entering the following at the terminal:

sudo sh -c "echo '2030-01-01 01:01:01' > /proc/acpi/alarm"

This should set it to wake a long way in the future. I tried this myself last night and the PC was still off this morning.

To bad, this did not help either. Any other ideas, anyone??

---

