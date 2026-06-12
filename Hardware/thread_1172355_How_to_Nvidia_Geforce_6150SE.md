---
title: "How to Nvidia Geforce 6150SE"
date: 2009-05-28
forum: Hardware
---

### Post by drascus on 2009-05-28
This post specifically addresses a problem that arises with emachines model ET1161-07. It took me forever to fix this and I found very little help online. This may also apply to other Desktops with The Nvidia Geforce 6150SE but I have only tried it on the emachine but it should work. It may also work on other types of Nvidia that cause a problem with x-org.

The Problem: Computer boots but gdm fails to start. you come to a blank screen with no command prompt.

The Solution:

Ctrl+Alt+F2 will bring you to a command prompt. log in and then restart the computer:
```
sudo shutdown -r now
``` 

when the grub loader shows up on restart press Esc key and from the list select recovery mode.

it will boot and give you some recovery options choose the root shell option.

now use this command:
```
sudo dpkg-reconfigure xserver-xorg
```
it will walk you through a few options don't configure the keyboard, but yes to everything else. 

after your finished and get back to the prompt restart the computer with the above command. 

after restart you will be asked if you want to start in low graphics mode. choose the option for this session only. 

then you will come to another screen that said x had some problem just choose yes and then it will start in low graphics mode.

after login go to Administration -> Hardware Drivers
choose the nvidia 180 option after the install restart the computer. 

all your problems should be solved. 

other suggestions:
I also recommend disabling Desktop effects. although they work they cause video and system hangs and jumpy video playback. 

I hope this helps. please post better suggestions or if you found an easier way to address this problem.

---

### Post by rosswmcgee on 2009-11-15
I get to the root  drop to root shell prompt:
I run the sudo dpkg-reconfigure-xorg:
All that happens is I get back to the root@ubuntu:~# 

I have been using ubuntu for years never had such a difficult install/ would you please take a look at my post "cd install fails"

Thanks

---

### Post by andy_blah on 2012-09-18
Sorry for beating up an old thread, but the thread opener might be able to help me. I have the same model of card on an E-Machines PC, and I have absolute no idea what I can do to make LiveCD on the latest Ubuntu work. You can see the main thread that I opened (that didn't get any replies as of lately) here: [http://ubuntuforums.org/showthread.php?t=2056816](http://ubuntuforums.org/showthread.php?t=2056816)

I've tried all the mentioned there. I swiched to Debian, I tried Mint, both reporting that there's no video adapter detected (nouveau, nv and vesa, all failed, imagine that...)

---

### Post by nothingspecial on 2012-09-18
Old thread.

Closed.

---

