---
title: "Fail to link to fglrx-libglx.so?"
date: 2012-02-03
forum: Hardware
---

### Post by jonnyboysmithy on 2012-02-03
I have installed fglrx driver and I'd like to be able to use desktop effects.
Also I cant open the catalyst control center.
When from a terminal I try to switch to integrated gpu to safe power I get: ```
jotham@Jotham-Laptop:~$ sudo aticonfig --px-igpu
[sudo] password for jotham:
No layout section was found in the file: '/etc/X11/xorg.conf'.
Please run 'aticonfig --initial' first or modify your configuration file manually and run aticonfig again.
aticonfig: parsing the command-line failed.
jotham@Jotham-Laptop:~$
```And when I run ```
jotham@Jotham-Laptop:~$ sudo aticonfig --initial
Uninitialised file found, configuring.
Fail to link to fglrx-libglx.so, please check whether driver is installed correctly
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.original-1
jotham@Jotham-Laptop:~$ 
```Some of the documentation tells me to fix the fglrx-libglx.so issue I have to: 
```
sudo apt-get install --reinstall xserver-xorg-core
```Which just makes the xserver not start properly, and then have to got to tty1 and re-enavble the driver using jockey-text.I'd be okay with not having any effects but I'd like to be able to switch to the eco graphics mode. I'm using 11.04 64bit ati hd 6700m series (6740m specifically I think?)

---

### Post by jonnyboysmithy on 2012-02-03
Screenshots:

---

### Post by jonnyboysmithy on 2012-02-04
So how can I re-enable desktop effects?

---

### Post by jonnyboysmithy on 2012-02-09
Solved!!:popcorn::guitar:

What I had to do was get the installer to compile for my system in particular where as before I had tried the stock configuration but it wouldn't work, compiling didn't work because I didn't  have all the build dependencies :biggrin:(it never told me but I later figured it out). Link to driver: [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)
Btw after installation you have to reboot (of course) and run: ```
sudo aticonfig --initial
```Hopefully someone else will find this useful..

---

### Post by jonnyboysmithy on 2012-02-09
I thought I had it. I'm back to square one. I think this is a bug. Any opinions?

---

### Post by DAB4970 on 2012-02-18
I also get that output from doing #aticonfig --initial -f

Using Radeon HD 5450 on Ubuntu 11.04

there is an "LN" cmd (creating links) that I found in my reference book, but I'm not sure exactly how to utilize it.

---

### Post by DAB4970 on 2012-02-20
I quit using the proprietary driver and went with the open sourced xserver-xorg-video-radeon pkg.  Meaning, I used "radeon" in the xorg.conf file on the drivers line.  It uses all the space on the monitor.  That was my main issue with the proprietary driver.

I tried the xserver-xorg-video-ati pkg ("ati" in the xorg.conf file) but that seemed to make the screen go blank after just a few minutes of use.  Not sure what is really was doing other than that.

Hope this help someone.

---

### Post by mastablasta on 2012-02-20
have a look here at the bottom:
[http://ubuntuforums.org/showthread.php?t=1927317](http://ubuntuforums.org/showthread.php?t=1927317)

---

