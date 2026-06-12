---
title: "Velociraptors in RAID 0"
date: 2010-01-02
forum: Hardware
---

### Post by Renée Jade on 2010-01-02
ok, so this isn't really Linux related at all, but I'm sure some of you guys will be interested in my question.

I'm building a brand new system and I want to set up a very fast hard drive system while avoiding the premature and overpriced (IMO) technology that is SSD. So I was thinking about using three (3) 150GB WD VelociRaptors in RAID 0 via the onboard controller on a GIGABYTE GA-X5A8-UD7 motherboard, since the feature is there and I can get the VelociRaptors for wholesale cost. What are your thoughts on this idea? Are there any issues or limiting factors that I am not seeing?

Thanks

---

### Post by tgalati4 on 2010-01-02
Why do you need RAID 0?  The raptors are quite fast alone; no need to take the risk that your motherboard's controller will melt and trash your work.

Unless you are doing real-time financial transactions, I'm not sure of the value of RAID for the home user.

I agree, SSD is not ready for prime time.

---

### Post by Renée Jade on 2010-01-02
Yeah I don't really need to. It's kinda one of those "because I can" sorts of things. But I really don't think it is worth it. Especially not with three as I think the performance might be limited by the motherboard. I might get two 150s and stripe them, as this would give me a performance increase over a single 300 without much extra cost. And the money not spent on the third velociraptor I could spend on a large "normal" hard drive for non-critical data storage and periodic backup of the RAID disks, too.

Thanks.

---

### Post by falconindy on 2010-01-02
Using RAID 0 with a fake-raid controller has been shown to give little or not gain in performance. There's benchmarks on Phoronix showing this.

Save your pennies, or put them somewhere else like faster RAM or CPU if the case is "because you can". The new velociraptors are insanely fast by themselves.

---

### Post by Renée Jade on 2010-01-02
> **falconindy said:**
> Using RAID 0 with a fake-raid controller has been shown to give little or not gain in performance. There's benchmarks on Phoronix showing this.

I argue not, since I know little about this. But wouldn't the effectiveness of fakeraid depend heavily on the quality of the controller chip, controller firmware and CPU speed? If you have a decent onboard controller, spare CPU cycles and the correct stripe width, surely you will see performance benefits from RAID 0.

---

### Post by falconindy on 2010-01-03
> **Renée Jade said:**
> I argue not, since I know little about this. But wouldn't the effectiveness of fakeraid depend heavily on the quality of the controller chip, controller firmware and CPU speed? If you have a decent onboard controller, spare CPU cycles and the correct stripe width, surely you will see performance benefits from RAID 0.
"Fakeraid" and "quality" don't belong in the same sentence. There's a reason you spend $200-300 for a reliable hardware RAID controller with its own BIOS and processor.

---

### Post by Renée Jade on 2010-01-03
Yeah I know. May I be more specific with what I am after? I'm a first time builder but I've done a lot of research for this project and I've spent a rather exorbitant amount of money on it. I've ordered the GA-X5A8-UD7 motherboard, an i7 950 CPU, 6GB or fast Corsair memory, and I don't even want to tell you how much I've spent on graphics. This ridiculous overkill (about which I am most excited) has left me with about $600AU, or about $540US (I think) to spend on storage (although I really don't have to spend that much). The motherboard supports fakeraid. Why not use it?

P.S. Please don't think of me as some spoiled gamer brat who has more money than brains. I'm a student who's spent half her summer holiday working her butt off at McDonald's to finance this :P

---

### Post by tgalati4 on 2010-01-07
I think the Raptors by themselves will provide higher data bandwidth by themselves than striping them with a fakeRAID.  I could be wrong, but I wouldn't trust a motherboard's fakeraid controller to handle my data.  Striping to get more disk throughput is helpful if you are rendering video animation.  If you aren't doing video editing, then use one Raptor for boot and one large SATA drive for data storage.

Setting up RAID for home use will cost you more in energy, noise, and headache.  You need a really good reason to use RAID.

---

