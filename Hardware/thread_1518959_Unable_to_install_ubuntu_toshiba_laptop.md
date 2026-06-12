---
title: "Unable to install ubuntu toshiba laptop"
date: 2010-06-27
forum: Hardware
---

### Post by gjonatha on 2010-06-27
I recently purchased a toshiba laptop (satellite L515). I have tried to install ubuntu several times without sucess. I tried Ubuntu 9.10 32 bit, I restart and can see the first screen to install, but no matter if I choose the live cd option or install ubuntu, the screen goes black and nothing happens. I have waited for about ten minutes but there is no difference.
 I also tried Ubuntu 10.4, when I reboot the laptop, it goes to a black screen directly, and there are some messages, one of them is Kernal threat (I can get all of the messages if needed).

 Latop:
Toshiba Satellite L515
3Gig ram
Core I3
260Gig hard drive

 The laptop has windows 7 home premium which works great, but I do want to install ubuntu.

---

### Post by wilee-nilee on 2010-06-27
> **gjonatha said:**
> I recently purchased a toshiba laptop (satellite L515). I have tried to install ubuntu several times without sucess. I tried Ubuntu 9.10 32 bit, I restart and can see the first screen to install, but no matter if I choose the live cd option or install ubuntu, the screen goes black and nothing happens. I have waited for about ten minutes but there is no difference.
 I also tried Ubuntu 10.4, when I reboot the laptop, it goes to a black screen directly, and there are some messages, one of them is Kernal threat (I can get all of the messages if needed).

 Latop:
Toshiba Satellite L515

3Gig ram
Core I3
260Gig hard drive

 The laptop has windows 7 home premium which works great, but I do want to install ubuntu.

Although I use a dual boot set up you might consider a wubi install for now if you want to get going.

I think with a live cd you hit the f6 key repeatedly at boot to get a nomodeset to boot it if it is a graphic card problem, but if your new at this, this will only get you in and then if you install you will have to get the correct driver setup. If you get to the f6 prompt you choose the mode to run hit esc and enter. The nomodeset will get you in, in low graphics mode. If you get in run in the terminal.
```
lspci | grep VGA
```
This will identify the graphics set up post the results.

---

### Post by 23dornot23d on 2010-06-27
Have you had a look here ....... [Screen L515]("http://ubuntuforums.org/showthread.php?t=1283940")


Go to Post number 7 on this thread ....... it explains what setup to have in the xorg.conf file

sudo gedit /etc/X11/xorg.conf

Will get you into the file so that you can change it ..... 

Do a search on [your machine and Ubuntu Solved]("http://www.google.com/search?hl=en&q=Toshiba+Satellite+L515+linux+ubuntu&aq=f&aqi=&aql=&oq=&gs_rfai=") ........

---

### Post by wilee-nilee on 2010-06-27
> **23dornot23d said:**
> Have you had a look here ....... [Screen L515]("http://ubuntuforums.org/showthread.php?t=1283940")

Yah I wonder if it's a graphic problem, a screen resolution problem is a sign of that, and this can be difficult for a new user without some guidance.

---

### Post by gjonatha on 2010-06-30
Hi, thanks for your reply.

I just tried what you said, but I am still getting the same problem. I still cannot get in, I tried using the live cd, the wubi, and the installation directly, but I still cannot get in.

Just to confirm, I get to the ubuntu screen with the options to try ubuntu, install, and so on. I press f6 and choose nomodeset, select it and hit esc, then I select either try ubuntu or install.

Please let me know if there is anything else I can try.

---

### Post by gjonatha on 2010-06-30
I just got an update, I am not sure if it can be helpful.

 After installing the wubi, I chose to boot ubuntu, I got a screen waiting to boot ubuntu, I pressed esc and got several options: normal mode, safe graphics mode, etc. I chose acpi workaround and after that the installation went through successful, but after rebooting and getting into ubuntu again I get the same error I was getting before. I can get to the gnu grub and get the normal booting options, but when I chose one, the issue occurs again. If I hit esc while on the grub menu, I get a console, I am not sure if I could try something from there.

 Thanks again for your help.

---

