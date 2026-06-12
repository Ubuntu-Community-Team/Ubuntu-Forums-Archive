---
title: "Trouble installing Ubuntu on a new HDD."
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by Panda Dan on 2009-04-03
Ive downloaded the Ubuntu 8.10 Desktop version ISO file and burned it to a CD-R but when I put it in my new computer, it isnt recognized as anything bootable and I don't know how to make it recognizable... I should also mention that my new computer is "home made" and so the hard drive is brand new and has never had an OS installed on it before. Help anyone???

---

### Post by lindsay7 on 2009-04-03
Did you set the bios to start with the cd first and then the hard drive?  It should have been set that way by default. Also, if it is a sata hard drive some motherboards need to have the bios set to have the sata controller set in bios. One more thing to make sure of is did you make sure that you burned the cd as an ISO image? You need to be sure. You can copy the file to a cd as a data file but it will not start up. It needs to be burned as an ISO file. Post how you make out.

---

### Post by Panda Dan on 2009-04-03
Ya, I already tried all of what you said, and the file on the CD is an ISO, just checked... it says the file on the CD is listed as compressed though, maby that has something to do with it?

---

### Post by woppy71 on 2009-04-03
Just wondering, did you check the integrety of the ISO when you burnt it? Most burning software offers this feature. Also, burn the disk (ISO) at the slowest speed possible, this will hopefully keep disk errors to a minimum.

Hope this helps!

):P

---

### Post by Panda Dan on 2009-04-03
This might seem like an outragously n00bie question, but is there is difference between burning and copying, because all I did was take the file from my hard drive and drag it into the CD folder... I did'nt really "burn" anything...

---

### Post by lindsay7 on 2009-04-03
Sounds like a bad cd burn. Try this just to see if everthing is working like it should. The site I am going to give you is the download site for Gparted live cd download. It is a small file and should download fast as an ISO file. Download it and burn it like you did the Ubuntu disk and see if it starts up like it should. In case you do not know Gparted is a utility used to partitions disks. You probable will want to keep it around anyway so it is not a waste of time to get it and have. Just see if you can get it to start. You do not need to run it. You can exit right after it starts up.

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)

---

### Post by lindsay7 on 2009-04-03
Yes. as I pointed out in my first post, you have to burn it as an ISO image or it will not work. What software did you use to burn it.

---

### Post by woppy71 on 2009-04-03
Yes, there is a difference... an ISO is an exact image of a bootable disk, down to the last bit, what an ISO burner does is take that image and re-create a copy of the oringinal disk, by copying the ISO file to a disk, all you have done is copy the actual file to a disk, not re-created the original disk.

Do you have a disk burning program installed?

---

### Post by Panda Dan on 2009-04-03
> **woppy71 said:**
> Yes, there is a difference... an ISO is an exact image of a bootable disk, down to the last bit, what an ISO burner does is take that image and re-create a copy of the oringinal disk, by copying the ISO file to a disk, all you have done is copy the actual file to a disk, not re-created the original disk.

Do you have a disk burning program installed?

I don't think I have anything for burning CDs on this computer, unless there is a built in program in xp that will burn CDs. What is a good free CD burner to download and where can I get it?

---

### Post by lindsay7 on 2009-04-03
here is a free site

