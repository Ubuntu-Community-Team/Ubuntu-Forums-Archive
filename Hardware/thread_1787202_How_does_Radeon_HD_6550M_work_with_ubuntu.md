---
title: "How does Radeon HD 6550M work with ubuntu?"
date: 2011-06-20
forum: Hardware
---

### Post by ntrgc89 on 2011-06-20
I'm thinking about a new laptop that has an AMD Radeon HD 6550M with 1GB ram for a video card. I've had issues with video cards on ubuntu before so I'm wondering if anyone has this card? If so, is it supported on ubuntu/does it have any issues?

Everything else on the laptop seems pretty standard, just the video card I'm worried about.

---

### Post by AraujoJordan on 2012-06-27
I have the same problem here. My laptop is hot as hell with the standard driver of Ubuntu 12.04 LTS version.

i have tried install with the terminal, the fglrx and fglrx-updates,
i have tried too with the official AMD site program (amd-driver-installer-12-4-x86.x86_64.run)

Every time i try something, appear a black screen after the splash screen of ubuntu. The standard driver is the only thing that work here.

---

### Post by |{urse on 2012-06-27
@AraujoJordan Do you have the same graphics chipset as the original poster?

---

### Post by AraujoJordan on 2012-06-27
yes, the same one. (My laptop: HP Pavillon DV6-3240BR)

---

### Post by AraujoJordan on 2012-06-27
I am concerned, I installed xsensor and he says that the temperature is 76 º C. ..

---

### Post by QIII on 2012-06-27
(Before I go on...  This thread was a year old and it might have been better to start a new thread than to revive an old one.  The forums staff may lock this thread for necromancy.  But we're here now.  If they lock it, start a new thread and I'll try and watch for it.)

I've been researching the HD xxxxM hardware, and I have more to go.  I do know that some have been able to install the fglrx drivers from the repos.  I prefer to do that in the command line rather than through the Additional Drivers gui.

Three things:

1.  When you installed via the command line, were you sure to do 

```
sudo aticonfig --initial
```*before* you rebooted?

2.  Is this a pure AMD/ATI set up, or a hybrid Intel/ATI setup (that is, switchable graphics)?  From the HP site it looks like pure AMD/ATI, but models change.

3.  Although that temp is a bit hot, in and of itself it is not alarming.  Video chips generally run hot and that is well within the design parameters -- but high for idle.  The max temp for that chip is probably in the 90s.  The real issue here is that a dedicated card in a desktop means that the GPU has a stand off from the motherboard and isn't baking the mobo's components directly.  The heat is vented outside the case by the card's cooler.  Your chip is on the PCB inside a notebook, which means that heat is a threat to other components.

If you did not do the initial configuration, that would most likely have resulted in a black screen.

Also, some users, including me, have not had great success thus far with the fglrx-updates package.

---

### Post by AraujoJordan on 2012-06-27
Are 2 ati video cards on my laptop, the 6550 and the 4250. I will try one more time the fglrx-update via terminal and the aticonfig that you say it. Later i will post the results. thanks

---

### Post by QIII on 2012-06-27
Skip the fglrx-updates for now and just install fglrx.

Also, if there are two cards, even two ATI cards, you may have to investigate switcheroo and use the open source Radeon driver.

I'll try to find you a link.

Edit:  it seems the Catalyst Control Center may have some functionality to switch/logout/login to switch between your cards.  Not something I'm familiar with.

---

### Post by AraujoJordan on 2012-06-27
I am here with live-cd, because i had another black screen, even with the aticonfig.
I will reinstall again.
When i use windows, i have the catalyst control center, to switch hight-end gpu and low-end gpu easily.
EDITED  There is a Catalyst on linux, and its works on the same way. ( a friend of mine have one switchable ati/ati card too)

---

### Post by AraujoJordan on 2012-06-27
i will try the beta version of catalyst on the amd site. maybe its works.

---

### Post by chinamusic on 2012-07-17
Araujo, if you find a solution I would be curious to get an update here.  My AMD A8-3870 is running fairly cool with Win7 and in the 70C range with Ubuntu 12.04 so I'm wondering if this is a driver issue as well.

Best,

---

