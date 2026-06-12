---
title: "Does Dual Xeon need a special kernel?"
date: 2009-07-07
forum: Hardware
---

### Post by flexgrip on 2009-07-07
Hello,

I have a Dell Precision 650 with dual xeon 3.06ghz cpu's running Jaunty. If I do "lshw" it shows me 4 processors. I am assuming they are each dual core?

Anyway, it seems to me that processes tend to only use one of those cores. Like no matter what, a process is only allowed to max out one of those cores. Often when I am doing cpu intensive tasks or running glxgears it will tell me that cpu 1, 2, and 3, are at like 3% but cpu 0 is stuck at 100%.

In general everything feels a lot slower than in xp. I run ubuntu on all 5 of my laptops/desktops and even at work. None of them follow this behavior.

So is there a kernel that is recommended for my setup? My other workstation has a quarter of the power that this system has but seems to be a lot quicker at everything which makes me think this cpu setup is limiting a process to only use one half of one of my two processors.

Thanks

---

### Post by shatterblast on 2009-07-07
> **flexgrip said:**
> Does Dual Xeon need a special kernel?

Yes. x64.

---

### Post by flexgrip on 2009-07-07
These xeons are 32bit I think. This is what lshw says about them.
```

*-cpu:0
          product: Intel(R) Xeon(TM) CPU 3.06GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.2.7
          size: 18EHz
          **[COLOR="Red"]width: 32 bits[/COLOR]**
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             **[COLOR="Red"]width: 32 bits[/COLOR]**
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             **[COLOR="Red"]width: 32 bits[/COLOR]**
             capabilities: logical
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 8KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-cpu:1
          product: Intel(R) Xeon(TM) CPU 3.06GHz
          vendor: Intel Corp.
          physical id: 2
          bus info: cpu@1
          version: 15.2.7
          size: 18EHz
          **[COLOR="Red"]width: 32 bits[/COLOR]**
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             **[COLOR="Red"]width: 32 bits[/COLOR]**
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             **[COLOR="Red"]width: 32 bits[/COLOR]**
             capabilities: logical
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 8KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB


```

I would be happy to run x64 if I could. Is this detecting them wrong or am I right in saying I can't use x64 with these cpu's?

---

### Post by shatterblast on 2009-07-07
By nature, x64 is a couple of x32 things slapped together with a bunch of other technology stuff around it and between.  Since software hasn't "evolved" to x128, a quad core will do the work internally to optimize itself in that regard.  Sometimes it waits for some kind of "flag" motion from the software to activate that feature.  An x64 operating system should allow that.

---

### Post by flexgrip on 2009-07-08
Yeah I went to install x64 and it is telling me x64 is the wrong kernel for my architecture.

So back to my original question. Is there a 32bit kernel that is better for my dual xeons that are 32bit?

---

### Post by flexgrip on 2009-07-08
So, if I turn hyperthreading off, then ubuntu will see only two processors. This will allow processes to at least take 100% of one cpu instead of 50%.

Is there not anything I can do to work around this? It is still going to not take advantage of all of my cpu's. Not to mention this dell bios is crappy and doesn't let me remove hyperthreading.

---

### Post by shatterblast on 2009-07-09
It is possible to disable hyper-threading in the Linux kernel itself, but I believe it comes at a drastic reduction in performance.  I wouldn't call the Dell BIOS "crappy," but rather over-simplified and safer for an average user.  Also, I think certain BIOS versions for Dell have it hidden.  Upgrading the BIOS can help, but making a mistake means flirting with disaster in the wrong way.  You might face the consequence of needing to purchase a new computer part.  I would suggest avoiding this path if not immediately obvious to you.

I don't know much about the Xeon set, but I am aware that more than one version exists.  Hyper-threading is a technology that existed before the dual core.  It provided a bridge from single to dual core.  Later, hyper-threading became optimized a little bit, reducing the cost for both Intel and buyers.  Thus, the quad core came to existence.  This is how your technology works.

Do you know the difference between a 4 valve and 8 valve engine in a vehicle?  A buyer may know that the 4 valve is less expensive and easier on fuel costs, but a buyer with a special need may purchase the 8 valve anyway.  Why?  I'll let you figure that out.

What about fuel?  Do you decide what type to use, or do you just prefer the least expensive one available?  The wrong fuel will damage an engine.

In the meantime, I suggest making a LiveCD for the x64 version and testing it on your system.  It won't harm your data unless you choose so.

---

