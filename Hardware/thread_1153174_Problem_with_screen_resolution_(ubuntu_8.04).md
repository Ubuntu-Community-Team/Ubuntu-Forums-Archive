---
title: "Problem with screen resolution (ubuntu 8.04)"
date: 2009-05-08
forum: Hardware
---

### Post by kokeroulis on 2009-05-08
Hello


Today i have installed in my pc the ubuntu 8.04 32bit.The problem is that the resolution has stuck in the 600x800.This is the maximum screen resolution.Here is the hardware which my pc has

CPU : Intel Pentium D 3.4 GHz and 1 GB ram
Graphic Card : Nvidia Geforce 7300cs
Hard disk : samsung 150 GB
Screen : Nec (i don't know which model is)

I hope this information is enough.If there isn't then let me know.

---

### Post by DJYoshaBYD on 2009-05-08
you need to get the newest Nvidia drivers... you should be able to go to system->preferences-> hardware drivers and install it like that...

OR

you can go to [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) and download EnvyNG.. It will automatically download and install your drivers for your video card

OR

you can go to the actual Nvidia site, and download the newest one from them for your card.. BUT, you have to stop GDM (or kde or xfce, depending on your flavor of ubuntu), THEN run the install program like so

open a terminal and navigate to the folder where your nvidia driver was downloaded to.. I use the desktop for this example
```

cd ~/Desktop
sudo ./Nvidia blah blah blah

```

the "./" in front of the file name will make the program run.. you need to have other things installed, like kernel headers, if you need the program to compile the kernel module for you without going online.. it also offers, during the installation, to download the appropriate kernel module.. 
 
that is the hardest way.. I actually recommend usng EnvgNG out of all of them, because it VERY VERY easy to use.. point and click, wait, reboot.. thats it.. I use the last method mentioned, cause im a nerd.. haha

after you install the nvidia drivers and reboot, then you can do 2 different things to change your resolution settings..

go to a terminal
```
sudo nvidia-settings
```

or

there should be a "Nvidia Display Settings" selection available in the system->preferences menu..

good luck.. use EnvyNG, and you wont need luck though.. lol.. just an internet connection..

---

### Post by DJYoshaBYD on 2009-05-08
oh yeah.. dont really type blah blah blah in the command.. lol.. type the real name of the file.. haha

---

### Post by kokeroulis on 2009-05-09
ok.Thanks you.It works.

---

