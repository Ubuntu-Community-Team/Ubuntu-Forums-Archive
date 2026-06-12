---
title: "Installing ATI driver"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by Klitsie on 2009-02-10
HI,
I am new to ubuntu.
I want to install my graphiccard driver.
So i downloaded it from the ati site. It is an .run file.
I can run it, then some other file pops up on the desktop. But then i get the message: You need to be a super-user.
I know that u can do super-user things in terminal by using sudo in front of the command. But how do i run this file in terminal?

Plz help.

Ty

---

### Post by Bablefish on 2009-02-10
You can get the driver here

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

They have links to install instructions

---

### Post by Klitsie on 2009-02-11
> **Bablefish said:**
> You can get the driver here

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

They have links to install instructions

I know that i can download it there.
And i have read the install instruction, but it doesnt make sense to me.
So anybody knows how to run an .run file while in terminal.
What is the command for that?

---

### Post by utnubuuser on 2009-02-11
.run?  Wrong file type.  You're looking for a .deb or tar.gz.

---

### Post by zika on 2009-02-11
> **utnubuuser said:**
> .run?  Wrong file type.  You're looking for a .deb or tar.gz.
no, it is not the wrong type.

```
[COLOR=Red]open Terminal[/COLOR]
cd [COLOR=Magenta]wherever You've DL-ed the file[/COLOR]
sudo chmod +x ati-driver-installer-9-1-x86.x86_64.run
sudo sh ati-driver-installer-9-1-x86.x86_64.run
aticonfig --initial -f
[COLOR=Lime]reboot[/COLOR]
```

---

### Post by Klitsie on 2009-02-11
> **zika said:**
> no, it is not the wrong type.

```
[COLOR=Red]open Terminal[/COLOR]
cd [COLOR=Magenta]wherever You've DL-ed the file[/COLOR]
sudo chmode +x ati-driver-installer-9-1-x86.x86_64.run
sudo sh ati-driver-installer-9-1-x86.x86_64.run
aticonfig --initial -f
[COLOR=Lime]reboot[/COLOR]
```

Ty,
the file is on my desktop. Wich path is that?
I am a newb, i know.

---

### Post by zika on 2009-02-11
```
cd ~/Desktop
sudo chmod +x ati-driver-installer-9-1-x86.x86_64.run
sudo sh ati-driver-installer-9-1-x86.x86_64.run
aticonfig --initial -f
[COLOR=Lime]reboot[/COLOR]
```

---

### Post by Klitsie on 2009-02-11
> **zika said:**
> ```
cd ~/Desktop
sudo chmode +x ati-driver-installer-9-1-x86.x86_64.run
sudo sh ati-driver-installer-9-1-x86.x86_64.run
aticonfig --initial -f
[COLOR=Lime]reboot[/COLOR]
```
I get this message:
Sudo: chmode: command not found 

Ty for the reply

---

### Post by zika on 2009-02-11
```
cd ~/Desktop
sudo chmod +x ati-driver-installer-9-1-x86.x86_64.run
sudo sh ati-driver-installer-9-1-x86.x86_64.run
aticonfig --initial -f
```
sorry one "e" too much ... ;)

---

### Post by Klitsie on 2009-02-11
> **zika said:**
> ```
cd ~/Desktop
sudo chmod +x ati-driver-installer-9-1-x86.x86_64.run
sudo sh ati-driver-installer-9-1-x86.x86_64.run
aticonfig --initial -f
```
sorry one "e" too much ... ;)

it now sais:
chmod: cannot acces 'ati-driver-installer-9-1-x86.x86_64.run' : No such file or directory 

I tried it couple of times, even with ~/desktop/ in front of it.

---

### Post by zika on 2009-02-11
change the name of the file (of course) accordingly. beware "Desktop" has the capital "D" in front.

```

cd ~/**D**esktop
sudo chmod +x **the_name_of_the_file_that_You_have_downloaded**.run
sudo sh ati-driver-installer-9-1-x86.x86_64.run
sudo aticonfig --initial -f
```

---

### Post by Bablefish on 2009-02-11
Install instruction link

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat91-inst.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat91-inst.pdf)

I would advise you to make a copy of it.

---

### Post by projectbronco on 2009-02-11
Hey thanks for this thread, this info helped me get past my installation woes.

---

### Post by Klitsie on 2009-02-19
HI,
Installed worked

But now i cant change anything.
When i open Catalyst Control Center (CCC)
I get this error message:
Initialization error
There was a problem initializing CCC Linux edition. It could be caused by the following.
No ATI graphics driver is installed, or the ATI driver is not functioning properly. Please install the ATI driver apropriate for you ATI hardware, or configure using aticonfig.


