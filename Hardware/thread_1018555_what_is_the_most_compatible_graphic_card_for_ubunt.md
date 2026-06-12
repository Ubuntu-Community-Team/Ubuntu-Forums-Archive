---
title: "what is the most compatible graphic card for ubuntu? (AGP &amp; PCIe)"
date: 2008-12-22
forum: Hardware
---

### Post by shinew on 2008-12-22
Hi, I need to buy another graphic card for my desktop. I've been using ATI 9600 Pro for many years now on windows but I just installed Ubuntu on it 2 days ago(and I"m loving it!!) and I've decided to use it as my main OS. 

the problem is that I couldn't configure it to work with my dual display(28"@1920x1200 & 21"@1600x1200). I really need dual output, and I've heard that NVidia cards are more compatible in linux than ATI. I would like to spend as little as possible on a AGP card (i know, upgrading soon.. :P) which can handle both of my display resolution w/ all the eye candy in ubuntu effortlessly. I also don't play games on computer.

so please click that "reply" button NOW if you're familiar with this. thanks! :D
p.s. a recommendation for a PCIe card with the same requirement is also appreciated since I'm building another computer soon.

---

### Post by markbuntu on 2008-12-22
Don't bother with agp if you are building a new system soon, agp is over.

There is a lot of controversy about ati vs nividia in the linux community and there are die hard partisans on both sides due mostly to past missteps by ati before they were bought by amd. 

The situation now is that ati is rapidly improving their proprietary driver and giving full support to the open source driver writers so those drivers are also rapidly progressing. Nvidia, though their proprietary drivers may be better than the ati drivers at the moment, is still not giving support to the open source driver writers.

So, if you have nvidia there is a good chance you will be stuck with proprietary drivers for a long time and if you have ati there will be a open source driver for you in the near future.

---

### Post by nick09 on 2008-12-22
AGP is not exactly over as they still make cards for the AGP slots. Its just cost worthy if you are still gonna use the older system for a while. As Markbuntu said, ati is getting better and nividia has good drivers but I'm not so certain about the future development.

---

### Post by shinew on 2008-12-23
So which one is the best choice based on my criteria now? As far as i'm concerned, ATI's native driver support sucks. I can't even configure a dual-head card to support dual display, and the video play back at full screen is very choppy.

I'm aware that AGP is a thing of the past already, but I'm still fairly happy with my system's performance, it got a AMD64 x2 2.6Ghz CPU, a8v delux motherboard & 3GB ram. So I'll keep using it as a secondary system even after I've built a new one.

so which one? :D thanks!

---

### Post by jrusso2 on 2008-12-23
I sure would not buy a video card hoping the drivers improve sometime in the future.  In the mean time most of the Nvidia cards work well with the Nvidia drivers I don't care they are not open.

I would beware of any card thats less then a year old though and make sure support is in Linux.

---

### Post by shinew on 2008-12-23
> **jrusso2 said:**
> I sure would not buy a video card hoping the drivers improve sometime in the future.  In the mean time most of the Nvidia cards work well with the Nvidia drivers I don't care they are not open.

I would beware of any card thats less then a year old though and make sure support is in Linux.

cool thanks! any specific model/chipset you can recommend? again, my requirement in order of importance:
1) dual head support(being able to also support rotation would be a MAJOR plus)
2) hi-res(may 1920x1200 X 2) support & smooth video play back at full screen, I would also like to be able to enable as much eye candy as i want without slowing down.
3) as cheap as possible, NO FANS on the graphic card.

thanks!

---

### Post by jrusso2 on 2008-12-23
> **shinew said:**
> cool thanks! any specific model/chipset you can recommend? again, my requirement in order of importance:
1) dual head support(being able to also support rotation would be a MAJOR plus)
2) hi-res(may 1920x1200 X 2) support & smooth video play back at full screen, I would also like to be able to enable as much eye candy as i want without slowing down.
3) as cheap as possible, NO FANS on the graphic card.

thanks!

I am running an 8800 GT which is PCI-E and a 7600 GS which is AGP in this PC.  And both work well. They both have fans however as most of the higher end cards have fans.

---

### Post by shinew on 2008-12-23
> **jrusso2 said:**
> I am running an 8800 GT which is PCI-E and a 7600 GS which is AGP in this PC.  And both work well. They both have fans however as most of the higher end cards have fans.

can you also rotate them 90 degree if you want to?

---

### Post by shinew on 2008-12-30
just to make a final update. I ended up purchasing a GeForce 6200 and it works beautifully in TwinView mode on Ubuntu 8.10 w/ driver version 177(works better than 173). The installation was as easy or or easier than installing a driver on a windows machine. So I'll definitely get an nvidia card for my new desktop.

---

