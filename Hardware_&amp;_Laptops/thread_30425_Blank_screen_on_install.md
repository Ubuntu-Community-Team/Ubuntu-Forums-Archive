---
title: "Blank screen on install"
date: 2005-04-28
forum: Hardware &amp; Laptops
---

### Post by kzin602 on 2005-04-28
I have a gateway M675 [http://gateway.com/products/gconfig/proddetails.asp?seg=ed&system_id=m675eplb](http://gateway.com/products/gconfig/proddetails.asp?seg=ed&system_id=m675eplb) 

I created a second partition to install ubuntu onto then booted off the install CD,
the the ubuntu logo pops up with the boot: prompt.
I hit enter
a bunch of grey text scrolls past (too fast for me to see any possible error messages) then the screen goes black.

I suspect the monitor is out of range, but if it is it's not saying so (it dosen't if i take it out of range in windows).

Any suggestions? Perhaps a way to specify video options?
thanks

---

### Post by LinxNew on 2005-04-28
I have the same problem.

I think that there is a 'little bug' in our ATI graphics card: 9700.

I'm tring this tip: at the boot prompt i'm writing   vga=ask   and I try to find some video modes.

If you find waht work for you, please tell me.  ;-)

---

### Post by LinxNew on 2005-04-28
This is the solution:  vga=791 or 792

---

### Post by worldwidedvds on 2005-05-05
[QUOTE=LinxNew]This is the solution:  vga=791 or 792[/QUOTE]
 At the "Boot:" I typed:
linux vga=771

Worked for me.  JUST got it installed.  Now fighting like mad to get the Wifi card working.

---

