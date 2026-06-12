---
title: "no OpenGL"
date: 2008-01-22
forum: Hardware &amp; Laptops
---

### Post by jhollenbeck20 on 2008-01-22
I installed Warsow and went to play it and i got a message that said You're OpenGL installation doesn't support direct rendering.  If you have an Nvidia or an ATI card you'll probably need to install the propritary driver.....I have an ATI card but im not sure which exactly...I am not very knowledgable with Ubuntu but i have 7.10.  I have installed compiz and it works fine they cube is awesome and everything.  i havent had any problems with my card except for this...so if anyone can help thank you and i will need a very easy method becuase i dont know that much.  

Oh i activated restricted drivers already...

---

### Post by Yellow Pasque on 2008-01-22
If you're using Compiz with the Ubuntu proprietary driver, that means you have XGL installed. Unfortunately, XGL is incompatible with direct rendering. If you have a Radeon 9500 or later, you could try and update to the latest ATI Catalyst driver if you want both Compiz and direct rendering (use Method 2 here: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide))

To ID your video card:
```
sudo update-pciids; lspci | grep VGA
```

---

### Post by jhollenbeck20 on 2008-01-22
I am using a laptop also Gateway...my card is [Radeon Xpress 1100 IGP].

---

### Post by Yellow Pasque on 2008-01-22
Ok, so what are going to do?:
1. Uninstall compiz and XGL and set up DR with your current driver
2. Give up on the games and keep your compiz
3. Try and upgrade to the latest Catalyst driver

I guess a 4th option might be creating a new partition so you can keep your current setup and try another ubuntu install there with the latest catalyst driver. I think this would be the best option if you had the disk space because I've seen people not be able to get compiz working again once they installed Catalyst drivers.

---

