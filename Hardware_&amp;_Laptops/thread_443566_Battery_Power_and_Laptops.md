---
title: "Battery Power and Laptops"
date: 2007-05-14
forum: Hardware &amp; Laptops
---

### Post by ghostboy on 2007-05-14
I hope I put this in the right forum. If I didnt, Sorry. 
 
I recently made the move from Windows XP SP2 to Ubuntu 7.04. What I have noticed is that my battery in my laptop seems to last longer and the battery timer is more accurate then in Windows. 
 
For example: On a full battery charge in Windows, my battery would only last about an 1.5 hours, and would need to be plugged in or charged.
 
In Ubuntu, I can run my laptop on battery power for 2-2.5 hours before I need to plug it in or I need to charge. 
 
Has anyone else had this amazing experience? Can someone explain to me why that is?
 
Thanks!!!

---

### Post by whayong on 2007-05-14
To be honest, I don't know how long my battery lasted in XP.  I couldn't tell you how long it lasts in ubuntu either cause I never tried. lol!  If I had to take a stab at it, I'd say RAM usage is the biggest factor for the battery life.

---

### Post by Hmarroqu on 2007-09-20
my toshiba and ubuntu have never gotten along, battery life is less than an hour and i posted asking how to improve on this and no dice.  plus a million other things ubuntu doesnt like my laptop and im starting to not like ubuntu.

---

