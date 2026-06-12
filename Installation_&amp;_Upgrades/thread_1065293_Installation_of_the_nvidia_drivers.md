---
title: "Installation of the nvidia drivers"
date: 2009-02-09
forum: Installation &amp; Upgrades
---

### Post by Zuajiu on 2009-02-09
Hello,

So before someone sends me to a linked page (I hope you can send me the right one), I have searched on the internet for hours, and alot on this site.

So I have this problem with my laptop.

i have jsut installed ubuntu Intrepid (8.10), really great, lots of nice stuff,
but then i trry to install those damned nvidia drivers.

So I got the problem where it sais :
Fatal server error:
No screens found
giving up.
xinit: Connection refused (errno 111): unable to conenct to X server
xinit: No such process (errno 3): Server error.

So then since I was quite new to linux, i didn't bother very long and jsut reinstalled.
The second time I did exactly the same thing then installed 32 bit, to see i i could get it working with that. 
Well no suck luck,
I've been burning lines of commands into my head, trying and trying to get it working (I guess that's a good thing no?). 
I've tried this link:[http://ubuntuforums.org/showthread.php?t=1054842]("http://ubuntuforums.org/showthread.php?t=1054842")

No deal.
I would guess that it's because I'm running on a Hybrid SLI Nvidia, (9200m GS dedicated, 9400M G motherboard). Whcih came out quite recently.
Do you think i should just give up o installing the driver, I think I tried everything.
Should i jsut reinstall and wait for a new driver to come out?

Thanks for any help or advice that can be given

---

### Post by Ripose on 2009-02-09
Your card is on the supported hardware list.

**GPU:** GeForce 9200M GS **Device PCI ID:** 0x06E8

Have you tried starting in Safe Mode and installing Linux-Restricted-Drivers?
Then in Hardware activate Nvidia 177.

---

### Post by Zuajiu on 2009-02-10
Well the problem is that even in safe mode, the GUI doesn't load,
when i try to launch the x server it just gives the same error as above,
so I tried resetting the xorg.conf file, then I opened it to check what was in it, and there.. well nothing, I mean there is nothing else written but
basic phrase like "Configured Video Devive" or "configured Monitor", is this normal?

---

### Post by Ripose on 2009-02-10
Yes, that's normal for xorg.conf open the the xorg.conf.######### to see what is set, it may shoe a couple of different settings such as **Driver Vesa**
If it does show anything different try entering them into the xorg.conf

I am currently trying to fix a very similar problem, I'll let you know how it goes.

---

### Post by Zuajiu on 2009-02-10
Sorry Ripose, i didn't get the xorg.conf.###### thing you told me, what am i supposed to do? (Still learning how linux works, sorry)

---

### Post by Zuajiu on 2009-02-10
.

---

### Post by jimv on 2009-02-10
I'm assuming you have internet access from the command line, so try this:
```

wget [http://us.download.nvidia.com/XFree86/Linux-x86/180.22/NVIDIA-Linux-x86-180.22-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/180.22/NVIDIA-Linux-x86-180.22-pkg1.run)
sudo sh NVIDIA-Linux-x86-180.22-pkg1.run
```

Follow through the instructions and reboot.

---

### Post by Zuajiu on 2009-02-10
I already tried that, it did actually install the driver, but there was still the no screen error after. So I just reinstalled linux, because it was really taking up to much time, though I would still like to try to install those nvidia drivers without having that bug, so that I can get 3D acceleration and stuff.

---

### Post by deanjm1963 on 2009-02-10
I found the only way to get the nvidia drivers to install correctly was as follows - for intrepid only!

sudo apt-get install nvidia-180 modaliases
sudo apt-get install nvidia-glx-180

after the install

run sudo nvidia-xconfig (TWICE - two times) first time will say there is no screen bla bla bla, but run it again.

by default there is no xorg.conf entries, but if you run it twice the driver will create the entries for xorg.conf

most important - check the horizontal and vertical refresh options for your monitor as they might need to be edited in the newly created xorg.conf

you can edit by sudo gedit /etc/X11/xorg.conf

hope this helps

---

