---
title: "Need Help To Configure my UPS With NUT"
date: 2022-05-15
forum: Hardware
---

### Post by guillaumesoucy on 2022-05-15
Hello,  
  
 
  I need help configuring my TrippLite UPS INTERNET550U connected by USB using NUT on Ubuntu 22.04 LTS.  

  
 
  When following directives here: [https://susilon.wordpress.com/2014/08/09/monitoring-a-ups-with-nut-on-debian-or-ubuntu-linux/](https://susilon.wordpress.com/2014/08/09/monitoring-a-ups-with-nut-on-debian-or-ubuntu-linux/)
  
 
  I’ve got:  
  
 
 ```
 -bash: /etc/init.d/nut: No such file or directory


```  
 
  When doing:
  
 
 ```
 /etc/init.d/nut start


```  
 
  I carefully followed the instructions but I’m not able to make it work.  
  
 
  The UPS seem to be detected as when doing:
  
 
 ```
 upsdrvctl start


```  
 
  It returns:


 ```
 Network UPS Tools - UPS driver controller 2.7.4

 Network UPS Tools - Generic HID driver 0.41 (2.7.4)
  USB communication driver 0.33
  Using subdriver: TrippLite HID 0.82


```  
 
  Thank-you in advance for help.  
  
 
  Guillaume

---

### Post by guillaumesoucy on 2022-05-17
Hello, 

Is someone have an idea?

Thank-you

---

### Post by guillaumesoucy on 2022-05-19
Hello, 

Is someone have an idea? I still need your help.

Thank-you

---

### Post by SeijiSensei on 2022-05-19
I've only ever used **apcupsd** which works out of the box with minimal configuration. DK if it will work with a Tripp-Lite UPS. I only buy APC hardware.

---

### Post by guillaumesoucy on 2022-05-19
Is apcupsd can work with Tripp-Lite HW? I could not find anything about it.

Thank-you

Guillaume

*edit* Yes, I finally do find some but, It wasn't relevant.

---

### Post by guillaumesoucy on 2022-05-25
I still need help. Thank-you.

---

### Post by guillaumesoucy on 2022-05-30
Hello, 

Is someone can help me with that please. 

Thank-you!

Guillaume

---

### Post by guillaumesoucy on 2022-06-05
Hello everyone, 

I still having the same issue. 

I still need your help to resolve it. 

Best regards, 

Guillaume

---

### Post by him610 on 2022-06-07
Maybe this will help,....[https://linux.die.net/man/8/tripplite]("https://linux.die.net/man/8/tripplite")

---

### Post by guillaumesoucy on 2022-06-07
Hello him610,

It say that only the models communicated using serials are supported. The UPS can communicate using USB and serial. Right now, the machine that I wish to hook the UPS to don't have any serial ports on it. But, when hooking the UPS using USB, it is detected. 

Is there still something to do with it, knowing the USB communication is working fine using the driver already present on the machine.

I'd found this at the bottom of the page: [https://linux.die.net/man/8/tripplite_usb](https://linux.die.net/man/8/tripplite_usb) will give it a try. I'm not very experienced with that, there a huge chance that I get back here asking for more help. :P

Thank-you

Guillaume

---

### Post by guillaumesoucy on 2022-06-14
Hello, 

Someone can help please. Thank-you! ;-)

---

### Post by guillaumesoucy on 2022-06-19
Hello, 

Someone can help please. Thank-you! :wink:

Guillaume

---

### Post by guillaumesoucy on 2022-06-23
Hello, 

Someone can help please. Thank-you! :wink:

Guillaume

---

### Post by guillaumesoucy on 2022-06-27
Hello, 

Someone can help please. Thank-you! :wink:

Guillaume

---

### Post by tea for one on 2022-06-27
I'm just supplying some info as I do not own a UPS.

The guide you used in post 1 is dated 2014..
Ubuntu introduced systemd during 2015.
Ubuntu 22.04 uses systemd.

Is this site any use?
It seems to contain a vast amount of info and documentation.
[https://networkupstools.org/index.html](https://networkupstools.org/index.html)

---

### Post by guillaumesoucy on 2022-06-27
Okay I will look at this. 

Thank-you!

Guillaume

---

