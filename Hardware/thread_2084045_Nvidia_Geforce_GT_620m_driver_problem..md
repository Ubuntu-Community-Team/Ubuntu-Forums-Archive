---
title: "Nvidia Geforce GT 620m driver problem."
date: 2012-11-14
forum: Hardware
---

### Post by Subcomfreak on 2012-11-14
I am currently running xubuntu version 12.04 and am wondering how to install the nvidia graphics drivers.

My machine is an ASUS u47VC ([http://www.asus.com/Notebooks/Superior_Mobility/U47VC/](http://www.asus.com/Notebooks/Superior_Mobility/U47VC/)) that actually has two graphics cards. It has the Nvidia 620m (the one I wish to enable) and an Intel HD 4000 integrated graphics card which I do not want to be disabled. 

So I know that I must install the nvidia drivers. However, under additional drivers there are no drivers available. When I tried to install the drivers from the command line using (sudo apt-get install nvidia-latest or something to that effect) it changed my screen resolution and was unable to to use any other resolution than 620x300. 

The x-server also complained about not having a xorg.conf file, and prompted me to create it with a command in the terminal. I did so and rebooted, but the x-server still said it did not exist. To compound that the x-server didn't seem to recognize my card.

So I did a little research on this xorg.conf file and someone suggested to add a mode with the max resolution of monitor. Well, once I did that and rebooted the screen went completely black right before the long in screen. So, with little linux experience, I was forced to reinstall xubuntu.


So in essence here is my problem:
I want nvidia graphics drivers for my nvidia 620m
I want to disable (if enabled) the intel integrated card
I want to be able to change my screen resolution with the graphics drives
I can not see any "additional drivers" listed on the additional drivers window.

Thank you in advance!

---

### Post by cromefx on 2012-11-14
I had the problem solved trough Bumblebee, check **_[here]("https://github.com/Bumblebee-Project/Bumblebee/wiki/Troubleshooting")_** and **[here]("http://ubuntuforums.org/showthread.php?t=2083855")**.

EDIT: and **[here]("https://wiki.ubuntu.com/Bumblebee#Installation")** and **[here]("http://bumblebee-project.org/install.html")**

---

### Post by cromefx on 2012-11-14
And to change screen resolution and dual monitor use I have [**ARandR Screen Layout Editor 0.1.4**]("http://christian.amsuess.com/tools/arandr/")

---

### Post by Subcomfreak on 2012-11-14
Thank you so much. I will try your solutions!

---

### Post by Subcomfreak on 2012-11-14
I installed ARandR and it seems to be a really neat program. Especially for when I will attach my computer to a monitor! Thank you the advice. I am installing bumble bee right now.

---

### Post by Subcomfreak on 2012-11-16
worked like a charm!

---

