---
title: "Need static device entries for USB serial"
date: 2008-03-21
forum: Hardware &amp; Laptops
---

### Post by triddle on 2008-03-21
Hello,

I have several serial adapters hooked up to my Ubuntu machine via USB but I need to make sure that certain adapters always have static entries in /dev - I think this is done via devfs but I'm not sure how to make it happen. I read the man page on devfs but it's light on how to actually accomplish things with the rules syntax. Can you guys provide some pointers/examples on how I can assign a static path (even via symlinks, that's fine) to a USB serial device no mater what order it's actually enumerated on the bus?

Thanks!

Tyler

---

### Post by unutbu on 2008-03-21
Excuse me if I'm wrong -- I am by no means an expert. 

I think unique identifiers (UUID) were created to solve this problem.
If you look in /etc/fstab you should see some lines that look like

```
UUID=03a507ee-cdac-4bd9-b438-eccd616b66ed / ext3 defaults,errors=remount-ro 0 1
```

This is on my system equivalent to 
```

/dev/sda3 / ext3 defaults,errors=remount-ro 0 1
```

except that it has the added advantage that if for some reason the system decided my / partition should be called /dev/sdb3, my /etc/fstab will still be good and my system won't break. 

In your case, I think all you need to do is add entries to /etc/fstab which refer to your devices by UUID instead of by /dev paths.

---

### Post by triddle on 2008-03-21
That would work for hard drives but I need to do the same thing except for RS232 serial ports via USB.

> **unutbu said:**
> Excuse me if I'm wrong -- I am by no means an expert. 

I think unique identifiers (UUID) were created to solve this problem.
If you look in /etc/fstab you should see some lines that look like

```
UUID=03a507ee-cdac-4bd9-b438-eccd616b66ed / ext3 defaults,errors=remount-ro 0 1
```

This is on my system equivalent to 
```

/dev/sda3 / ext3 defaults,errors=remount-ro 0 1
```

except that it has the added advantage that if for some reason the system decided my / partition should be called /dev/sdb3, my /etc/fstab will still be good and my system won't break. 

In your case, I think all you need to do is add entries to /etc/fstab which refer to your devices by UUID instead of by /dev paths.

---

### Post by unutbu on 2008-03-21
Ok, sorry!

---

### Post by unutbu on 2008-03-21
Just so I know better next time, is your problem like this:

<Serial device> ---- <serial port A> ---- <USB port on computer>
<Serial device> ---- <serial port B> ---- <USB port on computer>

and you want something like /dev/sdb1 assigned to whatever device is connected to <serial port A> no matter which serial device it happens to be?

---

### Post by triddle on 2008-03-21
> **unutbu said:**
> Just so I know better next time, is your problem like this:

<Serial device> ---- <serial port A> ---- <USB port on computer>
<Serial device> ---- <serial port B> ---- <USB port on computer>

and you want something like /dev/sdb1 assigned to whatever device is connected to <serial port A> no matter which serial device it happens to be?

I think you've got it. I know it's got to be possible it's just not clear as to how to make it happen.

---

