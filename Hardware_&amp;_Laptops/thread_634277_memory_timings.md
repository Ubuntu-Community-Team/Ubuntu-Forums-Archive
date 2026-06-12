---
title: "memory timings?"
date: 2007-12-07
forum: Hardware &amp; Laptops
---

### Post by sayuki288 on 2007-12-07
what's the best settings or timings for these type or RAM?

cause im buying one but don't know if what its  appropriate  ram timings are

[http://www.newegg.com/Product/Product.aspx?Item=N82E16820134116](http://www.newegg.com/Product/Product.aspx?Item=N82E16820134116)

---

### Post by sayuki288 on 2007-12-07
what's the best settings or timings for these type or RAM?

cause im buying one but don't know if what its appropriate ram timings are

[http://www.newegg.com/Product/Produc...82E16820134116](http://www.newegg.com/Product/Produc...82E16820134116)
__________________

---

### Post by wolfen69 on 2007-12-07
there is no need to set the ram timings. the bios will automatically set them for you.

---

### Post by Yellow Pasque on 2007-12-07
Broken link. Err, got it now.

The correct timings are 5-5-5-15. These should be programmed into the memory and you shouldn't have to touch any memory voltage/timing settings in the BIOS.

---

### Post by sayuki288 on 2007-12-07
does it make a difference in performance iif i change the timings?

---

### Post by wolfen69 on 2007-12-07
in my opinion, it doesnt make much difference. the increase in speed is minimal and could cause problems if you're not careful.

---

### Post by rsambuca on 2007-12-07
Please do not make duplicate threads with the same question.  I have requested that the threads be merged.

---

### Post by victorgreen on 2007-12-07
timings make virtually no difference unless you want really nice games to run smoothly with graphics maxed out. But with DDR2 ram timings matter even less. Unless you want to risk frying something and voiding any and all warranties, dont go overclocking your ram and fiddle with the timings.

---

### Post by Skip Da Shu on 2008-01-06
> **wolfen69 said:**
> there is no need to set the ram timings. the bios will automatically set them for you.

Yes it will... but...

Some higher end DDR and DDR2 memory sticks use very conservative SPD timings to make sure the machine will boot and "expect" you to set to the "claimed" latency timings in BIOS.  I recently purchased some DDR2-800 that claimed 4-4-4-12 but SPD defaults were 4-5-5-15.  The memory in fact tests out fine at 4-4-4-12 @ 840MHz.  I have one mobo with some Kingston DDR2-667 that claims to be 5-5-5-18 but some poor math benchmarks made me suspect it might be defaulting to something slower.

The fact of which has forced me to install wine and try and get CPUZ work so I can see what it's really running at under Xubuntu. I haven't got cpuz.exe working (gets error) but CBid reports it at 6-6-6-20! 

Back in DDR single core days of XP and Athlon 64 chips from AMD and Pentium 4 and D chips from Intel the 'general rule' was that AMD chips benfited more from tighter timings whereas the Intel chips benefited more from higher frequencies.  I'm sure this has changed 3 times since then though.

Skip

---

### Post by Yellow Pasque on 2008-01-06
> **Skip Da Shu said:**
> Back in DDR single core days of XP and Athlon 64 chips from AMD and Pentium 4 and D chips from Intel the 'general rule' was that AMD chips benfited more from tighter timings whereas the Intel chips benefited more from higher frequencies.  I'm sure this has changed 3 times since then though.

Yeah, Core 2 has a shorter pipeline and benefits about equally from tighter timings or higher bandwidth. Synchronous mem speed (i.e. no divider) is also more important with C2D than with the old P4/D.

---

### Post by Skip Da Shu on 2008-01-06
> **sayuki288 said:**
> does it make a difference in performance iif i change the timings?

Well somebody needs to give the opposing view.  Needless to say I seem to be the minority here.  So, with that said... I'd be a bit embarrassed if I had any memory running stock speed & stock timings if I have any control over it.  

I'll admit I've scrambled system files in Windows with pushing it to far and had to reinstall but I've never been able to do damage to the hardware.  I've not been able to scramble Xubuntu (yet).  

The only thing that can really get your hardware is **voltage**.  I recommend you try your timing changes at spec voltages (1.8~1.9v for DDR2, 2.5 to 2.6v for DDR) unless your memory has a higher spec (eg, Crucial Ballistix DDR2 is rated for 2.2v). Don't bump voltage by more than 0.1v and only if it gets you to the next level or makes almost good timings stable.

It's very time consuming to test it out properly but if you like fiddling than I say it's "free" performance that's there for the taking.

---

### Post by Skip Da Shu on 2008-01-06
> **sayuki288 said:**
> what's the best settings or timings for these type or RAM?

cause im buying one but don't know if what its appropriate ram timings are

[http://www.newegg.com/Product/Produc...82E16820134116](http://www.newegg.com/Product/Produc...82E16820134116)
__________________


A much better buy IMHO...

[PQI 2x512MB DDR2-800 CAS4]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820141185")

---

### Post by Yellow Pasque on 2008-01-06
> **Skip Da Shu said:**
> A much better buy IMHO...

[PQI 2x512MB DDR2-800 CAS4]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820141185")
I'd rather have 2GB of slightly slower memory.

---

### Post by Skip Da Shu on 2008-01-06
> **Temüjin said:**
> I'd rather have 2GB of slightly slower memory.

Generally I'd agree... I was just trying to give same size, near same price... 

but looking again... for a couple bucks more (after a rebate) there [THIS]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820211066") 2x1GB A-data.  I've actually used the 2x512 version of this and proved solid up to about 850 on defaults.

---

