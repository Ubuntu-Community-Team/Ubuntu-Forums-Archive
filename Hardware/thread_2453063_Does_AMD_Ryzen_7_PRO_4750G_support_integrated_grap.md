---
title: "Does AMD Ryzen 7 PRO 4750G support integrated graphics?"
date: 2020-11-02
forum: Hardware
---

### Post by satimis on 2020-11-02
Hi all,

I'm searching information to build a desktop PC for serving Dell 32" 4K display, model U3219Q, without graphic card to be added.

I don't game but need speed for WordPress websites running on VMs of Oracle VirtualBox

OS - Ubuntu 20.04 desktop
Graphic editing software - GIMP, Inkscape and Darktable, etc.

Planned configuration of the PC:-```

CPU - AMD Ryzen 7 PRO 4750G 100-000000145 8C/16T,3.6GHz,12MB Cache
RAM - Corsair Vengeance RGB PRO CMW32GX4M2C3000C15 DDR4 3000MHz 32GB Kit (2x16GB)
Hard Disk - Corsair Force Series Gen.4 PCIe MP600 1TB NVMe M.2 SSD
Motherboard - ASUS ROG STRIX B550-F GAMING (WI-FI) AM4 Socket,Intel 2.5Gb Lan,WiFi ax,USB3.2,PCIe 4.0

```
Does AMD Ryzen 7 PRO 4750G support integrated graphics?

Advice would be appreciated. Thanks in advance.

Regards

---

### Post by mikewhatever on 2020-11-02
Not sure what you mean by 'support integrated graphics'. 

All you need to know is in the data sheet here->[https://www.amd.com/en/products/apu/amd-ryzen-7-pro-4750g](https://www.amd.com/en/products/apu/amd-ryzen-7-pro-4750g), or in a review here->[https://www.tomshardware.com/reviews/amd-ryzen-7-pro-4750g-renoir-review](https://www.tomshardware.com/reviews/amd-ryzen-7-pro-4750g-renoir-review).

...very easy to find too :~)

---

### Post by satimis on 2020-11-02
> **mikewhatever said:**
> Not sure what you mean by 'support integrated graphics'. 

All you need to know is in the data sheet here->[https://www.amd.com/en/products/apu/amd-ryzen-7-pro-4750g](https://www.amd.com/en/products/apu/amd-ryzen-7-pro-4750g), or in a review here->[https://www.tomshardware.com/reviews/amd-ryzen-7-pro-4750g-renoir-review](https://www.tomshardware.com/reviews/amd-ryzen-7-pro-4750g-renoir-review).

...very easy to find too :~)
Hi,

Thanks for your reply and links

