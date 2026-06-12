---
title: "intel hd graphics drivers"
date: 2011-03-14
forum: Hardware
---

### Post by vibrunazo on 2011-03-14
Hello, I just bought a new laptop with intel hd graphic 3000 card and I'm trying to install the drivers. Searching around I've found a few topics about this but all of them are saying ubuntu should have automatically detected and installed the drivers for this card. But that was not the case. I installed ubuntu 10.10 and it didn't install the drivers.

How do I install those drivers?

---

### Post by Yellow Pasque on 2011-03-14
What is the output of:
```
glxinfo
```

---

### Post by vibrunazo on 2011-03-14
> ~$ glxinfo
name of display: :0.0
Unrecognized deviceID 116
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  155 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  21
  Current serial number in output stream:  24
There's over 2GB of free memory, what does that mean?

---

### Post by sml on 2011-03-26
This is the new sandy bridge right?

Need more info here!

How is progress in the last week? Please update.

---

### Post by powerofpi on 2011-04-02
I just bought a new Sandy Bridge laptop with Intel HD 3000 graphics, and both Maverick and Natty Beta worked out of the box. Multi-monitor setups work just fine for me as well.

---

### Post by vibrunazo on 2011-04-06
> **sml said:**
> This is the new sandy bridge right?

Need more info here!

How is progress in the last week? Please update.Pardon my newbieshness, what is a sandy bridge? That's the processor, right? At least that's what I found googling it.

If so, according to the manufacturer it has:

CPU     INTEL® CORE™ I5 2410M
CHIPSET	INTEL® HM65
GRAPHIC	INTEL® HD GRAPHIC 3000
AUDIO	HIGH DEFINITION AUDIO

The official page from the manufacturer is here:
[http://www.cceinfo.com.br/produtos/notebook/novo-intel-core-i5/Chromo%20-%20535P](http://www.cceinfo.com.br/produtos/notebook/novo-intel-core-i5/Chromo%20-%20535P)
(in portuguese)

btw, the audio also isn't working in ubuntu 10.10. But then I updated the kernel to 2.6.36-020636 (from 2.6.35-28 that ubuntu 10.10 was using), because another forum posted was saying it could help fix the graphic problem. And then the audio started working, but the wireless stopped working, and the graphic wasn't fixed. So I had to go back to 2.6.35. Is that "normal"? I'm completely confused ><

---

### Post by vibrunazo on 2011-04-06
Well... I just kinda "solved" my problem. I just formatted everything but the home folder partition and installed ubuntu 11.04 beta instead of 10.10. And now everything that was weird or just plain not working before. Is now just working perfectly :)

Video, audio, wireless. Everything is perfect now. Guess it was just 10.10 being weird. So to anyone reading this having similar issues. Maybe try out 11.04 and see if it helps you too.

---

### Post by jimmybrite on 2011-04-13
Same for me, but I have the desktop sandy bridge i5 2nd gen, the 2500k model. I had ubuntu 10.10 (now 11.04 beta2) and I couldn't get the xorg-edgers to work. Now, It works marvelously, I am getting stutter in some games, which are mainly in wine, or java (minecraft). I have to say those are some nice community drivers we got, they could be better of course, but I am one happy customer. 
I just blame Intel for bad support.
Also my gpu is @ 1600 mhz over 1100 stock.

:p

---

### Post by sarathsnair on 2011-09-28
i hav a laptop with i7 2630 QM  procesor. it contains inel hd 3000 graphics. but i didnt get visual efect such as compiz and unity. how can i activate it ? how can i download drivers for this hd3000

---

### Post by realzippy on 2011-09-28
The drivers are part of the kernel.
You need at least 2.6.38 for it.
Try those commands:

```
sudo add-apt-repository ppa:glasen/intel-driver 
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-image-generic-lts-backport-natty linux-headers-generic-lts-backport-natty 

```
reboot

---

### Post by arman8236 on 2011-09-30
i hv same prblm in my pc...
i have acer aspire 5750 n core i3 processor and intel HD 3000 grapics...
but when i install 10.10 first my lappy not displyed grphcs properly....
than i contnly instlld it 3 tyms...!:(
thn my problm solved litle bit...
but thn another problem i faced is that system freezing whn i play video...
ohhh goood...!!
my 3 year old PC has core 2 duo n 1 gb ram and hv geaphics accleter...
evnthough it desply grapics awasome and evry effct of compiz and other...
n my brand new lappy wid advnced system doesnt work good acrding to my PC...
What should i do for it????
m too confusd...

---

### Post by sereza on 2011-09-30
I have an integrated Intel graphics on my Toshiba Portege laptop and it work normally with standard drivers,  but when I connect external monitor the machine hangs at random time (not immediately) (Ubuntu 11.4 64 bit).
  Is there a possibility to change the graphics driver somehow?  Would that help?  (Or would that make a BIG trouble to me??)

---

### Post by www.rzr.online.fr on 2011-10-09
FYI this "Unrecognized deviceID 116" is also afecting lenovo g470 
-- 
[http://rzr.online.fr/q/lenovo](http://rzr.online.fr/q/lenovo)

---

### Post by GoGreenBear on 2011-10-30
Good Evening Everyone. 
I am new to ubuntu. I have installed 11.10 just last night. I have a DELL N41110 and I am trying to install the graphic drivers which are a intel HD 3000 I believe. I have typed the following code provided by "realzippy" into the terminal. Although the part does not work for me is the last sudo " sudo apt-get install linux-image"

I am getting this headers-generic-lts-backport-natty
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-image-generic-lts-backport-natty
E: Unable to locate package linux-headers-generic-lts-backport-natty
Can anyone help me?

---

### Post by satyaog on 2011-11-11
The suffix "natty" for packages is related to ubuntu 11.04 (natty narwhal). The code name for 11.10 is "oneiric ocelot" so try changing "natty" for "oneiric" in the last command :

```

sudo apt-get install linux-image-generic-lts-backport-oneiric linux-headers-generic-lts-backport-oneiric

```

---

### Post by ikari2_2000 on 2011-11-16
[FONT=monospace]Dell Latitude E6520 i7-2620M
Intel HD 3000 videocard(Sandy?)

user1@ubuntu1:~$ sudo apt-get install linux-image-generic-lts-backport-oneiric linux-headers-generic-lts-backport-oneiric
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-image-generic-lts-backport-oneiric
E: Unable to locate package linux-headers-generic-lts-backport-oneiric

[/FONT]

---

### Post by slotdoctor on 2011-11-18
Thank you realzippy. That worked perfect for my new Thinkpad x220. Now I have my external Asus monitor displaying and image of the laptop. Again thank you.

---

### Post by Sinopa on 2011-12-30
> **satyaog said:**
> The suffix "natty" for packages is related to ubuntu 11.04 (natty narwhal). The code name for 11.10 is "oneiric ocelot" so try changing "natty" for "oneiric" in the last command :

```

sudo apt-get install linux-image-generic-lts-backport-oneiric linux-headers-generic-lts-backport-oneiric

```

When I tried that I got:

[FONT=monospace]E: Unable to locate package linux-image-generic-lts-backport-oneiric
E: Unable to locate package linux-headers-generic-lts-backport-oneiric

I also tried precise, but that didn't work either.
[FONT=monospace] 
:(
[/FONT]

---

### Post by Mark Phelps on 2012-01-02
The inclusion of "backport" is to force the utilization of "older" software -- which Oneiric is not.

Try taking out the "backport" and see if that works.

And, stay away from Precise.  That is in early Alpha stage and NOT something you want to mess with at present.

---

