---
title: "NVIDIA GeForce 9800 GTX"
date: 2008-05-09
forum: Hardware
---

### Post by MrShurr on 2008-05-09
Hey,

I'm doing a project for school where I have to build a computer. I've gone shopping and found all of the parts that I want to use but I have a question:

Will the NVIDIA GeForce 9800 GTX graphics card work with Ubuntu (specifically, 8.04)? I've looked online and I can't find any information on this.

Thanks for the help,
David

**EDIT:**
[Here's the link to the card's specs.]("http://www.nvidia.com/object/geforce_9800gtx.html")
I've looked in the drivers section and there's nothing for Linux (both 32bit and 64bit).

---

### Post by PmDematagoda on 2008-05-09
In order to use the Nvidia card(your particular card) you will need to beta Nvidia drivers that add support for the 9-series, they can be obtained from [here]("http://www.nvidia.com/object/linux_display_ia32_173.08.html").

---

### Post by MrShurr on 2008-05-09
Thank you very much for your incredibly fast response :)

Awesome, I think I can go ahead and finish my project now ^-^

---

### Post by nova47 on 2009-02-26
I know this response is a long time after but as a caution to anyone else goes to try it I just built my own computer and I have dual SLI 9800 GTX's in it. The Ubuntu driver does not work and in fact when I installed the restricted driver the gui stopped working. And of course due to changes in the way 8.10 handles xwindows I'm probably going to have to reinstall because no one has provided an adequate explanation on how to roll back the driver. (And I don't have the cosmic space brain necessary to figure out how to do it on my own.)

Edit: If you happen to have trouble with your computer not being able to boot x server changing monitors worked for me. My new monitor with a higher refresh rate was able to display the screen just fine with the restricted drivers.

---

