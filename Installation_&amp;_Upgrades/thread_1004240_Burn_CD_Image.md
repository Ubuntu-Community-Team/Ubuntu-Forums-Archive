---
title: "Burn CD Image?"
date: 2008-12-07
forum: Installation &amp; Upgrades
---

### Post by Camaro on 2008-12-07
Hi all,

I'm VERY new to Linux/Ubuntu, and I honestly have no idea what I'm doing when it comes to this OS that I've heard nothing but good things about.

Anyway, I have a very simple question regarding tbe ISO image. It is 698MB on disk, and I have a CD-RW that I'm trying to write it to that only has 655MB of space. How exactly would I go about burning this image? Is there another version of Linux I could download that would fit on this CD? Could I somehow compress it and keep the files needed to install intact? Simply put, I don't have the time or money to go out and buy a CD-R/RW that has enough space to burn it to.

Also, the reason I plan on using Ubuntu is because, and correct me if I'm wrong, I read that it can boot from an external hard drive connected through USB? Or perhaps it's some other version of Linux that I have to use?

Thanks in advance. Sorry if I've asked questions that have already been answered. I am quite desperate and frankly don't have time to sift through FAQs or google searches.

---

### Post by taurus on 2008-12-07
If you don't want to spend the money to get the 700MB CDR, then request a free Ubuntu CD!

[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

---

### Post by Camaro on 2008-12-07
Thanks, but I already did that. I'll look forward to it in 6 weeks. For now, I NEED a computer for multiple reasons, and I basically need it *now*. Any other help is appreciated

---

### Post by inobe on 2008-12-07
thought this would be useful to you .

i hope its helpful, the link contains many methods that will install ubuntu without a cd.




[https://help.ubuntu.com/community/Installation#Installation%20without%20a%20CD](https://help.ubuntu.com/community/Installation#Installation%20without%20a%20CD)

---

### Post by inobe on 2008-12-07
this may also help you with the external drive, the link contains flash drive information too, just follow what applies to you.

[http://ubuntuforums.org/showthread.php?t=1004240](http://ubuntuforums.org/showthread.php?t=1004240)

---

### Post by falcon61102 on 2008-12-07
Also, if it's a CD-RW, can't you remove what's on the CD temporarily and then burn the ISO onto the CD for the install?

EDIT: And yes, you can run Ubuntu completely off an external or USB flash drive.  Takes a little bit longer to load some things but other than that, once you have it set up it runs great.

---

### Post by Camaro on 2008-12-07
Thanks Inobe, I will look through those links and see what works best.

Thank you Falcon for your response, but I already deleted everything on the CD-RW I have. It's absolute maximum capacity is 655MB. Per Inobe's link, I'm trying the mini image so it can download the proper files during install. Then I will try the other things as there seems to be plenty of options.

Thanks for the help. I will reply later, hopefully on my working computer, with how I got it to work.

---

### Post by Camaro on 2008-12-07
I have successfully installed and booted Ubuuntu, but it only started as a text based command line. I found a command to load the gnome gui, and after loading a bunch of files, it just stopped and turned off my monitor. I'm wondering if this is normal? Is it doing stuff in the background?

How do I get it to load the gnome gui automatically without going through the commmand line loadup?

Thanks again.

---

### Post by taurus on 2008-12-07
After logging in, run

```
sudo /etc/init.d/gdm start
```
to start the GUI login screen.

---

### Post by Camaro on 2008-12-07
I typed this command and I got a "command not valid" error. Perhaps gnome didn't install properly? If so, what is the command to install it?

---

### Post by taurus on 2008-12-07
```
sudo apt-get update
sudo apt-get install gdm
sudo /etc/init.d/gdm start
```

---

### Post by Camaro on 2008-12-07
The first two codes appeared to work properly, but when I do the third code, my monitor just shuts off like before when I typed startx. I'm starting to think I'm missing something here. I don't know if this is normal or what...it's starting to tick me off. I thought this would be easy but boy was I wrong

---

### Post by taurus on 2008-12-07
Try

```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm start
```

---

### Post by Camaro on 2008-12-07
Ok, I tried the whole process of installing ubuntu over again, thinking it would make a difference when I try to do the codes, but now I'm stuck at the screen where I'm trying to download the release file. It stays stuck at 0% and eventually says it can't download it. I know it's not the connection because I double checked the internet cable. Any ideas?

---

### Post by Camaro on 2008-12-08
Alright, I was able to write the ubuntu image to a DVD and somewhat install it. It had an ubuntu logo and a loading bar, but now it's back at a command line thing waiting for a command. It says:

[initramfs]

Now what do I do? I tried the sudo command and it says sudo not valid.

---

