---
title: "Controlling fan speed?"
date: 2008-08-29
forum: General Help
---

### Post by MaxIBoy on 2008-08-29
Under Windows, I had the fan speed for my Radeon HD 4850 bumped up to 40% to prolong its life. How do I do the same under Linux? I've got CCC and fglrx working fine.



Also, I need to turn down the speed of my case fan (sys_fan on the mobo.) Right now it's 100% all the time and it's far too loud. Is there a good Linux app for that?

---

### Post by Tom--d on 2008-08-29
For the CPU fan. Look in the BIOS for information on that. There probably is a option for making the fan in 'smart' mode (something like that) only comes on at certain temps.

---

### Post by MaxIBoy on 2008-08-29
The CPU fan is fine, I'm talking about the case fan. (Although technically it's a CPU fan bolted onto the case, it's not connected to the CPU fan port.)


Thanks anyway!

---

### Post by mrsteveman1 on 2008-08-29
there are some commandline tools to do that, i think lm-sensors and the PWM package stuff can turn fans on based on temperature etc. I think gkrellm can do it as well.

---

### Post by fragos on 2008-08-29
I purchased an inexpensive fan controller to set the speed of my case fan -- Zalman Fan Mate 2 [http://www.zalman.co.kr/ENG/product/Product_Read.asp?idx=206](http://www.zalman.co.kr/ENG/product/Product_Read.asp?idx=206)

---

### Post by mrsteveman1 on 2008-08-30
> **fragos said:**
> I purchased an inexpensive fan controller to set the speed of my case fan -- Zalman Fan Mate 2 [http://www.zalman.co.kr/ENG/product/Product_Read.asp?idx=206](http://www.zalman.co.kr/ENG/product/Product_Read.asp?idx=206)

Thats a good point, these motherboards all support multiple fans and controlling them sometimes, but it's not the easiest thing to get going and it's usually better to just set them where you want them with a controller. You can add more fans that way too.

---

### Post by MaxIBoy on 2008-08-30
Thanks all around, I'll look into those.

---

### Post by mb_webguy on 2008-08-30
If you have a Dell, you can control your fans by installing the i8kutils package, or the gkrellm and gkrellm-i8k packages.

---

### Post by MaxIBoy on 2008-08-30
Completely homemade, sorry.

---

