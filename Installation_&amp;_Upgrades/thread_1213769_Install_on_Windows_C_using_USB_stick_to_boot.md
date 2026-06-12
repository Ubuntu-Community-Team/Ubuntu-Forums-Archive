---
title: "Install on Windows C: using USB stick to boot?"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by bit mad on 2009-07-15
Hi everyone.

Would it be possible to install Ubuntu on a Windows machine, but leaving the boot sectors well alone... requiring a USB memory stick to boot up?

Why? Well, the most offputting things to daunted Windows users are
a) re-partioning
b) worries about messing up the boot process or ending up with Ubuntu as the default when we'd rather have Windows as the first choice... not being able to change it... losing the ability to boot, etc.

I've been researching and have tried a few things...
1) I used Unetbootin to run a Live version on a 2GB thumbdrive, which was interesting but not ideal with slow speed and no persistence. It seems that persistence is in its infancy and even when it becomes well understood and easy to achieve, the drawbacks of USB sticks will remain - slow access speeds and worry over wear and tear on the memory that can only take so many write cycles.
2) I installed VirtualBox and Ubuntu.. which works well enough but it's slow and because I'm interested in video editing *(kdenlive and Openshot for example)* I'd rather have a full speed solution.
3) I've found out about Wubi and I can see the appeal but again it has drawbacks of messing with the main bootup, as well as the small speed penalty and reliance upon the integrity of one large file in the Windows NTFS partition. I've been looking around these forums and there are enough people complaining about bootup problems that it really puts me off messing about and risking the main Windows OS.

It strikes me that a hybrid solution using a memory key would be the best of both worlds. Whether it is with a Wubi-like 'loopback' device with everything in one Windows file, or a resized C: drive with a new partition *(backing up is easy, so shrinking the C: and adding a new partition is MUCH less scary to me than risking mucking up the boot!)*... surely it must be possible to install something on a USB key as follows :

- the USB key is used to boot up *(by pressing F8 on the booting machine)* and a program from the memory key scans for (or remembers) the location(s) of the partition(s) (or virtual partitions) and then hands over control to the one selected. The USB key can then be removed so that other keys may be used later, and voila, Ubuntu is running at full speed on the harddrive. And, as a bonus, as there would be so little code actually on the USB key, the remainder of it could be made available as usual on another partition so it still remains a doubly useful USB key.

Is this possible? It strikes me as the least frightening way to get Windows users safely introduced to Linux. Either the Wubi-ish technique with no boot-up risks for the really wary amongst us, or the Real Way on the hard-drive but with a safer boot up - it would certainly seem a lot less risky to leave the normal boot up process well alone unless the USB key is inserted.

Advantages in a nutshell :
* proper hard disk installation running at full speed
* normal Windows boot process unaffected, needs USB key to boot into Ubuntu

It's quite a good security system too, take the key with you and your Ubuntu is safe!

I can imagine some of you will say "Don't be so scared of boot up problems" but the fact remains that problems *do* occur and some of us *REALLY* don't want to risk it. Using a USB stick to boot would be much less worrying. Apologies if this has been possible for years and I simply haven't found out yet!

Thanks.

---

### Post by Herman on 2009-07-15
[You could use  Super Grub Disk for USB]("http://www.supergrubdisk.org/")

---

### Post by bit mad on 2009-07-15
Thanks, but whoah! - that's a bit more than I can bite off and chew.
I was kinda hoping that you gurus would say "hey what a neat idea!" and implement it easily for everyone... :p

---

### Post by Npl on 2009-07-15
AFAIR you can simply choose not to install the bootblock on the first HDD and can specify another device. I know this option is atleast on the alternate CD.

---

### Post by bit mad on 2009-07-15
Thanks Npl, but can that be achieved from one disk to another? Can a boot block on the USB stick point to the right place on the hard-drive and divert the loading from one device to the other? I'm probably too clueless to realise I'm talking ******s I suppose :-#

---

