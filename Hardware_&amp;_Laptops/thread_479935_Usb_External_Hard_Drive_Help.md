---
title: "Usb External Hard Drive Help"
date: 2007-06-20
forum: Hardware &amp; Laptops
---

### Post by cartooncartoon on 2007-06-20
hello 
i have been using the wubi install of ubuntu and kubuntu for the past couple days. im learing alot and really like what i have seen so far, but there are a few things that i just can't seem to get working no matter how many forums and manuals i read. the most important of those is the drive mounting which has me baffled. in ubuntu , all the drives seems to work just fine with out my intervention. on kubuntu i can't seem to get my usb external hard drives to work. 
all 12 drives on this system are NTFS, 2 are external usb, and there is about 4tb of data here that, i not only want access to , but i also don't want to lose data by doing something stupid in frustration or haste. 
so far im pretty sure i can see the drive when i do a fdisk -l ... and i opened the GUI in the system settings for drives and filesystems and the drive shows up there , and i was able to access the admin features one time ... now i can't push the admin button because it says i am not logged in as root which i can't seem to manage to do. also the drive shows up when i plug it in to the usb port and asks what i want to do with it and it says that it is an unmounted removable medium 

im runnin kubuntu 7.04 installed dual boot with xp 

please help me

---

### Post by moore.bryan on 2007-06-20
[I]first thing i'd try is installing hal and pmount, just in case they're not already installed:
```

sudo aptitude install hal pmount

```
then, you can use pmount to mount your external devices.  my external drive is always connected, so i use ivman (it's in the repos) to manage that stuff.  gnome-volume-manager is another and i'm not sure what kde uses.

typing "man pmount" in the terminal will give you a good idea on how to command it.  if you can spare more info, perhaps the community can better help...
[/I]

---

### Post by cartooncartoon on 2007-06-20
ok well that command didn't seem to work , it downloaded , and when i 

pmount sdc1 external

im not sure what more information you need , but im willing to offer any info that may be useful. remember ive only been using linux for like 3 days and am not familiar with the lingo or the commands

i still don't understand why when i log into the system settings i can see the drives , but then when i try to set the advanced options it tells me changes there require root access , isn't possible for me to set myself as the root somehow as im the only one using this ?

---

### Post by cartooncartoon on 2007-06-20
also , for example , i want to edit my xorg,conf and can't do that either cause it tells me everyting that i want to do i need to be root , is there a way to make me root just for a session so i can just make changes without having to do an hour of futile research everytime i want to make a change ? or is that just how it works , im sure that can't be correct and i don't have endless freetime , so i would like to make the most of what little i have

thanks

---

### Post by moore.bryan on 2007-06-21
> **cartooncartoon said:**
> ok well that command didn't seem to work , it downloaded , and when i 

pmount sdc1 external

im not sure what more information you need , but im willing to offer any info that may be useful. remember ive only been using linux for like 3 days and am not familiar with the lingo or the commands

i still don't understand why when i log into the system settings i can see the drives , but then when i try to set the advanced options it tells me changes there require root access , isn't possible for me to set myself as the root somehow as im the only one using this ?

> **cartooncartoon said:**
> also , for example , i want to edit my xorg,conf and can't do that either cause it tells me everyting that i want to do i need to be root , is there a way to make me root just for a session so i can just make changes without having to do an hour of futile research everytime i want to make a change ? or is that just how it works , im sure that can't be correct and i don't have endless freetime , so i would like to make the most of what little i have

thanks
[I]both of these seem linked to using "sudo."  if i want to run a command as root, but don't want to change into the root user (safer), ubuntu allows me to use sudo as the pre-command.  for example, if i wanted to install something, i can't type ```
apt-get install something
``` because apt-get requires root privileges.  instead, i have to use ```
sudo apt-get install something
``` and it will ask for my password and grant me temporary root access.  
for your external drive, why don't you try ```
sudo pmount /dev/sdc1
``` and post what, if anything, it responds.
sorry about not explaining more fully, i did forget you're new to linux; if no one has welcomed you yet, welcome!
why do you want to edit your xorg.conf?  have you tried ```
sudo dpkg-reconfigure xserver-xorg
```?
[/I]

---

### Post by cartooncartoon on 2007-06-21
ahhh ok i think im begining to understand , i knew about the sudo , but i think i just didn't know how to explain the question very well ... anyway i will try this once i get home [slackin off at work hah] thanks for your prompt response , im sure i will be making a **** ton of posts to the forum for the first little while. will post results here , thanks again

---

### Post by moore.bryan on 2007-06-21
*glad to hear you get a chance to "slack."  post with any questions which may arise; this is a fantastic community full of solid answers.  remember, though, linux is all about choices, so there will often be several different ways to "skin the cat."*

---

### Post by cartooncartoon on 2007-06-21
ok well i use the pmount command with sudo , and the drive shows up on my desktop but i get an error 
 
unable to enter file:///mediasdc1. you do not have access rights to this location 

and i think this might be related to my earlier problems , i never have rights for anything , is there some way that i can set myself to admin or root or whatever , or am i doing something wrong ?

---

### Post by moore.bryan on 2007-06-21
*hmm, that's a little weird.  which "flavor" of ubuntu are you using?  let me suggest a simple test... restart the computer with your external usb attached and post.*

---

### Post by cartooncartoon on 2007-06-21
i have kubuntu 7.04 , i installed it with that wubi thingy to make a dual boot along side my old xp 
 and yes i have restarted the pc a few times and tried a few things i have searched 
but so far , there are many many things that tell me i don't have rights for access

---

### Post by cartooncartoon on 2007-06-21
oh and i want to edit my xorg.conf file cause when i restart , my settings don't seem to be saving ... and i ran that automated thing , but i don't know all the correct answers and it would be easier for me to say for example , set the color depth to 24 there , cause i can't find anywhere else to set that where it will stay. i tried doing it in sudo nvidia-settings , but sometimes it works like if i want to run beryl , but sometimes the system won't boot and i have to remove and reinstall the OS .. :( but if i can get some of these major hurdles out of the way i think i can stop asking so many questions , its just hard when every time i want to change something , i don't have access rights

---

### Post by cartooncartoon on 2007-06-21
also haha sorry 

xander@ubuntu:~$ sudo nvidia-settings
Password:
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
xander@ubuntu:~$

not sure what thats about but im pretty sure that is also in that file xorg.conf

so many questions

---

### Post by moore.bryan on 2007-06-21
[I]okay... well, let's try one thing at a time.  for your mounting issue, try installing ivman:
```
sudo aptitude install ivman
```
and then restart you're computer, once again with the external drive attached.

for your xorg issue, it may be a nvidia issue... did you follow [this guide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Graphics_Card") to set things up properly?
[/I]

---

### Post by cartooncartoon on 2007-06-21
ok , once again , there is no way for me to know if it worked , there are the folder from my previous attempts , but when i go to click on the one i think is it , it tells access denied 
i guess i will give the xorg.conf thingy a go :(

---

### Post by moore.bryan on 2007-06-21
[I]what do you mean by folders from your previous attempts?  on your desktop should be something that looks like a drive or a usb symbol.  another weird issue.  what is in the /media folder when you look in it:
```
cd /media && ls -a
```
[/I]

---

### Post by cartooncartoon on 2007-06-21
and yes i have tried that guide and several others a few times each and never seem to get quite the same reusult , i can go to nvidia-settings and make changes , but that doesn't seem to solve the problem i have accessing everything im scared to try 1920x1200 , its kind of worked since i leave it on the low res , but im sure this can't be right

---

### Post by moore.bryan on 2007-06-21
*i don't use nvidia, so i'm sorry i can't help you out there... a quick look around this forum might show a couple of really good tutorials, like [this one]("http://ubuntuforums.org/showthread.php?t=432056&highlight=howto+nvidia").  but, like i wrote, i don't have/use nvidia.*

---

### Post by cartooncartoon on 2007-06-21
Unable to enter file:///media/sdc1. You do not have access rights to this location

that is what i get when i click the icon on the desktop , i think i might just reinstall and start over  :) 

thanks for all your help im sure i will be poppin up all the time here

---

### Post by moore.bryan on 2007-06-21
[I]i'm sorry none of the work-arounds actually worked.  :-(
if it makes you feel any better, i've reinstalled more times than i can count to get the system just the way i like it and, like many others around here, keep fooling around with it.  good luck.
[/I]

---

