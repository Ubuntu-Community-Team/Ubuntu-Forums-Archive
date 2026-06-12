---
title: "Installing Ubuntu."
date: 2009-09-09
forum: Installation &amp; Upgrades
---

### Post by timeagan on 2009-09-09
Hey folks,

I've been looking for quite some time now (about a week) and I cannot figure out how to install Ubuntu (Eeebuntu exactly) onto my laptop. I have downloaded the .so file, extracted the files with winRAR.. but I can't figure out how to do the rest. I am a total newbie here and all the instructions I have found seem to be quite out of my league. Does anyone know where I can get really easy instructions on how to do it? It's quite frustrating that I cannot figure it out... :[

I have a Dell with Windows Vista loaded on it, an external hard drive of 40gb, and Eeepc model 900a and a lot of confusion. If someone can guide me somewhere or even through it I would be grateful.

Bottom line: I have all these machines, and I need to figure out how to put Eeebuntu onto my Eeepc with the external hardrive, thus then being able to install it on that computer. 
I am also new to Linux.. and I cannot execute programs through the hard drive..

Any suggestions?

Regards, Tim

---

### Post by rob-ward on 2009-09-09
The guide here [http://www.liliputing.com/2008/12/how-to-install-eeebuntu-with-a-usb-flash-drive.html](http://www.liliputing.com/2008/12/how-to-install-eeebuntu-with-a-usb-flash-drive.html) explains step by step how to install eeebuntu.

Hope that helps, if you run into any specific problems then just ask I am sure someone will be able to help.

---

### Post by overdrank on 2009-09-09
Hi and welcome, maybe the [EeePC]("https://help.ubuntu.com/community/EeePC") can help. Good luck. :)

---

### Post by timeagan on 2009-09-09
Hello, and thanks for the links. Starting to work on it right away. 

Quick question.. if I'm loading the files from a windows OS for a linux OS should I use the unetbooking thingy for linux of windows?

Haha, I'm a failure. :D

---

### Post by timeagan on 2009-09-09
Okay, followed instructions carefully and here are my results:

Everything installed fine from Windows -> plugged hard drive into the Eeepc and pressed esc, loaded the hard drive.. but nothing happened and it booted my regular linux OS.

I tried loading the files from windows with the Linux version.. but i dont have an appropriate program to open it with.

Any help/advice? 

Thanks,

---

### Post by timeagan on 2009-09-12
No advice? I went to a computer store today and they said they did not know why it wasn't working. Im thoroughly confused.. if someone can e-mail me at [email]timothymeagan@gmail.com[/email] or has any advice.. i'd have mini orgasms. 

Thanks,
Regards, Tim

---

### Post by dumblebee100 on 2009-09-12
> **timeagan said:**
> Okay, followed instructions carefully and here are my results:

Everything installed fine from Windows -> plugged hard drive into the Eeepc and pressed esc, loaded the hard drive.. but nothing happened and it booted my regular linux OS.

I tried loading the files from windows with the Linux version.. but i dont have an appropriate program to open it with.

Any help/advice? 

Thanks,

I didnt get your problem exactly 

do u want to boot from the external hdd huh?

and what files did u access and which programs u need ?

---

### Post by timeagan on 2009-09-12
Well, I want to boot 1st from the external HDD, and eventually remove Linux and replace with Ubuntu.

Well, I downloaded Eeebuntu of their site and I'm not exactly sure what i need to do. I switched my external HDD from NSTF to Fat32.. but even that doesn't work :/

As for Linux.. I don't know how to execute a file in it.. when you open a .exe it doesn't launch automatically..

---

### Post by rob-ward on 2009-09-12
Am I right in saying that you are trying to install ubuntu on the HDD inside your eeepc, or are you trying to install in on the external HDD.

Either way you need to create a bootable usb pen stick, there are a lot of ways to do that. You have a choice of using either eebuntu or just the standard ubuntu NBR, I recently installed ubuntu NBR on the 1005ha and it worked perfectly and should work on the 900 series as well.

You can download Ubuntu NBR from here 

[http://www.ubuntu.com/GetUbuntu/download-netbook](http://www.ubuntu.com/GetUbuntu/download-netbook)

and instructions for creating a bootable peb stick are here

[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

Once you have a bootable pen stic you need to make your laptop boot from it, to do this you need to enter your laptops bios and make the usb pen stick your boot device or disable the fast boot option, i am not sure what key it is for entering the bios on your computer, i beleive it will be f2 but it could be esc or del or ???

If you choose to diable fast boot rather than making the stick the first boot option(this is the better option) then on the start up of your computer you need to press f12 until a menu shows up, from the menu you then need to select the name of your penstick.

At this point the computer will boot from you pen stick and give you a ubuntu menu, from this wenu select the try without installing option(or similar can't remember the wording). 

The computer will now boot into the ubuntu NBR screen at which point you can check that your hardware works and install it.

I think this is what you are asking, if not hopefully this will help someone else and you can correct me with regard to what you actually want to do :-)

---

