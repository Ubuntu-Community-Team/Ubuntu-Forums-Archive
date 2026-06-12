---
title: "Jaunty won't boot, i will die!!!!"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by Will4 on 2009-05-07
Hey any one,

i just upgrade from 8.04 to 9.04 and everything went well until i had the PC turned off. I mean, now when i turn it on it does not go further than boot splash. don't even let me see the "nice" log in screen. I have all my data there, not saved. Can any one please, tell me how to downgrade to my loyal 8.04 please? I don't want Jaunty any more. Just go back, please. May be once all bugs get SOLVED. 
I die first if i lose my data!! 

Please, help a so desperate soul. Any help will be very appreciated. 

"EYES"  XXXXXXX

IF YOU HAVE THE SAME PROBLEM, PLEASE DON'T POST HERE JUST TO TELL ME, BECAUSE OTHERS WILL SEE THIS THREAD ALREADY "TAKEN" OR ANSWERED AND WON'T EVEN CHECK. 
PLEASE, BE WELCOME TO POST HERE IS YOU HAVE THE SOLUTION. DON'T GET ME WRONG I AM JUST DESPERATE. THANK YOU SO MUCH.

---

### Post by taurus on 2009-05-07
You shouldn't jump from 8.04 to 9.04, bypassing 8.10 in the process.  And as far as I know, I don't think you can go back to hardy again once you have upgraded your machine to Jaunty.  One thing you could do is to boot your machine with Ubuntu LiveCD.  Then mount the partition(s) where you want to save your personal files and copy them to a second CD/DVD drive or an external drive.  Once you've done that, you can reinstall either hardy or jaunty again.

---

### Post by Will4 on 2009-05-07
Thanks Taurus,

But... will i be able to save the data in my home directory?? Like Documentation i had there!!!???

---

### Post by Kareeser on 2009-05-07
You should be able to. From the sounds of it, the Jaunty install completed, but it just won't boot.

Use the LiveCD to boot into a desktop environment, mount your hard drives (it should do that automatically) and copy everything onto a USB key or external hard drive.

---

### Post by Will4 on 2009-05-07
and what Ubuntu LiveCD??? 8.04 or 8.10 will work???

i don't have 9.04 yet...

---

### Post by Kareeser on 2009-05-07
Any Live CD will work, it is OS-independent.

We can try fixing Jaunty though... what is the error message that pops up when you try to boot up?

---

### Post by nawitus on 2009-05-07
In the Kernel selection menu ( the grub menu ), remove the splash word from boot options by pressing 'e'. That way you can see text print out and hopefully the error. Remove the word 'quiet' too.

---

### Post by Will4 on 2009-05-07
Thank you [Kareeser]("http://ubuntuforums.org/member.php?u=503906"),

Actually i will be glad to get a message popped up. It wont go further than boot screen.

the black screen with the Ubuntu and the line down loading the OS
even before it pops the log in screen

it stops there and nothing happens then. Stays so like for ever.

Thank you for helping, Any idea???

---

### Post by Kareeser on 2009-05-07
Follow nawitus' suggestions. Press "esc" on the GRUB countdown when your computer starts booting and edit the boot line like he suggests.

---

### Post by Will4 on 2009-05-07
OK Thanks then

your help is very much appreciated

---

### Post by albinootje on 2009-05-07
> **Will4 said:**
> i just upgrade from 8.04 to 9.04 and everything went well until i had the PC turned off. 
How did you do that upgrade ? From 8.04 to 8.10 first or not ?

I recommend booting from a Linux live cdrom or usb stick, and back up your /home first.

---

### Post by doas777 on 2009-05-07
boot off a live CD, mount your drive, and back up your content, via network,DVD-R, usb, partition transfer,  or whatever. 

this article describes backing up content off a dead windows instance, but should be eaisly converted to linux. 
[http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)

alternately, if you can get to the grub options screen, you can boot into recovery mode. if you manage to do that, copy '\var\log\dmesg.0' to a disk and post it here, so those more knowledgable than I may be able to diagnose your issue. while you're there you can back up your content.

when you rebuild, consider creating a seperate home partition (it's easy at install time), so that you can wipe out your os instance, without losing your data or desktop settings.
At install time:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

after install:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)



good luck

---

### Post by Egi_Power on 2009-05-08
Hi!

In Hardy when you boot up, if you press ***CTRL+ALT+F1*** during the splash screen you can see all the messages. That might help you to find where the boot process hangs. I think this combination works on any version of Ubuntu, but I'm not 100% on it.

Good luck sorting your problem out.

Take it easy.

Egi_Power

---

### Post by Zyma on 2009-05-08
Hi,
I did some googling and the problem may be due to the incompatibility of Intel integrated graphic chips with jaunty. Needless to tell that I experience the same problem and more desperate ( I am writing my thesis and all my fortran programs are stored there!)

---

### Post by maheshvs on 2009-05-08
I dloaded ISO image of 9.04 and burned it. however, it does not install. i have erased my hard drive after complete back up and expected no problems in installation. i can go into Live Environment, but unable to install. can anyone help?

---

### Post by Kareeser on 2009-05-08
Please start your own topic for your issue.

---

### Post by Will4 on 2009-05-09
Thank you so much [doas777]("http://ubuntuforums.org/member.php?u=451394")

I am seeing what you recommended now, about  looking into 
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition) and [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)


Thanks a lot again.

---

### Post by Zyma on 2009-05-10
Hi Will4!,

As you may remember from my previous post, I had exactly the same problem as yours. Now it is officially solved! 

How ?

Follow the instructions I got from coffeeaddict22 at:

[http://ubuntuforums.org/showthread.php?t=1152097&highlight=black+screen+login](http://ubuntuforums.org/showthread.php?t=1152097&highlight=black+screen+login)

in order to recover all your data.

Then go to:

[http://ubuntuforums.org/showthread.php?t=1123929&highlight=p%3D7068981&page=3](http://ubuntuforums.org/showthread.php?t=1123929&highlight=p%3D7068981&page=3)

post #29, if you want to know how to get rid of ubuntu. (You can do that in order to reinstall the version you prefer).

You will be shocked to see how easy it is!!

---

