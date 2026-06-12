---
title: "Compaq Presario F500"
date: 2007-07-18
forum: Hardware &amp; Laptops
---

### Post by ErusGuleilmus on 2007-07-18
At first I couldn't get this too boot Ubuntu, but I found out that it was because of the Graphics. For this to successfully boot, I need to add these to things to the script by pushing "e" on the boot kernel: "vga=792" & "noapic". It is a minor pain in the butt because every time I reboot I have to re-add these things in. Is there a way for me to permanently add them so I never have to do it again? Thank you for all the support these forums are famous for!

---

### Post by LaGzo on 2007-07-27
What version of ubuntu are you running? I have the same laptop and it wont boot into ubuntu...

---

### Post by zoid15 on 2007-07-31
hi,

i have an F500 as well and managed to get it to install and boot fine once i used the noapic and nolapic commands when booting off the downloaded CD image. #

Now if only I could get the wireless working its goodbye microsoft!!

---

### Post by zwies on 2007-08-04
I have been trying to install some form of linux on my compaq presario f500 for the last few days and have not been able to.

Would one be able to say how they were able to get it on their system. have been trying to use ubuntu 5.04. and it is having problems detecting the hardware. the live CD reckons there is no screen attached thus failing to start the x server. and the install disk with that for some reason can not detect the hard drive.

i could probably guess that getting the latest version would fix some of the issues.

---

### Post by zoid15 on 2007-08-05
All I had to do to get the CD to boot was type the "noapic nolapic" in the install with additional command screen you get by pressing F something...

Sorry I cant be more specifiic

---

### Post by bpierce815@yahoo.com on 2007-08-08
OK.  Here are the steps that I had to use to get anything installed on this system. This is going from memory. Not difficult, just had to know the commands.

I used the x86_64 version of Fedora7, but this should work for any modern linux distribution using grub boot loader.

When the CD boots to the grub menu, hit "e", then on the line that start with "kernel", hit "e" again and append the following to that line:```
 noapic irqpoll acpi=off
```  Hit enter to apply the changes and then "b" to boot with them.

Once the operating system is installed, and the computer reboots to the installed grub menu, follow the same procedures again on that grub menu.  This will mess with the irqs a little and the wireless card will be trying to associate to irq-0 which will not work, but we are going to fix that.

Disable the service "cpuspeed" according to you distributions instructions. 

Then edit the grub.conf file by typing:```
sudo gedit /boot/grub/grub.conf
```Append the following to the end of the line that starts with "kernel":```
noapic irqpoll
``` Save the file and reboot. *NOTE: acpi=off is no longer needed because we have turned off cpuspeed and turning acpi off completely causes other problems.*

Everything should run smoothly from here.  To get the wireless working, install ndiswrapper according to your specific distribution, and search google for bcmwl5.inf with bcmwl5.sys(for i386 installations) and bcmwl5.inf with bcmwl564.sys(for x86_64 installations). 

Hope this helps

---

### Post by marc66thomas on 2007-08-27
> **bpierce815@yahoo.com said:**
> OK.  Here are the steps that I had to use to get anything installed on this system. This is going from memory. Not difficult, just had to know the commands.

I used the x86_64 version of Fedora7, but this should work for any modern linux distribution using grub boot loader.

When the CD boots to the grub menu, hit "e", then on the line that start with "kernel", hit "e" again and append the following to that line:```
 noapic irqpoll acpi=off
```  Hit enter to apply the changes and then "b" to boot with them.

Once the operating system is installed, and the computer reboots to the installed grub menu, follow the same procedures again on that grub menu.  This will mess with the irqs a little and the wireless card will be trying to associate to irq-0 which will not work, but we are going to fix that.
[B]
Disable the service "cpuspeed" according to you distributions instructions. [/B]

Then edit the grub.conf file by typing:```
sudo gedit /boot/grub/grub.conf
```Append the following to the end of the line that starts with "kernel":```
noapic irqpoll
``` Save the file and reboot. *NOTE: acpi=off is no longer needed because we have turned off cpuspeed and turning acpi off completely causes other problems.*

