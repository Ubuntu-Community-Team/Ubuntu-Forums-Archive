---
title: "Black Screen After Logout in Intrepid?"
date: 2008-10-31
forum: General Help
---

### Post by nilpill on 2008-10-31
Whenever I attempt to log off of my computer or restart the X server since upgrading to 8.10, instead of being taken back to the login screen, the screen simply turns black, and I'm unable to do anything but to turn my computer off and back on to log back on. I honestly have no clue what would be causing this.

I'm using a Lenovo Thinkpad R61 with an NVidia Quadro NVS 140M video card, if that info helps.

---

### Post by GodsRockstar on 2008-10-31
I am experiencing the same problem (black screen that restarts X server several times and eventually reverts to the failsafe X login) after logout. 
I have a an Thinkpad T61p laptop with the Nvidia Quadro FX 570M GPU.
I am using the 177 Nvidia Driver Version that was configured and recommended via "Restricted Drivers" menu.  

However, there is a work around is to downgrade to the 173 Nvidia Driver Version via "Restricted Drivers" menu.  After downgrading I am able to logout multiples time without ant problems.

I would really like to use the latest Nvidia driver (177) with my newly upgraded Intrepid Ibex laptop, so if anyone knows how to overcome the "black screen" error on logout...Please provide any suggestion.

Thanks,
GodsRockstar

---

### Post by GodsRockstar on 2008-10-31
> **GodsRockstar said:**
> I am experiencing the same problem (black screen that restarts X server several times and eventually reverts to the failsafe X login) after logout. 
I have a an Thinkpad T61p laptop with the Nvidia Quadro FX 570M GPU.
I am using the 177 Nvidia Driver Version that was configured and recommended via "Restricted Drivers" menu.  

However, there is a work around is to downgrade to the 173 Nvidia Driver Version via "Restricted Drivers" menu.  After downgrading I am able to logout multiples time without ant problems.

I would really like to use the latest Nvidia driver (177) with my newly upgraded Intrepid Ibex laptop, so if anyone knows how to overcome the "black screen" error on logout...Please provide any suggestion.

Thanks,
GodsRockstar

I have found and confirmed this bug in Launchpad --> [Latest NVIDIA drivers: X hangs with blank screen after logout]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/258357")

---

### Post by sdowney717 on 2008-10-31
happens with fglrx ATI cards also.

It will even be black and never come back if the monitor goes to sleep.
The good thing about bugs like this which are pervasive is they are likely to be fixed soon. I did not have this problem with IBEX before the final release.

---

### Post by Matoridi on 2008-10-31
I have a similar problem when trying to log out, except the screen is kind of orangy...  I have an Intel GMA 3100 based video card.

---

### Post by forger on 2008-10-31
If you think it's nvidia's fault, nvidia-glx debian packages contain a command for bug reporting:
```
sudo nvidia-bug-report.sh
```
Read the instructions.

To everyone: Create a new user and try the log out / black screen thing. Does it still happen to the new user?

If it still happens, perhaps you need to reconfigure your xserver:
**[COLOR="Red"]WARNING! You might get stuck with console! Backup first!![/COLOR]**
Backup
```
cp /etc/X11/xorg.conf $HOME/xorg.conf
```
Reconfigure xorg.conf:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Reboot your computer:
```
sudo reboot
```

Once you're back, if your screen doesn't work, restore the backed up file:
```
sudo cp $HOME/xorg.conf /etc/X11/xorg.conf
```
(Don't continue if your screen doesn't work, just reboot and try something else.)

Login, install and configure your xorg.conf with nvidia-settings
```
sudo apt-get install nvidia-settings
gksu nvidia-settings
```
"X Server Display Configuration" > Click "Detect displays", choose your resolution, click "Save to X configuration file" and click Quit :)

---

### Post by eamonireland on 2008-11-11
Has anyone had success with forger's solution? It looks complicated, so I want to check it works first!

---

### Post by Matoridi on 2008-11-13
You can try his solution if you want, but basically, it just puts the xserver configuration file (xorg.conf) back to default settings... Or if you install nvidia-settings and try configuring the xserver file with it, you might get better results.  But this latter solution can only be used if your computer has an NVidia graphic card.


IMHO, I don't think that this problem is caused by the xorg configuration file, but as I got back to Hardy (which runs pretty fine), I never searched for a solution to this problem.

Good luck!

---

### Post by feeshy on 2008-11-28
Thinkpad T61, Nvidia NVS 140M, 177 Drivers

Same problem - guess we wait for an official fix.....

After Hardy was so good to me I think I'll try stick with LTS releases from now on....

---

