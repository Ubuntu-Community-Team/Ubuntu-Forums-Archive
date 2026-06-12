---
title: "Hibernate/suspend/sleep do not work at all in 9.10 Karmic"
date: 2009-11-18
forum: Hardware
---

### Post by sfordin on 2009-11-18
I see that there have been many similar threads about problems with hibernate/suspend/sleep in 9.10 Karmic. Those threads seem to mainly deal with waking up from hibernation, suspend, and/or sleep. My problem, however, is that those features simply do not work at all on my Toshiba Satellite A205.

It doesn't matter whether I choose hibernate or suspend from the shutdown menu, or use the pm-hibernate or pm-suspend commands. The screen will go dark and the hard drive will apparently spin down, but the power light and system logo light never turn off, and it's clear the machine is still powered on. Worse, the machine can't wake up from this limbo state. It's neither off nor on, and the only thing for it is to do a hard power reset.

I've tried adding the acpi=oldboot statement to my grub.cfg. No joy. I've tried installing the hibernate program, which worked quite well in 9.04. No joy again. I am at my wit's end here, and wondering if I need to downgrade to 9.04. This would be a shame because there are lots of things I really like about 9.10. This hibernate/suspend thing is a show-stopper though.

Thanks in advance for any help,

Scott

---

### Post by sfordin on 2009-11-19
I discovered a workaround that enables my machine to hibernate and wake up without a hitch. I usually keep an SD card in the card reader slot on my Toshiba A205 laptop for "on the go" backups, and as it turns out, the hibernation fix is to eject the SD card before initiating the hibernation.

Network mounts don't seem to matter, nor does the Windows partition I have mounted from the same physical drive on which my Ubuntu partition is located. It's just the SD card in the SD card slot. Go figure.

So, to reiterate, here's the routine I now follow to hibernate my laptop:

[LIST=1]
[*]Eject the SD card.
[*]Choose Hibernate from the Gnome shutdown menu.
[*]Wait for everything to spin down and the lights to go off (~45-60 seconds).
[*]Close the laptop lid.
[*]Put the SD card back in the slot, pack up the computer, and move on to the next bit of fun.
[/LIST]

Later, when I open the lid of the computer, it resumes like a champ, although I sometimes need to eject and reinsert the SD card to mount the card. Otherwise, everything seems to work fine, including the network mounts that were there when I hibernated, assuming, of course, the relevant network connections are still physically available.

I hope someone else finds this useful.

Scott

---

### Post by anton610 on 2009-11-21
Same Problem, no hybernate or standby with a asus ion mainboard. all bios power things are activated.
 
Any ideas??
 
Thanks Anton

---

### Post by jimmyjones on 2009-11-27
Mini 9 9.10 upgrade:

I found I only have to un-mount the volume, it's not necessary to physically remove the card.

Same procedure, un-mount volume, suspend, when it wakes up I go to places and select the SD, in mounts and everything is peachy. 

Real annoyance though.

---

### Post by wahid on 2009-11-29
And I've also the same Problem with my Toshiba Satellite A100-153, however the hibernation mode worked always out-of-the-box on Jaunty. The Standby worked "strangely" once in 5 attempts under Jaunty, but I could live with it. However on Karmic I can't now go back from neither Standby nor Hibernation to my session and I get every time this "Black Screen of Death", which force me also to do a Hard-Poweroff!!!!
For any indication or help I would be really glad.

Thanks

---

### Post by confused_user on 2009-12-04
same, i dont have a card in my sd card reader so i dont think it is that.

I disabled networking to ensure that my ssh mounts (sshfs) were not getting in the way.  same.  When i close the lid it wont suspend / hibernate / shutdown.

Has anyone filed bug report?

this used to work on 9.10 by the way, from the default install i remember it working just fine, i did an update just after i installed though and i guess it has not worked since then.

form previous experience with updating karmic i'm terrified of doing it again.

---

### Post by manolomanolo on 2010-01-03
Suspend works very fine to me, Hybernating does not work (it acts quite similar to suspend).

