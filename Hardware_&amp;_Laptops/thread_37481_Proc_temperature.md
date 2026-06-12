---
title: "Proc temperature"
date: 2005-05-27
forum: Hardware &amp; Laptops
---

### Post by christooss on 2005-05-27
With which program I can check my pocessor temperature. In bios I can see how hot I my proc and I want see that in Ubuntu.

Thanks for the anwsers

---

### Post by dave9191 on 2005-05-27
Your current cpu temp is stored in the /proc/acpi/thermal_zone directory. 

You can have this shown to you using the following command in a terminal 

```
cat /proc/acpi/thermal_zone/ATF0/temperature
```

Check the thermal_zone dir if you have more sensors installed on the system (ATF0, ATF1, etc). I only have the one so ATF0 is my cpu sensor. If you want a program that can show you the temperature in a GUI form then Gkrellm ( [http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html](http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html) ) can do that as well as monitor cpu access, memory use, network and other stuff. 

Dave

---

### Post by christooss on 2005-05-27
[QUOTE=dave9191]
You can have this shown to you using the following command in a terminal 

```
cat /proc/acpi/thermal_zone/ATF0/temperature
```

Dave[/QUOTE]

Thanks for the anwser but...

I have nothing in /proc/acpi/thermal_zone directory

---

### Post by dave9191 on 2005-05-27
Did you do a full install of ubuntu ? Are you sure that you have thermal sensors in your system? If the answer is yes to both, then either Linux doesnt support them, or you need to add the support somehow. Either way I cant help further, sry 

Dave

---

### Post by christooss on 2005-05-27
[QUOTE=dave9191]Did you do a full install of ubuntu ? Are you sure that you have thermal sensors in your system? If the answer is yes to both, then either Linux doesnt support them, or you need to add the support somehow. Either way I cant help further, sry 

Dave[/QUOTE]
 Yes and Yes are the anwsers

Ok I will manage to live withot termal information

---

