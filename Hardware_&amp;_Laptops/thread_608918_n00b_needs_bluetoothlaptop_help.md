---
title: "n00b needs bluetooth/laptop help"
date: 2007-11-10
forum: Hardware &amp; Laptops
---

### Post by svguy on 2007-11-10
I just installed 7.10 on my dell d600 with built in blue tooth and everything on the computer works great and looks awesome.  However, my bluetooth doesn't seem to be working.
When i look at the bluetooth file in /etc/default is says HIDD_ENABLED=0  and that i should change that to "1" in order to use a bluetooth mouse.

I tried downloading the tar utilities and libraries from bluez.org but i really don't have any idea of what i'm doing, yet now knowing how to fix it is driving me crazy.

Can anyone help a linux novice out?

Thanks in advance.

---

### Post by steveneddy on 2007-11-10
Bluetooth should be enabled out of the box with Gutsy - have a look at [my How to]("http://ubuntuforums.org/showthread.php?t=586105").

---

### Post by svguy on 2007-11-10
thanks for the tip, i'll try that out when i get home.  I thought i remembered trying to do an apt-get for bluez-utils and it couldn't find anything. I'll try again though.

---

### Post by svguy on 2007-11-10
actually it looks like none of that worked.
I don't have my bluetooth mouse yet, but i have my phone, which didn't show up when i did lsusb.
when i did hcitool dev nothing came up
when i did hidd --search nothing came up
and finally when i stried to sudo gedit /etc/default/bluetooth it said:
sudo gedit /etc/default/bluetooth
cannot open display: 
Run 'gedit --help' to see a full list of available command line options.

Am i being a kn0b, or is there something else going on? Should i be able to edit the file if i want to?

---

### Post by steveneddy on 2007-11-10
Did you read [the web page that I cited]("https://help.ubuntu.com/community/BluetoothSetup") in my how to?

---

### Post by svguy on 2007-11-11
actually my dad was able to help me edit the bluetooth file to state HIDD_ENABLED=1 but i guess i'll have to wait until i get my bluetooth mouse before i'll know if it actually works.

---

### Post by steveneddy on 2007-11-11
> **svguy said:**
> actually my dad was able to help me edit the bluetooth file to state HIDD_ENABLED=1 but i guess i'll have to wait until i get my bluetooth mouse before i'll know if it actually works.

Yeah - it's hard to test hardware without the hardware

---

### Post by svguy on 2007-11-13
alright, i got  the bluetooth mouse today and confirmed that it doesn't work.
Just to review i've got a dell d600 which i was told has bluetooth.
When i do hcitool dev i get nothing. 
i just read that bluetooth was optional on the d600, so i guess it's possible i don't have a bluetooth device at all.

Is there a way to check? or when hcitool dev pops up with nothing is that what it's telling me?

---

### Post by svguy on 2007-11-13
it also looks like if i am lacking integrated bluetooth on this machine i can actually buy the chip for about $20 on ebay and install it myself. But i worry that i won't be able to get drivers to make it work, or if i do have, that i don't have drivers to make it work currently.

---

### Post by red_five on 2007-11-14
I have the D600 myself, and I can tell you that adding in the module from eBay will work right out of the box. It's what I did last month. Just make sure you have all the various Bluez and gnome-bluetooth packages installed for all the utilities. Then when you get the module and install it, turn on the laptop and it'll detect it just fine.

Under the screen, where you have the power, HD, and battery lights, you'll notice a new BLUE LED light up, with the Bluetooth logo. You can use Fn-F2 to turn the module on and off. The BT module is actually an internal USB device, and it installs under the palmrest near the left speaker, just in front of the hard drive. It's not too hard, but you will have to partially disassemble the laptop, including removal of the LCD panel. It's not as hard as it sounds, though. I did it in about 20min.

To check whether you have it, just look in System | Preferences | Hardware Information for the Bluetooth Host Controller Interface. If it's installed, you'll see it under one of the 82801DB**** USB UHCI Controllers, probably #1, and it'll show up under Unknown (0x8000). If you don't see it, try hitting Fn-F2 first; if it still doesn't show up, you'll need to buy the module from eBay. I'd say, though, that if you have never seen the blue indicator under the right side of the LCD panel, you probably don't have it.

---

### Post by svguy on 2007-11-14
hey thanks for the response.
I got a little USB bluetooth adapter today and was able to get my mouse to work.
I checked the BIOS and it says "not installed" under the bluetooth section, so i'm going to assume that i don't have it.
I found some instructions on how to install the bluetooth module from dell, and i think i might just buy one for the convenience of it.  Did you have to remove the bottom of the case as well or just the top and the LCd panel?

---

### Post by svguy on 2007-11-15
Alright, so i've got my mouse working great with the USB BT module.
I've ordered the integrated one for my laptop and plan on installing it.
My other question is: is there a hotkey on this computer to toggle BT on or off? The FN+f2 combo turns off my wireless card currently, is that going to change when i install the bluetooth?

---

