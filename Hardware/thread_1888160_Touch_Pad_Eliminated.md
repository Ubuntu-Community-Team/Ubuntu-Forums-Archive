---
title: "Touch Pad Eliminated"
date: 2011-11-28
forum: Hardware
---

### Post by insession on 2011-11-28
The right-click on my touchpad wasn't working when I installed ubuntu 11.10 (common problem) and this is what I did:

> **Sabot said:**
> To get the trackpad working correctly you need to use the terminal and enter in the below commands. Make sure you press enter after each command:

    ```
sudo su
```

    ```
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
```

    ```
reboot
```


Once the computer reboots your trackpad will be able to do left click and drag and right clicking.

But these commands made it so my touchpad is detected AS the mouse...so my right click works but now I can't change any settings on the touchpad, because there isn't the option to. How do I get my touchpad back? I searched the forums but couldn't find a similar issue. Thanks for your help.

---

### Post by BC59 on 2011-11-28
If your touchpad is Synaptics you can install gsynaptics

```
sudo apt-get install gsynaptics
```

---

### Post by insession on 2011-11-28
Seems like that gave me two errors (bolded):


Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gpointing-device-settings libgpds0
The following NEW packages will be installed:
  gpointing-device-settings gsynaptics libgpds0
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 85.7 kB of archives.
After this operation, 758 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/universe libgpds0 amd64 1.5.1-5ubuntu1 [19.6 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/universe gpointing-device-settings amd64 1.5.1-5ubuntu1 [63.4 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/universe gsynaptics amd64 1.5.1-5ubuntu1 [2,750 B]
Fetched 85.7 kB in 1s (70.4 kB/s)  
Selecting previously deselected package libgpds0.
(Reading database ... 154841 files and directories currently installed.)
Unpacking libgpds0 (from .../libgpds0_1.5.1-5ubuntu1_amd64.deb) ...
Selecting previously deselected package gpointing-device-settings.
Unpacking gpointing-device-settings (from .../gpointing-device-settings_1.5.1-5ubuntu1_amd64.deb) ...
Selecting previously deselected package gsynaptics.
Unpacking gsynaptics (from .../gsynaptics_1.5.1-5ubuntu1_amd64.deb) ...
Processing triggers for gconf2 ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up synaptics-dkms (1.0.0) ...
Loading new synaptics-1.0.0 DKMS files...
[B]Error! /usr/src/synaptics-1.0.0.dkms.tar.gz does not exist.
dpkg: error processing synaptics-dkms (--configure):
 subprocess installed post-installation script returned error exit status 2[/B]
Setting up libgpds0 (1.5.1-5ubuntu1) ...
Setting up gpointing-device-settings (1.5.1-5ubuntu1) ...
Setting up gsynaptics (1.5.1-5ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
[B]Errors were encountered while processing:
 synaptics-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]



Suggestions?

---

### Post by BC59 on 2011-11-28
Run 

```
sudo dpkg --configure -a
sudo apt-get -f install
```

---

### Post by BC59 on 2011-11-28
You can install the same app from the Ubuntu Software Center searching for gsynaptics. It appears another app for Pointing devices which you could use it as well.

---

### Post by insession on 2011-11-28
I ran ```
sudo dpkg --configure -a
``` and got this:

Setting up synaptics-dkms (1.0.0) ...
Loading new synaptics-1.0.0 DKMS files...
[B]Error! /usr/src/synaptics-1.0.0.dkms.tar.gz does not exist.
dpkg: error processing synaptics-dkms (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 synaptics-dkms[/B]

---

### Post by insession on 2011-11-28
I'll try the Software Center right now

---

### Post by insession on 2011-11-28
that didn't work either, it was already installed so I tried removing it to re-install it and there was an error.

---

### Post by BC59 on 2011-11-28
Before everything you have to delete the package which is causing the problem. Try:

```
sudo apt-get purge synaptics-dkms
```

---

### Post by insession on 2011-11-28
no luck....:(

Usually under System Settings > Mouse and Touchpad there's a tab for Mouse and another tab for Touchpad. It seems what I did eliminated the Touchpad tab completely. Does that help any?

---

### Post by insession on 2011-11-28
...in diagnosing the problem

---

### Post by BC59 on 2011-11-28
Just try now to install the 2 apps from Software Center.

---

### Post by insession on 2011-11-28
Still no cigar...

(by 2 apps you mean synaptiks and Pointing Devices right?)

---

### Post by BC59 on 2011-11-28
Yes these are the apps concerning touchpad.

You could try from Synaptic if you have it installed to find the broken package and eliminate it.

In any case try again

```
sudo dpkg --configure -a
``` and

```
sudo apt-get purge synaptics-dkms
```

---

### Post by insession on 2011-11-28
> You could try from Synaptic if you have it installed to find the broken package and eliminate it.

How would I find the broken package? Sorry I'm a complete beginner at this.


Retried and got this:
E: Unable to locate package synaptics-dkms

I have both apps installed...

---

### Post by BC59 on 2011-11-28
Well go to the dash, on the upper part of the launcher bar and on the search box write gsynaptic. The 2 apps should be there. Execute them to tweak your touchpad.

---

### Post by insession on 2011-11-28
Looks like the two apps don't show up when I write 'gsynaptic' in the dash. I installed synaptiks and Pointing Devices.

---

### Post by insession on 2011-11-28
do you mean go to 'Mouse and Touchpad'? I still don't have the option for tweaking the touchpad unfortunately, the tab still isn't there.

---

### Post by BC59 on 2011-11-29
Open Pointing devices and manipulate the settings to change the configuration of the buttons.

---

### Post by insession on 2011-11-29
I have Pointing Devices installed (according to the Software Center), but it doesn't show up when I type it in the dash.

I should be able to configure touchpad settings from System Settings > Mouse and Touchpad too right? But I can't.

---

### Post by BC59 on 2011-11-29
If the app Synaptic is working, open it then put your password and from the panel left down choose **Custom filters** From there to the top left you see **Broken**. Choose it and if it appear broken packages click to fix them.

---

### Post by insession on 2011-11-29
Doesn't look like anything's broken.

Is there a way to reverse directly the commands I put in the first post?



**EDIT: Here's how, for those who run into the same problem:**
```
sudo rm /etc/modprobe.d/psmouse.modprobe
```

Pretty simple really -_-


And thanks for your help BC59!

---

