---
title: "Installing an NVIDIA card on ubuntu 11.10 machine"
date: 2011-11-25
forum: Hardware
---

### Post by gearage on 2011-11-25
Very new to the whole ubuntu scene, just downloaded it on to a brand new machine yesterday. Additionally I am inexperienced with computers in general, I decided to try ubuntu because I like the whole open source idea.   The system seems to be running fine in general and I am managing the basics however I have an NVIDIA card which from the web I understand can be installed etc. Not sure why I need it but thought I might as well have it running! I have looked at loads of sites and so far can not manage this.  The Video card is a - NVIDIA Geforce GTX 550 Ti  I have I think successfully downloaded a driver - NVIDIA-Linux-x86-275.09.07.run  I am using ubuntu 11.10  What I need is a step by step guide for how to install this. It really needs to be step by step as I have failed with several step by step guides so far.  Regards  Gearage

---

### Post by sudodus on 2011-11-25
Welcome to the Ubuntu Forums

I think that before you start installing the downloaded drive, try the proprietary driver offered via Ubuntu. I green icon (or widget) should show up on your 'desktop' a while after you have logged in to the computer (after you have put the card itself into the box).

Click on the green icon (or widget) and you will be offered to install the proprietary driver offered via Ubuntu. The installation is very easy. However it might be older than the driver downloaded directly from nvidia.

If it does not work, come back and ask for more help!

---

### Post by gearage on 2011-11-25
FAO : Sudodus  Many thanks for replying so quickly -   Re - Click on the green icon (or widget) and you will be offered to install the proprietary driver offered via Ubuntu. The installation is very easy. However it might be older than the driver downloaded directly from nvidia.  I have only the very basics on my desktop from the first installation yesterday morning. I am sure nothing new is on there. I have just 10 icons plus the waste bin in my launcher, nothing else. I put the card in this morning and expected to get some kind of a prompt but nothing. Possible that I have done this wrong however I think it is just an edge connector yes/no?  I tried to find some kind of device manager to see if the system could see it but am as yet unable to do this.   Anyway no widgets etc  Gearage

---

### Post by grahammechanical on 2011-11-25
Is the GTX 550 the only video adapter in the machine? If so, then if it was not fitted properly you would not get any output to the screen.

First, stop thinking like a Windows user. Second, if you are booting into a desktop then Ubuntu is already booting and using a driver for your GTX 550.

There are two kinds of drivers for Linux. Those developed by the Linux community under an open source licence and those developed by the maker of the equipment (called proprietary drivers). The programming code for these are not open source. Therefore, some Linux users will not use them as a matter of principle. Therefore these proprietary drivers are not installed by default. We, the user, have to activate them to use them.

Sadly, manufacturers cannot be forced to develop Linux drivers for their equipment and so the Linux community tries to produce the drivers we need and the community is hindered by the maker refusing to provide technical details of their hardware. For this reason a proprietary might work better than an open source driver. This is why we nearly always suggest installing the proprietary driver.

As you are using 11.10 you can open the Dash and type Additional Drivers and you will find the utility (widget) referred to in the earlier post. Click on the icon of a green computer expansion card.

If there is a driver available for this card you can activate it with this utility, which will download and install it for you. It will replace the existing drivers. This is the Ubuntu easy way to install video card drivers. The method that you have seen may be necessary if you need the most up to date driver but it is not so easy to do. As you have noticed.

I am using the Nvidia driver for my GT 220. It is version 280.13. There are more up to date versions but I do not need them.

Once the driver has been installed open the Dash and search for Nvidia. You can then load the Nvidia X-Server Settings utility that is installed along with the driver.

Regards.

---

### Post by gearage on 2011-11-27
FAO : grahammechanical     Thanks for getting back to me.    The Asus motherboard has its own video output which I ma currently using which is fine.       I got the video card when I bought the bits as I assumed I needed one however when I started putting stuff in the case I saw the video output on the motherboard.   As I had purchased it I thought I had better fit it especially as I think I may need its features in the future to run downloaded documentaries on my TV in the lounge.    At present there is nothing coming from the video output on the card.   I am going to try and get the driver in through the Dash feature etc and I will get back to you.    Many thanks for your assistance  Regards  gearage

---

### Post by gearage on 2011-11-27
FAO : grahammechanical  Update - I have located the widget called Additional Drivers.  Interestingly there is a closed padlock on the lower right corner of the icon . Significance?   Next to the icon there is the message  - No proprietary drivers are in use on this system.  As I said before I think I have managed to download the NVIDIA driver - NVIDIA-Linux-x86-275.09.07.run - what is next move?    Is there an easy way to verify whether I have fitted the card correctly?   Basically I just put it in the slot.  There was an additional cable with a black 6 way conn but there was no corresponding conn on the NVIDIA card.    All instructions in Chinese.   Later I will open up the machine and see if the fan is running etc.   I must sound like an absolute technophobe - sorry  regards  gearage

---

### Post by gearage on 2011-11-27
FAO : grahammechanical Update - I have opened up the case and the NVIDIA card is receiving power and the fan is spinning.  Confirmed that nothing is coming out of the video output.

---

