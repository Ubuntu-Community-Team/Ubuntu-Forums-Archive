---
title: "nVidia Hybrid SLI able in Ubuntu?"
date: 2008-08-19
forum: Hardware
---

### Post by centered effect on 2008-08-19
I recently purchased a Biostar GF8200 board with onboard graphics and Hybrid SLi capabilities. I plan on getting an extra card for gaming purposes and want to try out Hybrid SLI, Geforce Boost, and Hybrid Power, but I only see this as a feature under Windows Vista. I wonder is Ubuntu capable of this Hybrid technology?
 
[http://www.nvidia.com/object/hybrid_sli.html](http://www.nvidia.com/object/hybrid_sli.html)
 
From Nvidia's User Guide PDF - [http://www.nvidia.com/content/hsli/configurator/assets/pdf/NVIDIA_Hybrid_SLI_User_Guide.pdf](http://www.nvidia.com/content/hsli/configurator/assets/pdf/NVIDIA_Hybrid_SLI_User_Guide.pdf)
 
> 
[LEFT][SIZE=5]Hybrid SLI [/SIZE][/LEFT]

[FONT=Garamond,Garamond][SIZE=3]SLI technology enables two discrete GPUs to work together and provide increased graphics performance. Hybrid SLI technology is similar to SLI technology in that it enables a 
[/SIZE][/FONT][LEFT]*[FONT=Garamond,Garamond][SIZE=3]motherboard [/SIZE][/FONT]*[FONT=Garamond,Garamond][SIZE=3]GPU ([/SIZE][/FONT]**[FONT=Garamond,Garamond][SIZE=3]mGPU[/SIZE][/FONT]**[FONT=Garamond,Garamond][SIZE=3]) to work with a [/SIZE][/FONT]*[FONT=Garamond,Garamond][SIZE=3]discrete [/SIZE][/FONT]*[FONT=Garamond,Garamond][SIZE=3]GPU ([/SIZE][/FONT]**[FONT=Garamond,Garamond][SIZE=3]dGPU[/SIZE][/FONT]**[FONT=Garamond,Garamond][SIZE=3]) to provide two key benefits to the user. [/SIZE][/FONT]
[FONT=Wingdings,Wingdings][SIZE=1]&#56256;&#56457; [/SIZE][/FONT]**[FONT=Garamond,Garamond][SIZE=3]GeForce Boost [/SIZE][/FONT]**[FONT=Garamond,Garamond][SIZE=3]The GeForce Boost feature enables the motherboard GPU to work collaboratively with the discrete GPU to increase the performance of the discrete GPU. When GeForce Boost is enabled, the [/SIZE][/FONT]**[FONT=Garamond,Garamond][SIZE=3]m[/SIZE][/FONT]**[FONT=Garamond,Garamond][SIZE=3]GPU and [/SIZE][/FONT]**[FONT=Garamond,Garamond][SIZE=3]d[/SIZE][/FONT]**[FONT=Garamond,Garamond][SIZE=3]GPU share the rendering load by rendering different frames of an image. Thus the graphics processing power of the [/SIZE][/FONT]**[FONT=Garamond,Garamond][SIZE=3]m[/SIZE][/FONT]**[FONT=Garamond,Garamond][SIZE=3]GPU is harnessed to enhance the processing power of the [/SIZE][/FONT]**[FONT=Garamond,Garamond][SIZE=3]d[/SIZE][/FONT]**[FONT=Garamond,Garamond][SIZE=3]GPU. [/SIZE][/FONT]
[FONT=Wingdings,Wingdings][SIZE=1]&#56256;&#56457; [/SIZE][/FONT]**[FONT=Garamond,Garamond][SIZE=3]HybridPower [/SIZE][/FONT]**[FONT=Garamond,Garamond][SIZE=3]The HybridPower feature enables the user to switch off the [/SIZE][/FONT]**[FONT=Garamond,Garamond][SIZE=3]d[/SIZE][/FONT]**[FONT=Garamond,Garamond][SIZE=3]GPU when the maximum performance of the [/SIZE][/FONT]**[FONT=Garamond,Garamond][SIZE=3]d[/SIZE][/FONT]**[FONT=Garamond,Garamond][SIZE=3]GPU is not required and use the [/SIZE][/FONT]**[FONT=Garamond,Garamond][SIZE=3]m[/SIZE][/FONT]**[FONT=Garamond,Garamond][SIZE=3]GPU for non-intensive graphics applications, such as high definition DVD playback, Web surfing, and office productivity applications. Switching off the [/SIZE][/FONT]**[FONT=Garamond,Garamond][SIZE=3]d[/SIZE][/FONT]**[FONT=Garamond,Garamond][SIZE=3]GPU not only lowers the total system power consumption but also lowers total system noise and heat. [/SIZE][/FONT]
 

[/LEFT]

---

### Post by loweb1 on 2008-09-13
I'm also curious about this.

I'm building a new system using the same motherboard and a GEForce 9500 GT discrete video card.

---

### Post by pelle.k on 2008-09-23
from what i understand, this is something nvidia will have no support for in their linux drivers. correct me if i'm wrong.

I was thinking of buying this laptop;
[http://www.fujitsu-siemens.com/home/products/notebooks/amilo_xi_3650.html](http://www.fujitsu-siemens.com/home/products/notebooks/amilo_xi_3650.html)

Apparently it's a gf 9600 gt with hybridpower (e.g. intel x4500 gpu on the mainboard). So, if there's no support for hybridpower, and i just pop in the ubuntu install cd, what gpu is going to be activated? Confusing to say the least!
Anyone know how one chooses "mode"? Is it done by hardware, i.e. if i switch in say windows, will the "mode" stick when booting linux?

---

### Post by avilella on 2009-03-19
Hi,

We are gathering DSDT information from people owning systems with Nvidia HybridPower or ATI PowerXpress cards.

Can please people who have hardware like this post the DSDT tables here?

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/312756](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/312756)

---

