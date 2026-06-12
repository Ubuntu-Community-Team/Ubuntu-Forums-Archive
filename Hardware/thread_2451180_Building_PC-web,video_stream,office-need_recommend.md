---
title: "Building PC-web,video stream,office-need recommendations"
date: 2020-09-28
forum: Hardware
---

### Post by sofasurfer on 2020-09-28
Wife wants a new pc. I haven't built one in years. Need suggestions. Heres what I know and what I need to know.

1) This will be used for general internet, watching video (streamed and non-streamed), office work. We do NOT play games,

2) I will install linux. I have used Ubuntu for years and been happy but I may try a different distro. Not sure.

3) I need recommendations for motherboard, CPU. memory. 

4) I have always used AMD processor and been happy. Now I read that AMD is more affordable and as good as Intel so I will stick with AMD. 

5) I think it is wise to have a graphics card other than what comes on the motherboard so I need recommendation for this. Probably doesn't take much of a graphics card now days to watch most anything.

6) I think a sound card in the motherboard is adequate.

7) I will be using a ATX tower.

8) Looking to keep the cost to a minimum or there abouts.

I can't think of anything else right now. 

I don't think this is a very complicated order at all. I just am not up on what available.

How you all will help me make some decisions. Thanks.

---

### Post by mastablasta on 2020-09-29
> **sofasurfer said:**
> 
How you all will help me make some decisions. Thanks.

Budget?

For your needs you could go with ITX, but anyway room for expansion is nice to have. also check some nice smaller boxes that will fit ATX PSU and a bunch of drives inside. 

the graphics chip is actually on the CPU. So i foyu get AMD or intel with such chip you will save on graphics card and on electricity bill.

