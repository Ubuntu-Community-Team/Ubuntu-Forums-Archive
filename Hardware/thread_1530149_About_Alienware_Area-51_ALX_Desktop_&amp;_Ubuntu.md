---
title: "About Alienware Area-51 ALX Desktop &amp; Ubuntu"
date: 2010-07-13
forum: Hardware
---

### Post by mesaphlin on 2010-07-13
Hello everyone,

I just want to purchase an Alienware Area-51 ALX Desktop Computer and install the Ubuntu in it and get rid of the Windoze.

I have read the threads about this Alienware beauty and Ubuntu compatibility in this forum but all the threads I came across with were all for the Alienware Laptops but not about the Desktops. 

Anyone could tell me that I could install the latest Ubuntu OS on this machine without any problems? (I don't want to deal with general problems that happened to other users in Alienware Laptops with Ubuntu)

Thanks in advance

Yigit

=)

---

### Post by AltomineUK on 2010-07-13
Aside from possible GPU driver & NIC issues I can't seem to find any cause for concerns.....

Someone please correct me if I'm wrong....

---

### Post by mesaphlin on 2010-07-13
I also have a question in my mind that I would like to share with you...

What if I build up a barebone PC just for Ubuntu - nothing else,.. then what computer components should I emphasize the most in order to install Ubuntu without any problems?

Could it be the Graphic card, or the motherboard, or else?

If there are some computer components on the market that work flawlessly with Ubuntu, could you give me some names of those products please?

Thank you

Yigit

---

### Post by AltomineUK on 2010-07-13
Hello again,

May I ask you what is the purpose of the system you wish to build? What would you like to use your PC for? I can advise you best if I could know this....

Thanks

---

### Post by mesaphlin on 2010-07-13
> **AltomineUK said:**
> Hello again,

May I ask you what is the purpose of the system you wish to build? What would you like to use your PC for? I can advise you best if I could know this....

Thanks

Actually, I want an Ubuntu system that allows me to use the top-notch graphical elements like compiz etc... in the first place - so I need a very good graphic card I assume. And also I could be able to write C code to execute some programs so I need i7 based Intel chip. On top of all, the system should fly in the air when it is running so cooling factor should be silent also - so do I need a system with fans or with the liquid-type of cooling?

In short, I want the best of the best which is totally compatible with Ubuntu.

I hope I dont look like a monster after all I said those things...

Thank you so much for helping me!!!...

Yigit

---

### Post by AltomineUK on 2010-07-13
> **mesaphlin said:**
> Actually, I want an Ubuntu system that allows me to use the top-notch graphical elements like compiz etc... in the first place - so I need a very good graphic card I assume. And also I could be able to write C code to execute some programs so I need i7 based Intel chip. On top of all, the system should fly in the air when it is running so cooling factor should be silent also - so do I need a system with fans or with the liquid-type of cooling?

In short, I want the best of the best which is totally compatible with Ubuntu.

I hope I dont look like a monster after all I said those things...

Thank you so much for helping me!!!...

Yigit

Haha, no you don't look like a monster....but i can help you.

Running compiz does not require "Top End" graphics cards. For example, i'm running my Ubuntu 10.04 LTS Desktop Edition on my netbook and here are its spec:

Processor: Intel Atom N270 @1.60 GHz (with HT)
                            : 512kb Cache
                            : 533 MHz or so FSB

RAM        : 1GB DDR2 @600-800MHz (not too sure of the clock speed)
HDD        : 160GB SATA @ 5,400 RPM
DISPLAY  : 1240 x 600 LED
GPU        : Intel 945 GME Integrated Media Accelerator

And compiz runs perfectly well on this system. I've got cube, wobbly windows and such running around and it runs just fine. That's the thing about Linux....you don't need high spec machines to get results!!

Of course, if you intend to run graphics intensive applications such as intense gaming, 3D rendering, hardcore photo/video editing you might want to have a look at somewhere around the NVidia 250 GTS or above... ATi support on Ubuntu is a bit shady at the moment so becareful of the ATi chipsets.

If you are into complex programming, along with all that 3D stuff I had mentioned earlier and require things to get done quickly (such as compiling, linking, running etc) then you might want to look at something like a Core 2 Duo or Core i3, i5s..... but please note that there are some kernel issues with the Core i-series, which requires update-to-date linux kernels to get the most out of them. Personally, I would go for Pentium Dual Core or even the dual core Atom platform with the NVidia Ion graphics. Both of these are more than capable of handling most of what you want to do quite easily (in Linux). 

If you really, really want an Extreme PC built from the ground up for running Ubuntu, you might consider building something a bit like this:

