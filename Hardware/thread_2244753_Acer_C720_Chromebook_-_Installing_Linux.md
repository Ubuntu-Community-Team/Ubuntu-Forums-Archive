---
title: "Acer C720 Chromebook - Installing Linux"
date: 2014-09-18
forum: Hardware
---

### Post by harry28 on 2014-09-18
I am new to the forum so not to sure if this is the write place for this thread.

Recently I purchased a Acer C720 Chromebook for college work. It is a great laptop and does pretty much everything that I want i to. However since I am studying computing, Java programming makes up a considerable part of the course. I found [this]("http://www.linux.com/learn/tutorials/764181-how-to-install-linux-on-an-acer-c720-chromebook") guide online on how to install Linux Ubuntu on the chromebook and it seems fairly easy to do so. However reading [this]("http://blogs.fsfe.org/the_unconventional/2014/04/20/c720-debian/") guide it says I need to remove the write protect screw in the laptop. Do I need to remove the write protect screw in order to install Linux?. Also will installing Linux void the manufactures warranty?.

---

### Post by endlessinstant on 2014-09-18
Your second link is for wiping the SSD entirely (thus completely discarding Chrome OS) and replacing it with a Linux distro, Debian in the case of the example.  The first link you post details using chrUbuntu which is a series of scripts that automates a dual-boot setup (so you can boot between Chrome OS and an Ubuntu partition).   

I personally use crouton, which is yet another script that does most of the work for you.   Crouton creates a virtualized environment and runs side-by-side with Chrome OS.  There are various technical/security based reasons why this is a bad idea but for a casual user it is fairly sophisticated.   [Here is a good tutorial]("http://chromespot.com/2014/01/29/how-to-install-ubuntu-chromebook-crouton/") on installing crouton.   If you plan to continue using Chrome OS, go with crouton or chrUbuntu.  If you want to forget Chrome OS, follow the instructions for wiping your drive and using SeaBIOS to install your own operating system

---

### Post by harry28 on 2014-09-18
Thanks for your reply. That's looks like an easy guide to follow to install linux. I do not want to get rid of Chrome OS entirely just incase I want to use it in the future so that seems the best way to do it. Also found [this guide]("http://chromeos-cr48.blogspot.co.uk/2013/10/chrubuntu-for-new-chromebooks-now-with.html") but I think the one you posted seems easier. Final question, reading forum posts apparently installing 12.04 Ubuntu, the touchpad will not work is this correct and shall I go with 13.10 instead?

---

### Post by endlessinstant on 2014-09-18
If you go crouton, I highly recommend either precise (12.04) or trusty (14.04) with Xfce.  

```
sudo sh ~/Downloads/crouton -r precise -t xfce
```
```
sudo sh ~/Downloads/crouton -r trusty -t xfce
```

Are your commands respectively.  The -e flag in the example that blog post provides is there to encrypt the chroot (aka the artificial environment the script makes) which you may want for security reasons.Your Acer is probably adequate for running Unity but I find it rather slow on my HP 14.  (by all means, try it! crouton is great for experimenting since pulling your setup apart and rebuilding it is as easy as running a couple commands with the script!).  Trusty in particular I have been quite pleased with as it required almost no babying out of the box.   (OTOH the Xfce Debian setup I am running ATM required a lot tinkering to get working) 

crouton installs a VERY minimal build of Ubuntu.  Just enough basic software to get you going.  Make sure to do this: 

```
sudo apt-get update
sudo apt-get install synaptic
```

from the terminal once you are up and running.  This will update apt (your command line package manager) and install Synaptic (a graphical package manager) from there you can use Synaptic to install all the utilities and things you might want, like the Ubuntu Software Center (though I stick with Synaptic on my HP 14) 

One fun trick - there are a lot of different targets you can install with the -t flag,  try chrome (this installs the chrome web browser out of the box inside your Ubuntu environment) you could do this ie with

```
sudo sh ~/Downloads/crouton -r precise -t chrome,xfce
```

You can do -t HELP to see a list of different stuff to add at install (this adds to setup time but can be quite useful for improving core functionality).

---

### Post by harry28 on 2014-09-18
Wow OK thanks, that explains alot. I think I may try to install Unity since I like the UI better but if that doesn't work then I will install xfce trusty 14.04 Will I have to install the trackpad and audio drivers manually or are they already installed? If I do have to install them, where do I get the packages from?

---

### Post by endlessinstant on 2014-09-18
Your trackpad and sound ~SHOULD~ work out of the box with Trusty and the latest version of the crouton script.  Both of these were issues in previous builds though so if you are having issues with either you will probably be able to find help if you google.   Linux doesn't use drivers in the same way that Windows does so its not really a matter of just installing a package to get everything going.  IE for my trackpad on my current Debian setup, I actually had to manually write a config file as root and store it in the right subfolder.   Though, again, there is direction for this kind of thing out there if something isn't working right.   

You can do 

```
croutonversion -u -d -c
```

 from inside Ubuntu on the command line.  This will automatically update the script without you having to go download crouton from the web again.  Then to update your chroot from Chrome OS's command line do

```
sudo ~/Downloads/crouton -u -n trusty
```

If you're having any kind of weird glitches like that make sure everything is up to date first as a fix could have been pushed out either by crouton or Ubuntu itself.  Like I said before, crouton actually runs side by side with Chrome OS (you can cycle between the two with CTRL + SHIFT + ALT + BACK or FWD) so sometimes getting something to respond right is as simple as snapping back to Chrome OS for a second and making sure IE sound is not muted.

---

### Post by harry28 on 2014-09-18
You have been a real big help thank you. I think I am definitely going to go ahead and install xfce 14.04 trusty along side chrome os (hope I have enough space since the ssd is 16gb) and see if I have any problems. Been looking and should be able to install Java SDK, compile and run Java programs shouldn't I with no issues?

---

### Post by endlessinstant on 2014-09-18
You will be fine.  Linux does not take as much space as you might imagine.  On my HP 14, I have two user accounts, both with offline sync enabled for Drive and various files stored locally, my Debian install (with lots of extras) and I still have 4 GB of space left on the SSD.   But I also have a 64 GB SD card that I use for most of my data (you can, BTW install to an SD card if you wish though I forget the exact process as I have not done it in awhile).   Chrome is very good about managing local data on the Chrome OS side if you work through Google Drive and offline sync the files you would like to have stored locally.  It does most of this syncing in the background with a minimum of slowdown as well.

---

### Post by harry28 on 2014-09-20
Thanks so much for your help. Managed to install Linux Ubuntu Precise with no problems. When I install XFCE, I had problems trying to install Java and whenever I ran the command to install Chrome, Linux would not boot from ChromeOS again for some reason. It runs really well, the trackpad, keyboard and audio worked with no problems and I didn't have to do anything. Installed Java JDK and can write, compile and run Java applications now. Running Wine has been a big help also since I can run Windows applications like Notepad++ with no issues. Finally, since my Acer C720 is only 16GB I though I would run into storage issues, however I still have ~6GB with ChromeOs and Linux installed side by side. Thanks again for your help!
[IMG]http://i.imgur.com/y79SiQ0.jpg[/IMG]

---

