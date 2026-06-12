---
title: "System freeze"
date: 2009-02-17
forum: Hardware
---

### Post by fox_XV on 2009-02-17
Hello,

Like many others I'm new in the Ubuntu/Linux community, I've installed Intrepid in a Laptop now dedicated for home (kids homework, web browsing and email basically), it's something I should have tried before because I'm impressed how it runs on this old Compaq Presario 1700, it's fast and powerfull. My problem is that from time to time the system freezes with no other option than cold boot (press power button for 5 seconds or so), the specs of my system are:
Compaq Presario 17XL365, Pentium III 600 MHz, 512 MB RAM, 60 Gb HDD (40 to Ubuntu and the rest for Windows).

I've seen others with similar problems in the Forum archive:
[http://ubuntuforums.org/showthread.php?t=259943](http://ubuntuforums.org/showthread.php?t=259943)
I know that post is closed because is quite old but they have (had) more less the same problem I have, I saw a recomendation about cleanning the memory modules, can someone tell me how to do it? is there any other thing I should try?

One last comment, the freeze tends to appear when changing windows (minimizing, changing active window, etc) but is random. I also noticed that everytime I tried to run the system monitor it freezes (tried 4,5 times until I decided to not running it anymore).

Thanks for your help, I'm happy discovering a lot of new things.

---

### Post by kestrel1 on 2009-02-17
It could be that the system is overheating, so putting extra strain on the CPU will make it lock up.
Make sure that the ventilation holes for the fan are not blocked & that the fan is working. You should be able to feel a flow of warm air coming from the vent holes.
If you don't mind opening the laptop up, then cleaning the fan would be a good idea, but I would recommend getting hold of a service manual, so that you can see what to do first. You could remove the memory modules & reseat them, but I don't really think that is your problem unless a memory module is faulty.
I will have a look around & see if I can find a service manual for you.

UPDATE:
I think I have found the correct manual. Download both parts & unzip them. If you unzip the first one it should select the second one & save several PDF's in to a directory. Open the Index.pdf to start.

[http://www.eserviceinfo.com/downloadsm/36236/](http://www.eserviceinfo.com/downloadsm/36236/)
[http://www.eserviceinfo.com/download.php?fileid=36237](http://www.eserviceinfo.com/download.php?fileid=36237)

---

### Post by fox_XV on 2009-02-17
Thanks a lot!

I'll do the maintenance when I get back home.

Fan seems to work, when working on the PC it runs for a while and stops so I presume it works, then after some time it runs again...

One thing to note is it is not a quite blow I can clearly hear when the fan runs and sometimes I think it makes more noise than it should.

By the way this is not seen in Windows XP.

---

### Post by kestrel1 on 2009-02-17
Just had a look at the link you gave & it does seem to be something with certain compaq machines. Have you tried running the system with the Live CD for a while & see if it does the same thing?
It is always possible that there is something in Ubuntu that is not compatable with these machines (probably drivers), but a clean out of the system won't hurt anyway.

---

### Post by fox_XV on 2009-02-17
I'm going home now and will try also the Live CD but I installed from it 1 month ago (or less) and have not done too much customization. In case I see that running from the CD doesn't freeze, what do you recommend to do? I'm not a Linux expert but trying to learn, just a few steps and I'll search the forum and/or google.

Thanks!

---

### Post by fox_XV on 2009-02-17
I tried the Live CD and got the same results, when I launch the System Monitor the freeze comes, tried also different monitor resolution sith no luck.

System ventilation is OK and fan runs when needed.

Is there a place where I can consult how to change the HW drivers?

---

### Post by kestrel1 on 2009-02-18
Shame that it still does it with the live CD.
Have you downloaded all of the latest updates & checked for any hardware drivers under
System -> Administration -> Hardware Drivers
If it runs fine under XP I would assume that the memory modules are OK, so can only think that it would be down to a hardware conflict of some sort.

---

### Post by fox_XV on 2009-02-19
I was not able to continue the troubleshoot yesterday will try more this afternoon. I'm a bit confused about the hardware drivers, when I click that tool the window says I don't have any private drivers installed and no other options are present, should I select a different tool?

Note: I'm not sure if that's exactly the message in english, my installation is in spanish and I think that's the translation.

---

### Post by kestrel1 on 2009-02-19
It will be proprietary driver, not private.
This just means that there are no drivers installed or possibly even available for your particular hardware.
Proprietary drivers are not open source drivers, therefore cannot be changed.
These are normally Graphics drivers & often on laptops, these will be wireless drivers.
If you haven't updated the system, these drivers do not always appear & appear after an update, but just need enabling.
If you could give us the output of the following command it may help:```
lspci
```

---

