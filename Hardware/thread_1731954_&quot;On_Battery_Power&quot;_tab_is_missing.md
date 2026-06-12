---
title: "&quot;On Battery Power&quot; tab is missing"
date: 2011-04-17
forum: Hardware
---

### Post by Culinax on 2011-04-17
Hello,

I don't have the "On Battery Power" tab in Power Management.

[IMG]http://www.techotopia.com/images/2/2f/Ubuntu_10.10_laptop_power_management.jpg[/IMG]

So it's that tab on this image above that I don't have on my laptop. It's just "On AC Power" and "General".
Is that caused because Ubuntu doesn't recognize this as a laptop or is there a special Ubuntu version for laptops?


Thank you in advance,

Culinax

---

### Post by Culinax on 2011-04-19
Is there someone who can help me please?

---

### Post by Culinax on 2011-04-21
Is there really nobody who knows how to solve this problem?

---

### Post by Culinax on 2011-04-23
Last bump...

---

### Post by KegHead on 2011-04-23
Hi!

If I remember correctly, when you're using an electrical connection
it won't show.

Are you running on a battery or connection when you post this screenshot?

KegHead

---

### Post by Culinax on 2011-04-25
I didn't make this screenshot, I found it on Google images and used it to show which tab is missing.
And it never shows up, not when I'm on AC power and not when I'm on battery power...

---

### Post by jawilljr on 2011-04-25
I had the same problem, no "On Battery Power" tab.

What I did to fix it was to power down the laptop and remove the battery for about 5 minutes.

Plugged the battery back in and powered up. After it booted I now have the "On Battery Power" tab.

Hope this helps.

Jerry

---

### Post by Culinax on 2011-04-26
I read that in another thread too.
I removed the battery for about 15 minutes (I cleaned the inside and the fan meanwhile) and when I rebooted that tab was still missing.

Additional information:
I found in another thread that I have to type "dmesg | grep batt" in terminal.
I did that, and it says that my battery is absent:

```
[    0.444251] ACPI: Battery Slot [BAT1] (battery absent)
[    2.116514] ACPI Exception: AE_ALREADY_EXISTS, Evaluating _BIF (20100428/battery-406)
```

What should I do now or somebody has any other ideas to solve this?


Edit:
Link: [http://ubuntuforums.org/showthread.php?t=1565260](http://ubuntuforums.org/showthread.php?t=1565260)
They weren't able to solve the problem there though...

---

### Post by Culinax on 2011-05-01
My problem got solved with upgrading to Ubuntu 11.04.


Thank you everybody for helping me.

---