I dont know what to do now :/
Plz help, ty

---

### Post by zika on 2009-02-20
> **Klitsie said:**
> HI,
Installed worked
But now i cant change anything.
When i open Catalyst Control Center (CCC)
I get this error message:
Initialization error
There was a problem initializing CCC Linux edition. It could be caused by the following.
No ATI graphics driver is installed, or the ATI driver is not functioning properly. Please install the ATI driver apropriate for you ATI hardware, or configure using aticonfig.
I dont know what to do now :/
Plz help, ty
```
sudo aticonfig --initial -f
```

---

### Post by Extol on 2009-02-20
blix@blix-desktop:~$ aticonfig --initial -f
Data incomplete in file /etc/X11/xorg.conf
	Device section "Configured Video Device" must have a Driver line.
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Data incomplete in file /etc/X11/xorg.conf
	Device section "Configured Video Device" must have a Driver line.
Segmentation fault


I get this message in the last step.

This one:

 aticonfig --initial -f

---

### Post by bustherh on 2009-02-20
I had much better luck with the open source ATI drivers. Download with synaptic package manager.

---

### Post by Klitsie on 2009-03-12
I did the aticonfig --initial -f.
Then got this in terminal:
Uninitialised file found, configuring.
Using /etc/x11/xorg.conf
Saved back-up to /etc/x11/xorg.conf.fglrx-0

Catalyst Control Center still gives me the same error message :/

How can this be solved?

---

### Post by Bloemetjesgordijn on 2009-03-12
Did you do: sudo aticonfig --initial -f

Cheerz

Bloemetjesgordijn

---

### Post by methoxyroxy on 2010-05-11
Hi, 

I get this message too:
*There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following. No ATI graphics driver is installed, or the ATI driver is not functioning properly. Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.*
 

when I do the 
sudo aticonfig --initial -f
it says
No supported adapters detected

What does that mean? Did I get the wrong driver?
I'm working with a Lenovo T42 and Lucid Lynx, did not have problems with Karmic (which was the first linux distro I have ever used)

Also, what does this do: 
sudo chmod +x

Thanks for helping!
~Roxy

---

### Post by angrymeat on 2010-05-11
I got the same error until i rebooted after installing the drivers .

---

### Post by erchinoald on 2010-07-18
> **methoxyroxy said:**
> Hi, 

I get this message too:
*There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following. No ATI graphics driver is installed, or the ATI driver is not functioning properly. Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.*
 

when I do the 
sudo aticonfig --initial -f
it says
No supported adapters detected

What does that mean? Did I get the wrong driver?
I'm working with a Lenovo T42 and Lucid Lynx, did not have problems with Karmic (which was the first linux distro I have ever used)
I'm having the same issue, I get 'no supported adapters detected' with this command. Any suggestions? Am also using Lucid Lynx.

---

### Post by srlake314 on 2011-04-07
Ok major issues. So I try to navigate to the directory and I keep getting errors no such file or directory exists, and yet there it is.
I use the command 
cd downloads nothing
cd~/Desktop nothing

I have tried all sorts of configurations. All I want to do is follow the instructions on the ATI website b I cant even get to the danged directory to even access the file in terminal.

Come on this is getting nuts!

---

### Post by srlake314 on 2011-04-07
ok so the steps that the pdf file from ati says "
To install the ATI Proprietary Linux driver using the Automatic option, follow
these steps:
1 Launch the Terminal Application/Window and navigate to the ATI Propri-
etary Linux driver download.
2 Enter the command sh ./ati-driver-installer-8.573-x86.x86_64 to launch the
ATI Proprietary Linux driver installer.
The ATI Proprietary Linux Driver Setup dialog box is displayed
It shows the ati with the penguin.  Mine doesnt show that for the file:
"ati-driver-installer-11-3-x86.x86_64.run

This is the driver that I got from the website.  But Im still having issues with Wow not working or recognizing that I have a great card (XFX HD 4770).

Please, I am sick of scrolling through hundreds of pages trying to get functions to work.

Sean

---

### Post by srlake314 on 2011-04-07
Forgot to mention.
Ok major issues. So I try to navigate to the directory and I keep  getting errors no such file or directory exists, and yet there it is.
I use the command 
cd downloads nothing
cd~/Desktop nothing

I have tried all sorts of configurations. All I want to do is follow the  instructions on the ATI website b I cant even get to the danged  directory to even access the file in terminal.

Come on this is getting nuts!

---

