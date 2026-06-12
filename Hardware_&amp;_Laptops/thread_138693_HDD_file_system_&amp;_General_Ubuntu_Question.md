---
title: "HDD file system &amp; General Ubuntu Question"
date: 2006-03-02
forum: Hardware &amp; Laptops
---

### Post by zzz@tkz on 2006-03-02
I'm new here (obviously), so sorry if this isn't in the right place for it (I'm a veteran of forums, and I hate when people say that too), but I have a liveCD and an empty partion that I was wanting to use for it. Someone at the other forums that I vist said that I had to "mount" it, but I dunno how that works.


Another thing I was thinking about (since I do like ubuntu a lot), was formating the other partion for ubuntu (I.E. writting the OS to the HDD), but when I partioned my HDD last time, it corrupted Windows, so I'm rather worried that it will happen again. I personaly don't like Windows, but my Dad and the rest of the family use it, (plus it has all of my files on it :P) so I couldn't risk losing it. So, what are the chances of somthing like that happening?


Thanks for your help :).

---

### Post by RaiSuli on 2006-03-02
The live cd should work straight from your cd rom. Just insert it and reboot. It's a good way to check if your hardware is supported.

If you want to install Ubuntu next to Windows, you should take a look at some of the excellent how-to guides in this forum. Search for "dual boot". I run a dual boot system and have had no problems.

Hope this helps!

---

### Post by bluevoodoo1 on 2006-03-02
Here is a great guide for dual booting, I used it in the past...
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Be sure to backup any data that is important. You can never be too careful with things like this. There is always a *chance* of something going wrong.

For the live CD you will probably have to make your system boot from the CD drive. It will be one of your F* keys. Mine is F8. Press it a few times as your system starts up.

---

### Post by zzz@tkz on 2006-03-02
Nonono....I know how to boot from a liveCD, I was just wondering what format the HDD needs to be in in order to save to the HDD from Ubuntu.


Does anyone know how often corruption of data occours?

---

### Post by bluevoodoo1 on 2006-03-02
[QUOTE=zzz@tkz]Nonono....I know how to boot from a liveCD, I was just wondering what format the HDD needs to be in in order to save to the HDD from Ubuntu.[/QUOTE]

ohhh, ok :)  My HD is an ext3, which many people use. Ubuntu can write to that. It cannot write to an NTFS though, only read. I believe Ubuntu and windows can both read and write with a FAT32 formatted HD.

---

### Post by zzz@tkz on 2006-03-02
So, formating the partion to FAT32 should work?

My Windows' partion is NTFS, so I assume that won't work :P.

---

### Post by sham69 on 2006-03-02
You won't be able to write to NTFS. If it is empty, reformat as Fat32 and both Windows and Linux can read and write. I keep my mp3's on a Fat 32 partition, so I can get at them from both OS on a dual-boot setup.

---

### Post by zzz@tkz on 2006-03-02
If I just install ubuntu over that partion (the empty one), it would automaticly format it correctly, right?

---

### Post by bluevoodoo1 on 2006-03-02
[QUOTE=zzz@tkz]If I just install ubuntu over that partion (the empty one), it would automaticly format it correctly, right?[/QUOTE]

Yes, there is a partition setup tool on the install disc. It isn't really automatic, but it will allow you to choose what format you want for that partition.

---

### Post by zzz@tkz on 2006-03-02
Ah...Okay. Thanks for your help (agian) :).

---