[http://cdburnerxp.se/](http://cdburnerxp.se/)

by the way, if you use Firefox, here is an add on that makes downloading ISO and other files much faster and easier.

[https://addons.mozilla.org/en-US/firefox/addon/201](https://addons.mozilla.org/en-US/firefox/addon/201)

---

### Post by woppy71 on 2009-04-03
Do a search on Google for "Deep Burner", it is free (well, the basic version is), it has an option to burn and check an image, as well as selectable burn speeds  ;)

---

### Post by woppy71 on 2009-04-03
> **lindsay7 said:**
> here is a free site

[http://cdburnerxp.se/](http://cdburnerxp.se/)

Yup, seconded!

---

### Post by Panda Dan on 2009-04-03
Arggg, more problems... when i try to open CDBurnerXP an red X window comes up saying I cant open the burner because it is not a valid Win32 application... now how do I fix that?
 
this is why im switching to ubuntu...

---

### Post by lindsay7 on 2009-04-03
I have never tried this burner so I can not recoment it, see if it works for you.,  I have no idea why the other one would not work, I have used it for over a year on vista 32 system.


[http://www.topshareware.com/Active-ISO-Burner-transfer-47550.htm](http://www.topshareware.com/Active-ISO-Burner-transfer-47550.htm)

---

### Post by lindsay7 on 2009-04-03
I looked at the web site for cdburnerexp and it looks like there is a new version, could be that is not working right, they listed some older versions you might try one of these.

[http://cdburnerxp.se/downloads/releases/](http://cdburnerxp.se/downloads/releases/)

---

### Post by Panda Dan on 2009-04-03
Yay!!! Got CDBurnerXP running, and Ubuntu on my other computer!!! Now I just have to install it. Thanks to everyone that helped me. 8-)

---

### Post by Panda Dan on 2009-04-03
crc error --system halted... what dose that mean? it goes to a screen saying that when i try to install ubuntu.

---

### Post by lindsay7 on 2009-04-03
I have never run across this before. Here is some of what I found. 

[http://www.computerhope.com/issues/ch000430.htm](http://www.computerhope.com/issues/ch000430.htm)


I suggested a web site to download Gparted which is an ISO file.  You might go ahead and get that and see if that will load on you computer with no problems. I do not think you need to run Gparted which is a partition utility.  JUst see if it runs.  You might also see if the disk that came with you hard drive will start up too.

---

### Post by Panda Dan on 2009-04-04
errr... i burned Gparted to a CD and i can get to the main menu screen of it but if i try to run it with default settings or in failsafe mode, it goes to black screen. not sure if thats as far as you wanted me to go with Gparted or not. and my Hard drive didnt come with a disk.

[http://www.geeks.com/details.asp?invtid=ST3500320AS-R&cat=HDD&cpc=HDDbsc](http://www.geeks.com/details.asp?invtid=ST3500320AS-R&cat=HDD&cpc=HDDbsc)

---

### Post by lindsay7 on 2009-04-04
I looked at the specs for you hard drive. One thing you might try is this.

The speck for you drive is sata 300.  Some motherboards only except sata 150.  There is a jumper on the back of your drive that probable is set for sata 300. Move the jumper over one slot. That will set it for sata 150. You should have that shown in your documentation for the drive somewhere.  At any rate you should be able to figure out how to do this.

Try this and see if it makes a difference. If not put it back in the 300 position. The documentation for the motherboard should tell you if it is setup for the 150 or the 300 speed. If you do not have the book that came with your motherboard you should be able to find the specs on the internet

---

### Post by Panda Dan on 2009-04-04
Just tried every jumper setting... still the same old crc error --system halted message when I try to install.:sad:

---

### Post by Panda Dan on 2009-04-04
So i ran memtest86... and a lot of errors came up... does that mean my HDD is bad or my RAM???

---

### Post by lindsay7 on 2009-04-05
Lets go back to square one. You said that you built this computer so, mestest86 is for testing ram memory in x86 machines. Is your computer one one of these. Do you have the correct ram for the motherboard? You you have it in the correct slots? Do you get any beeps when you start it up. Are you running memtest86 from the Ubuntu install disk? Do you have a windows install disk that you could try installing (you can over write this with a Ubuntu install)?  Check the specs for your motherboard for the required ram (ddr, ddr2, speed, location, etc.) against the memory (ram) that you have and see if everything is correct.  Something is not adding up. If you are using the Ubuntu disk to run the memtest86, then it sounds like you cd drive is working OK and the ram is good enough to get you that far but it could be the wrong ram (speed or slot location or bad ram or something).

---

### Post by Panda Dan on 2009-04-05
Yes, I am booting from the Ubuntu install disk, and Im running memtest86 from that too. I do have a windows xp install disk and I've tried installing from that, but I get BSODed everytime. I DID build this system myself and Im pretty sure everything is compatable but Ill give you the links to the RAM, and Motherboard so you can see for yourself... maybe you will see something I did'nt. Also, as you can see, I am using DDR2 1066 OCZ Reaper RAM in the two DDR2 slots in my Motherboard. (which is 1066 compatable)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16820227289](http://www.newegg.com/Product/Product.aspx?Item=N82E16820227289)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813157131&Tpk=ASRock%20P45R2000-WiFi](http://www.newegg.com/Product/Product.aspx?Item=N82E16813157131&Tpk=ASRock%20P45R2000-WiFi)

*edit* Oh... and also, I don't know what you mean by "x86 machines" or if my computer is one or not, maybe you can tell me.

---

### Post by Panda Dan on 2009-04-05
More random info that might help...

Under BIOS > Advanced Tab > IDE Configuration it lists my configuration as follows SATAII 1 ----------- Hard Disk
           SATAII 2 ----------- Not detected
           SATAII 3 ----------- ATAPI CDROM
           SATAII 4 ----------- Not detected
           etc. up untill SATAII 6... all not detected.

Also, I was going to try switching my RAM to 800 because it says in the BIOS that it is running 1066 right now, but will I be able to switch it back or will that totally mess up my computer so I cant even get to the BIOS?

---

### Post by lindsay7 on 2009-04-06
Switching out memory should not harm or do anything to you computer. I would reset the bios however so that the computer thinks it is the initial start up. Move the appropriate jumper over to do this or take the battery out for a few seconds. I looked at the motherboard specs and the memory specs and I do not see anything out of place. There was some notes on the 2.1 volt memory being a problem with some boards.  Are you sure that your memory is placed in the yellow slots?

You may want to start a new clean thread on what you new problem is to see if you get some new help as your problem now is not just with installing Ubuntu. This more of a hardware problem now than installation.

---

### Post by Panda Dan on 2009-04-06
YAYYYYYY!!!!! I switched my RAM speed to 800 instead of 1066 and now no more crc error! Thank you for all your help lindsay. But now I have a new problem... running my system at full 1066. I dont know if I will be able to boot without crashing if I switch back to 1066, but there is only one way to find out.;)Maeby I have to give the RAM more voltage??? Or less??? What do you think?

---

### Post by lindsay7 on 2009-04-06
Good for you. Here is what I think. If you have you system working with the computer set to 800 I would leave it that way and be happy. In practice, from what I understand there is very, very little difference between these two speeds and in fact a lot of ram memory never runs at the adverized or rated speed i.e. 1066. So why mess with it or the voltage if it is working. You will not see any difference in your system speed or operation.  From the specs that I read on your system, you are going to have a really cool computer in total and the little bit of ram speed difference will not amount to enough to care about. Just enjoy it and have a good time.  Most people would love to have you computer.

---

### Post by denphi03 on 2009-04-09
> **lindsay7 said:**
>  Also, if it is a sata hard drive some motherboards need to have the bios set to have the sata controller set in bios.

Hello, I am new to Ubuntu and this forum, but I have a similar issue to the original poster, so I figured this is a good place to ask...

My wife dropped her gateway mx6930 laptop and broke the (SATA) hard drive permanently. I bought a new SATA hard drive and of course it happens to be a different manufacturer and model, but I'm trying to get Ubuntu on it.

The computer boots to bios and i can configure it, but once i press "install" ubuntu tells me that it cannot detect my hard drive.

i think setting my sata controller in bios might fix this issue, but i need a little guidance on how this is accomplished please?

---

### Post by lindsay7 on 2009-04-09
You should start a new thread and discribe you problem. You will not get much attention a the end of this one. It is getting old and no one will be looking at it.

I assume you are trying to install Ubuntu with an install disk that you downloaded? Let me know what you are doing and I will follow you here until you get a new thread going. There will be much more support for you doing it that way.

---