### Post by gjonatha on 2010-07-05
Does anybody have an idea on how to solve this?

 Thanks.

---

### Post by AltomineUK on 2010-07-05
Hello there...

I'm afraid I can't get the full picture of your problem, so I will just ask a couple of questions. Please feel free to answer however you like :) 

1. Are you attempting a dual boot (using wubi) or would you like to have a Linux only machine?
2. Does it boot from the liveCD?
3. If you have installed your Linux OS on the partition, does your laptop load GRUB and allow you to boot Linux? 

4. Finally, if your answer to all the above questions is 'yes', does the Linux OS you have installed actually WORK?

---

### Post by gjonatha on 2010-07-05
1. I would like a Linux only machine, but if I could at least make the wubi work, that would be a progress.

2. No, I have not been able to get to the ubuntu desktop yet. When the cd starts booting, it goes to a black screen with 9.10 and gives me some errors with 10.4, always on a black screen.

3. I could get to the grub menu, but only using wubi. The only way to make the installation go through was.  while loading the cd and after installing wubi on the windows system, I hit esc, it gives about five seconds to do so, I get some options, normal mode, safe graphics, acpi workarounds, demo, and there is another one I do not recall at the moment. I can only make the installation go through if I choose acpi workarounds, I already tested them all. But after installing, when I choose ubuntu from the boot menu, I can get to the grub menu, but after the seconds to boot pass or you hit enter I get the exact same problem.

I also could see that if while on the grub menu you hit enter, you get some kind of console but I am not familiar with this one and do not know if it can be useful.

I have checked the cds, even install wubi using the daemon tools, but it has never gotten passed the black screen, it does not matter how long I leave it there.

I tried the workaround provided as noted on previous posts, but it did not work.

Thanks.

---

### Post by bcbc on 2010-07-05
> **gjonatha said:**
> I just got an update, I am not sure if it can be helpful.

 After installing the wubi, I chose to boot ubuntu, I got a screen waiting to boot ubuntu, I pressed esc and got several options: normal mode, safe graphics mode, etc. I chose acpi workaround and after that the installation went through successful, but after rebooting and getting into ubuntu again I get the same error I was getting before. I can get to the gnu grub and get the normal booting options, but when I chose one, the issue occurs again. If I hit esc while on the grub menu, I get a console, I am not sure if I could try something from there.

 Thanks again for your help.

When you chose the acpi workaround to install wubi, that was a one time override. You need to do that every time you boot until you can update your drivers to resolve the hardware issue you have.
So, when you choose Ubuntu, you see the grub menu. Instead of hitting ENTER, hit 'e' and go to the part where it says 'quiet splash'. Just add 'noacpi' there so it looks like 'quiet splash noacpi' and then CTRL+X to boot.

Then you can go to System, Administration, Hardware Drivers and see if there is a recommended driver for your system. If you can't sort it out there is a way to make the workaround permanent without editing grub each time, but better to find out what drivers you need.

---

### Post by gjonatha on 2010-07-05
Hi

 I just tried what you said, I made sure it reads as quiet splash noacpi. Then I get Booting a command list, and I get the same error again.
 I also tried ubuntu 9.10, but with that version the acpi workarounds does not work. I have been doing this testing with lucid 10.4.

 Any other suggestion would be appreciated.

 Thanks.

---

### Post by bcbc on 2010-07-05
> **gjonatha said:**
> Hi

 I just tried what you said, I made sure it reads as quiet splash noacpi. Then I get Booting a command list, and I get the same error again.
 I also tried ubuntu 9.10, but with that version the acpi workarounds does not work. I have been doing this testing with lucid 10.4.

 Any other suggestion would be appreciated.

 Thanks.

try 'nomodeset' instead of noacpi. That seems to work for most. It depends on your graphics card but I don't think you mentioned what it is.

---

### Post by gjonatha on 2010-07-06
Hi,

 I just did dual boot on my laptop. I tried nomodeset and it did not work, but I tried acpi=off, and that made the trick, right now I am posting from my laptop using lucid. 
 I tried looking for drivers as you suggested, but it does not find anything. I was also wondering if there is a way to set up this option by default to not have to do it manually all the time or if I can find drivers somewhere.

 Here is the output for lspci | grep VGA:
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)

