---
title: "Modem issue on the Asus L3800C"
date: 2006-04-26
forum: Hardware &amp; Laptops
---

### Post by VPetres on 2006-04-26
Has anyone got the modem on the Asus L3800C working with Ubuntu 5.10 as OS?

---

### Post by towsonu2003 on 2006-04-27
check out ubuntu wiki (second link in my signature) on how to configure a winmodem (assuming it's a winmodem). It's usually a hard process that requires much patience. Some modems are just not supported.

---

### Post by VPetres on 2007-02-02
wow, bumping a really old topic ;)
recently i've tried to get my modem working again and while reading the wiki i came across the following sentence ;
"You will now have to download modem drivers and install them..."

but i can't find the location of these drivers and honestly, don't even know what drivers he's talking about ;)

maybe you can point me at the correct location?

thnx!

---

### Post by towsonu2003 on 2007-02-02
> **VPetres said:**
> wow, bumping a really old topic ;)
recently i've tried to get my modem working again and while reading the wiki i came across the following sentence ;
"You will now have to download modem drivers and install them..."

but i can't find the location of these drivers and honestly, don't even know what drivers he's talking about ;)

exactly where does it say that? it has quite a few separate sections now :)

---

### Post by VPetres on 2007-02-04
You can find it by cLicking on the second link mentioned by you "DialUp Modem HowTo for Ubuntu".
Then go to the link PCTel Modems. In the HowTo there is a sentence "You will now have to download modem drivers and install them", but the link to downloading the drivers is never mentioned.

---

### Post by towsonu2003 on 2007-02-04
I believe the link you're looking for is [http://linmodems.technion.ac.il/pctel-linux/pctel-0.9.7-9-rht-6.tar.gz](http://linmodems.technion.ac.il/pctel-linux/pctel-0.9.7-9-rht-6.tar.gz)

I added thatto the wiki -thanks (hope it works)

---

### Post by VPetres on 2007-02-05
I will try it. Thanks.

---

### Post by VPetres on 2007-02-09
So close but there are some problems i have to solve. In the meantime i've upgraded to the 2.9.15-23 kernel. I've followed the posted link ([http://linmodems.technion.ac.il/pcte...9-rht-6.tar.gz](http://linmodems.technion.ac.il/pcte...9-rht-6.tar.gz)) and downloaded the pctel-0.9.7-9-rht-6_for_Ubuntu-2.6.15-23-386.tgz package instead of the suggested one. Because i'm a newbie in linux i couldn't compile the driver using the src of the previous mentioned kernel. While i tried to run the command sudo make install, it suggested that i should try the slmr drivers which i also did. I downloaded the slamr-2.6.15-23-386 package which contained precompiled *.ko drivers for my current kernel (2.9.15-23). After running the setup the modem was detected succesfully. The only thing left was to change some settings in wvdial.conf, make a connection to the service provider en surf the internet. But sadly the log of wvdial contained the following message:

--> WvDial: Internet dialer version 1.55
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT140
--> Waiting for carrier.
ATDT140
CONNECT 52000
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATDT140
--> Waiting for carrier.
** Ascend TNT Terminal Server **
ascend%
ascend%
ascend%
ascend% ATDT140


Is there something wrong with:

1 the fact that it did not get information for serial port.
2 the init string (ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0) 

or is it something else?

---

### Post by VPetres on 2007-02-12
Finally i can write this post using my dialup connection within ubuntu. In order to do this i had to fix three things:

1 In the wvdial.conf the i had to use Carrier check = no and Stupid Mode = yes
2 In network i had to deactivate my network connection
3 In my browser (firefox) i had to change to automatically detect proxy settings

The only thing still left is to automatically load my drivers when starting up.

Thanks t those who helped.

---

