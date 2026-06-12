---
title: "Cannot get Ubuntu (any release) to install."
date: 2009-06-07
forum: Installation &amp; Upgrades
---

### Post by Engleman07 on 2009-06-07
Hi, I am rather new to ubuntu and linux in general.  I have successfully installed the 32-bit version on my laptop and currently using it. But, when it comes to installing the 64-bit version on my desktop, which I built, it fails to install everytime.  I am using an AMD Anthlon X2 processor so that is fine and graphics card is more than capable and im using a IDE hard drive. it seems that every time i download a new .iso image it has 1 error.  I downloaded the 8.10 release last night and it comes it with no errors but when i go to install it doesnt get past the first screen.  I do not even get the screen to choose my language.  Does anyone have any help for me?  I have probably downloaded and burnt next to 15 iso's and none work.  not even my 32-bit version works.  This is beyond aggravating. Thanks for any advise folks!

---

### Post by mgt_90 on 2009-06-07
When you boot from the CD, choose the option to verify the installation media. That way we can know whether or not the installation disc is at fault or not.

---

### Post by merlinus on 2009-06-08
Did you burn the .iso as a disk image at a slow speed (4x or less)?

---

### Post by Engleman07 on 2009-06-08
Only for the 9.04 release do I get an error when running the test.  The same happens to Xubuntu 9.04 release.  However, when I run the 8.10 release it doesn't say there is an error during the test.  It does though when installing before it didn't but now it says input/output error on a black command screen.  

And, yes I burnt it as an image at 4x using InfraRecorder.

---

### Post by Kevbert on 2009-06-08
Have you performed a memtest86+ check via the CD boot menu ? It may be that you have some badly seated memory (Windows may still work, but crash occasionally).  You need to run this for a minimum of two full passes.

---

### Post by wpshooter on 2009-06-08
On which machine are you downloading and burning the ISO image, the laptop or the desktop ?

---

### Post by Pioden on 2009-06-08
Hi Engleman07,

I had the same trouble with my laptop - and just got it sorted :) Try using the 'alternative' download with the text based installer. That worked just fine for me and detected all the hardware perfectly (so far).

The text based installer is not nearly as scary as it sounds to most beginners. Just make sure your PC is connected to the net so it can download packages etc.

Best of luck

Huw

---

### Post by Villiam on 2009-06-08
BTW have you tried Wubi for installing Ubuntu. Check this out over her: [http://wubi-installer.org/](http://wubi-installer.org/)

[ubuntu]("http://www.linux-archive.org/ubuntu-user/")

---

### Post by sendblink23 on 2009-06-08
You don't really have to *check test the distro live cd.. f you burned it in your lowest possible speed,its certain the burning was a success (trust me I have burned over 40 different os iso's) and like you as well I also use Infra Recorder for those burnings.

BUT,,, Its trully really strange you can't install 64bit on your Rig
I had a Intel Pentium 4 that is 32bits, and pretty funny I can install 64bit Ubuntu with no issues... so its more odd your Rig being pretty advanced... that is not letting you install it

3 ideas I can give you burn 2 different versions of Ubuntu 64bits CD & DVD *LOWEST BURNING SPEED* (if they both fail on Installing)... here is the 3rd suggesting and pretty easy USB install ...  read here on this SAME *Area of the forum.. there is a recent installing Ubuntu from USB post with the instructions on how to create it with the live cd.

*UPDATE* tried searching for the thread of the USB method... but couldn't find it really weird when I read it a few minutes ago.. :(  well I hope the rest can help out

---

### Post by Engleman07 on 2009-06-08
Thanks for all the ideas guys, and to answer the question about which computer is downloading and burning them, it is the laptop.  The desktop does not have an operating system installed on it.  I have not tried the wubi installer for ubuntu, but i will definitely give it a try.  I am open to anything and everything on trying to get this to work.  Oh, and no i have not done the memtest on the live cd.  I have done the check disc for errors and that is it. I will also do that to make sure everything is working correctly.

---

### Post by wpshooter on 2009-06-08
> **Engleman07 said:**
> Thanks for all the ideas guys, and to answer the question about which computer is downloading and burning them, it is the laptop.  The desktop does not have an operating system installed on it.  I have not tried the wubi installer for ubuntu, but i will definitely give it a try.  I am open to anything and everything on trying to get this to work.  Oh, and no i have not done the memtest on the live cd.  I have done the check disc for errors and that is it. I will also do that to make sure everything is working correctly.

Have you considered the possibility that this is a problem with your CD drive.  Have you cleaned it recently ?  Have you tried another CD drive in the desktop to see if another CD drive will verify and then install Ubuntu from your burned CD ?

Have you checked to see that the "FIRMWARE" on your CD drive is on the latest version ?

---

### Post by Engleman07 on 2009-06-08
I have considered it and thought that was the case. The problem with that, is this.  I have no other CD Drive to switch in and out, and I don't want to spend money on a new one and it end up not being the problem.

---

### Post by Pioden on 2009-06-09
Have you tried installing the 32 bit version on your desktop? It would be interesting to know if that works.

---

### Post by Engleman07 on 2009-06-10
I have tried installing the 32-bit version and to avail it hangs during installation.  I'm assuming it is the CD drive. I have had some trouble with it in the past so I'm just going to throw another in there and hope that works. Thanks for all the ideas guys!

---

