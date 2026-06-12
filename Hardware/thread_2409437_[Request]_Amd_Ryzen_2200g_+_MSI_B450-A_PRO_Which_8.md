---
title: "[Request] Amd Ryzen 2200g + MSI B450-A PRO: Which 8GB RAM?"
date: 2019-01-02
forum: Hardware
---

### Post by gipsyshadow on 2019-01-02
I'm building an office pc with very low power consumption (<100W). It's not for gaming or video editing, I won't get any dedicated graphic card therefore I think 8GB ram is going to be ok.
I've already chosen an Amd Ryzen 2200g, that has an integrated Radeon Vega 8 Graphics and 2993MHz System Memory Specification, and a MSI B450-A PRO that carries "4 x DDR4 memory slots, support up to 64GB - Supports 1866/ 2133/ 2400/ 2667Mhz (by JEDEC) - Supports 2667/ 2800/ 2933/ 3000/ 3066/ 3200/ 3466 MHz (by A-XMP OC MODE)".

Now I've to choose the ram and the 2200g works better at higher ram frequencies, at least 3000mhz, as far as I know from web researches.
[This]("https://www.msi.com/Motherboard/support/B450-A-PRO#support-mem-13") is the MB's tested ram official list, then you've to filter by "Memory by Rx-2x00G/GE (raven ridge)", finally you can order by size. Unfortunately I can get only few listed modules by my local amazon, such as:
- Kingston HyperX Predator HX432C16PB3A/8, 1x8GB, @3200, cl16, SK hynix C, single rank
- Kingston HyperX Predator HX430C15PB3K2/8, 2x4GB, @3000, cl15, SK hynix, single rank

I know ram can be overclocked but I'm very newbie so I can't say anything about that but I guess I could get a lower freq ram and then oc it to 3200mhz, but which one? I don't know ram quality, reliability and overclock-ability and my goal is to get a stable 8GB ram @3200mhz with my configuration.
For example, can this [dual rank 1x8GB crucial ballistix sport lt @2666 cl16]("https://www.crucial.com/ProductDisplay?urlRequestType=Base&catalogId=10151&categoryId=&productId=1738510&urlLangId=-1&langId=-1&top_category=&parent_category_rn=&storeId=10151#spec") be overclocked for sure up to 3200mhz?

Can you suggest me a 8GB (both 1x8GB and 2x4GB), ddr4 ram under 100$ that will be surely compatible with my MB and that has a 3200mhz frequency or that can be oc-ed to that with my configuration?

---

### Post by Autodave on 2019-01-02
You want a stable system but you are thinking over over-clocking the RAM?  That is not conducive to having a stable system.

---

### Post by gipsyshadow on 2019-01-02
I see, I'll avoid overclocking. Therefore I must get a "native" 3200mhz ram, mustn't I?
I can get both these for the same price:
Kingston HyperX Predator HX432C16PB3A/8, 1x8GB, @3200, cl16, SK hynix C, single rank (already listed above)
Kingston HyperX Predator HX432C16PB3K2/8 2x4GB @3200 CL16
Which of them and why do you suggest me? Are there other ddr4 8GB, 3200mhz (**<- effective**), compatible ram modules under 100$ that you can suggest me?

---

### Post by mikasu on 2019-01-02
The second generation Ryzen CPUs only support up to 2933MHz officially. The support for 3200MHz ram is up to silicon lottery. Though I would suggest browsing on newegg if they ship in your region. They have pretty good deals on hardware and you can filter for the ram speed you want. Alos, since you have an APU, I would highly recommand going for 2x4GB for better performance.

---

### Post by mikasu on 2019-01-02
My suggestion would be:
G.Skill Ripjaws V Series 8GB (2x4GB) @ 2800MHz CL15 (CL16 is also available) - $58 USD on newegg.com : [https://www.newegg.com/Product/Product.aspx?item=N82E16820231931](https://www.newegg.com/Product/Product.aspx?item=N82E16820231931)

---

### Post by gipsyshadow on 2019-01-02
I'm not sure about the right/best frequency to get. As said, I thought the "perfect" freq was 3000 or 3200mhz and not less because:
> 
[3000mhz (2966mhz) / 3200Mhz memory is best as it strikes a balance between costs and speed, remember **Vega shares sytem memory**.]("http://www.tomshardware.co.uk/answers/id-3742308/memory-choose-ryzen-2200g.html")

[URL="https://www.quora.com/Which-RAM-should-I-get-with-a-Ryzen-3-2200G-which-can-be-overclocked"]
[...] since Ryzen uses Ram as its l3 cache the speed and performance of the ram directly effects the processors performance, something with 2400mhz is as low as i would suggest, but **it’s better to get at least 3000mhz**, anything above that will just improve processor function even better, after 4000mhz performance doesn't really seem to be noticeably better unless on high performing ryzen cpu’s like a 2700x.
[...]
Ryzen processors benefit from fast RAM as the data fabric (DFICLK) runs at half the speed of the DRAM memory controller. So **for best results get a 3200 MHz CL14 or CL16 kit**, preferably those which use the Samsung B-dies.[/URL]


@mikasu So why did you suggest a 2800mhz ram? Did you mean I'll have to oc it up to 3200mhz? As Autodave warned it's not reliable to oc the ram so what have I to do?

---

### Post by Yellow Pasque on 2019-01-02
> Kingston HyperX Predator HX430C15PB3K2/8, 2x4GB, @3000, cl15, SK hynix, single rank

This should work well (without OC'ing) if you are not gaming.

---

### Post by mikasu on 2019-01-02
because the processor supports up to 2933Mhz. If you have a good silicon, your processor will support 3200Mhz. Besides, I went for a complete dual channel which will help the integrated graphics' performances and the CPU's performance(Ryzen is quite a lot bound to it's ram). I suggested 2800MHz ram because I think it's safer to assume that this one will work with the CPU flawlessly since the specs are 2933Mhz. But again, if you want to take the bet, maybe your silicon can support 3200Mhz.

---

### Post by CatKiller on 2019-01-05
You're conflating two things.

The highest supported speed is 2933. Anything over that is overclocked as far as official support is concerned.

Because of the interconnect architecture, **if** you use higher speed memory, the rest of the system will benefit from more than just the RAM access speed. However, that means that problems with the RAM speed will also have knock-on effects. The second generation Ryzens are much more robust in their memory support than the first generation was, particularly after the first round of BIOS updates. 

Since you describe the new build as a low-power office machine, the RAM speed is irrelevant. It's going to be idle almost all of the time. Get whichever RAM is available from the QVL. Some RAM manufacturers will also certify specific modules for use with Ryzen.

---

### Post by mikasu on 2019-01-05
Just pointing out : even if it says «For Intel...», it will work just fine. I would recommend a Corsair RAM, they work pretty good with Ryzen. HyperX is also a brand that is known to work great with Ryzen processors. But most RAMs will work just fine. If the memory speed is still a concern for you, the 2800MHz RAM that I suggested should be a perfect balance, it's faster than average and it's officially supported by the processor. You will still have 8GB total but you will benefit from the dual channel memory.

---

