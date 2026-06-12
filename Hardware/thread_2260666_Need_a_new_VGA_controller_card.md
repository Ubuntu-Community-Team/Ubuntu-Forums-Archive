---
title: "Need a new VGA controller card"
date: 2015-01-13
forum: Hardware
---

### Post by richpri on 2015-01-13
I recently installed 14.04 on my Compaq which has a built in VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RS780L [Radeon 3000] [1002:9616] (prog-if 00 [VGA controller]).  This controller is not working very well and I have found references to the fact that it is considered legacy and is no longer supported by AMD. I would like to install a different VGA controller card and use it instead. I would like to choose an inexpensive card that will be compatible with Ubuntu14.04 and with my desktop. I need some guidance on choosing such a card. Note that I am not a player of video games and any card that runs well with Unity will do fine. 

This is the result of the **dmidecode -t 2** command.

```
# dmidecode 2.12
SMBIOS 2.6 present.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
	Manufacturer: FOXCONN
	Product Name: 2AB7
	Version: 1.00
	Serial Number:  
	Asset Tag:  
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis:  
	Chassis Handle: 0x0003
	Type: Motherboard
	Contained Object Handles: 0


```

---

### Post by mörgæs on 2015-01-14
Have you tried Lubuntu? With a lighter desktop environment I think the GPU will work fine.

---

### Post by QIII on 2015-01-14
^^ Free and worth a try!

---

### Post by Mark Phelps on 2015-01-14
> it is considered legacy and is no longer supported by AMD.

While that is true, the default open-source Radeon drivers should work well, as long as you don't need temperature control or hardware acceleration for Gaming.

---

### Post by Yellow Pasque on 2015-01-14
> This controller is not working very well
Be more specific. A 780L is not a powerful chip, but it should be enough to run Unity comfortably. About the only thing the GPU doesn't do out of the box is assist the CPU with video playback decode. That can be enabled, but it requires jumping through some hoops.

> as long as you don't need temperature control or hardware acceleration for Gaming.
I'm not sure what you mean. The open source driver supports Dynamic Power Managment (DPM). I can't remember whether it's enabled by default in Ubuntu 14.04, but one can manually enable it like so: [https://help.ubuntu.com/community/RadeonDriver#Kernel_3.11.x_.28Ubuntu_13.10.2BAC8-Saucy.29_and_Later](https://help.ubuntu.com/community/RadeonDriver#Kernel_3.11.x_.28Ubuntu_13.10.2BAC8-Saucy.29_and_Later)
Also, 3D acceleration has been supported for a while (though I wouldn't expect great gaming performance on this GPU regardless of what OS or driver I was using).

---

### Post by MartyBuntu on 2015-01-14
> **richpri said:**
> I would like to choose an inexpensive card that will be compatible with Ubuntu14.04 and with my desktop.

Just go with some low-power, inexpensive NVIDIA card and be free of graphics driver hassles. Best of luck.

---

### Post by richpri on 2015-01-15
Since I upgraded to 14.04 I have been experiencing 2 problems:

First [often] Firefox and [sometimes] Thunderbird have been crashing with crash reports like this one:
```
ProductID: {ec8030f7-c20a-464f-9b0e-13a3a9e97384}
ProductName: Firefox
ReleaseChannel: release
SecondsSinceLastCrash: 273406
StartupTime: 1420481432
Theme: classic/1.0
Throttleable: 1
URL: https://docs.google.com/spreadsheets/d/1E47Jsws0mwiiq8WjKBEyKxYk7BayUclDw_4P036u_nQ/edit#gid=38420198
Vendor: Mozilla
Version: 34.0
useragent_locale: chrome://global/locale/intl.properties

This report also contains technical information about the state of the application when it crashed.
```

Second when moving images [such as cards in freecell] the images blank or fuzz out until they are dropped.

---

### Post by BadMichael on 2015-01-15
Do you have any specific NVIDIA cards in mind? I'm experiencing the same video problems as the OP.

---

### Post by Yellow Pasque on 2015-01-15
Check to see if something's wrong with your 3D:
```
glxinfo | grep OpenGL
```

I would try the latest driver before throwing money at the problem: [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)

---

### Post by richpri on 2015-01-16
I am now looking into acquiring a NVIDIA GT610 graphics card for my Compaq Presario CQ5700Y.
But i have two questions/concerns about this card.

First, the specifications for the card call for a 300W power supply but the computer only has a 250W supply.
I know that specs are often very conservative so I wonder if 250W would actually be enough. 
The computer is otherwise un-enhanced and will have no other cards in its expansion slots.

Second the computer has PCI Express X1 slots [one channel]. Will that be enough bandwidth for the card?

Any advice on either of these questions would be appreciated.

---

