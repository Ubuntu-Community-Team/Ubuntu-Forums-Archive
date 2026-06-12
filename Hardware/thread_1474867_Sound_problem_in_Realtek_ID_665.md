---
title: "Sound problem in Realtek ID 665"
date: 2010-05-06
forum: Hardware
---

### Post by joyous on 2010-05-06
Hi there,

I have Dell studio 1450 with Realtek ID 665 sound card. I have installed Ubuntu 9.10 and works properly except the speaker. There is a low sound on headphone but no sound from the inbuilt speaker. Though it works properly in windows. 

I have searched for the alsa drivers for the above sound card and found that there is no alsa drivers for this sound card. So Is there any solution or Should I try with Fedora or Mandriva ???

Please help ...........

Thanks
joy):P

---

### Post by freefallguy on 2010-05-06
Try here:
[http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/)

or here:

[http://ubuntuforums.org/showthread.php?t=1278146&highlight=ALSA+upgrade&page=2](http://ubuntuforums.org/showthread.php?t=1278146&highlight=ALSA+upgrade&page=2)

---

### Post by joyous on 2010-05-07
Hi,

I have tried with first option to upgrade alsa with [http://monespaceperso.org/blog-en/20...ic-koala-9-10/]("http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/"). But I am getting error like 
checking form.h presence... yes
checking for form.h... yes
checking for new_panel in -lpanelw... no
configure: error: panelw library not found
I have tried with the options there. But the 'cat /proc/asound/version' command is showing that i have already alsa version 1.0.22.1. (Advanced Linux Sound Architecture Driver Version 1.0.22.1.)

Still, there is no sound from the inbuilt speaker.
Ohh...I have HDA : Intel G45 DEVCTG with codec Realtek ID 665.
So what should i do next??

Thanks
joy

---

### Post by dino99 on 2010-05-07
install paprefs and gnome-alsamixer (tweak the settings)

into /etc/modprobe.d/alsa-base.conf
add the good codec
options snd-hda-intel model= (try with "model=auto" or "enable_msi=1"
( info at cat /proc/asound/card0/codec#* | grep Codec )

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by alex_kent_18 on 2010-05-08
Hi, 

I think, you might have downloaded an old driver. Refer to my post, it should work as I have got dell studio 1450 and same problem as your laptop but I could manage to solve it.

You can find the step by step procedures in that post. Here is the link :
[http://ubuntuforums.org/showthread.php?t=1473191&highlight=dell+studio+1450]("http://ubuntuforums.org/showthread.php?t=1473191&highlight=dell+studio+1450")

All the best!

---

### Post by joyous on 2010-05-10
> **alex_kent_18 said:**
> Hi, 

I think, you might have downloaded an old driver. Refer to my post, it should work as I have got dell studio 1450 and same problem as your laptop but I could manage to solve it.

You can find the step by step procedures in that post. Here is the link :
[http://ubuntuforums.org/showthread.php?t=1473191&highlight=dell+studio+1450](http://ubuntuforums.org/showthread.php?t=1473191&highlight=dell+studio+1450)

All the best!


 Hi Alex,

 Thank You very much for your information....now I am getting sound from the speaker. Again thanks.
But the quality of the sound is not better as in Windows. Oh.during the last step of installation I got  some warning ! like-
" The mixer channels for the Alsa driver are muted by default ! you would use some Alsa or OSS mixer to set the appropriate volume."
Will there be any problem for this??

Thanks & Regards,
Sujay 
:guitar:

---

