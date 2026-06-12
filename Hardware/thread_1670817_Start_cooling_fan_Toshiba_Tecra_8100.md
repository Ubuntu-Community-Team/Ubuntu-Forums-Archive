---
title: "Start cooling fan Toshiba Tecra 8100"
date: 2011-01-19
forum: Hardware
---

### Post by MasterFenrir on 2011-01-19
NOTE: I am sorry for double posting this topic, but something went wrong and the other one is empty. I also can not post a reply.

Good day,
I was planning to install Lubuntu on the laptop mentioned in the title.
It has a Pentium 3 700 mHz processor, 256 MB RAM and 10 GB HD.
But that's not the point. The point is, the fan won't turn on when the CPU gets too hot.
With Puppy Linux I had the same problem, and I don't want it to happen with Lubuntu, since it's probably based on software (I've read about that).
Now is my question, how can I fix this before installing Lubuntu? (Since the installation might take long, the laptop might die before it is finished).
Yeah, a LiveCD, but what should I do to make the fan work? I don't care if it's on all the time, or only when the CPU is getting too hot, no, as long as it works and I can use my laptop. Then I'm happy.
So, just to clarify, at this moment there isn't any OS on the laptop.

---

### Post by SteveDee on 2011-01-19
> **MasterFenrir said:**
> ...Yeah, a LiveCD, but what should I do to make the fan work? ....

You might like to research a possible solution that involves adding the line:-
```

GRUB_CMDLINE_LINUX="acpi_osi=\"Linux\""

```
...to the /etc/default/grub file.
I have a note on this but can't remember why this may be necessary on some laptops.

If you want to try it, I suggest you make a Lubuntu USB memory stick on another computer, edit grub to add this line, and then run:-
```

sudo grub-update

```

Now put the memory stick in your Tosh and boot from it.

---

