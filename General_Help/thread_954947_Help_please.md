---
title: "Help please"
date: 2008-10-21
forum: General Help
---

### Post by vedo87 on 2008-10-21
Hello my lovely new open source friends! :)

I am totally new to this, and I have a real beginners question. :)

I downloaded Ubuntu 8.04 and it was a .rar of course, and after extracting it, I saw that it is the source code of Ubuntu, full of subfolders and files.  I burned it so to a DVD and tried to boot it but it didnt work...

My question is how should I burn it to be bootable or should I burn it at all?  I have an empty partition where I plan on installing it.  Can it be done by starting the .exe file from windows?

Thanks in advance!
Vedad

---

### Post by tCarls on 2008-10-21
It was a .rar? Where did you get it from? Usually it's a .iso. You can get the .iso from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download). Instructions for burning it to a bootable CD are at [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto).

What .exe file are you talking about? wubi.exe? If so then, yes, you can just run that from Windows without burning a CD, but if you're planning on putting Ubuntu on its own partition then I'd recommend using the .iso and burning a CD.

good luck

---

### Post by vedo87 on 2008-10-21
> **tCarls said:**
> It was a .rar? Where did you get it from? Usually it's a .iso. You can get the .iso from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download). Instructions for burning it to a bootable CD are at [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto).

What .exe file are you talking about? wubi.exe? If so then, yes, you can just run that from Windows without burning a CD, but if you're planning on putting Ubuntu on its own partition then I'd recommend using the .iso and burning a CD.

good luck

You know what?  U r the man! :)  It was a .iso file but the icon wan from .rar so I didnt even look at the extansion.

I burned the .iso already!  Thanks mate!  

Now...  Once I insert it and boot it... Is there anything else that I should be aware of?  Something I usually wouldnt know? :)

---

### Post by tCarls on 2008-10-21
Thanks for the kind words. The only thing I can think of that you may need to be aware of is if it doesn't boot, you may need to change the boot order in your BIOS to boot from the CD-ROM before the hard drive. Other than that, just take things as they come.

---

### Post by vedo87 on 2008-10-21
> **tCarls said:**
> Thanks for the kind words. The only thing I can think of that you may need to be aware of is if it doesn't boot, you may need to change the boot order in your BIOS to boot from the CD-ROM before the hard drive. Other than that, just take things as they come.

Oh yes... I always change the BIOS to CD/DVD as soon as I get a new computer, but what I meant is once I install it, whats up with drivers for example?  What software do u recommend?  Ex. antivirus software, I dunno...  What does not work that usually works with XP or Vista, etc...?

---

### Post by vedo87 on 2008-10-21
> **tCarls said:**
> Thanks for the kind words. The only thing I can think of that you may need to be aware of is if it doesn't boot, you may need to change the boot order in your BIOS to boot from the CD-ROM before the hard drive. Other than that, just take things as they come.

I got 2 questions: 

1) I am about to install 8.04.  Do u think I should wait few more days to install the 8.10?  Is there a big difference?  What is the difference?  When a new version comes out... is that like when Microsoft comes out with a new OS like Vista (and its all crappy and unstable) or is this version system more like the service pack?  I hope u understand me.

2) I was playing with the installation to get a feel for it and run into a little problem.  I am on step 4 out of 7 where you prepare partitions.  Now, I got 3 partitions, I got vista on the first and the second two are empty (I am guessing vista is on the partition that has most used space). So I try to select a second partition to install ubuntu on but I get an error message that says: No root file system is defined.  Please correct this from the partition menu...  What should I do?

---

