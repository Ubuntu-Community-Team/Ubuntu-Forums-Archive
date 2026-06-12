---
title: "Ubuntu 8 does not open"
date: 2008-09-23
forum: General Help
---

### Post by sowhat12345 on 2008-09-23
I have bought a new computer. I installed Windows XP first properly. Then I tried to install Ubuntu 8.04 but just after the loading bar get fulled , the white screen comes and the progress did not go on. This mentioned white screen remains permanently and installation progress does not go on. In the end I'm forced to reset my computer. I face the same problem when I try to open Ubuntu with live CD.
My hardware configuration is:

Intel QuadCore Q6600 2.4
2X 1024 Kingston Ram 800 mhz
Maxtor 250 GB 7200 rpm SATA Harddisk
Gigabayt GA-P35-S3G Mainboard
Powercolor PCX 1GB HD3850 256bit VGA
Feel Horrucane 2 0508bs fl460 case
samsung 20x sata dvdrw
Creative live 7.1 audigy 2

By the way I try it with 3 different cd s which I had copied.

Thanks a lot...

---

### Post by spiderbatdad on 2008-09-23
Did you check the integrity of the cd? You might try a different mirror if the cd is bad, or burn again at a slower speed. Also see testing the md5sum before burning a bad file to disk.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If the problem persists, and cannot be attributed to the cd, you might try the alternate cd for hardware compatibility.

---

### Post by sowhat12345 on 2008-09-23
The cd does not have any problem. Because now I tried it in a computer of my friend. It works properly.

---

### Post by spiderbatdad on 2008-09-23
you might try this: press F6 at the start up screen for other options. If a dialog window opens, go ahead and escape it. Then delete the words "quite splash --" from the end of the boot line on your screen.
There may be specific boot options that will allow ubuntu to boot on your system, but it is a little bit of trial and error. noapic or acpi=off are common ones.
Deleting quiet splash will get you started in a verbose boot, so that you might be able to see where the boot is hanging.
See here for a little more on boot options.
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

There are a great number of options. The wiki doc only touches on a few. Google is your friend on that one.

---

### Post by sowhat12345 on 2008-09-23
I open it with safe graphic mode . It works :) Thanks for helping me . 

Now I am thinking about if I have to a swap partition ? My computer is fast but I don't know if I must open a new partition for swap? Can you help me about it ? I am waiting for install your answers ?

---

### Post by spiderbatdad on 2008-09-23
swap will be created if you allow guided partitioning if you partition yourself you should create a swap partition. Opinions vary a little as to the size. Generally  nram = 2*nswap up to 2 gigs, I think. Check here for more info on swap size. [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

