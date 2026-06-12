---
title: "Laptop won't hibernate at times"
date: 2007-07-23
forum: Hardware &amp; Laptops
---

### Post by Majorix on 2007-07-23
(I get a DB error when hitting tab from the title, so I don't know if there are relevant topics, sorry.)

Well the problem is that my computer won't hibernate at random times. Its set to hibernate when the lid is closed, but to my tough luck, it won't hibernate every time I do this. Just sometimes.

And since I can't usually know whether or not it is put to hibernate after closing the lid, I usually don't plug in the power, so after a few hours when I open the computer back again I find out that the battery is out.

The laptop is a Toshiba M70-215.

Any help is much appreciated.

Thank you.

---

### Post by Majorix on 2007-07-26
Today I experienced this problem: The computer seemed to have hibernated, the power leds were off. Then when I turned the computer back on, it didn't ask me for any password. It directly booted into Gnome and said "HAL failed to hibernate". Then keys locked off, mouse locked off. I couldn't do a thing. CAPS lock led was blinking. I finally did a hard reset and everything was ok again.

I don't know what causes this problem and I haven't got any replies in more than 2 days :(

Thanks.

---

### Post by Majorix on 2007-07-26
Can anybody help?

---

### Post by Majorix on 2007-07-26
Anyone?

I also reported this as a bug over at launchpad a few hours ago but noone replied there either...

---

### Post by shanix on 2007-07-27
Have you tried the method showing on the thread here?
[http://ubuntuforums.org/showthread.php?t=471855&highlight=2.6.20.16+hibernate](http://ubuntuforums.org/showthread.php?t=471855&highlight=2.6.20.16+hibernate)

Please let us know how it goes,

---

### Post by Majorix on 2007-07-27
Finally a reply! Haha!

But no, the method suggested doesn't work with me :(

---

### Post by Majorix on 2007-07-31
Come on, how do I hibernate by closing the lid? Did noone have the same problem before? :confused:

---

### Post by likpok on 2007-07-31
how big is your swap space, and how big is your ram? You can find out using the free command.

Hibernating works by suspending your ram to your swap (at least on my laptop), so if you don't have enough swap, sometimes it will fail.

---

### Post by scholzilla on 2007-07-31
I have the same problem with my Gateway MT-something or other running Feisty. It's frustrating because there seem to be so many proposed fixes in these threads that it's hard to know which one to try (if any). Incidentally, likpok, here's what free tells me:

             total       used       free     shared    buffers     cached
Mem:        897324     838320      59004          0     197000     265160
-/+ buffers/cache:     376160     521164
Swap:      2626588      38960    2587628


Does this tell you anything is in need of fixing?

Thanks!

---

### Post by Majorix on 2007-08-01
Results of free:
```
 total       used       free     shared    buffers     cached
Mem:        506916     456492      50424          0       6476     144464
-/+ buffers/cache:     305552     201364
Swap:      1477940      34600    1443340

```

I don't think it has anything to do with free swap space since I have more than enough to fit my ram in.

Any other ideas?

BTW I thought maybe updating the kernel would fix it... But no it didn't.

---

