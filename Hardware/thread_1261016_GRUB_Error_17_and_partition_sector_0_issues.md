---
title: "GRUB Error 17 and partition sector 0 issues"
date: 2009-09-08
forum: Hardware
---

### Post by humaneasy on 2009-09-08
Hi,

I have here in a machine the following configuration:
```

   /dev/sda1    /boot    98MB    Ext2
   /dev/sda5    /var     06GB    Ext3
   /dev/sda6    /        60GB    Ext3
   /dev/sda7     swap    02GB    Swap
   /dev/sda8    /home    92GB    Ext3

```

Only Ubuntu Jaunty is installed.

Today, when I turn it on GRUB return me "Error 17" and froze.

I checked Bios and all is ok. Neverthless, if GRUB runs is because the disk was found.

I tried to boot from LiveCD to check what could be the issue but it couldn't load and in terminal there were several messages regarding /dev/sda6 and read problems with sectors, starting at 0.

I look into the forums but got no info on how can I recover info from my disk and make it run again.

Please help.

Thanks in advance.

---

### Post by humaneasy on 2009-09-08
Can someone give me an hint? Need to go back to work so need to get in that machine sometime soon :)

---

### Post by rob-ward on 2009-09-08
I had a GRUB error 17 in the past, It is normally caused by a corrupt boot menu or drive.

In my case I used the info on this site to fix the problem:

[http://stringofthoughts.wordpress.com/2009/05/24/grub-error-17-debianubuntu/](http://stringofthoughts.wordpress.com/2009/05/24/grub-error-17-debianubuntu/)

However your issue looks a bit more serious as you are getting error messages when you are trying to boot a LiveCD. 

Have you tried booting the computer with the LiveCD and the HDD disconnected to see what happens?

---

