---
title: "thinkpad T20 NIC not recognized"
date: 2005-10-15
forum: Hardware &amp; Laptops
---

### Post by stepore on 2005-10-15
I had this problem with the Hoary upgrade from Warty also. I've filed a bug report twice, no answers. I'm not looking for answers really, just assumptions or theory on why this is happening.

It's a standard thinkpad T20, using the 3c59x module, worked absolutely great in Warty (and 3 versions of mandrake before that).  I won't post dmesg no other error messages, didn't help before. so, here's what i've done.

Warty livecd and install -- works. (3c59x module loads and wired NIC is recognized)
Gnoppix livecd (based on warty) kernel 2.6.7 -- works. 
Linux Rescue CD, using kernel 2.4-26 -- works. 
Simply Mepis LiveCD. using kernel 2.4.?? -- works 
Simply Mepis LiveCD, using kernel 2.6.10 option -- Does not work.

Breezy LiveCD and install Cd -- won't even recognize a Network interface at all during the install of Breezy or using the live CD. Installer asks me if i want to configure a firewire 1394 device for my networking. the Thinkpad T20 doesn't even have a firewire device.

Given all that, does anyone have any theory as to what's going on? Is it strictly a kernel problem, and if so why? it works with some 2.6 - based kernels (warty and gnoppix) but not others.

anyone? anything? i'm dying here.

cheers,
johnny

---

### Post by Azrael on 2005-10-17
Dude, don't die just yet.

I'm typing this in Breezy on a T20 with the same 3Com NIC you have. I also had the same problem as you back when I used Hoary. My 3Com works fine with Breezy though.

Why? Maybe it's because I always boot Ubuntu Breezy with the acpi=off parameter. I suggest you add acpi=off to the Ubuntu boot command in your grub/lilo config file.

HTH

---

### Post by knappen on 2005-10-17
Yes, you should not use acpi on your laptop. I am running kubuntu on a T21 with acpi=off and it detects the network card fine.

---

### Post by stepore on 2005-10-18
[QUOTE=Azrael]Dude, don't die just yet.
Why? Maybe it's because I always boot Ubuntu Breezy with the acpi=off parameter. I suggest you add acpi=off to the Ubuntu boot command in your grub/lilo config file.
HTH[/QUOTE]

Thanks kids -- both of you, Azrael and knappen. I tried acpi=off in Hoary and it didn't work, it even disabled my wireless PCMCIA card, so i didn't even think of it for Breezy. But hell if it didn't work. Cheers!

Since i have you both here, though, and you both use thinkpad T20s, have either of you gotten apm -s or any form of sleep/hibernation to work. i've tried both from the log-off menu and from a shell with 'apm -s'. and it sleeps ok, but after it wakes, i can't start x again? with gdm or just 'startx'. X windows will start coming up, but then just stays loading for ever. never actually getting back up to a gnome-session.

any ideas?

thanks again.

---

### Post by knappen on 2005-10-21
No I have not tried sleep or hibernation.

Sorry!

---

### Post by lu5t on 2005-10-22
[QUOTE=Azrael]Dude, don't die just yet.

I'm typing this in Breezy on a T20 with the same 3Com NIC you have. I also had the same problem as you back when I used Hoary. My 3Com works fine with Breezy though.

Why? Maybe it's because I always boot Ubuntu Breezy with the acpi=off parameter. I suggest you add acpi=off to the Ubuntu boot command in your grub/lilo config file.

HTH[/QUOTE]

I just wanted to say thanks for this bit of information.  I have a thinkpad 600e that I've never been able to get pcmcia to work right on.  Now it works flawless.

---

### Post by knappen on 2005-10-24
Good to hear!

---

### Post by lbjay on 2005-12-14
I have recently gotten this to work my Ubuntu T20 by stopping the pcmcia services before suspend and restarting them after resuming, like so

```
%> sudo /etc/init.d/pcmcia stop
%> sudo apm -s
sleeping...
[resume]
%> sudo /etc/init.d/pcmcia start
```

This is all problably scriptable via apm, but I haven't gotten off my lazy butt to do it yes. Also, starting and stopping pcmcia may be overkill, but I'm just so happy to have it working I don't care.

Good Luck!

[QUOTE=stepore]
Since i have you both here, though, and you both use thinkpad T20s, have either of you gotten apm -s or any form of sleep/hibernation to work. i've tried both from the log-off menu and from a shell with 'apm -s'. and it sleeps ok, but after it wakes, i can't start x again? with gdm or just 'startx'. X windows will start coming up, but then just stays loading for ever. never actually getting back up to a gnome-session.

any ideas?

thanks again.[/QUOTE]

---

### Post by Grugs on 2005-12-22
[QUOTE=Azrael]Dude, don't die just yet.

I'm typing this in Breezy on a T20 with the same 3Com NIC you have. I also had the same problem as you back when I used Hoary. My 3Com works fine with Breezy though.

