---
title: "Thinkpad failing suspend"
date: 2005-03-23
forum: Hardware &amp; Laptops
---

### Post by jalexstark on 2005-03-23
On the whole Ubuntu does well on my Thinkpad T20, but suspend is awful, and actually a bit deceitful in a way.

Has anyone got Warty to work _properly_ with a T20, ie including suspend?


Previously I've had Mandrakes and Knoppix working fine with all three Fn-triggered suspends.  (Albeit with varying DVD playback mileage thereafter.)

Sometimes suspend partially works under Ubuntu.  But it is lying to me.  My laptop behaved as if suspended to memory, and later I noticed the fan on, and it was warm.  And it didn't resume.

This might render Ubuntu useless to me.

I have followed various instructions.  /etc/modules has apm, for instance.  Latest (386) kernel.  I have read claimed successful installs on T20s, but question if they can get suspend to work, since some people have different ideas of success.  No dmesg or /log/messages info of interest.


(Plus I notice writing this that firefox-bin is using an infeasible consistent 3.7% and above.  And the fan is on...)

/Alex

---

### Post by LadyRoot on 2005-03-31
I have T21 and the only thing I have to do for my laptop working properly is turning off acpi and rely on apm only.
(in lilo.conf add append="acpi=off" if you are using lilo).
If I won't do it, many things fail to work, e.g. no network cards are detected.

greetings

---

### Post by jalexstark on 2005-12-08
There are still problems with Breezy, and, yes, I have "acpi=off"

This aspect is really not impressive.  The most obvious problem is delays in launching applications smelling rather of timeout waits.

/Alex

---