### Post by daniel.hodge on 2008-10-21
Ubuntu 8.10 is almost the same as 8.04. There are some major updates and improvements system wide. There is a website that lists some of the major changes in 8.10. [http://www.ubuntu.com/testing/intrepid/beta](http://www.ubuntu.com/testing/intrepid/beta)

When installing Ubuntu on your second partition, select the edit tab at the bottom. A few drop boxes should show up. You should probably format the partition to ext3, and the mount point drop box should be "/". Once that is done, it should continue installation for you.

---

### Post by tCarls on 2008-10-21
I realize daniel.hodge already answered your questions (thanks) but I spent a while typing this so I'm gonna post it anyway.

> 
what I meant is once I install it, whats up with drivers for example? What software do u recommend? Ex. antivirus software, I dunno... What does not work that usually works with XP or Vista, etc...?

For the most part things work out of the box. What doesn't work can usually be fixed with some effort. I'd say just play around and post any problems you run into here.

I wouldn't worry about antivirus software. I've never used it with Linux and I've never had any problems. The only reason you might want antivirus software would be to scan files before forwarding them to someone using Windows.

Common things that take some (but usually not much) effort to setup are mp3 support, DVD playback, and video drivers for nvidia or ati cards. Some wireless cards have issues, but I haven't run into anything lately. I commonly run into bugs with Adobe Flash. Overall, the most common problems with Linux tend to relate to proprietary software.

So those are some things to look out for. Without knowing what you plan on using it for it's hard to say what to recommend. Just to to Applications -> Add/Remove Software and install whatever looks good.

> 
1) I am about to install 8.04. Do u think I should wait few more days to install the 8.10? Is there a big difference? What is the difference? When a new version comes out... is that like when Microsoft comes out with a new OS like Vista (and its all crappy and unstable) or is this version system more like the service pack? I hope u understand me.


Well, it's kind of in between a service pack and a new OS. Linux doesn't change in big steps like going from XP to Vista. There are constant incremental improvements (more noticeable than a service pack but less drastic than an entirely new OS.)

Go ahead and install 8.04. You can always update to 8.10 when it comes out. You won't even need to burn a new CD or go through the installation process again. There should be a popup saying 8.10 is released and asking if you want to upgrade.

> 
2) I was playing with the installation to get a feel for it and run into a little problem. I am on step 4 out of 7 where you prepare partitions. Now, I got 3 partitions, I got vista on the first and the second two are empty (I am guessing vista is on the partition that has most used space). So I try to select a second partition to install ubuntu on but I get an error message that says: No root file system is defined. Please correct this from the partition menu... What should I do?


Does the screen look something like the image below? Leave the vista partition how it is (probably the largest used space, type should be ntfs.) Select one of the others for Ubuntu. Set the type to ext3 and the mount point to /. Check format. Be warned that this will overwrite anything on that partition so only continue if it's blank or backed up.

[IMG]http://johnbokma.com/mexit/2008/08/05/ubuntu-install-prepare-partitions.png[/IMG]

---

### Post by scouser73 on 2008-10-22
I had very minor niggles in 8.04 and it was just that I had to restart the PC as sound would cut out, but with 8.10 it's fixed, and although it's still in the last stages of beta it already feels like the finished product to me. I'm glad you've decided to use Ubuntu, and you'll recieve as much help as possible, we have a great forum here as you can see.  So enjoy yourself.

---

### Post by hyper_ch on 2008-10-22
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse brackets around (each) output. That makes it also easier to read.

---

### Post by vedo87 on 2008-10-22
> **daniel.hodge said:**
> Ubuntu 8.10 is almost the same as 8.04. There are some major updates and improvements system wide. There is a website that lists some of the major changes in 8.10. [http://www.ubuntu.com/testing/intrepid/beta](http://www.ubuntu.com/testing/intrepid/beta)

When installing Ubuntu on your second partition, select the edit tab at the bottom. A few drop boxes should show up. You should probably format the partition to ext3, and the mount point drop box should be "/". Once that is done, it should continue installation for you.

Hey thanks!  I installed it successfully (I think). But I run into another problem as you can imagine. :)

When I start my notebook, it starts Vista right away...  and it doesnt ask me what I want... so now I cannot log into Ubuntu at all...  When I go to my computer, I see that windows thinks that that partition where I installed linux that there is nothing, says format it to use it...  Of course I wont do this...

Do u have an idea what should I do to get into ubnuntu, or to ask me what I want to log in?

---

### Post by vedo87 on 2008-10-22
> **tCarls said:**
> I realize daniel.hodge already answered your questions (thanks) but I spent a while typing this so I'm gonna post it anyway.


For the most part things work out of the box. What doesn't work can usually be fixed with some effort. I'd say just play around and post any problems you run into here.

I wouldn't worry about antivirus software. I've never used it with Linux and I've never had any problems. The only reason you might want antivirus software would be to scan files before forwarding them to someone using Windows.

Common things that take some (but usually not much) effort to setup are mp3 support, DVD playback, and video drivers for nvidia or ati cards. Some wireless cards have issues, but I haven't run into anything lately. I commonly run into bugs with Adobe Flash. Overall, the most common problems with Linux tend to relate to proprietary software.

