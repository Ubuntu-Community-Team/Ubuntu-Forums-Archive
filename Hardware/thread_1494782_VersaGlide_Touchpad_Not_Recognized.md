---
title: "VersaGlide Touchpad Not Recognized"
date: 2010-05-27
forum: Hardware
---

### Post by OldHW on 2010-05-27
I have an old NEC Versa Vxi laptop with a 'VersaGlide' touch-pad that is not recognized by any newer version of Ubuntu or Xubuntu I have tried. The recently released Lubuntu is targeted at old hardware and would seem to be a good candidate, but it does not recognize the touch-pad either. In addition, none of these OS’s like my USB mouse either; They recognize the mouse but don’t like to move the cursor.
   
  I found that I had to go back to version 6.06 for the touch-pad to work. However, I've been unable to get any of my wireless cards working with 6.06; Nor will 6.06 recognize my PCMCIA Ethernet card. So I'm stuck with a way-old version of Ubuntu or Xubuntu with no Internet access and no obvious way to upgrade.
   
  In another forum I read that Xorg likely dropped support for my touchpad some time ago. Nevertheless, since I had no other obvious options I tried upgrading 6.06 via CDs to see if I could get Ethernet or wireless networking to work - knowing that even if that was accomplished, as soon as I updated the installation Xorg would likely be replaced and the touch-pad would be rendered useless. And yes, that’s what happened.  But upgrading from CDs caused lots of problems that were far beyond my level of expertise.  Also, installing Lubuntu directly on top of Xubuntu 6.06 KO’d the touch-pad.
   
  Ideally, I'd like to get Lubuntu working on this old laptop. After Lubuntu, my second choice would be to get any recent variant or version of Ubuntu (preferably Xubuntu) working on the laptop, but that seems unlikely at the moment.
   
  QUESTION:
  It seems that Xorg has dropped support for the touch-pad on my old laptop, so:
  Does anyone have a suggestion as to how I might install a recent variant of Ubuntu that will recognize my VersaGlide touch-pad? Or is it a lost cause?
   
   
  [FONT=&quot]* As an aside, there are versions of Puppy Linux that run very well on the laptop and I have installed and used them, but they all have a serious deficiency – and that is their wireless support. On all of my Puppy installations I’ve had to run through the networking wizard at every boot and every hour or two of operation. More often than not, I’ve had to run through the networking wizard 2 or 3 times to get it to work. Eventually, every Puppy install has gone completely wireless-bonkers on me – becoming very stubborn in recognizing and configuring my wireless card, requiring a re-install.

[SIZE=2]Thanks for any suggestions!
- Frank[/SIZE]
[/FONT]

---

### Post by dino99 on 2010-05-27
found : [http://www.bloomington.in.us/~gmarsh/](http://www.bloomington.in.us/~gmarsh/)  look #6

[http://members.shaw.ca/grayhouse/e120.html](http://members.shaw.ca/grayhouse/e120.html)

into synaptic, install : xserver-xorg-input-synaptics

---

