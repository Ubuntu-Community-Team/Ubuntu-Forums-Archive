---
title: "Problems with ICH8 sound card"
date: 2008-02-19
forum: Hardware &amp; Laptops
---

### Post by LuisGMarine on 2008-02-19
Hello guys,

I recently installed ubuntu 7.10 on my toshiba sattalite laptop with the ICH8 HD family.
I've got sound.  The problem is that the sound quality is very poor and on top of that it comes in very low.  I've set the PCM and Alsamixer volume to the max setting with no improvement.  I've done my fair research around the forums and all the fixes most people post don't work.  Here is the output of this command if it helps,

[I]
sudo lshw -C multimedia[/I]


```

 *-multimedia UNCLAIMED  
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0



```

Please let me know if you need me to run and post other commands.  It's been a while since I last used linux and I'm not sure what things to run in this sittuation to help you guys better understand my hardware.

Thanks,

Luis :guitar:

---

### Post by LuisGMarine on 2008-02-19
I think I found a fix.  I the post where the guy asked to compile a new version of alsa, I got some errors on the utils but I skipped that whole part, and got sound to be loud as regular.

Here is the link, I hope this fixes a problem that seems a lot of people are having issues with.  Please post if this fix works for you guys or not!

[http://85.17.184.130/forums/index.php?showtopic=30750]("http://85.17.184.130/forums/index.php?showtopic=30750")

---

### Post by CompleteMike on 2008-04-17
Hello,

I have been struggling with this audio issue for a couple of days.  Your suggestions (from [http://85.17.184.130/forums/index.php?showtopic=30750](http://85.17.184.130/forums/index.php?showtopic=30750)) worked for me.  Specifically, I did this part from that page:

1. System-> Administration-> Synaptic Package Manager
2. settings at the top -> repositories -> updates -> tick gutsy backports close and reload as before.
3. Close Synaptic package manager then open a terminal,
4. sudo apt-get install linux-backports-modules-generic
Backports uses alsa 1.0.15rc3
then 
5. reboot
6. open a terminal and type
7. alsamixer
8. you should have sound

It worked for me on a Dell 1720 Ubuntu 7.10 install

Thanks so much!

Mike

---

