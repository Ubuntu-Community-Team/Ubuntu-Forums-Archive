---
title: "Screen doesn't dim when power switches to battery"
date: 2013-08-06
forum: Hardware
---

### Post by benjamin3 on 2013-08-06
My name is Ben and this is my first post.  I have been using all sorts of OS's my whole life, and have recently decided to try running a linux distro full-time.  I chose Ubuntu 13.04 32bit for my daily-used personal machine.

I am using Ubuntu 13.04 32bit Desktop on an Acer 5534 laptop. My machine is set for dual boot; Windows 7 32bit and Ubuntu 13.04 32bit.

Quick specs
CPU: AMD L310 (1.2Ghz/64bit/x2Athlon) GPU: ATI HD3200 RAM: 4Gig HD:250Gig (120G for Ubuntu)

I have attempted to search the forum for an answer to this question, but have failed in reducing the search results down to a managable size.



Under Windows, whenever my power adapter falls out of the plug, the screen dims quite a bit because the OS is set to do that on battery power.  Likewise, whenever I manage to get the plug to stay put, the screen brightens back to full (since the power has been restored).

Put simpler:

Whenever the battery is being discharged, the screen dims.  Whenever the battery is recharging, the screen brightens.



My question is:

How do I force Ubuntu to do the exact same thing?

I have read the posts that claim setting the brightness when on battery should cause the machine to remember that as the 'battery powered' setting, but this does not function as expected on my machine.  *It seems as though there is only a single setting saved, and that single setting is applied regardless as to the power state.*

I read in another post about a command I can type to check stuff out, but to be completely honest I must be having some brain fog today... I can't follow any of it... something about for i = catx;stuff-and;stuff  

I am very leary of typing any commandline into my Ubuntu without understanding it first.  It took 4 installs to get my big tower setup properly, and I still hosed it again trying to get the screen bitness down to 16bit color (I failed and gave up).


I had been waiting impatiently for the forums to return so I could register just to ask this.  Glad the forums are back!

Thank you in advance for any and all advice!  I am trying to learn and retain so can be as proficient with linux as I am with M$ products.

---

### Post by slickymaster on 2013-08-06
Hi benjamin3, welcome to the forums.

There's something you can try, which is to add the parameter _acpi_backlight=vendor_ in **/etc/default/grub **file.
First open a terminal window and run the following:```
gksudo geany /etc/default/grub
```(replace geany with your installed text-editor). You'll be prompt to insert you password and once that's done you'll be presented with the file in question ready to be edited so all you have to do is to add the acpi_backlight parameter:```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX[COLOR=#ff0000][/COLOR]=[COLOR=#ff0000]**"acpi_backlight=vendor"**[/COLOR]
```Save and close the file and after that run:```
sudo update-grub
sudo reboot
```

---

### Post by benjamin3 on 2013-08-06
Okay, I got a problem immediately.

No gksudo command found.

what is gksudo, and why use it instead of sudo?

how would I discover my installed text editor?

and if something goes wrong, could that include a blank screen on reboot?

---

### Post by benjamin3 on 2013-08-06
I looked it up... gksudo redirected to gksu...

so gksu gives buttons to terminal programs... it is more complicated than that, but the general idea is certain terminal commands work better with window managers, and gksu gives them the option to use the window manager functions...??

For simplicity, gksu is sudo with window decorations..?

I'm installing it now... will report the results

---

### Post by benjamin3 on 2013-08-06
Okay, here is the command I used to begin with

gksudo gedit /etc/default/grub

it loaded up gedit and allowed me to edit it.  I made the edit, saved, now I'm about to reboot.  

Here's hoping it boots... every other time I tried out my Terminal-foo I failed miserably....

---

### Post by slickymaster on 2013-08-06
gksudo or gksu stands for running sudo graphically. [See this very good explanation on the subject]("http://www.psychocats.net/ubuntu/graphicalsudo").

There were rumors about getting rid of gksu replacing it by pkexec in the standard desktop, but I was under the impression that it wasn't supposed to happen until Saucy. Anyway you have two options, either you run the first command using sudo with the -i switch, like this:```
sudo -i geany /etc/default/grub
```or you choose to install gksu:```
sudo apt-get install gksu
```and then you will be able to use gksudo.

---

### Post by benjamin3 on 2013-08-08
Well, that didnt seem to have an effect- but to be honest I cant tell as my power jack actually broke while I did this... I have no external adapter at the moment to confirm the edit solved the problem or not...

I did notice the screen was dim upon reboot, then it promptly turned off (no power).

The act of my unplugging it it a rush finished off the job of breaking it... lol

just my luck.

I will get back to this once I repair it.

Thank you very much. 
:)

---

### Post by ooddiittyy on 2013-09-06
I am attempting to find a way to do the exact same thing as Ben; I am running 13.10, with the latest stable mainline kernel build (3.11) on a Sony Vaio Pro (2013) ultrabook. The Sony comes with a hardware light sensor to auto dim/brighten depending on ambient lighting, but all I'm really looking for is a way to maintain differential default levels on AC/battery power. I have tried appending "acpi_backlight=vendor" in the grub config to no avail. Does anyone else have any additional recommendations?

---

### Post by Toz on 2013-09-06
> **ooddiittyy said:**
> I am attempting to find a way to do the exact same thing as Ben; I am running 13.10, with the latest stable mainline kernel build (3.11) on a Sony Vaio Pro (2013) ultrabook. The Sony comes with a hardware light sensor to auto dim/brighten depending on ambient lighting, but all I'm really looking for is a way to maintain differential default levels on AC/battery power. I have tried appending "acpi_backlight=vendor" in the grub config to no avail. Does anyone else have any additional recommendations?
Here is how I do it:

1. First, find out which (if you have more than one) backlight interface(s) is your active interface. You can run this command to identify the interfaces:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; cat $i/actual_brightness; done
```
...in my case, I get:
> /sys/class/backlight/intel_backlight
3484     *<--- brightness*
3484     *<--- max_brighntess*
3484     *<--- actual_brightness*


