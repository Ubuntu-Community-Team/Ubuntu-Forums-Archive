---
title: "hp dv6255us boot problem"
date: 2007-06-26
forum: Hardware &amp; Laptops
---

### Post by ganglia on 2007-06-26
hp dv6255us model laptop didn't boot with ubuntu 7.04. I tried with some boot options mentioned here 
[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29?highlight=%28dv6000%29](https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29?highlight=%28dv6000%29)
but it hangs at gnome window manager step.
I tried Linux Pardus then it had succesful boot but this time it has some trouble with sound card (all other devices except wireless of course worked good), 
in addition i preffer ubuntu :)
unfortunately there is no help in ubuntu with this laptop.
Any help would be appreciated.

---

### Post by Ayuthia on 2007-06-26
Which options have you tried?  I have a dv6338se and it starts with 'noapic nolapic'.  Out of curiosity, where does it stop when you use 'noapic nolapic'?  Can you try that out and also remove the quiet option so that you can see where it stops?

---

### Post by ganglia on 2007-06-27
thanks a lot :)
noapic nolapic
works.

but previously I tried
NOAPIC NOAPCI NOIRQPOLL NOSMP  
boot options, these didn't worked.

---

