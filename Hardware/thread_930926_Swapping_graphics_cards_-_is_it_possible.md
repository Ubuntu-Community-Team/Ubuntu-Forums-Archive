---
title: "Swapping graphics cards - is it possible?"
date: 2008-09-26
forum: Hardware
---

### Post by Bou on 2008-09-26
Hiya,

I'm facing this problem:

-I bought [this laptop](http://www.ciao.es/Sony_VAIO_VGN_FZ31E_1500__1204285) some two months ago, and it's pretty fine but its Nvidia card is giving me oh so many headaches.

-Someone in my family owns [this other laptop](http://www.acer.es/campaigns/asp_5630/), a bit crappier but with an Intel graphics card that works just fine.

My question is, would it be possible for me to get each laptop's cards and swap them, so I can get the Intel card working in the Vaio and viceversa? Or must each laptop work with the very card it came with?

---

### Post by slmkbh on 2008-09-26
In some dell families the graphics cards are swappable modules, but the general thing is that the graphics cars is integrated onto the motherboard, and usually in intels case, the chipset. 

So the short answer is no, it is not possible to swap the graphics cars in these machines. 

good luck with the nvidia driver!

---

### Post by mike1234 on 2008-09-26
> **Bou said:**
> Hiya,

I'm facing this problem:

-I bought [this laptop]("http://www.ciao.es/Sony_VAIO_VGN_FZ31E_1500__1204285") some two months ago, and it's pretty fine but its Nvidia card is giving me oh so many headaches.

-Someone in my family owns [this other laptop]("http://www.acer.es/campaigns/asp_5630/"), a bit crappier but with an Intel graphics card that works just fine.

My question is, would it be possible for me to get each laptop's cards and swap them, so I can get the Intel card working in the Vaio and viceversa? Or must each laptop work with the very card it came with?

 It would be easier to just reinstall Ubuntu. Or install on both laptops then trade. The time it takes to install Ubuntu is nothing compared to the time you will waste looking for a solution. You must have an odd nvidia card. Most, including mine work flawless.
  
sudo apt-get install nvidia-settings
gksudo nvidia-settings
save to x

M.

---

### Post by zolero on 2008-09-26
Hey, **Bou**...

**Mike** was right when wrote:
> **mike1234 said:**
> It would be easier to just reinstall Ubuntu. [...] The time it takes to install Ubuntu is nothing compared to the time you will waste looking for a solution. [...]

I just would like to suggest you the **envyng** utility beside what Mike wrote. Thus your commands should be:
```
sudo apt-get install envyng-core nvidia-xconfig

sudo envyng -t
```**Here choose 2 first, then - without restart - choose 1** ==> **reboot. **After the reboot, when you're up
```
gksudo nvidia-settings ==> ***tweak what you wish here***
```Choose **"Save to X-config"** when you're satisfied with your settings. This should solve headaches... ;-)

---

### Post by Sef on 2008-09-26
What is your graphics card?

---

### Post by zolero on 2008-09-26
> **Sef said:**
> What is your graphics card?

For the first one (Sony Vaio):

```
Gráficos NVIDIA GeForce 8400M GT 128Mb          
[LIST]
[*]Memoria gráfica total disponible 831Mb
[/LIST]


```

Fr the second (Acer Aspire):

```
• nVidia® Geforce® 7300 128/256 Turbocache
```

---