So those are some things to look out for. Without knowing what you plan on using it for it's hard to say what to recommend. Just to to Applications -> Add/Remove Software and install whatever looks good.



Well, it's kind of in between a service pack and a new OS. Linux doesn't change in big steps like going from XP to Vista. There are constant incremental improvements (more noticeable than a service pack but less drastic than an entirely new OS.)

Go ahead and install 8.04. You can always update to 8.10 when it comes out. You won't even need to burn a new CD or go through the installation process again. There should be a popup saying 8.10 is released and asking if you want to upgrade.



Does the screen look something like the image below? Leave the vista partition how it is (probably the largest used space, type should be ntfs.) Select one of the others for Ubuntu. Set the type to ext3 and the mount point to /. Check format. Be warned that this will overwrite anything on that partition so only continue if it's blank or backed up.

[IMG]http://johnbokma.com/mexit/2008/08/05/ubuntu-install-prepare-partitions.png[/IMG]

Thank you! 
As I wrote to the other guy as well...
"I installed it successfully (I think). But I run into another problem as you can imagine.

When I start my notebook, it starts Vista right away... and it doesnt ask me what I want... so now I cannot log into Ubuntu at all... When I go to my computer, I see that windows thinks that that partition where I installed linux that there is nothing, says format it to use it... Of course I wont do this...

Do u have an idea what should I do to get into ubnuntu, or to ask me what I want to log in?"

TO answer your question what will I use it for:  EVERTHING. :)  I dont believe in TV and other forms of media and brainwashing so a GOOD notebook is all I have in my apt. :)  Believe or not, I am PHP/MySQL programmer and I have a hosting account on linux server. :D  But so far I never had or wanted to mess with this...  So, I will need things like Zend, CuteFTP, UltraEdit, some burning tool, something like WMA, something for DVDs and divx, msn, mitorrent, limewire, something for pictures like Photoshop, etc... :)

---

### Post by vedo87 on 2008-10-22
> **scouser73 said:**
> I had very minor niggles in 8.04 and it was just that I had to restart the PC as sound would cut out, but with 8.10 it's fixed, and although it's still in the last stages of beta it already feels like the finished product to me. I'm glad you've decided to use Ubuntu, and you'll recieve as much help as possible, we have a great forum here as you can see.  So enjoy yourself.

Hey thanks for the heads up...  I will upgrade to 8.10 when it comes out...  But how I am supposed to do that?  Do I have to burn again an ISO image and boot it... or I can start it out of Ubuntu without burning it?

---

### Post by vedo87 on 2008-10-22
> **hyper_ch said:**
> It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse brackets around (each) output. That makes it also easier to read.

Thanks for the advices, will keep that in mind. As u can see I just registered and didnt realize I can mark threads as solved until u didnt mention it.

I was thinking to keep this one open for few days and ask a whole bunch of unrelated questions since I am just starting with this and once I get a hang of it, I will close the thread.

---

### Post by vedo87 on 2008-10-22
Hey I re-install ubuntu using this [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4)
blog.  

I tried to do the last step and because I dont have that boot loader...  and when I re installed ubuntu it said fatal error couldnt install boot loader and I went into terminal and typed
sudo gedit /boot/grub/menu.lst and ITS EMPTY!!! How is this possible?  What should I do?

---

### Post by vedo87 on 2008-10-22
Oh man this sucks...  I am going to install everything from scratch.  I want to install xp, vista, and ubuntu.  What should I install first, what second, how many partitions...  give me some advice please.