No SD on any other external volume mounted.

---

### Post by latrodectus on 2010-01-03
Gents, at least you are still able to use your computers...I haven't been able to wake my Satellite 1410 up after closing the lid once. 
Here's the link to the thread I opened, I would really appreciate if someone could help in bringing life into it: [http://ubuntuforums.org/showthread.php?t=1370593](http://ubuntuforums.org/showthread.php?t=1370593)

Cheers,
latrodectus

---

### Post by Mocker on 2010-01-03
sfordin,

Thanks! I was at my wit's end with sleep mode on my Fujitsu P1510D, which I recall had a working sleep mode in Feisty. I keep an SD card in the slot constantly to hold MP3's and other things, since the hard drive is so small. Ejecting the SD and the Compact Flash worked just fine. 

Like you, my laptop would never go into sleep mode... it would hang after clearing the screen, but the power light and screen backlight would remain on, and would have to be powered off. 

Has anyone hacked a solution so we don't have to manually eject cards? I imagine you could set up a script that runs as the sleep mode kicks in to unmount the SD drive, and then re-mount on wakeup. I may tackle this, since I really like having the added storage of the SD card, and don;t like having to remember having to eject or manually dismount the thing before suspending.

---

### Post by Mocker on 2010-01-03
Turns out unmounting the SD automatically on suspend/hibernate is easy. The sleep demon will execute files in /etc/pm/sleep.d before sleeping or hibernating.

I added a script to this directory to automatically unmount the SD card's block device, like this:

On the commnd line, type:

```
sudo gedit /etc/pm/sleep.d/99_umountsd
```

Paste the following into the editor, then save the file:
> 
#!/bin/bash

case $1 in
    hibernate)
        umount /dev/mmcblk0p1 # change me!
    ;;
    suspend)
       umount /dev/mmcblk0p1 
    ;;
    # thaw)
    #    
    # ;;
    # resume)
    #   
    # ;;
esac


In the script, you need to change the "/dev/mmcblk0p1" to the device name for your mounted SD card. (Use the mount command to print out a list of all your mounted volumes if you don't know what the device name is.)

Finally, make the file executable:

```
sudo chmod a+x /etc/pm/sleep.d/99_umountsd
```

You may need to reboot in order for these changes to take.


It worked fine for me... your mileage may vary.

I didn't have to have the script remount the SD drive after being woken out of sleep... it seems to do this automatically.

---

### Post by ferminnajar on 2010-04-10
Hey thanks ! I have months trying to find a solution. I have a toshiba satellite and, yes, i was always a SD card mounted. It was the last thing i need to fix in ubuntu 9.10 for use it more often.

Thanks pals !

---

### Post by jimmyjones on 2010-05-01
Back again, same issue in Lucid.

This fix works in Lucid too !

The 99_umount got lost in the upgrade, had to redo it, no biggy, just took awhile to find this thread.

---

### Post by manolomanolo on 2010-05-01
**I am still unable to hibernate here in Lucid too**.

I have a suspect: am I required to have some minimal amount of **swap memory** size in order to be able to hibernate?
At the moment I have 478.5 MiB as System Monitor says

---

### Post by 2FishInATank on 2010-06-03
Just a quick note to report that the SD unmounting solved my suspend problem on a Dell Precision M4400 running the 64 bit version of 10.04 Lucid.

Cheers!

---

### Post by Trenchbroom on 2010-06-05
Thank you Mocker!  Haven't been able to suspend on my mini9 with an SD card inserted since 9.04.  Your fix works great in 10.04.  You rock!:guitar:

---

### Post by JBA2337 on 2010-07-07
Thanks Mocker! Your post was in January, but I just saw it today.

You solved a very irritating problem for me. I use a 32 GB SDHC card in my Toshiba A105 laptop. With the card installed in the slot I couldn't Hibernate or Suspend the computer.

Now both Hibernation and Suspend work perfectly!

Many kudos to you!!!   :D:D:D ):P

JBA2337

---

