---
title: "Share a Printer Over Network?"
date: 2010-10-29
forum: Hardware
---

### Post by csharpplus on 2010-10-29
Hi,

I am a newbie, so apologies if I am missing something obvious.

I have a printer that is connected (through a USB connection) to **computer1**. both  **computer1 ** and **computer2 **are connected to a switch through RJ45 cables (each computer has its own static IP).

Is there a way to 'allow' **computer2** to access the printer, print pages etc?

---

### Post by IcarusR on 2010-10-29
What OS do each of the machines run ?

Assuming they are both ubuntu...

On machine with local printer go to System >Administration >Printing & hilite your printer, then right click it & select 'Shared'
Then click on the Server menu then Settings & select 'Publish Shared Printers Connected To This System'

Now go to the other (client) machine & go to System >Administration >Printing & click 'Add' Ubuntu will search & find your shared printer & set it up for you.

---

### Post by csharpplus on 2010-10-29
I use Ubuntu for both -- this has worked perfectly. thank you!

---

### Post by arnavk007 on 2010-10-29
could you mark this thread as solved

---

### Post by csharpplus on 2010-10-31
I did. Thank you.

---

