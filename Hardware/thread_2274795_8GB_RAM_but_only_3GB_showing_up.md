---
title: "8GB RAM but only 3GB showing up???"
date: 2015-04-22
forum: Hardware
---

### Post by goemonburo on 2015-04-22
I have a Dell Inspiron 530 running Lubuntu 12.x, and just put 8GB of RAM into it.  When I look in the Bios Setup, it shows 8GB.  I did Memtest with no errors.  But when I type "free" at the command line once I'm logged in, I'm only seeing 3,209,500 as the total...seems like nearly 5GB is missing.

Or am I just reading it wrong?  

Thank you for any help.

---

### Post by dino99 on 2015-04-22
go back to the bios next time you boot, and uncheck/check the ram setting to enable the full size.

you can also check:
cat /proc/meminfo
sudo lshw -C memory
[http://askubuntu.com/questions/433861/lshw-not-showing-individual-memory-bank-info](http://askubuntu.com/questions/433861/lshw-not-showing-individual-memory-bank-info)

---

### Post by Bucky Ball on 2015-04-22
Can I have a guess you are using a 32bit Ubuntu install?

---

### Post by mrbigmouth502 on 2015-04-22
Hmm, sounds like you accidentally installed 32-bit. Try downloading the x86-64 release of Lubuntu and installing that.

---

### Post by Vladlenin5000 on 2015-04-22
That's a very old machine for 8GB and depending on the exact model it may not support more than 4GB.

The maximum amount of memory is determined by the CPU (and motherboard revision number). Late 530 had quad-core CPUs and those are the only ones in the product line to support up to 8GB RAM (4*2GB, if I'm not mistaken).
- Motherboard's references up to G33M02 (Dell p/n 0RY007) support 4GB only. Therefore:

Only  the combo **G33M03** motherboard (Dell p/n 0FM586) + **quad-core CPU** + **Ubuntu 64-bit** can really work with 8GB RAM in a Dell Inspiron 530.

---

### Post by RobGoss on 2015-04-22
If it's a older machine it may not support 8GB of ram it's good pritace to check the
Machine specs to see how much ram your computer can take befor purchasing it. Older computers were not built to hold a large amount of Ram  especially those that are running Windows Xp I know because I have three and unless I'm willing to replace my mother board some may only hold around 2GB.

---

### Post by goemonburo on 2015-04-22
Thank you for all the answers.  Before even getting the memory I checked uname and I'm running 64-bit Lubuntu.  And the motherboard (if I read the docs right) should support 8GB since it has 4 memory slots, and clearly they all fit fine and the BIOS registers 8GB.  Unfortunately the Service Tag is totally faded to nothing, so I can't tell the model number -- is there another way to tell which motherboard I have?  Is it easily found on the motherboard itself, perhaps?

The first answer above, cat /proc/memory shows 3209500, but lshw -C memory shows 8Gib and 4 banks.  I'm guessing it's just the Bios that needs to be ticked?  

(But why did the Bios show 8GB already?  Which Bios option do I have to click, specifically, to clear that cache?)

Thank you (again!) to everyone with a suggestion.  I'm almost there!!!   :-)

---

### Post by goemonburo on 2015-04-22
Also, @dino99 -- is there any way to do that Bios check/uncheck without being in front of the computer?  :-)  I'm guessing not.  

I am going into the Main Menu's "System Memory" readout and just...unticking it, and then ticking it again?  Even though it says "8GB"?

---

### Post by dino99 on 2015-04-22
> **goemonburo said:**
>  Which Bios option do I have to click, specifically, to clear that cache? 

only your eyes are able, mine cant, as i have no idea about your bios; take time to glance at each tab; on my system (AMI) it is called something like 'extended memory' or so. You might have a few words explaining each setting in that bios i suppose.

with lshw you can get each hardware details (brand, model, n°, ...) ; see the manpage (man lshw)

---

### Post by dino99 on 2015-04-22
> **goemonburo said:**
> Also, @dino99 -- is there any way to do that Bios check/uncheck without being in front of the computer?  :-)  I'm guessing not.  



indeed you cant do that remotedly, you have to call the bios at boot time (very beginning process, usually hiting Del or F2 or ... depending of the machine, often displayed at the bottom screen while boot start.)

