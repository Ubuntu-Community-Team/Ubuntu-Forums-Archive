---
title: "Hardware drivers for Lenovo N200 3000 series"
date: 2008-03-29
forum: Hardware &amp; Laptops
---

### Post by Whaat on 2008-03-29
Hi everyone

I want to install Ubuntu on my new Lenovo N200 3000 series laptop which already have vista bussiness OS. I want to install Ubuntu on a seprarate partition. 

My question is, does Ubuntu support all laptops hardware?. I mean do I need to grab hardware drivers separately from somewhere before installing Ubuntu or Ubuntu already contains all necessary drivers from  different laptop manufacturers such as Lenovo. I checked Lenovo website they have drivers for only Vista and XP nothing is mentioned about Linux.

I am installing Linux first time.  I never used it so please help me.

Thanks and BR
Whaat

---

### Post by CazperII on 2008-03-29
Most hardware just works with the n200. These are the things that didn't work right away in my case:
[LIST]
[*]sound (just adding 1 line fixes the problem search this forum for answer)
[*]fingerprint reader (You can get it to work but it's more difficult) 
[*]SD-card reader (also not hard to get working)
[/LIST]

I think this is it, you got a good laptop for Ubuntu on your hands.

Advice for 1st install:

[LIST]
[*]Use the restricted driver if you have an nvidia graphic card.
[*]Find out what hardware you have by typing in these commands in a terminal:
[/LIST]
```

lspci 
lsusb
```
Get all sorts of debugging information with the following command:
```

dmesg
```

Good luck installing this wonderful OS, it takes some getting used to but it's worth the trouble!

---

### Post by LODRazor on 2008-04-04
CazperII, how did you get the card reader to work??  I was able to fix the sound issue and don't care about the fingerprint issue, but I do need the card reader working?  You stated that it was "not hard to get working", what did you do?  Thanks in advance.

---

### Post by CazperII on 2008-04-06
Take a look here:

[http://ubuntuforums.org/showthread.php?t=636867&highlight=n200](http://ubuntuforums.org/showthread.php?t=636867&highlight=n200) 

If you can't get it to work i'll try and post a more detailed description (don't really have time now).

---

### Post by GabrielWolff on 2008-04-13
Hey, I'd like to get it all work.

How did you make the fingerprint work?

Thanks

Gabriel

---

### Post by reinz on 2008-04-21
Gabriel, you can find the fingerprint reader how-to from here:

[https://www.2030.tk/wiki/Enable_AuthenTec_Fingerprint_Reader_as_PAM_modul](https://www.2030.tk/wiki/Enable_AuthenTec_Fingerprint_Reader_as_PAM_modul)

It worked form me and i'm totaly a linux n00b :)

---

### Post by stuoolong on 2008-04-24
Whaat, hope your install went OK, I have the same laptop and installed Gutsy on it just fine. I did have a sound problem but fixed it, try [this thread](http://ubuntuforums.org/showthread.php?t=603809) if you have the same "no sound at all" issue. 

Haven't tried the SD card or fingerprint thingy but all the other hardware worked fine on Gutsy with no probs. I had bigger problems with Windows - one of those critial windows security updates crashed the disk drive which took me an entire day of tinkering and system restores to fix...

---

### Post by veganrailpunk on 2008-04-25
cool

i just bought this laptop and it's really good to see that i can get it all working properly without vista (not that i can get it working with vista anyway!)

cheers for this thread :)

---

### Post by GabrielWolff on 2008-04-26
> **reinz said:**
> Gabriel, you can find the fingerprint reader how-to from here:

[https://www.2030.tk/wiki/Enable_AuthenTec_Fingerprint_Reader_as_PAM_modul](https://www.2030.tk/wiki/Enable_AuthenTec_Fingerprint_Reader_as_PAM_modul)

It worked form me and i'm totaly a linux n00b :)

Hey, the link is broken...

Can you try it once more?

Gabriel

---

### Post by reinz on 2008-04-26
> **GabrielWolff said:**
> Hey, the link is broken...

Can you try it once more?

Gabriel

Strange,when I click on that link, then it seems to be OK. Can you access this? [http://www.2030.tk/wiki/Main_Page](http://www.2030.tk/wiki/Main_Page)
If yes, click on topic "Enable AuthenTec Fingerprint Reader as PAM modul".

---

### Post by rac83 on 2008-05-13
the one you posted first is an ssl link, lot of offices restict access to ssl sites....
Be aware that i wrote this some time ago... better search for new debian packages or compile it yourself because this is a really beta package with some bugs...
on 
[http://www.2030.tk/wiki/Install_Ubuntu_7.10_on_Lenovo_3000_N200](http://www.2030.tk/wiki/Install_Ubuntu_7.10_on_Lenovo_3000_N200)
you will find some links to get all working... as soon as I get time to install gutsy I make a new wiki entry with hopefully less manual fixes ;-)

---

