---
title: "ACER Aspire One AO725 fan problem"
date: 2017-11-02
forum: Hardware
---

### Post by pozzo2 on 2017-11-02
Hello everybody. I hope that this is the right section for my thread.
I've got an Acer Aspire One AO725 on which I've installed Lubuntu 17.04. The problem is that the fan doesn't work even if the temperature is rising over the critical value and then the laptop suddenly shuts down.

Thank you for your help

---

### Post by gsahli on 2017-11-02
Read this:
[https://unix.stackexchange.com/questions/328906/find-fan-speed-and-cpu-temp-in-linux](https://unix.stackexchange.com/questions/328906/find-fan-speed-and-cpu-temp-in-linux)

---

### Post by mörgæs on 2017-11-03
Have you updated BIOS / UEFI?

---

### Post by pozzo2 on 2017-11-03
[QUOTE=gsahli]Read this:
[https://unix.stackexchange.com/questions/328906/find-fan-speed-and-cpu-temp-in-linux](https://unix.stackexchange.com/questions/328906/find-fan-speed-and-cpu-temp-in-linux)[/QUOTE]

Yes I've already read something similar, if I use ```
sensors | grep fan
``` I don't get anything. And I've already used ```
sensors
``` by itself to find out the temperature of my computer.

[QUOTE=mörgæs]Have you updated BIOS / UEFI?[/QUOTE]

No, but I've read that it's risky to upgrade it (and I don't know if it is possible to do so having only lubuntu installed on my computer). I consider it as the last option and I was searching for alternative solutions.

---

### Post by mörgæs on 2017-11-04
> **pozzo2 said:**
> 
No, but I've read that it's risky to upgrade it

Have you read that it's risky for your particular hardware? Don't pay attention to what people have experienced using completely different gear.

---

### Post by pozzo2 on 2017-12-30
> **mörgæs said:**
> Have you read that it's risky for your particular hardware? Don't pay attention to what people have experienced using completely different gear.


Sorry if I'm this late with my reply. I've reinstalled windows, updated the bios (the latest one was the 2.12 according to [https://www.acer.com/ac/en/ID/content/support-product/4253;-;AO725](https://www.acer.com/ac/en/ID/content/support-product/4253;-;AO725)) and reinstalled Lubuntu but the problem is still there... ](*,)

---

### Post by mörgæs on 2017-12-30
So far, so good. 
Next step is testing the latest software. How does it work in a live boot of 18.04 (development version)?

---

### Post by pozzo2 on 2017-12-30
> **mörgæs said:**
> So far, so good. 
Next step is testing the latest software. How does it work in a live boot of 18.04 (development version)?

Sorry if my question is stupid but I'm not an expert, I've searched the 18.04 here on [https://lubuntu.net/downloads/](https://lubuntu.net/downloads/). But won't the 18.04 be released on April 2018? (If not, can you please tell me where can I get it?)

---

### Post by mörgæs on 2017-12-30
Yes, release is in April but one can download and test the daily progress: 

[http://cdimage.ubuntu.com/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/daily-live/current/)

---

### Post by pozzo2 on 2018-01-08
> **mörgæs said:**
> Yes, release is in April but one can download and test the daily progress: 

[http://cdimage.ubuntu.com/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/daily-live/current/)

Ok, I tried running it on a Live boot and it worked fine, but then when I installed it on the PC i encountered same problem as before. :confused:

---

### Post by Yellow Pasque on 2018-01-08
Try booting with acpi_osi=Linux

---

### Post by pozzo2 on 2018-01-11
I tried but no results at all... Same as before

---

