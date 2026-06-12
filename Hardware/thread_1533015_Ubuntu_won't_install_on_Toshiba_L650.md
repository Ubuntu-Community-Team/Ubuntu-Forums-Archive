---
title: "Ubuntu won't install on Toshiba L650"
date: 2010-07-17
forum: Hardware
---

### Post by mat1tc on 2010-07-17
Hi,

I've just changed laptops to a Toshiba L650 and Ubuntu, sadly, won't install (from 10.4 to daily builds of maverick).

It will install with the boot option acpi=off, but that's not really a long term solution, not to mention disabling many features.

Has anyone else managed to fix the problem? Currently I'm stuck using the pre-installed Windows 7. 

Thanks

---

### Post by ralpyka on 2010-07-17
Hi
I have a Toshiba L650 too, and I have problems with the new linux distributions like you. I think that the problem is with the kernel, because I can't install Ubuntu 10.04, Fedora 13, OpenSuse 11.3.
But I could install Ubuntu 9.10 (only from the alternate CD, because the graphics card(ATI 5145) was not recognized). After that I installed the ATI driver from a terminal, and now everything is working(I do not need to use the acpi=off option with this version of Ubuntu).
This is good, but would be better, if someone could say a solution, to be able to use the new distributions with the new kernel too.

---

### Post by mat1tc on 2010-07-22
Toshiba released a BIOS update yesterday (21/07/10) and it has resolved the ACPI issues, Ubuntu now installs without a problem!

The update can be found on their website [http://uk.computers.toshiba-europe.com/innovation/download_bios.jsp?service=UK](http://uk.computers.toshiba-europe.com/innovation/download_bios.jsp?service=UK)

Goodbye windows 7!

---

### Post by gareththered on 2010-08-19
Just a quick question:-

Does everything work on the Toshiba with Ubuntu?  I'm thinking of getting a L670, that's all.

Thanks in advance.

---

### Post by clarkac on 2010-08-19
See this thread - may help.  [http://ubuntu-utah.ubuntuforums.org/showthread.php?p=9738660#post9738660](http://ubuntu-utah.ubuntuforums.org/showthread.php?p=9738660#post9738660)

---

### Post by mat1tc on 2010-08-19
As for things working - well I'm running the alpha of 10.10 and it's mostly functional, certainly compared to the previous version. 

Currently the only things (that I've noticed) not working are the internal mic and the headphone jack (though I haven't tried updating the ALSA drivers yet). As far as I can tell everything else is fine!

Good luck if you decide to go ahead with the purchase.

---

### Post by gareththered on 2010-08-19
Thank you both.
 
The headphone/mike problem is quite common I believe.  I have it on my current laptop - well, I did when I last checked but things may have progressed since then.  
 
I'm still looking around but the L670 is currently top of the list.
 
Thanks again.

---

### Post by houndi on 2010-08-19
I could install Ubuntu 9.10 (only from the alternate CD, because the graphics card(ATI 5145) was not recognized). After that I installed the ATI driver from a terminal, and now everything is working(I do not need to use the acpi=off option with this version of Ubuntu).
This is good, but would be better

---

### Post by ralpyka on 2010-08-21
After the BIOS update everything is working (Ubuntu 9.10, 10.04, 10.10, OpenSUSE 11.3). The only problem is that if i plug in my headphone, the built-in speakers are still sounding, but i haven't tried to solve this problem. I'm currently using Win7, because when ubuntu 9.10,10.04 is starting and shutting down, there is some noise(crackle) coming from the left side of the notebook(the HDD is on the right side). On 10.10 i haven't this problem, but this is not enough stable to use it. But you can buy a Toshiba laptop, because Ubuntu is working at worst the Ubuntu 10.10, and from the beta i think that will be usable.

---

### Post by nilsja on 2010-09-17
is it also working without acpi=off ?

i just bootet the 10.04 live-cd with acpi=off and after connecting to the wifi i had a total freeze.

---

### Post by ralpyka on 2010-09-17
Yes, after the BIOS update ubuntu is working without the acpi=off. If you start the computer with acpi=off inter alia the power management is disabled, and this generates a lot of heat.

---

### Post by Inoki on 2010-09-18
maybe a stupid question, but how can i update BIOS on a toshiba L650?

---

### Post by ralpyka on 2010-09-18
You can download the BIOS update or other drivers from here: [http://eu.computers.toshiba-europe.com/innovation/download_drivers_bios.jsp](http://eu.computers.toshiba-europe.com/innovation/download_drivers_bios.jsp)

For me is a .exe file, so i need to update the BIOS under windows. I don't know, that how secure is this(because windows can easily get a BSOD...), i only updated one time, and this was successfull.

---

### Post by schnelle on 2010-09-20
Does ATI 5145 works well with catalyst (fglrx) driver?

---

### Post by ralpyka on 2010-09-21
I currently use maverick, and in the jockey isn't driver for my graphic card(in the older releases of ubuntu there is driver in the jockey). I have not tried with the drivers from the ati website, because the open source driver is good for me: compiz is working pretty well.

---

### Post by Narendran95 on 2010-12-01
so I got this bios update and it was an .exe file. I can't run it on wine! So how do I update my bios (toshiba satellite c650) same acpi trouble...

---

### Post by ralpyka on 2010-12-06
You need to install Windows for the BIOS update

---

### Post by canucked on 2010-12-09
ralpyka: I don't know if you're still having the sound issue, but I configured a Toshiba L655 for a friend and found a solution for the non-working built-in microphone, microphone jack, and headphone jack.

The laptop I configured used a Conexant CX20585.

To fix the sound I edited /etc/modprobe.d/alsa-base.conf and added:
   options snd-hda-intel model=thinkpad

I created a thread further explaining the issues I had with that laptop:
[http://ubuntuforums.org/showthread.php?t=1641931](http://ubuntuforums.org/showthread.php?t=1641931)

Hope this works for you!

---

### Post by canucked on 2010-12-09
Narendran95: I configured a Toshiba Satellite L655-S5115 for a friend.  The BIOS I downloaded for his model from toshiba.com was called: sk2cv170.exe

My friend's laptop had Windows 7 as a dual-boot, so I installed that BIOS update using Windows.  However, I just downloaded the file again and its contents can be extracted using Archive Manager in Ubuntu.  One of the extracted files is a bootable ISO which can be burned to a CD and will presumably update your BIOS without Windows.  Further explanation is provided in the readme.txt file contained in the BIOS update exe file.

Hopefully the BIOS update you've downloaded also contains a bootable ISO.

Best of luck!

---

### Post by ralpyka on 2010-12-10
Yes, I found almost the same solution to the sound problem, I added 
```
options snd-hda-intel model=dell-vostro
```
to my config file.

---

