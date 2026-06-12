---
title: "Noob attempt failed"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by apostra on 2009-11-10
Hello there,

I think as noob, messed up big time here, would like your help please.

I got Vista, by default two partitions, C: operation 135GB of 197GB free and  D: data which was empty 195 free of 195 GB, i mention the capacities cause thats the problem

I was thinking to install 9.10 on the D partition, but at installation got confused, my screen wasnt excactly the same as print-screens found on the internet. So didnt know how to move the bar or how to choose the D partition etc. So i decide to cancel installation and find some more information (silly me thought was ready for installation).

Now the big fun begins, two issues:

1) I just noticed that while on Vista, my D partition (data and empty) has new capacity, 20GB, 20GB free of 20GB. Thats down from 195 of 195GB free!!!!!!!!!!!!

So i'm wondering, what happened? Why vista read only 20GB from D partition?I didnt changed anything at installation, didnt touch anything, didnt move anything, quite it normally whitout errors, boot vista without errors too!!!!

So question 1: How i restore back to normal my D: partition?


2) If and when the D partition is restored, at the installation, how could i install 9.10 on D partition? at the installation screen i got sda1:8.8GB (vista) sda2:197GB sda3 195GB) and a totall "free space" of both partition, which that confuses me. Could some1 guide me step by step please, on that step only?

So what of the three options i choose? **The first one?** but the free space is the _total free space of both partitions and i want to leave C: partition untouched._ **The second** one is not a solution, as i want to keep vista and the third one, which is the D partition? sda3? and why the free space that gives me is again the total free space of both, which confuses me again.

I'm really sorry if the answer is out there, I know is out there in front of me, but too much info pop straight away for a noob like me and got really confused. I dont want to make my own dicision cause affraid that will mess up again :~(

I know is a lot i'm asking but would be greatly appreciated if you provide some help plz.


Once again really thank for your time to read and help guys.

Regards

---

### Post by Bartender on 2009-11-10
Well, it *sounds* to me like you created a third partition, and that partition's file system is something Linux-y.  Windows tries to act like Linux doesn't exist so it won't report Linux partitions.

Got a thumb drive?  Can you boot from an Ubuntu LiveCD, and choose "Run Ubuntu without making any changes"?  When you get to the desktop, plug in the thumb drive and wait for it to appear on the desktop.  Make note of the name.
Then go to System>Administration>Gnome Partitioner.  When the partition map comes up, go to Applications>Accessories>Take Screenshot.  Take a screenshot, save it to that thumb drive, then close the partitioner, right-click on the thumb drive icon, eject the volume, then close out of the LiveCD.
Come back to the forum however you can and post the screenshot.

I'm thinking the thing to do is go in with a LiveCD or GParted LiveCD (link under my sig), delete that third partition, delete the second partition, create one extended partition out of the space, then install Ubuntu, but it'd be good to see what you've got first.

---

### Post by apostra on 2009-11-11
Bartender thanks alot for your help and time, much appreciated.

I dint save it to any drives, i just boot on LiveCD, took the screenshot, save it and email to my secondary email. My desk its too messed up atm to find the drive :~(  Hope its same thing, if not i'm gonna dig in find my drive and do it as you asked.


(Both Links same image)
[http://img136.imageshack.us/img136/9535/16373247.png](http://img136.imageshack.us/img136/9535/16373247.png)
[http://yfrog.com/3s16373247p](http://yfrog.com/3s16373247p)

---

### Post by pullmoll on 2009-11-11
> **apostra said:**
> Hope its same thing, if not i'm gonna dig in find my drive and do it as you asked.

Well, there on the screen you can see your 20GB D: partition and 370GB of unallocated space. All you need to do is to resize D: to the size you want by clicking on it and selecting move/resize.

IIRC you should get a context menu with the right mouse button. Otherwise you'll find the move/resize option in the _Partition menu entry.

HTH
pullmoll

---

### Post by apostra on 2009-11-11
Hello again,

well now I feel like stupid ( once again he he ) 

I think I understood what you were saying and did something, i would like your opinion as you are more experienced to be sure I didn't messed up again.

1)As you suggested, boot on Live-CD, open the G Parted.
2) Delete all the partitions except the two using the vista
3) Created a new **[COLOR=black]Extended Partion,[/COLOR]**[COLOR=black] I put bold cause unfortunately all guides i found was saying "create partition" and i added Primary at first, then I got the msg that cant make more than 4 partitions, when i was trying to make the last one, the swap. So if you are noob like me Extended than Primary at the first one.
4)Create a Primary partition label /
5)Resized the Primary partition, step 4, to make a new partition with label /home
6)Finally resize the partition on step 5, the /home partition, to make a swap