### Post by carml on 2009-07-15
> Ubuntu as the default when we'd rather have Windows as the first choice... not being able to change it... losing the ability to boot, etc. 
Not necessarly,if you edit a line in /boot/grub/menu.lst you can set Windows as the default OS i.e. the one that starts if you don't choose a OS at boot.

---

### Post by bit mad on 2009-07-15
Thanks

But you must admit it's not exactly unheard of to find people asking for help because their boot process is messed up!

That's what us clueless Windows would-be Linux newbies are scared of.... so we'd be a lot calmer about the whole *Try Ubuntu!* thing if our normal Windows OS was not at risk and everthing *(except the small new partition introduced for the experiment) *could be abandoned with no ill effects by just removing the USB key if it all went pear shaped.

Surely it's a Great Idea?! ;)

---

### Post by Herman on 2009-07-15
;) There's a website in my sig link all about boot loaders and how to use the Ubuntu 'Desktop Installation' CD and the 'Alternate Installation' CD too. I think I covered just about everything there is to say about boot loaders and how to install Ubuntu, and how to fix things in case anything goes wrong. It's illustrated to make sure it's as easy to read as I can possibly make it.

If there's something I missed, be sure to let me know. Maybe there's too much information there now.

---

### Post by presence1960 on 2009-07-15
your windows OS is not at risk unless you format it during the install. If you try Ubuntu with GRUB you can still restore Windows to MBR with your windows disk if you have one or with Super GRUB Disk. Unfortunately there is no "easy" way out for you. In fact it is your fear that is making it difficult as all the options mentioned by our forum members are not difficult to do. So maybe you should read and understand what it is you want to do before you attempt to do it. This way you will be familiar at least a little with the process and have some confidence that you can do it. If it is that daunting maybe you should get someone to install Ubuntu for you.

---

### Post by bit mad on 2009-07-15
OK thanks

I understand that it's all simple from your knowledgable perspective, but if it was all so easy, you wouldn't have people on here crying that there boot loader is broken, and Wubi wouldn't have been written as a simple alternative, to entice newbies like me away from Windows!

It's the *perception* of risk that is indeed the problem, people like me see that Ubuntu is there for the trying, then we look into it and browse forums like these... then we see that some people are having nightmarish problems, and it puts us off.

My suggestion was, I believe, a good way (if possible) to make things less scary... but if nobody wants to run with it that's no big deal, I did my best making the suggestion. I'll probably try to stick it on my second drive D: and see if I can select OS simply by selecting which disk to boot from...... but I firmly believe that my big idea would make things much more *"Ok then, why not?"* for a great many people. If that's what the community wants?

Cheers

---

### Post by presence1960 on 2009-07-15
All I can do is share my experience with switching from windows to Linux. I rushed to install Ubuntu. I did not do what I suggested for you to do, which is to read and familiarize yourself with the process. So I went to install Ubuntu thinking I know computers but really all I knew was windows. The result was at the Prepare disk space of the install I chose the option that wiped my hard disk and installed Ubuntu on the whole disk. I lost windows and all my files. Luckily I made backups every week so at least I still had my files. I was so mad and blamed Ubuntu. I reinstalled windows and began to read about the process of installing Ubuntu. That reading showed me that it was really my fault that my windows and all my files were toast. It was my total lack of preparation and total lack of having at least an idea of what I was trying to do that was my downfall.

Installing an OS from scratch should not be taken lightly as say- installing a program like MS Office or Open Office. It is a world of difference. If you have never installed an OS before you have to do prep work to get up to speed! Installing Windows from a recovery disk(s)/partition does not really count as installing an OS because the partition or disk(s) do all partitioning/formatting of the hard disk(s) and install all your device drivers for you. And it installs all your programs that came with your machine.

Now if you have ever installed Windows from an OEM/retail installation disk then you have an idea what it is like installing an OS. You have the ability to partition/format your disk and windows itself does not have all the device drivers for your hardware. After the install you must install these drivers for your hardware to work. Then you must install all your programs as well!

