---
title: "Aspire 3680 card reader"
date: 2007-10-25
forum: Hardware &amp; Laptops
---

### Post by Sparkfist on 2007-10-25
Ok I've searched the web and these forums to see if drivers get get the 5-in-1 card reader working. As there doesn't seem to be a solution that works under Linux. Would it be possible to run WinXP in VMware to access the card reader? I would like to be able to use the card reader as it's the only xD card reader I have and my digital camera uses that format.

Thanks for any help.

P.S. The model is 3680-2022, and the memory has been upgraded to 1.5GB. So it should be able to run two OS at the same time right?

---

### Post by MaximusTG on 2007-10-25
I also have an Acer Aspire 3680, with internal card-reader (not sure what you mean by 5-in-1 reader, mine only takes SD-cards) and to get that working I had to edit /etc/modules

```

sudo gedit /etc/modules

```
and add a new line, saying

'tifm_sd' 

(without quotes of cours)

---

### Post by Sparkfist on 2007-10-26
The card reader in my Aspire will read SD, MMC, MS Pro, MS Pro Duo, and xD. I don't have a problem with SD or MMC, I know both of those are supported, I also have a USB card reader that can read most of the popular card media save for xD.

Has anyone been able to get hardware to work by using WinXP under VMware before. I'd like to know if it's possible. I want to avoid having to repartition my hard drive and install WinXP just so I can use the card reader, or if possible avoid having to buy a USB card reader.

Again any help I would appreciate.

---

### Post by MaximusTG on 2007-10-26
My lspci output gives this:

```

0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

```

Do you get the same result (does it use the same controller?) if so, you don't need the vmware solution, because it can work natively. Just checked, and my aspire 3680 also lists all those flash formats under the opening for the card. To test, boot into Gutsy, live or regular install, and type:

```

sudo modprobe tifm_sd

```
 
If that works, and your reader works in Gutsy, add it to /etc/modules like I said earlier. It will then load automatically next time.

I don't think you can use the built-in card reader with VMware though, USB readers will work, you can redirect USB devices to be controlled by the guest operating system

---

### Post by Sparkfist on 2007-10-27
I did what you posted but didn't get anything back from the modprobe. So I don't know if I did something wrong or if the drivers for the card reader are not installed.

As for how it card readers is connected it could be a simple USB card reader. I'd love for that to be the case as I don't have to worry about all the BS that has gone into developing for the card reader on my Pavilion zv6123cl. Stupid custom chip-set and that weird bus it runs on.

I guess I'll just have to download and install VMware. See if it works or not. Might take me a few days to get things running to really check but hopefully this will work.

---

### Post by MaximusTG on 2007-10-27
Jeah, you probably don't get a response if you type the modprobe command in, but to check, just put in an SD card, and it should get mounted automatically.. 
Oh wait, you want to use it to read an XD card. Then you should 

sudo modprobe tifm_core
sudo modprobe tifm_7xx1

The try putting in an xD card.

---

### Post by natehatewindows on 2007-10-29
I have the same card reader as you in my toshiba p-105, i have had no luck trying to get it to work. I only use MS pro and when i put in the MS the light turns on and everything like in windows but it never mounts.

---

