---
title: "AMD Mobility Radeon HD 4225/4250 Driver/flgrxv"
date: 2013-05-26
forum: Hardware
---

### Post by samgabbay on 2013-05-26
[COLOR=#000000]I have a big issue here[/COLOR]





[COLOR=#000000]I have a AMD Mobility Radeon HD 4225/4250 and when i install the fglrxv and   i reboot it wont show the whole unity desktop like no launcher and no upper bar,  [/COLOR]



[COLOR=#000000] if i shouldnt be using fglrxv how do i install the driver i downlaoded off the amd site and make sure that the unity stuff stays [/COLOR]

[COLOR=#000000]i have ubuntu 13.04 and its like fresh and brand new and its fully up to date.  [/COLOR]

[COLOR=#000000]please assist me[/COLOR]

---

### Post by QIII on 2013-05-26
Hello!

The first thing is that the fglrx driver you will find in the repo *is *the same driver you will find on AMD/ATI's website -- which Canonical gets from AMD/ATI prior to release to the general public.  It has just been packaged for the repo.  Downloading and installing from the AMD/ATI website will do you no good.

Unfortunately, AMD/ATI has dropped driver support and development for all cards prior to HD 5000 series.  That means that your HD 4000 series will not work with any version of Ubuntu later than 12.04.1, which is to say 12.04.2 and later.

This is not a problem with Ubuntu, but a decision on the part of AMD/ATI.

There are methods given on the web for downgrading X Server, patching the kernel and installing a legacy version of the driver.  However, I recommend so strongly against that that I don't provide links or suggestions for doing that.  I am opposed to such methods for two reasons: 

1.  Using them effectively breakes your installation and ***nobody*** can say for sure what sort of problems you will encounter with updates/upgrades in the future.  Although you can hold some packages to avoid updates, holding those may mean you either can't update other packages or you will end up with broken packages later.  Few of the PPAs and scripts that do the work tell you what you are doing to your system or inform you about the potential future effects of their use.

2.  Those older cards will work with Ubuntu 12.04 and 12.04.1, which still have 4 years of support left -- and you don't have to worry about a broken system.

As I see it, you have two choices:

1.  Back up to Ubuntu 12.04 or 12.04.1 with the fglrx driver in the 12.04 repo and use it for 4 years without worrying about breakage -- as long as you don't install a newer driver.

2.  If you use 12.04.2 or later, use the default open source Radeon driver that is present when you install Ubuntu.  The developers of the Radeon driver have done some very hard work on improvements and the driver is really good now.  Although it may not have many of the features of the proprietary driver, it at least works with earlier cards and later versions of Ubuntu.

I'm sorry I don't have better news.

Best wishes!

---

### Post by samgabbay on 2013-05-26
can u give me a guide on hwo to do this i badly need my drivers :/

---

### Post by QIII on 2013-05-26
As I said, I won't give you instructions on how to break your system if you are using 12.04.2 or later.

Would you prefer to install 12.04 or 12.04.1?

---

### Post by samgabbay on 2013-05-26
not really but i jsut want to get the drivers working to be real with you

---

### Post by QIII on 2013-05-26
OK.

I won't help you do that on 13.04 because I feel so strongly about it.  However, there are a couple of people who would probably be willing to help.  If Temujin answers the thread, you can trust absolutely in his technical expertise and be assured you will not be led astray.

***Do not PM him***.  He will probably not answer a PM request for help and we don't like that anyway, since PMs don't show up on the forum for others to learn from.

Best wishes.

---

### Post by samgabbay on 2013-05-26
thanks btw i cant find version.h

---

### Post by samgabbay on 2013-05-26
can i downgrade install teh drivers then reupgrade?

---

### Post by QIII on 2013-05-26
No, unfortunately not.  When you upgrade from, say 12.04, you really should uninstall the fglrx driver first.  Leaving drivers installed when upgrading is a very good way to have the upgrade fail.

---

### Post by samgabbay on 2013-05-26
oh well is there really nothign i can do about my graphics card because i wanna play some games :(


can i install the windows drivers with wine and use it?

---

### Post by Mark Phelps on 2013-05-26
> **samgabbay said:**
> oh well is there really nothign i can do about my graphics card because i wanna play some games :(

can i install the windows drivers with wine and use it?

NO -- Wine can NOT be used to install drivers.  And even if it could, they wouldn't work because you need Linux drivers, not Windows drivers.

And ... I strongly support the advice against hacking your system to allow the X-server downgrade to install the older version for the fglrx drivers.  You will almost certainly enounter problems down the road doing this.

---

### Post by samgabbay on 2013-05-26
im going back to 12.04 cuz my drivers are supported there and il wait for 14.04 or whatever is next to come out

---

### Post by QIII on 2013-05-26
The situation will not be changed by future versions.  However, since 12.04.1 is supported for 4 more years, you have plenty of time to plan a new purchase. :)

---

### Post by Yellow Pasque on 2013-05-26
> **QIII said:**
> Temujin ... will probably not answer a PM request for help
I turned off PM's years ago :P

The most likely negative outcomes of downgrading X is that you have issues:
- installing/upgrading packages
- with the default Ubuntu desktop (Unity)

I personally don't consider those catastrophic, as long as I can live with xfce desktop (which I personally like better) and can boot to a terminal or LiveCD, back up my data, and do a reinstall. If a sudden borked system and/or impromptu reinstall doesn't bother you, then check out: [https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)

Obviously, you should have some backup OS/partition as a more stable option if you need your system for work/school. Consider yourself warned!

---

### Post by samgabbay on 2013-05-26
Hahah but can u help me with installing my drivers on 13.04 its super annoying i downgraded the server install the drivers did a tun of things then my system wouldnt boot and thats were i knew something doesent work

Can you tell me how i can install it 

Btw i found this but i dont know if it would work (i just googled this) 

[http://www.thefanclub.co.za/how-to/ubuntu-amd-catalyst-install](http://www.thefanclub.co.za/how-to/ubuntu-amd-catalyst-install)

---

### Post by Yellow Pasque on 2013-05-26
> **samgabbay said:**
> then my system wouldnt boot

Can you be more specific? Where did the boot process get held up?

---

### Post by samgabbay on 2013-05-26
> **Temüjin said:**
> Can you be more specific? Where did the boot process get held up?

After selecting ubuntu on grub then it becomes blue then it flashes then stays black

---

### Post by Yellow Pasque on 2013-05-26
You were supposed to follow the directions on the link I gave you...
```
sudo add-apt-repository ppa:makson96/fglrx
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install fglrx-legacy
```
I've never seen that installer program before and I have no idea what it does exactly or whether it's reliable.

---

### Post by samgabbay on 2013-05-26
I did that but when i do i dont see the status nor taskbar after boot

---

### Post by samgabbay on 2013-05-26
I tried installing it from the app store and thats when i got the probelm, isint it the same?! And i did what i said too and it resulted in losing unity taskbar and status bar

---

### Post by Yellow Pasque on 2013-05-26
Well, the owner of the PPA does warn of Unity not playing nicely. I have no idea what state your system in and not sure exactly what package you installed from the 'app store'. If you can get /var/log/Xorg.0.log posted, that might help. Otherwise, drop to a terminal (Ctrl+Alt+F1) and use these commands to get back to the default setup (open-source radeon driver): [http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Removing_Catalyst.2Ffglrx)

---

### Post by samgabbay on 2013-05-26
> **Temüjin said:**
> Well, the owner of the PPA does warn of Unity not playing nicely. I have no idea what state your system in and not sure exactly what package you installed from the 'app store'. If you can get /var/log/Xorg.0.log posted, that might help. Otherwise, drop to a terminal (Ctrl+Alt+F1) and use these commands to get back to the default setup (open-source radeon driver): [http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Removing_Catalyst.2Ffglrx)

Yea but if i remove catalyst then will it remove the driver?

---

### Post by Yellow Pasque on 2013-05-26
fglrx/catalyst IS the driver, so yes.

---

### Post by samgabbay on 2013-05-27
> **Temüjin said:**
> fglrx/catalyst IS the driver, so yes.

Alright so i did what u said and same thing black screen after grub

I had to reinstall ubuntu

I have a 64 bit system btw

---

