---
title: "linux + laptops + wireless = instant fail"
date: 2011-06-19
forum: Hardware
---

### Post by SeePU on 2011-06-19
I can't get wireless to work on my Acer Aspire 5002 laptop w/ wireless.  

Here's what happens:

One flavor of Debian - doesn't work at all...not detected whatsoever... this is NOT true Debian, though

Xubuntu - usb stick - loads fine... plugged in/wired... works - have internet

I KNOW what packages are needed - bcm4318 chipset - uses 'firmware-43-installer' and after that is installed, I'm good to go...

Not sure if a subsequent step is needed but I got to the point in which xubuntu shows nothing, no network manager, no internet/ethernet utility of any kind...  VERY ODD AND PATHETIC...SORRY!  IT'S TRUE!

So, I install wicd.  What else is there?   Network manager???

Wicd displays the available connections... so far, it's ok.  I don't know why mine is only 70% though... that isn't accurate at all... I'm right beside the router and connection.

Anyway, I try to configure the wireless connection and it fails... error message displays incorrect password... yeah, right!  

I DON'T THINK SO!  I check my router settings... making sure I haven't lost my mind... it's fine.

Sorry, the long story made short simply states... EPIC FAILURE WITH WIRELESS AND LINUX ONCE AGAIN!  

I am not sure what is to blame but a Broadcom wifi card almost always means PROBLEMS.  But, since the available networks were detected, I'm not sure what's going on.

This laptop I just obtained/acquired so I would like to get a Linux install on it if I can.  

If anyone knows or can recognize what is going on, please provide info!  I have had more success with my Thinkpad but it's not 64-bit and is a weaker laptop with defective hardware (issues).  I might not have any choice, though, if I can't figure out what's going on with the Acer.  

Any ideas?  Sorry for my tone... I thought this laptop would not be a problem for installing Linux on it.  I did use live media but still, that should not be an issue.  I have used wireless on other laptops configured via live media before.  

Help? :confused:

---

### Post by Peter09 on 2011-06-20
Should not be that bad in Ubuntu - have you checked the third party drivers application - it should detect your card and ask to download the driver?
 
What version O/S are you running?

---

### Post by SeePU on 2011-06-20
> **Peter09 said:**
> Should not be that bad in Ubuntu - have you checked the third party drivers application - it should detect your card and ask to download the driver?
 
What version O/S are you running?

Please check this thread.  It is more specific and has more info.

[http://ubuntuforums.org/showthread.php?p=10960719#post10960719](http://ubuntuforums.org/showthread.php?p=10960719#post10960719)

I also tried all the *buntus and same result in each.

I have researched the install for this b43 driver quite extensively so I'm at a loss of what is going wrong.   I only know one thing:  I really, really, really, really, really hate broadcom stuff.

:(

---

### Post by SeePU on 2011-06-20
A side note:

sudo apt-get install updates 

E: Unable to locate package updates..... LOL!!!!!!!!!!!!!!

Ubuntu thinks this is a package now?!?   WOW!

---

### Post by Yellow Pasque on 2011-06-20
> **SeePU said:**
> A side note:

sudo apt-get install updates 

E: Unable to locate package updates..... LOL!!!!!!!!!!!!!!

Ubuntu thinks this is a package now?!?   WOW!
*cough
```
sudo apt-get update
```
You might want to check syntax/spelling twice before ranting ;)

---

### Post by SeePU on 2011-06-20
> **temüjin said:**
> *cough
```
sudo apt-get update
```
you might want to check syntax/spelling twice before ranting ;)i tried that... Same output!

---

### Post by Yellow Pasque on 2011-06-20
Then you must be using a very different apt than the rest of the world. Maybe someone else can help you with that. Good luck...

---

### Post by Cheesehead on 2011-06-20
You might make progress if you troubleshoot methodically. You almost certainly won't make progress if you randomly shout and blame.

Don't make assumptions. Check and verify. Use the tools you have properly. Ask questions when you don't know. And document, document, document the steps you take, the questions/answers, and  the changes you make - human memory is fallible.

For example, how did you determine the chipset?
How did you determine the correct driver for that chipset?
Are you certain you downloaded the correct drivers? It's really easy to get the wrong ones.
Did the drivers install without error?
Did the drivers load?
Were there errors in dmesg?
Did the kernel create an interface?
Did the udev interface rules run?
Can you configure the interface manually?
Did you change any Upstart /etc/init/ config files or sysvinit /etc/init.d/ files or links?

---

### Post by Prikolchik on 2011-06-21
I don't really have any advice on how to get the card to work, but...

I had similar problems with Broadcom BCM94322SHM. Connection loss, had to wait 2 minutes for it to pick up wireless, installing drivers from manufacturer didn't help, intermittent problems. Ended up getting Intel 6200 card on ebay for $25 shipped. All my problems were over the moment I put the new card in :D I also got a significant boost in battery life due to better power management.

Is it worth paying $25 to put an end to the headaches? Hell yes.

---

### Post by SeePU on 2011-06-21
> **Prikolchik said:**
> I don't really have any advice on how to get the card to work, but...

I had similar problems with Broadcom BCM94322SHM. Connection loss, had to wait 2 minutes for it to pick up wireless, installing drivers from manufacturer didn't help, intermittent problems. Ended up getting Intel 6200 card on ebay for $25 shipped. All my problems were over the moment I put the new card in :D I also got a significant boost in battery life due to better power management.

Is it worth paying $25 to put an end to the headaches? Hell yes.Well, I would have replaced it if I could but it's an *integrated* wifi card.  

So, one is stuck with it unless you want to do some fancy soldering. ;)

Anyway, it's currently working for me (*knock on wood*) but I can't explain why.  Therefore, I don't consider the situation 'solved' per se.   More like, it's working but with* ;-)

---

