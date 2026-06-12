---
title: "Belkin f5d7050 not working"
date: 2008-11-13
forum: Hardware
---

### Post by seth_reaver on 2008-11-13
Ok i am new so please do not talk in linux gibberish please!
well i installed the drivers and wireless network is setup but when i plug in my usb wireless it will not even attempt to work. It works on my xp side fine though any help?

Ps: using a compaq v6000 laptop running the newest Ubuntu 8.10 i believe

---

### Post by 081104jk on 2008-11-13
&#12290;[**&#32593;&#31449;&#24314;&#35774;&#20844;&#21496;**](http://www.71668.net/wangzhanjianshegs.htm)BANNER&#24191;&#21578;&#25152;&#20381;&#25176;&#30340;&#23186;&#20307;&#26159;&#32593;&#39029;&#12289;&#20851;&#38190;&#35789;&#24191;&#21578;&#23646;&#20110;&#25628;&#32034;&#24341;&#25806;&#33829;&#38144;&#30340;&#19968;&#31181;&#24418;&#24335;&#65292;Email&#24191;&#21578;&#21017;&#26159;&#35768;&#21487;Email&#33829;&#38144;&#30340;&#19968;&#31181;&#65292;&#21487;&#35265;&#32593;&#32476;&#24191;&#21578;&#26412;&#36523;&#24182;&#19981;&#33021;&#29420;&#31435;&#23384;&#22312;&#65292;[**google&#25512;&#24191;**](http://www.71668.net/googletuiguang.htm)&#38656;&#35201;&#19982;&#21508;&#31181;&#32593;&#32476;&#24037;&#20855;&#30456;&#32467;&#21512;&#25165;&#33021;&#23454;&#29616;&#20449;&#24687;&#20256;&#36882;&#30340;&#21151;&#33021;&#65292;&#22240;&#27492;&#20063;&#21487;&#20197;&#35748;&#20026;&#65292;&#32593;&#32476;&#24191;&#21578;&#23384;&#22312;&#20110;&#21508;&#31181;&#32593;&#32476;&#33829;&#38144;&#24037;&#20855;&#20013;&#65292;&#21482;&#26159;&#20855;&#20307;&#30340;&#34920;&#29616;&#24418;&#24335;&#19981;&#21516;&#12290;&#23558;&#32593;&#32476;&#24191;&#21578;&#29992;&#25143;&#32593;&#31449;&#25512;&#24191;&#65292;[**google&#25490;&#21517;**](http://www.71668.net/googlepaiming.htm)&#20855;&#26377;&#21487;&#36873;&#25321;&#32593;&#32476;&#23186;&#20307;&#33539;&#22260;&#24191;&#12289;&#24418;&#24335;&#22810;&#26679;&#12289;&#36866;&#29992;&#24615;&#24378;&#12289;&#25237;&#25918;&#21450;&#26102;&#31561;&#20248;&#28857;&#65292;&#36866;&#21512;&#20110;&#32593;&#31449;&#21457;&#24067;&#21021;&#26399;&#21450;&#36816;&#33829;&#26399;&#30340;&#20219;&#20309;&#38454;&#27573;&#12290;

---

### Post by seth_reaver on 2008-11-13
Help?

---

### Post by C.S.Cameron on 2008-11-13
I have three F5D7050 on different Ubuntu computers, all of them are plug and play, I never installed any drivers, just plugged them in and they worked.
With Windows I needed to install drivers for them.

---

### Post by teaker1s on 2008-11-13
be very careful of product version changes as hardware is sometimes changed 
```
lsusb
``` should help identify it

---

### Post by seth_reaver on 2008-11-13
thx ill try it

---

### Post by james_vanb on 2008-11-13
I've always had to use ndiswrapper to install the drivers for this usb adapter. Install has been the same using ndiswrapper and the Belkin install cd as follows: 

Unplug adapter before you boot.

Install ndiswrapper through Synaptic.

Open terminal.

Remove the following drivers using these commands:

```
sudo modprobe -r rt2500usb
sudo modprobe -r rt73usb
```


I'm not sure that this actually removes the drivers, but after 3 weeks of farting around with them it made me feel better.

Blacklist rt2500usb and rt73usb by opening text editor (mousepad for Xubuntu - gedit for Ubuntu) as follows:

```
sudo gedit /etc/modprobe.d/blacklist
```

add "blacklist rt2500usb" and "blacklist rt73usb" (Without the quotes) to end of list, save and close.

REBOOT

This is where the guides I was following failed. Blacklist doesn't work until you reboot. If you don't, the wrong driver will be associated.

On your desktop, open "Home" - right click in an open area and create a file - I called mine "Belkin". Insert the install cd. Open and navigate to the driver file under XP. there will be 3 files. Copy all 3 files to the file you created under "Home" by dragging and dropping. The drivers will not load directly from the cd.

Now install the driver you just copied with the following (If the .inf file you copied is not the rt73, replace as appropriate below) :

```
sudo ndiswrapper -i /home/(your user name)/Belkin/rt73.inf
```

Insert the wireless adapter.

Now issue the following commands:

```
sudo depmod -a
sudo modprobe ndiswrapper
```

I think these create the module. Now edit modules to load ndiswrapper when you boot as follows (If you are using Xubuntu, replace gedit with mousepad):

```
sudo gedit /etc/modules
```

Add "ndiswrapper" (without quotes) to the end of the list.

Establish alias with following command:

```
sudo ndiswrapper -m
```

Reboot

---

