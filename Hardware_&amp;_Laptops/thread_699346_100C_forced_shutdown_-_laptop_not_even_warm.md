---
title: "100C forced shutdown - laptop not even warm"
date: 2008-02-17
forum: Hardware &amp; Laptops
---

### Post by Argentino on 2008-02-17
Hello, this is my first post, here we go:

I did some searching and could not find an answer, if this is answered please direct me.

I have yet to find a pattern but Ubuntu does a forced shutdown because it tells me the CPU has reached a critical temp (100C). I have felt the bottom of the laptop and it is very nice and cool, actually I find no warm spot on the laptop at all. 

It happened twice while playing Super Mario on gsnes, and once while composing an email on Thunderbird, so I see no obvious pattern.

Is there a way to either fix this or disable it? I do not leave the laptop on when I am not using it so I do not think that if I were to disable the setting it would damage the laptop, and under normal usage it wont go over 40C anyways. 

Pleas help, and thank you in advanced. :)

---

### Post by mridkash on 2008-02-17
I've seen CPU temp on my Laptop rising to 95 degrees C in summers but it didn't do a forced shutdown. Also, from my experience, you cannot guess the temp of CPU by touching the laptop, try feeling the air near the fan outlet. Or, check if the fan is running properly. Can you hear it? It makes a lot of noise when temp goes above 80.

Also, keep a tab on system temp, type this commands in terminal and see whats the output,

```
 cat /proc/acpi/thermal_zone/*/* | grep temp
```

---

### Post by Argentino on 2008-02-18
> **mridkash said:**
> I've seen CPU temp on my Laptop rising to 95 degrees C in summers but it didn't do a forced shutdown. Also, from my experience, you cannot guess the temp of CPU by touching the laptop, try feeling the air near the fan outlet. Or, check if the fan is running properly. Can you hear it? It makes a lot of noise when temp goes above 80.

Also, keep a tab on system temp, type this commands in terminal and see whats the output,

```
 cat /proc/acpi/thermal_zone/*/* | grep temp
```

Well, I feel the vent and it is working fine and the air coming out of the fan is nice and cool, so I know for sure that the CPU is not reaching that temp.

I am thinking that something is not reading the temp right. How can I turn this off?

---

