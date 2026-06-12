---
title: "Monitor detected as &quot;Unknown display&quot; or &quot;Built-in display&quot;"
date: 2015-05-26
forum: Hardware
---

### Post by matt. on 2015-05-26
Hi all, I'm not an advanced linux user so bear with me, and thanks for your help in advance!

I have a Samsung 943-BWX monitor and can't change the resolution or any other details because Ubuntu does not recognize it.
I have a NVidia Geforce GTX 570HD video card using the proprietary driver 346.59 and have tried to fix the problem by using the default driver as well, but nothing changes.





When I boot into the default Ubuntu display manager, this is what I get (1)






When I log in with the  Gnome classic display manager, this is what I get (2)







And when I log in with the Gnome Flashback(compiz and metacity) display managers, this is what I get (3)




I get different results but none of them recognize the monitor. And if I use the additional drivers program, then it shows no options for a monitor, only for my video card and processor. Samsung's official website has no drivers for linux for this model either :(


This is my output when running lspci with no arguments:

```
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1a.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
01:00.0 VGA compatible controller: NVIDIA Corporation GF110 [GeForce GTX 570 Rev. 2] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF110 High Definition Audio Controller (rev a1)
02:00.0 Ethernet controller: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101/6102 single-port PATA133 interface (rev b2)
05:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

```



Thanks for your help! Let me know if you need any additional information.

---

### Post by Vladlenin5000 on 2015-05-26
Are you using VGA (D-sub)?

---

### Post by matt. on 2015-05-26
> **Vladlenin5000 said:**
> Are you using VGA (D-sub)?

Nope, I'm using DVI.

---

### Post by papibe on 2015-05-26
Hi matt.

When using the Nvidia proprietary driver, don't use 'Displays', use 'Nvidia X Server Settings' instead.

Does the latter recognize correctly the display?

Regards.

---

### Post by matt. on 2015-05-26
> **papibe said:**
> Hi matt.

When using the Nvidia proprietary driver, don't use 'Displays', use 'Nvidia X Server Settings' instead.

Does the latter recognize correctly the display?

Regards.


Maybe I'm not seeing something that I should, but when I open the Nvidia X Server Settings, I don't see anything that could help out.
Here are two screen shots when selecting the only options that show up in the program:








Thanks.

---

### Post by papibe on 2015-05-26
It looks like the Nvidia driver is not loaded.

Could you open a terminal, run these commands, and post back the results (you can copy/paste the text)?
```
dpkg -l | grep nvidia

apt-cache policy nvidia-current

lspci -nnk | grep -iA2 vga

lsmod | grep -E 'nvidia|nouveau|i915|radeon|fglrx'

ls /etc/X11/xorg.conf
```
Regards.

---

### Post by matt. on 2015-05-26
> **papibe said:**
> It looks like the Nvidia driver is not loaded.

Could you open a terminal, run these commands, and post back the results (you can copy/paste the text)?
```
dpkg -l | grep nvidia

apt-cache policy nvidia-current

lspci -nnk | grep -iA2 vga

lsmod | grep -E 'nvidia|nouveau|i915|radeon|fglrx'

ls /etc/X11/xorg.conf
```
Regards.

Of course, here's my results:


dpkg -l | grep nvidia -
```
ii  nvidia-346                                           346.59-0ubuntu1                            amd64        NVIDIA binary driver - version 346.59
ii  nvidia-opencl-icd-346                                346.59-0ubuntu1                            amd64        NVIDIA OpenCL ICD
ii  nvidia-settings                                      346.59-0ubuntu1                            amd64        Tool for configuring the NVIDIA graphics driver

```


apt-cache policy nvidia-current- 
```

nvidia-current:
  Installed: (none)
  Candidate: 304.125-0ubuntu2
  Version table:
     304.125-0ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ vivid/restricted amd64 Packages

```



lspci -nnk | grep -iA2 vga - 
```

01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF110 [GeForce GTX 570 Rev. 2] [10de:1086] (rev a1)
    Subsystem: eVga.com. Corp. Device [3842:1571]
    Kernel driver in use: nvidia
01:00.1 Audio device [0403]: NVIDIA Corporation GF110 High Definition Audio Controller [10de:0e09] (rev a1)
    Subsystem: eVga.com. Corp. Device [3842:1571]
    Kernel driver in use: snd_hda_intel
02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)

```


