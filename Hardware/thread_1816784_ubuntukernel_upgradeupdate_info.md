---
title: "ubuntu/kernel upgrade/update info"
date: 2011-08-02
forum: Hardware
---

### Post by ruseriousb511 on 2011-08-02
Hi everyone !
    Ok so I got this computer (laptop) from e-bay and it has Linux installed on it which is perfectly fine with me but since I did not install it I do not know much about how to go aabout this process. I have an HP Compaq Presario X6000, it has Linux 2.6.32-22-generic installed on it with Ubuntu 10.04 Lucid and Gnome 2.3.
    I tried to update to Ubuntu 10.10 Maverick and got this message :
                 "Not all updates can be installed, can be caused by :
                   * a previous update which did not complete
                   * problems with some of the installed software
                   * unofficial software packages not provided by Ubuntu
                   * Normal changes of a pre-release version of Ubuntu
How do I know which one it is ? How do I fix it ?

When I went to actually do a "partial download" I get this message :
                 "Aborted download upgrades" = problem with internet connections (which are strong and running properly) or problem with installation media ( not sure how to check/fix ). It also says "failed  to fetch security.ubuntu.com......long list of characters and stuff. Anyone know why or how I can get to fully finish ?

Also since my kernel (which I would REALLY like to upgrade) is a kernel version 2.6.32-22.generic what would the best next kernel to upgrade to be ?Is this like the distos. where you have to go from one to another or can I jump from this to the new 3.0 ? I am familiar with kernel upgrades on tablet pc's as I have a ZT-180 that I have upgraded the kernel on and rooted. How do I go about the upgrade ?

I AM a newbie to Linux/Ubuntu but since I did not actually install these systems and I have no way to contact the person who did I am that much farther behind. ANY help or direction to the right forums, instructions, tips, or advice would be VERY much appreciated.

Thank you all for your patience help and understanding in this matter. Please take it easy on me and again, Thank you.

---

### Post by Beacon11 on 2011-08-02
How much have you used this computer? Or, let me rephrase-- how much would you lose if you reformatted and reinstalled? I would highly recommend doing that-- who knows what happened to the install before you got it.

Beyond your issues, I wouldn't trust it. Would you trust a computer from ebay that had Windows preinstalled? Just because your computer came with Linux on it doesn't mean its previous owner couldn't have done something nasty.

There are plenty of guides out there on how to install Ubuntu, but let me know if you want some pointers or have questions.

---

### Post by Metaxa on 2011-08-03
I second his statement. I would download 10.04.03 from [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download), burn the .iso and follow the installer. It is straight forward and starts you off with a fresh machine.



Metaxa

---

### Post by ruseriousb511 on 2011-08-04
ok so there really isnt much on the pc as far as things I have put on it. My internet bookmarks are about it. 

So should I update the kernel as well as re-load Ubuntu or just re-load Ubuntu 10.04 ?

I understand what you are saying as far as trusting what the previous user may or may not have put on this but the guy that sold it said the guy was really good with computers, but who knows. 

So so I upgrade kernel and then Ubuntu 10.04, or just Ubuntu 10.04, and after I download 10.04 should I then update to 10.10 maverick or leave it at that ?

As I said I am prety new to this but I am totally willing to learn, there is so much about this system and I have been reading for days but its kind of overwhelming for a newbie.

Ill take all the help and pointers I can get, so what do you suggest ?

---

### Post by Metaxa on 2011-08-04
I would do the following:

Download 10.04.03
Burn the CD
When you boot from it choose the "try it" option instead of install to check if all your hardware works properly and that you can access the Internet, then...

Start anew with this machine. The main reason for this is you know everything you are doing to it and any changes that may be required. When you do a fresh install of 10.04LTS it will give you the latest kernel for that release. The LTS designation tells you that it is for long term support, meaning it has been highly tested and is very stable. LTS distros are generally support with security updates and the like for a good amount of time while non-LTS are not. 

You may choose to upgrade to 10.10 as some people do but stability is not guaranteed and some of your hardware may react differently to it, not always the case but it may happen. Once you are more comfortable with the life cycles of different distributions you may want to move up to the newer ones.

On a side note, while you have this machine running you should do some research into potential problems with your hardware that may arise, (wireless card, video card, etc.)


Metaxa

Long time user, uses Google to solve my problems

---

### Post by ruseriousb511 on 2011-08-04
So I burned the cd and everything went fine, I went to actually install the system by erasing the old and replacing with the new when the prompt came up.  I went through all of that and went to install and I got a new error prompt saying " ubiquity suddenly stopped" and that was it. Nothing else happened and it was over without installing the full version to use without the cd.

I do not understand what happened with this and if you could explain it it would help or if you could tell me what went wrong to cause this.

I was unable to install after I got this force close error, why what happened ?

---

### Post by Beacon11 on 2011-08-05
> **ruseriousb511 said:**
> I went through all of that and went to install and I got a new error prompt saying " ubiquity suddenly stopped" and that was it. Nothing else happened and it was over without installing the full version to use without the cd.

Ubiquity is the graphical installer. Is that the exact message it gave, with no other information? Check the MD5 sum on the download if you can, make sure you got a good iso. On the boot part, where you selected "try before install," there was an option to verify the disk. Do that as well, to make sure the disk you burned has no issues.

> **ruseriousb511 said:**
> I understand what you are saying as far as trusting what the previous user may or may not have put on this but the guy that sold it said the guy was really good with computers, but who knows.

That's actually all the more reason to reinstall. I'm pretty good with computers myself, and if I was slightly more evil, I'd sell computers bundled with keyloggers etc. to try and get bank account information. Windows isn't the only operating system susceptible to those things :) .

---

### Post by ruseriousb511 on 2011-08-06
can you tell me how to check the md5 info on the download ? Like I said im a newbie and some of this stuff goes over my head.

Another thing I was wondering, can I download and install a completely different OS instead of this Ubuntu lucid ? something like Dreamlinux, Debian 6.0.2, Mint, or even directly try to install Ubuntu 11.04 natty, I was wondering because I have a Linux OS package that has 5 different complete linux os's on it and I was thinking of completely switching over to something different. Is this o.k. and possible ?

---

### Post by RafalCOM on 2011-08-06
if you already deleted the previous installation it's a great time to try whatever you want. Just give them a shot and see. You will not break anything. Just every time use a clean instal and see. If I were you I would try natty.

---

### Post by gordintoronto on 2011-08-06
Mint 11 might save you a little bit of learning curve. Ubuntu 11.04 has better community support.

Different kernel versions have different device support. For example, I have a USB wireless adapter which "just works" in Ubuntu 11.04, but not in earlier versions.

---

### Post by ruseriousb511 on 2011-08-06
cool thanks guys, now to decide which one I want to go with, LOL, there are SO many choices but I need one that is more stable than not so ......

---

