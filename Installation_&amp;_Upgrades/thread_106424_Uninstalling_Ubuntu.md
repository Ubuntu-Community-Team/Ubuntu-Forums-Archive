---
title: "Uninstalling Ubuntu?"
date: 2005-12-20
forum: Installation &amp; Upgrades
---

### Post by SomethingTohide on 2005-12-20
I never really came acrose this anywhere. How do I uninstall it? I tried formatting the whole drive to what XP uses, but I get an error saying the MBR has an error, and it says that everytime I try to boot. I installed Ubuntu again on that partition and wanted to know how to completely get rid of it.

---

### Post by SomethingTohide on 2005-12-20
Would it work if I just installed another linux over Ubuntu, like formatted the drive using another linux boot disk, then installing that linux on that partition.

I'm using XP and Ubuntu on dual boot, both on seperate partitions of seperate drives. I don't have my XP or any Windows disk right now, it's still packed up in a box somewhere

---

### Post by mo_x on 2005-12-20
You can just overwrite the patitions or remove them and create new ones.
Do you have Windows XP installed on the same machine? I guess you then have to rewrite the MBR.
The big question here on the Ubuntu forums: Why do you want to uninstall Ubuntu?

---

### Post by mo_x on 2005-12-20
You can just overwrite the patitions or remove them and create new ones.
Do you have Windows XP installed on the same machine? I guess you then have to rewrite the MBR.
The big question here on the Ubuntu forums: Why do you want to uninstall Ubuntu?

---

### Post by robenne on 2005-12-20
Try booting off a floppy and after getting the a:\ prompt type: 

format /mbr

Then reinstall XP

---

### Post by SomethingTohide on 2005-12-20
To mo.. I wanted to try out another Linux system, just checking around.
Does it matter what's on the floppy?

---

### Post by harisund on 2005-12-20
> 
Then reinstall XP
OMG for heaven's sake, you don't need to reinstall XP. That's absolutely insane. 

If you are so keen on uninstalling Ubuntu, use Windows XP to format the disk on which Ubuntu is stored (you know how to do that right? If not I will walk you through it.)

Once that is done, boot with your windows XP install cd and during the installation process, you will find an option that says "1. Install a fresh copy of Windows. 2. Repair an existing version of Windows." Select 2, and then you will be taken to the command prompt  (see, you get a command prompt in Windows repair too!)  and while there type fixmbr. 

But why?

---

### Post by SomethingTohide on 2005-12-20
I want to try something else out, just to see if it works, if not then I'm reinstalling ubuntu, which isn't hard because I'm a noob at this and don't have anything besides the base package. What could I do if I don't have the XP disk, and I can't get it for a whileeee

And format using XP, but when I'm in my computer the drive that Ubuntu is on doesn't show.

---

### Post by harisund on 2005-12-20
Well then you would need a floppy. Still the same thing I said would work, and you wouldn't need to reinstall Windows XP.

---

### Post by robenne on 2005-12-20
[QUOTE=harisund]OMG for heaven's sake, you don't need to reinstall XP. That's absolutely insane. [/QUOTE]

My bad!! I misunderstood what he wanted to do. I thought he was wanting to remove Ubuntu and reinstall XP. :cool:

---

### Post by SomethingTohide on 2005-12-20
Ok does it have to be any floppy or a repair floppy. I've got blank ones but where can I get the stuff for it to work?

---

### Post by SomethingTohide on 2005-12-20
Could I use this?