lsmod | grep -E 'nvidia|nouveau|i915|radeon|fglrx' -
```

nvidia               8380416  0 
drm                   344064  2 nvidia

```


ls /etc/X11/xorg.conf - 
```

ls: cannot access /etc/X11/xorg.conf: No such file or directory

```


Thanks so much for your fast responses, and willingness to help! :D

---

### Post by papibe on 2015-05-26
Thanks.

How did you get the 346.59 driver? From a ppa, or from the Nvidia website?

Regards.

---

### Post by matt. on 2015-05-26
From the additional drivers program, I just selected it from the menu and hit apply.

---

### Post by papibe on 2015-05-26
Could you post the content of this file?
```
/var/log/Xorg.0.log
```
Please paste it here: [Ubuntu Pastebin]("http://paste.ubuntu.com/"), and then post back the link to the upload.

Regards.

---

### Post by matt. on 2015-05-26
Here are the contents of "/var/log/Xorg.0.log/":

[http://paste.ubuntu.com/11381825/](http://paste.ubuntu.com/11381825/)

---

### Post by papibe on 2015-05-26
Thanks. The driver is not loading properly:
```
[   768.372] (II) LoadModule: "nvidia"
[   768.373] (WW) Warning, couldn't open module nvidia
[   768.373] (II) UnloadModule: "nvidia"
[   768.373] (II) Unloading nvidia
[   768.373] (EE) Failed to load module "nvidia" (module does not exist, 0)
```
I believe you are running Vivid, right?

Let's try to reinstall the driver:
```
sudo apt-get install --reinstall nvidia-346 nvidia-346-uvm
```
Then create a xorg config file:
```
sudo nvidia-xconfig 
```
Then restart, and let us know how it goes.
Regards.

P.S.: If you boot into a black screen, just press Ctrl+Alt+F1, or Ctrl+Alt+F2 to get a text mode console screen. Login and clean the house:
```
sudo apt-get purge nvidia-346 nvidia-346-uvm
sudo rm /etc/X11/xorg.conf
```
and then restart:
```
sudo reboot
```

---

### Post by matt. on 2015-05-26
I ran the first command and got this output: [http://paste.ubuntu.com/11382419/](http://paste.ubuntu.com/11382419/)
It seems like everything worked fine, but when I ran the "sudo nvidia-xconfig" line, it said command not found. 
I sudo apt-get update and sudo apt-get upgrade to see if that would fix the issue but it did not. 

Referencing this post: [http://ubuntuforums.org/showthread.php?t=1756211](http://ubuntuforums.org/showthread.php?t=1756211)
It seems like I may need to install nvidia-settings and nvidia-current so I ran "sudo apt-get install nvidia-settings nvidia-current" to see if it would install without removing any programs but it said it would install and remove some things so I've posted it's output here:

```

sudo apt-get install nvidia-current nvidia-settings
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-settings is already the newest version.
nvidia-settings set to manually installed.
The following package was automatically installed and is no longer required:
  kde-l10n-engb
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
  libcuda1-304 nvidia-304 nvidia-opencl-icd-304
The following packages will be REMOVED:
  libcuda1-346 nvidia-346 nvidia-346-uvm nvidia-opencl-icd-346
The following NEW packages will be installed:
  libcuda1-304 nvidia-304 nvidia-current nvidia-opencl-icd-304
0 upgraded, 4 newly installed, 4 to remove and 0 not upgraded.
Need to get 47.7 MB of archives.
After this operation, 126 MB disk space will be freed.
Do you want to continue? [Y/n] n
Abort.

```

---

### Post by papibe on 2015-05-26
nvidia-settings is already installed. It is on the nvidia-346 package.

nvidia-current is another version of the driver (304). Do not install it just yet.

Did you restart after the reinstall?

Regards.

---

### Post by matt. on 2015-05-26
Yes, I rebooted to see if that would fix the issue and tried to run "sudo nvidia-xconfig" and got the same error.
Also, the nVidia X Server Settings program hasn't changed any.

---

### Post by papibe on 2015-05-26
At this time, I would try another version of the driver.

To clean the house:
```
sudo apt-get purge nvidia-\*
```
Then install the 'current' driver:
```
sudo apt-get install nvidia-current
```
Then try to create the xorg config file:
```
sudo nvidia-xconfig
```
Then reboot.

Let us know if that makes a difference.
Regards.

---

### Post by matt. on 2015-05-26
I've been trying to edit my last post but the page just kept loading and loading. I apologize for posting twice but thought it was important that you know the nVidia X Server Settings program hasn't changed any.

Thanks.

---

### Post by papibe on 2015-05-26
If it does not show something, it means the Nvidia driver is not loading properly. Here's an example on how it should look:
[ATTACH=CONFIG]262230[/ATTACH]

Regards.
P.S.: 'NVidia X Server Settings' is actually nvidia-settings, BTW

---

### Post by matt. on 2015-05-26
Nothing has changed. I purged all Nvidia, then installed the current driver, then rebooted and still the same situation.

Here is a paste of the output when installing the current version:
[http://paste.ubuntu.com/11383338/](http://paste.ubuntu.com/11383338/)

---

### Post by matt. on 2015-05-27
Could there be anything else causing the driver to not load properly?

---

### Post by papibe on 2015-05-27
From the output of:
```
$ lspci -nnk | grep -iA2 vga 
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF110 [GeForce GTX 570 Rev. 2] [10de:**[COLOR="#FF0000"]1086[/COLOR]**] (rev a1)
    Subsystem: eVga.com. Corp. Device [3842:1571]
    Kernel driver in use: nvidia
```
I see that your card internal Nvidia ID is 1086. We can check if the driver support the card by running:
```
for f in /usr/share/doc/nvidia-*/README.txt.gz; do zgrep -H 1086 "$f"; done
```
Could you run that command and post back the output?

Regards.

---

### Post by matt. on 2015-05-27
Sure, this is the output I received:

```

for f in /usr/share/doc/nvidia-*/README.txt.gz; do zgrep -H 1086 "$f"; done
/usr/share/doc/nvidia-304/README.txt.gz:    GeForce GTX 570                       0x1086             C

```

---

### Post by papibe on 2015-05-27
Well, it is supported.

Let's see if there's any difference in the log. Could you upload a new version of the /var/log/Xorg.0.log this time after booting with with 304 driver?

Regards.

---

### Post by matt. on 2015-05-27
Sure, I pasted the log file here:

[http://paste.ubuntu.com/11400701/](http://paste.ubuntu.com/11400701/)

Also, to show which driver is running:

```
sudo dkms status
nvidia-304-updates, 304.125, 3.19.0-18-generic, x86_64: installed
```

---

### Post by papibe on 2015-05-27
Same problem as before.

Let's see if there are other compatibility issues. Could you run these?
```
lsb_release -a

uname -a

sudo update-alternatives --config x86_64-linux-gnu_gl_conf

dpkg -l | awk '/linux-headers/ {print $2}'

apt-get cache policy linux-headers-generic

zcat /usr/share/doc/linux-headers-generic/changelog.gz | head

```
Regards.

---

### Post by matt. on 2015-05-27
Again, thank you very much for your help!

Here are the results:


lsb_release -a
```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 15.04
Release:	15.04
Codename:	vivid

```


uname -a
```

Linux gengar 3.19.0-18-generic #18-Ubuntu SMP Tue May 19 18:31:35 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```sudo update-alternatives --config x86_64-linux-gnu_gl_conf


dpkg -l | awk '/linux-headers/ {print $2}'
```
linux-headers-3.19.0-15
linux-headers-3.19.0-15-generic
linux-headers-3.19.0-18
linux-headers-3.19.0-18-generic
linux-headers-generic

```


apt-get cache policy linux-headers-generic
```
E: Invalid operation cache

```


zcat /usr/share/doc/linux-headers-generic/changelog.gz | head
```
linux-meta (3.19.0.18.17) vivid; urgency=medium


  * linux ABI 3.19.0-18


 -- Luis Henriques <luis.henriques@canonical.com>  Tue, 19 May 2015 19:08:55 +0100


linux-meta (3.19.0.17.16) vivid; urgency=medium


  * linux ABI 3.29.0-17

```

---

### Post by papibe on 2015-05-27
Thanks.

I made a mistake on the apt-cache command, it should be:
```
apt-cache policy linux-headers-generic
```
Also, you missed this one:
```
sudo update-alternatives --config x86_64-linux-gnu_gl_conf
```
(just press enter when ask to reconfigure)

Regards.

---

### Post by matt. on 2015-05-27
Ahh, I see lol. Here are the correct results:

apt-cache policy linux-headers-generic
```
linux-headers-generic:
  Installed: 3.19.0.18.17
  Candidate: 3.19.0.18.17
  Version table:
 *** 3.19.0.18.17 0
        500 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     3.19.0.16.15 0
        500 http://security.ubuntu.com/ubuntu/ vivid-security/main amd64 Packages
     3.19.0.15.14 0
        500 http://us.archive.ubuntu.com/ubuntu/ vivid/main amd64 Packages

```


sudo update-alternatives --config x86_64-linux-gnu_gl_conf
```
There are 2 choices for the alternative x86_64-linux-gnu_gl_conf (providing /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf).


  Selection    Path                                       Priority   Status
------------------------------------------------------------
  0            /usr/lib/nvidia-304-updates/ld.so.conf      9701      auto mode
  1            /usr/lib/nvidia-304-updates/ld.so.conf      9701      manual mode
* 2            /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf   500       manual mode


Press enter to keep the current choice
[*], or type selection number: 

```

---

### Post by papibe on 2015-05-27
OK, something interesting!

Run this again, and this time select the first alternative (number 0)
```
sudo update-alternatives --config x86_64-linux-gnu_gl_conf
```
Restart, and let us know how it goes.
Regards.

---

### Post by matt. on 2015-05-27
Ok I did that, rebooted and this is the screen I got:

[IMG]http://s17.postimg.org/tkjqysxrj/IMG_0679.jpg[/IMG]




So, I opened the tty1 terminal, and tried to stop and start the lightdm service and got these errors:

[IMG]http://s17.postimg.org/xfn51dgxb/IMG_0675.jpg[/IMG]




So, I ran
```
[COLOR=#000000]sudo update-alternatives --config x86_64-linux-gnu_gl_conf
```
again and selected the 2nd option like it was before, and rebooted and was able to boot into the GUI but not with the nvidia-settings working correctly.[/COLOR]

---

### Post by grahammechanical on 2015-05-27
I am using a Sharp 24 inch LCD TV as a monitor and Displays calls it Sharp 7 inch. I can confirm that using a VGA connection with these types of displays will certainly limit the resolution options. But DVI should give you the full range.

The trick when switching between proprietary and open source video drivers is to know when to switch to the right settings utility. Displays for open source and Nvidia XServer Settings Manager for Nvidia. Get confused as I have in the past and it really gets confusing.

The Nvidia XServer Settings Manger should be much more useful than what you are seeing. Go to About this computer. If the Details page says Gallium you are running on Nouveau the open source video driver. With the Nvidia  driver it should tell you what Nvidia adapter you are using.

Regards.

---

### Post by matt. on 2015-05-28
Thanks grahammechanical, but I am using a DVI connection not VGA. The details page for my computer says it is running Gallium which is so frustrating.

Could any of this have to do with which display manager I'm using?

---

### Post by papibe on 2015-05-28
> **matt. said:**
> Could any of this have to do with which display manager I'm using?
In my assessment no.

According to the Xorg logs, the driver is not being loaded. That occurs before the attempt to recognize the monitor.

Thinking...

---

### Post by v3.xx on 2015-05-28
Post#30 screenshot

> NVIDIA: could not open the device file /dev/nvidiactl (no such device or address)

It is my understanding this file is generated at boot.

Could nvidiactl file be manually generated with the 'mknod' command?

---

### Post by matt. on 2015-05-28
What is the usage of the 'mknod' command?

Thanks.

---

### Post by v3.xx on 2015-05-29
I rather papibe chime in on this.  This at best could be a work-a-round, not a fix.  It should generate the file, but will be lost again on reboot.
```
man mknod
```

---

### Post by blm-ubunet on 2015-05-29
The OP needs to remove the "nomodeset" from the grub kernel cmd line..

The posted log file shows that nVidia, nouveau & vesa drivers are tried & fail, leaving FBDEV driver.
The first (3) require kernel mode setting (KMS) driver.

AFAIU
The installation process of the nVidia driver builds a shim between installed kernel & the close source kernel module.
That's why you need the linux kernel headers package that matches installed kernel.
Each time the installed kernel changes the above process is repeated.
The user space components of driver will not load/work without the kernel module loaded.

---

### Post by matt. on 2015-05-29
> **blm-ubunet said:**
> The OP needs to remove the "nomodeset" from the grub kernel cmd line..

The posted log file shows that nVidia, nouveau & vesa drivers are tried & fail, leaving FBDEV driver.
The first (3) require kernel mode setting (KMS) driver.

AFAIU
The installation process of the nVidia driver builds a shim between installed kernel & the close source kernel module.
That's why you need the linux kernel headers package that matches installed kernel.
Each time the installed kernel changes the above process is repeated.
The user space components of driver will not load/work without the kernel module loaded.

So all I'll need to do is remove "nomodeset" and that should fix the errors?

---

### Post by papibe on 2015-05-29
Could you show us the content of your /etc/defualt/grub?
```
grep -vE '^#|^$' /etc/default/grub
```
Regards.

---

### Post by matt. on 2015-05-29
Sure, here is the result of 
```

grep -vE '^#|^$' /etc/default/grub

```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

---

### Post by papibe on 2015-05-29
Thanks.

You don't have the nomodeset option set. Did you remove it? If so, you need to reboot to take effect.

If it wasn't there in the first place, let's try to boot with it in order to see if it makes a difference. To edit the file:
```
sudo nano /etc/default/grub
```
got the line that looks like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
and change it so it looks like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```
Save the file.Now update grub:
```
sudo update-grub
```
And finally you're ready to reboot. 

Let us know how that goes.
Regards.

---

### Post by matt. on 2015-05-29
Ok, I know that I did take it off while troubleshooting. So, I'll add it back and see what results I get.

---

### Post by matt. on 2015-05-29
Ok, I know that I did take it off while troubleshooting. So, I added it back and rebooted, and it's exactly the same.

Now, I'm going to run 

`[COLOR=#000000]sudo update-alternatives --config x86_64-linux-gnu_gl_conf `

And select the 0th option (like we tried to do earlier), then reboot. I'll post those results next.

[/COLOR]

---

### Post by matt. on 2015-05-29
I selected the nvidia driver(auto mode) and rebooted, and got the same "starting version 219" screen. Followed by not being able to start lightdm or startx with the same errors.

---

### Post by papibe on 2015-05-29
Let's try one thing at a time. Left the 'update-alternatives' as when it was working, and test with and without the nomodeset option.

We need to get the driver loaded first, and then tackle the monitor.  When the driver is loaded, you'll see a bunch of stuff on the 'Nvidia X Server Settings' (like my example on post #18) even if the monitor says unknown.

**IMPORTANT:**

I missed one instruction on post #41 (now updated): every time you modify the grub file, you have to run this before reboot:
```
sudo update-grub
```
Regards.

---

### Post by blm-ubunet on 2015-05-29
The /var/log/Xorg.0.log clearly shows the actual/real/last kernel boot command..
The last posted log shows "nomodeset".

It would appear that changes to grub-kernel command were never being actually applied during (previous) debugging.
So you have to disbelieve all previous findings.

No modern video driver works with "nomodeset" kernel option; that's why it exists. It allows to bypass broken systems & use the framebuffer driver. All video cards firmware have to provide support for the basic "VGA" interface.

---

### Post by matt. on 2015-05-29
> **papibe said:**
> Let's try one thing at a time. Left the 'update-alternatives' as when it was working, and test with and without the nomodeset option.

We need to get the driver loaded first, and then tackle the monitor.  When the driver is loaded, you'll see a bunch of stuff on the 'Nvidia X Server Settings' (like my example on post #18) even if the monitor says unknown.

**IMPORTANT:**

I missed one instruction on post #41 (now updated): every time you modify the grub file, you have to run this before reboot:
```
sudo update-grub
```
Regards.


I left the update-alternatives as it was before the changes (option 2) and added "nomodeset" to the grub file, then ran "update-grub". Same problems, the Nvidia X Server Settings is still nearly empty. Should I change update alternatives and try again with the "nomodeset" in the grub file?

---

### Post by matt. on 2015-05-29
> **blm-ubunet said:**
> The /var/log/Xorg.0.log clearly shows the actual/real/last kernel boot command..
The last posted log shows "nomodeset".

It would appear that changes to grub-kernel command were never being actually applied during (previous) debugging.
So you have to disbelieve all previous findings.

No modern video driver works with "nomodeset" kernel option; that's why it exists. It allows to bypass broken systems & use the framebuffer driver. All video cards firmware have to provide support for the basic "VGA" interface.

So this means that I should try everything without nomodeset after update-grub?

---

### Post by papibe on 2015-05-29
> **matt. said:**
> Should I change update alternatives and try again with the "nomodeset" in the grub file?
Just remove nomodeset, update-grub, reboot.

Regards.

---

### Post by matt. on 2015-05-29
> **papibe said:**
> Just remove nomodeset, update-grub, reboot.

Regards.

No change at all.. again.

---

### Post by blm-ubunet on 2015-05-30
Now we need to see the log file..
/var/log/Xorg.0.log

---

### Post by matt. on 2015-05-30
Sorry, I won't be able to post the log file until tomorrow (I am away from home for the weekend).

But I did find something very interesting - when I run 'sudo nvidia-settings', I get these error messages:

```
** Message: PRIME: No offloading required. Abort
** Message: PRIME: is it supported? no


ERROR: nvidia-settings could not find the registry key file. This file should
       have been installed along with this driver at
       /usr/share/nvidia/nvidia-application-profiles-key-documentation. The
       application profiles will continue to work, but values cannot be
       preopulated or validated, and will not be listed in the help text.
       Please see the README for possible values and descriptions.
```

---

### Post by matt. on 2015-05-30
Another interesting thing I discovered:

After reading about the above problem, someone found a solution by installing the 3.19.0.5 kernel and booting with that. So I went to the synaptic package manager to see if I could find that kernel, I couldn't, but I did realize I had both 3.19.0.18 and 3.19.0.15 (15 came on my install disk and during install it was updated to 18).

So, I booted into the version 15 kernel, and now I can change my resolution from the display settings and my monitor shows up as a Samsung.

Interesting that the newer kernel couldn't recognize it for some reason. And now I'm thinking that the driver is running (a few games showed dramatic improvement) and it's just nvidia-settings that isn't being properly loaded.

---

### Post by blm-ubunet on 2015-05-30
Log files tell you everything.. no guessing required.
All good s/w generates std-out & log files.

The nVidia driver package has to build against **every** kernel.
It is possible you don't have the linux headers meta package installed.
It is possible your nVidia package can not be build against that kernel version.

For many years I've sourced the nVidia packages from xorg-edgers ppa.

The synaptic package manager or apt-get std-out (terminal text) would show you precisely what is happening.
It shows you each kernel installed being examined & then rebuilding the nVidia module for each.
Then this triggers updates of "initramfs" images for grub process.

The xorg log file shows precisely which kernel & xorg version is running & build time.

AFAIK
Don't use sudo with nvdia-settings, I think it uses the wrong home settings file (.nvidia-settings-rc).
Only problem with this is if you need to save configuration to "/etc/X11/xorg.conf" (which you do not.)

---

### Post by matt. on 2015-05-31
> **blm-ubunet said:**
> Now we need to see the log file..
/var/log/Xorg.0.log


The latest log:

[http://paste.ubuntu.com/11484533/](http://paste.ubuntu.com/11484533/)

---

### Post by blm-ubunet on 2015-05-31
The log file shows kernel 3.19.
The log shows nouveau fails because KMS fails:
> (EE) [drm] KMS not enabled
AFAIK that can be because kernel is not compiled with DMS support or loaded with "nomodeset" kernel cmd option.

Maybe your nouveau packages are to old to support GTX570 fermi NVC0/NVC8 (GF110) .. don't know, can't tell from nouveau web resources when support was added.

Can you install nVidia 304.125 ? and post the log file again.

OR
can you use grub & reboot with 3.15 kernel & then post Xorg log file ?

---

### Post by matt. on 2015-05-31
Sure, first I'll boot with 3.15 and post results.

Also, what method for installing nVidia 304.125 do you recommend?
I ask because you can install from nVidia's site, through additional drivers, and through the synaptic package manager.

Thanks.

---

### Post by matt. on 2015-05-31
Log from booting with 3.15: [http://paste.ubuntu.com/11485304/](http://paste.ubuntu.com/11485304/)

---

### Post by blm-ubunet on 2015-05-31
Success.
That shows nouveau driver loading.
The xorg.conf should be moved out of the way for nouveau.

Kernel 3.19 (from ubuntu vivid) clearly does not work right at the moment.

Rename /etc/X11/xorg.conf to make a backup copy
Then delete /etc/X11/xorg.conf..
Switch to console tty "ctrl+alt_f1"
kill/start X server "sudo initctl restart lightdm"
Login
Use unity desktop appearances to change resolution or xrandr.

Synaptic & additional drivers (jockey tool) (& apt-get) should give exact same result.
Synaptic is the best tool IMO.
Do NOT use nVidia website to get driver unless you are expert.
The xorg edgers ppa is an good option for those who need later versions/bugfixes etc.

---

### Post by matt. on 2015-06-01
I don't have a file named xorg.conf in /etc/X11/:

```
matt@gengar:~$ cd /etc/X11
matt@gengar:/etc/X11$ ll
total 92
drwxr-xr-x  11 root root  4096 May 22 16:23 ./
drwxr-xr-x 153 root root 12288 May 30 15:17 ../
drwxr-xr-x   2 root root  4096 Apr 22 08:08 app-defaults/
drwxr-xr-x   2 root root  4096 Apr 22 08:08 cursors/
-rw-r--r--   1 root root    14 May 22 16:23 default-display-manager
drwxr-xr-x   5 root root  4096 May 22 16:22 fonts/
-rw-r--r--   1 root root 17394 Dec  3  2009 rgb.txt
drwxr-xr-x   2 root root  4096 May 22 16:04 xinit/
drwxr-xr-x   2 root root  4096 Jun 23  2014 xkb/
-rwxr-xr-x   1 root root   709 Apr  1  2010 Xreset*
drwxr-xr-x   2 root root  4096 Apr 22 08:07 Xreset.d/
drwxr-xr-x   2 root root  4096 Apr 22 08:07 Xresources/
-rwxr-xr-x   1 root root  3730 Mar  9 06:38 Xsession*
drwxr-xr-x   2 root root  4096 May 26 20:53 Xsession.d/
-rw-r--r--   1 root root   265 Jul  1  2008 Xsession.options
drwxr-xr-x   2 root root  4096 Apr 22 08:08 xsm/
-rw-r--r--   1 root root   601 Apr 22 08:07 Xwrapper.config

```

It looks like that file doesn't exist anymore: [http://www.askubuntu.com/questions/4662/where-is-the-x-org-config-file-how-do-i-configure-x-there](http://www.askubuntu.com/questions/4662/where-is-the-x-org-config-file-how-do-i-configure-x-there)

And what can I do about the nVidia X Server Settings still not working?
I'm super excited that I can change to a resolution that looks nice on this monitor, but I'd still really like to be able to change other settings that I should be able to change.

How could it still not be working anyway with the driver loaded and everything?

---

### Post by blm-ubunet on 2015-06-01
The file "/etc/X11/xorg.conf" can still be used but is not necessary except for unusual use cases like custom modelines & display devices without EDID etc.
Was just making sure there wasn't a conf file interfering.

Have you installed nVidia proprietary driver ?
Have you confirmed this by checking "/var/log/Xorg.0.log" ?

Then start nvidia-settings from the cmd line from terminal (ctrl+alt+t) & note the stdout messages.
Don't try start this from console tty.

---

### Post by matt. on 2015-06-01
I'm not sure what exactly to look for in "/var/log/Xorg.0.log" to check and make sure the nVidia driver is installed properly. 

And I get the same std-out from earlier when starting nvidia-settings:

```
matt@gengar:~$ nvidia-settings
** Message: PRIME: No offloading required. Abort
** Message: PRIME: is it supported? no


ERROR: nvidia-settings could not find the registry key file. This file should
       have been installed along with this driver at
       /usr/share/nvidia/nvidia-application-profiles-key-documentation. The
       application profiles will continue to work, but values cannot be
       preopulated or validated, and will not be listed in the help text.
       Please see the README for possible values and descriptions.
```

---

### Post by papibe on 2015-06-01
> **matt. said:**
> I'm not sure what exactly to look for in "/var/log/Xorg.0.log" to check and make sure the nVidia driver is installed properly. 
Paste it on paste.ubuntu.com, so we can take a look.

Regards.

---

### Post by matt. on 2015-06-01
Results of "/var/log/Xorg.0.log" when booting in 3.15:  [http://paste.ubuntu.com/11510639/](http://paste.ubuntu.com/11510639/)

---

### Post by papibe on 2015-06-01
It looks like still the driver is not loading. Neither the open source, nouveau, or the proprietary Nvidia driver :(

---

### Post by blm-ubunet on 2015-06-03
Matt, note you're trying to use kernel 3.19 again..
That specific version was causing all your problems with nVidia..

The nouveau driver has loaded fine.
Your monitor is:
> Monitor name: SyncMaster
[    38.475] (II) NOUVEAU(0): Serial No: HCGQ912383
[    38.475] (II) NOUVEAU(0): EDID (in hex):

Note that you can **not** use nvidia-settings with nouveau driver.. You must use xrandr or the desktop managers screen/appearances tool.

The previous nVidia registry keys missing message is about some missing files in nVidia install that provide "tooltips" & default values in dialogue boxes in the nvidia-settings GUI; has no impact on core driver.

Summary:
kernel 3.19 - is a failure with nVidia; okay with nouveau
nVidia 304 - failure due to display artifacts/corruption
nouveau - not tried with kernel 3.15. prob okay

---

### Post by matt. on 2015-06-03
I'm almost positive that log was after booting with the 3.15 kernel.

And now I am 100% sure that I booted with 3.15 before getting the log. Here's the output: [http://paste.ubuntu.com/11554476/](http://paste.ubuntu.com/11554476/)


When I boot in the 3.19 kernel, I can barely run Minecraft without locking up my computer, but when I boot in with 3.15 it runs pretty well. If none of the drivers are being loaded, then why is this the case?

---

### Post by blm-ubunet on 2015-06-04
> 38.177] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-15-generic root=UUID=0e194148-db23-40de-aff3-95dce217ccbc ro quiet splash
Your pastebin log shows 3.19

From your posted logs kernel 3.19 only showed a problem with the nVidia driver.

---

### Post by ratta77at on 2015-10-02
I got the same problem (maybe) on 14.04 LTS.

I could solve this problem by copying the driver library.
```
sudo cp /usr/lib/nvidia-[DRIVER_VERSION]/xorg/nvidia_drv.so /usr/lib/xorg/modules/drivers
```
In my case (nvidia-340-updates),
```
sudo cp /usr/lib/nvidia-340-updates/xorg/nvidia_drv.so /usr/lib/xorg/modules/drivers
```

Reference:

[LIST]
[*]Ubuntu&#12391;NVIDIA&#12398;&#12487;&#12451;&#12473;&#12503;&#12524;&#12452;&#12489;&#12521;&#12452;&#12496;&#12364;&#21205;&#20316;&#12375;&#12394;&#12356;&#22580;&#21512;&#12398;&#12481;&#12455;&#12483;&#12463;&#38917;&#30446; [http://qiita.com/gm3d2/items/8346c76961d3fdb257b7](http://qiita.com/gm3d2/items/8346c76961d3fdb257b7)
[/LIST]

---

### Post by VMC on 2015-12-14
I have nvidia driver working fine in kernal 3.19.0-39-generic, but I have this same issue in kernal 4.3.0.2 running current xubuntu 16.04. I will check launchpad for any references.
I have the exact same issue in xorg.log of nvidia not loading.

---