I found this...  [http://ubuntuforums.org/showthread.php?t=275243](http://ubuntuforums.org/showthread.php?t=275243)  They said xp first, vista then ubuntu.  Now I need somebody experienced to tell me how should I divide my 305GB of space.  ON the other thread it said:

ntfs for xp
ntfs for vista
ext3 for /
(ext3 for /home?)
ext3 for swap

I understand the first 3, but what is that swap?  How do I make that?  And the home?  I am guessing that should be the biggest partition?  Is that the partition that all the OS's will see? How do I do this?

Please help. 
Thanks!

---

### Post by Bluebell392 on 2008-10-22
Install them in this order:

XP, Vista, Ubuntu.

If you install Ubuntu first, Windows will make sure you can't get into ubuntu.

Let windows make their partitions, make sure they are small enough so you can install Ubuntu! In the ubuntu installer, let it resize an existing partition and use the freed space.
swap is a special type of partition, of type swap. It is for when you run out of physical memory, swap acts as extra memory.

---

### Post by tCarls on 2008-10-22
> but what is that swap?

I think swap is called virtual memory in Windows. When you use all of your RAM the OS will use the hard drive as extra RAM, "swapping" the data between RAM and hard drive as needed. I think the rule used to be to have twice as much swap as you have RAM, but with 2GB to 4GB of memory becoming common, that's hardly necessary. I'd say 1GB of swap should be plenty.

It is a good idea to create a separate partition for /home. This is where your personal files will be. The advantage of using another partition is it makes it much easier to install/reinstall an OS. When reinstalling, you can overwrite the / partition and leave the /home partition alone, which means you don't have to back up your files when you install a new OS (although it's still a good idea.)

You mentioned Windows not recognizing the Ubuntu partition. Windows won't recognize it unless you install ext3 drivers. I've never done that so I can't tell you how well it works. I don't know if I'd plan on sharing /home with Windows; you might want to make the Windows partitions large or maybe create a third ntfs partition just to share between xp and vista.

Make the partitions pretty much the same way you created the / partition last time.


```

mount point    type         size
---------------------------------
/xp            ntfs         >15GB
/vista         ntfs         >15GB
/              ext3         ~15GB
/home          ext3         large
swap           swap         ~1GB

```

---

### Post by vedo87 on 2008-10-22
> **Bluebell392 said:**
> Install them in this order:

XP, Vista, Ubuntu.

If you install Ubuntu first, Windows will make sure you can't get into ubuntu.

Let windows make their partitions, make sure they are small enough so you can install Ubuntu! In the ubuntu installer, let it resize an existing partition and use the freed space.
swap is a special type of partition, of type swap. It is for when you run out of physical memory, swap acts as extra memory.

Dude, is there a way to prevent windows from stopping me getting inot ubuntu agian.  I messed up.  I isntalled xp, and ubuntnu...
now I am affraid to install vista...

Ive heard sometihng change the bootloader GRUB into something or to somthing but I dunno how to do this...  Can this be done like through editing that menu.lst? or maybe that startup manager?  If yes... please share how?

---

### Post by tCarls on 2008-10-22
There's no way to prevent Windows from overwriting the boot loader during installation, but you can restore it afterwards.

[How to restore Grub from a live Ubuntu cd.]("http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+grubhttp://ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub")

---

### Post by vedo87 on 2008-10-23
> **tCarls said:**
> There's no way to prevent Windows from overwriting the boot loader during installation, but you can restore it afterwards.

[How to restore Grub from a live Ubuntu cd.]("http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+grubhttp://ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub")

Hey mate, can u explain something to me? 

I installed first, xp, then Ubuntu, then Vista...  When I restart, it cant see ubuntu, only 2 windows... when I install xp, vista and last ubuntu.... still same story, I restart and it doesnt see ubuntu.  How is this possible?  what should I do?

Or lets make it simpler...  (man this is killing me... I am messing with this stuff for 3 days and I cant get it to work...)

Anyway...  I got xp and vista working...  I will re-install ubuntu for the 7th time now, just tell me what should I do when I get to the 7 step, right above the install button there is advanced.  I click on it and it says following.

(checked) install boot loader
default is hd0 (on the scroll menu there are my 5 partitions)
sda ATA 298 GB 
sda1 windows vista longorn loader
sd2 ubuntu 8.04
sda4 is blank 
sda-1 blank

The 2 blank ones nad the ATA 298 are : vista, swap and one big partition where all my stuff will go, I just dont go which one is which...

So tell me?  Do I need to mess with this advanced?  I guess I have to install this boot loader, but where?  So far I tried without touching this advanced, which means it installed it somewhere on hd0 which is the first partition (I guess windows.... thats why I could boot only ubuntu at one of my previous experiments) and I tried ubuntu 8.04 partition... but then I cannot boot into ubuntu, just vista and xp.

Please help.

---

### Post by tCarls on 2008-10-23
> I installed first, xp, then Ubuntu, then Vista... When I restart, it cant see ubuntu, only 2 windows...
That's to be expected because vista overwrites the boot loader.