Thanks :p

---

### Post by bcbc on 2010-07-06
> **gjonatha said:**
> Hi,

 I just did dual boot on my laptop. I tried nomodeset and it did not work, but I tried acpi=off, and that made the trick, right now I am posting from my laptop using lucid. 
 I tried looking for drivers as you suggested, but it does not find anything. I was also wondering if there is a way to set up this option by default to not have to do it manually all the time or if I can find drivers somewhere.

 Here is the output for lspci | grep VGA:
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)

Thanks :p

mmm... I thought noacpi was the same as acpi=off and you tried that earlier!

You can persist the setting by editing the /etc/default/grub file and changing it to read:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"

Then run ```
sudo update grub
```

But I think there are some features you'll miss. I'm not big on the different graphics cards, but some have used "i915.modeset=0" for intel cards. 

this website has some more info [http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

---

### Post by killer3010` on 2010-07-06
the issue he is having im having the same issue with my new Toshiba satellite L505 i have tried the live  disc and i get a kernal error im not sure if  it its the same issue Gjonatha is getting when i try to install Ubuntu i have gotten this problem with both the 32bit and 64bit version

---

### Post by bcbc on 2010-07-06
> **killer3010` said:**
> the issue he is having im having the same issue with my new Toshiba satellite L505 i have tried the live  disc and i get a kernal error im not sure if  it its the same issue Gjonatha is getting when i try to install Ubuntu i have gotten this problem with both the 32bit and 64bit version
This seems like a different issue with your bios...
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/472183](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/472183)

---

### Post by gjonatha on 2010-07-10
I just tried the workaround provided and it works fine. But as mentioned, there are some features I am missing, for instance the power management does not work and I am not sure if this is related but everytime I shutdown the pc, it gets stuck and manual shutdown is needed, I imagine there will be other features I will miss as well, I have not tested everything yet.

 I also checked the page for workarounds for this graphic card but neither of them worked. I was wondering if anybody knows if there is a way to get drivers for this card some where.

 I would also like to know if this is an issue specific with ubuntu not being compatible with this graphic card or with toshiba laptops in general, I have just heard too many issues concerning toshiba working with ubuntu.

 And finally, if this is an incompatibility issue, is there a hope this gets resolved in any future release?

Thanks for your help.

---

### Post by bcbc on 2010-07-10
> **gjonatha said:**
> I just tried the workaround provided and it works fine. But as mentioned, there are some features I am missing, for instance the power management does not work and I am not sure if this is related but everytime I shutdown the pc, it gets stuck and manual shutdown is needed, I imagine there will be other features I will miss as well, I have not tested everything yet.

 I also checked the page for workarounds for this graphic card but neither of them worked. I was wondering if anybody knows if there is a way to get drivers for this card some where.

 I would also like to know if this is an issue specific with ubuntu not being compatible with this graphic card or with toshiba laptops in general, I have just heard too many issues concerning toshiba working with ubuntu.

 And finally, if this is an incompatibility issue, is there a hope this gets resolved in any future release?

Thanks for your help.

I've searched on the web, and about all I could find is that your core-i3 is not supported by karmic 9.10, but should be supported in 10.04. The problems that people have had with 10.04 and intel graphics cards are (I believe) an older intel card. So it's puzzling.

I can only recommend detailed searches with your specific hardware and see if something turns up. But I'd expect to see a lot more posts on core-i3 chips if there was a problem with 10.04.

---

### Post by kspringer on 2010-07-10
No help here...  But here's my Toshiba story...

My sister has a nice Toshiba laptop and I wanted to see how it worked with Ubuntu. I decided to test it with my bootable persistent USB.
Never did get it to boot - at all.  It immediately froze up the computer and when she booted into windows again, it threw up an error I'd never seen before.  I had to "repair" the windows installation.

Needless to say, she wouldn't let me near her laptop anymore after it was fixed.

A couple of google searches revealed USB booting problems with Toshibas but it left a bad taste in my mouth.  They look really, really nice with Windows - but I'm staying away from Toshibas.  Sorry.

k

---