Why? Maybe it's because I always boot Ubuntu Breezy with the acpi=off parameter. I suggest you add acpi=off to the Ubuntu boot command in your grub/lilo config file.

HTH[/QUOTE]

Hi.  I'm also have a problem getting a pcmcia nic to find a network which can be found with the same card by a windows xp machine (so I know the network is there).  So I'd like to try "acpi=off", but where might I find my "grub/lilo config file".  I tried su - root, then find / | grep lilo, but all I get is:

/usr/share/doc/memtest86+/examples/lilo.conf
/usr/share/vim/vim63/syntax/lilo.vim
/usr/share/locale-langpack/en_GB/LC_MESSAGES/kcmlilo.mo
find: WARNING: Hard link count is wrong for /proc: this may be a bug in your filesystem driver.  Automatically turning on find's -noleaf option.  Earlier results may have failed to include directories that should have been searched.

This is kubuntu 5.10 (installed yesterday - I'm new to ubuntu), the pcmcia card is an "Intel PRO/Wireless" card, model WPC2011NA.

Thanks for any help.

---

### Post by Grugs on 2005-12-22
I had been assuming lilo was already installed.  It wasn't.  So installed it using Synaptic.  At the end of the installation I was told:

It seems to be your first LILO installation. It is absolutely necessary to run liloconfig(8) when you complete this process and execute /sbin/lilo after this.

LILO won't work if you don't do this.


So I ran the liloconfig command, but it then said:

    
    WARNING!
        Your /etc/fstab configuration file gives device /dev/mapper/Ubuntu-root as the root
        filesystem device. This doesn't look to me like an "ordinary" block
device. Either your fstab is broken and you should fix it, or you are
using hardware (such as a RAID array) which this simple configuration
program does not handle. 

You should either repair the situation or hand-roll your own
/etc/lilo.conf configuration file; you can then run /usr/sbin/liloconfig
again to retry the configuration process.
Documentation for LILO can be found in /usr/share/doc/lilo/.


Is getting a pcmcia nic so complicated?  I feel that I am heading down the wrong path.

Note my laptop is not a Thinkpad, but a Dell Inspiron 2500.

---

### Post by djroadrash on 2006-01-01
hello, i think i have the same problem i also have a t20 and it did not recognized the internal ethernet card on install (ubuntu 5.10), i started an other thread but this seems to be the same problem you guys have.
my card is:



mando@ubuntumando:~$ lspci | grep Eth 
0000:00:3.0 Ethernet controller: 3Com Corporation 3c556B CardBus [Tornado] (rev 20)

mando@ubuntumando:~$ lsmod | grep mii
mii 5248 1 3c59x


how do i turn  acpi=off
is it done on the console or on a window?
thanx
:confused:

---

### Post by moondancer on 2006-01-03
[QUOTE=djroadrash]hello, i think i have the same problem i also have a t20 and it did not recognized the internal ethernet card on install (ubuntu 5.10), i started an other thread but this seems to be the same problem you guys have.
my card is:



mando@ubuntumando:~$ lspci | grep Eth 
0000:00:3.0 Ethernet controller: 3Com Corporation 3c556B CardBus [Tornado] (rev 20)

mando@ubuntumando:~$ lsmod | grep mii
mii 5248 1 3c59x


how do i turn  acpi=off
is it done on the console or on a window?
thanx
:confused:[/QUOTE]


try sudo gedit /boot/grub/menu.lst 
add acpi=off to the end of the kernel line

---

### Post by plamtrue on 2006-01-07
I had the same exact problem, and it's been bugging me for a couple weeks now.   I just got it working and here's what I did:  

First I connected my network card directly to my DSL modem, 
bypassing my router.  

Next, upon installing Ubuntu,
at the boot prompt, I entered "linux acpi=off", 

(as suggested in the F3 menu).  That's it.  After install, I got my router working (with a less than average amount of frustration!).  And I even got my wireless pcmcia working!  :razz:

---

### Post by djroadrash on 2006-01-30
i agree, just reinstall and choose linux apci=off, like magic, ethernet device is there. and just have to start firefox. worked for me. thanx everyone.
:-D

---

### Post by r4ik on 2006-01-30
I was looking for this solution thanks a lot guys !!

---

### Post by biddy79uk on 2008-06-18
hi there y'all i just googled T20 NIC and popped this site up,
so here i am :)
anyway i have been reading some of the posts and they are exactly what my problem is APART from i'me running windows xp...
I cant seem to get any driver installed for the network,,,ive heard something about asci = off or something,
ime busy downloading ubuntu now to install on the IBM ThinkPad T20.

as soon as i install ubuntu can anyone Further assist me on how to get a network driver installed and where to get it cos i am going out my mind here...Thanx alot peeps :KS

---

