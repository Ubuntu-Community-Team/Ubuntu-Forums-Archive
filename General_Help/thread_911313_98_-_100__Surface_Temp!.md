---
title: "98 - 100  Surface Temp!"
date: 2008-09-05
forum: General Help
---

### Post by Nylo on 2008-09-05
Its been four days since I loaded Ubuntu (Hardy) and I'm here to tell you it has not been a fun ride.  It took me two hours to get the screen reg right, and Im still dealing with the network managers "WPA" issue.  Sometimes it works and some time it don't....  Without me doing a thing!  

Now my laptop is running very hot.  Last night I took a surface IR temp check and got a range from 98-100 degrees!  Will the insanity ever stop?

If anyone has a solution to my hot Vaio please let me know.  I have read this is an issue with many and a fix is needed.  Still if someone has a clue of whats going on here please let me know.  If I cannot resolve this I'm going back to XP.  It maybe bloated but it works.

---

### Post by lackoblacko on 2008-09-05
this could be the reason why

[http://www.chicagotribune.com/business/chi-sony-vaio-recall-080904-ht,0,6001851.story](http://www.chicagotribune.com/business/chi-sony-vaio-recall-080904-ht,0,6001851.story)

---

### Post by nacho32 on 2008-09-05
question can you here the fan run ?

---

### Post by Titan8990 on 2008-09-05
Is that 98-100C or Fahrenheit?

---

### Post by Nylo on 2008-09-05
> **nacho32 said:**
> question can you here the fan run ?

The fan is constantly running at full speed.

---

### Post by Nylo on 2008-09-05
> **Titan8990 said:**
> Is that 98-100C or Fahrenheit?

That's 98-100 Fahrenheit.

---

### Post by Nylo on 2008-09-05
> **lackoblacko said:**
> this could be the reason why

[http://www.chicagotribune.com/business/chi-sony-vaio-recall-080904-ht,0,6001851.story](http://www.chicagotribune.com/business/chi-sony-vaio-recall-080904-ht,0,6001851.story)

Unfortunately my Vaio is about eight years old though it may have the same issue.

---

### Post by yjwong on 2008-09-05
> **Nylo said:**
> That's 98-100 Fahrenheit.

That's a pretty low temperature, since 98 - 100 Fahrenheit is essentially around 37 degrees Centigrade/Celsius. Are you sure?

You can check the internal temperature by opening a Terminal (Applications -> Accessories), and typing the following command:

```

cat /proc/acpi/thermal_zone/THM0/temperature

```

If it complains about file not found, replace THM0 with TZS0 OR TZS1.
Hope that helps.

---

### Post by Nylo on 2008-09-05
> **yjwong said:**
> That's a pretty low temperature, since 98 - 100 Fahrenheit is essentially around 37 degrees Centigrade/Celsius. Are you sure?

You can check the internal temperature by opening a Terminal (Applications -> Accessories), and typing the following command:

```

cat /proc/acpi/thermal_zone/THM0/temperature

```

If it complains about file not found, replace THM0 with TZS0 OR TZS1.
Hope that helps.

Sorry..... Its 98-100 degrees. As in Las Vegas in the summer.  It never ran this hot with XP.  It gets so hot it screws up my WiFi connect.

---

### Post by mb_webguy on 2008-09-05
Um... 100 degrees Fahrenheit isn't really that hot.  CPU temp is normally measured in degrees Celsius, with normal temperatures falling in the 40 to 60 degree range.  That would be from 104 to 140 degrees Fahrenheit.

---

### Post by CEB2nd on 2008-09-05
Take a look at this [Thread]("http://ubuntuforums.org/showthread.php?t=771258").

---

### Post by wolfen69 on 2008-09-05
do not worry if it's 100 F. that is pretty low. if it was 100 C, you probably would have fried your PC to a crisp by now.

---

### Post by Nylo on 2008-09-05
> **mb_webguy said:**
> Um... 100 degrees Fahrenheit isn't really that hot.  CPU temp is normally measured in degrees Celsius, with normal temperatures falling in the 40 to 60 degree range.  That would be from 104 to 140 degrees Fahrenheit.

Humm...  I guess I dont need to worry.  Just seems to produce more heat than it did with XP.

---

### Post by rossjman1 on 2008-09-05
My GPU gets to 102 celcius after playing Enemy Territory.

---

### Post by wolfen69 on 2008-09-05
> **rossjman1 said:**
> My GPU gets to 102 celcius after playing Enemy Territory.

that is hard to believe, as most cpu's will stop working after 80-90C.

---

### Post by rossjman1 on 2008-09-05
> **wolfen69 said:**
> that is hard to believe, as most cpu's will stop working after 80-90C.
My GPU gets to that range cpu stays around 70 degrees.

---

