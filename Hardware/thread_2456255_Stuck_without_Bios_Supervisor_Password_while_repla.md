---
title: "Stuck without Bios Supervisor Password while replacing laptop HD with Ubuntu HD"
date: 2021-01-07
forum: Hardware
---

### Post by 216ann on 2021-01-07
Hi, I am a noob who was given a newer laptop Toshiba L55 A5226 with a 5400 HD.
I had, what I thought was a clever plan at the time, to use my old laptop's 7200 HD with Ubuntu to replace.
Both HDs worked perfectly fine prior to the replacement.  
First, there was an error claiming no bootable drive when I tried to start the Toshiba.
I didn't know the bios password (and neither did my friend who had the laptop sitting in a garage for years) so I don't know how but I was able to get it to boot off a live ubuntu usb and "Try Ubuntu"
I was able to see the 7200 HD (so the HD hasn't crashed) and even able to copy some files but it kept giving me errors that I did not have root permissions to the HD.
I did have a password for root on the HD but I never seemed to have the opportunity to put that password in.  
I tried repairing the Grub per instructions here.
[https://www.howtogeek.com/196740/how-to-fix-an-ubuntu-system-when-it-wont-boot/](https://www.howtogeek.com/196740/how-to-fix-an-ubuntu-system-when-it-wont-boot/)
GRUB wasn't working so I repaired it 
[https://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/](https://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/)
Then I entered recovery mode & clean, dpkg fine.
system summary showed that several of the parameters were not matching but could not be fixed.
It all seemed to work except that fsck claimed that /dev/sda5 was mounted and so failed.
I did access root to try to fix and MAY have successfully unmounted sda5.
whatever I did, the system restarted.
Now, however, regardless of whether I press shift or other keys it goes to a screen with Toshiba splash as well as Ubuntu.  
But then the screen appears to freeze and I have left it there for an hour without progression.
when I try to turn off, some process seems to be running sda5 but can't see because it just flashes the info and just shuts off
the live USB ubuntu does not boot, and attempts to go to the bios are met with a claim I must put in the supervisor password or F11 to get limited access.
I have tried removing the bios battery for two hours and looked for but not found the "two contacts" that I must bridge to get the bios to reset.
I even tried this Ctrl then Tab then Ctrl then enter thing I saw on YouTube but it was not successful.  
So at this point I seem to only get to the Toshiba/Ubuntu screen or the Bios supervisor password screen.
Please advise.  thanks.

---

### Post by yancek on 2021-01-07
Exactly how old is this Toshiba?  There should be a way to reset to factory defaults or similar so you can set a supervisor password.

If you get no bootable drive, do you have the correct drive in the boot options of the BIOS? 
Does the old hard drive you put in the Toshiba get recognized in the BIOS?
If your old hard drive has Ubuntu on it, which release is it?

> I did have a password for root on the HD but I never seemed to have the opportunity to put that password in.   

Not sure what you're doing here.  Ubuntu uses sudo so there is no root user as such configured.  If you are booting from a USB/DVD, the default user is ubuntu and there is no password.  Your post indicates you are using some release of Ubuntu on a USB.

The first link you posted explains how to repair an installed system which from your post it seems you can not boot?
If you have boot repair on the Ubuntu USB, the best step to take to get help is to run boot repair and not try to repair but rather, select the option to Create BootInfo Summary.  When it finishes. it will give you a link you can post here to get help.

Which release of Ubuntu do you have on the hard drive?  The second part of your post seems to indicate that you are able to at least start to boot the installed Ubuntu, is that correct?

Run boot repair and post the link here.

---

### Post by crip720 on 2021-01-07
According to a fast google search, if bios or supervisor password is unknown, you have to send it to a toshiba service centre to change.  There was one link where if original drive unchanged, there is a reset partition on it, unknown if for bios.

---

### Post by 216ann on 2021-01-10
Thank you for your responses.
Sorry about the delay...I thought I replied but ended up sending an email to info @ ubuntuforums.org
Maybe 5yrs old.  I tried all the methods I could find on resetting the bios password (take out battery, ctrl/tab/ctrl/enter, use "Toshiba", etc) but none of them worked.
Yes, it is set to boot off that 7200 HD with Ubuntu 20.
Yes, the HD is recognized by bios and even that one time when I (I don't know how) got it to boot off the USB (recall I was able to even get some but not all of the files copied).
I am trying to save money so didn't bring to Toshiba and they require proof of purchase which would require my friend to pay a researching fee to his credit card.  They also say, you have to pay them even though they don't fix anything and they usually claim you have to replace part XYZ which costs even more money.  Trying to avoid.
Sorry, I meant I had the sudo password for the 7200 HD with Ubuntu 20.
I got it to boot off the USB by accident and can't seem to reproduce that but it did not have a sudo password.
I ran the boot repair as I was trying to explain under recommended settings but it failed so as I recall, there was no link.  Again, since I can't get it to boot off the USB again, I was unable to go back to that screen.
Yes, currently, upon powering up, the Toshiba splash comes up, then Ubuntu with the circular "working" rotating arrows.  But then it just sits there for an hour or more.
When I try to power off, there is a flash of what seems to be root/terminal stuff going on but I can't read it because it is way too fast.
Then it reverts to the Toshiba and Ubuntu page and does nothing again.
Again, I did the boot repair but I didn't save the error message and haven't been able to get back to that screen.
Thanks again, this is way too complex for me.
Appreciate the advice.

---

### Post by yancek on 2021-01-10
If you are able to boot the Ubuntu usb again with boot repair, you need to select the Create BootInfo Summary Option as shown at the link below.  That should provide you with a link which you can post here.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

The site at the link below describes simple steps to reset to factory settings for your Toshiba.  I've never heard of the site and it is NOT the Toshiba site so if you're feeling adventurous, you might try it.  Another thing you might try is an online search for your particular Toshiba model with the word manual in the search option.

 [https://www.helpowl.com/q/Toshiba/SatelliteL55/Technical-Support/reset-factory-settings-toshiba-l55a5226/850493](https://www.helpowl.com/q/Toshiba/SatelliteL55/Technical-Support/reset-factory-settings-toshiba-l55a5226/850493)

---

### Post by 216ann on 2021-01-17
Thanks for the replies.
Took a while but I was finally able to bypass and reset the bios on the Toshiba.
Now however, when I reset the boot order to the USB Ubuntu, it doesn't work.
This is true even though the same USB works on other laptops.
Both the USB & the main 7200HD Ubuntu goes to the Toshiba splash screen, then adds an ubuntu buffering symbol below and then sits there as if the screen is frozen.
However, upon using F9 button, shows that it is slowly going through commands "A start job is running for Hold until boot process finishes up (##min ##s / no limit)", with # being numbers that count down until the next command is done then it shows a higher number later.
This never seems to end despite hours.
Someone stated that I would have more success if I changed the boot drive from UEFI to legacy/CSM and the drive to AHCI however, that just creates a different Grub error regarding not being able to find "initramfs" file.  The supposed solution to this (which is finding and manipulating the initramfs file seems pretty complicated and I fear that I may damage my own system).  
Please advise.   Thank you in advance.

---

### Post by CelticWarrior on 2021-01-17
The drive to AHCI yes, it's a must (almost).
Legacy is a definitive NO.

---

### Post by 216ann on 2021-01-17
> **CelticWarrior said:**
> The drive to AHCI yes, it's a must (almost).
Legacy is a definitive NO.

Thanks for the response.
In order the get the AHCI option, I have to change it from UEFI to CSM (which the computer calls legacy).
Despite that, I get the initramfs GRUB recovery error.

When I don't change it, it goes on a very, very long process saying "A start job is running for Hold until a boot process finishes up".
Despite leaving it on over night, it continues starting and finishing various processes such as "clean php session files" & "Started run anacron jobs".

Again, I am confused because both the USB AND the harddrive runs fine on another laptop that I used (which is older and has poorer specs).  
Are you saying that I should not try to boot with BIOS defaults and change it to AHCI (the other choice is "compatibility" mode).  
How would I deal with the unable to find initramfs files GRUB recovery error?  

Thanks for the advice in advance.

---

### Post by yancek on 2021-01-18
I've never seen the error you refer to.  Did you google it and find any sites with suggestions.  Link below discusses it, seems like an extreme solution but might be worth bookmarking if nothing else works.

 [https://askubuntu.com/questions/760825/cannot-boot-system-due-to-start-job-running-for-hold](https://askubuntu.com/questions/760825/cannot-boot-system-due-to-start-job-running-for-hold)

Just to clarify, you get this when booting the old hard drive with Ubuntu 20.04 on the new Toshiba?  Since the Toshiba is UEFI capable, do you have the Ubuntu on the old drive installed in UEFI or Legacy mode?  If it is Legacy/CSM the you need that set in the BIOS on the Toshiba.

In your original post, you indicate you were able to see the 7200 HD from your older computer.  Was this while booted into the Toshiba?  How did you do that as you don't indicate that you have any operating system installed?  Or do you?  Do you still have the 5400 HD in the Toshiba?

If the computers you are able to boot the Ubuntu USB on are Legacy, they may not be capable of booting in UEFI mode.  

In post 4 above, you indicate that you previously booted Ubuntu off the USB.  When doing things like this that you are unfamiliar with, it is imperative that you keep notes.  Only thing I can think of is that it needs to be Legacy in the Toshiba BIOS as your Ubuntu isn't UEFI capable, just a guess.

---

### Post by 216ann on 2021-01-19
Hi, Thanks so much for the assist.
I had an HP ProBook where both the USB as well as the 7200 drive works with Ubuntu 20 (when the 7200 was installed).
However, neither seems to work with the less-old Toshiba Satellite L55 A5226, when I swapped out the 5400 HD for the 7200.  
This is true regardless of whether the Toshiba is on UEFI or CSM mode and regardless of whether it is on ACHI or "compatibility" mode.
The setting changes only produce different errors (ie, the ACHI results in the initramfs file not found GRUB recovery error and keeping it on UEFI makes it go to that infinite "A start job is running" process).  
I actually don't know if the HD or the USB itself is set to UEFI or Legacy, but both worked on my older HP Probook which has the default BIOS settings.
I have never been able to boot into the Ubuntu 7200 HD on the Toshiba; once was able to boot into the USB (before I ever adjusted the BIOS/UEFI) but that has never happened again.  
Is there a way to run a diagnostic for the USB or HD to see if they are legacy or UEFI?  
Yes, you are right, I never thought it would be this many problems and just assumed it would go smoothly so never took notes.
Again, even on Legacy/CSM whether with AHCI or "compatibility" mode, the Toshiba is stuck on this initramfs error.
According to what I read on the link you provided (thank you by the way), it appears I have to somehow get access to the root.
However, I do not seem to be able to do that on either the USB or the 7200HD...the closest I seem to get is the GRUB recovery mode.
Please advise.  Thanks.

---

### Post by 216ann on 2021-01-19
Honestly, what I really would like is to reliably get all the data off the 7200 HD and have the new Toshiba format the drive.  
But I am confused as to how I can do that without some USB SATA adapter or how the Toshiba without an OS would be able to format its 7200HD with Ubuntu 20.  
Is there a way that a windows OS HD can repair the 7200 HD?

---

### Post by CelticWarrior on 2021-01-20
The point here for both retrieving the data out of the HDD and eventually format and install Ubuntu is to boot a live session.

---

### Post by 216ann on 2021-01-20
> **CelticWarrior said:**
> The point here for both retrieving the data out of the HDD and eventually format and install Ubuntu is to boot a live session.

Correct, which is why I have tried to boot with the USB over and over again.
Was able to finally have the Bios boot off the USB but it results in the GRUB recovery error with missing initramfs file.
Have not been able to find a solution for that.  
The one and only time I was able to boot off the USB (by accident it seems), I was not able to copy all the files because apparently I didn't have root access to the 7200 HD.
I know the password for the root for the 7200HD but I have not been able to get to a point where, using the live ubuntu 20 USB, that I can put in the root password for the 7200HD for access.
So currently I have two stumbling blocks.
BTW, I have also considered the possibility that if I were to get a hold of an older laptop which may already be on legacy/AHCI settings and successfully boot off the 7200HD as well as copy all the data, I could wipe the drive and start afresh.  But that doesn't solve the issue of getting this more recent Toshiba laptop to format the 7200HD drive because the USB doesn't work.
Is there an ability to get an Ubuntu USB to be formatted so it is recognized by UEFI? & not be AHCI???  please let me know, thanks

---

### Post by CelticWarrior on 2021-01-20
Redo the USB. Very likely it became corrupt after those attempts. If doing it in Windows prefer tools like Balena Etcher because it's fool-proof and the resulting media boots in BIOS or UEFI mode. AHCI has nothing to mdo with booting a live session / installer.

In alive session you may need to chown the folders you want to backup. If the partition/drive is encrypted then it's a whole different can of worms.
Yes, of course it's preferable to boot it where it was installed and then backup. Any reason why aren't you doing that?

---

### Post by 216ann on 2021-01-21
> **CelticWarrior said:**
> Redo the USB. Very likely it became corrupt after those attempts. If doing it in Windows prefer tools like Balena Etcher because it's fool-proof and the resulting media boots in BIOS or UEFI mode. AHCI has nothing to mdo with booting a live session / installer.

Thanks will do that.  I was using Rufus.  

> **CelticWarrior said:**
> In alive session you may need to chown the folders you want to backup. If the partition/drive is encrypted then it's a whole different can of worms.
Yes, of course it's preferable to boot it where it was installed and then backup. Any reason why aren't you doing that?
I am not sure how to chown folders in another drive...I am a noob.  I can chown in the live USB.  
I also do think that the 7200HD is encrypted because I needed to put in a password first to access the 7200HD and then use yet another password to access sudo/root.
I don't have access to the old computer anyway and need to borrow someone else's.  
It also doesn't solve the issue of Ubuntu being unable to be run on that 7200HD in the more recent, better Toshiba computer.  
If I were to do things this way, is there a way to use the USB to create a drive that would be compatible even if not on legacy or AHCI (a Ubuntu that would be usable in the default BIOS settings of the Toshiba)?  
Thanks again for all the help.

---

### Post by yancek on 2021-01-21
> I am not sure how to chown folders in another drive. 

You need to first know the complete path to where the partition on the drive you want to use the chown command exists.  Using Ubuntu, this will generally be under /media/username and on a 'live' usb the username is ubuntu so:  /media/ubuntu.  The various partitions there will probably show by UUID.  In order to make any changes you need root permissions so any chown command would need to be preceded by sudo.

 >   I can chown in the live USB.  

A 'live' usb in this context is a readonly filesystem and any changes you make will be lost on reboot unless you have a persistent install.

If your intention is to access data and copy it to another location, you generally do not need root/sudo to copy FROM but may need it to copy TO, depending upon where you want to copy to.  If the device partitions are encrypted that adds another layer of complexity to the problem.

---

### Post by 216ann on 2021-01-26
> **yancek said:**
> You need to first know the complete path to where the partition on the drive you want to use the chown command exists.  Using Ubuntu, this will generally be under /media/username and on a 'live' usb the username is ubuntu so:  /media/ubuntu.  The various partitions there will probably show by UUID.  In order to make any changes you need root permissions so any chown command would need to be preceded by sudo.

 I am a noob and a little confused as to whether I need to mount or unmount first.  And how to do that.
Then if I use the chown using the /media/username I get this, not a file error.
I tried gksu  nautilus cmd suggested by this video youtube.com/watch?v=gtvt2MjeCeg
But that did not work.  
Essentially, what I want is to boot off the live USB, use terminal or the GUI to go to my boot drive (which can't boot but is Ubuntu 20), and save all the files off that.
All the right click permissions are greyed out.  
I tried      askubuntu.com/questions/527304/how-to-change-permission-of-a-drive-in-an-external-hard-disk
but I guess I did it wrong.  I am getting confused as to what I would put as username for each drive and whether the password I put in would be for the live USB or for the 7200HD
would this be better?      sudo chmod -R 777 /media/username/nameofdrive

> **yancek said:**
> A 'live' usb in this context is a readonly filesystem and any changes you make will be lost on reboot unless you have a persistent install.

If your intention is to access data and copy it to another location, you generally do not need root/sudo to copy FROM but may need it to copy TO, depending upon where you want to copy to.  If the device partitions are encrypted that adds another layer of complexity to the problem.
I am getting problems copying the 7200HD files to an external HD that I connect (ie, I am using the live USB to boot, then that OS to access the 7200HD to try to copy files to yet another external HD).  
This is not working because it claims I don't have permissions but never gives me a prompt to put in the 7200HD's password.
So I guess it is encrypted.
Thanks for all the help.

---

