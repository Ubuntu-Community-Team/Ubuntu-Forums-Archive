---
title: "Can't boot into ext4 partition"
date: 2009-07-16
forum: Installation &amp; Upgrades
---

### Post by Graeme2804 on 2009-07-16
Hi,

I have a ext4 partition of 9.04 on my laptop which takes up all but 15gb of space.

On the other 15gb I installed ubuntu 8.04 for testing etc. and now I can't boot into 9.04.

I can see the partition on Places->Computer->XGB Media but when I click on it says "The volume uses the ext4 file system which is not supported by your system."

When booting up my computer I don't get the option in the list of OS's to boot into the ext4 partition.

Any help is greatly received - I do not want to lose the data on that partition.

---

### Post by navaneethan on 2009-07-16
Hi 

Still now ext4 is not developed for GRUB .It is developed for only **/**

so you have to add one seperate partition for **/boot** in ext3

then it ll be successful try it

---

### Post by Graeme2804 on 2009-07-16
> **navaneethan said:**
> Hi 

Still now ext4 is not developed for GRUB .It is developed for only **/**

so you have to add one seperate partition for **/boot** in ext3

then it ll be successful try it


Hi,

Thanks for the quick reply.

I'm not exactly sure what you mean though?

I don't want to mess around with my partitions without knowing what I'm doing so if you could be more detailed that would be great!

Thanks again.

Graeme.

---

### Post by Sub101 on 2009-07-16
You could probably chainload from the initial bootloader in 8.04.

Maybe adding somethng like:

```
title Ubuntu9.04
    root (hd0,0)
    chainloader +1

```

But changing the root to the same as your 9.04 partition. The potential problem is whether it can read the second grub due to it being ext4. 

Other than that you would need to restore the 9.04 grub to become the one that is initially opened.

---

### Post by navaneethan on 2009-07-16
> **Graeme2804 said:**
> Hi,

Thanks for the quick reply.

I'm not exactly sure what you mean though?

I don't want to mess around with my partitions without knowing what I'm doing so if you could be more detailed that would be great!

Thanks again.

Graeme.

you have to create one more parition **/boot** in **ext3** using partition tool in ubuntu

you have spend atleast 2 GB for **/boot** in ext3

[ref]("http://navaspot.wordpress.com/2009/07/10/ext4s-intro/")

---

### Post by Graeme2804 on 2009-07-16
Hi,

Sorry, I don't know how to do either of the above.

---

### Post by navaneethan on 2009-07-16
> **Graeme2804 said:**
> Hi,

Sorry, I don't know how to do either of the above.


1.Go to ubuntu live CD mode

2.see the tool "Partition Editor" tool and select it 

3.Allot 2 Gb drive from free one seperately

4 Make that drive ext3 and try to allot /boot if it is not possible

 you have to reinstall it 

**/** in ext4
**/boot** in ext3
**/home** it is ur need

understand?

---

### Post by Graeme2804 on 2009-07-16
> **navaneethan said:**
> 1.Go to ubuntu live CD mode

2.see the tool "Partition Editor" tool and select it 

3.Allot 2 Gb drive from free one seperately

4 Make that drive ext3 and try to allot /boot if it is not possible

 you have to reinstall it 

**/** in ext4
**/boot** in ext3
**/home** it is ur need

understand?

Not really, lets see.

I create a new 2GB partition.
I change the ext4 filesystem to be an ext3 filesystem.
I install ubuntu 9.04 on the 2GB partition?

---

### Post by running_rabbit07 on 2009-07-16
:popcorn::)

---

### Post by Graeme2804 on 2009-07-19
> **navaneethan said:**
> 1.Go to ubuntu live CD mode

2.see the tool "Partition Editor" tool and select it 

3.Allot 2 Gb drive from free one seperately

4 Make that drive ext3 and try to allot /boot if it is not possible

 you have to reinstall it 

**/** in ext4
**/boot** in ext3
**/home** it is ur need

understand?

Just for everyone's reference in the future, I have done the quoted procedure and restored my lost partition.

Thank you guys.

---