Closed the G parted, run the installation. There i select manual, i double clicked on each partition to set them as root etc. That was it! How silly of me got stacked at first.

*Did the two partitions, the "/" and "/home" as I had in mind with windows installation to create the operation partition and the data partition. But I'm not sue if what I did, is what I wanted to do.


Below are some screen-shots, please if you are not busy have a look and advice me if its all fine or missing something or whatever. Its my very first attempt to install Linux and not sure what I'm doing here! 


[http://img121.imageshack.us/img121/231/60849395.png](http://img121.imageshack.us/img121/231/60849395.png)
[http://img517.imageshack.us/img517/6277/51724779.png](http://img517.imageshack.us/img517/6277/51724779.png)
[http://img340.imageshack.us/img340/8880/97866699.png](http://img340.imageshack.us/img340/8880/97866699.png)
[http://img121.imageshack.us/img121/3638/91877279.png](http://img121.imageshack.us/img121/3638/91877279.png)


Once again thanks again for time and help, much appreciated.



[/COLOR]

---

### Post by Bartender on 2009-11-11
Hi, apostra -
I'm on dial-up so your screenshots are killing me, but you did good as far as I can tell.
I'm not familiar with the Palimpset Disk Utility.  Is that something in the new Ubuntu, or an application you downloaded?

Anyway, yeah, you figured out the primary vs. extended on your own so that's good too.  Lots of people really get hung up when confronted with primary vs. extended and logical.  I know I did!

This [thread]("http://ubuntuforums.org/showthread.php?t=1321649") is somewhat similar to yours, don't know if you've been following it.

So is Ubuntu working now for you?

---

### Post by apostra on 2009-11-11
Hey again,

Thanks for coming back.

Firstly about the thread i didn't touch wubi at all, before starting anything google it and as I show the most was preferring a clean install or a partition install. So i didnt even click wubi to see what pop ups or anything, am affraid have none experience on that. From what I show at forums here (mostly) and generally from sites is that I need a swap, /  and a /home partition, so I tried to make mine look like it. To be honest till get the different between primary, extended, logical took me like 10 times to reformat my disks. Did all the possibles combinations until found it! I was too close, starting shooting my pc and my girlfriend's mother (the last just for the crack, kidding of course! love them both ) 



The Palimpset Disk Utility found it at System->Administration->Disk Utility, so I guess comes with 9.10. Never had the 9.04 before so from what you're saying must be new, as i didn't download anything too.


Ubuntu runs smoothly! After installation, I just reboot the machine, the boot screen prompt me to choose what system to boot and all was smooth. The only I could advice to any noob like me, that choose to do it like that, is that, when it boots, the screen where prompts me to choose operating system, the vista is named like sda2. not vista. The ubuntu is pretty clear, only the vista referred as sda2, in my case at least. So if you are not familiar with anything like that, its good to write notes for what is what when do the partition, I know silly but helped me :~)



Ubuntu know runs perfect! At least from what I can see. As long as I booted it, found the Graphic card and prompted me to activate it. Then I run the updates, reboot again and everything was perfect.


However I got a couple questions again,

1)Do I have to download and run any drivers for graphic card? When prompted me to activate the graphic card and driver, I saw that downloaded some drivers for the card too. Is this enough or should I do more about it? I should mention that I tested the visual effects on full and all was fine.


2)I got confused about kernel now. Is the one the cd has enough?I download the cd and install system, yesterday if that helps. Should i download/install/compile it or is it included? Why some people says kernel is just a headache and if system runs good there's no reason to add it?

(Last one finally, sorry for that)

3) This is very noobish i promise you!! As I did the partition, I thought that would be like windows style, to see two hard disk drives. But as I go to Places->Computer-> I see the one HHD is the total disk, including the vista and the other is the..... File-system. I was expecting having three total, one the total disk, as it, then one for the "/" partition and the other for "/home" partition, like C: D: E: etc. Now is it something I don't get, or the one partition isn't showing? But then the total size of the current File-system is the correct one.

