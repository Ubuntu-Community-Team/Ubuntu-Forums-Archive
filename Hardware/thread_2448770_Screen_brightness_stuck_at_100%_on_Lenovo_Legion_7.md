---
title: "Screen brightness stuck at 100% on Lenovo Legion 7i"
date: 2020-08-13
forum: Hardware
---

### Post by elie2 on 2020-08-13
Hello,

I got the Lenovo Legion 7i last week. I installed Ubuntu on it. Most things work great, except the screen brightness. I can't control it and it's stuck at 100%.

I tried to edit [xorg.conf]("https://askubuntu.com/questions/1217133/cant-control-screen-brightness-acpi-error-lenovo-legion-y540"), but it didn't changed anything.

---

### Post by drpjkurian on 2020-08-23
Hmmm
I'm not sure whether this solution will work for you. I installed an application for my old Lenovo IdeaCentre when the hardware keys failed to reduce the brightness. The application is 'Brightness' which can be downloaded from the 'software center.'

---

### Post by elie2 on 2020-08-23
> **drpjkurian said:**
> Hmmm
I'm not sure whether this solution will work for you. I installed an application for my old Lenovo IdeaCentre when the hardware keys failed to reduce the brightness. The application is 'Brightness' which can be downloaded from the 'software center.'

I installed brightnessctl, is that the right one?

It doesn't give any error, the console output seems fine, but it as not effect.

```

Updated device 'nvidia_0':
Device 'nvidia_0' of class 'backlight':
    Current brightness: 20 (20%)
    Max brightness: 100



```

---

### Post by drpjkurian on 2020-08-25
I'm not sure whether you installed the one I meant. Nevertheless, see my screenshot of my software center.

---

### Post by gsync on 2020-08-25
> **elie2 said:**
> Hello,

I got the Lenovo Legion 7i last week. I installed Ubuntu on it. Most things work great, except the screen brightness. I can't control it and it's stuck at 100%.

I tried to edit [xorg.conf]("https://askubuntu.com/questions/1217133/cant-control-screen-brightness-acpi-error-lenovo-legion-y540"), but it didn't changed anything.


I have Legion Y740 and exactly the same issue.
I installed this one - [http://ubuntuhandbook.org/index.php/2017/05/install-brightness-controller-utility-in-ubuntu-16-04-higher/](http://ubuntuhandbook.org/index.php/2017/05/install-brightness-controller-utility-in-ubuntu-16-04-higher/)
It's working on all releases, including 18.04 and 20.04.

Not to mention that if you have multiple external displays you can control their brightness as well.

---

### Post by elie2 on 2020-08-25
I installed it and it works, but if I'm not mistaken, it's only a software solution, it makes the screen darker, but doesn't actually change the back-light intensity. A hardware solution would be better for battery life.

---

### Post by CelticWarrior on 2020-08-26
> **elie2 said:**
> I installed it and it works, but if I'm not mistaken, it's only a software solution, it makes the screen darker, but doesn't actually change the back-light intensity. A hardware solution would be better for battery life.

You are mistaken.
It changes the backlight intensity - that's what makes the screen darker or brighter - and the result is exactly the same as using dedicated function keys.

---

### Post by elie2 on 2020-08-27
There is two programs mentioned above. 
Today I tried the one mentioned by @gsync ([http://ubuntuhandbook.org/index.php/2017/05/install-brightness-controller-utility-in-ubuntu-16-04-higher/](http://ubuntuhandbook.org/index.php/2017/05/install-brightness-controller-utility-in-ubuntu-16-04-higher/)). I didn't saw any changes in power consumption when looking at powertop.

I will try to test the other one. I'm hopping that I'm wrong and it does indeed change the backlight intensity.

---

