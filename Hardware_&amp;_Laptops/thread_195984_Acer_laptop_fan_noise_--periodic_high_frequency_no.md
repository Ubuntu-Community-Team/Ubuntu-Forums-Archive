---
title: "Acer laptop fan noise --periodic high frequency noise"
date: 2006-06-13
forum: Hardware &amp; Laptops
---

### Post by boom2k1 on 2006-06-13
Hello all,

 I am hearing strange periodic (kind of high frequency) sound from the laptop in Ubuntu. It can be heard every half a minute or so.

I am not sure whether it is from the fan because there apparently is a much louder fan noise when the fan is operating at the full speed.

The problem does not exist in Windows XP.

I am using Acer 3502.
The laptop gets quite hot actually... (55-61 degree Celcius)

Does any acer users have the same problem?

How should I fix it?

Thanks!

---

### Post by andersonmanly on 2006-06-13
Are you using the i686 Kernel? If so, there seems to be an issue with frequency scaling using that version. When I loaded it onto my laptop (Pentium M, 1.73GHz) - it seemed to cause the CPU to run at full load the whole time, which caused to the laptop to get hot, in turn, causing the fan to kick on. I had to go back to the i386 kernel, as I could not find a solution to the problem.

---

### Post by boom2k1 on 2006-06-13
How do you tell if you are running on i386 or i686 kernel?

But I am more worried about the high frequency noise that would run regardless of what the temperature is!

Thanks~

---

### Post by andersonmanly on 2006-06-13
Open a terminal and type `uname -r`...your kernel version will be displayed. If it says 686 at the end, then you're running the i686 kernel. Perhaps the fan is only running at half speed?

---

### Post by boom2k1 on 2006-06-13
Thanks!

Do you think a laptop cooling pad might solve the issue?

---

### Post by andersonmanly on 2006-06-13
Was that the issue? Did you have the i686 kernel? If so, you might want to go install the i386 kernel, so that you can have full frequency scaling on the CPU...that way you won't be running hot all the time.

---

### Post by boom2k1 on 2006-06-14
I am using the 386 kernel, so I really don't know what happened..

I just bought a laptop cooling pad.
However, what is weird is, although the laptop feels cool, acpi -V reads that it is as hot as the temperature before I use the cooling pad!
doesn't make sense because i can feel so much cooler now!

---

