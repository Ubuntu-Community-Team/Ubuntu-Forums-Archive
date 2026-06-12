---
title: "New laptop- need some confirmations about graphics"
date: 2011-02-13
forum: Hardware
---

### Post by kinggo on 2011-02-13
I have (well, had :( ) hp tx1000, and I've been using ubuntu since 8.04.
Now, I need a new machine but I'm quite confused with all this graphics issues now. If I understand correctly, all i3 and i5 intel chips already have Intell HD Graphics built in. And that would be enough performace vise. Compiz should work fine and HD videos should also work fine. But the problem is that I don't have many options for 17" with i3 and integrated graphics.
So the questions is, what now. I was always fan of nvidia, but optimus is no go for now. Also, finding the laptop with BIOS option for switching of integrated GPU is impossible. None is listing something like this in specs. I know that I don't have to install drivers and I can use only intel GPU, but whats the point. Nvidia still works and produce aditional heat.
What about i3 + ATI. I've been reading about switcheroo but experinces are from good to none working. And if I understad it correctly activating ATI card once should be enough.
 I don't care about battery life, but I'm worried about overheating.

---

### Post by fjgaude on 2011-02-13
Compiz works fine with Intel HD GPU built-into most i3 and i5 CPUss. So what's the issue... buy a laptop from Dell!

---

### Post by cascade9 on 2011-02-14
Considered an AMD laptop? No optimus to worry about, and you dont have to deal with intel video either. 

If you get an AMD laptop with a single ATI/AMD GPU, then it should be hassle free.

---

### Post by kinggo on 2011-02-15
> **fjgaude said:**
> Compiz works fine with Intel HD GPU built-into most i3 and i5 CPUss. So what's the issue... buy a laptop from Dell!
Well, the only not so expensive dell avilable with i3 is inspiron N5010. But that is 15". Dell in my coutry is about 70-80% more expensive than the prices on Dell's web. :( The cheapest 17" is over 1000€ and has nvidia GT 330M. Is it optimus or not? I can't find that info and the seller doesn't even know what optimus is. 
Toshiba with more RAM an bigger HD but with ATI is 30% cheaper. 
The problem is that I don't have many options for 17" with intel HD. Actually, tho only one I found so far is Asus K72F and they only have brown one :(
And buying something that can't be used and also generetes unwanted heat makes no sense.

---

### Post by kinggo on 2011-02-15
> **cascade9 said:**
> Considered an AMD laptop? No optimus to worry about, and you dont have to deal with intel video either. 

If you get an AMD laptop with a single ATI/AMD GPU, then it should be hassle free.
Well. the same is with single intel card. But the problem is that a lot of i3 models has aditional card. If it is nvidia optimus it won't work at all. If it is ATI than maybe I wpuld be abel to use it. But it's hard to tell. Depends how lucky I am.
And AMD ATI combination would also be fine. But I'm not so much into new AMD processors and I don't know if they even have somethig that is running on so low power as intel and with so low heat emmision. And what if I buy something that has also integrated graphich and discrete one. As far as I know before optimus we had switchable graphics. Some laptops even have a dedicated switch just for that.

---

### Post by mastablasta on 2011-02-15
HP has laptops with i3 and ATI cards with openSUSE preloaded. If openSUSE works there Ubuntu will probably work just as well.
 
UPS 17" then maybe Dell (intel HD) and Asus (though they have ATI)
 
EDIT: where are you from?

---

### Post by cascade9 on 2011-02-15
> **kinggo said:**
> Well. the same is with single intel card. But the problem is that a lot of i3 models has aditional card. If it is nvidia optimus it won't work at all. If it is ATI than maybe I wpuld be abel to use it. But it's hard to tell. Depends how lucky I am.
And AMD ATI combination would also be fine. But I'm not so much into new AMD processors and I don't know if they even have somethig that is running on so low power as intel and with so low heat emmision. And what if I buy something that has also integrated graphich and discrete one. As far as I know before optimus we had switchable graphics. Some laptops even have a dedicated switch just for that.

Believe it or not, the most of the newer mobile phenoms are actually rate at the same or less TDP (thermal design power) than most of the iX mobile CPUs. 

AMD so far isnt really doing intergrated GPUs (yet), so as long as you get a laptop with just one GPU you wont have any switchable graphics problems.

---

### Post by kinggo on 2011-02-15
Guys, if I understand correctly, there's no combo of integrated+discrete that will work as it is intended. That's why I'm looking for integrated intel HD. But almost all 17" I found so far are combos. Apart from some with core duo but that's pretty old nowdays. And with AMD I found only Asus k72f i Acer Aspire 7551. 
And AMD:intel ratio is around 1:6 here. :confused: 
**@mastablasta ** croatia

---

### Post by cascade9 on 2011-02-17
I'm pretty sure that with a little hacking, switchable graphics works just fine. Porbably not with all models however, so it would take a little work to figure out what is good and what should be avoided. 

AMD laptops are always harder to find. 

If you really want a 17''+ laptop with intel video only, try looking for an Asus K72F (K72F-TY129V)

HP Probook 4720s (various sub-models) are meant to work pretty well with linux from what I've heard. They have ATI 6370 GPUs, not intel GMA- 

[http://www.linlap.com/wiki/hp+probook+4720s](http://www.linlap.com/wiki/hp+probook+4720s)

---

### Post by typhoon_tip on 2011-02-17
Go for anything that uses ATI, they are doing a great job with their Catalyst driver, and is totally integrated with Kernel updates. I have had numerous problems with NVIDIA and Kernel updates, while Intel also being not stable.

---

### Post by kinggo on 2011-02-17
**@ cascade9**
everything is an option. The bottom line is that I don't want to buy something that can't be fully usable. Thats all. 
**@ typhoon_tip**
I never had any problems with intel GMA or nvidia. But I know that ATI was somehow problematic back in the days when I started with linux. So I was always avoiding it. I don't know how it is now. But even if it works fine, switchable graphics is still a problem. And as I said, number of AMD models is way lower then intel models.

---

### Post by typhoon_tip on 2011-02-17
> **kinggo said:**
> **@ typhoon_tip**
I never had any problems with intel GMA or nvidia. But I know that ATI was somehow problematic back in the days when I started with linux. So I was always avoiding it. I don't know how it is now. But even if it works fine, switchable graphics is still a problem. And as I said, number of AMD models is way lower then intel models.

I don't know about the past personally, but I suspect you may be correct. Now is totally reversed. I have an IT company and we are installing hundreds of computers (mainly new, some of them with Ubuntu) and are having troubles with Intel integrated graphic (especially some models, forget 3D at all) and NVIDIA (at kernel update the system won't restart anymore or start with a broken video driver...).

The switchable graphic is not an issue of ATI, also because NVIDIA has the same thing. Just kill the function from the BIOS or hardware switch (some VAIO notebook use the speed/stamina switch to control switchable graphic) and ... there you go !

):P

---

