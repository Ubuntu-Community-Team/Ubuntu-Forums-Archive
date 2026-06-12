---
title: "Samsung Q430 Ubuntu 10.04 Fully Working"
date: 2011-01-29
forum: Hardware
---

### Post by killthebabysitter on 2011-01-29
Figured I would share with everyone how I got my Q430 working in full with Ubuntu 10.04.

1. Install Ubuntu
2. Plug in LAN and update everything, and install nvidia and wireless restricted drivers.
3. Enable two finger scrolling
gedit /home/EnableTwoFingerScrolling.sh
#!/bin/sh
# Enable Two Finger Scrolling Script
sleep 5 # This seems to make the script work 100% of the time
synclient VertTwoFingerScroll=1
synclient HorizTwoFingerScroll=1
synclient EmulateTwoFingerMinW=5
synclient EmulateTwoFingerMinZ=48
Save and exit gedit
Add /bin/sh /home/EnableTwoFingerScrolling.sh to Startup applications

4. Enable backlight control
sudo add-apt-repository ppa:voria/ppa
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install nvidia-bl-dkms
sudo gedit /etc/modules
add the line nvidia_bl

5. Misc tools
sudo apt-get install samsung-tools 

That's it! Now you can let your i5 breathe!

Thanks to all the guys at [http://www.voria.org](http://www.voria.org) for your hard work!

Enjoy,
Alex

---

### Post by skchoe on 2011-02-04
Hi, congratulations!

I wonder if your Samsung notebook has this model number:

NP-Q430-JSB1US

If you are outside of US, the last letters US is not your case.

But I am interest in buying a laptop of the model number above, 
I wonder if its graphics card is working under Optimus Tech by Nvidia. (In that case, nvidia driver won't work AFAIK). 

Let me know if your model number is same and it use Optimus.

Thanks,

SK

---

### Post by gusbeto37 on 2011-02-06
Hey there,

I also have a Samsung Q430, bought last july on the US. Thanks for how to make the brightness controls work.

But I cannot make the wireless work fine. And ubuntu 10.04 does not detect any drivers needed besides the graphics card. 

How did you manage to make it work?

Also, I made the two finger script, but it does not work??

---

### Post by hedleysmith on 2011-02-13
Just got a new Samsung Q430, followed the instructions posted above and everything works flawlessly! Thanks

---

### Post by user_cero on 2011-02-14
I wonder, did you get the audio working out of the box or did you have to do something to make it work? If yes, could you please tell me what did you do?

---

### Post by gusbeto37 on 2011-03-14
@usercero: try checking your pulse audio config under sysyem-preferences-sound

To all people getting bad battery performance, install the samsung tools and when you open them (system menu) go to the last tab, enable laptop mode and play with the settings. Much easier than doing it manually.

I manages to go from 1 hour of battery to 3 hours

---

