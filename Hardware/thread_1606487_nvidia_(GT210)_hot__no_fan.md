---
title: "nvidia (GT210) hot / no fan"
date: 2010-10-26
forum: Hardware
---

### Post by debili on 2010-10-26
My nvidia's temperature is constantly between 60-90 C, the fan on the card isn't spinning and the card itself it so hot i can't even touch it. I didn't find much info about what settings could i check to see what is wrong; does somebody have suggestions what could be the cause? I can't tell when this started..
my system: ubuntu10.10 64, card recognized: nVidia GT218 (GeForce 210) (rev a2)

---

### Post by debili on 2010-10-27
anyone please?

---

### Post by realzippy on 2010-10-27
which nvidia driver do you run?

---

### Post by cascade9 on 2010-10-27
> **realzippy said:**
> which nvidia driver do you run?

Good question. 

I'd gues that you've got a hardwarefailure in the fan though, not the drivers.

---

### Post by debili on 2010-10-27
> **realzippy said:**
> which nvidia driver do you run?

thanks foryour reaction;

the driver version is 260.19.12

---

### Post by debili on 2010-10-27
> **cascade9 said:**
> Good question. 

I'd gues that you've got a hardwarefailure in the fan though, not the drivers.

I've recently reset my Bios to defaults, could that be in some way related ?

thanks

---

### Post by nerdy_kid on 2010-10-27
try to get the fan working with nvclock first:
```

sudo apt-get install nvclock

```
then run
```

sudo nvclock --info

```
it should spit out a bunch of info from your card, as long as it does run

```

sudo nvclock --fanspeed 40

```
keep messing with the number to see if the fan will work.  If it works, then maybe someone smarted can help you :)  if not, then see if the fan is jambed.  (try spinning it with your fingers)

---

### Post by debili on 2010-10-27
> **nerdy_kid said:**
> try to get the fan working with nvclock first:
```

sudo apt-get install nvclock

```then run
```

sudo nvclock --info

```it should spit out a bunch of info from your card, as long as it does run

```

sudo nvclock --fanspeed 40

```keep messing with the number to see if the fan will work.  If it works, then maybe someone smarted can help you :)  if not, then see if the fan is jambed.  (try spinning it with your fingers)

Hi nerdy_kid, after installing and runnning "sudo nvclock --info" i get ```

:~$ sudo nvclock --info
It seems your card isn't officialy supported in NVClock yet.
The reason can be that your card is too new.
If you want to try it anyhow [DANGEROUS], use the option -f to force the setting(s).
NVClock will then assume your card is a 'normal', it might be dangerous on other cards.
Also please email the author the pci_id of the card for further investigation.
[Get that value using the -i option].


```should i go ahead and force it ?

---

### Post by realzippy on 2010-10-27
yes..try to force it since fan is not running at all in the moment,it cannot get worser.

---

### Post by debili on 2010-10-27
> **realzippy said:**
> yes..try to force it since fan is not running at all in the moment,it cannot get worser.

ok; so now i got:
```

:~$ sudo nvclock --info -f
-- General info --
Card:         Unknown Nvidia card
Architecture:     GA8 A2
PCI id:     0x0
GPU clock:     -2147483.750 MHz
Bustype:     PCI

-- Memory info --
Amount:     512 MB
Type:         128 bit SDR
Clock:         -2147483.750 MHz


```
then:
```

:~$ sudo nvclock --fanspeed 40 -f
Error: Your card doesn't support fanspeed adjustments!

```

ps. something tells me that the cards memory isn't 512MB...

---

### Post by nerdy_kid on 2010-10-27
Does the nvidia-settings utility work correctly?
I would try purging the driver and reinstalling it.

---

### Post by Frogs Hair on 2010-10-27
The info is correct , your card has no fanspeed control , that card runs the same speed all the time . Try cleaning the card and connections and take static precautions.

---

