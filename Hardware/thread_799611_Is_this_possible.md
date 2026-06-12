---
title: "Is this possible?"
date: 2008-05-19
forum: Hardware
---

### Post by Herbonator on 2008-05-19
I would like to run Ubuntu (or whatever distro can do it the easiest) off a USB flash drive or a SD memory card in my laptop but with a twist.

I want to completely turn off my HDD and underclock my CPU while in this OS so I can greatly increase my battery life. Im hoping for no power at all to the HDD. Ideadly I'd like to have the option of switching the HDD on and off while booted in case I need to access something without doing a full boot.

This would hopefully turn my laptop into a faux-ssd laptop and give me incredible battery life. Possible?

---

### Post by bobblehat on 2008-05-19
I've had Ubuntu running well off a Compact Flash card in a desktop (via a CF to SATA adapter) so what you're doing sounds possible in that respect. I'm not sure how you'd shut down the hard drive on the fly.

(As friendly hint - a more descriptive title might attract more comment.)

---

### Post by sharkbite1414 on 2008-05-19
Try looking in your laptop's BIOS (Basic Input Output System) by pressing DEL, F1, F2 etc. before any OS boots. Look for HDD Power down. If you have this option set it to 1 min. or however long you want. This does not turn the HDD off as such, but stops the disks spinning after the HDD has'nt been accessed for however long you set.

=;:-#:!:WARNING!!! Be Carful when wondering around you BIOS, it is for chanching viatal system prosses and you can easliy criple your system if your not carful. If you feel unconfortable doing this by youself why not not get a friend who knows abit more about computers.

Hope this helps.

---

### Post by Herbonator on 2008-05-19
Is having the HDD powered down the most efficient I could possible get? What I am hoping for is to turn my regular power munching laptop into a 3 or 4 hour power saving device that I can write on in press rooms and whatnot without having to connect to power. Id be wanting to cut power to all the devices that I didnt need in order to get maximum battery life.

I hope Im making myself clear with all this, thanks for your help.

---

### Post by bobblehat on 2008-05-19
Other things that'll help are turning down brightness and turning off BlueTooth and WiFi.

It's worth noting too that flash memory generally has a fairly limited number of erase and re-write cycles compared with a standard hard disk. If you're running your O/S from a SD card or flash drive it'd be worth minimising anything that's heavy on repeated writing. At minimum you probably want to disable swap.

---

### Post by Herbonator on 2008-05-19
Yeah I had considered that but with the price of flash memory these days I dont really care. I just want some of the benefits of the EeePc without all the drawbacks. Pendrivelinux looks promising but im still not sure about disabling the HDD. The HDD is one of the biggest battery life sucks isnt it?

---

### Post by kurtpete on 2008-05-19
Not sure if this is an attractive option for you, but some laptops (my m1210 for instance), make removing the hard drive pretty simple.  Take out 4 screws, and slide it out.  

This may not be the most convenient (and not even sure the bios would allow it, I haven't tried it), but it would also have the added benefit of reducing weight a little bit.  I guarantee it won't spin disconnected...  :)

---

### Post by Herbonator on 2008-05-20
Haha thanks Kurtpete. Thats something that I might experiment with if this proves not to be possible. If that is the case though I might as well just find a power outlet.

I want this for use in press conferences and press rooms where there is rarely a spare outlet and I need to be typing for extended periods. Battery life takes priority over performance or convenience in this case.

---

### Post by nicedude on 2008-05-20
There is no way I am aware of that you can both fully disable the hard drive and be able to re-enable it during a session on any OS. That said you could either disable your hard disk in your bios or remove it compleatly and that would stop your system from using it but you would not be able to re-enable it during a session ( I would recommend using the bios method over actual physical removal for obvious reasons ). Furthermore as to your question of power usage I am not sure the hard drive is the biggest power muncher but it would be system specific . I would tend to think the CPU and graphics chip to be big munchers of power as well, maybe more than the drive.

Have you tried installing powertop utility and looking at what is using the power up in your system? If not I would recommend doing that as it will also give you some advice of modifications to the system that will reduce power usage. 

Also to anyone interested in saving power with their laptop while on batteries try disabling devices and services that you do not use as that can give good saving without you noticing a difference and actually speed up your system as well. Some to look at first that I would suggest are Blue Tooth & the cups printer system.

Hope this helps everyone get some more battery life as I am currently working on this for my own situation.

If anyone here knows of any other utilities that will help me to manage my Acer 5520's power levels please PM me as I would appreciate the info :-)

*** To all laptop users please read my thread linked below about hard drive park & unpark behavior under Linux ( Ubuntu Hardy included ) that could reduce your hard disks lifespan by a large amount. I have a simple test outlined there to see if you are effected as well as A fix if you find as many do that you are. Don't panic but please check this out as I assure you it is no joke.

[http://ubuntuforums.org/showthread.php?t=795327](http://ubuntuforums.org/showthread.php?t=795327)

nicedude

---

### Post by bobblehat on 2008-05-20
Just a thought - what about replacing your internal hard drive entirely with one of those flash to 2.5" disk adapters then putting your existing drive in an external usb or firewire can for times when you need the data capacity? With 4-8GB internal flash you could easily run Linux + enough space for a typing session then transfer to the external disk afterwards.

---

### Post by Herbonator on 2008-05-20
> **bobblehat said:**
> Just a thought - what about replacing your internal hard drive entirely with one of those flash to 2.5" disk adapters then putting your existing drive in an external usb or firewire can for times when you need the data capacity? With 4-8GB internal flash you could easily run Linux + enough space for a typing session then transfer to the external disk afterwards.

Hey bobblehat, thats a great idea but unfortunately it doesnt suit my needs. I often need to upload and edit photos on the same day that I am in press conferences so I need the space readily available and fast sometimes.

---