Our community documentation is very good at preparing you to install Ubuntu. It really can't be any simpler, but you need to do the legwork to insure you somewhat understand what you are about to embark upon. Here are a few links to get you started:
[https://help.ubuntu.com/community](https://help.ubuntu.com/community)
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)  -for a pdf Ubuntu pocket Guide which has a very good step by step how to on installing Ubuntu and much more.

I would make a backup of all my data because murphy's law is always waiting for someone who tries to skip a step or two. 

As far as making it easier to install, I don't think that is possible. It is pretty easy & straightforward I think. All it takes is some prep to get it right. Fortunately Ubuntu is not like windows, which by the way I am forever thankful. I believe it is a case of being new rather than being difficult. I had to unlearn all those window-isms and bad habits I learned over the years using windows. With a lot of reading and this community it was a breeze.

Now I ask how bad do you want to get off windows? If it is that bad invest some time studying before you try installing Ubuntu. You have been using windows how long? I don't think another couple days to a week will hurt you. I use Ubuntu because I want to. I don't really care if another single person chooses to use it, that is what choice is all about. But I will try to be helpful to anyone who wants to try Ubuntu. Ubuntu is what it is and didn't get where it is by trying to be like windows. When in Rome do as the Romans do. learn the Ubuntu way and you will see it really is easy but very different from what you are used to.

---

### Post by bit mad on 2009-07-16
Thanks for your help, personally I'm happy to invest time and effort into it but there are lots of people out there who just want it made as easy as possible. Get them in, hooked, and the additional learning and personal IT growth can follow later!
I was under the impression that the Linux world wants to attract as many followers as they can get.

cheers :)

---

### Post by sangup on 2009-07-16
I totally agree with your idea. I am also trying to install Ubuntu on my system and scared that it will break something. It would be great if someone can create a very easy solution. I think the pen drive linux with persistence is a great idea however if the casper-rw file can be setup on the hard disk so that read and write speeds are faster and USB is not read - write everytime that can make for a very good solution also.


> **bit mad said:**
> Thanks for your help, personally I'm happy to invest time and effort into it but there are lots of people out there who just want it made as easy as possible. Get them in, hooked, and the additional learning and personal IT growth can follow later!
I was under the impression that the Linux world wants to attract as many followers as they can get.

cheers :)

---

### Post by presence1960 on 2009-07-16
> **bit mad said:**
> Thanks for your help, personally I'm happy to invest time and effort into it but there are lots of people out there who just want it made as easy as possible. Get them in, hooked, and the additional learning and personal IT growth can follow later!
I was under the impression that the Linux world wants to attract as many followers as they can get.

cheers :)
Don't believe the hype! Sure there are those who use Linux who are more than over-eager to convert the masses. But Linux and open source is about choice. Each chooses which OS he/she wants to use and I respect that. Without my respect of other's choice of OS how can I ask that my choice be respected? A real Linux user respects other's choices as well as his/her own and isn't out to convert the masses. Linux for the most part is not a for profit business enterprise and as such it does not matter how many people use Linux. it exists solely as an option for those who choose to use it.

Again it is your fear that is keeping you from trying Linux. It is pretty simple to install once you understand the process. And herein lies the problem- you haven't learned enough about it to overcome your fear. Linux is not for everyone and if you can't get past the fear of installation I would suggest you hold off until you can overcome that internal obstacle of yours.

If you are that adamant about changing the installation process then you should join the development team.

---

### Post by bit mad on 2009-07-17
Thanks for the replies, thanks sangup for seeing things from my point of view and for taking the time to write.

presence1960 I understand your viewpoint too, good job we're all welcome to  differing opinions :D

Well, in the unlikely event that nobody has thought of it before, at least I've done as much as I can - float the idea and see if anyone else thinks highly enough of it  that they move it onwards to those who can do something about it. That's all I can hope for.

I do believe the hype - I think there are committed people that want to help others to learn and progress. Getting Windows users to try Linux is a Good Thing IMHO. Anything that can be done to make it less daunting is worthwhile. Removing all fears of bootup catastrophes can only help.

Cheers

---

