---
title: "Help installing ubuntu on Dell 8400"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by slowMX5 on 2009-09-03
I'm new to ubuntu and struggling with the install. I am installing ubuntu on a fresh HDD in my old Dell Dimension 8400. I have the 2.5GB partition size problem but being new to the file system etc I've not been able to successfully change the partition size. Ubuntu can use the whole disk as it is a new install.

Would really appreciate the help as I'm keen to dip my toe into the world of ubuntu!

---

### Post by stlsaint on 2009-09-03
see [here]("http://ubuntuguide.org/wiki/Ubuntu:Jaunty") for full help on jaunty.

---

### Post by presence1960 on 2009-09-03
select use entire disk at the prepare disk spzce window.

---

### Post by slowMX5 on 2009-09-03
Thanks for the responses - appreciated.

I've just tried selecting use entire disk at the 4th step - the 'bar' below it is all orange and reserved for ubuntu 9.04. When the setup starts to format the disk it freezes as soon as it gets to 5%. I think this is related to this [problem ]("http://ubuntuforums.org/showthread.php?t=1232743")but I could not follow the instructions on how to repartition the disk properly.

The ubuntu link looks very useful once I have got past this formatting/partitioning problem but I did not see nay trouble shooting there?

Thanks for any help you can offer.

---

### Post by presence1960 on 2009-09-03
> **slowMX5 said:**
> I'm new to ubuntu and struggling with the install. I am installing ubuntu on a fresh HDD in my old Dell Dimension 8400. I
Would really appreciate the help as I'm keen to dip my toe into the world of ubuntu!

try the alternate text based installer. get it [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

---

### Post by slowMX5 on 2009-09-03
Thankyou - I'm downloading PC(intelx86) alternate install CD. I hope that is the right one.

Once downloaded I'll burn it and give it a go.

---

### Post by slowMX5 on 2009-09-03
Update: Well the disk partition formatting now gets to 33% before the setup crashes. I clearly do not understand how to set the partitions up to allow ubuntu to install properly. The issue appears to lie in my understanding of how to get around the 2.5GB partition size bug.

I was hoping, with a fresh HDD, that it would be simple case of letting ubuntus setup install the OS and then for me to download/install what software I required and have a play.

Perhaps I should come back to it tomorrow.

Edit: BTW is there a step by step idiots guide to getting around the 2.5GB bug? For someone migrating from Windows and unfamiliar with ubuntu?

---

### Post by presence1960 on 2009-09-03
If you are using the "use entire disk" option what does the 2.5 GB error have to do with it? maybe you are not expressing in clear terms what it is exactly you are doing. The 2.5 GB error only occurs when you use the install side by side option and fail to move the slider to allocate more disk space for Ubuntu.

---

### Post by slowMX5 on 2009-09-03
> **presence1960 said:**
> If you are using the "use entire disk" option what does the 2.5 GB error have to do with it? maybe you are not expressing in clear terms what it is exactly you are doing. The 2.5 GB error only occurs when you use the install side by side option and fail to move the slider to allocate more disk space for Ubuntu.


Hmmm, OK. It seems I may be a little mixed up then. I am trying to install Ubuntu on a fresh disk. I get past step 4, enter the required information and then when the install gets to formatting/setting up of the partition it falls over at 5% through. Simply freezes at that point and I have to power off the PC. I then tried the alternate CD and it got to 33% at the same stage before falling over.

Steve.

---

### Post by presence1960 on 2009-09-03
> **slowMX5 said:**
> Hmmm, OK. It seems I may be a little mixed up then. I am trying to install Ubuntu on a fresh disk. I get past step 4, enter the required information and then when the install gets to formatting/setting up of the partition it falls over at 5% through. Simply freezes at that point and I have to power off the PC. I then tried the alternate CD and it got to 33% at the same stage before falling over.

Steve.

OK, well that has nothing to do with the 2.5 GB bug in the installer. That is only when you choose the side by side option and fail to adjust Ubuntu's partition size by moving the slider. You have other problems

Look at [Boot Options]("https://help.ubuntu.com/community/BootOptions"). Scroll down to F6 and try some of those when you boot the Live CD.

P.S. it would help if you could post any error messages you may have received during the install.

---

### Post by slowMX5 on 2009-09-03
> **presence1960 said:**
> OK, well that has nothing to do with the 2.5 GB bug in the installer. That is only when you choose the side by side option and fail to adjust Ubuntu's partition size by moving the slider. You have other problems

Look at [Boot Options]("https://help.ubuntu.com/community/BootOptions"). Scroll down to F6 and try some of those when you boot the Live CD.

P.S. it would help if you could post any error messages you may have received during the install.

Sadly I don't have any error messages when it locks like this as I have force the PC to shut down by holding the power button - unless they are saved somewhere.

I will take a look at the link you have provided but, in the meantime here are the settings I have presently under the manual partition screen:

SCSI1 (0,0,0) (sda) - 160GB ATA Hitachi .....
#1 Primary 157.0GB 
#5 Logical 3.1GB F swap swap

If I hit finish with these settings setup displays a red screen saying:
No root file system defined.

Do my settings look OK or are they in need of adjusting.

I'll go and take a look at that link now. Thanks for the help and everyones patience.

Steve

---

### Post by presence1960 on 2009-09-03
> **slowMX5 said:**
> Sadly I don't have any error messages when it locks like this as I have force the PC to shut down by holding the power button - unless they are saved somewhere.

I will take a look at the link you have provided but, in the meantime here are the settings I have presently under the manual partition screen:

SCSI1 (0,0,0) (sda) - 160GB ATA Hitachi .....
#1 Primary 157.0GB 
#5 Logical 3.1GB F swap swap

If I hit finish with these settings setup displays a red screen saying:
No root file system defined.

Do my settings look OK or are they in need of adjusting.

I'll go and take a look at that link now. Thanks for the help and everyones patience.

Steve

Under the manual partition screen highlight the 157 GB partition and click Edit. Then set the parameters that show up. Use as -> choose ext 3 or ext4 filesystem, tick the format box and on mount point use the drop down and choose /.

Do the same for swap and for use as choose linux-swap. You won't have to do anything else for swap. Then proceed with the install.

---

### Post by slowMX5 on 2009-09-05
Just tried to setup the manual partitioning as you suggest and it gets to 33% in the Partitions formatting screen then stalls. Text under the red/blue bar is:
Creating ext4 file system for / in partition #1 of SCSI1 (0,0,0) (sda)....

I have also just tried to load windows XP. It gets to 100% of the formatting but then says formatting failed and that the HDD may be damaged. I have replaced the new HDD with another new HDD today and both Ubuntu and Windows continue to exhibit the same behaviour. i.e. no change. That suggests that it may not be the operating system or the HDD that is at fault. Do I have another hardware issue (if spo how can I determine what it is) or perhaps there is something particular to the Dell setup that is preventing successful installation?

I really want to get Ubuntu up and running, I'm quite excited about trying it out but, at present, I ma beginning to think that buying a new PC is in order and that will put me back with windows again as it'll be pre-installed.

TIA for any help.

Steve.

---

