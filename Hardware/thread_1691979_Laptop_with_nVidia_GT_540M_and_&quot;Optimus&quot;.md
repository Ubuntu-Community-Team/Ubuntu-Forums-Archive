---
title: "Laptop with nVidia GT 540M and &quot;Optimus&quot;"
date: 2011-02-20
forum: Hardware
---

### Post by seanlano on 2011-02-20
I am looking to purchase a new laptop, a Sager NP5160, which has an nVidia GT 540M and "Optimus" graphics switching, to the internal GPU in the Core i7 CPU. 
I know that, as yet, there is no support in Linux for either the GT 540M or Optimus - but does anyone know if it is likely to be supported in the near future? 
And what about forcing the computer to use the internal Intel GPU (GMA HD), which should have support in Linux? 
I'm not so fussed about automatic switching, but if I can at least manually override it to use the Intel GPU then it will work until there is a Linux driver for the GT 540M.

---

### Post by btermeli on 2011-02-26
I have bought an Acer laptop with Nvidia GT540M / Optimus Tech two days ago. If I install the recommended driver, black screen and GDM is not started.Without driver,effects work perfect.

---

### Post by seanlano on 2011-02-26
So, are you saying that it "just works"? Is this with the Noveau or whatever the default driver is? And compiz works? Have you tried watching HD videos with it? 

Thank you very much!

---

### Post by cascade9 on 2011-02-26
Optimus has about 0% chance of getting nvidia support anytime soon. It might run in a while(IMO 1 year + minimum) with nouveau, but thats no help at all really. No VDPAU, without gallium you get virtually no 3D performance and even with gallium you get very poor 3D performance. 

Unless there is a BIOS switch you cant really force the intel video. It will be used anyway, the main advantage to being able to force the intel video is that in at least some cases, it disables the nVidia GPU. Without that BIOS switch, its unlikely you will be able to disable the nVidia GPU, so it will just suck battery power and create heat. 

IMO......find a different laptop if you want to run linux on it. Some of the earlier i7 models dont have optimus (no intel video on the earlier i7s), that might be yout best bet. 

BTW, nVidia doesnt have even have windows drivers up for the GT5XXM series. If you go to the GT540M page and then click on "Downlaod the latest drivers here" link you go to this page- 

