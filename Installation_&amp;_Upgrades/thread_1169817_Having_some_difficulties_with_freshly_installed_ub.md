---
title: "Having some difficulties with freshly installed ubuntu"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by Endless Dementia on 2009-05-25
Ok, Well I just installed Ubuntu on my vista computer by using wubi. When I started up ubuntu, I updated from add/remove and I tried to do some things which didn't seem to work.
Here is the list of problems I have run into
-I can't change my resolution higher than 1280 x 720 even though my computer supports 1680 x 1050. Is says my monitor is unkown
-When I got to appearance preferences and try to change it to extra, it says it could not enable it
-When I went on youtube it prompted me to download adobe flash player so I did. When the firefox load thing is done I get "Error: wrong architecture 'i386'
-I can not acces my windows vista files.

Any help is GREATLY apreciated. Im new to Ubuntu and I have no idea how to use it but I want to learn how.


EDIT:I updated hardware drivers and now when I change display I get thsi
"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

what does that mean and what do i do 

PLEASE I NEED HELP

---

### Post by coffeecat on 2009-05-25
> **Endless Dementia said:**
> -When I went on youtube it prompted me to download adobe flash player so I did. When the firefox load thing is done I get "Error: wrong architecture 'i386'

This means that either you are running 64-bit Ubuntu and you downloaded the 32-bit version of flash, or vice versa. As a general rule, DON'T download software from the internet - even if YouTube tells you to. **Especially** if YouTube tells you to. :wink: That's the Windows way of doing things. Whenever you can you should use the Ubuntu package manager. Go to System > Administration > Synaptic and install the package flashplugin-nonfree. That will install the correct version of Adobe flash for you. Better still, install the package ubuntu-restricted-extras. That will install flash, a whole load of useful multimedia codecs and the MS core fonts. When you've finished doing that (and trying out Youtube videos), close Synaptic and have a look at Applications > Add/Remove. It's a much more newbie-friendly package manager than Synaptic.

> **Endless Dementia said:**
> -I can not acces my windows vista files.

Oh, yes you can! Although you may be wise not to. Have a look in the Places menu. Your Vista partition will be listed there. Click on it, enter your password where prompted and voila. HOWEVER, if you are running the 64-bit version of Vista, DO NOT write to your Vista partition from Ubuntu. You may make your Vista partition unbootable. This is not Ubuntu's fault. This is a quirk of Vista. In fact you would be wise not to write to your Vista partition even if it's 32-bit. Vista is much more likely to be upset than XP.  *****Edit:** sorry - you're running with wubi. There's a different way of accessing your Windows partition with wubi. I'll see if I can find it and then I'll post again. But in the meantime I'll leave what I said because writing to a Vista partition can be problematic, although you should be OK reading from it. **Edit 2 - see below**

> **Endless Dementia said:**
> I updated hardware drivers and now when I change display I get thsi
"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

Did you reboot? After installing the proprietary nvidia driver you must do a reboot, otherwise you are still using the open-source nv driver, which may explain your monitor resolution problem.

**Edit 2 - accessing Windows partition from wubi**: apparently, it's to be found at /host. What this means is go to Places > Computer. Double-click on 'Filesystem'. Now look in the folder called 'host'. If that doesn't work, look in the folder called 'media'.

---

