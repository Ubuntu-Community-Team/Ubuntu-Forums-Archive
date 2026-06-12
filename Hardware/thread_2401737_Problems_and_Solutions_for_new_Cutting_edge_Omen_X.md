---
title: "Problems and Solutions for new Cutting edge Omen X Laptop - To help Others!"
date: 2018-09-21
forum: Hardware
---

### Post by markackerman8@gmail.com on 2018-09-21
First ,

Thanks to Mark Freudenberg for a Difficult issue of Ubuntu not showing My HDMI-0 or in other words My Digital Sound Card was not even RECOGNISED for a week and no help until I had to stumble upon this great thread ... See My Problem "1/"

But I will add now at the top some seriously annoying issues (just Problems with OUT Solutions - Any Help Greatly Appreciated - but sadly not expected - 13 years helping others and minimal reciprocity - Oh Well.

*Just UNFIXED PROBLEMS* :(

1/ UNFIXED / 
No HDMI Sound After Suspend or Hibernate (rebooting - no problem just down right ANNOYING)
Tried 30 posts and getting exhausted ... from my terminal (just my commands so you can get an idea of my unfruitful attempts :
$ lspci -v | grep -A7 -i "audio" (I will post the output of my HDMI to help those who may help me troubleshoot)
01:00.1 Audio device: NVIDIA Corporation GP104 High Definition Audio Controller (rev a1)
	Subsystem: Hewlett-Packard Company GP104 High Definition Audio Controller
**Note NVIDIA and Hewlett-Packard !! Damn Hp!

$ pulseaudio --kill; pulseaudio --start
$ pulseaudio --kill
$ load-module module-switch-on-port-available
$ sudo gedit /etc/pulse/default.pa
$ sudo chmod +x /lib/systemd/system-sleep/tv-sound
$ pacmd list-cards
$ sudo alsa force-reload
$ lspci -v | grep -A6 Audio
$ rm -r ~/.config/pulse ~/.config/pavucontrol.ini
$ sudo apt install --reinstall alsa-base alsa-utils pulseaudio linux-sound-base libasound2
$ pulseaudio -k
$ pulseaudio -v
$ sudo apt install pavucontrol (already installed of course)
$ mkdir ~/.pulse
$ echo "autospawn = no" >> ~/.pulse/client.conf
$ sudo gedit /etc/pm/sleep.d/50alsa
$ sudo alsa force-reload
#################### You get the idea at least you see I am trying !

$ pacmd list-cards

2/ UNFIXED
perhaps related to above and a partial solution below (#3)
in Gnomes Awesome Logs ... "Important" Errors

acpi INT3400:00: Unsupported event [0x86]  **387 TIMES!!!!!**
Everything I read says it is not important - I can assure you on this laptop it IS important!

ANy and I mean ANY Suggestions Appreciated Immensely

Over and Out for now Mark




*So A Big Problem and A Big Solution :D:*
 
1/ Add this patch to enable Cutting edge Nvidia HDA (High Def'n Audio)
the steps were a tad tricky so I will post them again:
I can confirm that kernel module, posted by Maik Freudenberg 

([https://bugs.freedesktop.org/show_bug.cgi?id=75985#c27](https://bugs.freedesktop.org/show_bug.cgi?id=75985#c27)), 

is working fine on my system. 

Thank you for the fix. The HDMI audio device now works as it should.

The steps I did to enable HDMI audio device:
1. Download and extract the file nvhda.tar.xz.
2.  Run these commands in Terminal,  in the location of the extracted folder 
 ```
make
```make
 ```
sudo make install
```sudo make install
 ```
echo nvhda | sudo tee -a /etc/initramfs-tools/modules
```
```
echo "options nvhda load_state=1" | sudo tee /etc/modprobe.d/nvhda.conf
```
```
sudo update-initramfs -u
```

3. Reboot.

################# Thanks Again Mark Freudenberg - ######################
and added info to show how it is like an Hp (Hewlit Packard Issue) and to show my card finally getting recognised

$ lspci -v | grep -A7 -i "audio"
00:1f.3 Audio device: Intel Corporation CM238 HD Audio Controller (rev 31) (prog-if 80)
	Subsystem: Hewlett-Packard Company CM238 HD Audio Controller
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel
01:00.1 Audio device: NVIDIA Corporation GP104 High Definition Audio Controller (rev a1)
	Subsystem: Hewlett-Packard Company GP104 High Definition Audio Controller
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel
See my Post ...[HTML]https://ubuntuforums.org/showthread.php?t=2401273[/HTML] for more info
##########################################################

2/ PROBLEM! 
W.R.T. This GTX 1080m and its Nvidia Driver, Some problems (MINOR ONES TO me!) but I am sure others would love an answer even more than I  - Any help appreciated!

There is no Option in this Optimus Laptop's Nvidia-Settings to Switch to Intel's GPU. Odd but I never use it.   Still it would be nice to be working as it should

3/ Huge Problem and **Solution** (MOSTLY Solved Only Sadly)
Problem:
Boot up and Shutdown can take long or even get Paralysed/ Hang 
And worse with this Danged HDMI Port plugged In! NVIDIA AGAIN!
Cause!!!!
Error: acpi INT3400:00: Unsupported event [0x86]  (115 time in this boot alone)
--------------------------------------
Here is a surprisingly simple solution that solved both problems (fast startup and normal background)
&#8227; Try disabling acpi in /etc/default/grub change this variable so it looks like this:
• ```
sudo gedit /etc/default/grub
``` 
 > GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=strict",

• Just add acpi=strict to whatever other directives existed already
• (used for acpi INT34000 Errors but rtesulted in 800x600 resolution PROBLEM)
• Make sure to
&#8728; sudo update-grub2, after modifying the file and before rebooting
• and reboot - problems solved :D
------------------------------------------------------------

But as I already mentioned the error still plagues this system !  Just manageable now!
Any Other Solutions??

And I am exhausted Now So I will post more Solutions and Problems Later

Thanks, Mark

---

### Post by markackerman8@gmail.com on 2018-09-24
OK I solved it myself ... !

At least for one reboot

I thought perhaps it had something to do with a few changed I made in the BIOS, which I thought "How can it effect, Sound?"

But reverting them back and sound magically appears

So here is what I changed from memory
Secure Boot Disabled (Why I enabled it for the re-install is beyond me - Oh Ya Ubuntu now has an option for "Secure or Fast Boot in the Startup Menu"

Disabled TPM key
and Disabled something else I can't remember,
Trying a restart to see if it persists - If it does there will be no more comments here!

---

### Post by markackerman8@gmail.com on 2018-09-24
But If someone can help with a little ISSUE, and this may help troubleshoot the root cause TOO.

After Hibernation, the card DISAPPEARS!

---

### Post by vishald on 2018-12-27
I had all these issues with Ubuntu .
I looked for 2 months for solution and finally solved every one.
But today I formatted my system and ended up back to where I started.
Hopefully I will be able to solve this time. Will make sure to post solution if I find any.

---

### Post by vishald on 2018-12-27
[B]Quick way to endup with less error on installing ubuntu 

[/B]If you have acpi error
-> first follow this step to turn on acpi off on loading

[COLOR=#0000ff]https://askubuntu.com/questions/160036/how-do-i-disable-acpi-when-booting/160056
[/COLOR]
as soon as you load 

->do [I]

sudo apt update
sudo apt upgrade
[/I]
->later install graphic driver
mention in step 7 of link

[COLOR=#0000ff]https://www.tecmint.com/things-you-mostly-need-to-do-after-installing-ubuntu-16-04/4/[/COLOR]

then restart 

you wont have to do acpi=off anymore after this your system will work properly without acpi errors

not sure if *sudo apt update* and *sudo apt upgrade* step is necessary

---