AMD - Ryzen 3 is enough, but if oyu can go for Ryzen 5 at least. The 3000 series has good support, but if you are short on cash the 2000 series might be cheaper. also the 5000 series is coming out for desktops soon, so maybe they will rop prices on 3000!? 
the G at the model means it has graphics chip on it. Ryzen 5 3200G for example. these benefit if you have dual channel RAM (so 2x4 GB, 2x 8GB sticks...). the lower end 3000 series come with vega 8 graphics chip. here are some benchmarks for that chip: [https://www.notebookcheck.net/AMD-Radeon-RX-Vega-8-GPU-Benchmarks-and-Specs.260180.0.html](https://www.notebookcheck.net/AMD-Radeon-RX-Vega-8-GPU-Benchmarks-and-Specs.260180.0.html)

as you can see you can do quite a bit of gaming on it. so videos and office work are very fluent. as a plus the drivers are opensource.
We got Ryzen 5 3500U (this is laptop) and they can play CS:GO, minecraft, some other a bit older games. but i saw they ran some new games at low settings as well. so the GPU on this chip is really good (compared to how they were 8 years ago).

it is a similar situation if you go with intel. but equivalent motherboard and CPU can cost 30% more, yet you gain only maybe 10 % or nothing in some cases. drivers are opensource here as well and part of kernel.

boards - Asrock, Asus and Gigabyte have descent Linux support. I went with Asus. 
ram - as much as you can afford. linux manages it well so having more ram is good. get at least 8 GB ram.

SSD or nvme - at least 256 GB for system, so that browsing and such is fast. add HDD for data if you have the money. you can also survive just on spinning disk.

most of the ATX box will be empty. you can fill it up with disks or decide you want to game and add a gaming GPU card. nvidia and AMD are quite close, though i think nvidia still has some edge. AMD cards in general draw more power. maybe next architecture will be more energy efficient.

my kid saved up some money and i used some old parts (2 year old 1TB hard disk and 1 year old power supply). we got Ryzen 7 2700 (this is old model with no GPU chip), 16 GB ram, new ATX box, new Asus motherboard and he wanted to game so he bought nvidia GTX 1650 which was on sale.  in total it cost about 500 EUR if i remember correctly. i bought him a large new monitor that was on sale as a gift (the old one had VGA connection...).

the other wanted one as well + he needs one for school, but i don't have room for another ATX. so we got him a laptop with Ryzen 5 3500U, 8 GB ram and 256 GB nvme drive. he can play games for limited time per day and plays counter strike, gary mod..., or watches videos or practices for school. we added some cheap keyboard so he doesn't ruin the one on laptop. it cost us 411 EUR for laptop with no OS preloaded and we paid 6 EUR for keyboard. i gave him my old medium sized mouse. i miss that mouse...

---

### Post by sofasurfer on 2020-09-29
> **mastablasta said:**
> 

For your needs you could go with ITX, but anyway room for expansion is nice to have. also check some nice smaller boxes that will fit ATX PSU and a bunch of drives inside. 


My current PC uses a micro ATX case but I think that greatly limits my motherboard options. Plus, wife prefers a "normal" case.

---

### Post by CatKiller on 2020-09-29
> **sofasurfer said:**
> Plus, wife prefers a "normal" case.

An option that you or your wife might not be aware of, which is quite a way from a huge ATX case, is the Intel NUC. They are very cute, and Ubuntu is a supported OS so everything works without any hassle.

For non-gaming use, pretty much anything will do. Integrated graphics from either AMD or Intel are more than enough for your needs. Drivers for either are open source, so you don't need to install anything else. Get an SSD and at least 8 GB RAM (although 16 would likely be preferred), and you're golden. Go Intel as a preference for WiFi chips if you want WiFi. Onboard sound will be fine and will work unless they've messed with it as a "value add." Same with Ethernet. Corporate-focused components are the most bog standard, and the most bog standard is what's most likely to work; gaming-focused components, in particular, are most likely to be messed with and least likely to work. Pick the processor you want, which will determine your motherboard choice, and then check the QVL for the motherboard you've picked for compatible RAM modules. If you *do* go for a huge case, I favour big heatsinks and big fans that almost never come on; a big fan moving slowly makes much less noise, and moves  more air, than a small fan moving quickly, and big heatsinks mean that the fans don't even need to move slowly that often. Better power supplies are semi-passive too, so that fan only comes on if it needs to, and modular power supplies keeps the rat's nest of cables at bay.

---

### Post by sofasurfer on 2020-09-30
```
the G at the model means it has graphics chip on it
```
I was not aware that graphics cards(chips) now come on CPUs. This is a new thing, right?

```
boards - Asrock, Asus and Gigabyte have descent 
```
I have use Asus and Gigabyte. I think gigabyte has always seems to satisfy me, although I am not sure why.

```
SSD or nvme - at least 256 GB for system, so that browsing and such is fast
```
I've heard good things about ssd but I think I will stay will tried and true hard drive

---

### Post by CatKiller on 2020-10-01
> **sofasurfer said:**
> I've heard good things about ssd but I think I will stay will tried and true hard drive

Using an SSD is the single best bang-for-the-buck responsiveness improvement you can get for a computer.

Edit:
> **sofasurfer said:**
> I was not aware that graphics cards(chips) now come on CPUs. This is a new thing, right?

 Since 2010. They became part of the CPU chip, rather than the CPU package, with Sandy Bridge in 2011.

---

### Post by CelticWarrior on 2020-10-01
> **sofasurfer said:**
> 
I've heard good things about ssd but I think I will stay will tried and true hard drive

Another place, another time:

I've heard good things about (motor)car but I think I will stay with tried and true horse carriage.

---

### Post by TheFu on 2020-10-01
Not all CPUs include a gpu too. Intel has them in more models. AMD has them in specific Ryzen models - loook for a 'g' so a ryzen 2200g or 2400g would include iGPUs. The higher end ryzen CPUs don't include iGPUs.  I think some Core i9 do not either along with xeons.

You really do want to use an SSD. The lifespans on quality SSDs are longer than for HDDs, by far. Just stick with well-known brands with the durability specs needed.  Lots of vendors refuse to publish endurance specs. Avoid those.  I've researched SSDs after being burned with cheap versions a few times.  The easy answer is to by Samsung 8xx or 9xx series. Don't confuse sandisk and samsung. when it comes to SSDs, there is a huge difference.  Every once in a while, if you watch closely, pricing mistakes for enterprise SSDs happen from non-consumer brands. I've lucked out once and got an enterprise SSD for less than a consumer samsung version.

Still use HDDs for large storage needs too. Having both works.

---

