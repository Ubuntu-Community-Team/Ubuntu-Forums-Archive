---
title: "[SOLVED] can i run windows vista inside linux"
date: 2008-08-06
forum: General Help
---

### Post by cowboyup6983 on 2008-08-06
i am still new to ubuntu and i wanted to know is there a way i can run windows inside ubuntu. i wanted to be able to play games like crysis or call of duty 4, but not have to boot into windows...

i dont know which would be better VMware or other? please let me know how to install VMware or other software, and will i be able to play games, i know vista comes with direct x 10 so does this mean i should be able to play? 

thanks in advance for the help!~!

---

### Post by billgoldberg on 2008-08-06
> **cowboyup6983 said:**
> i am still new to ubuntu and i wanted to know is there a way i can run windows inside ubuntu. i wanted to be able to play games like crysis or call of duty 4, but not have to boot into windows...

i dont know which would be better VMware or other? please let me know how to install VMware or other software, and will i be able to play games, i know vista comes with direct x 10 so does this mean i should be able to play? 

thanks in advance for the help!~!

I'm pretty sure you can run Vista in a virtual machine (virtualbox, ...) but it will be impossible to play games that require direct x.

You could try playin COD4 and Crysis with WINE (wine is not an emulator) but it will be a pain in the *** getting it to work, if it's even possible.

So if you want to game, do like me, keep a small winxp or vista parition.

---

### Post by cowboyup6983 on 2008-08-06
> **billgoldberg said:**
> I'm pretty sure you can run Vista in a virtual machine (virtualbox, ...) but it will be impossible to play games that require direct x.

You could try playin COD4 and Crysis with WINE (wine is not an emulator) but it will be a pain in the *** getting it to work, if it's even possible.

So if you want to game, do like me, keep a small winxp or vista parition.

can someone tell me how to install virtualbox, i want to add XP or Vista to run inside ubuntu to play games like crysis or call of duty

---

### Post by Ryadt on 2008-08-06
In terminal do```
sudo apt-get install virtualbox-ose
```

---

### Post by jonian_g on 2008-08-06
You can't play windows games with virtual machines. It doesnt matter if it is wmware or virtualbox. Only with wine.
The best solution is dual boot.

---

### Post by Locutus_of_Borg on 2008-08-06
sudo apt-get install frozen-bubble ascii-invaders tuxkart cowsay

gaming problem solved


srsly though, virtual machines do not emulate graphics

---

### Post by nbayiha on 2008-08-06
@cowboyup6983 
Actually if you want to run game like COD4 you will need wine installed to be able to play it. With a virtual machine i don't think you will play it.
And Crysis is still not playable throw Wine , cause he required to much power. 
So just do a search on the forum about Wine and COD4 and they will explain you how to set it up.
You don't need a Virtual Machine to play those game, if that's what you are looking for.

> You could try playin COD4 and Crysis with WINE (wine is not an emulator) but it will be a pain in the *** getting it to work, if it's even possible.
 Actually as i read in the forum , it's pretty easy to make COD run throw wine. But for crysis is probably impossible.

---

### Post by cowboyup6983 on 2008-08-06
> **nbayiha said:**
> @cowboyup6983 
Actually if you want to run game like COD4 you will need wine installed to be able to play it. With a virtual machine i don't think you will play it.
And Crysis is still not playable throw Wine , cause he required to much power. 
So just do a search on the forum about Wine and COD4 and they will explain you how to set it up.
You don't need a Virtual Machine to play those game, if that's what you are looking for.

 Actually as i read in the forum , it's pretty easy to make COD run throw wine. But for crysis is probably impossible.

kwel. so can someone tell me the best way to install wine, on my PC. ive look a little online, but i kinda would like an offical way from here. thanks all!

---

### Post by Locutus_of_Borg on 2008-08-06
```
wget http://ibiblio.org/pub/linux/system/emulators/wine/wine-1.0.tar.bz2
tar -xjf wine-1.0.tar.bz2
cd wine-1.0
./configure
make
sudo make install
```

it does take a long time to compile

alternatively, ```
sudo apt-get install wine
``` will get you some version that is available in the repos. its a bit quicker, but i dont know if its the latest (stable) version

---

### Post by cowboyup6983 on 2008-08-06
wget [http://ibiblio.org/pub/linux/system/emulators/wine/wine-1.0.tar.bz2](http://ibiblio.org/pub/linux/system/emulators/wine/wine-1.0.tar.bz2)
tar -xjf wine-1.0.tar.bz2
cd wine-1.0
./configure
make
sudo make install


do i just copy all this into a terminal??

---

### Post by Locutus_of_Borg on 2008-08-06
well, one line at a time, but yeah, essentially

---

### Post by kidux on 2008-08-06
> **jonian_g said:**
> You can't play windows games with virtual machines. It doesnt matter if it is wmware or virtualbox. Only with wine.
The best solution is dual boot.

You can play windows games with VM's, just not 3d accelerated ones. I play the Fallouts, Baldur's Gate's, etc in a VM all the time, and it's much easier and stable than WINE.

---

### Post by cowboyup6983 on 2008-08-06
cant i just go to add/remove and type in wine under search and install that way. or is it not a complete install and stable version of wine

---

### Post by tuxxy on 2008-08-06
Goto synaptic and search for it instead.

---

### Post by mb_webguy on 2008-08-06
The version of Wine in the Ubuntu repositories is somewhat out of date.  Follow the instructions on the [Wine website]("http://www.winehq.org/site/download-deb") to add their repositories and *then* install it through Synaptic.

---

### Post by Locutus_of_Borg on 2008-08-06
> **cowboyup6983 said:**
> cant i just go to add/remove and type in wine under search and install that way. or is it not a complete install and stable version of wine

yes you can do it that way, i'm just not sure if its wine-1.0 or some older version in the repositories

---

### Post by cowboyup6983 on 2008-08-06
thanks for all the help... i found this to be a little more helpful


[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

