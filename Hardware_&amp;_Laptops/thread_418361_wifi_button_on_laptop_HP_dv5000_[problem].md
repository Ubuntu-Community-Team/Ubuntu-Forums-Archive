---
title: "wifi button on laptop HP dv5000 [problem]"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by aj2r on 2007-04-22
Hi and excuse my English. 

I have installed Kubuntu Feisty Fawn in my laptop Hp dv 5000, all it´s ok, but the wifi button does not work and i cant connect to my wireless network. ¿Anybody can help me?¿How can i activate this botton?

Thank you very much.

---

### Post by rivera151 on 2007-04-22
You probably have a broadcom wifi card.

Type in the console:
```

lspci | grep Broadcom

```

If this is true, then use [this tutorial]("http://ubuntuforums.org/showthread.php?t=197102").  Note that if you are running a 64 bit OS on an AMD 64 processor, you will have to get a vanilla kernel before you try this fix.

Hope that helps.

---

### Post by aj2r on 2007-04-22
Yes, i have a Broadcom wifi card. Thank you for the answer, im gonna try it now.

---

