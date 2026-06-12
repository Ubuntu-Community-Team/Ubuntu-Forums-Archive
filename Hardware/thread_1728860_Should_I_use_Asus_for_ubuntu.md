---
title: "Should I use Asus for ubuntu???"
date: 2011-04-14
forum: Hardware
---

### Post by mephistux on 2011-04-14
Hey i am new in Ubuntu, i am using 10.04 now on my notebook, but i want to buy a new laptop soon and i definitely dont want to use windows on it, but i also want a quite powerful computer, so i can play games if i feel like and try some of the true power of Ubuntu.

I've done plenty of research and the laptop i like the most is an Asus G73SW, the specifications are great, the price is fine and based on all the reviews i have read (which have been quite a lot) seems to be working fine, however i see that kind of a lot of Asus' users have had problems when installing Ubuntu.*

So i just wanna know if it worth buying an Asus or if is better to use another brand. I want some opinions.
The laptop i am talking about is this one:

[http://usa.asus.com/Product.aspx?P_ID=KeYVsP7c4mgNmh2B](http://usa.asus.com/Product.aspx?P_ID=KeYVsP7c4mgNmh2B)

thank u if anybody interested

---

### Post by Joe of loath on 2011-04-14
According to 30 seconds of googling it seems to work fine!

Also, Asus build quality is great. The laptop I'm using was a class laptop at a school for 5 years, then it got thrown away and rained on before I pulled it out of a dumpster, and it still looks brand new. There is one scratch on the corner of the lid.

---

### Post by beew on 2011-04-14
Just make sure that the laptop is not Optimus enabled or the Nvidia graphic card won't work in Linux even though the card is "supported" with Linux driver. Since most new laptops with Nvidia are Optimus enabled if I were you I would do some thorough research first, perhaps by writing to Asus (the sales people I encountered are quite clueless, some don't even know what Optimus is) 

With Optimus Linux can only access the cheap Intel graphic card while the Nvidia card is still sucking power and generating heat so it is worse than a paper weight. Unless the laptop comes with a BIOS switch to disable Optimus (which is rare) the only thing you can do would be somehow hack to disable the Nvidia card and turn it into an expensive paperweight (see link below, which gives an overall explanation to Optimus) Bu if you disable the Nvidia card this way I am not sure whether the Intel card would work as well as it would stand alone (for example, I read some people cannot use Compiz even though the Intel card alone should be sufficient for that)

Many Linux users have already been burnt since all parts (including the graphic card) may be Linux compatible but with Optimus the thing would still not work.


[http://ubuntuforums.org/showthread.php?t=1657660&highlight=optimus](http://ubuntuforums.org/showthread.php?t=1657660&highlight=optimus)

---

### Post by mephistux on 2011-04-14
[QUOTE=beew;10676585]Just make sure that the laptop is not Optimus enabled or the Nvidia graphic card won't work in Linux even though the card is "supported" with Linux driver. Since most new laptops with Nvidia are Optimus enabled if I were you I would do some thorough research first, perhaps by writing to Asus (the sales people I encountered are quite clueless, some don't even know what Optimus is) 

First of all thanks 4 answering, i am glad to see that this forum actually works.


