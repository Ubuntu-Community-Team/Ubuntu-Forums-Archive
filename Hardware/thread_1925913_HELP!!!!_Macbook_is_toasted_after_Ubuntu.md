---
title: "HELP!!!! Macbook is toasted after Ubuntu"
date: 2012-02-15
forum: Hardware
---

### Post by DerpQuest1 on 2012-02-15
thanks for checking out my topic!

Here's my situation...
I clean installed my macbook pro 13" with UBUNTU. So it does not have OSX on it any more.

Now... I need OSX back on the laptop, the disc drive doesn't work so I am trying to use the remote install disc with a Ethernet cable and my desktop.

The problem is... when I hold option on start-up, and select the Apple installer option (which appears) the laptop simply boots into Ubuntu. 

I CANT FIGURE THIS OUT!!! 

please help would be so appreciated.

~thanks in advance

---

### Post by madvinegar on 2012-02-15
What boot option are you chosing ?

Also, you can try loading the iso of the OS in a USB stick (i.e. using Unebooting) and boot from USB.

---

### Post by DerpQuest1 on 2012-02-15
> **madvinegar said:**
> What boot option are you chosing ?

Also, you can try loading the iso of the OS in a USB stick (i.e. using Unebooting) and boot from USB.

im choosing the boot option for the shared disc. but it just ignores it and boots to linux. Also i have tried loading boot discs onto the flash drive. My pc can recognize them but the mac just wont

---

### Post by madvinegar on 2012-02-16
I think that the problem is that you have first to perform a format in the hard drive.
Probably Makintosh do not recognize the hard drive as it is in "ext" format instead of ntfs(?)

Can you perform a format in the hard drive using the Makintosh? Is there any such option? In other words, do not start directly the installation, _but first chose to format the drive_.
I have never used Makintosh so I do not clearly know what type of hard disk format they use/prefer. Is it ntfs like windoes?

If Makintosh do not have such an otpion you can do it through the live DVD of ubuntu (through Gparted), or any windoes DVD.

I believe that this will solve your broblem.

---

### Post by penguinv on 2012-02-16
> **madvinegar said:**
> I think that the problem is that you have first to perform a format in the hard drive.
Probably Makintosh do not recognize the hard drive as it is in "ext" format instead of ntfs(?)

Can you perform a format in the hard drive using the Makintosh? Is there any such option? In other words, do not start directly the installation, _but first chose to format the drive_.
I have never used Makintosh so I do not clearly know what type of hard disk format they use/prefer. Is it ntfs like windoes?

If Makintosh do not have such an otpion you can do it through the live DVD of ubuntu (through Gparted), or any windoes DVD.

I believe that this will solve your broblem.

But the OP said the disk drive does not work.

Ask Apple, best at the Genius Bar. They have been helpful except about getting linux ON it.  heh

---

### Post by madvinegar on 2012-02-16
> **penguinv said:**
> But the OP said the disk drive does not work.

Ask Apple, best at the Genius Bar. They have been helpful except about getting linux ON it.  heh

I think he means "the CD/DVD optical drive" when he writes "disk drive".

---

### Post by DerpQuest1 on 2012-02-16
THHANKS everyone for the responses. Just to clarify, YES the optical CD drive is broken. I have tried to format the hard drive in UBUNTU, but since im running ubuntu on said HDD, i cannot do this.The problem with trying to run a boot disc is that the computer simply boots to linux anyway. I tried using GRUB, and i can succsesfully boot to GRUB but i have no idea what to do after that.

---

### Post by madvinegar on 2012-02-17
> **DerpQuest1 said:**
> I have tried to format the hard drive in UBUNTU, but since im running ubuntu on said HDD, i cannot do this.

This is because your drive is mounted. In order to be able to format your drive it must be unmounted. You can do this by using the live DVD of ubuntu. Insert the DVD, reboot, and in the options chose "boot to live DVD". After you login to the live desktop use Gparted to format the drive.

(You can also download Gparted and create a live cd/usb from here [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) )


As I said, I don't know if same can be done by using the DVD of OSX. When you boot with OSX, do you get any list of options? Apart from the installation option, do you see anything else like "format drive" etc?

If not, do as I explained above with the live DVD of ubuntu, or the live CD of Gparted to format the drive.

---

