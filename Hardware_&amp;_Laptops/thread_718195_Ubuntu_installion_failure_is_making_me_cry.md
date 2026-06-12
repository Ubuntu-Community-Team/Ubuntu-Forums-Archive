---
title: "Ubuntu installion failure is making me cry"
date: 2008-03-07
forum: Hardware &amp; Laptops
---

### Post by adorableedgar on 2008-03-07
okay i've been having a terrible time installing Ubunut 7.1. I've posted a thread under the the installation catergory but i was directed here by the kind people that were helping me.

the link to the previous thread is [http://ubuntuforums.org/showthread.php?t=707805]("http://ubuntuforums.org/showthread.php?t=707805")

problem- I built a new pc (hardware list at bottom) i really don't want to spend 250 for the BASIC edition on Vista, plus i have XP already on my other PC. So i looked at Youtube videos of Ubuntu and i thought it was amazing. So i ordered the Ubuntu live DVD from amazon because my old computer's dvd burners is slacking lately. So when i got the DVD i tried running it but i got the dreaded "Timer not working!reboot and try running with the noapic option!" so i restarted and disabled "apic" from the BIOS and then i clicked on the option "install/run ubuntu" fronm the live CD menu. Success, i was able to run the Live CD. Next i clicked on the install icon, and it asked me all that it should. i chose the "use enitre disk" option for partitioning. the installer bar pulled up and once it was finished it just disappeared. I never got the "restart your computer" message. So i manually restarted. All i got was a blank screen, the installation had failed for some reason. then i enabled "apic" from by motherboard and added "noapic" to the end of the line you get when u press F6 on the live cd. I reinstalled, and this time i did get the 'restat computer" message. I restarted, the grub boot menu appeared with the option to press "esc". i left it alone. then the Ubuntu Logo and the loading bar came up and it filled up like 3cm and the disappeard and all i got was a blank screen with a flashing cursor. I rebooted and tried to boot with the "noirqpoll" AND the "noapic" option and the loading bar filled up 3/4 of the way and i got the same results as i did with just the "noapic" option after that. I thought something else had failed during installtion and so i tried reinstalling for a 3rd time. 

the third time i did the text based install. everything went okay until i got to the "selecting and installing programs". the install selected programs always failed and the grub boot loader failed to install....so i picked to option to install the lilo boot loader....it failed as well. 

I tried reinstalling a fourth time with the Live CD install and the "noapic" option. It installed and asked me to restart. I did and all i got was the Ubuntu logo and the loading bar that turns into a blank screen wiht a flashing cursor. 

i haven't done anything after that....thats all i've tried.
my hardware is below


Asus MSN-MS SE PLUS NVIDIA nForce 430 MCP         -MOTHERBOARD
AMD ATHLON 64 X2 4000+ socket AM2                       - CPU
Seagate 80 GB serial ATA 7200/8mg/SATA-3G
Kingston 1024MG pc4200 DDR2 533mhz (2x512)
Aopen 16x DVD ROM 1648L pro chameleon retail


thanks for any help in advanced

---

### Post by davarino on 2008-03-08
I am not the best one for fixing this, but I notice no one else has stepped up to the plate.

Did you check the md5sum of your Ubuntu install disk? It could be a defective image that you are working with. <https://help.ubuntu.com/community/HowToMD5SUM>

It could be that you are one of the "lucky" :( people who are fated to have trouble installing Ubuntu 7.10. My experience and reading of the forums indicate that 7.10 has had more problems in installation than either 7.04 or 6.06LTS. You may wish to try either of those two very good versions. (Later is not necessarily better... sad but true in Ubuntulandia.)

Good luck and best wishes. Ubuntu is a good choice of operating system, but it can give you problems you never dreamed would raise their heads.

---

### Post by adorableedgar on 2008-03-08
> **davarino said:**
> I am not the best one for fixing this, but I notice no one else has stepped up to the plate.

Did you check the md5sum of your Ubuntu install disk? It could be a defective image that you are working with. <https://help.ubuntu.com/community/HowToMD5SUM>

It could be that you are one of the "lucky" :( people who are fated to have trouble installing Ubuntu 7.10. My experience and reading of the forums indicate that 7.10 has had more problems in installation than either 7.04 or 6.06LTS. You may wish to try either of those two very good versions. (Later is not necessarily better... sad but true in Ubuntulandia.)

Good luck and best wishes. Ubuntu is a good choice of operating system, but it can give you problems you never dreamed would raise their heads.

i bought the CD from Amazon. i didn't burn it. Even so i did the "check CD for errors" option at the beggining when i first put the CD in the computer. Could it still be the image?

---

### Post by oldsoundguy on 2008-03-08
Some of the attempted installs using the "Live" install of Ubuntu have failed and I can attest to that on 2 out of 3 machines.  HOWEVER the "Alternate" version installed without a hitch.  All I had to do afterwards was install the programs I wanted to use from the repositories and used Envy to install the drivers and software for the NVidia graphics cards.

What you need to do is get a good burner/machine combo and download and burn the iso: (disk image)
[http://releases.ubuntu.com/7.10/](http://releases.ubuntu.com/7.10/)

Also best to be on broadband to download.

---

### Post by pbpersson on 2008-03-08
I read your old post.  If Ubuntu worked fine from the Live CD then it should work from the hard drive.  It is just that simple.  People in the other post were saying "try other distros to see if your computer is Linux friendly" and that does not make any sense to me.

I would go with the settings where the machine works the best - where the progress bar gets the farthest to the right before everything goes out the window and then go from there.

I would think there would be a detailed boot log that you could view from recovery mode to see if it fails at the same point every time - like "sending XYZ sync signal to the JKL device....oh no, my mind is going....."

Hey......I just built a brand new machine here.....does the motherboard use SATA 1.0 or 2.0 and how is the hard drive jumpered?

If you have a motherboard that uses SATA 1.0 and the drive is jumpered for the higher SATA 2.0 speed, that would be a bad thing.


Phil

---

### Post by adorableedgar on 2008-03-09
> Some of the attempted installs using the "Live" install of Ubuntu have failed and I can attest to that on 2 out of 3 machines. HOWEVER the "Alternate" version installed without a hitch. All I had to do afterwards was install the programs I wanted to use from the repositories and used Envy to install the drivers and software for the NVidia graphics cards.

Okay, my new dvd burner is coming on tuesday....my main computer isn't recognizing blank DVD's and also it won't spit them back out once i put them in.....it works fine with regular CD's.....SOOooo i bought a new DVD burner that i'll put on external exclosure for a while. ....and maybe i will try downloading and burning the alternate CD....but wouldn't it be the same thing as installing in Text Mode from the live CD?

> I read your old post. If Ubuntu worked fine from the Live CD then it should work from the hard drive. It is just that simple. People in the other post were saying "try other distros to see if your computer is Linux friendly" and that does not make any sense to me.

I would go with the settings where the machine works the best - where the progress bar gets the farthest to the right before everything goes out the window and then go from there.

I would think there would be a detailed boot log that you could view from recovery mode to see if it fails at the same point every time - like "sending XYZ sync signal to the JKL device....oh no, my mind is going....." 

okay i will try to do recovery mode tomorrow and i will take note of everything and post it here.

---

### Post by adorableedgar on 2008-03-09
Re: Desktop Hardware Incompatibility List. 

--------------------------------------------------------------------------------

ASUS MOTHERBOARD M2N4-SLI

- MP-BIOS bug: 8254 timer not connected to IO-APIC.
- Kernel Panic - not syncing: IO-APIC + timer doesn´t work!. 
- HARDWARE ERROR. CPU0: Machine Check Exception. TSC 539c47cf42 ADDR 5bcf78. This is not a software problem. Kernel panic - not syncing: Machine Check
- Contact your hardware vendor.
__________________

     

ElQuia 
View Public Profile 
Send a private message to ElQuia 
Send email to ElQuia 
Find all posts by ElQuia 
Add ElQuia to Your Buddy List 

  #19       April 20th, 2007  
pross  
5 Cups of Ubuntu
   Join Date: Aug 2006
Beans: 32
The Feisty Fawn Testing User
Thanks: 0 
Thanked 0 Times in 0 Posts  

 
Re: Desktop Hardware Incompatibility List. 

--------------------------------------------------------------------------------

asus m2n4-sli
nvidia 7900gs x2 sli

boot from CD produces 'Kernel Panic - not syncing: IO-APIC + timer doesn´t work!'

adding noapic at bootime allows you to boot but no audio and no SATA.. nv driver is loaded but results in a black screen i had to ALT+F1 then edit xorg.conf and change the driver to vesa and restart X

after installing i added 'enable_8524_timer pci=biosirq' at bootime...now everything works  




i know the first user has the same problem as i do but the second one i dont know....i look similar but is he talking about his video card or his chipset? and how would you edit "xorg.conf"?

---

### Post by kenny1948 on 2008-03-09
I too am having a problem with installation.  I had feisty installed but kept having problems with updates. I was also having problems with XP on a dual boot ( I only use it for programs that don't have Linux equals. Like Nero Burning for DVD and Video editing.

Anyway, I decided to start all over.  I reinstalled XP and then attempted to burn an install DVD.  Had a little trouble but the third time was dream.

However when installing, I got as far as this and it stopped dead.  I'm a bit confused, because I am able to use Ubuntu during this install.  Maybe it simply installed but the window hung up. I haven't gotten any error messages. Anyway please see screenshot. attached.

I haven't tried to reboot yet.  I guess that's when I will know.

---

### Post by adorableedgar on 2008-03-10
kenny, a new thread would be nice thing to do. it helps avoid confusion.

---

### Post by dptxp on 2008-03-10
If you are finding it hard to run Ubuntu, try Linux Mint. It is based on Ubuntu.

If you want latest Debian, try sidux.
If you want a solid system with Ubuntu kernel and Debian stable, try Kanotix. It is supposed to have good hardware detection.

You can wait for next release of Ubuntu in April 2008. Being a Long Term Support version, you may not find so many problems.

Gutsy has been a problem for many. You can also try the previous version Feisty (7.04).

---

### Post by adorableedgar on 2008-03-10
> **dptxp said:**
> If you are finding it hard to run Ubuntu, try Linux Mint. It is based on Ubuntu.

If you want latest Debian, try sidux.
If you want a solid system with Ubuntu kernel and Debian stable, try Kanotix. It is supposed to have good hardware detection.

You can wait for next release of Ubuntu in April 2008. Being a Long Term Support version, you may not find so many problems.

Gutsy has been a problem for many. You can also try the previous version Feisty (7.04).
*turns green* ARHARHGHAHERARHARHAHR  but i want UBUNTU 7.1 GUSTY! lol thats what im planning to do, get a different OS, like Fedora. however im still waiting for my DVD burner to come. ....why can't Ubuntu be as ez as Windows.....(lol cuz ur not paying $250 for it) i still think ubuntu looks better than Vista...idk about performance because i haven't gotten ubuntu to work lol

---

### Post by adorableedgar on 2008-03-10
>  	
Re: Ubuntu installion failure is making me cry
I read your old post. If Ubuntu worked fine from the Live CD then it should work from the hard drive. It is just that simple. People in the other post were saying "try other distros to see if your computer is Linux friendly" and that does not make any sense to me.

I would go with the settings where the machine works the best - where the progress bar gets the farthest to the right before everything goes out the window and then go from there.

I would think there would be a detailed boot log that you could view from recovery mode to see if it fails at the same point every time - like "sending XYZ sync signal to the JKL device....oh no, my mind is going....."


Phil

okay i tried booting in recovery mode and i get this towards the end before it stops doing  anything.......

Begin: Running /scripts/init-premount
Segmentation Fault
Segmentation Fault
Done.
Begin: Mounting root file system
Segmentation Fault
Begin: Running/Scripts/local-top
Segmentation Fault
Done.
Segmentation Fault
Segmentation Fault
Begin:waiting for root file system
Segmentation Fault



and thats all i get....after that it just stays there and doesn't do anything.....this is really frustrating because right now I'm posting this using the Live CD and I'm even listening to music from an external drive....

---

### Post by adorableedgar on 2008-03-10
any wonderful and knowledgeable person out there that would like to tell me if that ^ is normal?

---

