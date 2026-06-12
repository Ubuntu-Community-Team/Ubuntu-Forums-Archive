---
title: "Re-considering Ubuntu"
date: 2008-09-09
forum: General Help
---

### Post by enbuyukfener on 2008-09-09
**[SIZE="4"]Problem:[/SIZE]**

I am using Arch and liking it however there are a few issues such as suspend to RAM that worked fine on Ubuntu out of the box that I miss. Other things include the fact that I have a laptop, that it is a Dell, and it had some nice modifications to things such as a safety net for kernels all done for you.

One thing that's important is the ability to install programs outside repositories. Maybe Ubuntu's repos have grown in size mitigating the issue but I don't want to bother with compiling and errors associated with the process as well as the lack of integration with the package manager unlike with Arch's "yaourt". I heard about "checkinstall" late into my Ubuntu usage which seems to be the closest solution.

Basically, what is the current status with such programs and is it a hassle to keep such programs up to date? Has the status changed much over the last year, or are there more deb's available? One of the biggest problems I had was VMWare Server if you want an example.

I would usually not consider this but I am planning on a fresh start with Linux so it wouldn't be much more hassle to use Ubuntu instead. Suspend to RAM not working, an annoying method to enable scanning, boot jargon, network warnings when shutting down that slow the shut down process down and other issues.

Any thoughts?

**[SIZE="4"]More background:[/SIZE]**

I used to use Ubuntu 7.04 (or was it 6.10?) and liked it however I stopped after a few months for a few reasons:
[LIST]
[*]content not in repositories was a pain to install, especially if I had to compile where I never expected an error
[*]had to use a hackish solution for wireless
[*]a number of other hacks not Ubuntu specific for getting certain hardware
[*]lacklustre 2D performance when using nvidia driver
[*]some minor problems such as Fn-F7/F8 not working
[/LIST]

Arch Linux seemed to solve most of those problems
[LIST]
[*]AUR meant I never compiled anything for the 12 or so months I've had Arch
[*]Networks were easier to configure through text files
[*]not Arch specific but a fresh start with more knowledge helped
[*]lacklustre 2D performance remained until nvidia 177.68 driver
[*]some minor problems remained
[/LIST]

Other pros and cons of Arch were rc.conf, leaner OS but suspend to RAM only works sometimes despite trying every other method

Now, there has been some changes:
[LIST]
[*]nm-applet now works properly for wireless and encryptions
[*]nvidia 177.68 is out, solves poor 2D performance and Fn-F8 (though the resolved issues were not Ubuntu specific)
[*]other general improvements
[/LIST]

---

### Post by Rocket2DMn on 2008-09-09
First and foremost, we suggest what works best for you.  If you want take Ubuntu for a spin again, a first step would be to try in the LiveCD environment.  You can't test everything here and it is limited in its capabilities, but hopefully you can check some things.
You can also setup a dual boot to make sure that Ubuntu really is what you want to switch back to.  You may want to check the repositories, too, to make sure the programs you want are available.
You can certainly try browsing the forums to see what problems people might be having with your hardware.

---

### Post by enbuyukfener on 2008-09-09
Now that you remind me, I forgot all about the spare 3GB partition I had, that will be perfect.

A live CD never done justice for me when it came to reviewing an OS though.

---

### Post by Rocket2DMn on 2008-09-09
3GB is pretty small, I'm not sure it's big enough to do much with using a regular install.  I think you could fit an install on it, but it would be tight.  Maybe try a minimal install - [uhelp]community/Installation/MinimalCD[/uhelp]
You might have to do more configuring afterward though because it won't come with a lot of utilities (it downloads everything during the install process, so should only get what you need).  This should at least give you the ability to test most stuff.

---

### Post by enbuyukfener on 2008-09-09
Wow... Ubuntu is hungry! I will resize partitions after awhile but I thought 3GB would comfortably fit a standard desktop installation.

---

### Post by Rocket2DMn on 2008-09-09
Om nom nom!
I think a standard install is like 2.2 GB actually.  Just not a lot of breathing room.

---

### Post by Flimm on 2008-09-09
You might like [Linux Mint](http://www.linuxmint.com). It's supposed to be more bleeding edge than Ubuntu, though it's based on Ubuntu.
EDIT: Actually, maybe not. I should do more research on it first.

---

### Post by enbuyukfener on 2008-09-09
I've had enough problems with apps to worry about bleeding edge. Ubuntu seems to be a nice balance.

Rocket2DMn, thanks for pointing that out, that was closer to my expectations (the reason I made it only 3GB)

One last question was about dealing with stuff not in repos? Do I have to settle with checkinstall to something similar?

---

### Post by Rocket2DMn on 2008-09-09
It depends on the program - some projects release .deb installers on their websites.  I never found checkinstall to work very well, and just ended up using make install on the very few programs I ever needed that weren't in the repositories.
Specifically, what programs do you need to know about?

---

### Post by oldos2er on 2008-09-09
I would agree with you that Ubuntu is very unfriendly to those who want to compile their own programs; I don't understand why gcc isn't included by default. I don't use Vmware, so I can't comment on that, but in general I haven't had major problems compiling/installing source code--but I don't mind searching around on my own to solve the problems one encounters in doing so. Others may.

 I run Vector Linux most of the time, so take my opinion for what it's worth!

---