2. To find out which one is the active one, echo a value between 0 and the second value above (max_brightness) to the brightness file:
```
echo 2000 | sudo tee /sys/class/backlight/intel_backlight/brightness
```
...you will probably need to change the value (2000) and the interface (intel_backlight) to suit your system. If you have more than one interface, try echoing appropriate values to all interfaces until one responds by changing the actual screen brightness. Some examples of commands are:
```
echo 4 | sudo tee /sys/class/backlight/acpi_video0/brightness
echo 32 | sudo tee /sys/class/backlight/acpi_video1/brightness
echo 64 | sudo tee /sys/class/backlight/nvidia/brightness
```

3. Once you have determined your active backlight interface and the correct brightness values that you want to use for "on battery" and "on a/c", create the following file:
```
gksu gedit /etc/pm/power.d/zzzbattery
```
...with the following content:
```
#!/bin/bash
case $1 in
    true) #on battery 
        echo [COLOR="#FF0000"]XX[/COLOR] > /sys/class/backlight/[COLOR="#FF0000"]INTERFACE[/COLOR]/brightness
        ;;
    false) #on ac 
        echo [COLOR="#FF0000"]YY[/COLOR] > /sys/class/backlight/[COLOR="#FF0000"]INTERFACE[/COLOR]/brightness
        ;;
esac
```
...where:
- [COLOR="#FF0000"]XX[/COLOR] is the brightness value you want for when the system is on battery
- [COLOR="#FF0000"]YY[/COLOR] is the brightness value you want for when the system is on a/c
- [COLOR="#FF0000"]INTERFACE[/COLOR] is your active interface name

4. Save the file and make it executable:
```
sudo chmod +x /etc/pm/power.d/zzzbattery
```
...and test.

_Caveats:_
If you have no backlight interfaces or you are unable to change the brightness by manually manipulating the interfaces, then more work needs to be done to get an active backlight interface.

---

### Post by ooddiittyy on 2013-09-07
> **Toz said:**
> Here is how I do it:

