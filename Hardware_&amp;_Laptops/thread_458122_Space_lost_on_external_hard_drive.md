---
title: "Space lost on external hard drive"
date: 2007-05-29
forum: Hardware &amp; Laptops
---

### Post by nacnud on 2007-05-29
Hi all,

I just reformatted my 250 ext. hard drive to ext3, but noticed immediately that it now shows only 217 GB available.  I know that you never get the advertized amount, but 33 gigs seems a lot to lose.  

Before I reformatted I had 21 gigs of music on fat32, and the system told me I had about 211 left.  Now I have nothing on there and only 217 left.  Did I do something wrong with the formatting?

Thanks for any help.

Duncan

---

### Post by lyceum on 2007-05-29
It is posible you did something wrong, but I could not say what as I do not know what you did ;) I would try to re-format it again and see what happened. Are you using fat32?

---

### Post by nacnud on 2007-05-29
It was fat32 and is now ext3.  I formatted first with gparted, then with the mkfs command, both with the same result.  When I ran fdisk it said something about superblocks and 5% being kept aside for the superuser....

---

### Post by lyceum on 2007-05-29
That goes beyond my knowledge. It makes sence, but I see no reason why 5% (or any amount ) would need to go to superuser. Sorry I could not be more help.

Check this out though:

[http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html](http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html)

---

### Post by nacnud on 2007-05-30
Well, thanks for trying!

I did find this command [here ]("https://help.ubuntu.com/community/InstallingANewHardDrive")to modify reserved space:

```
sudo tune2fs -m 1 /dev/hdd1

```

But my empty 250g drive still shows up as 226.7g.  What the heck?!

---

### Post by lyceum on 2007-05-30
You can modify but not use it???? That blows my mind!

---

### Post by vishnumrao on 2007-06-05
I too have the same problem. I recently bought two 500 Gb Hitachi Sata drive. Formatted them to ext3. And I see that I have lost a lot of space. I lost about 30 Gb of space and 

```
sudo tune2fs -r 0 /dev/sda1

```

helped me get back some of my space. But I still see that about 7.5Gb of space is still missing. I formatted the drive to fat32 which gives me the unused space to the full of 465.76Gb. (I know a 500 Gb drive = actually 465.7 Gb) . But formatting in ext3 still takes away 7.5 Gb of space.

please see attached screenshot of the drive size after formatting to ext3 and then Gparted after running the above command.

 Any suggestions?

---

