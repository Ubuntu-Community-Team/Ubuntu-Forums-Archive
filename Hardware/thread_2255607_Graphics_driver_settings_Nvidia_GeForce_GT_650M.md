---
title: "Graphics driver settings Nvidia GeForce GT 650M"
date: 2014-12-06
forum: Hardware
---

### Post by pieter512 on 2014-12-06
Hello

I am often using Blender for 3D modeling. I do the rendering on my GPU (Nvidia GeForce GT 650M), because it's faster. Therefore, I have the nouveau driver disabled, and I'm using the 331.38 ubuntu Nvidia driver.
The problem I have encounter is the following: when I am rendering, Blender uses 99-100% of the GPU, and this causes the unity shell to have an extreme lag. It takes up to 20 seconds before the sidebar appears for example, and the mouse pointer seems to refresh only 2 times per second. Windows (8.1) doesn't seem to have this problem, I guess this is because Windows uses the Intel graphics. Is there a way to do the same in Ubuntu? Having the Nvidia driver enabled for programs like Blender or Steam, but using the CPU for the window bars and unity etc. ? 
Another problem is video tearing: with the nouveau driver, this doesn't seem to be a problem, but with the Nvidia driver enabled, it's just horrible, it's impossible to watch a movie, especially when a second display is connected. Even when scrolling in a browser or a text editor, I sometimes get those ugly lines, and it takes over a second to refresh the page completely. However, sometimes, there's no problem at all.
What causes this and how can I get rid of it?

Thanks in advance

Pieter

---

### Post by Lorenz_ on 2014-12-06
Maybe you could use bumblebee and just start the programs you need with the GPU. Take a look  at [http://bumblebee-project.org/](http://bumblebee-project.org/)

---

### Post by pieter512 on 2014-12-07
Thanks! I'll give it a try!

---

### Post by pieter512 on 2015-01-03
If someone has the same question: I used this link: [http://askubuntu.com/questions/452556/how-to-set-up-nvidia-optimus-bumblebee-in-14-04](http://askubuntu.com/questions/452556/how-to-set-up-nvidia-optimus-bumblebee-in-14-04) 
I clicked the icon in the right upper corner, then clicked 'Configure Apps' selected 'Blender*' in the left tab, 'Performance mode' in the right tab, and clicked Apply now in the left tab.
If Blender does not show up in the list, it's because you didn't create a [.desktop file.]("https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles") 

At first, I couldn't get the CUDA working, then I installed the Nvidia legacy driver from the Additional Drivers settings. Everything seems to work just fine now. 

* I downloaded Blender from the official site, the version from the software center has fewer features (it's only 2.69) and doesn't support CUDA rendering for Cycles.

---

