---
title: "Need help fixing Ubuntu 7.something"
date: 2008-08-08
forum: Hardware
---

### Post by blackriven on 2008-08-08
I installed Ubuntu on an HP laptop and turns out a bunch of hardware, including the modem, is unsupported. I went online and started doing research for workarounds, but I'm having difficulty implementing them. 

I downloaded ndiswrapper and the modem's drivers, but I'm unable to compile ndis. It doesn't find any of the header files and reports implicit declarations on every function that uses them. 

I do have an updated version of the kernel and of gcc, but apparently there's something called essential gcc package or something to that effect that I probably lack (hence the compilation problems). Also, when I typed the command to the kernel directory the readme file said I should have an include folder and a .config file. I have the folder but not the config file. How do I adress all these things? 

Thanks in advance.

---

### Post by Kevbert on 2008-08-08
If you use the original install disk it should be on there with all dependencies.  Go to System-Admin-Software Sources and tick the CDROM box.
Now if you run up System-Admin-Synaptic Package Manager is should look for the CD and you can search for ndiswrapper from there.
Remember once you've installed everything you need, to turn off the CDROM access by unticking it in Software Sources (otherwise you'll get prompts to put the CD in the drive when using Synaptic).

---

### Post by doas777 on 2008-08-08
make sure you have the build-essential package installed. you can find it in the repositories.

I didn't have to compile ndis on my HP, so you may want to look into a simpler (downloading) approach.

---

### Post by blackriven on 2008-08-08
Really? What model do you have? I have a Pavillion dv6500.

---

### Post by doas777 on 2008-08-09
dv9810us and dv9205us. 

if i recall correctly I installed it via the repositories. make sure you have the multiverse enabled and the add medibuntu repos, and see if you can 
```

sudo apt-get install ndiswrapper

```

I used several tutorials to get it going. one of them may have advised adding another repo, so I can't gaurentee that that is where i got it but it's worth a try.

hope that helps,

---

### Post by ThaRabbit on 2008-08-09
Also note that ubuntu 8.04 is the latest release :) It might solve your issues.

---

