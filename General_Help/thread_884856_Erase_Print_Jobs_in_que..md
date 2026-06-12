---
title: "Erase Print Jobs in que."
date: 2008-08-09
forum: General Help
---

### Post by Roasted on 2008-08-09
I have an Epson CX4800. Love it, great printer. Ubuntu Hardy Heron.

I printed something last night. One page. But it keeps printing it out, over and over, and over. So I just turned the printer off.

Now, today, I need to print directions from google maps. I turn printer on... error button is flashing. I press it, bam... starts printing out the same page from last night.

I need to clear the que so I can print my directions. How do I do that? I used to have a print icon in the upper right corner and I could cancel jobs, similar to the page you see in XP. But I can't figure it out.

---

### Post by plucky on 2008-08-09
> **Roasted said:**
> I have an Epson CX4800. Love it, great printer. Ubuntu Hardy Heron.

I printed something last night. One page. But it keeps printing it out, over and over, and over. So I just turned the printer off.

Now, today, I need to print directions from google maps. I turn printer on... error button is flashing. I press it, bam... starts printing out the same page from last night.

I need to clear the que so I can print my directions. How do I do that? I used to have a print icon in the upper right corner and I could cancel jobs, similar to the page you see in XP. But I can't figure it out.

Open Firefox and put in the address bar ```
http://localhost:631/printers/
``` will get you to the CUPS interface for your printer.You should be able to clear the jobs in the printer queue.

Good Luck

---

### Post by Roasted on 2008-08-09
That's interesting. Is 631 the default printer port?

---

### Post by tacutu on 2008-08-10
```
lprm
```

if you hame more than 1 printer, ```
lprm -p PRINTERNAME
```

---

