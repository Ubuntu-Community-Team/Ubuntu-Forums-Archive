---
title: "S-Video on Ubuntu 9.04 WORKING !!!"
date: 2009-05-05
forum: Hardware
---

### Post by JKoder on 2009-05-05
Hello everyone.
After allot of testing finally i managed to get S-Video work on my Ati Radeon Xpress 1100 (200M ) video card.
I will describe here the steps i did to make it work, and i expect everyone who will try it to give some feedback.
Before we start i must say that i am using the default video driver that Ubuntu provides , so NO proprietary drivers here.


So let's start.

enter the following commands in a terminal:

Make sure your TV is actualy connected before running this
```
xrandr --output S-video --set load_detection 1
```

Setting tv standard to use:
```
xrandr --output S-video --set tv_standard ntsc
```

Do not worry . I live in Europe so normaly the TV Standard should be pal. It working just fine with NTSC

Adding a mode for it (currently it supports only 800x600):

```
xrandr --addmode S-video 800x600
```

I'll go for a clone mode:
```
xrandr --output S-video --same-as VGA-0
```

So far so good. Now let\'s try to see what we have:
```
xrandr --output S-video --mode 800x600
```

So here we are, now we normaly see something on the TV.
On my case the image was full of garbage, but JUST by mistake i switched to a console CTRL+F1 and the Back CTRL+F7.... SURPRISE the TV image was briliant i could see a normal image.

To turn off S-Video just type:
```
xrandr --output S-video --off
```

For ease of use, i put all of this command to a script file and i run it whenever i need S-Video.
Please try it and let me know if this works for you finally.
THANK YOU !

---

### Post by runrun on 2009-05-07
I have an ati x1950pro, and need to add the ATOMTvOut switch in xorg.conf to get my machine to detect the svideo port.

Desperately been trying to get svideo output on 9.04, as it's required for my use and I want to move away from windows XP.

Unfortunately your method did not work for me. My tv doesn't even show a garbled screen when outputting with xrandr, and switching to a console with svideo enabled gives me a pink background rather than a black one.

A little more reading on phoronix tells me that the r5xx chips (in my card) have very unsupported tv out in the oss driver, and it's the reason that the ATOMTvOut option is disabled by default - I had issues in the Preferences>display program after editting xorg, along with others like my lcd monitor using the wrong resolution.

Unfortunately it seems like most of the development is pushing towards getting 2d/3d acceleration working on newer ati cards; good news, just not for me :)

Unfortunately I'll have to carry on using xp till this is fixed. Buying an nvidia card just for tv out on a system that is working 'ok' seems a bit overkill.

---

### Post by ads98765 on 2009-05-13
I followed your guide and on got it to work on my tv and monitor at first on the tv it was just in one quarter of the screen i have solved this problem thou 

one problem is when i log out my svideo connection loses and i have to set it up again. How do i save the settings so when i reboot they are still there and whats is this script you mention would you be able to program ubuntu to boot this script at start up? thanks alot for this guide!!

---

### Post by Pharmacore on 2009-05-15
thanks! worked a treat. however, i am curious how to make the output PAL and another desktop rather than mirrored.

---

### Post by landman 1560 on 2009-06-13
Upon running:

```
xrandr --output S-video --set load_detection 1
```

I get the following error:

```
X Error of failed request:  164
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  15 ()
  Serial number of failed request:  24
  Current serial number in output stream:  24

```

Any idea what this means?

---

### Post by Altay_H on 2009-06-14
I also have an ATI Radeon Xpress 200M graphics card, but your method did not work for me. First I plugged the s-video cable into my computer and television, then I ran each line of code you provided in the order you wrote them.
```
$ xrandr --output S-video --set load_detection 1
$ xrandr --output S-video --set tv_standard ntsc
$ xrandr --addmode S-video 800x600
$ xrandr --output S-video --same-as VGA-0
$ xrandr --output S-video --mode 800x600
```
After I entered the last command, the television screen began to show random descending diagonal gray lines. Everything seemed to be going correctly so far.

Next I pressed Ctrl+Alt+F1 to switch to the first virtual terminal. Once it switched, the television screen turned black. I pressed Ctrl+Alt+F7 to switch back, but the television screen just went back to the fuzzy descending gray lines screen. I can't get the television screen to work by switching in and out of Virtual Terminals.

I'd appreciate it if you can help me to get it to work, especially because we seem to have the same graphics card. Thanks for your useful post!