[http://www.system76.com/product_info.php?cPath=27&products_id=94](http://www.system76.com/product_info.php?cPath=27&products_id=94)

As for cooling, Water cooling is more efficient than air cooling. Your PC can run more silently if it's water cooled and can provide a higher overclocking capacity. That said, you have to be cautious about bringing water and electronics together and air cooling systems are easier to install and have far less components to go wrong.... unless you use a lot of fans....

I mean, this was just a brief overview of things....if you have any specific queries, just post them and I'll be happy to help you out =)

---

### Post by mesaphlin on 2010-07-14
Dear AltomineUK,

First of all, I would like to thank you for helping me. I really appreciate it. ;)

Actually, I have some questions..

* ((1)) You mentioned about NVidia 250 GTS or above for the graphic card. Well, I guess I will buy the...
          (*) 1536 MB nVidia GeForce GTX 480 Graphic Card. I think there will be no problem with this specific card under Ubuntu.
What do you think?


* ((2)) You also mentioned about some kernel issues with the Core i-series, which requires update-to-date  linux kernels to get the most out of them. Well I am thinking about getting the...
          (*) Intel Core i7 975 3.33GHz 8MB Cache LGA 1366 Processor.
I think every week, sudo apt-get update command in the Terminal will do its job. Don't you think?

* ((3)) I also want to ask you about the motherboard - is there any good motherboard for i7 core processor on your mind? Or any of them which is compatible with i7 core processor fits okay with it.

* ((4)) The other thing pops up in my mind that the 32-bit or 64-bit Ubuntu. I know that some programs are still for 32-bit but time is going by and soon I think major population of the programs will go for 64-bit. So if I build up a top-notch PC now, so do you think I go for the 64-bit instead of 32-bit?

Dear AltomineUK,

Sorry to ask you a little too much questions but you are really helping me - I cannot thank you much enough for that.

Please take care of yourself so much...

Yigit

):P

---

### Post by AltomineUK on 2010-07-14
1) A very powerful choice. I see no reason as to why such a capable card wouldn't run on Ubuntu. I think Ubuntu does offer a suitable driver for this by default. 480 GTX is a lot of graphics and a lot of power.

2) Ah I wish it was that simple, but it is not. You have to download the kernel deb. file manually and install it. sudo apt-get update only updates user-software. They do occasionally release updated versions of the kernel along with other system updates, but this happens bit too slowly. 

3)As for motherboards, Asus and Gigabyte are my personal favourites. Intel Core i7 will generally fit into any X58-motherboards such as Gigabyte GA-X58A-UD3R or Asus P6X58D-E. The socket type of the i7 is 1366, so just make sure that it has the socket. The examples I have given support things like SLi/Crossfire, Triple Channel DDR3 capabilites etc. If you want to go over the top then there is the Asus Rampage III Extreme which is very, very robust and you'll not need another motherboard for a looong time. Gigabyte GA-X58A-UD9 also has similar features.

Two more to consider are Asus P6T Deluxe V2 and Asus P6 X58D Premium. All these are based on the fact that you want  a good performance system.

4) Yes, we are slowing moving into the realms of the 64-bit. I chose 32-bit for my PC because of compatibility, availability of software and stability. 64-bit support is not quite there yet, but we are fast approaching. Even flash 64 is not fully available from the repositories. You have to get it from the Adobe Labs. By all means go for the one you feel most comfortable in. 64-bit should speed things up and should be slightly more secure than 32-bits.

---

### Post by mesaphlin on 2010-07-14
Dear AltomineUK,

Thanks for everything...

I have a last question... :rolleyes:

I also need a good Ubuntu installed laptop for mobility.

I checked the latest Alienware M-Series laptops but I have read that they have some problems on Audio etc... if the Ubuntu installed on them -- besides the battery-life is 1 hour or so on those laptops. It looks cool but hey we need some other aspects too as you know.

So do you recommend any other brand of laptops for Ubuntu? Like Lenovo for example... (I like the LENOVO                             G550 CORE2 DUO actually - also I have read in this forum that everything works out of the box when ubuntu is installed in it. I think Beryl Cube - Compiz and other desktop environments might work with that axe without any hassle..)

That's it!!!...

I promise you I won't bother you again...

:p ;)

Thank you so much for your kindness and understanding.

Yigit

:redface:

---

### Post by AltomineUK on 2010-07-15
Hahaha.... no problem!!!

If you are happy with the Lenovo and you didn't find any problems with it then go for it. If the forum said everything works out-of-the-box then that's great!!! I kinda find it hard to come across a laptop where EVERYTHING works. Yea, although they have huge amounts of processor and graphics power, Alienware has issues when you put Ubuntu on it so it'd be best not to go for it unless you know the work-around for it.

