---
title: "[B]  Super user??? [B]"
date: 2008-03-23
forum: Hardware &amp; Laptops
---

### Post by BillyBlaze on 2008-03-23
Okay I found the driver from ATI for my laptop. It was not a Synaptic application, but no big deal I already made the change in the respositories, and changed the permissions to execute the file as a program. 

Here's the catch. When I run the application witch ATI says it will create an installaion package. Ubuntu tells me I can only do this as super user. I've ran the application both in GNOME and Terminal, with the same result. I've used the SUDO command, and nothing

I'm so frustrated. How can I be the "SUPER USER" so that I can install my driver.?????????

---

### Post by Sam Lars on 2008-03-23
The usage is 
```
sudo command
```
If that's not getting you anywhere, where did you get this program?

---

### Post by BillyBlaze on 2008-03-23
I downloaded the linux driver from ATI. It has a nice instruction page on how to install the driver.

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat83-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat83-inst.html)

I type "sudo then the file, but it won't run. Says it's a bad command.

 Then I run the file from GNOME and it tells me I have to be the supper user.

 Finally I double click the file in GNOME and select "run in terminal". This at least starts the process, but again will tell me I have to do this as the "Super User"

I have used the SUDO command, but nothing.

---

### Post by Migoo on 2008-03-23
First you have to make the command executable like this:
chmod o+x  ati-driver-installer-8.3-x86.x86_64.run

Second you have to add the path to the command you want to execute. If you are standing in the same folder as ati-driver-installer-8.3-x86.x86_64.run is in you should type:
sudo ./ati-driver-installer-8.3-x86.x86_64.run

I hope this was what you where looking for.

---

### Post by BillyBlaze on 2008-03-23
Thanks for the reply. I typed the fist command you told me, but it just came back and repeated the command I typed in followed by "command not found".  I tried it both in just the root directory, and the folder that the downloaded file was in. 

Just for the heck of it I tried the second command, but came up with the same result. The command followed by "command not found". 

It has to be something easy I'm missing. I have used the (su -), and (sudo -i) commands to stay logged in as the "super user" but still nothing. 

root@wmanganaro-laptop:/home/wmanganaro/Documents/Downloads#

This is where the file is located. In the Downloads folder, but when I type a command it comes back telling me it's a bad command. 

root@wmanganaro-laptop:/home/wmanganaro/Documents/Downloads# ls
ati-driver-installer-8-3-x86.x86_64.run
root@wmanganaro-laptop:/home/wmanganaro/Documents/Downloads# 

This is an exact copy and past of what happens:

root@wmanganaro-laptop:/home/wmanganaro/Documents/Downloads# ls
ati-driver-installer-8-3-x86.x86_64.run
root@wmanganaro-laptop:/home/wmanganaro/Documents/Downloads# hmod o+x ati-driver-installer-8.3-x86.x86_64.run
bash: hmod: command not found
root@wmanganaro-laptop:/home/wmanganaro/Documents/Downloads#

---

### Post by aJayRoo on 2008-03-23
That is just because of a typing error. The command you need to use is called 'chmod'. Once the file is executable then second command should work.

---

### Post by BillyBlaze on 2008-03-23
Thank you I didn't catch that. Sadly I still have a problem. 

root@wmanganaro-laptop:/home/wmanganaro/Documents/Downloads# ls
ati-driver-installer-8-3-x86.x86_64.run
root@wmanganaro-laptop:/home/wmanganaro/Documents/Downloads# chmod o+x ati-driver-installer-8.3-x86.x86_64.run
chmod: cannot access `ati-driver-installer-8.3-x86.x86_64.run': No such file or directory
root@wmanganaro-laptop:/home/wmanganaro/Documents/Downloads# 

Now it tells me there is no such file or directory, but as you can see using the (ls) command It's right there. On my terminal it's in green. 

You think you may be able to shed some more light on this?

---

### Post by aJayRoo on 2008-03-23
Erm, yeah... Another typo perhaps! I think there is a dash between the 8 and the 3 not a period. You can use tab completion to avoid this issue. Simply type the start of the command and the first part of the filename then press tab and the shell will complete the filename for you, or offer a list of completions if more than one is available. Hope that helps.

---

### Post by BillyBlaze on 2008-03-23
Yea you were right. I made the correct and after a long painfull process I was able to get the driver installed. 

Only problem now is I have two monitors. The laptop screen, and a 24" lcd. I couldn't configure the resolution in console, so I did it with the catalist control center it gives you here in GNOME. Now I can only run one screen or the other. If I do run both the resolution is horrible. 

Man what a pain in the ---!

Thanks for the help.

---

### Post by Migoo on 2008-03-24
Why don't you take a look at xrandr. It's a small command that might help you to connect your laptop to external screens.
Here are a page that might help you:

[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)

I have a couple of very small scripts that I use when connecting my Dell D830 to for example a projector and so on. One example is this one:

#!/bin/bash
xrandr --output LVDS --mode 1680x1050 --output VGA --mode 1024x768 --same-as LVDS

The small script (command line) above makes sure the resolution on my laptop is 1680x1050 and the output to the projector, connected to my VGA port, has 1024x768 and the screen is cloned.

---

### Post by aJayRoo on 2008-03-24
you could try and use the command line tool called 'aticonfig'. I can't remember exactly how to do this, I think you should use:
```
sudo aticonfig --initial=dual-head
```
and then use:
```
sudo aticonfig --mode2=1680x1050
```
making sure to use the correct resolution for your second monitor. I'm not sure that these commands are precisely what you need but I think something along those lines should do it. To get a list of options for aticonfig use:
```
aticonfig --help
```
 Make sure you take a backup of your xorg configuration file before running these commands:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup-20080324
```
Also you will not be able to use two monitors like this if you are using the xgl xserver, if you don't know what that means then you won't need to worry about it! Hope that helps.

---