---

### Post by Jeenyus on 2009-06-14
> **Altay_H said:**
> I also have an ATI Radeon Xpress 200M graphics card, but your method did not work for me. First I plugged the s-video cable into my computer and television, then I ran each line of code you provided in the order you wrote them.
```
$ xrandr --output S-video --set load_detection 1
$ xrandr --output S-video --set tv_standard ntsc
$ xrandr --addmode S-video 800x600
$ xrandr --output S-video --same-as VGA-0
$ xrandr --output S-video --mode 800x600
```
After I entered the last command, the television screen began to show random descending diagonal gray lines. Everything seemed to be going correctly so far.

Next I pressed Ctrl+Alt+F1 to switch to the first virtual terminal. Once it switched, the television screen turned black. I pressed Ctrl+Alt+F7 to switch back, but the television screen just went back to the fuzzy descending gray lines screen. I can't get the television screen to work by switching in and out of Virtual Terminals.

I'd appreciate it if you can help me to get it to work, especially because we seem to have the same graphics card. Thanks for your useful post!

I am having the same issue, random grayish lines flying everywhere.

Thanks,
Jeenyus

---

### Post by Altay_H on 2009-06-15
Well, I just gave it another try after my friend suggested I try plugging the television in before I boot up and it worked. This time there were no gray lines, but there were black and white static-like patches that occurred in some white places, but not others. Anyway, the quality wasn't perfect, but the colors were vivid.

I figured maybe you suggested the Ctrl+Alt+F1 trick to fix the static patches, but that didn't work.

---

### Post by gabbar_singh on 2009-06-17
I have the same problem as Landman1560 
```
$ xrandr --output S-video --set load_detection 1
X Error of failed request:  164
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  15 ()
  Serial number of failed request:  24
  Current serial number in output stream:  24

```

Any idea whats going on and how to solve the problem.

---

### Post by bakie on 2009-06-19
> **gabbar_singh said:**
> I have the same problem as Landman1560 
```
$ xrandr --output S-video --set load_detection 1
X Error of failed request:  164
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  15 ()
  Serial number of failed request:  24
  Current serial number in output stream:  24

```

Any idea whats going on and how to solve the problem.

are you trying to do that command over an ssh connection ?
I got the error when doing that over ssh, but then I used remote desktop viewer to see the desktop and it worked :)

---

### Post by landman 1560 on 2009-07-01
No.  There was no ssh.  That was with a tv hooked up with s-video.

Any other ideas?  This is a really important option.

---

### Post by morrie on 2009-07-11
I got it work (sort of) just by copying and pasting the code the second time (I had the same  problem as Landman the first time).  Maybe evoking xrandr on it's own, then with params?(a guess).  I have also seen other posting that the scripts don't work the first time, maybe it's the same here-you just need to try a couple times?

plays U-tube, but not AVI, why not?  The AVI on the TV just shows the player window with a black spot where the video should be.

BTW, I have Radeon 7500

---

### Post by wcasper4 on 2009-07-12
I hooked my tv up via my s-video output as well, but upon changing the resolution to fit my tv, when I go back to the 1024x768, the screen does not fill my laptop screen... any suggestions?

---

### Post by marawuti on 2009-07-25
ads98765 could you edit your post to educate the rest of us how you resolved the 1/4 screen problem?
Thx

---

### Post by theregoesmyeye on 2009-08-19
> **landman 1560 said:**
> Upon running:

```
xrandr --output S-video --set load_detection 1
```I get the following error:

```
X Error of failed request:  164
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  15 ()
  Serial number of failed request:  24
  Current serial number in output stream:  24

```Any idea what this means?

I had that problem until I added this to the device section of my xorg.conf:
    Option "ATOMTvOut" "True"

Everytime I use this, my monitor has lines running through the screen, making text barely readable and very fuzzy. Tele still doesn't work, also.

---

### Post by doogiekd on 2009-08-25
Friend, 

Thank you for taking the time to solve this problem and post the result. 

I followed the instructions and it worked - I can get video on my television now. My home entertainment system is back!

Now if there could only be a solution to this problem that it can run every time at startup, without having to enter the commands every time.

Thanks again,

doogiekd

---

### Post by Altay_H on 2009-08-25
> **doogiekd said:**
> Now if there could only be a solution to this problem that it can run every time at startup, without having to enter the commands every time.
Save the commands as a shell script and set it to run at startup by going to System > Preferences > Startup Applications > Add. That should work.

