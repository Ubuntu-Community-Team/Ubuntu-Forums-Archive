---
title: "suggestions for asus Eeepc model 701sd"
date: 2008-12-11
forum: Hardware
---

### Post by cmay on 2008-12-11
hi.
i have gotten my new asus Eeee pc back from repair today. it was missing the alt key when i packed it out of the box so i got a repair / trade.  
it is the model 701sd with xandros linux preinstalled which i sort of think is very funny but really not that useful when one is used to using debian and ubuntu . i have tried to run some usb stick distros on it here tonight and this is both eeebuntu and ubuntu eee and puppy linux. i have also been running belenix (open-solaris based) from a usb stick on it. i wonder if anyone has got a suggestion for a good linux for this model of eee pc. i can say first of all i do not need or even want the wireless to work. i do not like wire less but i like to have my webcam working and i would like to have the ordinary internet working as well. i would like to hear from other users of this model what linux they prefere to use and i would like to know what is the most easy one to install and bear in mind the wireless is not important at all. the webcam and the ordinary network connection is however. sound and  battery life means something to me as well as i am going to use it for when i go to the hospital so i want to have so i can read my pdf books and listen to my music on it. (and play supertux :)) 
thanks for your time.

---

### Post by GHerzog on 2008-12-19
I have a 701/4g loaded with Ubuntu EEE 8.04.1.  For the most part, the installation is just fine.  I still have to tweak for the microhone and camera, but the hot keys are working and it seems like an excellent starting point.

This is NOT an official Ubuntu, but a remix and I am abit concerned about updates.  But, the official Ubuntu requires more low level installation at this point.  So, the trade off is to immediately see what Ubuntu can be on an EeePC or to learn to DIY every detail from the start.

Imay have a bug in it that prevents full updates and that is what I am now trying to research.  It sure would be nice if Ubuntu provided a >4gbyte sanctioned version at this point because the EeePC have install about 250,000 copies of the Ubuntu EEE 8.04.1 at this point in time.

---

### Post by snowpine on 2008-12-19
Hi GHerzog, 

Ubuntu eee is now called Easy Peasy, and the new version will be out in January.

Ubuntu's under 4gb version is called Xubuntu, it takes about 1.5 gb. It doesn't support the eee any better than Ubuntu however.

I find the easiest way to get Ubuntu working on the eeeis to install the custom kernel from array.org, which adds support for all of the eee's hardware (wireless, wired, webcam, etc.) and works with Ubuntu/Xubuntu/Kubuntu hardy or intrepid: [http://array.org/ubuntu/](http://array.org/ubuntu/)

It is the same kernel used in Ubuntu eee, so if you already have Ubuntu eee, you don't need it--just pointing it out for other forum readers. :)

---

### Post by slater86 on 2009-02-16
I found the custom kernel works very well and is easy to install/maintain (EeePC 701D).

Thankyou very much snowpine, you've saved me a lot of time and effort.

--Matt

---

### Post by simon_ives on 2009-04-01
Running a vanilla Ubuntu 8.10 on my 701sd here.  All works out of the box except the wireless (which was easy to configure).  I've got the Ubuntu NBR stuff as well which is quite nice.  I'm going to check out this array.org kernel though, seems it may make things a little eeeasier.

---

### Post by roy.b on 2009-04-28
I have just installed the new 904 nbr release on 701sd. It seems to work just fine, except the cursor is really jerky when navigating on the main page. When i am in an application the cursor is fine.

Is there anything that can be done to correct this. I just installed over eeebuntu-nbr 2 which did not seem to have this problem.

---

### Post by dfjkl on 2009-04-28
Yes there is...yes there is.  

[http://ubuntuforums.org/showthread.php?t=1139314](http://ubuntuforums.org/showthread.php?t=1139314)

Slowness issues:

[https://bugs.edge.launchpad.net/linux/+bug/349314](https://bugs.edge.launchpad.net/linux/+bug/349314)

---

### Post by roy.b on 2009-04-28
I followed all of these instructions but still have the same problem, no desktop-switcher and jerky cursor movements over any link on the main page.

---

### Post by VictorR on 2009-05-03
Netbook - Asus EEE PC 701 4GB SSD. After installing new kernel to prevent mouse lag I got no taskbar no window borders.
 
I installed a new .deb from
[https://bugs.edge.launchpad.net/desktop-switcher/+bug/349519/comments/59](https://bugs.edge.launchpad.net/desktop-switcher/+bug/349519/comments/59)
and run

```
gconftool-2 --set /desktop/gnome/session/required_components_list --type list --list-type=string ["windowmanager","panel"]

gconftool-2 --recursive-unset /apps/panel
```

This helped.

The temporary solution to get computer working when there is neither task bar nor windows decorator presented, is to switch to Classic mode then back to Netbook mode.

---