> when I install xp, vista and last ubuntu.... still same story, I restart and it doesnt see ubuntu. How is this possible? what should I do?
That's odd. Did you try following that link I posted earlier? It's a little more complicated than it should be but it should work without needing to reinstall.

> 
(checked) install boot loader
default is hd0 (on the scroll menu there are my 5 partitions)
sda ATA 298 GB
sda1 windows vista longorn loader
sd2 ubuntu 8.04
sda4 is blank
sda-1 blank

The 2 blank ones nad the ATA 298 are : vista, swap and one big partition where all my stuff will go, I just dont go which one is which...


You listed sda1 twice and didn't list sda3, so I'll assume that blank sda-1 should be sda3. You say "2 blank ones" but then list three: vista, swap and the big one. Also, where's XP?

> 
I guess I have to install this boot loader, but where? So far I tried without touching this advanced, which means it installed it somewhere on hd0 which is the first partition (I guess windows.... thats why I could boot only ubuntu at one of my previous experiments)

The boot loader doesn't go on any of the partitions, it goes on the MBR (master boot record) at the beginning of the drive.

Also, the hd0/sda notation is a little confusing. hd0 is not the first partition, it's the entire drive. sda is also the entire drive, same as hd0. sda1, sda2, (hd0, 1), (hd0, 2), etc. are the partitions. It's confusing. The reason for it is that linux uses the sda notation while the bios uses the hd0 notation.

So do you have four partitions or five? You should have: vista, xp, ubuntu root, ubuntu home, and optionally swap.

> 
(man this is killing me... I am messing with this stuff for 3 days and I cant get it to work...)

I will re-install ubuntu for the 7th time now

I know it gets frustrating sometimes, but I think it's worth it. Hang in there.

---

### Post by vedo87 on 2008-10-23
> **tCarls said:**
> That's to be expected because vista overwrites the boot loader.


That's odd. Did you try following that link I posted earlier? It's a little more complicated than it should be but it should work without needing to reinstall.



You listed sda1 twice and didn't list sda3, so I'll assume that blank sda-1 should be sda3. You say "2 blank ones" but then list three: vista, swap and the big one. Also, where's XP?


The boot loader doesn't go on any of the partitions, it goes on the MBR (master boot record) at the beginning of the drive. So I think you were a little confused when you said the vista loader was on sda1.

Also, the hd0/sda notation is a little confusing. hd0 is not the first partition, it's the entire drive. sda is also the entire drive, same as hd0. sda1, sda2, (hd0, 1), (hd0, 2), etc. are the partitions. It's confusing. The reason for it is that linux uses the sda notation while the bios uses the hd0 notation.

So do you have four partitions or five? You should have: vista, xp, ubuntu root, ubuntu home, and optionally swap.


I know it gets frustrating sometimes, but I think it's worth it. Hang in there.

I am serious man...  I tried about 10 times...  Thats all I've been doing the last 3 days...  

I put in xp and make 5 partitions for: xp, vista, ubuntu, swap and home.  I install xp sp3, works fine, I install vista sp1, works fine...  I put in ubuntu 8.04, come to the partitions, select manual and select the the third partition to be ext3 with / and forth for swap. I come to last step there is that advanced option its says Install boot loader hd0 or something like that...  if I leave like that and install, all I get is ubuntu and cant boot into xp or vista... if I change that to the ubuntu partition nothing happens...  I just have xp and vista like before and cant boot into ubuntu...

---

### Post by tCarls on 2008-10-23
> 
if I leave like that and install, all I get is ubuntu and cant boot into xp or vista... if I change that to the ubuntu partition nothing happens... I just have xp and vista like before and cant boot into ubuntu...


I know you've already been through a lot, but could you get back to booting to ubuntu (where xp and vista don't work.) I think it's your best bet to start from there. It's possible that the menu to select xp or vista is just hidden or maybe there's just no entries for them. When you booted to ubuntu, are you sure there wasn't a brief message for a couple seconds that said press ESC to enter grub menu or something like that?

This thread seems similar, it might be worth looking through: 
[dual boot vista/ubuntu no grub or vista all of a sudden]("http://ubuntuforums.org/showthread.php?t=956399")

> 
I am serious man... I tried about 10 times... Thats all I've been doing the last 3 days...

Yeah, I've been there.

---