I have chosen a netbook, where pretty much everything is Intel and so everything just works.

---

### Post by cascade9 on 2010-07-15
> **mesaphlin said:**
> Actually, I want an Ubuntu system that allows me to use the top-notch graphical elements like compiz etc... in the first place - so I need a very good graphic card I assume. And also I could be able to write C code to execute some programs so I need i7 based Intel chip. On top of all, the system should fly in the air when it is running so cooling factor should be silent also - so do I need a system with fans or with the liquid-type of cooling?

You dont need a very powerful card to run compiz. 

C code should work fine on any CPU, you dont need an i7 for that. 

Water cooling kits are overrated, and custom built water cooling isnt exactly easy.... Even stock heatsinks/fans these days are pretty good, but if you want somethign quieter than the stck cooling a nice aftermarket heatsink with a 120mm fan is the way to go. 

> **mesaphlin said:**
> * ((1)) You mentioned about NVidia 250 GTS or above for the graphic card. Well, I guess I will buy the...
          (*) 1536 MB nVidia GeForce GTX 480 Graphic Card. I think there will be no problem with this specific card under Ubuntu.
What do you think?


Dont get a GTX480 unless you to play a huge amount of games.....and you dont mind a loud system. They are loud, very hot (which makes it much harder to keep quiet) and use a lot of power. 


> **mesaphlin said:**
> 

* ((2)) You also mentioned about some kernel issues with the Core i-series, which requires update-to-date  linux kernels to get the most out of them. Well I am thinking about getting the...
          (*) Intel Core i7 975 3.33GHz 8MB Cache LGA 1366 Processor.
I think every week, sudo apt-get update command in the Terminal will do its job. Don't you think?

sudo apt-get update will just get the newest updates for your system as provided by ubuntu. If the newer kernel isnt in the updates, then it wont help at all. 

IIRC 'truboboost' is teh main thing missing from the current linux kernel used by ubuntu. I'm not sure if that is going to be 'backported' into the current kernel. 

> **mesaphlin said:**
> 
* ((4)) The other thing pops up in my mind that the 32-bit or 64-bit Ubuntu. I know that some programs are still for 32-bit but time is going by and soon I think major population of the programs will go for 64-bit. So if I build up a top-notch PC now, so do you think I go for the 64-bit instead of 32-bit?

I'd go with 64bit. You could check the software you are planning on running, but with almost everything there is a 64bit version, or you can get things going with 'force architecture'

---

### Post by mesaphlin on 2010-07-15
Thanks for the info cascade9

I really appreciate it...

Yigit

---

### Post by mesaphlin on 2010-07-19
Hello,

I have found a nice deal for Alienware Aurora ALX Desktop Computer.

The graphic card is ATI® Radeon HD 5870 (1 GB GDDR5).

Does it work with Ubuntu flawlessly? Any ideas?

Thanks in advance.

Yigit

:rolleyes:

---

### Post by cascade9 on 2010-07-20
HD 5870 should work fine in linux...but he ATI cards still have less features than the nVidia cards, and IMO are more likely to have issues with drivers, etc. 

As for wanting a 5870 in linux....I dont see why. Not many linux games are going to need that amount of power. Are you planning on dual-booting with windows and using windows for games almost all the time? 

It would need to be an amazing deal for alienware to be worth looking at, the alienware computers are just really expensive dells these days.

---

### Post by mesaphlin on 2010-07-21
> **cascade9 said:**
> HD 5870 should work fine in linux...but he ATI cards still have less features than the nVidia cards, and IMO are more likely to have issues with drivers, etc. 

As for wanting a 5870 in linux....I dont see why. Not many linux games are going to need that amount of power. Are you planning on dual-booting with windows and using windows for games almost all the time? 

It would need to be an amazing deal for alienware to be worth looking at, the alienware computers are just really expensive dells these days.

Dear cascade9,

I want to reformat it and install only ubuntu in it. I am fed up with windoze. I am not a gamer but of course sometimes I play games but not that hardcore... ( I wanna play the top-notch linux games of course)

There are two options for me for the Alienwares...

(1) Alienware Area 51 ALX comes with Dual SLI nVidia® GeForce GTX295 VGA (1.8 GB) which is good because it is nVidia (compatible with Ubuntu) but it is too much for regular use of Ubuntu and plus it is 6929  USD?

(2) Alienware Aurora ALX comes with ATI® Radeon HD 5870 (1 GB GDDR5) and as you say "still have less features than the nVidia cards, and IMO are more likely to have issues with drivers, etc." which terrifies me whether if I will have problems using Ubuntu with it after I pay for it like 3775  USD?

:confused:

---

