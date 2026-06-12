---
title: "fglrx &amp; powerstates"
date: 2006-06-06
forum: Hardware &amp; Laptops
---

### Post by kreso on 2006-06-06
when I'm using dual head, I can't clock down my laptop's display card (Ati mobility radeon X600).

I'm using aticonfig --set-powerstate=1

When I'm connected to only one display, it allows me to clock the display card, thus save batter power significantly and reduce heat generation.

is there a workaround other then using only one screen?

---

### Post by t0mc4t on 2006-06-06
Sorry for not answering but asking..
What is powerstate? What is the default value? Since I see that you want to change it into 1.
I'm using Radeon Xpress 200M, do I also have the powerstate property?
Thanks..

---

### Post by kreso on 2006-06-06
if you set the powerstate to 1, your display card will work slower, but will consume much less power and won't generate as much heat. This is obviously very usefull for laptops :)

In windows, this is called "POWERPLAY(tm)"

---

### Post by t0mc4t on 2006-06-06
Ic... thanks for the explanation..
Anyway.. what is the default value for that? Can we see the information by typing some command on console?

---

### Post by kreso on 2006-06-06
well, the default power state is 2, meaning full power.

you can verify it if you have fglrx and aticonfig installed.

commands: 

aticonfig --lsp to list powerstates &
aticonifg --set-powerstate=NUMBER to set it

---