### Post by dakuran on 2007-09-24
@ the contrary, my batter life has greatly diminished =[ but that won't stop me from using Ubuntu, I love this distro waaaaaaaaaay to much!

---

### Post by maxwells_demon on 2007-09-24
It seems others (including myself), find battery-life a lot shorter in Ubuntu. Consider yourself lucky!

Although I love Linux for my desktops, I find Mac OS X (and unfortunately even windows :( ), to be better suited for laptops. Although *self-proclaimed*  "power-users" will always dismiss problems to n00bishness, I think in the case of linux on laptops, your model wll usually determine how much hassle you'll receive :)

---

### Post by AnimateDeath on 2007-09-25
Toshiba Satellite A135-S4467 here, and I have noticed the same thing in battery life that Ghostboy did. I went from about 1.5 (vista) to about 2.5 (ubuntu 7.04).  Maybe just laptop brand and model, but I am very happy with ubuntu so far. It is my attempt at getting away from windows completely.

---

### Post by fauntumnus on 2007-09-25
i have 3.5~ hours of battery life on compaq nx6325 while using ubuntu (wit standart battery and notebook is 1,5~ years old)
it used to last for 1.45~2.15 hours with windows xp, to conclude, it gives me more work time with ubuntu installed

---

### Post by Hmarroqu on 2007-10-03
anyone knw how i could get a good pwr mangmnt or extend the battery on my toshitba by makin some canges?

---

### Post by gn2 on 2007-10-03
> **Hmarroqu said:**
> anyone knw how i could <> extend the battery on my toshitba by makin some canges?

Is there a long life battery available for your model?
My Portege 3440CT has the option to fit an extended life battery which lasts roughly four hours.

Try reducing your screen brightness and look in the BIOS settings for power saving options.

---

### Post by CWayne on 2007-10-03
Hello, I have a Toshiba A75 S229. My battery life was 1 to 1.5 with XP. Now with Ubuntu it is 2.5 to 3.  Windows always seemed to be running programs (like system idle processes) in the background. It also ran much hotter and used more processor time. I'm very pleased with Ubuntu.
Cliff

---

### Post by hardyn on 2007-10-03
this has been posed a few times... i started a batter life request back at the beginning of gutsy, which didn't seem to get much traction... there are however, a few things that you can do...

enable 'laptop mode' is somewhat convoluted to explain but there are many posts.
BUT... it is defaulted to spin down the hard disk after 5 seconds, which is abusive... change the value to something larger, 240 seconds has been working well for me.

buy more ram (see above)

dont use ndis wrapper and buy hardware with native linux support... that said, ubuntu still does not take advantage of the power management capabilities that are built into the intel and other drivers.

dont use NV or ATI video drivers, they are not very good in my experience, you will get much better battery life and cooler running using the factory drivers.

disable the wireless when not in service (of course this is a no brainer)

even after implementing all of the above, i still loose about 30min to ubuntu over xp.

---

### Post by dinub1 on 2007-10-03
> **AnimateDeath said:**
> Toshiba Satellite A135-S4467 here, and I have noticed the same thing in battery life that Ghostboy did. I went from about 1.5 (vista) to about 2.5 (ubuntu 7.04).  Maybe just laptop brand and model, but I am very happy with ubuntu so far. It is my attempt at getting away from windows completely.

This is what I think...... I agree with previous poster that claimed that RAM usage is a big factor in battery usage time. This is how it works... HDD's are elecro-mechanical devices. They incorporate an electrical motor to spin the platters. That is a big power consumer in a laptop. Probably the HDD and the DVD/CD-RW  drive are the biggest power consumers in a laptop. RAM is a solid state device, uses considerably less power than a HDD and if say an OS can maximize the usage of RAM instead of using a swap file on HDD (for the same purposes), then that OS would be beneficial in regards to battery life. Due to the fact that Ubuntu tries to maximize the usage of RAM, that is loads say 80% of RAM and makes minimal usage of the swap file. This is how, in comparison with Windows XP, it saves baterry life.  Windows XP uses considerably large swap files, therefore HDD to perform various tasks. But I think all this is depedent on each particular laptop hardware.

---

### Post by Z_Cee on 2007-10-06
I've noticed on my Toshiba A75 that battery life dropped drastically and I noticed the heat level was always higher with the past few releases of Ubuntu. This was after testing the versions for a couple of months at a time. 

It got so bad that I had to reinstall XP just to hopefully restore the battery level somewhat. So far I've had a bit of success in recovering the battery life using XP. My A75 was dropping battery life while using Ubuntu from 75 percent to 20 percent in a span of just a few minutes.

---

### Post by GavinZac on 2007-10-06
> **Z_Cee said:**
> My A75 was dropping battery life while using Ubuntu from 75 percent to 20 percent in a span of just a few minutes.

That is obviously not normal and probably a symptom of a serious error.

---

### Post by John64 on 2007-10-23
i have an IBM T40 and it has insanely good power management support for windows.  I love ubuntu, so i am forced to use it in a VM only because the battery under feisty was about half of what i got with XP.  I am going to try out the latest Gutsy and see how i like it, but i have become so accustomed to Outlook 2007 that i might not get used to running VirtualBox/Vmware to get to it.

---

### Post by dinub1 on 2007-10-23
> **John64 said:**
> i have an IBM T40 and it has insanely good power management support for windows.  I love ubuntu, so i am forced to use it in a VM only because the battery under feisty was about half of what i got with XP.  I am going to try out the latest Gutsy and see how i like it, but i have become so accustomed to Outlook 2007 that i might not get used to running VirtualBox/Vmware with it

Well, Outlook 2007 and MS Outlook in general (all versions)  is amazingly good email software. I am using it almost exclusively. I do not know of any Linux email clients that can match MS Outlook.

However I do not see why your laptop battery will have a shorter operational time than under MS Windows. Though I never timed accurately mine, My HP Pavilion ZE4045 laptop has a similar battery life span as under Windows.

---

### Post by Daelyn on 2007-10-23
I have a Sony VAIO SZ4
It has both a Intel GPU as well as nVidia.
2.16GHz Core2Duo and 2 GB memory.


In WinVista (works flawless btw):
2+ hours on nVidia GPU with average usage and small time gaming.
3+ hours on nVidia GPU with machine used lightly.
4 hours on Intel GPU and use the machine lightly
5 hours on Intel GPU with DVD/ethernet/brightness lessened and light usage.

Ubuntu:
1.5-2 hours on nVidia GPU with minimal load (watching a episode of NCIS in VLC).


Dont know why this is, and I am very very disappointed.
Have not switched to the intel GPU yet (have already set up a script to change xorg.conf at boot depending on used GPU, so it is prepared, just havent been bothered)


Saw something about a command I could use to turn off unnecessary commands/devices when on battery power. Although forgot what it was. 

Any advice to make ubuntu suck less power is greatly appreciated

---

