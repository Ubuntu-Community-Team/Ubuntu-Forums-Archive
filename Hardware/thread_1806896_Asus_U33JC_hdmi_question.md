---
title: "Asus U33JC hdmi question"
date: 2011-07-18
forum: Hardware
---

### Post by Washus on 2011-07-18
Hi all.

I'm about to buy a ASUS U33JC  for use with ubuntu. It' s actually the cheapest <14 inch laptop I can buy around where I live:

- i3 370m processor
- HM55 Express Chipset 
- NVIDIA GF 310M - 1GB DDR3 VRAM + Intel GMA HD (Support NVIDIA Optimus Technology)
- 4GB 1066 MHz SDRAM

[http://www.asus.com/Notebooks/Superior_Mobility/U33Jc/](http://www.asus.com/Notebooks/Superior_Mobility/U33Jc/)

It has optimus, but it seems there's a way to either disable the Nvidia GPU via acpi_call module and use the built-in intel GPU instead, or disable the intel gpu (bios option) and use The Nvidia GPU instead. So I think the optimus problem is somewhat solved, even without bumblebee. (Am I being naive here?)

[http://www.linlap.com/wiki/asus+u33jc](http://www.linlap.com/wiki/asus+u33jc)

But it is of the utmost importance to me that HDMI works,  including sound. 
Is it safe to assume that since I can use either the Nvidia proprietary drivers, or the Intel graphics that hdmi will work perfectly in at least one of these two possible configurations?

So, in short, is there any known issues with this laptop and HDMI? Do you own or have seen one of these with hdmi working? Do you think it's safe for me to go ahead and buy it? I don't care too much about 3D performance, and so the built in Intel should be enough for my needs. **But I do need HDMI working.**

Any thoughts will be greatly appreciated.

Thanks a lot!

---

### Post by d98jh on 2011-07-19
Hi,

I don't have a U33JC but the similar spec'd U35JC and HDMI works just fine in 11.04 on mine so I don't see why it shouldn't on the U33JC that you have. Any other questions? Might not have an answer for you but I promise I'll try. :)

---

### Post by Washus on 2011-07-20
Thank you very much for your answer d98jh. I think I'll go ahead and buy it! (I'm glad I asked for a unit to be sent to my local shop. They're already sold out online because of the great sale price.) 

How did you circumvent optimus? Which GPU are you using? Did you disable the Nvidia via acpi_call or did you disable the Intel in the Bios? Or maybe you are using Bumblebee....

Did everything work with 11.04 out of the box or did you have to do some extra stuff? What should I expect? Although I used Ubuntu before on a laptop, I'm not very familiar with it, since I usually use Gentoo, 

I'll probably have a few more questions when I get my U33JC (probably Friday) and install Ubuntu on it.   

Thanks again for your help!
Washington

---

### Post by d98jh on 2011-07-20
> **Washus said:**
> 
How did you circumvent optimus? Which GPU are you using? Did you disable the Nvidia via acpi_call or did you disable the Intel in the Bios? Or maybe you are using Bumblebee....
I unfortunately don't have the option to disable the Intel card in BIOS so initially I just disabled the nvidia card with acpi_call but now I'm using bumlebee which works great.

> **Washus said:**
> 
Did everything work with 11.04 out of the box or did you have to do some extra stuff? What should I expect? Although I used Ubuntu before on a laptop, I'm not very familiar with it, since I usually use Gentoo, 

I used some of the tips in this blog: 
[http://robbyx.net/blog/?p=190](http://robbyx.net/blog/?p=190)
Didn't find that all of them were needed though. I'm also using the latest compat-wireless drivers since I was unable to use 802.11n otherwise.

> **Washus said:**
> 
I'll probably have a few more questions when I get my U33JC (probably Friday) and install Ubuntu on it.   

Thanks again for your help!
Washington

Glad to help. Just ask if there's anything else you're wondering about. Might forget to check the thread though so just send me a PM.

---

### Post by Washus on 2011-07-25
Hi

I bought the U33JC and except for one major issue (for me) it works fine out of the box using 11.04 64bit, with some minor issues easily solved (suspend, upside down cam on skype). All video configurations I discussed above work fine, including HDMI with sound in all of them.

The major issue I have now is poor video playback.  Frame tear occurs in every single configuration I tried:

[http://ubuntuforums.org/showthread.php?t=1811711](http://ubuntuforums.org/showthread.php?t=1811711)

---

### Post by d98jh on 2011-07-26
Did you try the Vsync settings mentioned in this thread?
[http://ubuntuforums.org/showthread.php?t=1680775](http://ubuntuforums.org/showthread.php?t=1680775)

---

### Post by DiamDavid on 2011-08-26
Hello, I need help with webcam and flash player. For my work I need to use the Talk Fusion - Video Email. More information [http://1186645.talkfusion.com/](http://1186645.talkfusion.com/) Unfortunately the service did not count with the support of Linux. (I have a laptop Asus U33jc, Ubuntu 11.04 32 bit.) Generally I have a problem with the webcam in Skype and I talk fusion inverted image. Skype can be solved script, which is on the forums, but in combination with flash it is impossible for me because it is not a flash in Firefox and Chrome be able to work fully and not to set up and operate. Probably should be added driver for the camera and something to add flash. Can you help please?

---

