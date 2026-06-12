---
title: "Cannot get resolution higher than 1024x768"
date: 2013-03-09
forum: Hardware
---

### Post by Ibnz1009 on 2013-03-09
I'm new to Ubuntu and I cannot figure out why it won't allow me to set my resolution to 1280x1024. I've looked at countless forums and nothing has helped. I have a laptop with an **Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller. **There's no driver updates or anything along those lines. I ran Gparted from a disc and it allowed me to set my resolution even higher than 1280x1024 so I know it's capable. Thoughts?

---

### Post by foresthill on 2013-03-09
How old is the laptop? Which Ubuntu version are you using? Is it 32 or 64 bit?

---

### Post by Ibnz1009 on 2013-03-10
Laptop is at least 3 years old. I'm using 32bit

---

### Post by neu5eeCh on 2013-03-10
Out of curiosity, try installing the Jupiter Power Applet:
> 

sudo add-apt-repository ppa:webupd8team/jupiter && sudo apt-get update

then:

> sudo apt-get install jupiter

Reboot. 

Then click on the Jupiter power applet and see what screen resolutions it offers you.

---

### Post by Absolute Terror on 2013-03-11
Gonna talk a wild guess and say that you have Ubuntu 12.10 and an Nvidia graphics card, yes?

Switch to 12.04, The latest version has some bug where it removes the headers when you install Nvidia drivers. 12.04 is much more stable in general too.

---

### Post by Ibnz1009 on 2013-03-11
Jupiter wont open.

I have 12.10 and I believe it's just a stock Intel graphics card. If I downgrade to 12.04, would I have to wipe my computer again?

---

### Post by Absolute Terror on 2013-03-11
I'd say so, if there is a downgrade option it's too much effort.

```
sudo apt-get install linux-headers-generic
sudo apt-get install linux-source
```

Try installing these if you insist on sticking with 12.10 and then restart your computer to see if it helps.

---

### Post by sudodus on 2013-03-11
What resolution is it on your built in screen? (I guess 1024x768). And you want more on an external monitor. I think you should use your menu program for screen settings, and set the computer to show different pictures on the internal and external monitor, or to set it to only use the external monitor.

---

### Post by Ibnz1009 on 2013-03-11
Jupiter shows up on the top bar, but it doesn't respond when I click "Screen resolutions" or anything like that.


My current resolution is 1024x768 but I would like it to be 1280x1024. I don't have any exterior monitors. The screen on 1024x768 looks really stretched horizontally and if I suspend it, it resumes looking normal, but doesn't stretch all the way across the screen. There's large black bars on the sides. I've never seen that before.

---

### Post by sudodus on 2013-03-12
> **Ibnz1009 said:**
> Jupiter wont open.

I have 12.10 and I believe it's just a stock Intel graphics card. If I downgrade to 12.04, would I have to wipe my computer again?

I think that the first thing to do is to download a few iso files with different flavours of Ubuntu 12.04, Lubuntu, Xubuntu and standard Ubuntu. Lubuntu has an ultra light desktop environment and Xubuntu has a light desktop environment and standard Ubuntu has more eye-candy, but needs more 'horsepower'. Make boot CD or USB drives and try them without installation.

You should get full resolution on your screen. If still problems, you need to give us more information about your computer, at least

- brand name and model
- cpu
- ram
- graphics card/chip (if more than one, that is if you have more than the intel graphics)
- wifi card/chip/adapter

---

