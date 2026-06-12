---
title: "Not seeing all my RAM"
date: 2009-12-20
forum: Hardware
---

### Post by doadesweb on 2009-12-20
Hi,

My desktop has 4GB RAM and running windows vista, its showing 4GB RAM and checking the BIOS its showing 4GB RAM but Kubuntu is showing 2.71GB RAM!

It can't be faulty ram as everything else is showing the correct amount?!

What do I do?

Andrew

---

### Post by sanderj on 2009-12-20
Run the python script attached to [http://ubuntuforums.org/showpost.php?p=8284040&postcount=11](http://ubuntuforums.org/showpost.php?p=8284040&postcount=11) 

```

$ sudo python check-my-hardware.py
```

and post the output here.

My prediction: you're running 32-bit bit Ubuntu ...

---

### Post by doadesweb on 2009-12-20
OK, you're root
ANALYSIS:
Total of physical memory modules found 4096 MB in 2 memory module(s)
BIOS offers 4093 MB as usable
Memory seen by OS 2770 MB
BIOS version 07/11/2008
CPU is PAE enabled
CPU is x86_64 64-bit enabled
OS is 32-bit
ADVICE:
You're running a 32-bit OS on a x86_64 CPU. Use a x86_84 64-bit OS to get access to more memory.


Damn, and I can't upgrade from 32bit to 64bit can I :(

---

### Post by doadesweb on 2009-12-20
I was under the impression that 32bit any OS can see up to 4GB?!

---

### Post by SuperSonic4 on 2009-12-20
Nope, only the PAE kernel can support it on 32bit

You could upgrade to 64bit next time you install but it's rare that I use 4gb ram anyway

---

### Post by doadesweb on 2009-12-20
Cheers, I at least know why its not seeing it all now.

I'll think about going 64bit

Andrew

---

### Post by sanderj on 2009-12-20
> **doadesweb said:**
> I was under the impression that 32bit any OS can see up to 4GB?!

Correct; but from 3.2 GB to 4 GB addressing space is used by something else than memory. And the memory originally there is mapped / hoisted above the 4GB limit ... which cannot be see by normal 32-bit kernel.

If you're running 9.10 Karmic, you can try the 32-bit PAE kernel: [http://packages.ubuntu.com/karmic/linux-generic-pae](http://packages.ubuntu.com/karmic/linux-generic-pae) . You can upgrade to that kernel, and then see all 4GB RAM. No need to reinstall a 64-bit kernel.

Please report back your results.

---

### Post by doadesweb on 2009-12-20
Cool, installing that kernel now gives me 3.92GB RAM.. AWESOME :D

Thanks all!!

---

### Post by sanderj on 2009-12-20
> **doadesweb said:**
> 

<snip>
windows vista, its showing 4GB RAM and checking the BIOS its showing 4GB RAM but Kubuntu is showing 2.71GB RAM!


If your Vista is 32-bit and SP1, it will report the *physically* installed memory, not the *usable* memory. See [http://support.microsoft.com/kb/946003/](http://support.microsoft.com/kb/946003/)

---

### Post by sanderj on 2009-12-20
> **doadesweb said:**
> Cool, installing that kernel now gives me 3.92GB RAM.. AWESOME :D

Thanks all!!

So: you installed the PAE-kernel just like that, rebooted, and now you have got 3.92 GB? Awesome indeed!

Two requests:
1) can you run the script check-my-hardware again, and post the output here?
2) can you run "uname -a" and post the output here?

---

### Post by doadesweb on 2009-12-20
Yep just did a simple apt-get install [linux-generic-pae]("http://packages.ubuntu.com/karmic/linux-generic-pae") and rebooted..
outputs below:

**"python script"**
OK, you're root
ANALYSIS:
Total of physical memory modules found 4096 MB in 2 memory module(s)
BIOS offers 4093 MB as usable
Memory seen by OS 4017 MB
BIOS version 07/11/2008
CPU is PAE enabled
CPU is x86_64 64-bit enabled
OS is 32-bit
ADVICE:
Sorry, no advice for you

**"uname -r"**
2.6.31-17-generic-pae

---

### Post by Gtklocker on 2009-12-20
If you want you system to be faster, you can use Con Colivas patches for kernel. (BFS)

---

### Post by sanderj on 2009-12-20
Can you post "uname -a"? I want to see whether there's still "i686", or something else.

```
sander@quirinius:~$ uname -a
Linux quirinius 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux
sander@quirinius:~$ 
sander@quirinius:~$ uname -r
2.6.31-16-generic
sander@quirinius:~$
```

---

### Post by doadesweb on 2009-12-20
ard@ard-desktop:~$ uname -a
Linux ard-desktop 2.6.31-17-generic-pae #54-Ubuntu SMP Thu Dec 10 17:23:29 UTC 2009 i686 GNU/Linux
ard@ard-desktop:~$ uname -r
2.6.31-17-generic-pae
ard@ard-desktop:~$

---

### Post by sanderj on 2009-12-20
> **doadesweb said:**
> ard@ard-desktop:~$ uname -a
Linux ard-desktop 2.6.31-17-generic-pae #54-Ubuntu SMP Thu Dec 10 17:23:29 UTC 2009 i686 GNU/Linux
ard@ard-desktop:~$ uname -r
2.6.31-17-generic-pae
ard@ard-desktop:~$

Thanks. That means that my script also has to look for 'pae' in uname.