Everything should run smoothly from here.  To get the wireless working, install ndiswrapper according to your specific distribution, and search google for bcmwl5.inf with bcmwl5.sys(for i386 installations) and bcmwl5.inf with bcmwl564.sys(for x86_64 installations). 

Hope this helps

Where are you finding "Disable the service 'cpuspeed' according to you distributions instructions" I'm going to install From 7.04 as a dual boot with Vista already installed. Are there any other "gotchas" on this machine since with Vista , Again it's already installed. and CD iso in hand.

---

### Post by tim1980 on 2007-09-03
Thanks for the information in here guys

I just bought a new Compaq Presario F500 with AMD Athlon 64x2 1700Mhz and went to show a friend Ubuntu booting on it for the first time as I had not tested first and was embarrassed when it failed.

It's booted now though and installing

---

### Post by tim1980 on 2007-09-05
Im very disappointed that this new laptop does not work correctly on any Ubuntu based Distro.

I have tested it on 7.1 a5 and it still cannot boot into the GUI, when the GUI should come up it fails to work and the screen goes crazy.

Yes the above workaround works, but then the system is without Power Management so cannot turn the laptop off without pressing the off button...

Also the wireless is not working, OMG so annoying:popcorn:

---

### Post by tim1980 on 2007-09-06
PCLinuxOS 2007 works on this laptop

---

### Post by zutronius on 2007-09-07
I also just put PCLINUXOS on my F500 and it works great (just have to get the wireless working!)

---

### Post by waseidel on 2007-09-27
well i have installed Ubuntu 7.04 and updating to 7.10 and my system works correctly just don't work wireless, at the first run I have to run in recovery mode to make work X server and then I make this to install the drivers

```
apt-get install nvidia-settings nvidia-glx nvidia-xconfig
```

then I reboot and voila it X server works correctly even the nvidia logo is showed, other way to run the nvidia driver it downloading directly from the nvidia's page you boot from recovery mode 

```
sh nvidia-xxxxxx.run
```

it guide you to install the driver you just have to follow it

I hope this can help you, if some of you have the way to make work the bcm43xx correctly please tell me

sorry if you can't understand my English but I speak Spanish I have to make in English (too much work for me)

---

### Post by oddchild on 2007-10-20
I also got the compaq Presario f500...


According to the features, broadcom and nvidia is supported... 

It seems to run more slow than the last release (i386 on AMD)

The broadcom and nvidia drivers are showing up on restricted drivers, but the broadcom is not working... Is it working for anyone else?

---

### Post by lahvak on 2007-10-21
I have this laptop, and I installed Fiesty on it following instructions from this forum, by booting from CD, editing the boot options (adding noacpi) and installing the system.  What impressed me was that GRUB got installed with the edited options.  Then I installed Nvidia drivers from the GUI. I got wireless working by installing ndiswrapper from source, and loading the correct windows driver from command line.  After upgrading to Gutsy, the boot and the NVidia drivers worked fine, but wireless was broken.  This time all I needed to do, though, was to install ndiswrapper and ndisgtk packages. After that, I could load the windows driver from the ndisgtk gui, and after a reboot, everything worked just fine.   It seems that for some reason the native bcm driver does not work on this laptop. You have to install ndiswrapper and use that instead. 

There are still couple of things that don't work for me.  One of them is user switching.   When trying to switch users, the screen becomes bright orange, and the laptop hangs, not listening to keyboard input at all, and has to be turned off.  Did anybody managed to get that working?

---

### Post by oddchild on 2007-10-22
i just tried your advice... i installed it and it still doesnt seem to work.  im not sure what to do. it looks like it is installed right, but it isnt detecting networks.. 

(help save me from the vista nightmare) 

Thanks, I appreciate your help.

---

### Post by lahvak on 2007-10-22
In addition to installing ndiswrapper, you may need to blacklist the native driver from the kernel: in a terminal, run

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist


