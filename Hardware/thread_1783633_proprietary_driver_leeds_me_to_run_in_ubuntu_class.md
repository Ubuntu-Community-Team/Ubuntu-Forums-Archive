---
title: "proprietary driver leeds me to run in ubuntu classic??"
date: 2011-06-16
forum: Hardware
---

### Post by abhayohri on 2011-06-16
hello guys
i just installed ubuntu 11.4 and have never worked with linux before.

i have a radeonHD 5650 and intel integrated graphics(switchable graphics). i downloaded and installed the  proprietary ati driver which now gave me an error message that my hardware cannot support unity and i have to select the classic ubuntu from the start up page .

please let me know how to fix this 
am very grateful

---

### Post by grahammechanical on 2011-06-16
I am not sure if I have the answer.

First, it is usual to get the message that the hardware does not support Unity but going to Additional Drivers and activating the recommended driver should fix that. So, I cannot think of a reason why you should get the message after installing the driver.

Second, the Additional Drivers dialog box will say that the driver is activated but not in use. This is a wrong message. The driver is in use. Ignore that message.

Third, When you log in and click on your user name look at the bottom panel. In the menu on the right do you see a line that says Ubuntu? That is Unity. You will also see Ubuntu classic. That is Ubuntu without Unity.

Fourth, if your hardware is unable to run Unity you can install Unity 2D. You get the effects of Unity without the 3D look of the Unity icons. Unity 2D is in the Ubuntu Software Centre. After it has been installed it will appear in the list of User Interface options at log in time.

Fifth, You should also install CompizConfigSettingsManager (CCSM). You can find it in the software Centre. Search for CCSM and choose Advanced Desktop Effects Settings. When the utility is installed you will find it in System Settings at the bottom of the menu under the shutdown button or icon. Load the utility and check the box Ubuntu Unity Plugin. This plugin will give you some options for adjusting the way Unity works.

I hope this helps

Regards.

---

### Post by Yellow Pasque on 2011-06-16
fglrx/Catalyst and Unity are known not to play nicely together (even the latest fglrx)..

---