[http://www.microsoft.com/downloads/details.aspx?FamilyID=55820edb-5039-4955-bcb7-4fed408ea73f&displaylang=en](http://www.microsoft.com/downloads/details.aspx?FamilyID=55820edb-5039-4955-bcb7-4fed408ea73f&displaylang=en)

---

### Post by harisund on 2005-12-20
[QUOTE=SomethingTohide][http://www.microsoft.com/downloads/details.aspx?FamilyID=55820edb-5039-4955-bcb7-4fed408ea73f&displaylang=en](http://www.microsoft.com/downloads/details.aspx?FamilyID=55820edb-5039-4955-bcb7-4fed408ea73f&displaylang=en)[/QUOTE]

Hmm.. I am afraid that is not going to work. On this page it says the floppy will only gain you access to the CD ROM, and is used on machines which can't be booted directly of the CD. 

I doubt with Windows XP you can actually boot of a floppy disk alone. 

When robenne typed earlier that you should boot of a floppy, I think the poster probably meant a Windows 98 boot disk. If you can indeed get access to a Windows 98 boot disk (I think you can also search on the web for it if you don't have ready access to W98 disks.)
However, robenne has mentioned format /mbr. Instead do fdisk /mbr. That should fix the drive. 

However, be warned you might still not have access to Windows XP, since you are using W98 floppy after all. I used to do that when I had 98 and it worked, so I am guessing it works with XP, but if not using the CD is the only way out.

---

### Post by SomethingTohide on 2005-12-20
Ok [http://freepctech.com/pc/002/files010.shtml](http://freepctech.com/pc/002/files010.shtml)
go there and under Special Boot Disks at the bottom would the Partitioner one work?

---

### Post by harisund on 2005-12-20
Yeah.. I think as long as it has fdisk.exe it should work. 

But be prepared, don't tell me I didn't warn you. Ok?

---

### Post by SomethingTohide on 2005-12-20
What could happen?

---

### Post by shelleyj on 2005-12-20
Hi Guys, I am wondering if someone here can help me?   After  having read so much about Linux and Ubuntu I decided that it could be worth my while to try it.  Sent off for the free cd, and installed it.
Now I hate having to admit this, but I am no longer young and it seems my powers of understanding have faded with age!!.  I installed it on a separate drive, and now have a Gnu boot that comes on at start up.  This gives me the choice of either Ubuntu or Microsoft XP.  However, I find that I must be too set in my ways, and just cannot get my head around Ubuntu!.  I fumble along and get nowhere.
So please guys, how do I uninstall it??  I am  not a programmer, and I guess I really shouln't have tried it, but I really was looking for an alternative to Microsoft.  I have to admit that I have reached my limits with XP and must give up on the idea of using Ubuntu.  
So please can you tell me if there is an easy way (for me) to uninstall Ubuntu??  All suggestions and diagrams will be much appreciated  Thanks a lot  Shelleyj

---

### Post by SomethingTohide on 2005-12-20
You were right lmao, I used the floppy, formatted the partition to NTSF, then I did fdisk /mbr and rebooted. It booted into windows like normal and Ewido Security Suite gives the error Cannot connect to device 2 and then like 5 seconds later it restarts.

---

### Post by scole on 2005-12-20
I could use a little help in this area 2 :( I have ubuntu on a sweet dell and am being forced to take it off i can delete the partions no prob. I cant wipe out winxp although id like 2. I need to remove grub how?

---

### Post by Mark4 on 2005-12-21
Hello

I would also like help in this area.

Why? because I installed Ubuntu on my best (win xp) machine to give it the best chance of a successful test and now want to remove it from this machine. 

[ In fact I want to install ubuntu on an older win98 machine which I plan to be a ubuntu-only machine.  ]

Meanwhile I believe it would be a good idea if the first chapter in the help documentation should be instructions on how to completely remove ubuntu, so that people trying it out can eliminate it from their computers at the end of the test.

regards
Mark

---

### Post by mo_x on 2005-12-21
Operating systems don't come with an unistall option (how do you uninstall Windows?) If you want to restore your Windows installation you have to overwrite the MBR. You can change and reformat your Ubuntu partition to remove all the data and get Windows to see it again.
See the following link for some help, look at fixmbr.
[http://support.microsoft.com/default.aspx?scid=kb;EN-US;314058](http://support.microsoft.com/default.aspx?scid=kb;EN-US;314058)

---

### Post by SomethingTohide on 2005-12-21
Ok well now I've got Windows working, and Ubuntu there, but the GRUB boot loader doesn't show up, how do I add it again? I've already got Ubuntu installed

---

### Post by scole on 2005-12-21
GRUB should have automaticly configured during the ubuntu installation. if it didnt what happens when you tell it to boot into ubuntu i dont know what to do does it even come up at all?? Woops my bad didnt read ur post all the way. what you can do i dont know if it will work it may boot up off the live cd and allow you to save your settings to your linux partions. Or what may also work is if you have high speed download the puppy linux iso and burn it heres the site [www.goosee.com/puppy](www.goosee.com/puppy) this little distro is only 55 meg and has grub included in the live cd so theoreticly all you would need to do is boot into the live cd and configure or install grub from there. I have not tried it because i have mine working fine. but it may be worth a try. :) if worst comes to worst wipe the entire hdd clean and begin again or wipe out your linux partion and reinstall it allowing ubuntu to automaticly partion out your free space. tell me if it works

---

### Post by Herman on 2005-12-21
To uninstall Ubuntu:
The first and most important step is to put your Windows boot sector back on your Master Boot Record. I wrote a website explaining how to install Ubuntu, and I already have a part of it that explains restoring your Windows boot sector. It's at the bottom of the 'GRUB Help' page, if you click on my signature link and go to the 'GRUB Help' page and scroll down right to the very bottom, you'll find this information already there for you. Take the link to the Microsoft knowledge base for the CD method, if you have XP. Otherwise, you can use the floppy disk method. it worked fine for me when I used it on my good XP/Ubuntu dual boot computer. (Just for an experiment). But why not consider leaving Ubuntu there and keep it for an emergency such as when Windows gets a major virus or something. You can still use all the space for storing back-up files where they'll be safe too. Ubuntu only actually takes up about 1.7 GB of the partition it's on. The rest of it would make an ideal area for securely storing files, even if you don't like Ubuntu. If you don't want to see the GRUB menu on boot-up, look at methods on the same 'GRUB Help' page to set Windows as your default system, set the timer to 1 second, and hide the GRUB menu. You'll never know Ubuntu is there! :smile: Anyway, it's totally up to you. I will improve my information on this subject for next time I update my website, (in a week or two), I didn't realize anyone would find it difficult to remove Ubuntu, or would want to. All the best anyhow. (Herman)

---

### Post by SomethingTohide on 2005-12-21
Could I just put in Ubuntu install CD, skip to step where boot loader is made, and then finish?

---

### Post by harisund on 2005-12-21
[QUOTE=SomethingTohide]Could I just put in Ubuntu install CD, skip to step where boot loader is made, and then finish?[/QUOTE]

I think you can do it with the expert mode. But I wouldn't suggest doing it unless you are familiar with the installation and know what you are doing!

---

### Post by SomethingTohide on 2005-12-21
I've only installed Ubuntu 6+ times on this computer haha. Thought the problem was that the CD was messed, but it was actually the retarted nvidia drivers not accepting anything more than 8bit for me -_-

---