[http://www.nvidia.com/object/notebook_drivers.html](http://www.nvidia.com/object/notebook_drivers.html)

Looks like nvidia might be splitting 'notebook' drivers of the standard geforce drivers. Some bits of that page make me think that they could be dropping support for 'M' (moblie) GPUs with linux totally. More bad news for nvidia linux laptop fans.

---

### Post by seanlano on 2011-02-27
I asked the manufacturer about a BIOS switch for the nVidia/Intel GPU, and there isn't an option for that. The reason I was wanting this particular laptop (Sager NP5160) is that it is available without an OS, meaning that I don't have to pay the so-called "Microsoft Tax". It is almost impossible to get a laptop without Windows on it. And System76 don't ship to Australia. 

Ideally I think I would only need the Intel GPU anyway, my current laptop has only an Intel GMA and it does all that I need. Maybe I could just remove the nVidia graphics card altogether? It would be a bit of a waste, but it would hugely improve battery life. Is the Intel GMA HD supported by linux?

---

### Post by cascade9 on 2011-02-27
How much are you paying for this laptop? Where from? 

As far as the 'microsoft tax' goes, if the laptop is more expensive than similar models with windows, you might as well have paid. 

System76 dont actually build laptops, they just get them from a manufacturer (clevo mostly IIRC). You should be able to buy the same laptops as what system76 sells with a different brandname easy enough. 

AFAIK, you wont be able to remove the nVidia GPU (its only possible with laptops with an MXM slot, and they are rare). 

Intel iX GMA does have linux support. Its not as good as windows support for the same chip in a lot of ways, but it should work.

---

### Post by btermeli on 2011-02-27
```
lspci | grep VGA
```

> 00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df4 (rev a1)

It is possible that Intel integrated card works but not nvidia :(
I haven't tried any HD movie.

---

### Post by seanlano on 2011-03-01
OK, thanks everyone. I think I'm going to reconsider Optimus then. On second thoughts, I think a small and lightweight laptop would be better - I can use a desktop for power usage so I'll look for a small (possibly tablet) laptop instead. :D

---

### Post by QuimNuss on 2011-04-04
Hello folks

I do have an nVidia GT 540M, are you saying there's no way I can make it work properly? There's a VGA button lid on the computer, is that the Optimus switch?

I've been trying to find out what I should do to get it working, at least increase the screen resolution. Any hints on how to do that? At least get partial support?

Also, how can I find out if the Optimus is turned on or not?

Argh, this is frustrating... I'd had switched from ATI to nvidia since they showed more linux support and here we are...

---

### Post by benoch on 2011-05-11
I have problems with a Dell XPS15 with nVidia GT 540M and "Optimus" because I need to use OpenGL and Glut (not running on Ubuntu 11.04). 
I have only a way to skip the problem afflicting me: run Ubuntu in Live Mode. Stuffs seems work on this temporary session. 

Is it possible to modify the linux boot to get nVidia card working properly like in live mode?

thank for answering,
benoch

---

### Post by shamrock_uk on 2011-05-11
Just to give you a gleam of hope, there is some unofficial work going to include Optimus support - it's now working on some laptops, albeit with no power management benefit and still needing manual work at this stage to run nvidia-accelerated apps. 

[http://www.phoronix.com/scan.php?page=news_item&px=OTQxNg](http://www.phoronix.com/scan.php?page=news_item&px=OTQxNg)

---

### Post by khendraw on 2011-06-06
Greetings,

Should there's any silly question or misinterpretation of Ubuntu / Linux, please pardon my lack of knowledge...

I've just made an automated  fresh installation of Ubuntu 11.04 (first 32bit first and then 64bit) on Asus A43SV (core i3, nVidia GT540M) and after installing the restricted driver as recommended by "Additional Drivers" (Jockey) - the restricted driver version number is 270.41.06 - I can run Unity and the default desktop effects.

The 540M chipset is also detected OK on the NVIDIA X Server Settings, Cuda Cores 96, VBIOS version, number of VRAM, and also memory interface.  There is also "Thermal settings" and "Power Mizer" setting to adjust the clocking (adaptive or full performance).

Is this a  sign that the driver is working perfectly on the 540M chipset?  I'm not sure about the nVidia - Intel switching on the Optimus feature with this driver, but at least I can use the most of the nVidia display chipset and I'm very happy with it!

Is there any way to confirm the driver functionality?

Thanks,

---

### Post by John_T on 2011-08-26
I just recently purchased an [MSi GE620]("http://au.msi.com/product/nb/GE620.html#/?div=Specification") notebook. It has an nVidia GE Force GT540M with 1 GB DDR3 RAM. The web site makes no mention of the "Optimus" feature for this model as far as I've noticed.

I installed Ubuntu 11.04 64 bit with no problems, other than that ubuntu said that the display driver wouldn't support Unity, so I'm using the classic interface. No big deal, but I'd like to have the option.

If I try the nVidia Xserver settings utility, I get the following dialog:

[IMG]http://img808.imageshack.us/img808/3687/nvidiaxservermessage.png[/IMG]

When I look a thte additional drivers I see the nvidia driver is installed but not actiivated, as shown below:

[IMG]http://img28.imageshack.us/img28/8268/additionaldrivers.png[/IMG]

I see no way to activate the driver. Has anyone been able to get unity working with this, or a similar graphics adapter?

I'm considering giving gnome 3/gnome shell a try if unity isn't an option. Any thought on that, am I likely to face the same issues?

---

### Post by den_perre on 2011-09-19
> **John_T said:**
> I just recently purchased an [MSi GE620]("http://au.msi.com/product/nb/GE620.html#/?div=Specification") notebook. It has an nVidia GE Force GT540M with 1 GB DDR3 RAM. The web site makes no mention of the "Optimus" feature for this model as far as I've noticed.

I installed Ubuntu 11.04 64 bit with no problems, other than that ubuntu said that the display driver wouldn't support Unity, so I'm using the classic interface. No big deal, but I'd like to have the option.

If I try the nVidia Xserver settings utility, I get the following dialog:

[IMG]http://img808.imageshack.us/img808/3687/nvidiaxservermessage.png[/IMG]

When I look a thte additional drivers I see the nvidia driver is installed but not actiivated, as shown below:

[IMG]http://img28.imageshack.us/img28/8268/additionaldrivers.png[/IMG]

I see no way to activate the driver. Has anyone been able to get unity working with this, or a similar graphics adapter?

I'm considering giving gnome 3/gnome shell a try if unity isn't an option. Any thought on that, am I likely to face the same issues?

I had these exact same problems to. I deactivated Optimus in my bios (dell latitude e6520) Now ubuntu runs solely on the nvidia gpu and i'm not having any problems anymore. For now this is ok for me. Check your bios you might find a similar option that might be of use.

---

### Post by .... on 2011-09-19
This is really a bug in jockey: [https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/660443](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/660443)

People stuck with Optimus might be interested in: [http://www.martin-juhl.dk/2011/08/ironhide-reporting-for-duty/](http://www.martin-juhl.dk/2011/08/ironhide-reporting-for-duty/)

---

### Post by Samiunn on 2011-09-27
You could refer to this [https://launchpad.net/~bumblebee/+archive/stable]("https://launchpad.net/%7Ebumblebee/+archive/stable") 
It works for me. When using the intel graphics, benchmark for glxspheres is about 6-7fps. But when activates the nvidia graphics using command "optirun" from bumblebee project, it rises to 55-60fps. :D

Oh btw i find several people successfully installed the nvidia driver for GT540M which uses Optimus on ASUS A43SV, using the "additional drivers".

---

### Post by realzippy on 2011-09-27
> **Samiunn said:**
> 
Oh btw i find several people successfully installed the nvidia driver for GT540M which uses Optimus on ASUS A43SV, using the "additional drivers".

..when you install bumblebee,the nvidia driver gets installed automatically.

---

### Post by Samiunn on 2011-09-27
> **realzippy said:**
> ..when you install bumblebee,the nvidia driver gets installed automatically.

He didn't even installed the bumblebee. He used the synaptic package manager without problem, and the Nvidia Settings works right-away after installing the driver.

Edit: It's ASUS K43SV.

[http://img827.imageshack.us/img827/4881/screenshotqah.png](http://img827.imageshack.us/img827/4881/screenshotqah.png)

---

### Post by realzippy on 2011-09-28
Ok,I see.
Good to know there is a laptop around to recommend.
Thanks for that info..

---

### Post by Clicksights on 2011-10-05
I have an MSI X460DX with optimus working oke with bumblebee.I went from 60 to 600 Fps!
[B]I did NOT install the Nvidia driver with the additional drivers! When i did that i got an error on booting!

[/B]I did ad the swat drivers deb, and blackilisted the driver that ubuntu installed (nouveau?)
added Bumblebee deb, rebooted, and checked with glxgears / optirun glxgears.
I did have to change a grub setting. But went from 60 to 600Fps!

help: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/699802](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/699802)
post 27! :-)
To get some more transformers to the case:

there is also Ironhide, a fork of Bumblebee, although i didn't try it yet.

---

