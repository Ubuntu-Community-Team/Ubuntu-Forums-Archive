---
title: "Increasing swap size."
date: 2008-10-29
forum: General Help
---

### Post by fullmetalgerbil on 2008-10-29
I'm just wondering if it's like a big involved process to increase the memory swap size. I only have 486 Mb of RAM and I've been suffering some performance lags,and app crashing problems. So knowing there's not much I can do short of buying more memory I thought maybe increasing the size of the swap partition might help a little.
I'm just getting ready for bed right now so I wont be able to do anything until at least tomorrow, but if anyone thinks increasing the size of swap might help please let me know.
Thanks

---

### Post by Pelham123 on 2008-10-29
Do you know how much of your swap is used with your current specs?

Maybe worth monitoring your swap usage with the System->Administration->System Monitor while you run some Apps that put a strain on your system.

---

### Post by Nepherte on 2008-10-29
For systems with 512Mb or lower, a swap of two times the amount of memory is typically enough. How big is your swap?

---

### Post by rakris on 2008-10-29
check executing "top"

check excetuing "free -m"

What do u see?

then decide :P

---

### Post by fullmetalgerbil on 2008-10-29
I checked free -m. Under total swap it said 1419.

---

### Post by fullmetalgerbil on 2008-10-29
I guess I should add that when the system is idling (except for the terminal being open) it uses 417 of 486Mb total memory. Which seems rather high to me being that I thought Ubuntu only needed like 256Mb minimum to run.

---

### Post by Helge on 2008-10-29
> **fullmetalgerbil said:**
> I checked free -m. Under total swap it said 1419.

What are your total, used and free values for swap?

---

### Post by fullmetalgerbil on 2008-10-29
My swap total is 1419 with 57 used and 1362 available. Thats with a browser and terminal open. 
It seems like I have plenty of swap, but just with these two things open I'm using 474 of 486Mb of actual memory-and I'm not even running a memory voracious app like the GIMP, which I can only run when all my other programs are closed and it usually still crashes. 
I thought maybe if I expanded swap or somehow allocated more of the memory hungry work of my apps to using the swap, though I know things would run slower at least I might have less problems with crashes.
thanks,
Dave

---

