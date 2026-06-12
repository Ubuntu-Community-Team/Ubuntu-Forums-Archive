---
title: "Ubuntu desktop machine"
date: 2011-04-16
forum: Hardware
---

### Post by sm1357 on 2011-04-16
Hello,

I'm relatively new to Ubuntu.

I would like to find an assembled computer to buy on which I can install it. I talked to customer support on Dell's website, but it seems they no longer have Ubuntu as an option.

Does anyone here have any advice?

Many thanks.

---

### Post by GTMoraes on 2011-04-17
You could always try installing by yourself.. It's easy as 1-2-3, specially with Natty.
You can also install with using a pendrive, look for unetbootin for placing your image on the flash drive correctly
[LEFT]__________________________
[/LEFT]

[CENTER]**Media Center PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 | 320GB HDD SATA II | Realtek ALC889A | Sony Bravia 46" 120Hz | Ubuntu Maverick
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" HD LED | 6:30hrs Battery | Ubuntu Natty
[size=1]|[color=#7FFF00]Microsoft WMM 4000[/color]|[/size]
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[SIZE="1"]**Ubuntu Powered.**[/SIZE][/CENTER]

---

### Post by coffeecat on 2011-04-17
You don't say which country you are in which makes it difficult to give you advice about suppliers of Linux-compatible machines. There are many small companies that specialise in machines for Linux, most in one country only. Although, having said that, most hardware is just fine with Linux/Ubuntu. You could always narrow your choice and post details for advice, or search the forum.

If you want to buy a machine and not have to pay for Windows, here are a couple of links. 

A site listing suppliers of machines with pre-installed Linux:

[http://lxer.com/module/db/index.php?dbn=14](http://lxer.com/module/db/index.php?dbn=14)

"Naked" computers, that is ones sold with no operating system installed:

[http://nakedcomputers.org/](http://nakedcomputers.org/)

---

### Post by GTMoraes on 2011-04-17
You could always buy a Windows computer, click on "I don't accept" on the first EULA, turn off, call the Computer's maker and ask for a refund. They'll ask to you send the computer over, without batteries and they'll remove it, and give you a check with the value of the system. Acer actually send a truck here to pick up my netbook and to deliver it, free of charge. I've got R$100 (around 50 US Dollars) back from my 7 Home Basic.

Ubuntu works fine on almost all computers, 90% of the time you don't even have to modify anything.
I've actually installed Ubuntu with success on 5 computers, two of them listed on my sig, one HP Mini 210-1020BR, Another desktop computer I've made for a friend (AMD Based, Gigabyte motherboard) and a "Positivo" (local brand) Core i5 notebook. 100% success, didn't even have to pop up the Terminal.
[LEFT]__________________________
[/LEFT]

[CENTER]**Media Center PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 | 320GB HDD SATA II | Realtek ALC889A | Sony Bravia 46" 120Hz | Ubuntu Maverick
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" HD LED | 6:30hrs Battery | Ubuntu Natty
[size=1]|[color=#7FFF00]Microsoft WMM 4000[/color]|[/size]
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[SIZE="1"]**Ubuntu Powered.**[/SIZE][/CENTER]

---

### Post by anajuliaqm on 2011-10-17
Hey GTMoraes,
I've seen you successfully installed Ubuntu in a HP Mini 210-1020BR, witch is exactly the one I'm having problems with. I've had a "firmware missing" message from the wireless connection and I can't seem to get my right buttom from the trackpad working as well. Did you had those issues? How did you solved them? 
I've installed 11.04 with Wubi.

Thanks!

---

### Post by GTMoraes on 2011-10-17
Hey, as you have a 1020**BR**, i assume you're an portuguese speaker, so if you wish, we could continue our conversation in portuguese through PM's or somewhere else =)

Well, I've had those issues indeed. The "Firmware Missing" thing was fixed by activating Restricted Drivers. If I remember correctly, it's the only driver available. The right click trackpad I used some 'workaround' to make it work, it's a prototype driver, if I'm not wrong.
Try this:


    ```
sudo su
```

    ```
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
```

    ```
reboot
```

Remember it's going to reboot your machine, so save all your files before running the last command. One issue that might remain is the trackpad's scroll. It will not work anymore (but I rather prefer rightclick than scroll, eh?)

All of above have been tested with Ubuntu 11.04 Natty. I'll be testing on 11.10 Oneiric on this 210-1020BR, but I believe it's going to work flawlessly.

---

### Post by ratcheer on 2011-10-17
I can recommend one **NOT** to buy: **CyberPower PC**.

I bought one this spring. It is a very nice PC and, once I figured everything out, it is working very well for me.

BUT

I could not install any Linux distro from the DVD drive. When I sent a polite enquiry to their tech support, trying to ask about the hardware configuration, I received the curt reply that they only support OS's installed by them, and even if they did support user installed OS, it would only be Windows.

It took me a couple of days to get enough info via the Internet to fix the problem, which was just to unplug the DVD player from a SATA III port and plug it into a SATA II port. Since Win7 worked fine with the DVD plugged into SATA III, I guess it really was an OS issue. But, their response lost me as a customer, forever.

---

