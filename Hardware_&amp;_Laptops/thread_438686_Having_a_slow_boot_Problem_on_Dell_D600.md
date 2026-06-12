---
title: "Having a slow boot Problem on Dell D600"
date: 2007-05-10
forum: Hardware &amp; Laptops
---

### Post by Matty2006 on 2007-05-10
My config:
feisty fawn kubuntu
running dell wireless 1530 configured with ndiswrapper
have muti-boot system with several partitions
sometime I boot with my evdo card in
Sometimes I doc my system into the dell D-doc booting kubuntu
_____________________________

When I boot my system, the boot seems to stall for some time before it finally goes all the way to completion.
When I first installed kubuntu there was no stalling and it seemed to load right up. After getting the Wireless card working with Ndiswrapper and maybe running my system docked a few times this seemed to effect the boot sequence.

I previously had Open Suse on here and it also had a similar problem. No if I boot up with the laptop plugged with power there boot time seems to be faster vs. running just on batteries.

I am wonder if there is a problem with the apci module or its IRQ assignment. If I boot with the wireless card disabled then it might me changing the IRQ for apci. I really don't know much about how these things load and why one item might hang up the whole boot process. I was hoping someone might be able to point me in the right direction.

It might be that since I have hard-coded the wireless device into interfaces as wlan0 and if the card is disabled on boot maybe this is causing the delays. 

If anyone knows what is going on here or a good way to troubleshoot this.. it would be much help!!!

---

### Post by obviouslyshane on 2007-05-10
I have an Inspiron E1505, with a dell wireless 1500 card, which is running through ndiswrapper. The stalling started only after i got the card working, I noticed that after the loooong stall, the wifi light comes on. So I am assuming that it has something to do with that. oh, and mine doesn't do it every time, I would say its 50/50

---

### Post by Matty2006 on 2007-05-10
I would have to say that this is pretty much the same story here.. Sometimes it boots fairly quick and then other times its taking years... more than 1 minute or more.

In looking into this more closely I have a come across a pretty cool tool that graphs out the boot process. I have an attached output file from my last boot. Looking at this it would appear that the there is a good deal of readahead and random areas of red in modprobe, and drive checking, mounting..

Personally I think it might be dhcp looking for something to assgin so if there is no active nic weather its the wifi card or wired it hangs for a bit.

But honestly, I really dont really know what to look for in reading this chart?

with any luck some one out there might know what up with this :)

-Matt

---

### Post by misfitpierce on 2007-05-10
Wireless using ndiswrapper sometimes has the effect to slow boot times from what ive seen. Just bear with it until wireless support gets better I guess :)

---

### Post by Matty2006 on 2007-05-20
All right.. I am still not really sure what is causing these slower boot times but my suspicion is that it has something to do with having the wireless card active and the computer running with the wall adapter vs. running of the battery.. 

I would have to say its some sort of computer voodoo ;)

Anyway, a simple method of dealing with this for now is to use the Hibernate function instead of shutdown.
I have doing this for the past few days and the boot times are much better. Hibernate uses some swap so, just keep this in mind. 

I also run windows on another partition and boot up there is generally long as well.

-cheers :)

---