### Post by debili on 2010-10-28
> **Frogs Hair said:**
> The info is correct , your card has no fanspeed control , that card runs the same speed all the time . Try cleaning the card and connections and take static precautions.

Hi FrogsHair ;) thanks for the info :guitar: !! I took out the card to have a look, it looked clean, but i noticed that compared to my CPU fan, i needed to put a bit more force into my fingers to turn it, i cleaned it as much i could with compressed air and put it back again; after startup i saw the fan moving but not really turning so i took it out again and cleaned it more/ pushed the fan up-down on its axis and so on.... strangely, but after startup the fan made like one turn per 5 seconds, the frequency increased eventually and now, after 5minutes it's pretty fast i can't read the letters in the turning circle and feel cool wind when approaching with my fingers; the GPU temp is now down to 45 C..i wonder if there is a sensor to tell me how fast the fan is spinning now so i can check occasionally
strange, the card/pc is like 9months old...

---

### Post by cascade9 on 2010-10-29
> **debili said:**
> I've recently reset my Bios to defaults, could that be in some way related ?

thanks

Nope, that shouldnt make any difference at all. 
> **debili said:**
> Hi FrogsHair ;) thanks for the info :guitar: !! I took out the card to have a look, it looked clean, but i noticed that compared to my CPU fan, i needed to put a bit more force into my fingers to turn it, i cleaned it as much i could with compressed air and put it back again; after startup i saw the fan moving but not really turning so i took it out again and cleaned it more/ pushed the fan up-down on its axis and so on.... strangely, but after startup the fan made like one turn per 5 seconds, the frequency increased eventually and now, after 5minutes it's pretty fast i can't read the letters in the turning circle and feel cool wind when approaching with my fingers; the GPU temp is now down to 45 C..i wonder if there is a sensor to tell me how fast the fan is spinning now so i can check occasionally
strange, the card/pc is like 9months old...

Siezed bearing. Sometimes they are fixable by 'forcing' the fan to spin, but in a lot of cases, its a temporay solution. 

Cheaper cards are more likely to have problems like that...but its prety rare for it to happen after 9 months.

---

### Post by debili on 2010-10-29
> **cascade9 said:**
> Nope, that shouldnt make any difference at all. 


Siezed bearing. Sometimes they are fixable by 'forcing' the fan to spin, but in a lot of cases, its a temporay solution. 

Cheaper cards are more likely to have problems like that...but its prety rare for it to happen after 9 months.
well i can recognize there is a bit of 'uncommon' sound whet the fan spins fast...hope that doesn't mean it'll stop again in a few weeks.
could you recommend any simple fan-speed monitor ? is it even measured on this type of graphic card?

---

### Post by cascade9 on 2010-10-31
sorry, I dont know of any fanspeed monitor for nvidia cards for linux. Pretty much all the cards I'm running are passive cooled, so no fan at all.

---

### Post by efflandt on 2010-10-31
The **NVIDIA X Server Settings** gui under System > Administration usually shows fan speed under Thermal Settings (actually no settings there, just monitoring).  But my GT 220 has variable speed fan and someone said yours is fixed speed (when it is running).  Or another way to get info in terminal is: **nvidia-smi -q -d**

This is idle:

```
Driver Version            : 260.19.12

GPU 0:
    Product Name        : GeForce GT 220
    PCI Device/Vendor ID    : a2010de
    PCI Location ID        : 0:1:0
    Display            : Connected
    Temperature        : 29 C
    Fan Speed        : 20%
    Utilization
        GPU            : 0%
        Memory        : 11%
```This is under full load when temperature stops rising:

```
Driver Version            : 260.19.12

GPU 0:
    Product Name        : GeForce GT 220
    PCI Device/Vendor ID    : a2010de
    PCI Location ID        : 0:1:0
    Display            : Connected
    Temperature        : 55 C
    Fan Speed        : 30%
    Utilization
        GPU            : 99%
        Memory        : 38%
```

---