And about the topic yeah well, first i am not really good at informatics and that stuff so i can understand only the basic stuff, but i think i got your point. 
Prior to this post i went through a lot of research about all the components of the computer and well this is what I got for the video card:
[http://www.nvidia.com/object/product-geforce-gtx-460m-us.htmlhttp://www.nvidia.com/object/product-geforce-gtx-460m-us.html](http://www.nvidia.com/object/product-geforce-gtx-460m-us.htmlhttp://www.nvidia.com/object/product-geforce-gtx-460m-us.html)

If i am understanding it right (the specs tab) seems like the video card has optimus enabled, however i found some other information in a review of the computer and seems to be a little contradictory "And no Optimus? WTF Asus, WTF!" got it from this site:
[http://www.anandtech.com/show/4207/asus-g73sw-third-times-the-charm/4](http://www.anandtech.com/show/4207/asus-g73sw-third-times-the-charm/4)

On the other hand, someone told me to look up the system76 laptops since those have Ubuntu preinstalled and i was kind of surprised when i realized that this computer has the same video card as the Asus i sited above:
[http://www.system76.com/product_info.php?cPath=28&products_id=113](http://www.system76.com/product_info.php?cPath=28&products_id=113)

well if this one has ubuntu preinstalled that means that it is working fine with the video card right?? i mean they wouldnt sell something which is not working would they?

Thanks 4 your comments!!!

---

### Post by beew on 2011-04-14
> **mephistux said:**
> 

well if this one has ubuntu preinstalled that means that it is working fine with the video card right?? i mean they wouldnt sell something which is not working would they?

Thanks 4 your comments!!!


It doesn't matter if the actual card is Linux compatible, if Optimus is enabled then you won't be able to use it in Linux,period (unless there is a BIOS switch to disable Optimus but such is rare) 

With Optimus the computer switches between the high performance Nvidia card and a low performance onboard Intel card so that when performance is not required it would be handled by the Intel card. The idea is to extend battery time since the Intel card uses less power. But this only works for Win7 (doesn't even support Vista or XP) and if you use Linux you are basically screwed as you get the worst of both worlds, the Nvidia card is not usable but continues to drain battery and heat up your laptop. 

The Linux driver for the card (supplied by Nvidia!) would not work because in Optimus the Nvidia card has no direct access to display and it has to do it through the Intel card, so the Optimus setup basically turns two cards which, while on their own are Linux compatible, into a hybrid for which the Nvidia Linux driver would not work.

So that answers your question, even if the same card works for the system76 machine (which is obviously Optimus free) it doesn't mean it would work for the Asus. It depends on whether the Asus is Optimus enabled.

So make sure the Asus is not Optimus enabled, if it is then forget about it,--unless you can disable it from BIOS,-- the fact that the card works with Linux by itself is irrelevant to your purchase.

**EDITED:** This is why it is a lot more tricky to buy a Nvidia laptop nowadays. You need to research more than just the specs and the problem is most new Nvidia laptops do have Optimus (sometimes without even being explicitly mentioned) so in effect Nvida is pulling the plug on Linux laptops.

Check out also this thread and if you have time, add your voice to the chorus. I don't expect Nvidia to support gpu switching in Linux, but I wouldn't think it is unreasonable to ask them for a way to use the Nvidia cards which the users paid for and Nvidia supports with Linux drivers!
[http://ubuntuforums.org/showthread.php?t=1712278]("http://ubuntuforums.org/showthread.php?t=1712278")

---

### Post by mephistux on 2011-04-15
ok thanks man i got it
But now i have another question.. What about games?? i mean what if i want to install lets say... crysis, or gears of war that kind of games? I thought using wine or a virtual machine installed inside ubuntu or have both operative systems on the computer. But if the optimus is a trouble for Ubuntu and i can not use it then i wouldnt have the optimus technology when i am running windows too would i? if i got it right no optimus, when running on windows, means that the video card will be working but will steal a lot more energy than if the optimus was working is that correct?? so i guess that means that the video card will use a lot more power than if that's the case, however, since i wont be relying on battery power that often i guess is not a problem 4 me as long as the video card does work.. 

thanks any comments!!

---

### Post by mastablasta on 2011-04-15
If you run windows and you have Optimus you will have better energy consumption. If you have optimus you can't run Linux on it.
 
IF you want to run WINDOWS games at their fulles then you will have to run them in Windows. Wine runs only a few while virtualization takes an even more RAM and CPU power and again probably can't run these new games at their fullest.
 
if you won't be relying on battery power (and will use AC cord all the time) then why buy a notebook? you can get a very good PC for that price. Or with bigger screen. you can even make one yourself.
 
This could help you in your quest for laptop:
[http://www.ubuntu.com/certification/](http://www.ubuntu.com/certification/)

---

### Post by mephistux on 2011-04-16
> **mastablasta said:**
> If you run windows and you have Optimus you will have better energy consumption. If you have optimus you can't run Linux on it.
 
IF you want to run WINDOWS games at their fulles then you will have to run them in Windows. Wine runs only a few while virtualization takes an even more RAM and CPU power and again probably can't run these new games at their fullest.
 
if you won't be relying on battery power (and will use AC cord all the time) then why buy a notebook? you can get a very good PC for that price. Or with bigger screen. you can even make one yourself.
 
This could help you in your quest for laptop:
[http://www.ubuntu.com/certification/](http://www.ubuntu.com/certification/)
I actually considered a desktop at the beginning but in my country computers are much more expensive than the States, thats why i want to buy it there and i dont really wanna take a desktop with me in the plane. 
Also i would like a laptop cause that way i can take it out of home if needed, though i wouldnt be doing it so much. 
Thanks x the advice anyway i will take it into consideration

---

