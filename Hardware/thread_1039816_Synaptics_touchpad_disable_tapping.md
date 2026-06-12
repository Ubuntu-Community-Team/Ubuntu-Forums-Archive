---
title: "Synaptics touchpad disable tapping"
date: 2009-01-14
forum: Hardware
---

### Post by jalexstark on 2009-01-14
**...and how can it be made permanent?**

OK, I've tried editing Xorg.conf, I've installed gsynaptics, and I've tried editing the HAL file, but tapping is always reenabled when I log in.

This is an FAQ, so does anyone have a *definitive* answer?

System: Intrepid, up-to-date on 2009/01/12, Dell Inspiron 1505.

The Xorg.conf file got overwritten by some program, so that is no good even if it works initially.

I have tried adding
<merge key="input.x11_options.MaxTapTime" type="string">0</merge>
to /etc/hal/fdi/policy/shmconfig.fdi
But this seems to be ignored.

Thanks!

---

### Post by sergiom99 on 2009-01-16
check if this helps:
[http://ubuntuforums.org/showthread.php?t=1027092&highlight=synaptic+touchpad+tapping](http://ubuntuforums.org/showthread.php?t=1027092&highlight=synaptic+touchpad+tapping)

---

### Post by jlh68 on 2009-01-16
What version of Ubuntu are you using? 

Ubuntu 8.10 will work fine with a synaptic touch pad.  Just click System > Preferences > Touchpad > Taping and then un-click the box in front of the "enable tapping".  Now taps will not affect the touchpad.

If you are not using 8.10, I recommend upgrading to it.

---

### Post by jalexstark on 2009-01-19
Thanks, sergiom99!

I have seen a lot of suggested fixes, but the page that you cited worked for me, and should work in more cases.  There are too many pages claiming to fix this problem.  (I added a note re gsynaptics-init to that page, which proves that there is a bug.)

My only concern would be the order in which startup programs are called, but for now it seems OK on mine.  One could always disable gsynaptics-init in the startup.

---

### Post by declipse on 2009-06-20
> **sergiom99 said:**
> check if this helps:
[http://ubuntuforums.org/showthread.php?t=1027092&highlight=synaptic+touchpad+tapping](http://ubuntuforums.org/showthread.php?t=1027092&highlight=synaptic+touchpad+tapping)

This worked for me as well - Kubuntu 9.04

Thanks!

---

### Post by Nino_Mezza on 2011-01-10
Hello World!

---

### Post by Nino_Mezza on 2011-01-10
> **declipse said:**
> This worked for me as well - Kubuntu 9.04

Thanks!

This worked for me as well - Xubuntu 10.10 

There's universal law out there:grin:

THANX sergiom99, my 1stpost here, UbuntuPeople4President!

---

### Post by jcesp on 2011-03-26
This Worked for ME .....
 
I right Clicked the Synaptics ICON down by the Clock   ,,, and Un tapped !!!!  
 
YOUR DONE,,,  
 
if the Icon is not there Enable the Synaptics program on start up,  by going to run,  then type msconfig.exe , by going to start up items ...  then click the  SYN  tp  
there should be two items , that will work ,,,
  reboot ==  and then right click  the Icon by the clock on Reboot as above to Un tap 
Gary T
Del Mar CA

---

