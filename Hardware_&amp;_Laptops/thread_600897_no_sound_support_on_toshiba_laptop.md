---
title: "no sound support on toshiba laptop"
date: 2007-11-02
forum: Hardware &amp; Laptops
---

### Post by elymic on 2007-11-02
dear friends,

I've recently instaled gusty on my laptop (toshiba satellite a135-s4407), and apparentely there's no support for the sound card - i think it's realtek. i read a few suggestions for getting an alternative open-source driver called alsa, but since i'm very new to linux and totally unfamiliar with the way of installing and configuring any drivers, i'm requesting for your detailed help about this issue. the ubuntu looks and feels really fantastic and i'm looking forward to get some sounds and music out of it as well...

many thanks to you all, please write me back in newbish...

mic

---

### Post by i_TheDevil_i on 2007-11-02
i don't know if that will work for you, but it worked for me (grenier actually gave me this advice)...

> open Synaptic Package Manager, then search packages by the name "backport"
you'll see the list in which just check the "linux-backports-modules".. in the description it's written, that "This package will always depend on the latest generic Linux backported
drivers available." so i think it will automatically upgrade the package when the linux kernel is upgraded.
after installing the package i got the sound working!

The Synaptic Package Manager could be found at "System>Administration" menu... u have to enter your root password (the pass u use to login).then the "linux-backports-modules" - be sure to check exactly "linux-backports-modules" without any version numbers!
Then reboot. The sound worked for me after that =)

About the music. T listen to music, u should install codecs. Once again open the Synaptic Package Manager and do a search of "gstreamer", then check all packages where u can see MP3, MPEG, etc. in Description area =)

P.S.: after marking/checking needed packages in Synaptic Package Manager, click "Apply" button to install them =)

---

### Post by elymic on 2007-11-05
Hi Devil, thanks for the reply! I now have sound and playback options but there isn't full support as I thought I'd get - the headphones out isn't recognized which is still a problem. another problem I face now is failure to conncet with both lan and wireless card, but I can't see how the new drivers are related to this. Did you find these as well? In case you did, could you suggest an explanation and a possible solution?

thanks again!

---

### Post by mimagabooks on 2007-11-06
Smile  Toshiba a135-s4727 or 4527
Gutsy Seems to have broken this fix for Toshiba a135-s4727. I have worked on two of this model and two of the 4527 as well as a 2234. But so far only the models ending in 27 have broken.

But after allot of searching I finally found a solution download and install the realtek High Def Driver for linux.


[http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/)

However the only way I and several others have made this work is as follows.

1. Start with a fresh install of Gutsy (k,u,x which ever you like)

2. Run the first update with your package manager do not install other software. (except a compiler if needed)

3. install the Realtek High Def Driver (or as realtek calls it "codec")

This will install the alsa drivers (1.0.14), your sound wheel will seem to work (1-100%).
Each program will control its own volume level.

Note: If you have already done the driver install steps above and it didn't work in gutsy I will say the only way this realtek driver has work for us is a fresh install.

If there is another way that makes every thing work in gutsy please let me know.

---

### Post by i_TheDevil_i on 2007-11-06
> **elymic said:**
> Hi Devil, thanks for the reply! I now have sound and playback options but there isn't full support as I thought I'd get - the headphones out isn't recognized which is still a problem. another problem I face now is failure to conncet with both lan and wireless card, but I can't see how the new drivers are related to this. Did you find these as well? In case you did, could you suggest an explanation and a possible solution?

thanks again!

the best way to solve the network problem is to find the exact name of your devices (lan & wireless)... then do a search =) 
wireless:
read [this]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") and u'll get your wireless working... if u have the driver CD for your laptop, then extract wireless drivers, then follow the instructions for ndiswrapper (the link). if u haven't got the CD, download the drivers from offsite =)
lan:
don't know what to say, haven't had such problem, so i have no solution.

---

### Post by elymic on 2007-11-15
Hi mimagabooks, thank you for your detailed reply. I had some problems with the wireless' configurations lately so I couldn't post earlier... the thing is I am a complete new to the area of linux os and was encouraged to install Ubuntu and join the community to experience it. What I'm trying to say is I honestly don't know how to follow the second step - running the first update with Synaptic. I blame Microsoft for shaping this helpless behavior to pointing and clicking anything one may need to add... couldn't locate any "Update" button in any of Synaptic sub-menus...

Similarly I'm not sure whether I should install the Realtek driver by downloading the file from the site or via Synaptic only - please guide me a bit on that.

I can't suggest a fresh install as a solution because sound didn't work at all for my laptop or desktop in any of the fresh installs I had.

Sorry for addressing such baic topics but I'm really determined to remain with an elegant and open-source os and eventually figure out how to control it, and I have to start from somewhere..
thanks

---

### Post by Sozin on 2007-11-16
> **i_TheDevil_i said:**
> i don't know if that will work for you, but it worked for me (grenier actually gave me this advice)...



The Synaptic Package Manager could be found at "System>Administration" menu... u have to enter your root password (the pass u use to login).then the "linux-backports-modules" - be sure to check exactly "linux-backports-modules" without any version numbers!
Then reboot. The sound worked for me after that =)

About the music. T listen to music, u should install codecs. Once again open the Synaptic Package Manager and do a search of "gstreamer", then check all packages where u can see MP3, MPEG, etc. in Description area =)

P.S.: after marking/checking needed packages in Synaptic Package Manager, click "Apply" button to install them =)
Awesome, it works now!! Thank you :)

---

### Post by naveen8888 on 2007-11-22
Hi i own a toshiba A135 S4527,have a problem with realtek audio.... no sound,it says 
Gstreamer plugin missing

I am very new to Ubuntu or linux for that case

just installed it yest,

I have to start from scratch ,  

i wud be very grateful somebody could help me

:(

---

### Post by i_TheDevil_i on 2007-11-22
> **naveen8888 said:**
> Hi i own a toshiba A135 S4527,have a problem with realtek audio.... no sound,it says 
Gstreamer plugin missing

I am very new to Ubuntu or linux for that case

just installed it yest,

I have to start from scratch ,  

i wud be very grateful somebody could help me

:(

omg... actually the "Movie Player" says that "gstreamer" plugin is missing when u try to play music or other media... have a look at previous post, there's an explanation how to install gstreamer plugins (for MP3 and other media playback) and linux-backports-modules (to make your sound working if it doesn't work)

---

### Post by naveen8888 on 2007-11-22
Thanks for replying 
actually before posting i did what u had said

i.e 

synaptics> search >"backport">checked "linux backport modules">installed>rebooted

but still doesnt work,
is there any other way ?

one of the other solutions were to 

 download and install the realtek High Def Driver for Linux.
from
[http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/)

I downloaded it from the website , but don't know to proceed further,
could u guide me step by step after that




thank you

---

