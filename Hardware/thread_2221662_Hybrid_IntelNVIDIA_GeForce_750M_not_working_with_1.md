---
title: "Hybrid Intel/NVIDIA GeForce 750M not working with 13.10/14.04"
date: 2014-04-04
forum: Hardware
---

### Post by Carlos_Eduardo_Gel on 2014-04-04
Hi,

I just bought a ["]dell inspiron]("http://www.shopping.com/dell-inspiron/products?CLT=SCH&linkin_id=8058742&subTrackingID=[USERID) 14r 5437-a40 with a hybrid card an [Intel card]("http://rover.ebay.com/rover/1/711-53200-19255-0/1?toolid=10029&campid=CAMPAIGNID&customid=CUSTOMID&catId=58058&type=2&ext=131154536112&item=131154536112") and a Nvidia GT 750M card.

I tried various instructions to make it work, and none of them actually worked.

I follow instruction to make the 750M running all the time, and I had a black screen after login.

And the instructions to install bumblebee, I simply can't run no app  with optirun, it returned with a message like "Cannot access secondary  GPU" "No devices detected".

My question is: If someone out there made the GT 750M work on Linux, please tell us!

---

### Post by Timothe_NICOLAS on 2014-05-03
Hi all,

I know this has been discussed at many places, but I still have not been able to solve this problem. I can't get my hybrid intel/NVIDIA system to work with Ubuntu. At first I received my PC in february from keynux firm ([http://keynux.com/default_zone/fr/html/home.php](http://keynux.com/default_zone/fr/html/home.php)), I believe the model is Ymax5M, with an intel chipset and an Nvidia GeForce 750M graphics card. When I received it, the company had installed Ubuntu 12.04 with bumblebee. However, after I tried the graphics card and it was not working, they told me that the problem of hybrid graphics was not solved for Nvidia cards of the 7.. series. So I was quite unhappy but decided to try something... So after reading a few things, in particular

[http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/](http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/)
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

I installed a 13.10 distro next to my 12.04. Then I installed

nvidia-319
nvidia-prime

It did not work since I ran into the "your system will run in low graphics mode" error.

So I upgraded to 14.04 and tried to install

nvidia-331
nvidia-prime

Still same error after reboot. So now I am at a loss... No other thread found on the web was able to help me out. Note that I do not necessarily care about switching between the intel and Nvidia cards. Since I will most often use my 12.04 for office work, I can use my 14.04 just for playing and then it is OK even if only the Nvidia card is used, I think.

Any ideas ? In particular, is it true that it could be due to the fact that my Nvidia card is of the 7.. series, as the company which sold me the PC told me ?

Thanks in advance
Best

---

### Post by ewmcnee on 2015-02-22
I have the exact same problem with my Inspiron 15 7000. I read this from the NVIDIA website:

> [COLOR=#333333][FONT=UbuntuRegular]Note that the list of supported GPU products is provided to indicate which GPUs are supported by a particular driver version. Some designs incorporating supported GPUs may not be compatible with the NVIDIA Linux driver: in particular, notebook and all-in-one desktop designs with switchable (hybrid) or Optimus graphics will not work if means to disable the integrated graphics in hardware are not available. Hardware designs will vary from manufacturer to manufacturer, so please consult with a system's manufacturer to determine whether that particular system is compatible.[/FONT][/COLOR]

I think we may be out of luck for now. :-(

---

### Post by ewmcnee on 2015-02-22
I am having the same problem with my Dell 15 7000. It has an NVIDIA 750m graphics card that I can't get working under Linux. Here is what I found on the NVIDIA website:

> [COLOR=#333333][FONT=UbuntuRegular]Note that the list of supported GPU products is provided to indicate which GPUs are supported by a particular driver version. Some designs incorporating supported GPUs may not be compatible with the NVIDIA Linux driver: in particular, notebook and all-in-one desktop designs with switchable (hybrid) or Optimus graphics will not work if means to disable the integrated graphics in hardware are not available. Hardware designs will vary from manufacturer to manufacturer, so please consult with a system's manufacturer to determine whether that particular system is compatible.[/FONT][/COLOR]

I fear that our laptops may not have a means to disable the integrated graphics (Intel HD). :-(

---

### Post by mörgæs on 2015-02-23
Merging two similar threads.

Ewnmcnee, please don't double-post. You could try 15.04 and see if the new kernel brings improvements.

---

### Post by efflandt on 2015-02-23
ewmcnee, which Ubuntu version are you running? I have an MSI laptop with Intel HD 4600/Nvidia GTX 765m and all I had to do after recently installing 64-bit Ubuntu 14.04.1 (which recently changed to 14.04.2), was to install **nvidia-331-updates**. I used synaptic to install that, but unless you installed some other nvidia version that you need to purge first, it could also be done from a terminal:```
sudo apt-get update
sudo apt-get install nvidia-331-updates
sudo reboot
```

Then from NVIDIA X Server Settings you should be able to select Nvidia (default) or Intel graphics. You can also set profiles to automatically switch between them, but I have not looked into details of that yet. I just left it set to nvidia graphics which works fine for Steam and Steam games.

Additional things had to be done in 13.10, but that is end of life anyway.

---

