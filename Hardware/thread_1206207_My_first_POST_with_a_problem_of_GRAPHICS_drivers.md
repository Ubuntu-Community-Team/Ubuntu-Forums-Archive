---
title: "My first POST with a problem of GRAPHICS drivers"
date: 2009-07-06
forum: Hardware
---

### Post by shail00 on 2009-07-06
Hello friends.
Am a new to linux ,after so many years of using the crap {windows},i want to shift to linux ..
i ordered the free cd and installed it quite easily...
i have updated my ubuntu 9.04
i use via k8m800 chipset 
and my display adapter is via/s3g unichrome pro igp..
my prblem is that after updating ,i am not able to see my moniter screen's correct resolution i.e 1024 768
Someone told me that the display drivers are missing ...
Can u plz help me?
my screen runs in only 832*624 mode and its pretty annoying...
PLZ HELP ME SOON

---

### Post by zepita on 2009-07-06
Go to software sources under administration and make sure all is checked except for "source code"
Then you may be asked for updating, click yes.

After that go to administration>update manager.

Update all and try restarting the X server or just restarting the computer and then trying to change the resolution.

If that does not work, you may have run this command to edit your X server settings

sudo gedit /etc/X11/xorg.conf

just replace whatever you have under "modes" for 1024x768

Then save and close and restart the X server or the computer.

I hope it helps. I'm not an experienced user but I found out that google provides good guides, but you have to be careful and maybe wait for a reply from someone else.

---

### Post by wojox on 2009-07-06
Sounds like good advice 
Just make a back-up copy of xorg.conf in case.

---

### Post by tommcd on 2009-07-07
You can also try booting to recovery mode and choose the option: **xfix fix video** and then reboot and see if you can get the proper resolution.
If that does not work, then try using **xrandr** as discussed in this tutorial:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

@ Shail00,
And welcome to the Ubuntu forums!

---

### Post by shail00 on 2009-07-07
doesnt solve my problem
everytime i edit xorg.conf file after restart ,the editing done by me is gone and default state is there?
wt to do?

---

### Post by dpenndorf on 2009-11-12
I had this problem for months, tried many different solutions, none worked.  Finally resolved!

Just added to xorg.conf:

Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       30-70
        VertRefresh     50-150
EndSection

---

### Post by tommcd on 2009-11-12
> **shail00 said:**
> doesnt solve my problem
everytime i edit xorg.conf file after restart ,the editing done by me is gone and default state is there?
wt to do?
Be sure to use sudo to edit system files. If you are using gedit to edit xorg.conf, you can lauch it with gksudo like this:
```
gksudo gedit /etc/X11/xorg.conf
```
Gksudo is sometimes recommended for launching graphical editors and programs like gedit, as opposed to terminal based editors like nano.
Be sure to backup your xorg.conf first for safety:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

---

### Post by huba on 2010-04-26
> **dpenndorf said:**
> I had this problem for months, tried many different solutions, none worked.  Finally resolved!

Just added to xorg.conf:

Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       30-70
        VertRefresh     50-150
EndSection

Thanks for this solutin dpenndorf!!
It workes for me too!

I also added:
```

Subsection "Display"
   Modes "1024x768"
EndSubsection

```
to Section "Screen",
but that probably wasn't essential.

---

### Post by Philip dT on 2010-07-05
Hallo. I am new here.
 
I have successfully downloaded and installed the latest ubuntu, and I am trying to get 1024X768 screen resolution.
 
I am trying to edit my xorg.conf file.
 
When I open a terminal window, and put in:
 
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
 
It says that it does not see such a file.  Do I need to change the directory?  If so, how do I do it.
 
Also, if I put in this in the terminal window:
gksudo gedit /etc/X11/xorg.conf 
then the file is blank, and if I want to save, it says that such a file does not exit.
 
What am I doing wrong?
 
(Remember I am completely new to ubuntu)

---