---

### Post by sanderj on 2009-12-20
New version of my script: it takes care of PAE-kernels, and will advice to use it, even on x86_64-bit CPUs


Feedback / Review welcome

```
sander@quirinius:~$ sudo python check-my-hardware.py 
OK, you're root
ANALYSIS:
Total of physical memory modules found 1024 MB in 1 memory module(s)
BIOS offers 1013 MB as usable
Memory seen by OS 993 MB
BIOS version 04/14/2009
CPU is PAE enabled
CPU is 32-bit, and not x86_64 enabled
OS is 32-bit with PAE
ADVICE:
Your physical memory is less than 3200 MB, and your system does not need special memory treatment
sander@quirinius:~$ 
```

---

### Post by sanderj on 2009-12-20
> **doadesweb said:**
> Yep just did a simple apt-get install [linux-generic-pae]("http://packages.ubuntu.com/karmic/linux-generic-pae") and rebooted..
outputs below:

**"python script"**
OK, you're root
ANALYSIS:
Total of physical memory modules found 4096 MB in 2 memory module(s)
BIOS offers 4093 MB as usable
Memory seen by OS 4017 MB
BIOS version 07/11/2008
CPU is PAE enabled
CPU is x86_64 64-bit enabled
OS is 32-bit
ADVICE:
Sorry, no advice for you

**"uname -r"**
2.6.31-17-generic-pae

It makes me think why the PAE kernel is not installed by default; it will give access to the full 4+ GB RAM, and thus will take care of a lot of questions in this forum ...

EDIT:
To answer my own question: not all CPU's are PAE-enabled, so I guess a PAE kernel won't work on those CPU's.

---

### Post by doadesweb on 2009-12-20
it would be nice if Ubuntu could tell/check then install that kernel if the CPU type is PAE enabled?

---

### Post by sanderj on 2009-12-20
> **doadesweb said:**
> it would be nice if Ubuntu could tell/check then install that kernel if the CPU type is PAE enabled?

Indeed! If the Ubuntu live boot and/or install procedure could run my script, and then advice and/or install the best kernel: plain 32-bit, 32-bit with PAE, or x86_64 bit. 

It seems that the PAE-kernel is quite safe for recent hardware: there is of course a correlation between 3.2+ GB RAM and modern-and-thus-PAE-enabled CPU's. Or, the other way round: very old hardware won't be PAE enabled, but you won't find 3+ GB RAM there neither, so PAE won't be useful anyway.

So: 
Default kernel for 32-bit CPU would be 32-bit with PAE, unless the CPU can't handle PAE. 
My personal opinion is to run x86_64 if your CPU can handle that; I run x86_64 without any problems since 2007. However, it seems that others think differently about that. In that case the 32-bit with PAE seems good there too.

---

### Post by sanderj on 2009-12-21
I ran my script on my 4GB machine live-booted with a 32-bit Ubuntu, and here's the output:
```


ubuntu@ubuntu:~$ sudo python check-my-hardware-2.py 
OK, you're root
ANALYSIS:
Total of physical memory modules found 4096 MB in 4 memory module(s)
BIOS offers 4029 MB as usable
Memory seen by OS 3465 MB
BIOS version 10/22/2008
CPU is PAE enabled
CPU is x86_64 64-bit enabled
OS is 32-bit without PAE
ADVICE:
You're running a 32-bit OS on a x86_64 CPU. Use a x86_84 64-bit OS to get access to more memory.
Or, probably easier: Upgrade to the 32-bit kernel 'linux-generic-pae' to get acces to more memory.
ubuntu@ubuntu:~$ 
```


And note the last line: "Or, probably easier: Upgrade to the 32-bit kernel 'linux-generic-pae' to get acces to more memory." :-)

---

### Post by doadesweb on 2009-12-21
Truly awesome!
Much better!!

btw, I love that script ;)

---

### Post by doadesweb on 2009-12-24
Just out of interest, I just read a post on the ubuntu community documentation site that said because my cpu is PAE enables and I'm now running the PAE kernel I should be able to get up to 64GB on 32bit?

[https://help.ubuntu.com/community/32bit_and_64bit#Memory](https://help.ubuntu.com/community/32bit_and_64bit#Memory)

Is this correct?  :O

---

### Post by SuperSonic4 on 2009-12-24
That is correct

---

### Post by sanderj on 2009-12-24
> **doadesweb said:**
> Just out of interest, I just read a post on the ubuntu community documentation site that said because my cpu is PAE enables and I'm now running the PAE kernel I should be able to get up to 64GB on 32bit?

[https://help.ubuntu.com/community/32bit_and_64bit#Memory](https://help.ubuntu.com/community/32bit_and_64bit#Memory)

Is this correct?  :O

... yes, but only if you can find a (32-bit) motherboard + memory combination that offers 64GB RAM ;-)

Some more background info on PAE: [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)


And BTW, this is interesting: [https://help.ubuntu.com/community/32bit_and_64bit#What%20should%20I%20choose%20-%2032%20or%2064%20bit?](https://help.ubuntu.com/community/32bit_and_64bit#What%20should%20I%20choose%20-%2032%20or%2064%20bit?) says

> 
What should I choose - 32 or 64 bit?

Unless you have specific reasons to choose 32-bit, we recommend 64-bit. 

But then why is the 64-bit Ubuntu so very hidden on the Ubuntu download page?!

---

