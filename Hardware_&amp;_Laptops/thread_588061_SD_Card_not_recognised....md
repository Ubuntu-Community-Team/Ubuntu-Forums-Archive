---
title: "SD Card not recognised..."
date: 2007-10-23
forum: Hardware &amp; Laptops
---

### Post by chrome101 on 2007-10-23
I've looked everywhere (sort of) for a solution to my problem and... failed! My Toshiba sp6100 does not recognise my sd-card (Fujifilm 512MB). Infact, it doesn't recognise any sd cards through the built-in card reader. On my Dell laptop its not a problem at all (both machines run ubuntu 7.04). Does a solution exist or do I have to upgrade to the next version of ubuntu?](*,)

---

### Post by fishyf on 2007-10-23
What is the output of the command
```
lspci | grep SD
```

---

### Post by chrome101 on 2007-10-23
This is what i get:

02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)

---

### Post by chrome101 on 2007-10-26
I take it nobodies got a clue then... Nevermind!!

---

### Post by MaximusTG on 2007-10-26
You need to load the tifm_sd module

```

sudo modprobe tifm_sd

```


Also see:
[http://www.infinity-ltd.com/mikkel/Toshiba.html](http://www.infinity-ltd.com/mikkel/Toshiba.html)

That uses the same SD controller.. Only supports SD cards though, didn't know that..

If that works, you have to add a line saying tifm_sd in /etc/modules, to make it load at boot.
Good luck!

Edit: Read some more on the web, not sure this will work anymore, but won't hurt to try of course

---

### Post by chrome101 on 2007-10-26
Thanks for that... Loaded everything fine and edited the /etc/modules... Rebooted system... But it didnt work... Looked at the other website too and I'll have to see what I can dig out of it.

---

