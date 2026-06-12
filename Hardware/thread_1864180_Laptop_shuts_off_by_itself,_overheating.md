---
title: "Laptop shuts off by itself, overheating?"
date: 2011-10-18
forum: Hardware
---

### Post by dannyboy79 on 2011-10-18
I have a Gateway T-1630 laptop. Specs are as follows:
AMD Turion™ 64 X2 2.0 GHz
ATI RS690T chipset
3072 MB 667 MHz DDR2 SDRAM
ATI Radeon® X1270 graphics (lspci -v reports RS690M, X1200)

I have tried 10.04, 10.10, 11.04, and 11.10. All default Ubuntu installs and no matter what the laptop will just shut off out of know where after heavy use. Example is Pioneer Trail in Facebook which is a Flash Media Game. You can hear the fan increase it's speed trying to cool down the laptop but I guess it can't keep it cool enough because it shuts down. The few solutions I have tried so far
1. Took off panel and cleaned out fan and vents
2. I've tried to use CPU scaling and set it to "conservative" or to just stay 800Mhz
3. The bios is updated with the most recent bios per Gateway website (90.03)
4. Tried using Google Chrome Browser because maybe it was a firefox memory leak issue but it still shut off when playing pioneer trail in Chrome Browser also.

I am at my wits end here. Can someone please help me? Is it the radeon open source driver that causes it to overheat? Should I try to install fglrx? I love Ubuntu and want to use ubuntu on this older laptop but obvisouly I can't if it's just going to shutoff when trying to use it under heavy stress. The battery doesn't hold juice anymore, so it's always plugged into wall, does that make a difference?

---

### Post by dannyboy79 on 2011-10-19
BUMP

Sorry for being impatient. Can anyone help please?

---

### Post by dannyboy79 on 2011-10-19
BUMP  Please help, anyone?

---

### Post by Redblade20XX on 2011-10-19
Can you run these commands in the terminal to install these packages?

```

sudo apt-get install acpi
sudo apt-get install lm-sensors

```

Afterwards, can you run these commands in the terminal and post the outputs?

```

acpi -V
sensors

```

Hopefully these will give us some info on your problem! :P

- Red

---

### Post by dannyboy79 on 2011-10-19
> **Redblade20XX said:**
> Can you run these commands in the terminal to install these packages?

```

sudo apt-get install acpi
sudo apt-get install lm-sensors

```

Afterwards, can you run these commands in the terminal and post the outputs?

```

acpi -V
sensors

```

Hopefully these will give us some info on your problem! :P

- Red
Results of commands

```
acpi -V
```
Adapter 0: on-line
Cooling 0: LCD 0 of 7
Cooling 1: Processor 0 of 3
Cooling 2: Processor 0 of 10

```
sensors
```
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +58.0°C                                    
Core0 Temp:  +55.0°C                                    
Core1 Temp:  +58.0°C                                    
Core1 Temp:  +57.0°C

I appreciate any help you can provide.

---

### Post by collisionystm on 2011-10-19
> **dannyboy79 said:**
> I have a Gateway T-1630 laptop. Specs are as follows:
AMD Turion™ 64 X2 2.0 GHz
ATI RS690T chipset
3072 MB 667 MHz DDR2 SDRAM
ATI Radeon® X1270 graphics (lspci -v reports RS690M, X1200)

I have tried 10.04, 10.10, 11.04, and 11.10. All default Ubuntu installs and no matter what the laptop will just shut off out of know where after heavy use. Example is Pioneer Trail in Facebook which is a Flash Media Game. You can hear the fan increase it's speed trying to cool down the laptop but I guess it can't keep it cool enough because it shuts down. The few solutions I have tried so far
1. Took off panel and cleaned out fan and vents
2. I've tried to use CPU scaling and set it to "conservative" or to just stay 800Mhz
3. The bios is updated with the most recent bios per Gateway website (90.03)
4. Tried using Google Chrome Browser because maybe it was a firefox memory leak issue but it still shut off when playing pioneer trail in Chrome Browser also.

I am at my wits end here. Can someone please help me? Is it the radeon open source driver that causes it to overheat? Should I try to install fglrx? I love Ubuntu and want to use ubuntu on this older laptop but obvisouly I can't if it's just going to shutoff when trying to use it under heavy stress. The battery doesn't hold juice anymore, so it's always plugged into wall, does that make a difference?


