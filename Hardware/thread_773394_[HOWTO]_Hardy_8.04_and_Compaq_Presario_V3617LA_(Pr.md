---
title: "[HOWTO] Hardy 8.04 and Compaq Presario V3617LA (Presario V3000 series)"
date: 2008-04-28
forum: Hardware
---

### Post by salvador_luna on 2008-04-28
Well, I have a "hard time" configuring my laptop with Gutsy and now with Hardy but, after some research i have a almost fully functional laptop (with both versions).

I decided to write this little "how to" because i searched the forums and I didn't find anything related to my specific model, so I had to put together all the info i was able to find: maybe what I did helps people with the same laptop.

So let's get started.

My specs (in short) are:

- Compaq Presario V31617LA (Presario v3000 series).
- 1024 MB RAM.
- 120 GB Hard disc.
- Mobile AMD Sempron.
- Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02).
- nVidia Corporation GeForce 7150M (rev a2)
- nVidia Corporation MCP67 High Definition Audio (rev a1).


[COLOR="Red"]Important: Before you start, make sure that your BIOS is up to date. I installed the update within windows.[/COLOR]

1) I started with a clean installation of ubuntu 8.4 in safe graphics (live CD). If I don't use this option, the live cd crashes randomly. I do not use any option like acpi=off, nor i dual boot with windows (if you update the bios, you be be able to begin in step 2).

2) Once it is installed, i proceed (using a cable) to download this packages in synaptic: “nvidia-glx-new”, “nvidia-glx-new-dev”, “nvidia-new-kernel-source”, eneabled them in the "hardware drivers" and restarted the system.
> sudo apt-get install nvidia-glx-new nvidia-new-kernel-source nvidia-glx-new-dev

3) back in Ubuntu, the resolution was correct and the effects were turned on. The next step was to configure the wireless card. Note that the network manager failed to detect mi wireless card, but i can see it with the "lspci" command in the terminal. I researched the forums and i can use ndiswrapper to configure the wireless:

a) Install ndiswrapper
> sudo apt-get install ndiswrapper

b) Download de driver from the manufacturer's website (in mi case, from HP.com and the windows xp driver).

c) Install cabextract
> sudo apt-get install cabextract

d) Extract the driver from the downloaded file:

> cabextract nameofthefile.exe

e) Install the driver using ndiswrapper. It is important to locate the .inf file from the extracted driver. If ther is more than one .inf file, maybe you should try them if the wireless card does not work with the one selected in the first place.
> sudo ndiswrapper-i nameofthefile.inf

f) Verify that ndiswrapper loaded the driver correctly:
> ndiswrapper -l

It should say something like this: driver installed, device present.

g)If it says that the driver is not installed or another error message, uninstall the driver and use another .inf file. To uninstall the driver do:
> ndiswrapper -e nameofthedriver

The name of the driver can be obtaained using the ndiswrapper -l command. It is the name before the "driver installed, device present" message.

h) If there is no error message, try this commands, one by one, in the terminal.

>     sudo rmmod b43
    sudo rmmod b44
    sudo rmmod b43legacy
    sudo rmmod ssb
    sudo rmmod ndiswrapper
    sudo modprobe ndiswrapper
    sudo modprobe ssb
    sudo modprobe b44

i) If the wireless network was detected and you can conect to it, use the following command to make the system runs the above commands and ndiswrapper can work fine:
> echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper

Make sure you fully copy the above line because it is a long one.

Note: This command will make the step h) permanent.

j) To load the ndiswrapper at the startup:
> sudo gedit /etc/modules

Add "ndiswrapper" (without the quotes) at the end of the file. Save it and close it. We finished with the wireless card.


4) To play flash files and avoid crashes on firefox or the sound system, follow this guide:

[http://ubuntuforums.org/showthread.php?t=768448](http://ubuntuforums.org/showthread.php?t=768448)


5) Everything else worked "out of the box" (including the integrated mic).


And that's all!


Now the bad things I've found so far:

1) Listening audio files and doing something else makes the song "choppy".

2) When i unplugged the power cable and let the screen get a little dark, i plugged in the power again and the brightness was set incorrectly (about 50%), nothing i can't live with.

I hope this little guide helps someone to configure their laptops (and to be a happy user of Ubuntu like me)and thank's to everyone for writting the posts I used to install Hardy in my laptop.

Sorry about my english! My native language is spanish :D

Original guides for wireless:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-a9c75e76532933266fabeef1b1aa742f3df4444c](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-a9c75e76532933266fabeef1b1aa742f3df4444c)
[http://ubuntuforums.org/showthread.php?t=734404&hi](http://ubuntuforums.org/showthread.php?t=734404&hi)

Thanks to all the people who wrote the guides used to configure this laptop, all the credit is yours!

---

