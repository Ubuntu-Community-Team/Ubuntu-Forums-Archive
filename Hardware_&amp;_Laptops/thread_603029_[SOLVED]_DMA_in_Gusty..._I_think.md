---
title: "[SOLVED] DMA in Gusty... I think?"
date: 2007-11-04
forum: Hardware &amp; Laptops
---

### Post by b3n87 on 2007-11-04
I think I have the jerky playback fixed

basicly I had to find out the name of the device that was slow, in my case it was a SATA dvd player on my laptop

in terminal i did

```

 gedit /etc/fstab

```

my device was called

/dev/scd0

edit the /etc/hdparm.conf file and add

/dev/scd0 {
    dma = on
}


now edit /etc/modules and add these too the TOP of the list of modules

piix
ide-core


another thing i have actived in the options is under System>Administration>Services
theres something called HD tuning, i enabled that

now restart the laptop/pc and it "should" work.

remember, DMA can mess up your CD/DVD drives if they dont support
so Im not responsible if it doesn't work, or brakes anything :)

im going to bed - ill check in the morning, let me know if it works or if it doesnt :)

cheers

---

