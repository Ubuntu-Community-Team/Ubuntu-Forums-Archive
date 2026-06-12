---
title: "Only Ubuntu not recognizing RAM upgrade"
date: 2009-05-08
forum: Hardware
---

### Post by gabrielalcivar on 2009-05-08
Hi!
I just upgraded my RAM to 4gb from 3gb on my HP dv6875se. The BIOS does show 4gb and my evil Windows partition is also recognising the 4GB. Therefore it can be assumed that its an Ubuntu issue:
```

             total       used       free     shared    buffers     cached
Mem:       3095952     488528    2607424          0      72872     196464
-/+ buffers/cache:     219192    2876760
Swap:      5116692          0    5116692
```

This, I think is also causing hibernation issues, which I will address when this is fixed.
All the best

---

### Post by abn91c on 2009-05-08
the 32bit ubuntu will only see 3.2 gig RAM, you will need the 64bit version for the full 4gig RAM if your CPU supports it

---

### Post by gabrielalcivar on 2009-05-08
Thank you. Pretty straightforward. Any reason for that Ubuntu 32bit not supporting more RAM? Will this change in future 32bit upgrades?
Thank you

---

### Post by sonicb00m on 2009-05-08
32bit technically will only see 3gb.

You can enable the server kernel which will show all 4gb though. Note that enabling 4gb support on a 32bit system does have some performance draw backs.

Is the windows you are running 64bit? I've never heard of 32bit windows supporting more than 3gb of ram but then i am not sure about it either.

---

### Post by Barry Carroll on 2009-05-08
> **sonicb00m said:**
> 
Is the windows you are running 64bit? I've never heard of 32bit windows supporting more than 3gb of ram but then i am not sure about it either.

In my experience it cannot despite any PAE or NX tweaks that you will see out there.

It's worth noting that after Vista SP1 32-bit windows reports the amount of installed memory, not the usable memory.

---

### Post by gabrielalcivar on 2009-05-08
its a 32 bit, but true, it may only report it and not be wholly usable. Now can you give post a link with the benefits and drawbacks of 64-bit ubuntu?
Thank you!

---

### Post by Barry Carroll on 2009-05-08
You could read up for ever about 64-bit vs 32-bit but at the end of the day 64-bit gives you the capability to address more than 4GB of RAM.  Right now there are no clear cut or appreciable performance differences and you'll find that some things are slightly faster in 64-bit and some slightly slower.

2 Things: Do you want to address more than 4GB and have you made sure all the binaries that you use are available in 64-bit versions?

ps. In windows have a look in the task manager on the 'performance' tab.  That will tell you what your usable memory is.

---

### Post by sonicb00m on 2009-05-09
> **Barry Carroll said:**
> In my experience it cannot despite any PAE or NX tweaks that you will see out there.

It's worth noting that after Vista SP1 32-bit windows reports the amount of installed memory, not the usable memory.

That's good to know!

> its a 32 bit, but true, it may only report it and not be wholly usable. Now can you give post a link with the benefits and drawbacks of 64-bit ubuntu?
Thank you! .

I always go with 64bit since the computer is capable of it. There's no reason not to unless you have a specific program that available in 64 bit. Usually that would only be proprietary software like Skype or something.

You can get Skype to work in 64 bit and works fine on Intrepid but I cannot get it to work on Jaunty with the same process.

---

### Post by sudosudont on 2009-06-04
try to sudo apt-get install the server kernel. it worked for me and i didnt have to reinstall the os.

---

### Post by pmj85 on 2009-06-08
Hmm strange; I too have just upgraded my laptop ram to 4GB and Ubuntu is only seeing 3.1gb. I know this to be a problem with 32bit O/Ses so I reformatted and installed the 64bit version. However, it's still only seeing 3.1gb of memory :sad:

*cue Twilight Zone theme*

---