1. First, find out which (if you have more than one) backlight interface(s) is your active interface. You can run this command to identify the interfaces:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; cat $i/actual_brightness; done
```
...in my case, I get:


2. To find out which one is the active one, echo a value between 0 and the second value above (max_brightness) to the brightness file:
```
echo 2000 | sudo tee /sys/class/backlight/intel_backlight/brightness
```
...you will probably need to change the value (2000) and the interface (intel_backlight) to suit your system. If you have more than one interface, try echoing appropriate values to all interfaces until one responds by changing the actual screen brightness. Some examples of commands are:
```
echo 4 | sudo tee /sys/class/backlight/acpi_video0/brightness
echo 32 | sudo tee /sys/class/backlight/acpi_video1/brightness
echo 64 | sudo tee /sys/class/backlight/nvidia/brightness
```

3. Once you have determined your active backlight interface and the correct brightness values that you want to use for "on battery" and "on a/c", create the following file:
```
gksu gedit /etc/pm/power.d/zzzbattery
```
...with the following content:
```
#!/bin/bash
case $1 in
    true) #on battery 
        echo [COLOR=#FF0000]XX[/COLOR] > /sys/class/backlight/[COLOR=#FF0000]INTERFACE[/COLOR]/brightness
        ;;
    false) #on ac 
        echo [COLOR=#FF0000]YY[/COLOR] > /sys/class/backlight/[COLOR=#FF0000]INTERFACE[/COLOR]/brightness
        ;;
esac
```
...where:
- [COLOR=#FF0000]XX[/COLOR] is the brightness value you want for when the system is on battery
- [COLOR=#FF0000]YY[/COLOR] is the brightness value you want for when the system is on a/c
- [COLOR=#FF0000]INTERFACE[/COLOR] is your active interface name

4. Save the file and make it executable:
```
sudo chmod +x /etc/pm/power.d/zzzbattery
```
...and test.

_Caveats:_
If you have no backlight interfaces or you are unable to change the brightness by manually manipulating the interfaces, then more work needs to be done to get an active backlight interface.

That absolutely did the trick! Thank you very much; I really appreciate the guidance. As an aside, it's curious to me why this isn't enabled by default. Do you happen to know the thinking?

---

### Post by Toz on 2013-09-08
> **ooddiittyy said:**
> That absolutely did the trick! Thank you very much; I really appreciate the guidance. As an aside, it's curious to me why this isn't enabled by default. Do you happen to know the thinking?
A few reasons come to mind as to why its not working automatically:
1. If you have more than one backlight interface, the system may be confused as to which one to use.
2. If you have laptop-mode tools installed, you may need to look closely at the configuration file and make sure its setup correctly.
3. The power manager for your DE (Gnome, Unity, Xfce, etc) may not be properly managing the backlight interface.

---

### Post by Bjornen on 2013-10-27
THX Toz. This worked out of the box for me :)

---

### Post by muhammad4 on 2014-09-25
Awesome! It worked indeed.

---

### Post by mohsen-forghani on 2015-01-11
great thanks, it works:p

---

### Post by thethakuri on 2015-01-20
First of all, thank you for your solution, it works. However I have couple of questions:
**1**. In step 2, you have asked to, "*To find out which one is the active one, echo a value between 0 and the  second value above (max_brightness) to the brightness file*". I have three backlight interface and all of them seem to be active. However I used *acpi_video0 *in the *zzzbattery* file and it seems to work. So, it is okay to ignore the remaining two interfaces even though they seem to be active as well ?
**2**. Secondly, when the the power profile changes (i.e. when power is turned off or on), there is a delay of few secs before the right measure is applied. Is it normal for Ubuntu ? In windows it seems to be a little bit swifter.
Cheers !

---

### Post by Toz on 2015-01-21
> **thethakuri said:**
> So, it is okay to ignore the remaining two interfaces even though they seem to be active as well ?
Yes. Although they are present, they don't seem to be the active ones.
> **2**. Secondly, when the the power profile changes (i.e. when power is turned off or on), there is a delay of few secs before the right measure is applied. Is it normal for Ubuntu ? In windows it seems to be a little bit swifter.
When the power profile changes, a number of scripts are run. Have a look at /var/log/powersave.log to see the sequence. You can try renaming zzzbattery to make it run earlier (the scripts are run in alphabetical order). The only thing to keep an eye on is if it gets reversed once again by one of the other scripts that may be affecting the brightness level. Moving it up in the execution order may have it execute quicker.

And btw, welcome to the forums.

---

