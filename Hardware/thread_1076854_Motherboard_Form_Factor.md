---
title: "Motherboard Form Factor"
date: 2009-02-21
forum: Hardware
---

### Post by Pyro.699 on 2009-02-21
Hello,

Ive recently come into the possession of a motherboard with the dimensions 8" wide and 9.5" long and couldn't find out which form factor it was. Looking on Wikipedia i found one which was close (203mm by 244mm) but i didn't think that "coming close" really cut it when looking for a case to screw them into. If i was to guess it would be DTX (the 203mm by 244mm). The motherboard is currently running without a case and is jut sitting on my table, it has linux running on it. How would i be able to figure out the name and model of the motherboard, **lspci** didnt help because it just listed the pci devices on the system.

Thanks
~Cody Woolaver

---

### Post by cariboo on 2009-02-21
I would suggest installing lshw-gtk, it is in the repositories. It won't create a menu item, so you'll have to do it yourself, or just press Alt-F2 and type:

```
gksu lshw-gtk
```

This should give you at least the model number of the motherboard. See Screenshot

Jim

---

### Post by Pyro.699 on 2009-03-01
Ok, i found my motherboard:

[http://www.msicomputer.com/product/p_spec.asp?model=K9MM-V](http://www.msicomputer.com/product/p_spec.asp?model=K9MM-V)

And i was wondering if it would work with this case:

[http://www.newegg.ca/Product/Product.aspx?Item=N82E16811121039](http://www.newegg.ca/Product/Product.aspx?Item=N82E16811121039)


The form factors match up, but its always good to check things out :)

Thanks guys
~Cody Woolaver

---

