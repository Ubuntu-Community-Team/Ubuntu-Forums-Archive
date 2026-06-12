---
title: "Installing Ubuntu on a Vista machine"
date: 2008-09-13
forum: Hardware
---

### Post by Sathed on 2008-09-13
I have a question.  I'm fairly new to Ubuntu.  I have the desktop version running one of my machines at home, but I want to dual boot it on my laptop.  I've already checked the specs on my laptop for compatibility with Ubuntu and everything is good to go.  However, I don't want to re-image and create a new partition on my installation I have now of Vista.  Is there a way to create partition for Ubuntu after Vista is already installed and running?  And if so, how?

~Sathed

---

### Post by Steve1961 on 2008-09-13
> **Sathed said:**
> I have a question.  I'm fairly new to Ubuntu.  I have the desktop version running one of my machines at home, but I want to dual boot it on my laptop.  I've already checked the specs on my laptop for compatibility with Ubuntu and everything is good to go.  However, I don't want to re-image and create a new partition on my installation I have now of Vista.  Is there a way to create partition for Ubuntu after Vista is already installed and running?  And if so, how?

~Sathed


You should be able to shrink the vista partition to make room for ubuntu from within vista itself.  See this link:

[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

Then just install ubuntu to the free space.

---

### Post by Sathed on 2008-09-13
After I create the new partition, do I need to format it with Vista?  If so, what is the best type of format?

---

### Post by mrsteveman1 on 2008-09-13
> **Steve1961 said:**
> You should be able to shrink the vista partition to make room for ubuntu from within vista itself.  See this link:

[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

Then just install ubuntu to the free space.

Sometimes Vista refuses to shrink beyond a certain amount, and it seems arbitrary. For instance my laptop has Vista in a 60gb partition, nothing installed so most of that is free space, but Vista won't take more than 800mb off of that partition even after a defrag.

The Ubuntu installer though can usually resize it as far down as you want it to.

---

### Post by Steve1961 on 2008-09-14
> **Sathed said:**
> After I create the new partition, do I need to format it with Vista?  If so, what is the best type of format?


When you've shrunk your vista partition with the vista tools or the ubuntu cd (both can do it, but as the previous poster stated, vista partition tools may have limitations) just let ubuntu create the partitions it needs in the free space.  Before you shrink the partition, however, defrag it fully and of course back up all your data just in case....

---

