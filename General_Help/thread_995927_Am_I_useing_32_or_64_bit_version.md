---
title: "Am I useing 32 or 64 bit version"
date: 2008-11-28
forum: General Help
---

### Post by its_jon on 2008-11-28
How do I check if I have a 32 or 64 bit version of Ubuntu ?

I have a 64 bit processor but just made aware that there are 2 versions.... which one did I install ?

I assume a 32 bit version will run on a 64 bit machine ?

Thanks !

---

### Post by taurus on 2008-11-28
Applications -> Accessories -> Terminal
```
uname -a
```
If you see i686, then it's 32bit.  Otherwise, you would see x86_64 for 64bit.

---

### Post by geirha on 2008-11-28
```
file /bin/bash | cut -d' ' -f3
```

@taurus, that only shows the architecture. If it says x86_64, the OP may still have the 32-bit version installed.

---

### Post by taurus on 2008-11-28
> **geirha said:**
> ```
file /bin/bash | cut -d' ' -f3
```

@taurus, that only shows the architecture. **If it says x86_64, the OP may still have the 32-bit version installed.**

I don't think so.

---

### Post by geirha on 2008-11-28
> **taurus said:**
> I don't think so.

I don't think so either anymore. I just checked on a 64-bit machine with a 32-bit install, and it does say i686, so I stand corrected :)

---

### Post by its_jon on 2008-11-28
:~$ uname -a

2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux

:~$ file /bin/bash | cut -d' ' -f3
32-bit

Got the above result----So...... does this mean I am running a 32 bit version ?.... on a 64 bit processor ?

---

### Post by geirha on 2008-11-28
```
sudo lshw -class cpu
``` should show you all information on the CPU.

---

### Post by SeanHodges on 2008-11-28
> **its_jon said:**
> Got the above result----So...... does this mean I am running a 32 bit version ?.... on a 64 bit processor ?

Yes. It means you are running 32-bit Ubuntu on your 64-bit machine.

This is fine, it just means your O/S is less optimised for your architecture. Many people run Ubuntu in this way.

---

### Post by taurus on 2008-11-28
> **its_jon said:**
> :~$ uname -a

2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 **i686** GNU/Linux

:~$ file /bin/bash | cut -d' ' -f3
32-bit

Got the above result----So...... does this mean I am running a 32 bit version ?.... on a 64 bit processor ?

Yes.

---

### Post by its_jon on 2008-11-28
is it possible to easily change to a 64 bit version ?

I am running a AMD 64 3200+

Thanks

---

### Post by SeanHodges on 2008-11-28
No, you will need to re-install Ubuntu.

---

### Post by its_jon on 2008-11-28
GRim....:(

Just got used to it as well... 

Any way to save all the important info such as connection details and sound card info, Email History from evolution ?.

I run a dual boot with XP..... anything I can do to make a reinstall of a 64 bit version a bit easyer ....

thanks

---

### Post by taurus on 2008-11-28
You know you don't have to run x86_64 on your machine even though you have a 64bit processor.  i686 should work just fine.

---

### Post by its_jon on 2008-11-28
Would I not see a speed increase in audio processing and graphic work by using the 64 bit processor better ?

---

### Post by its_jon on 2008-11-28
sod it.... Im going for it.....

Downloading the 64 bit version now.

---

### Post by its_jon on 2008-11-28
OK.....

I have backed up Evolution into a Tar.gz thing

Backed up pictures, docs, work

Im hoping the 64bit version will detect my nec connection details from my XP install.... the 32 bit version did.

Anything else I should do before burning this ISO and reinstalling ?

---

### Post by Tom--d on 2008-11-28
Really there is no difference in speed.

You might see a boost in speed in Audio and Video encoding.

---

### Post by its_jon on 2008-11-28
I do a lot of gimping and audio processing. Audacity/Ardour 

any boost is welcome

trouble is im also new to Linux....so... I may as well jump in now and get it wrong sooner rather than later.

---

### Post by bodhi.zazen on 2008-11-28
To see the arch you have installed :

```
uname -m
```

i686 = 32 bit
x86_64 = 64 bit.

To see if your processor is 32 or 64 bit :

```
grep --color=always ' lm ' /proc/cpuinfo
```

If you see a red lm in the output you have a 64 bit processor(s),

You can also get (some) hardware information from

System -> Administration -> System Monitor

---

### Post by oldos2er on 2008-11-28
> **its_jon said:**
> Would I not see a speed increase in audio processing and graphic work by using the 64 bit processor better ?

 Yes, there's some speed improvement in video encoding.

---

### Post by its_jon on 2008-11-28
Weeeeeeeeeeeeeeeeeeeeeeeeeeeeeeee :)

Almost flawless installation ... my backup worked... detected my connection and............... 

Its off like a rabbit !!!!!!!!

Slick desktop animations...Smooooth desktop cube, nuo jumpyness at all

x86_64 ;) ..... worth the effort.

Many thanks.
JOhn

---

### Post by aboud on 2008-11-28
looks like my cpu is 64-bit, 

sudo lshw -class cpu 

shows width 64 bit. and if pass it thro | grep 32 nothing left. 

do you think 8.04 will work fine  ?
is there any other way to switch than reinstalling every thing? 

ubuntu 8.04 on Sony/vaio core 2 duo.

---

### Post by roger_1960 on 2008-11-28
Hi

Yes, core 2 duo chips are 64 bit.  You will need to reinstall from amd64 cd.  Backup first!

---

### Post by its_jon on 2008-11-28
I have to say this.... with my processor at least

AMD 3200+
2.6 gig ram
gforce embedded mobo

2004'ish vintage PC

I was happy with Ubuntu 32 bit but was slightly disappointed at the quality of the goom visual for example... with 8.10 came a beter looking Goom but the large or extra large version of it when running rhythmbox was useless, processor was overloaded....
Again with the desktop effects.... I had to reduce the animation/rendering settings to make it usable...... Now everything is SLIIIIIIICK at top setting.

Looking forward to working with PCU hungry apps now :)

So (in my case) running a 64bit version on a 64 bit machine has certainly made a huge difference ! especially as my last O$ - XP was also running at 32 bit.


______________

Now.... here is a suggestion... 

I know a friend of mine tried to install a 64 bit image onto a 32bit machine and one of the first things the install presented him with was the message 

"This is a 32 bit machine and you are attempting to install a 64 bit version"

As I am absolutly SHURE there will be thousands of people like me who have installed a 32 bit Ubuntu on a 64 bit machine and dont know it, and are possibly disappointed with the speed of the UI.
Thats a big shame as 64 on 64 is SO much better.....why not:-

Detect if a user is about to install a 32 bit version onto a 64 bit machine as well ?.... on detection display this message:-

"You are about to install a 32 bit version of Ubunto onto a machine capable of running the more advanced 64 bit version of Ubuntu"

The 64 bit version is available to download from the Ubuntu site and recommended for your machine

However

You may continue to install this 32 bit version which will still work fine" 

Or something like that.... :)

---

### Post by aboud on 2008-11-30
all right, i reinstall it.

 ubuntu 8.10 amd64

can't notice any difference in  performance. 
videos on the cube not playing good like it was.

---