---

### Post by goemonburo on 2015-04-22
Thanks so much.  I had no problem with the lshw command...and it shows all four banks and a total of 8Gb.  Has to be a good sign.  I'm guessing it's just a matter of finding that setting in the Bios.  Hope so anyway!!!  :-)

---

### Post by goemonburo on 2015-04-22
So in further poking around, I checked the BIOS version and might this be the issue?  It's old:

BIOS Information
        Vendor: Dell Inc.
        Version: 1.0.10
        Release Date: 12/15/2007

A discussion on the Dell forum says the latest is 1.0.18.  Maybe I need to upgrade the BIOS?

Or is it just a simple matter of if the Bios recognizes the memory (it displays it) then I'm going to be able to use it once I flip the right switches?  

I only have a 2-core processor, however.  Another show-stopper?

---

### Post by Mike_Walsh on 2015-04-22
If, as you say, your machine is an Inspiron 530 series, then according to THESE guys, it'll only take 4 GB of RAM:-

[http://www.offtek.co.uk/ram-memory-2/dell/dell-desktop-memory/inspiron-530/mid86060](http://www.offtek.co.uk/ram-memory-2/dell/dell-desktop-memory/inspiron-530/mid86060)

I've been using them for years, and they're rarely wrong. Mind you, I have an old Dell Inspiron 1100 laptop, from 2002. The manual says a max of 1 GB; but on the Dell forums, people are saying they've installed 2 GB.....and it works perfectly, apparently. So.....you can't always believe the 'experts'...


Regards,

Mike. ;)

---

### Post by Yellow Pasque on 2015-04-23
> **goemonburo said:**
> Or is it just a simple matter of if the Bios recognizes the memory (it displays it) then I'm going to be able to use it once I flip the right switches?

I'm not really sure what "switches" you're talking about.
The BIOS may be able to read the SPD on the RAM sticks and tell you that you have four 2GB modules installed (and commands like lshw and dmidecode will subsequently report that too), but that doesn't mean the memory controller on the mobo can physically address all of it and make it usable to the OS.

---

### Post by dino99 on 2015-04-23
> **goemonburo said:**
> So in further poking around, I checked the BIOS version and might this be the issue?  It's old:

BIOS Information
        Vendor: Dell Inc.
        Version: 1.0.10
        Release Date: 12/15/2007

A discussion on the Dell forum says the latest is 1.0.18.  Maybe I need to upgrade the BIOS?



if you have a bios howto for upgrading it, then go (but take time to check the option(s) twice before blindly hit 'Enter' key. Either the hardware doc or their support might have some usefull tips about that. You should also find the bios changelog to know the diff

---

### Post by goemonburo on 2015-04-23
> that doesn't mean the memory controller on the mobo can physically address all of it and make it usable to the OS

@Temüjin -- thank you for the info.  Do you know how I can verify whether the motherboard IS able to use all the RAM?  

@dino99 -- I tried last night to reboot and find any kind of memory settings in the BIOS.  Alas, the only page with memory on it doesn't seem to be anything with an editable menu.  Other sections deal with boot devices and some settings of the graphics and so on, but I couldn't find anything that seemed to be memory related.  

Definitely I don't want to upgrade the BIOS and risk bricking the system if that's not the actual issue.  Any other ideas?

---

### Post by mörgæs on 2015-04-23
> **goemonburo said:**
> 
Definitely I don't want to upgrade the BIOS and risk bricking the system if that's not the actual issue.

Does googling indicate that there is a risk when upgrading BIOS for your particular hardware?

---

### Post by Yellow Pasque on 2015-04-23
> **goemonburo said:**
> @Temüjin -- thank you for the info.  Do you know how I can verify whether the motherboard IS able to use all the RAM? 

It's best to get the specs from the mobo maker, or in the case of OEM model, from the OEM (i.e. Dell). It sounds like some folks running that board have had success with 8GB of RAM using uupdated BIOS: [http://en.community.dell.com/support-forums/desktop/f/3514/p/19287044/19527076#19527076](http://en.community.dell.com/support-forums/desktop/f/3514/p/19287044/19527076#19527076)

---