I know you said you took of the panel, BUT you might want to disassemble it a little further. 

You need to make sure you get everything out of the heatsink that should run underneath the keyboard. Usually the CPU and video card share the same copper cooling tube. Pull off the keyboard, remove as many pieces as you can and hit it with an air compressor ... or can of air

OH and make sure your CPU fan is spinning. Look under the laptop with a flash light and peak into the vents, you should see the fan spinning pretty good.

---

### Post by superbatlife on 2011-10-20
put heat sink compound between the copper tube and the processor. you need good heat transfer or it will overheat and crash...i use the cheapy from radio shack, its silicone base heat sink compound. Was having same issue with my gateway m1625 about 6 weeks ago...

---

### Post by dannyboy79 on 2011-10-21
> **superbatlife said:**
> put heat sink compound between the copper tube and the processor. you need good heat transfer or it will overheat and crash...i use the cheapy from radio shack, its silicone base heat sink compound. Was having same issue with my gateway m1625 about 6 weeks ago...i've built plenty of towers but i have never messed around with a laptop. so you're saying i just need remove the heat sink that sits on top of the cpu, clean surfaces and apply new thermal paste? i think i have some arctic silver left over from my last computer build.is this done from removing bottom panels or do i have to remove keyboard? hopefully there is a guide out there somewhere of steps to disassemble laptop. thanks for your help, i'll post results after this weekend.

---

### Post by superbatlife on 2011-10-24
On my gateway the copper piece and processor are just under the cover, where as on my acer, I have to do more extensive disassembling. I wouldnt know on yours without seeing it. I do know that after redoing the heat sink compound that mine stopped overheating. Its wierd with laptops. My acer never even gets warm. The other thing on my gateway is that when I boot up it telles me I have a bad battery. It is correct, my battery is bad. I think it telling me is really cool. Do you have any clue as to radeon x1270 drivers for ubuntu?

---

### Post by dougalkerr on 2011-10-24
Definitely try the fresh heatsink compound. My Dell is prone to doing exactly what yours does but, even after cleaning and fresh compound it still shuts off after heavy use, especially Firefox use (Firefox seems to be bad for thrashing the processor).
This didn't help me and I cured the problem by getting a cheap and cheerful laptop cooler. Only cost a few notes and the laptop never shuts off now.
A lot of posts about my model Dell having this problem and this is what has cured mine - get good air flow under the laptop, never put it on your lap directly.

My setup is a piece of hardboard or slim mdf as a bas the, the laptop cooler and then the laptop. Absolutely no problem with shutting off after this.
It is a little clumsy but, it keeps me going...

---

### Post by dannyboy79 on 2011-10-24
> **superbatlife said:**
> On my gateway the copper piece and processor are just under the cover, where as on my acer, I have to do more extensive disassembling. I wouldnt know on yours without seeing it. I do know that after redoing the heat sink compound that mine stopped overheating. Its wierd with laptops. My acer never even gets warm. The other thing on my gateway is that when I boot up it telles me I have a bad battery. It is correct, my battery is bad. I think it telling me is really cool. Do you have any clue as to radeon x1270 drivers for ubuntu?
i am under the impression that the radeon driver provided in ubuntu is good enough for my purposes. i don't need all that fancy 3d direct rendering BUT it did cross my mind that different drivers may handle the radeon x1200 (GS690M) differently? Maybe some drivers control the fan better or whatever, I dunno???  It shuts off like clockwork if my GF is on facebook playing a flash media intensive game like pioneer trail or similar. 

I still didn't take it apart yet to redo the thermal paste, got busy this weekend. will take a look at it soon. thanks for the feedback everyone!

---

### Post by superbatlife on 2011-10-24
Off subject, but I did figure out while hooked up through hdmi on my big screen, that I can watch movies normally without lag just by lowering screen resolution. Bad part is that the hdmi sound doesnt play and I have to use line in for sound...Good luck on your laptop, and I looked at your blog..nice!

---

