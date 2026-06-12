---
title: "Urgent Help Please!"
date: 2008-04-23
forum: Hardware
---

### Post by hardcastle1 on 2008-04-23
Okay, so im not the most pc literate person, but I thought I'd give a go at dual-booting and adding Ubuntu to my Laptop,which already has Vista basic, I followed a guide to the tee, shrunk the Vista partition as it said etc, went through the boot cd Ubuntu installation but at the last hurdle, it told me that neither of the boot software things, lola ? and grub? could be installed, at this point I figured maybe Ubuntu wouldn't work, but never mind I'll just keep on with vista, so i safely exited the installation process, or it finished, to be fair and try to boot up Vista, as i normally do and this comes up ' NO OPERATION SYSTEM FOUND' on like a black screen!

Gah!

so I figured, maybe i've messed up my hd, so i went into bios, to see if it's still recognised and working, it is. It can't be disconected, cause the odds of a cable coming lose at this time, are nigh on Lottery win other week odds.

Its a fujitsu siemens laptop and it came with a 'driver and utilites' disk which hasn't done anything or allowed me to boot or anything.

Any help please?!

I'd really,really appreciate it,

Hardcastle

---

### Post by VeN0mizer on 2008-04-23
No worries, I'm almost sure that windows is still there. Try checking the BIOS to see if there is some kind of "protection" for the boot record enabled. If that doesn't seem to help, you could always insert a vista CD and try some kind of repair option? I know you can repair windows XP by putting in the cd, boot from it, select R to use recovery console, put in admin password, and then type in "fixboot" and "fixmbr" to restore the boot files, etc. As far as repairing a vista installation with an xp disc, let me get back to you after doing some research. (Have you tried using the "install inside of windows" feature of hardy heron?)

---

### Post by VeN0mizer on 2008-04-23
Ok try looking into this article from Microsoft as the XP cd won't help I don't _think_:

[http://support.microsoft.com/kb/927392/en-us](http://support.microsoft.com/kb/927392/en-us)

It is for vista specifically, and this should get you taken care of as long as you didn't delete vista's NTFS partition ;)

I might add that I think you should "grow" the NTFS partition back with the live CD after you get your boot record back using GParted, and THEN installing ubuntu inside of windows so to speak, with hardy heron. I did this on my parents comp and it works GREAT! It uses vista's boot manager so there's no hair pulling here ;)

Good luck and keep us updated ;)

---

### Post by hardcastle1 on 2008-04-23
yeah, I wish I'd done that, Im seriously regretting this.

'Don't worry, it's simple - follow my instructions and reap the rewards' X 10

Yeah, I followed your fricking instructions pal, but look where they got me! Grrrrrr

Now I think im in even deeper brown stuff, as i just clicked on repair using the disc and didnt even come up with anything to repair - so i thought %^^%&!!!, So i had a look at putting vista back on, went through to the drive part and this comes up ' Volume not found '

---

### Post by hardcastle1 on 2008-04-23
Right forget that, i managed to get the repair thingy going and now its told - An error occurred while attempting to read the boot configuration data.

---

### Post by hardcastle1 on 2008-04-23
Riiiiiiiiight -

I think *Fingers crossed* Vista is re-installing - So ive lost all my music, but ive got that all on my mp3 player, luckily all my important docs are backed up via email attachments and so on.

Learnt my lesson though,heh.

I think I might invested in an portable HD, and put Linux onto there, that way my laptop won't require more of my blood sweat and tears !

---

### Post by VeN0mizer on 2008-04-24
> **hardcastle1 said:**
> yeah, I wish I'd done that, Im seriously regretting this.

'Don't worry, it's simple - follow my instructions and reap the rewards' X 10

Yeah, I followed your fricking instructions pal, but look where they got me! Grrrrrr

Now I think im in even deeper brown stuff, as i just clicked on repair using the disc and didnt even come up with anything to repair - so i thought %^^%&!!!, So i had a look at putting vista back on, went through to the drive part and this comes up ' Volume not found '

Sorry for trying to help you, but...
Yeah if nothing came up to repair, then you most likely deleted your NTFS partition somehow and this tutorial will not help you. Sorry I can't help you and I know it must be frustrating, but trust my I have lost gigs and gigs of irreplaceable data with windows many many times before. One time being when I used the encrypting file system with XP Pro and backed up my entire user folder (over 20 gigs of source code I had written, among other videos, music, etc) and after I reinstalled windows, they were inaccessible to me due to me somehow not backing up my EFS keys when I thought I had....so I DEFINITELY feel your pain...Best of luck to you...

---

### Post by BatsotO on 2008-04-24
There are many undelete application you can use. many strong enough to recover files even after deleting partition.

---

### Post by ndale686738 on 2008-04-25
if you have a fresh install of windows vista you should go ahead and let vista shrink your partition for you so if you decide to give linux another shot it will not screw up your windows install. just follow this guide to shrink your partition. [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) Make sure that you do not format the partition with windows and choose the "use largest contiguous free space" option when installing Ubuntu and it will automatically select the unallocated partition. don't give up. Linux is wonderful once you get past the newby jitters. Also next time you have a problem try searching through old posts for a while before posting a question. it will help you sort out the bad advice from the good ones. Hope you give it another shot.

---

