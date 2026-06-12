---
title: "Alienware M15x gen 1 ubuntu?"
date: 2021-03-31
forum: Hardware
---

### Post by reefsider on 2021-03-31
Hi, I have an older Alienware M15x with an i7 720qm processor, 750GB 7200rpm hard drive and 4GB (2x2GB) ram; Currently running Windows 10.

     I am wondering what the best plan for this computer is?  Its kind of a special case so I'll explain whats wrong with it and what I'd like to use it for and go from there.

     This computer worked perfectly for the first 3-4yrs but then it started having issues.  When I contacted Dell they told me the hard drive had bad sectors and it should be replaced so I replaced it with a 750GB 7200rpm drive.  While reinstalling the hardware there was a bios update from dell so I gave the computer to a friend and he did the bios update and reinstalled the factory OS.  Since then none of the alienware stuff works and the computer has had some issues.  I looked on the Dell forums and it seems the bios update from Dell messes up a chip on the mother board and to fix it you need to replace the motherboard at your own expense.  Needless to say I doubt I'll ever buy another Dell but anyways lol.  I still use the computer but none of the alienware lights or features work at all anymore.  It shows all these .NET framework errors when i boot it up.  I also haven't really needed a laptop for too much so it sat around a lot and I'm just getting back to it now.

     I am now trying to learn to code and would like to use the laptop once and a while when I'm visiting family etc.  I have started The Odin Project and am enjoying it.  I set up my home computer with a partition for dual boot and may just go entirely to Ubuntu at some point.  I can't seem to do the dual boot on this computer though.  I looked into it and apparently its not possible for the Alienware.

So my main question is what is my best option for this computer? I don't really want to buy a new motherboard but they are available from aliexpress for about $100US.  I don't mind if I need to buy ram but I have a single 8GB PC4-2400T ram i can install but I think that is not the same as whats in there so i'm not even sure if I can use it? I don't really care if the lights work but it would be great if I could get them to work.  I am more concerned about the video card, cooling system and all the peripherals.  Anyways, my other questions are:

- Will Ubuntu work on this computer and have all the functionality I have now? 
- is there any chance of getting the lights to work with ubuntu


I'd love to hear what other, more experienced people would do with this computer.  Thanks in advance for any help and advice you have.

reefsider

---

### Post by mastablasta on 2021-04-01
boot into Ubuntu from USB to try it. see what works and what doesn't.

why would dual boot not be possible? it is always possible. but you say you have a bunch of errors on windows, so why would you want to stay on windows?

if BIOS update destroyed the functionality of the chip, then you have to take it up with dell. if there are no major issues with computer then BIOS update is not really needed. you may be able to flash the BIOS to the original one. though i am not sure how you do that on laptop.

next time i would invest into SSD rather than going to fast spinning HDD. i bet the difference is not that big in price. plus there is a reason why most 2,5" drives are 5400rpm

---

### Post by reefsider on 2021-04-01
Hi, yes I have tested it with the USB boot option and it seems to work well.  Still no Alienware lights or F/X but that's ok.  

Dual  boot is not an option given when you boot from USB unlike my other  computer.  With any other computer I have tried it gives 3 options; Try  it out from USB, Dual boot or the complete install.  This computer only  gives me 2 options; try it from USB or complete install.  When I looked  into it further, it seems this is not an uncommon thing for Alienware  computers, they have somehow blocked the dual boot ability and the only  option is to run from USB or do a complete install formatting the disk  and removing windows and Alienware entirely.  

As for the Bios  Update, Dell will fix it but at my expense (it wasn't cheap) as the  computer was 2 weeks out of warranty at the time.  This was a well known  and discussed issue on forums as I found several people upset about it,  as they should be.  There are also youtube videos of people using a  chip flasher/debugging tool to flash a .HEX file to the affected chip  and fixing the lights and alien FX.  However I can't find any actual  instructions on how to do this.  I have an STM chip flasher (ST-Link V2)  and have used it for other projects so if I could find the wiring  connections and the HEX file i would have no problem doing that.  

I would have bought an SSD drive but it was like 5yrs ago and they were still super expensive and 1/3 the capacity.

anyways,  thanks for the help.  Running by USB helped me find out most of the  stuff works so I'm less nervous about a complete install.  Im leaning  towards a complete install of Ubuntu but I'll wait a bit and see if  anyone has any other suggestions and get the computer cleaned out and  ready for a complete wipe

---

### Post by reefsider on 2021-04-01
I have decided to install Ubuntu and it seems to be working well for me :)  If anyone has any suggestion to try to get my LED lights and other FX working let me know

---

### Post by mastablasta on 2021-04-02
i though the drive was changed now. yes SSD were expensive a few years ago, nowadays they have descent price.

the boot goes from BIOS/UEFI -> to boot manager -> OS. so as long as the boot manager loads (for example GRUB), it can then handle booting into Linux or Windows. so capability of multiboot is actually decided by boot loader. you even have boot loaders that will boot to selected OS from floppy drive. well grub can probably do it as well, but it is a bit more complicated to setup.

now there is a function called secure boot that microsoft promoted and got included in UEFI. this caused a lot of issues at first for other operating system that could already use UEFI. now the rule is if windows is installed with secure boot on, then linux has to be as well (so it needs to have signed keys). if windows is not installed in secure boot then ubuntu shouldn't be as well. i turn off secure boot if i install only linux.  it is mostly "secure" only by name.


LED lights - i don't know how they do it, they likely control with some fn keys on windows?!? 
anyway have you seen this?: [https://askubuntu.com/questions/1065463/alienfx-on-ubuntu](https://askubuntu.com/questions/1065463/alienfx-on-ubuntu)

otherwise you can probably do it manually by scripting specific keys and all. but if any of these apps work, then why bother? :)

---

### Post by reefsider on 2021-04-02
> **mastablasta said:**
> 

now there is a function called secure boot that microsoft promoted and got included in UEFI. this caused a lot of issues at first for other operating system that could already use UEFI. now the rule is if windows is installed with secure boot on, then linux has to be as well (so it needs to have signed keys). if windows is not installed in secure boot then ubuntu shouldn't be as well. i turn off secure boot if i install only linux.  it is mostly "secure" only by name.


Just to be clear do you mean installing with the option to encrypt the installation?  

Also do I want to check the box for LVM?

I have installed it with both those options selected but I find the constant passwords a pain so I will install it again without that if its not really any more secure.

I will try to use those AlienFX programs but I don't have a lot of faith they will work.  From my understanding it is a hardware issue that is preventing them from being seen or used but I could be completely wrong.  On widows there is actually a program called Alien Command Center and that is where you can select the colors and different areas of lighting.  the biggest pain is there is a bar above the keyboard that has touch sensitive controls on it for volume and things like ejecting the CD that is unlit so its kind of a guessing game as to where the actual buttons are lol.  to eject the CD I have to just run my finger across the bar until I hit the right button and eject the cd lol. On Ubuntu these buttons still work so having them light up would be very useful.  Anyways it is definitely worth a try and I appreciate you passing those links along to me.

Thank you for your replies, its been quite helpful :)

---

