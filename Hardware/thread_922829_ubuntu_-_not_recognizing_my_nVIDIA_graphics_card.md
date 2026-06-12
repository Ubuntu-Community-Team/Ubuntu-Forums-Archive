---
title: "ubuntu - not recognizing my nVIDIA graphics card"
date: 2008-09-17
forum: Hardware
---

### Post by ninch on 2008-09-17
Ubuntu 8.04 used to recognize my graphics card. I have been using it for about 3 weeks now. But now all of a sudden when I turned on my computer today, it could not recognize my nVidia geforce graphics card (series 7). A pop-up came in the beginning which said:

"Ubuntu is running in low graphics mode because it cannot recognize your graphics card. Click configure if you want to manually configure the graphics card, or cancel to run ubuntu in low-graphics mode."

I tried to configure it, but with no luck. I am kind of new to linux. I decided to run it in low graphics mode, and tried to change the screen resolution (which was 800x600 in the low graphics mode) to 1680x1050 (my default monitor resolution). However, the only screen resolutions I could choose were 800x600 and 600x400..

I am now on windows xp, and XP has recognized my graphics card fine, so I know that there is no problem with the card. If this helps, I did recently install "hardy-proposed" updates to my computer. Normally, I only install the security and the supported updates, but I wanted to try the hardy proposed updates..dont ask why :s

ANY help will be greatly appreciated.
Thanks in advance,

Ninch

---

### Post by ninch on 2008-09-17
bump

---

### Post by IntuitiveNipple on 2008-09-17
What nvidia video driver is installed? 

The Ubuntu Restricted Driver is nvidia-glx-new. You might also have installed directly from Nvidia or using the Envy scripts.

It sounds as if you've installed a kernel update and not also updated the associated video chip-set driver kernel module.

---

### Post by ninch on 2008-09-17
nvidia-glx-new is already installed, but the graphics card does not show up under the system->hardware drivers

I do not really understand what you mean.

Thanks for the post, though

EDIT:
I did not upgrade my older ubuntu to get 8.04. I downloaded the file onto a cd and then installed it onto my computer. This computer only installed ubuntu once, and that was with 8.04

---

### Post by Sef on 2008-09-17
Please don't bump your thread until 24 hours has gone by.  Thank you.

---

### Post by ninch on 2008-09-17
nice avatar, and sorry, it wont happen again.

I un-installed then re-installed nvidia-glx-new but I had no success. The hardware drivers still cannot recognize my graphics card.

I do not mind re-installing all the software I need to, I just do not want to re-install all of ubuntu again. As of now, my first goal is to try and make ubuntu recognize my graphics card. Any suggestions will be welcomed.

---

### Post by gali98 on 2008-09-17
please post the output of lshw -C video

Kory

---

### Post by dharkus on 2008-09-18
i'm having the same problem - my result to that is:
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: G70 [GeForce 7600 GS]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list
       configuration: latency=0
and that not the only driver that doesn't appear - none of my drivers appear in system>admin>hardware drivers

---

### Post by gali98 on 2008-09-18
You might try using envy

sudo apt-get install envyng-gtk

envyng-gtk

The interface is pretty self explanatory...
Kory

---

### Post by ninch on 2008-09-18
Thanks for your replies.

Envy worked great for me, and now ubuntu recognized my graphics card.
Thanks :)

---

### Post by gali98 on 2008-09-18
Sweet.... cause I wouldn't have known anything else to do :P
Kory

---

