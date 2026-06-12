---
title: "printer samsung , ml 1610"
date: 2007-09-28
forum: Hardware &amp; Laptops
---

### Post by deepinlife on 2007-09-28
guys i have xubuntu fesity.
i have Samsung printer ml 1610 usb.i have another linux installed mandrivia2007
i can't install on teh xbuntu but i can on mandrivia..
i checked the driver in teh GUI tools provided in the menu , tehy all say that everything is ok , teh driver is there and jobs go to it , but it has stooped status , why is that ?
i can print normally on mandrivia , and even i printed once using Xubuntu but after taking teh driver off , it don't want to print again , for sure i have reinstalled teh driver but in vain ?

---

### Post by Linicks on 2007-09-28
I have a ml-1610 and it works fine.  Although I have my printer installed on my Slackware box using CUPS, and from my laptop I just pointed to the box, told it what the printer was, slected port to use, and that was it.

So this printer works OK.

How are you using it?  CUPS?

Nick

---

### Post by deepinlife on 2007-09-28
well i don't know if i m using Cups or not , but i think so ..
i used it well on slackware too..and now it works fine on mandrivia..
but some problems on Ubuntu ?
how to know if am  i using Cups ?

---

### Post by Linicks on 2007-09-28
Open up firefox and goto:

[http://localhost:631/](http://localhost:631/)

Nick

---

### Post by deepinlife on 2007-09-28
it was so good to see how to configure teh printer ..
here what i got.

Samsung (Default Printer) "Could not find a suitable printer!"

i don't know why it says "Could not find suitable printer" ??

---

### Post by Linicks on 2007-09-29
Well, what I would do is remove the printer totally and then run through the CUPS interface to set it up again.

Nick

---

### Post by deepinlife on 2007-09-29
nothing changed the same thing..
it says ok , then when i try to print , "printer couldn't found" ?

i just log to mandrivia and print , so everything is ok but on mandrivia

---

### Post by Linicks on 2007-09-29
I don't know - reading up, it could be a bad driver you have selected.

In CUPS manage printers, this is what I have:

```
Description: ML-1610
Location: Here
Make and Model: Samsung ML-1610 Foomatic/gdi
Printer State: idle, accepting jobs, published.
Device URI: http://192.168.1.23:631/printers/samsung
```

Can you post your similar lines too?

Nick

---

### Post by deepinlife on 2007-09-29
```

Samsung (Default Printer) "Could not find a suitable printer!"
Description:
Location:
Make and Model: Samsung ML-1610 Series (SPL II)
Printer State: idle, accepting jobs, published.
Device URI: usb://Samsung/ML-1610

```

---

### Post by Linicks on 2007-09-29
I am sorry - I don't know.

But it really looks like the printer is not found on the system, and you have entered the details rather than as CUPS detects it.

?

Nick

---

### Post by deepinlife on 2007-09-29
Linicks thank u for ur effort for me..

---

### Post by Linicks on 2007-09-29
OK, look!  You have different driver than me!

Me:

```
Make and Model: Samsung ML-1610 Foomatic/gdi
```

You:

```
Make and Model: Samsung ML-1610 Series (SPL II)
```

So, go to localhost:631/

Manage Printers->Modify Printer

and when you get to the driver, select:

'Samsung ML-1610 foomatic/gdi (en)

Lets see what that does.

Nick

---

### Post by deepinlife on 2007-09-29
it signal error message and say that no printer ..i mean when i try different model.
by the way this driver is the one came with the printer , it is the one i used in all linuxs ,and also i tried the built in driver in the ubuntu itself..

---

### Post by Linicks on 2007-09-29
OK, sorry then, I don't know without being at the keyboard/machine to see what is going on.

Nick

---

