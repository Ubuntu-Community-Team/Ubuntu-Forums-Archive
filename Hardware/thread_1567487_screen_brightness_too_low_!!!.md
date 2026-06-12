---
title: "screen brightness too low !!!"
date: 2010-09-03
forum: Hardware
---

### Post by rebrov on 2010-09-03
just installed ubuntu 10.04 and at booting the brightness going so low and stay on that after i login ..and thats annoy me 

i got command from google to make the brightness higher and it worked fine but when i restart again every thing back to normal and brightness still so low ...i have to type the same command again 

is there anyway to do this command at startup ! ?

---

### Post by kja999 on 2010-09-04
you could add it into the /etc/rc.local file, before the exit command

---

### Post by rebrov on 2010-09-04
> **kja999 said:**
> you could add it into the /etc/rc.local file, before the exit command

ahaa i got that :) 

do u think that i can fix my IP & mac also by this tip because i tried it on /etc/rc.local but didn't work

or should i put the command in specific line in rc.local ? 

or anywhere be4 "exit" will work ?

---

### Post by kja999 on 2010-09-04
You wouldnt fix an IP in rc.local, for that you need /etc/network/interfaces.

Google linux static IP for many instructions on this

---

### Post by rebrov on 2010-09-04
> **kja999 said:**
> You wouldnt fix an IP in rc.local, for that you need /etc/network/interfaces.

Google linux static IP for many instructions on this

> **kja999 said:**
> You wouldnt fix an IP in rc.local, for that you need /etc/network/interfaces.

Google linux static IP for many instructions on this

i know this about /etc/network/interfaces :) 

but my problem was not static even with adding my ip address at 
/etc/network/interfaces script

anyway i fixed this & the brightness both with adding it to startup at /etc/init.d/rc.local

SOLVED

---

