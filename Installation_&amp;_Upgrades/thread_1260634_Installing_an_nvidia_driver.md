---
title: "Installing an nvidia driver"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by IAmNoodle on 2009-09-07
In an attempt to get rid of the constant high-pitched hum, I'm trying to install a driver for my graphics card (somehow the graphics card is related to the sound, or so I've been led to believe by my computer), so after much searching, I've finally found the relevant driver to download, and haver downloaded it, but now I can't seem to install it. Synaptic package installer doesn't want to know about it, and double clicking it results in confusing gpedit... Any ideas?

Cheers

---

### Post by MTGap on 2009-09-07
What is the graphics card chipset? Nvidia or Ati?

---

### Post by IAmNoodle on 2009-09-07
Nvidia

---

### Post by MTGap on 2009-09-07
Well I'm guessing you downloaded it from Nvidia.com, if so here is their readme: [http://us.download.nvidia.com/XFree86/Linux-x86/185.18.36/README/chapter-04-section-02.html](http://us.download.nvidia.com/XFree86/Linux-x86/185.18.36/README/chapter-04-section-02.html)

I highly doubt this will fix your problem, do you by chance know what driver you already using?

---

### Post by MTGap on 2009-09-07
> Well I'm guessing you downloaded it from Nvidia.com, if so here is their readme: [http://us.download.nvidia.com/XFree86/Linux-x86/185.18.36/README/chapter-04-section-02.html](http://us.download.nvidia.com/XFree86/Linux-x86/185.18.36/README/chapter-04-section-02.html)

I highly doubt this will fix your problem, do you by chance know what driver you already using?

Oops sorry that was weird, sorry for the double post.

---

### Post by IAmNoodle on 2009-09-08
> **MTGap said:**
> Well I'm guessing you downloaded it from Nvidia.com, if so here is their readme: [http://us.download.nvidia.com/XFree86/Linux-x86/185.18.36/README/chapter-04-section-02.html](http://us.download.nvidia.com/XFree86/Linux-x86/185.18.36/README/chapter-04-section-02.html)

I highly doubt this will fix your problem, do you by chance know what driver you already using?

Thanks for the link, I didn't know such a page existed. It's still left me just as bemused though. 

What does 
> 
After you have downloaded the file NVIDIA-Linux-x86-185.18.36-pkg#.run, change to the directory containing the downloaded file, and as the root user run the executable:
     # cd yourdirectory
    # sh NVIDIA-Linux-x86-185.18.36-pkg#.run
mean? I don't know what 'cd yourdirectory' is, and am I supposed to copy and paste the second line into the terminal? or both? :confused: I'm still pretty much a complete newbie to the linux experience

Also, I've just enabled one of the proprietary  drivers (downloaded from the list on synaptic, Nvidia) that has made a huge difference to the graphics, but the hum is still present

---

### Post by shred_eng on 2009-09-08
hi, ive installed nvidea drivers before and if youre totally new it isnt easy but not impossible either, so,
you downloaded drivers now go to the directory you downloaded them to, presumably 

/home/yournamehere , if so do this:

$cd /home/yourname
run the script...you might have to be root
sh NVidia-Linux-x86-185.18.36-pkg#.run
or  might be ....
./sh NVidia-Linux-x86-185.18.36-pkg#.run  
    
 but first you might have to shutdown xserver      (pretty certain you do or you get errors)

something like this: (at least it was on suse)
$telinit 3     
  
so i think youll end up in console, where you type the first lot of code (sh NVidia etc)
 follow instructions that appear in console.

see where that gets you, then come back if theres more probs

good luck:)

edit: just noticed you installed NVidia drivers, perhaps you should try replacing your souncard, or take one out of another old computer if you have one, to see if the hum goes away

---

### Post by RockDoctor on 2009-09-08
> **IAmNoodle said:**
> Also, I've just enabled one of the proprietary  drivers (downloaded from the list on synaptic, Nvidia) that has made a huge difference to the graphics, but the hum is still present

It's quite likely that the nvidia driver you installed via synaptic is actually newer than the driver you're trying to install manually. (Not at my desktop machine now, but I seem to recall that the last Karmic update installed a 190.xx driver.

---

### Post by IAmNoodle on 2009-09-24
YEEEEEEEEEEEEEEEEEEES! I've done it! I've solved the problem I've been having with the hum! It turns out the sound has absolutely bugger all to do with nVidia. Downloading OSS [http://www.opensound.com](http://www.opensound.com) and tinkering with the sound mixer settings (such as with mixer to use) as well as attempting to make use of Phono Gstreamer (whether or not that makes any difference, I don't know, but I've got it all working :D

Thanks for everyone's help

---