---

### Post by doogiekd on 2009-08-26
I would give a try, except I have never saved commnads as a shell script before. Can you explain how to do that?

Thanks.

---

### Post by Altay_H on 2009-08-26
I'd be glad to help you out. Start by opening a text editor like Gedit or Kate, then paste the following text into it.

```

#!/bin/sh

xrandr --output S-video --set load_detection 1
xrandr --output S-video --set tv_standard ntsc
xrandr --addmode S-video 800x600
xrandr --output S-video --same-as VGA-0
xrandr --output S-video --mode 800x600

```

Save the file with the extension sh (for example screen_script.sh) and remember where you saved it. Then go to System > Preferences > Startup Applications > Add and select your script. Now it should run every time your computer boots up.

---

### Post by doogiekd on 2009-08-27
Thanks Altay_H, 

This worked perfectly.

---

### Post by SBenvie on 2009-09-03
> **landman 1560 said:**
> Upon running:

```
xrandr --output S-video --set load_detection 1
```I get the following error:

```
X Error of failed request:  164
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  15 ()
  Serial number of failed request:  24
  Current serial number in output stream:  24

```Any idea what this means?

i am having this same problem, it is a recent thing, i am very new to linux/ubuntu. i know the s-video cable is good, have used it alot, i have also had ubuntu displaying on my tv perfectly. i do not know what has changed, i have been reading post for about 2 hours and nothing i have read has helped me solve my problem. the only thing i can think of that is diffeent is that i was reading about intel graphic cards having issues with ubuntu 9.04, and i followed the directions on how to roll back the driver to the previous ubuntu version and that was supposed to fix alot of the issues, wich it didnt. please help.

---

### Post by rafeUbuntx on 2009-09-08
awesome man!!!! :)
I have almost 2 weeks trynig to use the super video in my ubuntu 9.04 and now I got it!!
I'm using ati mobility radeon 9000 igp 

great work!!

---

### Post by eaterjolly on 2009-09-12
> **landman 1560 said:**
> Upon running:

```
xrandr --output S-video --set load_detection 1
```I get the following error:

```
X Error of failed request:  164
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  15 ()
  Serial number of failed request:  24
  Current serial number in output stream:  24

```Any idea what this means?
i got the same thing

---

### Post by eaterjolly on 2009-09-14
i have a Intel GMA X3100 Dynamic Video Memory Technology 4.0 graphics chip

---

### Post by hubertofliege on 2009-09-20
A lot of people mentioned that they followed the instructions, but when they hit ctrl+f1 it did nothing.  After I followed the instructions, I tried hitting a button on my laptop, CRT/LCD, which I've used whenever I plug it into a projector.  It tells the computer to display the screen on another monitor.  That worked.  Try looking for this key on your own computers.  On my Dell, it is an alternate function of the F8 key.  I hold the little blue [COLOR=Navy]Fn [COLOR=Black]and then F8, which is labeled "[COLOR=Navy]CRT/LCD[COLOR=Black]"

I am not sure how to change the resolution, though.  When S-video is working, my computer must display the same resolution on my monitor and on the TV, and it only allows the TV to be displayed at 800x600, which is not right for my monitor.  

Does anyone know how to display S-video output in a different resolution (mine is 1024x768 )
[/COLOR][/COLOR][/COLOR][/COLOR]

---

### Post by hubertofliege on 2009-09-27
I was going through all the threads on this topic which I had posted questions/solutions on and I am beginning to suspect I might be a serial thread killer.

Still don't know what to do about resolution.

---

### Post by Rohan Kapoor on 2009-10-10
All I'm getting is the garbage. Even after switching with Crtl f1 and ctrl f7. Any ideas?

---

### Post by kerzane on 2010-09-27
Hello folks,

I've read a lot of threads and articles about this issue, and this seems to be a good point from where to ask for help.

Following the initially posted commands, I get (after a screen flash) an error (in one of those pop-up notifications in the top-right corner of the screen) 

Could not switch the monitor configuration
requested position/size for CRTC 65 is outside the allowed limit:
position=(1440,0), size=(800,600), maximum=(1440,1440)

Specifying the position with the --pos option to xrandr does not solve the problem.




Can anyone suggest where I should go from here?

```

eoin@eoins-laptop:~$ lspci -nn | grep VGA
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE) [1002:5955]

```

Many thanks, would really appreciate some help with this.

---

