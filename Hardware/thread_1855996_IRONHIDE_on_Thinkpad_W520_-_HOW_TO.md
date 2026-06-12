---
title: "IRONHIDE on Thinkpad W520 - HOW TO"
date: 2011-10-07
forum: Hardware
---

### Post by houserparker on 2011-10-07
I spent a night getting this and up and running and couldn't find any complete instructions on how to do it so After working it out I thought I'd take the time to write them up on the forum.

Instructions to install and configure **Ironhide **on a **Thinkpad W520** running Ubuntu 11.04:-

Open a terminal and run through the following steps:-

1. ```
sudo add-apt-repository **ppa:mj-casalogic/ironhide**
```2. ```
sudo apt-get update && upgrade
```3. ```
sudo apt-get install ironhide ironhide-ui
```4. During the installation process a configuration window will pop-up. Follow the prompts. **If in doubt choose all default options available until you exit this window as the most important part is the next step.**

5. In /usr/share/ironhide/examples you'll find various examples of scripts to enable and disable the Nvidia graphics card. The file includes a template and scripts that have already been used and verified by other users. 

In my case I own a Thinkpad W520 so I used the supplied example of the Thinkpad T420 and it works flawlessly.

**Most important thing to remember is that without these power script (ironhide disable/enablecard) configured correctly the Nvidia card will not be powered down. **

To use these pre-defined scripts follow these steps.

In my case:-

6.```
sudo cp -r /usr/share/examples/ironhide-disablecard.lenovo.ThinkPadT420/usr/local/bin/ && mv /usr/local/bin/ironhide-disablecard.lenovo.ThinkPadT420 /usr/local/bin/ironhide-disablecard
```7. ```
sudo cp -r /usr/share/examples/ironhide-enablecard.lenovo.ThinkPadT420 /usr/local/bin/ && mv /usr/local/bin/ironhide-enablecard.lenovo.ThinkPadT420 /usr/local/bin/ironhide-enablecard
```8. Follow the instructions from this link [http://community.linuxmint.com/tutorial/view/610 ]("http://community.linuxmint.com/tutorial/view/610")to configure the inronhide UI applet that allows you specify which programs run discrete graphics through ironhide.

9. After doing all this reboot your computer and on restart run the following in a terminal. ```
optirun glxgears
``` If you see messages that the card is being enabled and disabled successfully everything should be working correctly.

Final note I just want to thank all the people involved in developing this great program.

Good luck!

Cheers,

---

### Post by kfaee on 2011-11-10
Dear houserparker,

thanks for your guide. This sounds promising. Could you please tell me your BIOS settings? I've a Thinkpad T420 and am not sure whether I should disable Optimus and switch to discrete graphics or not.

Thank in advance

---

### Post by croo on 2011-11-14
Thanks houserparker, that was fairly painless and I have a functioning ironhide enabled thinkpad now!

There are some typos in the final cp/mv commands that I'd just hightlight. A space missing in the enable script cp, plus the path is missing one directory (ironhide) on both. Minor details but I tend to cp & paste commands on instructions so I noticed these. 
> sudo cp -r /usr/share/ironhide/examples/ironhide-disablecard.lenovo.ThinkPadT420 /usr/local/bin/ && mv /usr/local/bin/ironhide-disablecard.lenovo.ThinkPadT420 /usr/local/bin/ironhide-disablecardAnd> sudo cp -r /usr/share/ironhide/examples/ironhide-enablecard.lenovo.ThinkPadT420 /usr/local/bin/ && mv /usr/local/bin/ironhide-enablecard.lenovo.ThinkPadT420 /usr/local/bin/ironhide-enablecardThese should be copy & paste safe now :)

Thanks again.

---

### Post by thaibuntu on 2011-11-19
Works on a T520. Thanks for the easy to follow instructions!

---

### Post by buzzcook on 2011-12-06
Thanks for the guide - does this work with Ubuntu 11.**10**?

---

### Post by Spitfire777 on 2011-12-18
Hi,

do I have to install nvidia-current before or after ironhide?

---