(If you ever want to reverse this step, just run 

sudo gedit /etc/modprobe.d/blacklist

and remove the line that says 

blacklist bcm43xx

)

---

### Post by oddchild on 2007-10-23
grr...

i did that, then reinstalled the driver via ndiswrapper, but now it doesn't allow me to "scan". It acts like I do not have a wifi card at all...


When I do a scan from terminal, via sudo iwlist scanning...


it says 


lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

It doesn't seem to notice the wifi card.. :(

Thanks everyone

---

### Post by oddchild on 2007-10-23
I got it to work! :) 


> Wireless Card Setup
Download and extract the files I have here.
Now go to System > Administration > Synaptic Package Manager.
While we're here we're going to unlock all our repositories. Go Settings > Repositories. Check all the boxes on the first page except for the CD, and hit close. A window will pop up telling you that you need to reload your packages. Go ahead and close that window, and click reload at the top.
Once that is finished click in the main window and start typing &#8220;ndiswrapper&#8221;. It will automatically scroll down and find it. Click the box next to &#8220;ndiswrapper-utils&#8221; and click &#8220;Mark for Installation&#8221;. Now go ahead and click Apply at the top.
After that is installed open a terminal window. Applications > Accessories > Terminal. Navigate to where you saved the drivers I had you download and extract. Now enter the following
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -m
Our wireless driver is now installed but not working just yet. It's currently being blocked by another driver that is trying to run, so we need to block this other driver. In a terminal enter &#8220;sudo gedit /etc/modprobe.d/blacklist&#8221; A text editor will pop up with the blacklist. Go to the end, start a new line, and enter &#8220;blacklist bcm43xx&#8221; without quotes. Save the file.
Now for some reason ndiswrapper doesn't load automatically when it starts up. So now let's make a new script. Open up a terminal and navigate to the folder with the wireless cards, or another safe folder. Enter "gedit ndiswrapper". The gnome text editor will come up again. Enter "modprobe ndiswrapper" and save it. Close the text editor and enter "chmod +x ndiswrapper" to make our script executable. And lastly enter "sudo update-rc.d ndiswrapper defaults".

After a restart your wireless should be working and the light should be glowing blue. Congratulations, you now have a functional wireless card.

Now that you have a functional laptop, lets go ahead and do those updates.


:)


YAY!!!!

---

### Post by zerobravo on 2008-04-25
I have a Compaq Presario F500 (F503AU)

I have everything working fine under Ubuntu 7.10 AMD64 without having to bash away in a terminal session to get the wireless to work.

I have written up what I did below....but have found that the firmware for the wireless broadcom 43xx doesn't seem to be picked up when I have installed a i386 release of ubuntu....weird

Model: F503AU
Video: Nvidia Go 6100 Video = working OK
Wifi: Broadcom 4319 = working OK

I booted with the Ubuntu 7.10 AMD64 Live CD
At the splash screen I pressed F6 for other options and at the end of the text string entered 

>  vga=792 noapic nolapic

I then got to the desktop and chose to install

I did all the usual localisation settings but for the formating of the hard drive I chose a guided install for the whole partition.

Ubuntu installed. AOK

I then did the updates. (approx 90)

reboot

I then went to System -> Administration -> Restricted Drivers Manager

In the manager I have listed

> DRIVER: Nvidia accelerated graphics driver (latest cards)

and  

> FIRMWARE: Firmware for Broadcom 43xx chipset family

I ticked enable for both

rebooted

Wifi light is now BLUE!!!!

Then I went to System -> Administration -> Network

clicked on Wireless Connection then Properties

set up my ssid and passkey

set DHCP for the IP address

and then was done....**nothing to do at the terminal**

Notes: 

1: I did a clean install to move to Ubuntu 8.04 i386, but the Firmware for the Broadcom Wireless was not in the restricted drivers manager - weird

2: On Ubuntu 7.10 AMD64 DHCP didn't work for me the first time I built it....but today after I went back to it from a failed install of Ubuntu 8.04 i386 DHCP worked fine......weird

---

