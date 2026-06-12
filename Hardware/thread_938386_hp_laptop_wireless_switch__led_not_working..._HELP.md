---
title: "hp laptop wireless switch / led not working... HELP"
date: 2008-10-04
forum: Hardware
---

### Post by smooth3006 on 2008-10-04
here are the specs of my laptop :

HP Pavilion dv6809wm Entertainment Notebook :
AMD Turion 64X2 2.0GHz.
Nvidia Geforce 7150m
3GB DDR2 Ram
120GB Hard Drive
Atheros AR5007 802.11 b/g

i have the wireless working with madwifi but i can't get the wireless switch on the front of the laptop to work nor the led to work either. it is always "orange" or off. it is suppose to turn "blue" for on and it is not. 

ive searched around and posted a bug but i still haven't found a solution. i even tried a guide i found online for laptops and it didn't work.

---

### Post by smooth3006 on 2008-10-04
anybody guys ? i know this is a well known issue with laptops & ubuntu. i just can't seem to find a specific fix for mine. 


:(

---

### Post by RedXanthus on 2008-10-04
Actually, I'm fairly sure this is a hardware bug with HP notebooks using Turion chips. I've had the same problem in both Windows and Linux with my HP. In the end I gave up and bought a USB wireless adaptor.

---

### Post by smooth3006 on 2008-10-07
does anybody have a solution for this, i gave up linux for now but i may go back soon and id like to know if there is a fix ?

---

### Post by icelechi on 2008-10-14
> **smooth3006 said:**
> here are the specs of my laptop :

HP Pavilion dv6809wm Entertainment Notebook :
AMD Turion 64X2 2.0GHz.
Nvidia Geforce 7150m
3GB DDR2 Ram
120GB Hard Drive
Atheros AR5007 802.11 b/g

i have the wireless working with madwifi but i can't get the wireless switch on the front of the laptop to work nor the led to work either. it is always "orange" or off. it is suppose to turn "blue" for on and it is not. 

ive searched around and posted a bug but i still haven't found a solution. i even tried a guide i found online for laptops and it didn't work.


Hey I have the same laptop and the only thing keeping me from using Ubuntu right now is the wireless.

How did you get the wifi to work?
What version of Ubuntu are you using?
Where did you get the Windows drivers for the madwifi?

Thanks

---

### Post by garciadealba on 2008-10-15
I'm in the same situation.  Can;t get wifi to work.

---

### Post by smooth3006 on 2008-10-16
> **garciadealba said:**
> I'm in the same situation.  Can;t get wifi to work.

Procedures are below:


1. Go to System > Administration > Hardware Drivers

2. Disable the following options:

- Atheros Hardware Access Layer (HAL)
- Support for Atheros 802.11 wireless LAN cards (in some cases this one is not necessary to disable)

3. Download this Driver Patch from [http://eeedora.googlecode.com/svn-history/r160/trunk/generate-rpms/madwifi/madwifi-ng-r3366+ar5007.tar.gz]("http://eeedora.googlecode.com/svn-history/r160/trunk/generate-rpms/madwifi/madwifi-ng-r3366+ar5007.tar.gz")
4. Reboot your system

5. After reboot, open a terminal and issue the following:

sudo apt-get install build-essential

tar xfz madwifi-ng-r3366+ar5007.tar.gz (this comand has to be issue in the same folder where you downloaded the file from point nr. 3)

cd madwifi-ng-r3366+ar5007

make

sudo make install

sudo modprobe ath_pci

reboot


6. Done! If everything went well, your wi-fi is ready to use!

In order to verify it, you can issue the following:

ifconfig wifi0

"this procedure will still not allow the wireless switch to work nor the led."

---

### Post by smooth3006 on 2008-10-19
there has got to be a fix or patch to get the led and toggle switch to work ? ive seen other fixes for other laptops.

---

### Post by xnostradamusx on 2008-10-19
my wireless led is same as yours i just ignore it because my wifi is working which is important i can ignore that part as long
as my wireless working great

---

### Post by smooth3006 on 2008-10-19
> **xnostradamusx said:**
> my wireless led is same as yours i just ignore it because my wifi is working which is important i can ignore that part as long
as my wireless working great

thats not the point man, it should work out of the box, if not with a patch or fix.

---

### Post by PatrickVogeli on 2008-10-19
> **smooth3006 said:**
> thats not the point man, it should work out of the box, if not with a patch or fix.
yeah, it should. Just say thank you to atheros and/or HP for that great linux support.

---

### Post by smooth3006 on 2008-10-19
> **PatrickVogeli said:**
> yeah, it should. Just say thank you to atheros and/or HP for that great linux support.

sorry i didn't mean to be rude at all, it just bugs me is all. in vista the led turns blue for on and the kill switch works, in ubuntu it does not. i do have the wireless working though. i just thought there might be a solution for this. i heard a rumor that in 8.10 the led will work out of the box, so i guess ill have to wait.

---

### Post by smooth3006 on 2008-10-19
it's weird because i read & heard hp has very good support for linux. i know dell even ship pc's and laptop with ubuntu on it, id like to think everything would work ?

---

### Post by smooth3006 on 2008-11-08
so did 8.10 correct these issues or what ?

---

