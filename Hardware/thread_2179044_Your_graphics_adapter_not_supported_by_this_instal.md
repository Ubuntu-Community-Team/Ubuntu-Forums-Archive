---
title: "Your graphics adapter not supported by this installation ubuntu - But I know it is"
date: 2013-10-06
forum: Hardware
---

### Post by m-lockhart on 2013-10-06
I've just installed Ubuntu on a PC that has an HD5770 Radeon card. I read through how to install it properly on 13.04 (64bit) but it keeps telling me that "Your graphics adapter not supported by this installation ubuntu"

When I do an lspci at the terminal it keeps thinking that I have a Radeon 1950 which I know is not supported. So it it is not seeing that I have this card. Anybody know a solution. (to make sure that my card is working properly I put the card in a Windows machine and it seems to get detected just fine. 

I have a TFORCE 550-SE mobo if that helps.

---

### Post by m-lockhart on 2013-10-06
Hopefully someone has an answer....It's a pretty nice card for what I want it to do. I noticed that the motherboards PCIe bridge driver is made by nVidia. I also found this link which states that the pciid 10027280 is being listed as ATI Radeon 1950 (R 570) which is what Ubuntu see's...and wont let me get past to update my card. Can someone explain this to me? I found this info on this website [http://kmuto.jp/debian/hcl/Biostar/TForce+550](http://kmuto.jp/debian/hcl/Biostar/TForce+550)

---

### Post by m-lockhart on 2013-10-11
Is it possible that this board's PCIe is driven by Nvidia technology so that if I add an Nvidia card under windows, it would operate as SLi, but with Ubuntu this mobo just won't work? When I had Ubuntu as a partition with Windows on 11.04 it appeared to work but now that I soley have Ubuntu and the latest version it is not>?

---

### Post by VMC on 2013-10-11
What does 'lsmod' show. I looked at the [motherboard]("http://www.biostar.com.tw/app/en/mb/introduction.php?S_ID=180#spec") and nvidia doesn't show up anywhere. Usually there chips will appear on hardware listings.

---

### Post by Yellow Pasque on 2013-10-11
> Is it possible that this board's PCIe is driven by Nvidia technology so that if I add an Nvidia card under windows, it would operate as SLi,
What? The mobo doesn't have onboard video, and you need two nvidia cards for SLI.

Are you absolutely sure you have a RadenHD 5770 card and not a RV570 card?

---

### Post by m-lockhart on 2013-10-11
I am absolutely sure I have a radeon HD 5770 card. My previous post was without coffee and makes no sense regarding SLi...lol. I have NO IDEA where that came from. I still have the box for the video card and I may be a newbie with linux but I am no newbie to Windoze. Didn't think to do an lsmod. Will do that this weekend when I can get back to the PC

---

### Post by deadflowr on 2013-10-11
Along with lsmod you can post the output of
```
lspci | grep VGA
```
which will tell us exactly what card the system is reading.

lsmod will tells us what driver/modules you have running/loaded, and my guess would be the open-source radeon driver.

---