### Post by dannyboy79 on 2011-10-24
> **superbatlife said:**
> Off subject, but I did figure out while hooked up through hdmi on my big screen, that I can watch movies normally without lag just by lowering screen resolution. Bad part is that the hdmi sound doesnt play and I have to use line in for sound...Good luck on your laptop, and I looked at your blog..nice!

i have really neglected my blog but thanks for taking a look at it though.

---

### Post by dougalkerr on 2011-10-24
superbatlife - I have found that changing the audio output option switches my HDMI sound on. It switches off the laptop sound but, hey sound through the HDMI is better than not.

---

### Post by Flymo on 2011-10-24
Hello Danny - been having a look at our small Acer laptop using acpi & sensors - the Celeron 540  cruises along happily for hours at the temperatures you are seeing. Not entirely certain that it is a temperature problem, although it does look that way.  

Anyone else have a view on the temperatures seen?

---

### Post by dannyboy79 on 2011-10-24
> **Flymo said:**
> Hello Danny - been having a look at our small Acer laptop using acpi & sensors - the Celeron 540  cruises along happily for hours at the temperatures you are seeing. Not entirely certain that it is a temperature problem, although it does look that way.  

Anyone else have a view on the temperatures seen?
i was going to run a memtest on the RAM, but when I tried the laptop had already been on for a while so in the middle of the memtest, it shut off. I just attributed it to overheating again BUT i wonder if it's a bad ram issue if you're saying that the temps i posted aren't that high. Though i don't think i had facebook pioneer trail open when did that test with lmsensors.

---

### Post by dannyboy79 on 2011-10-26
Its seems as though re-doing the thermal paste between the heat sink and the cpu has made a huge impact. I followed this guide for disassembly [http://www.youtube.com/watch?v=VGzqoVH8b7g]("http://www.youtube.com/watch?v=VGzqoVH8b7g")  

The vent for the fan to blow hot air out was completely caked with dust and dirt (on the inside) as well just as they showed in the youtube video. The fan hardly even spins up now, whereas before it would spin really loud probably to make up for the fact that it wasn't venting out the heat from the heat sink. I used Arctic Silver thermal paste. 

I ran sensors again and it showed temps around the same as last time 58 to 62 degrees celsius BUT that was after playing Pioneer Trail for 1 hour and having other videos playing in Youtube. I am guessing that it's fixed now. Whereas when I ran it and posted my results before, that was immediately after turning it on without doing anything else. LOL

Hope others can get some help out of this thread. Thank to everyone for their help. I love Ubuntu and it's community!

---

### Post by dougalkerr on 2011-10-27
Just like I was saying, serious overheating problem. The amount of machines I have seen with blocked air ways. It is just like getting a cold, if you can't breath, you heat up. I have even seen one with a melted chocolate bar blocking the fan vents!!!
I suspect your machine will be fine but, probably has suffered stress on the components due to the amount of time it sounds like you have had the problem.
If I was you I would still seriously think about getting a laptop cooler. At a few bucks it is really worth it.
They can be slippy under the laptop depending upon which one you get so you might have to get some sticky rubber feet for the bottom of the laptop as well to stop it sliding.

Have you tried the audio settings change as I suggested for your HDMI.
It worked a treat for me and is probably all you need to do as well.
Good luck again.

---

### Post by dannyboy79 on 2011-10-27
> **dougalkerr said:**
> Just like I was saying, serious overheating problem. The amount of machines I have seen with blocked air ways. It is just like getting a cold, if you can't breath, you heat up. I have even seen one with a melted chocolate bar blocking the fan vents!!!
I suspect your machine will be fine but, probably has suffered stress on the components due to the amount of time it sounds like you have had the problem.
If I was you I would still seriously think about getting a laptop cooler. At a few bucks it is really worth it.
They can be slippy under the laptop depending upon which one you get so you might have to get some sticky rubber feet for the bottom of the laptop as well to stop it sliding.

Have you tried the audio settings change as I suggested for your HDMI.
It worked a treat for me and is probably all you need to do as well.
Good luck again.

I am not using HDMI out so you must be talking to the other person.

---

### Post by thiyagi on 2012-11-18
thanks for the info guys, cleaned the fans which had a lot of dust. Now the system is not restarting as well as the temp is 20 degree low..:)

---

### Post by wildmanne39 on 2012-11-18
Old thread closed.

---

