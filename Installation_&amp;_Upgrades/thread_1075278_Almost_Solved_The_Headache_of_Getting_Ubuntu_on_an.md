---
title: "Almost Solved The Headache of Getting Ubuntu on an inspiron"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by OnkelTom on 2009-02-20
Hi everybody!

I've just signed up to the forums, as (suprise suprise) I need a bit advice from some experienced Linux users as this is my first time round.

Well basically, after having Vista break everything I decided "im not buying that again!" . So anyways, I've "rebuilt" my inspiron 1720 with some nice hardwear and set about getting OS's on.

First off, vista did go on (for some programmes for Uni that may not work!) onto a relativley small partition. Then came getting UBUNTU to work.

Now there was all sorts of problems but i sorted it out by searching these boards! Thanks! But there Is one last problem holding me back from getting at Ubuntu! (Except perhaps for sorting the wireless out once i get on it xD)

Anyway, in the end it turns out I can install Ubuntu without crashes only by booting from the 8.10 Alternative CD IS0 on a USB flash stick thingy. That goes through fine then I get "install Grub bootloader etc" so I click "yea ok".

But the problem is this. On start up, i get the choice between Vista and Ubuntu. Looks promising, but it isn't. Clicking on ubuntu brins up the "splash screen". It turns out its looking for the LiveCD to install it or play the demo! Madness!

I think this is because in one of my earlier attempts at getting it on, through the (non-alternative) live CD, it wouldnt read off the CD properley, so i went into windows, ran the CD then clicked the option "Help me boot from CD".

So all in all, i belive the ubuntu option is actually telling the PC to look for the live cd, not the ubuntu installed on the HD.

To solve this, i just tryed using vista's CD to kill ubuntu by deleting its partition, then using cmd prompt to fix bootmgr and all that jazz, but it still comes up with these two options, and worse still, if i try to install again from the UBS(with alt-inst ISO on) it thinks UBUNTU has allready been installed and wont do anything :()

So basically, I need the computer to forget Ubuntu was ever there  and have it go straight into vista, so i can install ubuntu without making the mistakes on the first run through that caused it.

But hears my problem, I cant think how to do it, and I think this is a realitivley unique mess up so havent found similar threads. 

The only solution (which seems extreeme) i can think of is to write zero's to the HArd disk, wiping it, and starting from scratch. ie- put vista on, install UBUNTU from alt-cd-usb then put the grub loader on. 


But that sounds like a right pain for the sake of something I suspect may be a small problem for someone in the know? 


If you've got this far and read my little essay I thank you allreadY! But any help or ideas would be appreciated greatley.


Thanks


O.T

---

### Post by balaknair on 2009-02-20
I've never come up against a problem similar to what you've described here, and I'm not sure i understand fully just what's wrong here. 

It could be a GRUB error and GRUB maybe still persists even after the cmdprompt stuff you did, but since you say you deleted the Ubuntu partition, I'm wondering where the menu.lst file that GRUB is reading is located. I'm not sure it would all fit on the MBR. What might be happening here is that the Vista bootrec.exe may have been modified by whatever the 'Help me boot from CD' option you mentioned does, so that it adds an entry pointing to the CD drive. So what you're seeing here is probably the modified Vista boot menu. Not sure why that would bug the Alternate ISO on the USB though.

You can fix it by either using the 'Repair my computer' option on the Vista DVD or (even better)by using EasyBCD, since apparently bootrec.exe/fixmbr hasn't worked for you.
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

Use EasyBCD to restore the vanilla Vista bootloader to the MBR(Master Boot Record)
using the 'Manage Bootloader' option--> 'Reinstall Vista Bootloader'--> 'Write MBR'

You can then continue and reinstall Ubuntu.

If you hadn't deleted the Ubuntu partition, you could have repaired the bootloader or reinstalled GRUB pointing to the correct partition.

NOTE: I'm assuming you can still boot into Vista to use EasyBCD.

wiki link
[http://neosmart.net/wiki/display/EBCD/Repairing+the+Windows+Vista+Bootloader](http://neosmart.net/wiki/display/EBCD/Repairing+the+Windows+Vista+Bootloader)

Hope you find this useful.
All the best.

---

### Post by OnkelTom on 2009-02-20
Thank you kind sir, that worked perfectly! :D

It went on fine, and everything was working by the time i rebooted- even the wireless wasnt a pain!

I was a bit confused though, because the GRUB seemed to be running from the USB live boot rather than from the hard disk. Hmnn
Now the next problem came when I decided to get into windows for some reason (bad move). Now for the life of me I cannot get it to run. Even "force booting from the USB" results in various errors because from what I make out it is searching for the boot up stuff in the wrong partition! I think windows has changed the order as I created a (FAT32) partition as a "sharing" hard disk space.

So thats tonights challange, and hopefully the last one. sort the bootloader out :S!

---

### Post by Pumalite on 2009-02-20
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by ChodeOfDoom on 2009-02-20
why not get an old windows floppy and do the following:
<A:>fdisk

choice 3 i think is to delete non dos partition
your ubuntu partition may be listed.  if so, delete it.


then create another partition in the hard drive manually with  choice 2 think.  TRY NOT TO COVER UP THE FIRST PARTITION FOR GODS SAKE!  then pop in the ubuntu cd after rebooting and ur good to go... i think

---

### Post by OnkelTom on 2009-02-22
Its all good in the hood guys, writing this from Ubuntu now, loving it. Still fine tuning it like, stuff like DVD write issues and getting used to the (quite frankly rubbish compared to office 07's) equation editor :P

---

### Post by balaknair on 2009-02-22
> **OnkelTom said:**
> Its all good in the hood guys, writing this from Ubuntu now, loving it. Still fine tuning it like, stuff like DVD write issues and getting used to the (quite frankly rubbish compared to office 07's) equation editor :P

Glad to hear you got your problems solved. :D

DVD write issues: Try K3B, by far the best CD/DVD burning app I've used. Available via the Add/Remove programs applet.

Office equation editor: You could try upgrading to Open Office 3, it's supposed to be much better.
[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

Have fun

---

### Post by Pumalite on 2009-02-22
[http://www.unix-tutorials.com/go.php?id=861](http://www.unix-tutorials.com/go.php?id=861)

---

