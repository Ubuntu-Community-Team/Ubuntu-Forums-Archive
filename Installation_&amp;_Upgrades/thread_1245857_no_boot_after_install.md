---
title: "no boot after install"
date: 2009-08-21
forum: Installation &amp; Upgrades
---

### Post by timayyy on 2009-08-21
i am a newbie when it comes to ubuntu. I did an install on an older HP pavillion desktop with a geforce fx5200 graphics card. after searching forums on installing I finally got it to install using the "text only" installer. now the system boots to the loading screen, but when the bar reaches 100 percent the screen goes black and nothing happens. I'm thinking its a driver issue, but without getting into the system i don't know what to do. can anybody help walk me through this. remember im a noob so be specific please!

---

### Post by Moop on 2009-08-21
You shouldn't need a driver for things to work. How much memory does your pc have?

Maybe you should try Xubuntu which uses less resources.

---

### Post by timayyy on 2009-08-21
I have 512 meg memory. I see in other posts about fx5200 video card issues, but from what i see, they resolved the issue from the control panel and updating drivers. My question is, if i cant load the system to access the control panel how do i get an updated driver to install and hopefully fix this issue......

---

### Post by timayyy on 2009-08-22
bump

---

### Post by stlsaint on 2009-08-22
say again why you arent installing thru by booting to cd and installing from there?

---

### Post by timayyy on 2009-08-22
I got the system installed correctly, my problem is it hangs up after  the splash screen, sometimes it will go as far as the first graphics screen with sound then the monitor goes black and wont go any farther. I'm begining to think my grapghics card is on its way out....

---

### Post by timayyy on 2009-08-22
99% of the time a message appears on the monitor "oversize recomand mode 1280X1024" then goes black. i installed new invidia drivers (173 and 180) but nothing changed. ran memtest for an hour and all is fine there.

---

### Post by presence1960 on 2009-08-22
> **timayyy said:**
> i am a newbie when it comes to ubuntu. I did an install on an older HP pavillion desktop with a geforce fx5200 graphics card. after searching forums on installing I finally got it to install using the "text only" installer. now the system boots to the loading screen, but when the bar reaches 100 percent the screen goes black and nothing happens. I'm thinking its a driver issue, but without getting into the system i don't know what to do. can anybody help walk me through this. remember im a noob so be specific please!

Boot into recovery mode and choose xfix. When that completes select Resume normal boot. Hopefully you will boot into Ubuntu. if not boot again and go back into recovery mode. This time choose command prompt with networking. I believe you will have to login to get the root prompt. Then run these two commands ```
sudo apt-get install envyng-core
```
when complete run ```
sudo apt-get install envyng-qt
```
Now run ```
envyng -t
```
and follow the prompts to install Nvidia driver. Hopefully one of these two will get it fixed for you.

P.S. you may not need sudo before those commands, but use it unless you get an error. Then drop sudo from the command. I haven't had to do this for a while!

---

### Post by timayyy on 2009-08-22
i installed envyng-core and envyng-qt followed prompts, reboot, no change. monitor still blacks out.
 
i also ran this:
 
sudo lshw -c video
 
in the list that came up i found one line that doesn't seem right.
 
BUS INFO: [EMAIL="PCI@0000:01:00.0"]PCI@0000:01:00.0[/EMAIL]
 
now, my card is AGP not PCI, could this be my problem.....:-?

---

### Post by timayyy on 2009-08-23
bump

---

### Post by AmerNewbieInDE on 2009-08-23
sound like a problem i had with windows, found out the drivers set the resolution higher then the screen could handle and at the end of boot, it went black. I dont know how to change the resulution from recovery mode, i did find this, [http://ubuntuforums.org/showthread.php?t=71673](http://ubuntuforums.org/showthread.php?t=71673) 

maybe someone else will be able to tell you.

---

### Post by timayyy on 2009-08-23
thanks for the link. it helped. I'm actually posting this from ubuntu(my other pc is vista equipped) i was finally able to load the desktop for the first time, but only in low resolution mode. I tried to make changes to display settings but after reboot it goes back to my original problem. then I have to reconfigure xserver again to get back into desktop(but only in low res. mode) a message does appear that says "another xserver is running on display:0" it asks to switch to another server. click yes and it will boot to desktop. I'm not sure why this is. thinking of going to an older version of ubuntu to get around dealing with this.

---

### Post by timayyy on 2009-08-24
ok. so it seems that there was a conflict with the drivers. just to make sure the correct driver was installed, i went into "envyng". Now to make certain something didn't install by accident i chose the uninstall ati driver option. then restart xorg. reboot. FINALLY!!!!!! ubuntu loaded all the way to the desktop with no hangs or errors. so for now problem solved. thanks to all who helped!

---

