---
title: "nvidia GeForce  8800GT Multi screen problem"
date: 2008-08-18
forum: Hardware
---

### Post by sherwoodwf on 2008-08-18
I have just installed ubuntu and I cannot use multi screen any more. I have both of my screens plugged into the GPU and all I get is one of my screens at a time. 

When I first turn on my computer it starts loading on screen number 1. But when it gets into ubuntu it moves to screen 2 and I get no signal input from screen 1. 

Any idea why/how? 

Or how to solve it.

Thanks

---

### Post by overdrank on 2008-08-18
> **sherwoodwf said:**
> I have just installed ubuntu and I cannot use multi screen any more. I have both of my screens plugged into the GPU and all I get is one of my screens at a time. 

When I first turn on my computer it starts loading on screen number 1. But when it gets into ubuntu it moves to screen 2 and I get no signal input from screen 1. 

Any idea why/how? 

Or how to solve it.

Thanks

Hi and if you have the nvidia drivers installed you can use nvidia settings to setup your extra monitor. Use the keys alt, F2 and enter the command ```
gksu nvidia-settings
```

---

### Post by sherwoodwf on 2008-08-18
I tried that and nothing seem to happe. All it did was ask for my password and then nothing happened after that.

Is that suppose to happen or am I doing something wrong?

---

### Post by overdrank on 2008-08-18
> **sherwoodwf said:**
> I tried that and nothing seem to happe. All it did was ask for my password and then nothing happened after that.

Is that suppose to happen or am I doing something wrong?

Hi and if you are using hardy then you will have to install the settings. Go to synaptic manager, located under system, administration and install.

---

### Post by sherwoodwf on 2008-08-18
okay I think I have done that. I went to Synaptic Package manager and installed gksu is that right? 

Also is there a program that I have to configure my screens with as well or should they both just work automaticly after installing gksu?

---

### Post by overdrank on 2008-08-18
> **sherwoodwf said:**
> okay I think I have done that. I went to Synaptic Package manager and installed gksu is that right? 

Also is there a program that I have to configure my screens with as well or should they both just work automaticly after installing gksu?

Hi and nvidia settings is what you will need to install. gksu should be installed by default. :)

---

### Post by sherwoodwf on 2008-08-18
okay so I have to install nvidia settings? But in synaptic package manager there are lots of diffrent things for nvidia. Any chance you know which one I need?

I appoligise I am very new to linuz/ubuntu.

---

### Post by overdrank on 2008-08-18
> **sherwoodwf said:**
> okay so I have to install nvidia settings? But in synaptic package manager there are lots of diffrent things for nvidia. Any chance you know which one I need?

I appoligise I am very new to linuz/ubuntu.

Ok if you used synaptic manager and searched for nvidia settings only one will be shown. If you have install it then you may use the command given earlier. 
Have you installed the nvidia drivers for you graphics card?

---

### Post by sherwoodwf on 2008-08-18
Yes I have isntalled the drivers .No I didn't have nvidia settings installed. Just installed it now. Typed in the command I was given above and now I get my Nvidia X Server Settings? It looks like the right menu.

I would like to thank you all who helped me out :D

---

### Post by sherwoodwf on 2008-08-18
sorry to have to double post but I thought I had it sortecd but I geuss I haven't. After plugging both screens up to my PC now when I turn it on one just says going to sleep and the other one just stays lit up but is just blank. 

So I don't no what to do know?

---

### Post by overdrank on 2008-08-18
> **sherwoodwf said:**
> sorry to have to double post but I thought I had it sortecd but I geuss I haven't. After plugging both screens up to my PC now when I turn it on one just says going to sleep and the other one just stays lit up but is just blank. 

So I don't no what to do know?

Ok try and boot into recovery mode which is usually the second choice from the grub and use the xfix option and hopefully this will get you back to the desktop.

---

### Post by sherwoodwf on 2008-08-18
Okay well that sorted out shutting both screens off now. But I only get one that works and my other just say not avalible. 

I also get this message when I try and go into nvidia X server setting like told above.

'You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.'

Thats the message

---

### Post by dingansich on 2008-08-18
I would recommend heading over to nvidia's website and grabbing the latest driver package from there.  There's a readme in it that should explain the basic installation.  But generally this means extracting the archive, stopping your xserver (either by sending 'stop' to gdm, or dropping your run level (init 1 should do it), and then running the install script as root.  (You'll need to use sudo to do all of that.)

The installer will give an option to configure your xorg.conf file - say 'yes' and that should make sure that your driver is set properly.  If everything goes according to plan, then when Ubuntu boots back up, you should be able to get your resolution/dual-monitor etc. running from the nvidia config panel - which the driver should also install.

I'm sure there are threads on the forum that provide much better explanations about this than I have done here.

---