### Post by cascade9 on 2010-07-22
Even 1 GTX295 is overkill for ubuntu. 2 cards in SLI is just gouing to make a lot more heat, and possible issues from SLI. 

$6929 US? I checked the alienware site, and it had 'starting from $3,999' for the Area 51 ALX and 'starting from $2,199' for the Aurora ALX. Are you ticking every option you can in the 'customise' screen? 

Those prices are way to high, you could get a really nice machine for far less than that.

---

### Post by mesaphlin on 2010-07-23
> **cascade9 said:**
> Even 1 GTX295 is overkill for ubuntu. 2 cards in SLI is just gouing to make a lot more heat, and possible issues from SLI. 

$6929 US? I checked the alienware site, and it had 'starting from $3,999' for the Area 51 ALX and 'starting from $2,199' for the Aurora ALX. Are you ticking every option you can in the 'customise' screen? 

Those prices are way to high, you could get a really nice machine for far less than that.

Dear Cascade9,

I am in Turkey so the prices are higher here. :( 

Would you please tell me the best components for Ubuntu if I may ask? I really want to have a nice machine for Ubuntu which will last at least 5 years.

Thank you so much!!!...

Yigit

---

### Post by SPARTAN-001 on 2010-07-23
You don't need a good computer for Ubuntu. Ubuntu will run on pretty much any hardware, and an Alienware is way overkill for just running Ubuntu, unless you're planning on doing serious computing (Folding @ Home, Blender, etc.) I'd recommend an i5 with something like a GTX 460 and 4GB of RAM. You don't need more if you aren't gaming or doing serious computing, and any more would just be wasteful. An i5 would be powerful enough for most things, and you will never need a GTX 480/ HD 5870 for Ubuntu, unless you're using the Folding @ Home GPU client. 4 GB of RAM is also more than enough for Ubuntu. Save yourself the money, and don't buy a crazy system for Ubuntu. You really don't need it. :)

---

### Post by PresenceofMind on 2010-07-23
> **SPARTAN-001 said:**
> You don't need a good computer for Ubuntu. Ubuntu will run on pretty much any hardware, and an Alienware is way overkill for just running Ubuntu, unless you're planning on doing serious computing (Folding @ Home, Blender, etc.) I'd recommend an i5 with something like a GTX 460 and 4GB of RAM. You don't need more if you aren't gaming or doing serious computing, and any more would just be wasteful. An i5 would be powerful enough for most things, and you will never need a GTX 480/ HD 5870 for Ubuntu, unless you're using the Folding @ Home GPU client. 4 GB of RAM is also more than enough for Ubuntu. Save yourself the money, and don't buy a crazy system for Ubuntu. You really don't need it. :)

Hello,

I agree with SPARTAN-001. Ubuntu (and Linux in general) really doesn't need all those exotic stuff to run smoothly unless you aim to go HARDCORE.....

I also agree with Cascade9. 2X 295 GTX is a lot of horsepower and a lot of heat and if you just want a "nice computer"..... it's a waste of money as well. You have to choose your machine that fits your purpose.

---

### Post by cascade9 on 2010-07-24
> **SPARTAN-001 said:**
> You don't need a good computer for Ubuntu. Ubuntu will run on pretty much any hardware, and an Alienware is way overkill for just running Ubuntu, unless you're planning on doing serious computing (Folding @ Home, Blender, etc.) I'd recommend an i5 with something like a GTX 460 and 4GB of RAM. You don't need more if you aren't gaming or doing serious computing, and any more would just be wasteful. An i5 would be powerful enough for most things, and you will never need a GTX 480/ HD 5870 for Ubuntu, unless you're using the Folding @ Home GPU client.

I wouldnt go as far as a GTX460 unless gaming is going to be the main use for the computer. A nice GT220/GT240 will do everything on the desktop just as well as an expensive, hot and power hungry GTX 460. 

I'd probably go for an AMD over an Intel i5, but that is from personal preference and better performance for the money.

---

### Post by SPARTAN-001 on 2010-07-24
Well, you have to have some bragging rights, no? :p
Otherwise, I would agree with the 240 or 220. They would perfectly fine for Ubuntu. An AMD CPU would also work nicely for Ubuntu. Something like the Athlon II X4 640 or lower even provide great power at an even better price. $100 for a quad core is something that Intel can't beat, even if the performance is a bit less than the i5.

---

### Post by mesaphlin on 2010-07-28
Thanks for your opinions...

I will not go crazy about the best system peripherals then...

Thanks again...

):P

:)

---

### Post by cascade9 on 2010-07-29
Good luck ;) 

Just a pity I lost contact with the Turkish guy I knew, he actually knew where to get good systems in Turkey......well, Istanbul anyway :)

---