I found my answer:-
Definition of integrated graphics | PCMag
[https://www.pcmag.com/encyclopedia/term/integrated-graphics](https://www.pcmag.com/encyclopedia/term/integrated-graphics)

Integrated GPU vs Dedicated GPU: What’s the Difference?
[https://techguided.com/dedicated-graphics-card-vs-integrated-graphics/#3](https://techguided.com/dedicated-graphics-card-vs-integrated-graphics/#3)

Dedicated Graphics Card vs. Integrated Graphics: Which is Better for YOU?
[https://techguided.com/dedicated-graphics-card-vs-integrated-graphics/](https://techguided.com/dedicated-graphics-card-vs-integrated-graphics/)

Further reading on;
Who Should Get A Dedicated Graphics Card?
[https://techguided.com/dedicated-graphics-card-vs-integrated-graphics/#4](https://techguided.com/dedicated-graphics-card-vs-integrated-graphics/#4)

I don't think I need a CUP supporting "integrated graphics".  I don't game.

I'll pick :AMD Ryzen 7 3700X".  Its price a little bid cheaper.
AMD Ryzen 7 3700X spec.
[https://www.techpowerup.com/cpu-specs/ryzen-7-3700x.c2130](https://www.techpowerup.com/cpu-specs/ryzen-7-3700x.c2130)

I have posted my question on "tomahardware", no reply received yet.

Regards

---

### Post by QIII on 2020-11-02
"Integrated" graphics are integrated on the *motherboard.*  That is to say that they are soldered down.  An APU has both the "dedicated" GPU and the CPU on the same die and you lock down the whole thing in one socket.

If you are going to use an APU there really isn't any reason to get a motherboard with integrated graphics if you can find one that comes without.  Particularly avoid Intel integrated graphics, as neither AMD nor Nvidia is kind to us Linux folks with regards to hybrid systems.  You would probably be doing yourself a favor to avoid having two GPUs, as even an AMD unit might cause you some grief that would be unnecessary if you are not going to game.  (Many modern Intel chips also feature both on the same die, in which case I'd still avoid further integrated graphics on the board.)

Just bear in mind that APUs can run hot, but they are designed for that.  Don't freak out if you see higher temps than you might expect with just a CPU in the socket.

---

### Post by mastablasta on 2020-11-03
go with first option (the new 4000 series APU). they heat up much less than the older ones. and also their integrated GPU is actually very good. we use the Ryzen 5 3500U which is a laptop APU (CPU with GPU) and it can handle surprising number of demanding games. maybe osme on medium settings or low but still. very good for something that uses so little power. mostly we played CS:GO or Garry's Mod on it and thee heat is really small (luke warm on touch).

the issue i can see is ASUS gaming motherboard. sometimes these cam cause issue. make sure the selected one works well.

---

### Post by satimis on 2020-11-03
> **QIII said:**
> "Integrated" graphics are integrated on the *motherboard.*  That is to say that they are soldered down.  An APU has both the "dedicated" GPU and the CPU on the same die and you lock down the whole thing in one socket.......
Hi,

Thanks for your advice.

A breif searching I found following link;

AMD Ryzen 7 3700X vs Intel Core i7-9700K - CPU ...
[https://cpu.userbenchmark.com/Compare/Intel-Core-i7-9700K-vs-AMD-Ryzen-7-3700X/4030vs4043](https://cpu.userbenchmark.com/Compare/Intel-Core-i7-9700K-vs-AMD-Ryzen-7-3700X/4030vs4043)

The difference, which I discovered, are;
1) Number of threads:
Ryzen 7 3700X - 8 Cores, 16 Threads
Intel Core i7-9700K - 8 Cores, 8 Threads

2) Date of release:
Ryzen 7 3700X - Q3 2019
Intel Core i7-9700K - Q4 2018

I'm aware that the heat generated by AMD CPU is more.  The history of my support to AMD can be traced back to >20 year ago when the CPU market was solely monopolised by Intel.  Later AMD came in and followed by IBM.  But IBM gave up very soon.

ROG STRIX B550-F GAMING (WI-FI) Spec;
[https://rog.asus.com/motherboards/rog-strix/rog-strix-b550-f-gaming-wi-fi-model/spec/](https://rog.asus.com/motherboards/rog-strix/rog-strix-b550-f-gaming-wi-fi-model/spec/)```

Graphic
Integrated Graphics Processor

```

Any suggestion on ASUS motherboard selection from you?.  I need Display Port but WiFi is not import.

Thanks

---

### Post by mastablasta on 2020-11-03
well they ran Crysis on AMD 4000 series with cooler on it: [https://www.techradar.com/news/so-an-amd-ryzen-4000-apu-can-apparently-run-crysis-without-a-cpu-cooler](https://www.techradar.com/news/so-an-amd-ryzen-4000-apu-can-apparently-run-crysis-without-a-cpu-cooler). 

it's an old game but still it demonstrates the current state of CPUs and heating. 

for your ROG Strix GPU you need to read the whole section. it says:
[FONT=segoeui]*Graphics specifications may vary between CPU types.[/FONT]

That's because the GPU is actually integrated on the CPU  not on the board itself. you can check the gallery. you can also check the boards manual and you will see there is no GPU chip on the board itself. same is with intel.

all i am saying is make sure it works with linux. if it does (e.g. someone already installed linux on it and didn't face any issues) then you are good to go. 

my kid has an older non gaming ASUS board and had no issues on install. we got an old Ryzen 7 2700 (without any GPU chip on it) and added separate nvidia GTX1650 card. works well for his needs. i used parts (PSU, HDD) from older PC that had issues with motherboard and also added new 16GB RAM and frame.

---

### Post by ajgreeny on 2020-11-03
I am pretty certain that the G in the numerical naming of the ***4750G*** means that it has integrated Graphics in the Ryzen CPU itself, like many of the Intel CPUs, so you should not need a separate GPU in order to run graphics unless you need a lot of fast, hi-res image work such as games.  As mastsblasta says, you need to be sure there is support for the AMD grahics used on that CPU; I suspect you will be good to go as long as your OS and in particular, your kernel are recent versions.

Th Ryzen CPUs without the G in their naming will definitely need some other graphics system available, either in the form of a separate graphics card or an integrated graphics system on the motherboard.

---

### Post by TheFu on 2020-11-03
> **ajgreeny said:**
>  
Th Ryzen CPUs without the G in their naming will definitely need some other graphics system available, either in the form of a separate graphics card or an integrated graphics system on the motherboard.

^^^^^ this!

The 3700X doesn't have a iGPU. You'll need to buy/install a separate GPU. The motherboard marketing doesn't mean it comes with a GPU, just that interfaces for Vega graphics from Ryzen CPUs with a "G" in the name can use the different display ports on the back of the motherboard.  BTW, Ryzen iGPU CPUs also bring some limitations to how certain motherboard features work and what speeds the PCIe slots support. 

Historically, the Ryzen 3200G and Ryzen 3400G are the 3xxxG series which have an iGPU so you don't need to buy separate.
[https://www.amd.com/en/products/apu/amd-ryzen-7-pro-4750g](https://www.amd.com/en/products/apu/amd-ryzen-7-pro-4750g) says the Ryzen PRO 4750G has 8 GPU cores, so AMD has kept the "G" in the model number standard for this Ryzen7 CPU.  Nice.

[https://www.amd.com/en/processors/ryzen-with-graphics](https://www.amd.com/en/processors/ryzen-with-graphics) is a page with all the 4xxxG processors listed. Nice that Ryzen 5 and Ryzen 7 are finally getting some love, not just the lower-end Ryzen 3 line.  But I'm pretty disappointed that **AMD isn't releasing these chips so I can build my own computer.  They are all listed as OEM only** - that means - no people like us unless we buy a complete system from a PC builder, probably like Dell. 

Appear the best Ryzen with iGPU we can buy today is Ryzen 3400G. ;(

---

### Post by rsteinmetz70112 on 2020-11-03
While AMD is not selling a retail version of the Ryzen PRO 4750G (yet) you can buy OEM versions from a number of places online. You need to provide your own cooler, which is probably a good idea anyway.

---

### Post by Yellow Pasque on 2020-11-03
> **QIII said:**
> "Integrated" graphics are integrated on the *motherboard.*  That is to say that they are soldered down.  An APU has both the "dedicated" GPU and the CPU on the same die and you lock down the whole thing in one socket.

You're using the word dedicated incorrectly there. Dedicated graphics is a chip that just does graphics. In other words, graphics on an APU are still integrated. They're just integrated directly into the CPU instead of the motherboard northbridge/chipset.

---

### Post by kurt18947 on 2020-11-03
I don't know how 20.04 and newer support the latest AMD graphics but I had a Ryzen 2200G APU on an Asrock B350 chipset motherboard. That was not a happy combination running 18.04. It did hard lockups and all sorts of unpleasant stuff. Installing HWE seemed to help a little but it still crashed. I ended up disabling the integrated GPU and installing a few years old AMD/ATI graphics card. That combo worked out reasonably well.

---

### Post by mastablasta on 2020-11-04
> **rsteinmetz70112 said:**
> While AMD is not selling a retail version of the Ryzen PRO 4750G (yet) you can buy OEM versions from a number of places online. You need to provide your own cooler, which is probably a good idea anyway.

they sell it with wraith stealth cooler here for 383 EUR+ shipping.

anyway i believe they will move the G to 5000 series and more or less skip the 4000 for desktops. at least that's what i read in the news.

---

### Post by mastablasta on 2020-11-04
> **kurt18947 said:**
> I don't know how 20.04 and newer support the latest AMD graphics but I had a Ryzen 2200G APU on an Asrock B350 chipset motherboard. That was not a happy combination running 18.04. It did hard lockups and all sorts of unpleasant stuff. Installing HWE seemed to help a little but it still crashed. I ended up disabling the integrated GPU and installing a few years old AMD/ATI graphics card. That combo worked out reasonably well.

that's odd. support should be good by now. even with pro drivers? what about PPA?

could it be the paste and cooling ? i mean in general CPUs  (APUs) work and i would understand if the first versions had issue and if early drivers had issues, but second gen? and a year or two later it should be fine. maybe not stellar still but it should have lockups and other things.

---

### Post by QIII on 2020-11-04
> **Yellow Pasque said:**
> You're using the word dedicated incorrectly there. Dedicated graphics is a chip that just does graphics. In other words, graphics on an APU are still integrated. They're just integrated directly into the CPU instead of the motherboard northbridge/chipset.

I used quotation marks on purpose.  While CPU and GPU are indeed etched together on the same die that also has an etched bus in an APU, the actual areas of the die work independently of each other.  They just do so very efficiently because of the inherent benefits of the lithography. And the area occupied by the GPU gets considerably hotter than the area with the CPU, meaning the entire thing has to be designed to bear greater heat.  But the CPU and GPU portions of the chip are in different locations and still require the bus on the chip in order to communicate.

APUs and SoCs blur the more traditional terms that I set off with quotation marks, rendering the terms somewhat archaic.  However, I would argue that "integrated" graphics still refer more to the integration of the graphics processing unit as a soldered-down component of a motherboard.  If you buy a board with "integrated graphics", there is a non-removable GPU present on the motherboard, and I suggested avoiding that. Note that I suggested "integrated graphics" as a part of the motherboard by italicizing *motherboard.*

Not trying to equivocate -- I both understand the manufacturing processes, hardware topography and terminology and I substantially agree with you -- but the OEMs still have a term for marketing the specs of their boards.  Buying a board that is advertised as having "integrated graphics" is unnecessary in these days where both AMD and Intel offer their products as they do.

I don't buy motherboards with "integrated" graphics because I use powerful multi-core CPUs and powerful GPU cards for the work I do.  If I were to use a modern laptop, I'd use an APU.

---

### Post by Yellow Pasque on 2020-11-04
> **QIII said:**
> Buying a board that is advertised as having "integrated graphics" is unnecessary in these days where both AMD and Intel offer their products as they do.

I'm not sure what you're getting at. The OP is talking about Socket AM4 boards, which all support integrated graphics (by having physical video outputs). I think you are just making things more confusing.

---

### Post by CelticWarrior on 2020-11-04
> **Yellow Pasque said:**
> I'm not sure what you're getting at. The OP is talking about Socket AM4 boards, which all support integrated graphics (by having physical video outputs). I think you are just making things more confusing.

Those support the graphics on CPU. All have to have physical video outputs, of course, how else would you use the graphics? But they don't advertise "integrated graphics", they advertise ports.

---

### Post by Yellow Pasque on 2020-11-04
> **CelticWarrior said:**
> But they don't advertise "integrated graphics", they advertise ports.

Okay, so can you or QIII give an example of a Socket AM4 motherboard that has integrated graphics in the way you define it that the OP should avoid? Also, note that the OP wants integrated graphics because the workload does not require a lot graphics power. In other words, I think QIII is trying to make a distinction that doesn't exist and unnecessarily confusing the OP. Furthermore, there's nothing wrong with integrated graphics (whether integrated into the mobo or CPU) if that's adequate for the workload.

---

### Post by kurt18947 on 2020-11-04
> **mastablasta said:**
> that's odd. support should be good by now. even with pro drivers? what about PPA?

could it be the paste and cooling ? i mean in general CPUs  (APUs) work and i would understand if the first versions had issue and if early drivers had issues, but second gen? and a year or two later it should be fine. maybe not stellar still but it should have lockups and other things.

AMDGPU installed by default IIRC. I didn't look at PPAs. The problem could also have been partially due to the motherboard, it was a return. I'm not really sure but I replaced the motherboard and processor, kept the memory and video card. That install would still lock up occasionally, a fresh install on an MSI B450 board with Ryzen 5 2600X processor (Mo' cores/threads!:P) with a few years old AMD video card using the Radeon driver seems to be working as expected.

---

### Post by mastablasta on 2020-11-04
> **Yellow Pasque said:**
> Okay, so can you or QIII give an example of a Socket AM4 motherboard that has integrated graphics in the way you define it that the OP should avoid? 

i don't know for desktop but you have on laptops Dell Inspiron 3850 (actualyl many others) or something like that that comes with 2 GPU chips. one is Intel, the other one is nvidia. intel GPU chip is on the CPU while nVidia is separate.  and that's how all laptops with nvidia optimus are made. you also have some with ryzen and nvidia. again 2 chips one is on CPU and the other one on the board.

you also have Intel Gaming NUC where you have one GPU on intel CPU and one is separate AMD Rxx chip on motherboard. only in both of these cases the setup would work. 

but they is a 2 chip setup and no dedicated card.

i don't know ho common is this on current desktop motherboards. it used to be pretty common back in the days to have nvidia motherboard chip and also nvidia GPU chip on the board itself. yet the bord was made for AMD Athlon CPU. i had one. i disabled the onboard nvidia GPU chip and added a dedicated GPU to it.

in any case this is now no longer needed (except on laptops where you might want more power than the GPU chip that is on the CPU itself can offer. quite often on gaming laptops or  portable workstations.

the Op doesn't need any of this. they should just buy a motherboard that is linux compatible and AMD chip with G nin the model name will take care of graphics. Other option is Intel chip with GPU on it. i think most models have it. but intel costs more. linux support is good though.

---

### Post by Yellow Pasque on 2020-11-04
> **mastablasta said:**
> I don't know how common this is on current desktop motherboards.

Intel moved the GPU from the motherboard to the CPU about 10 years and AMD about 8 years ago. So it's not common anymore and I'm not sure why we are telling OP about it, especially when OP wants a CPU with integrated graphics anyway. When I asked for an example of a Socket AM4 board that  had graphics integrated on the motherboard, it was a rhetorical question. There are none. (Maybe some Socket TR4 server mobos still use a very basic GPU on the board.)

---

### Post by rsteinmetz70112 on 2020-11-04
> **mastablasta said:**
> they sell it with wraith stealth cooler here for 383 EUR+ shipping.

anyway i believe they will move the G to 5000 series and more or less skip the 4000 for desktops. at least that's what i read in the news.

Interesting. In the US the only ones I could find were online OEM processors, not boxed processors with a cooler.  Where are you located?

---

### Post by mastablasta on 2020-11-05
> **rsteinmetz70112 said:**
> Interesting. In the US the only ones I could find were online OEM processors, not boxed processors with a cooler.  Where are you located?

I am in Slovenia. 

I am not sure if they are boxed. It doesn't say box.
It just says the cooler is included. and in description (translated)

AMD Ryzen 7 PRO 4750G processor, 8 cores, 16 threads, 65 W, Wraith Stealth cooler (100-100000145MPK)

they are sold like this in multiple webshops i checked online. so maybe it is a distributor decision? 
we have many odd things. for example many laptops and computers were sold with no OS (i would say about a 3rd). but lately they are filled with either FreeDOS or Linux (we had SUSE EL, some bootable linux, Asus Linux, Ubuntu...). but the prices are often the same as if you take it with Windows preloaded. so many people take the one with widnows. but every now and then they would drop prices and when they drop, those with linux get cheaper.

anothe rodity is that in Europe prices are often in same number as in US. so something that costs 100 USD would get price 100 EUR. but where i live it is often 100 EUR+ 23% VAT tax + margin, so it would often be 150 EUR or more. but it i go across the border which is min 45 minutes drive away and not max 2.5 hour (Italy) or if i order online from there i would get the 100 EUR price. so why would they sell more expensive if i can buy same thing cheaper and i am buying both online anyway?  and salaries are lower here that in say Austria, so why is any stuff generally more expensive is really puzzling.

---

