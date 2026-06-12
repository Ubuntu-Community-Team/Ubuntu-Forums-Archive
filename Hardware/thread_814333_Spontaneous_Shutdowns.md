---
title: "Spontaneous Shutdowns"
date: 2008-05-31
forum: Hardware
---

### Post by javagamer on 2008-05-31
Hi,
   Since just yesterday my computer has been shutting down without warning.  I've found a few things I can do which will guarantee this:
[LIST]
[*]Playing  Steam Games in Wine (takes a few minutes)
[*]Running memtest
[*]Running my MB's memory test
[/LIST]
I thought this could be a MB problem so I upgraded the BIOS on my nVidia nforce 780i to the latest version (PO5).  After this my computer continued to have the same problems as before.  I can't remember doing anything in between the time my computer worked fine and the time it started shutting down.  Any help would be appreciated.

---

### Post by ubukool on 2008-05-31
Hi, do you have a problem with your computer overheating?  I've had a couple of spontaneous shutdowns due to this.  There's a thread on this problem on the forum.

:)

---

### Post by hotweiss on 2008-05-31
> **javagamer said:**
> Hi,
   Since just yesterday my computer has been shutting down without warning.  I've found a few things I can do which will guarantee this:
[LIST]
[*]Playing  Steam Games in Wine (takes a few minutes)
[*]Running memtest
[*]Running my MB's memory test
[/LIST]
I thought this could be a MB problem so I upgraded the BIOS on my nVidia nforce 780i to the latest version (PO5).  After this my computer continued to have the same problems as before.  I can't remember doing anything in between the time my computer worked fine and the time it started shutting down.  Any help would be appreciated.

When this started happening to me, it was because of bad memory. Run memtest from the live CD for about an hour and see if you get any errors.

---

### Post by javagamer on 2008-05-31
ubukool: I doubt it would be an overheating problem since my case has nice cooling and the problem has just started recently and is very reproducible.

hotweiss: My computer shuts off in the middle of a memory test regardless of where it's from, MB, Grub, Live CD.  Is it possible that this is because of bad RAM, and is there a way to tell for certain?

---

### Post by hotweiss on 2008-06-01
> **javagamer said:**
> ubukool: I doubt it would be an overheating problem since my case has nice cooling and the problem has just started recently and is very reproducible.

hotweiss: My computer shuts off in the middle of a memory test regardless of where it's from, MB, Grub, Live CD.  Is it possible that this is because of bad RAM, and is there a way to tell for certain?

Just buy new memory and put it in. I'm 99% sure it's your memory.

---

### Post by javagamer on 2008-06-01
I just burned the latest memtest86+ onto a disc and ran it.  Apparently my memory is fine.
Is it possible that my computer just recently started overheating?  When I check the CPU temperature from the BIOS some times it's excess of 100C.  Is that possible?
I have all my fans in my case hooked up and a stock cooler on it.  I haven't overclocked anything, though my graphics card was already overclocked.  The case I have is supposed to have really nice cooling.
Should I look into a better CPU fan, or should I run memtest again?
Also, I think the spontaneous crashes went away when I enabled the 2 modes of temperature control on the CPU.

---

### Post by hotweiss on 2008-06-01
> **javagamer said:**
> I just burned the latest memtest86+ onto a disc and ran it.  Apparently my memory is fine.
Is it possible that my computer just recently started overheating?  When I check the CPU temperature from the BIOS some times it's excess of 100C.  Is that possible?
I have all my fans in my case hooked up and a stock cooler on it.  I haven't overclocked anything, though my graphics card was already overclocked.  The case I have is supposed to have really nice cooling.
Should I look into a better CPU fan, or should I run memtest again?
Also, I think the spontaneous crashes went away when I enabled the 2 modes of temperature control on the CPU.

Those CPU's are designed to work to about 72 degrees Celsius. So if your temperature is 100, the heat is most likely your problem. Is your fan working properly? Did you put too much thermal paste between your CPU and heatsink? Try restoring your motherboard defaults if you played around with them.

---

### Post by javagamer on 2008-06-01
The problem was I didn't have any thermal paste.  I assumed that since I was just re-adjusting the fan (since it was loose) I could just use what was already on there.
When I went out and bought some thermal paste the temperature dropped between 1/2 and 1/3 of what it was.  As I type this I'm idling at 45C.

---

### Post by hotweiss on 2008-06-01
> **javagamer said:**
> The problem was I didn't have any thermal paste.  I assumed that since I was just re-adjusting the fan (since it was loose) I could just use what was already on there.
When I went out and bought some thermal paste the temperature dropped between 1/2 and 1/3 of what it was.  As I type this I'm idling at 45C.

LOL, OK problem solved.

---

