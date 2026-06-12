---
title: "How to tell Max Ram per slot?"
date: 2009-07-26
forum: Hardware
---

### Post by conradin on 2009-07-26
HI all,
how can I tell what the maximum ram per slot is?
 I have tried:
```

sudo lshw

```

Which shows :
     *-memory
          description: System Memory
          physical id: 2f
          slot: System board or motherboard
          size: 768MiB
          capacity: 3GiB

is capacity per slot or total?
-Yes, Im aware I can prolly look it up on the motherboard manufacturer's website, I am just wondering if theres a way to get detailed specs on my hardware.

---

### Post by rodh on 2009-07-26
I think you would have to go to the web site of the company that made your Motherboard, Look up the specs on the Motherboard it should tell you what type and max size.

---

### Post by conradin on 2009-07-27
> **rodh said:**
> I think you would have to go to the web site of the company that made your Motherboard, Look up the specs on the Motherboard it should tell you what type and max size.

I hate to say it, but Microsoft has programs that can do this. What I have is a several labs, and class rooms with a variety of hardware searching out each manufacturer will be tedious.

---

### Post by wojox on 2009-07-27
capacity: 3GiB = total

size: 768MiB = add sizes of number of occupied banks

---

### Post by jerrrys on 2009-07-27
how bout

[http://ubuntuforums.org/showthread.php?t=588081](http://ubuntuforums.org/showthread.php?t=588081)

---

### Post by conradin on 2012-08-14
```
dmidecode
```
that does the trick! Marking as solved!

---

