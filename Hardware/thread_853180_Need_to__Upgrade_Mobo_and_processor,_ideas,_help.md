---
title: "Need to  Upgrade Mobo and processor, ideas, help?"
date: 2008-07-08
forum: Hardware
---

### Post by kystorms on 2008-07-08
How would I go about finding out what I need to up grade to in the following hardware departments?

Motherboard
processor
videocard

I need to know how I can locate what I have now ( does Hardy have a software that reads my system and tells me what I have currently?) 
AND how can I then find out what I can upgrade to, that will work with Hardy?


I hope that makes sense, I am a newbie to upgrading hardware

thanks for any and all ideas and help
:-)

---

### Post by developer001 on 2008-07-08
hiii..
i brought a new loptop and i have face few problem about mine laptop..and all stufff help me out .. I need to know how I can locate what I have now ( does Hardy have a software that reads my system and tells me what I have currently?)
AND how can I then find out what I can upgrade to, that will work with Hardy?

---

### Post by Vivaldi Gloria on 2008-07-08
There are a number of commands that give general info about your hardware:

```
lshw
hwinfo
dmidecode
```

If any of these are not installed then search & install them using synaptic.

Preferably use these with sudo:

```
sudo lshw
```

etc.

These spit out so much info that it may be better to save the output into a text file:

```
sudo lshw > info1.txt
sudo hwinfo  > info2.txt
sudo dmidecode  > info3.txt
```

Start by using the short versions

```
sudo lshw -short
sudo hwinfo --short
```

They have flags to restrict the output to certain hardware. For example

```
sudo lshw -class system
```

gives a basic info and motherboard. To learn more about these flags see their man pages:

```
man lshw
```

etc.

If you know nothing about your hardware then first try to find your motherboard model. Then google it to see if it is a socket 775 motherboard (which is the current type) or a previous type. Then find about your processor, ram etc. Then see your motherboards supported hardware list to find out what you can upgrade to.

I remember also seeing some system info applications with a gui in synaptic. You may want to searh for them in synaptic also.

---