### Post by Ripose on 2009-02-10
There is another copy of **xorg.conf** that will look something like this **xorg.conf.20090209144928** which may have different settings than xorg.conf

They are both in the **/etc/X11** directory, the settings in the numbered .conf *may* show what you need to have in the main xorg.conf

Assuming you can get to the command line.
[B][COLOR=Blue]
nano /etc/X11/xorg.conf[/COLOR][/B]
make the changes you found from the numbered .conf
**[COLOR=Blue][CTRL]O[/COLOR]** to write the changes**[COLOR=Blue] [ENTER][/COLOR]** to save using the same name**[COLOR=Blue] [CTRL]X[/COLOR]** to exit

You may also have to change the /boot/grub/menu.lst

NOTE: **nano** is an easy editor to use, however you may not have it installed, so try **vi** or whatever you choose.

---

### Post by Ripose on 2009-02-10
I highly suggest you read [THIS]("https://help.ubuntu.com/community/NvidiaTroubleshooting") too.

---

### Post by Zuajiu on 2009-02-11
oh ok, well actually in the x11 file I only have one xorg.conf, no other one...
I had one with a numeric ending before the reinstallation, but as i remember they were exactly the same as the original.
I had managed to install the nvidia 180 driver, the xorg.conf file did have information, but i still had the no screen error, that's when i gave up and reinstalled because if it wasn't the xorg file then I had no idea what it could be.

---

### Post by Zuajiu on 2009-02-11
hey deanjm1963, are you sure that is the right package to install?
I try it on the CL, and it sais that it can't find that package.

---

### Post by deanjm1963 on 2009-02-11
> **Zuajiu said:**
> hey deanjm1963, are you sure that is the right package to install?
I try it on the CL, and it sais that it can't find that package.

Yes, those packages are in the repositories - but they're only for intrepid.

I just checked and I made a typo ... I was missing a " - "

again

sudo apt-get install nvidia-180-modaliases
sudo apt-get install nvidia-glx-180

---

### Post by Zuajiu on 2009-02-12
Thanks, I'll try that as soon as I have the time(have to make time for the case where i have to install again...).
Thanks anyways for you help.

---

### Post by Aflack on 2009-02-16
i may try this also, im having the same problem with dual nvidia cards and driver 177.

EDIT: does anyone know for sure if it works?

---

### Post by Zuajiu on 2009-02-21
Well I tried the install once again, with the 180 drivers, didn't work, x server had the same error,
I managed to fix it by booting into restricted mode, and just repairing the xserver through that, which strangely enough hadn't worked after the other tries.
Well anyway, I think I'm going to give up on installing that driver for now, maybe when a new one comes out.

---

### Post by Zuajiu on 2009-02-24
Finally I managed to make it work, thanks to all the help i got.
So to resume everything that one must to make the nvidia drivers work for Linux 8.10 on a Studio XPS 13:

1.Exit the GUI, type: "Ctrl+Alt+F1" 
( to return press Ctrl+Alt+F7)

2. $ sudo killall gdm 
(to stop the GUI)

3. $ sudo apt-get install nvidia-180 modaliases
(this will download the driver from internet, and since I'm not sure how to connect with wifi, use ethernet)

4. $ sudo apt-get install nvidia-glx-180
(this will install the driver, just enter y when it is asked)

5. When the install is finished:
$ sudo nvidia-xconfig
(there will be an error, doesn't matter)
Type in the same command again
(this time it will work)

6. $ sudo reboot
(restarts the computer)

7.At this point it will give the error, 'no screens'
enter your username and password then:

$ sudo nano /etc/X11/xorg.conf
(this will edit the xserver configuration page)

8.Go down to "Section Device"
And add a the very end the line:
BusID   "PCI:03:00:0"
(remember this is for the studio xps 13)

9.Quit the editor with:
Ctrl+X <Enter>
then:
Y <Enter>
then:
<Enter>

10. reboot the computer once more and tadaaa, it works

I spent such a time to make this work, I was very happy when it finally worked, thanks alot for the help from everybody.

P.S If this doesn't work just reboot the computer choose the restricted partition, and just do do "Repair X"

---

