---
title: "Installing software...............HELP!"
date: 2008-08-09
forum: General Help
---

### Post by Chris62 on 2008-08-09
Hi,

I would be very grateful if someone would help with this problem. I have only been using Ubuntu for a short time and am still 'feeling my way' around it, so perhaps this is a very naive question

I have been trying to install Ubuntu 8.04 on a pen drive or memory stick using a live CD and the method described at [www.pendrivelinux.com](www.pendrivelinux.com).

At one point in the procedure it has to connect to the internet to download 'syslinux' amd 'mtools'which are then installed in the appropriate place on the pen drive. Unfortunately I cannot connect to the internet when using the live CD because, I have just discovered, I am using a USB ADSL modem and, apparently, Ubuntu doesn't "like" them. Even if I could find out what to do about the modem I can't access the Network manager because Ubuntu says that I am not 'allowed' to. The computer that I am using to do this is a friend's Windows machine and I don't want to make any changes which might cause problems for him later on apart from the fact that I don't know what changes to make in order to get Ubuntu using this modem.

I have downloaded 'syslinux'and 'mtools' as .deb packages using Windows and have transferred them to another pen drive with a view to putting them on the Ubuntu desktop when the live CD is running. How do I then install these packages onto the pen drive?

Presumably once Ubuntu is properly installed on the pen drive I will be able to find and install drivers to make the Sagem Fast 800 ADSL modem acceptable to Ubuntu?

Any help would be gratefully received.

---

### Post by zxscooby on 2008-08-09
can you install it on the usb drive using your computer?
then you can find out what drivers are required for the usb modem, install them , and then run it on your friends computer.

---

### Post by Chris62 on 2008-08-09
Thanks for your reply, zxscooby. No, I can't because Ubuntu isn't properly installed yet on the pen drive. I already have the modem drivers but can't install them on the pen drive because I don't know how to install syslinux etc and finish the Ubuntu installation and then install the modem driver

---

### Post by dexter.deepak on 2008-08-09
while using the live cd, open a terminal and type:
```
gksu nautilus
```
in this new nautilus instance, you can navigate to where your debs are.
and now you can install them by double-clicking.
the installation will be on the live cd,and not your pen-drive, and this is what the tutorial wants you to do.:)

---

### Post by dexter.deepak on 2008-08-09
> **Chris62 said:**
> Hi,

Even if I could find out what to do about the modem I can't access the Network manager because Ubuntu says that I am not 'allowed' to.
for this problem, you can type this in terminal :
```
sudo network-admin
```

---

### Post by Chris62 on 2008-08-09
Hi dexter.deepak,

I have probably misunderstood you but what is the point of installing syslinux to the live CD, and how can it be done? Surely it needs to be on the pen drive? If you have looked at the link that I gave in my initial posting, I had got to step 13 (sudo apt-get install syslinux mtools) and was unable to proceed because of getting error messages which I thought were the result of not being able to connect to the internet.

That's why I thought that I could put the .deb packages which I downloaded using windows, which does connect to the internet,on the desktop when the live CD was running and then somehow install them onto the pen drive. Am I barking up the wrong tree completely?

---

### Post by dexter.deepak on 2008-08-09
> **Chris62 said:**
> Hi dexter.deepak,

I have probably misunderstood you but what is the point of installing syslinux to the live CD, and how can it be done? Surely it needs to be on the pen drive? If you have looked at the link that I gave in my initial posting, I had got to step 13 (sudo apt-get install syslinux mtools) and was unable to proceed because of getting error messages which I thought were the result of not being able to connect to the internet.

That's why I thought that I could put the .deb packages which I downloaded using windows, which does connect to the internet,on the desktop when the live CD was running and then somehow install them onto the pen drive. Am I barking up the wrong tree completely?

when i say "installing on the cd" , it doesnt mean that you are "writing" that stuff on your cd...you are just installing the .debs on the virtual filesystem being presented by the cd (which is currently on your ram).
this means that the softwares you install using the live cd, is actually installed on the live-cd filesystem, and will get erased as soon as you eject the cd.
now the point is...why do we need to install these debs on the live-cd ?
because these are some tools necessary for the installation procedure, and the tutorial you are following probably will use this files from your installed directory.
i hope things are  clearer now :)

---

### Post by Chris62 on 2008-08-10
Thanks dexter.deepak,

As you can see I haven't really got to grips with Ubuntu yet, but thank you for all your time and trouble. No matter what I do, I just cannot install the debs onto the live CD. I have them on a spare pen drive and double clicking them does nothing. Right clicking produces an option to use Archive Manager so I tried that and when asked where I wanted them extracted I tried "Desktop" and when that didn't work I tried the CDROM which didn't work either so I then transferred the debs to the desktop and tried installing from there with no success
I don't really understand what is going on because the last deb file I used was on a computer with Ubuntu installed on its HD and I just downloaded the file which was placed on the desktop and I double clicked it and it was installed - much better than Windows I thought (at the time).

Anyway, I think I have taken up more than my fair share of your time so I will say "thanks for your help" and flounder along in the dark for a while!

Regards,
Chris

---

### Post by dexter.deepak on 2008-08-10
i am sorry to hear that, probably ubuntu doesnt have gdebi (the program wich helps installing by double-click) installed by default.
you can open up a terminal, and try :
```
gdebi
```
to see if it is installed or not.

for the current problem,i dont know if it will work, but you can place the debs in this folder : "/var/cache/apt/archives/ " ...you have to use sudo for copying.
now in a terminal , type:
```
sudo apt-get install syslinux mtools
```

---

### Post by vjkeito on 2008-08-10
i would download this using a PC connected to the web [USB ADSL Modem Manager for Gnome]("http://www.squeezedonkey.com/wiki/linux/index.php?title=Main_Page").

then install onto Ubuntu either by transferring using the flashpen or cd.

then install and you should be able to connect using ubuntu then.

after that continue with the guide.

---

### Post by vjkeito on 2008-08-10
when using the live-cd you have a set amount of memory allowed for you to use, thus meaning you can install packages using ubuntu (no packages get written to the CD obviously, they get written to RAM).

if you are using a cheap flash pen then make sure you follow the procedure to update the boot sector using LILO otherwise it may not boot.

lastly, remember to set the usb to boot in you BIOS!

good luck!

---

### Post by Chris62 on 2008-08-10
Thanks dexter.deepak,

I thought that I was beginning to get somewhere in that I got the debs into /var/cache/apt/archives from the USB drive using nautilus but typing "sudo apt-get install syslinux mtools" drew a blank. The system said it could not find the files so I changed to that directory and tried from there but it still wouldn't work; it still said it couldnt find the file. As a last resort I tried again, giving the full deb name and that wouldn't work either.

I am going back to France to my own computer next week and I think I will leave it until then to try anymore. The problem stems from the fact that this computer can't connect to the internet when the live CD is running

Thank you too, vjkeito, I will leave your suggestion until next week as well. I will still need to be able to use a USB ADSL modem for when I go to the UK (or "Gordon's Gulag" as I recently heard the UK described) again

---

