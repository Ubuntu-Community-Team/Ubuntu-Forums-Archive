---
title: "Livecd freeze on install"
date: 2006-07-02
forum: Hardware &amp; Laptops
---

### Post by fra1027 on 2006-07-02
Hi all,
I have an HP pavillion notebook (ze5507ea) and I try to install from my Ubuntu livecd but my drive (dvdrw) speed is very slow and install freeze while load the first step of installation. I try to "transform" my livecd into livedvd but I receive on boot "ISOLINUX image checksum error". I changhe "md5sum.txt" file but I receive  the same error.

It's impossible to install ubuntu on my laptop? 
Please don't answer yes. :P

How "transform" correctly into livedvd?

Thanks in advance for your answer.

---

### Post by fra1027 on 2006-07-02
Anyone can't help me?

---

### Post by fra1027 on 2006-07-07
Ok, I have an idea! :D
I read this post: [URL]http://ubuntuforums.org/showthread.php?p=687306#post687306
[/URL] 
and I have decided to boot from hdd.
I try to modify my menu.lst in different mode but I receive error in mount filesystem or bad root directory.
How I do to boot from hdd?
Migth I modify something file thath I copy on hdd?

---

### Post by awahl on 2006-07-08
Try using the Alternate Install CD - It works great for older machines. It's in the Downloads section, the third option (after Desktop & Server). It worked for me (after having similar problems with the Live CD) on a circa 1998 IBM ThinkPad.

Cheers & HTH

Andy

---

### Post by awahl on 2006-07-08
...also make sure yuu check your MD5sum after downloading...You want the checksum on your download to match the text file.... not vice versa.

---

### Post by fra1027 on 2006-07-08
Thanks for your answer.
I have a 56k modem (I can't download alternate or another live)and I have the "official" livecd of shipit.. it is arrive the 1st July.
Can you have a suggestion for my idea of boot from hdd?

---

### Post by fra1027 on 2006-07-08
Oh, I have an actual machine... bougth in 2003. But it has only 256MB.. maybe this is true problem...
But I'd like to try to boot the contenent of live cd(copied on hdd) with grub.

---

### Post by awahl on 2006-07-08
Your machine is not that old, and 256mb is probably not the issue. 

You mentioned that you received a checksum error during install? That's surprising with a shipit CD...

Are you running any other operating system on the laptop?

Do you have access to any broadband connection (work) - where you could download the alternate install?

I am not sure what you mean by installing "from"the HDD....?

---

### Post by awahl on 2006-07-08
sorry for throwing so many questions at you, but I have ten other things going on and not paying attention too well...

The option to boot from HDD only works if you have an os loaded already (like another version of Ubuntu or even windows.

What happens when you boot without the CD in the drive?

Also, there are options you can give at the command line for install. When the live cd first boots up, there are some options you can run at the command line that may help with the install. I believe there is a help option (f4?) that let's you see the list of options....

;)

---

### Post by fra1027 on 2006-07-08
The "official" livecd boots and load Ubuntu 6.06, but when I try to install from ubuntu desktop, the dvd drive (for cd) is more more slow and the install procedure don't load.
I had an idea!!.. I "transform" cd in dvd but don't works.
Then I changed.
Another idea(my curent idea.. :P) is to boot from hdd as DSL or Puppy.. please read post that I linked up^^.
It's all rigth to boot laptop with grub and other os(Win xp, win2k) but with ubuntu 6.06 (files on cd copied to hdd)I need to configure correctly my menu.lst. 
I try to do this but receive error to mount filesystem or on root dev.
Plese, help me to configure.

---

### Post by fra1027 on 2006-07-09
Up.. :)

---

### Post by stevieb on 2006-07-09
> **fra1027 said:**
> Hi all,
I have an HP pavillion notebook (ze5507ea) and I try to install from my Ubuntu livecd but my drive (dvdrw) speed is very slow and install freeze while load the first step of installation. 

I had the same problem with my new Lenovo 3000 C100, and the alternate install CD did the trick.  One thing- make sure you read up on partitioning before you wipe out Windows like I did :oops: .  I have to say, though, that I am psyched to have a linux-only laptop! :cool:  Now working on getting the Broadcom 4319 up; making progress.  Thanks to all who give advice in these forums!  :KS 

-steve

---

### Post by fra1027 on 2006-07-09
Yes the alternate cd it's solution.. but I don't download.. I have a 56k connection. Sorry, if I always say the same thing.. :) 
But Is it impossible to boot from hdd with contenent of livecd?
Because I try and seems to work but  at the end I receive error... Which is the "cool" string to boot with grub and Ubuntu live?

---

### Post by awahl on 2006-07-10
Hi There... 

Not sure if you've got this going yet. I read the post re booting DSL/Puppy from the HDD, but I believe they are referring to an image file located on the hdd being used to run the "live cd" - versus the CD itself. It may be possible to install from that with the proper partitioning, but frankly it sounds a bit more complicated than necessary...

Another option is to try loading the "Server Only" version of Dapper Drake. Unless you have similar drive/freeze-up problems, that will get you minimal install to get things going. From there, you could use apt to get the Ubuntu Desktop (or Xubuntu/Kubuntu).... You should be able to find plenty of resources here for what packages you need. To install server version, type "server" at the install prompt. 

Otherwise - best option is to just download the alternate install CD - Can you log in and leave it on to download overnight...?

Hope this helps...

---

### Post by fra1027 on 2006-07-11
Yes method of DSL/Puppy is complicated but seems the rigth way..

I type "server" at boot but I receive "could not locate kernel image" or similar.. I try to type "live server" but starts livecd in normal mode.

Sorry but the alternate is more more big file for me && my 56k.

---

### Post by fra1027 on 2006-07-13
up

---

### Post by fra1027 on 2006-08-23
I "upgrade" my initial post to tell you thath finally I download the alternate 6.06.1 cd but the install freeze on "wdial conf". Which is the problem?
I have an conexant modem on my notebook, maybe it is the problem?

---

### Post by fra1027 on 2006-08-29
Come on!
Give me an help!

---

### Post by fra1027 on 2006-09-19
SOLUTION:
I install (alternate) breezy and then upgrade to dapper.
I have the "wdial conf" problem but I press "CTRL C" and the breezy install, then upgrade to dapper and install new version on wvdial.
Thanks a lot to all that reply me but I must say thath I don't find the solution in this place. :(

---

