---
title: "USB locks up after 15mins ????"
date: 2007-05-10
forum: Hardware &amp; Laptops
---

### Post by derek45 on 2007-05-10
I installed 7.04 on my TOSHIBA M45-S165 laptop.  Dual boot.


After about 15mins,  my USB mouse stops working.  afterward, the touchpad still works.

I thought it was a mouse issue,  but today I had my USB thumb drive mounted,  and right after the mouse froze, I got a message telling me to eject my thumbdrive before removing it.
( I didn't remove it)

Any Ideas for this Newbie ?

Thanks in advance.

---

### Post by derek45 on 2007-05-27
anyone? , anyone?,  .....Bueller?,   . . . . . . Bueller?

---

### Post by mattmyers83 on 2007-05-29
I am having the same issue with my toshiba a105-s171 laptop.  I have a logitech usb mouse, after 15 minutes of using it, it will stop working and no USB device will work until I reboot.

---

### Post by mattmyers83 on 2007-05-29
Can someone help us look in the right direction?  How do i submit a bug?

---

### Post by octathlon on 2007-05-29
I also have a Toshiba Satellite M45, ATI graphics, with the same exact problem, USB works at first then in a few minutes stops working.  I'm using the Feisty live CD.  Obviously no point in installing until the problem is solved.  

After searching, I see there are a lot of threads describing this problem, but none seem to have an answer.   I've been using Dapper on my Desktop for a long time, but haven't had problems before this, so I don't know how these thing work.  Is there a bug report filed on it?  Do I need to keep rechecking all these threads to see if an answer is found or what??  Is there any more info I could post that would help?

---

### Post by mattmyers83 on 2007-05-29
From what I gather everyone who is using the el cheapo Realtek audio AC97 + ATI mobile graphics card and ati northbridge is having this issue.  Laptops that use this combo are Toshiba, Compaq, and some gateway machines.  ACPI errors seem common with this as well.  Where do I go to submit a bug, and what info do I need to submit to fix this error.  FYI I was able to fix my sound issue with the ac97 by physically removing my modem card in my toshiba laptop.  Then updating to the latest kernel via Ubuntu Updates.

---

### Post by derek45 on 2007-05-29
Well,  at least I'm not alone.

:-|


I had zero trouble installing 6.10 on two different desktops.

I stuck the CD in the Toshiba, when everything seemed to work, including wi-fi, I went ahead and installed it.

I've changed GRUB  default boot to XP first.  I haven't had any luck finding a solution.

---

### Post by mattmyers83 on 2007-05-29
Glad to see im not the only one.  I thought I was going crazy for a bit.

---

### Post by octathlon on 2007-05-29
I don't seem to be having any problems with the sound, just the USB.

---

### Post by derek45 on 2007-05-29
> **octathlon said:**
> I don't seem to be having any problems with the sound, just the USB.

+1 

sound works fine.

---

### Post by octathlon on 2007-05-29
A little more info: I booted up the Edgy Live CD and had the same problem with the USB.  Then I booted up the Dapper Live CD and so far USB is still working after about 40 minutes.

Sounds played fine in all 3 versions, but since Matt mentioned there could be a relationship to the sound card, I tried Sound Recorder and couldn't get the microphone to work in any of them - tried both ALSA and OSS mixer, but I don't know enough about this to draw any conclusions.

As I said, I have been running Dapper on my Desktop, so maybe I should just go with that on the laptop. I just hate the idea of not being able to upgrade to the latest version and missing out on the new features. 

BTW, this same problem occurred on this laptop when I tried the Mint (based on Edgy) live CD also.  But it did not happen with the MEPIS live CD (v 6.5) .

---

### Post by derek45 on 2007-05-29
> **octathlon said:**
> A little more info: I booted up the Edgy Live CD and had the same problem with the USB.  Then I booted up the Dapper Live CD and so far USB is still working after about 40 minutes.

Sounds played fine in all 3 versions, but since Matt mentioned there could be a relationship to the sound card, I tried Sound Recorder and couldn't get the microphone to work in any of them - tried both ALSA and OSS mixer, but I don't know enough about this to draw any conclusions.

As I said, I have been running Dapper on my Desktop, so maybe I should just go with that on the laptop. I just hate the idea of not being able to upgrade to the latest version and missing out on the new features. 

BTW, this same problem occurred on this laptop when I tried the Mint (based on Edgy) live CD also.  But it did not happen with the MEPIS live CD (v 6.5) .

That's good info.
I'm running 7.04 now,  but if that would fix it, I'd uninstall it and run Dapper.

How does Dapper handle wi-fi?

(I arrived about the same time as Edgy, never had Dapper)

Thanks

---

### Post by octathlon on 2007-05-30
> **derek45 said:**
> 
How does Dapper handle wi-fi?

(I arrived about the same time as Edgy, never had Dapper)

Thanks

Dapper and all of them handle the wi-fi (Atheros AR5005G) with no problems, I just have to enter my WEP key (haven't tried WPA).  :)


What's ironic is that on Win XP which came pre-installed, I always have to turn off the Wireless Zero Config service after booting, or else it drops the wi-fi connection after a few minutes; then any time I resume from sleep or hibernate, I have to start and stop it again.

---

### Post by agentx on 2007-05-30
Try disabling USB Legacy support from your BIOS. Apparently there are some problems with this (and not only for ubuntu, it's a kernel issue).

---

### Post by mattmyers83 on 2007-05-30
I tried disabling USB Legacy support and still the same issue on my Toshiba a105-s171

---

### Post by mattmyers83 on 2007-05-30
On another note it seems having an external mouse hooked up is what is locking up the USB Bus.  I had a Microsoft external keyboard hooked up for hours with no issue.  But as soon as I hooked up a mouse and clicked anywhere from 25-45 times the USB bus locked up causing all connected devices to stop functioning.  It even sends a kill command to my external hard drive causing the drive to stop spinning and power off.  Very bizzar, If anyone knows what type of steps I can take maybe some logs to look at I would apreciate it because i am getting know where on this USB issue.

---

### Post by mattmyers83 on 2007-06-01
Has anyone found a solution to this problem yet?

---

### Post by derek45 on 2007-06-02
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Workaround_for_random_device_disconnections]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Workaround_for_random_device_disconnections")

---

### Post by derek45 on 2007-06-03
> **mattmyers83 said:**
> Has anyone found a solution to this problem yet?

I thought I had.  It ran over two hours last night with no trouble.
then today it locked up after 5 mins.:(

I'm in XP now :x

---

### Post by titus1950 on 2007-06-03
> **derek45 said:**
> I thought I had.  It ran over two hours last night with no trouble.
then today it locked up after 5 mins.:(

I'm in XP now :x

I did the "irqpoll" in "menu first" solution explained in the following thread,and usb mouse OK now, used to stop randomly after a few minutes.

[http://ubuntuforums.org/showthread.php?t=414152&highlight=irqpoll&page=2](http://ubuntuforums.org/showthread.php?t=414152&highlight=irqpoll&page=2)

---

### Post by derek45 on 2007-12-03
> **titus1950 said:**
> I did the "irqpoll" in "menu first" solution explained in the following thread,and usb mouse OK now, used to stop randomly after a few minutes.

[http://ubuntuforums.org/showthread.php?t=414152&highlight=irqpoll&page=2](http://ubuntuforums.org/showthread.php?t=414152&highlight=irqpoll&page=2)



I tried that,  and 10 mins later, my USB mouse locked up.:confused:

should I change it back,  or leave it?

---

### Post by derek45 on 2007-12-09
I must have got fat fingered. I tried this again,  rebooted, and my USB mouse has not locked up again.:guitar:

---