_I try to answer the last question, in hope to save you some time and headache._ Is this happening cause the one partition is inside the other? In other words, the /home partition appears to my screen as folder than a separate disk? Did i made the /home folder not only folder but a partition?

Meaning that, I can save all my data on /home folder and the "/" partition would be appear for example, after a year when I try to install the new version of Ubuntu? 

Or

Simply something is missing and I have to find it? :~)


I tried to to resize the picture for helping :~(
[http://img41.imageshack.us/img41/9278/85169905.png](http://img41.imageshack.us/img41/9278/85169905.png)


Once again thanks for helping and time you giving, much appreciated.

Regards

---

### Post by Bartender on 2009-11-11
All of your recent questions sound to me like unfamiliarity and disorientation with your new surroundings.  This will dissipate with time and experience, and probably looking here at the forums when you have questions.

1) If you went to System>Administration>Hardware Drivers, and Ubuntu found drivers for your graphics card, then downloaded and installed those drivers, that's all you need to do.  Unfortunately, we're still subject to the whims of the graphics card manufacturers and the drivers which they supply (or don't).  This situation has gotten better over the last few years.  Nvidia has been more helpful than ATI/AMD but ATI's driver support has improved.

2) The Linux kernel is the core of any Linux OS.  Many people will tell you that it's more accurate to refer to your new OS as "Linux/GNU" because without GNU people like you and me would be helpless.  Well, I would anyway.  I don't have the foggiest idea how to communicate directly with the kernel!  This is another thing that you don't need to worry about.  Several times a year there will be a kernel update along with your other updates.  Just let it install.  Sometimes after a kernel update some drivers will break, but let's not worry about that for now.  About the only thing you should know about kernel updates is that Ubuntu keeps previous kernels.  You can safely delete older kernels, but lots of folks recommend keeping at least two - the current one and the one previous to that.  This is in case the current one breaks and you need to boot into the previous one.  I've never had to go back to the previous kernel, but I do follow that rule of keeping at least two.

3) Forget about how Windows shows drives and partitions.  Try to familiarize yourself with how Linux portrays them.  You can go to Synaptic Package Manager and download the gnome-partitioner.  That will show you your partitions graphically.  There's also a utility called - um - gnome-device-manager? or something very similar that lists detected devices and such.  

"File System" is the Linux OS.  You can look around in there but don't try to make changes.  First off, Ubuntu won't let you unless you know how to get in, and second off, there's rarely any need for the average user to go mucking around in the File System.

Your Home will show up as a folder, yes.  You have permissions to read and write to your home folder, so you can create folders, etc.  It seems a little odd at first, coming from Windows, but it's a very simple and logical concept.  Anything you save or copy or rip will go into your Home Folder.  

If you download the gnome partitioner you can "see" how the partitions relate to each other physically.

---

### Post by UltraZone on 2009-11-11
Everything that you set up looks good, however I would suggest that your Swap partition is too big and all that space is going to waste now.  I think that 4 - 8 Gb for normal home use is all you need unless you have good reason for it to be so big.  So just consider shrinking the swap and extending either of the other two.

---

### Post by apostra on 2009-11-12
Hi again guys,

indeed Bartender, many new things for me. Even that i like them, the look the way it runs, i still have the "windows" virus in me and compare/waiting to show up like windows. It will take while to used to it but i think gonna like it. Seems as you said very logic they way it is and i want to dig into ubuntu more and more.

Good thing you mention about the Filesystem cause already find the way to log in as root, via console or from login screen hehe. I'm gonna follow your advice and don't touch anything for some ( really some ) time!

You're right Ultra too, think its too much as I check it more on forum, when I was doing it thought to make it like 8-10G as windows use for their own, but didn't know if that was enough for Linux. I'm going to fix that shortly as well.



I would like to really thank you helping for installing the Ubuntu. Couldn't do it without you. Your advices and tips was very important! 

I was looking for ages at forums and couldnt find something similar to what i wanted.



Thanks a lot again, much appreciated!

---

