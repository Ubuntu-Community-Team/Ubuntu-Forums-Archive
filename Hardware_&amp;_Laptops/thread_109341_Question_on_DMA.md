---
title: "Question on DMA"
date: 2005-12-28
forum: Hardware &amp; Laptops
---

### Post by Michel F on 2005-12-28
I am very new to Ubuntu. I am trying to increase the performance of my DVD-ROM with the use of DMA.

As per numerous threads, I have set DMA on in my hdparm.conf file without any issue and after reboot hdparm -i shows it is effectively on.

However the speed for cached reads is still around 3 MB/s.

I read that some lines shoud be present in my /etc/modules files, namely (in this order) piix, ide-core, ide-cd, ide-disk and ide-generic. 

None of them are in my file. Not even the last three.

What is their use ? Should I add them ? I believe the question has already been asked here : [http://www.ubuntuforums.org/showthread.php?t=105900](http://www.ubuntuforums.org/showthread.php?t=105900), but still no answer.

Thanks in advance to any Ubuntu rescuer.

PS : My initial issue is slow and irregular DVD play in Totem. I know my pc is outdated (PIII 500 MHz), but it makes it under Windows. So...

---

### Post by Michel F on 2006-01-05
Any idea ?

PS: Happy new-year everybody!

---

### Post by Amon_Re on 2006-01-05
[QUOTE=Michel F]Any idea ?

PS: Happy new-year everybody![/QUOTE]

What does the following give you?

```
sudo hdparm /dev/dvd
```

If you get something like this it should work:

```
/dev/dvd:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
```

---

### Post by Michel F on 2006-01-07
Well, thanks :) , but that's what I have.

The hdparm -tT command gives me 250 Mb/s and 4.35 Mb/s results. I guess it's the 4.35 which is too small. 

How do this compare with others ?

And of course, welcome to any other idea.

---

### Post by Michel F on 2006-02-03
OK, I finally solved my initial issue (DVD play). I also changed the kernel to the 686 version. Perhaps that was sufficient to free the little amount of resources needed by my (old) box to do the job. Oh, and this may also play a role, I switched from Ubuntu to Kubuntu :).

---

