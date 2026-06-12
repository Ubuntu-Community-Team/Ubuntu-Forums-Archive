---
title: "Various Things with Acer Aspire One w/3G built IN"
date: 2009-04-27
forum: Hardware
---

### Post by lfmiller on 2009-04-27
Radio Shack is selling an Acer Aspire One with AT&T 3G built into it - nice netbook - And it just went on sale again!!! $50 bucks - SO I bought one - 
I have two problems - The first is this netbook comes with WinDoze XP on it - (Ok, truely this isn't the frist problem...just figured I would make people laugh) - I bought the display model - And it looks like the store told the thing to never ask to make the backup discs for the hidden partion - so my true first problem is how to I get to the hidden partion and do a backup before I install UNR to this - I only want to do this because it is a legal copy of windoze - So i would like to back that up before I make major changes -
My 2nd and probably more important problem - This netbook comes with a Qualcomm 3G modem built into - I am using the "Live CD" - usb flash of 9.04 UNR currently not installed on the netbook till I solve the first problem - 
BUT I can't get it too connect to the AT&T wireless network - I know I am doing something wrong - I did a dmesg and here is what it says:
[ 2311.322149] atkbd.c: Unknown key pressed (translated set 2, code 0xc4 on isa0060/serio0).
[ 2311.322165] atkbd.c: Use 'setkeycodes e044 <keycode>' to make it known.
[ 2311.329125] atkbd.c: Unknown key released (translated set 2, code 0xc4 on isa0060/serio0).
[ 2311.329141] atkbd.c: Use 'setkeycodes e044 <keycode>' to make it known.
[ 2312.184123] usb 1-6: new high speed USB device using ehci_hcd and address 10
[ 2312.322661] usb 1-6: configuration #1 chosen from 1 choice
ubuntu@ubuntu:~$ lsusb
Bus 001 Device 010: ID 05c6:9211 Qualcomm, Inc. 
Bus 001 Device 003: ID 0c45:62c0 Microdia Pavilion Webcam
Bus 001 Device 002: ID 090c:1000 Feiya Technology Corp. Memory Bar
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

also above is a lsusb -

In the network editor I said I was on AT&T in the mobile broadband settings - but I don't see anything that says connect or even shows that I have that setup.... so a little help is needed - I really hate windoze - I can put up with it if I have too - but here lately it seems that I have to a lot more then I should! - 

I also own an eeePC 701, and an eeePC 900 - both run UNR great (the 701 is running 8.04) and I am going to upgrade the 900 to UNR 9.04 today 
 
anyhelp on my two problems would be great - Thanks - LeRoy, KD8BXP

---

### Post by ddrichardson on 2009-04-27
> **lfmiller said:**
> Radio Shack is selling an Acer Aspire One with AT&T 3G built into it - nice netbook - And it just went on sale again!!! $50 bucks - SO I bought one - 
I have two problems - The first is this netbook comes with WinDoze XP on it - (Ok, truely this isn't the frist problem...just figured I would make people laugh) - I bought the display model - And it looks like the store told the thing to never ask to make the backup discs for the hidden partion - so my true first problem is how to I get to the hidden partion and do a backup before I install UNR to this - I only want to do this because it is a legal copy of windoze - So i would like to back that up before I make major changes -
If it still has the recovery facility then I's make a disk image with partimage which you can restore if needed later.

I don't know about the modem but Linpus Linux Lite must have a driver in the source, I haven't the link handy but I'll have a look.

---

### Post by lfmiller on 2009-04-27
> If it still has the recovery facility then I's make a disk image with partimage which you can restore if needed later.

I don't know about the modem but Linpus Linux Lite must have a driver in the source, I haven't the link handy but I'll have a look.


Thanks - Yes, the recovery partition is still intact - Ubuntu doesn't see it, nor does the partion editor - I don't know what would happend if I tried to install - I don't know if the installer would see the partion and destory it - It looks like what radio shack did is tell the windoze system not to create the backup disks - the erecovery program apparently went and wrote to that partion that the disks were not to be made and then never offered them to be made when I got the machine - I did do the factory recovery because it was a floor model, hoping that it would then give me the chance to make the disks - no luck - so what I want to do is do a live boot of ubuntu - access the partion (which I can't find), and make an img of that partion to a DVD or USB Flash drive -- 
someone told me if I called acer they would send me a disk I have not tried, but that maybe something I consider doing - 
I only want to do this because like I said it is legit and came with the netbook - Thanks for the ideas, let me know about the link to the acer linux I can try it out. 
LeRoy, KD8BXP

---

### Post by ddrichardson on 2009-04-28
Most OEM will charge for a recovery disk but its worth a try.

---

### Post by Qunt on 2009-04-30
Hi,

Has anyone found a solution to the modem issue?
I have the same problem using my Nokia phone as a 3G modem.
The network manager wizard took me through the setup and found my operator. I double checked the suggested settings and it all checks out. The only thing I'm missing at this point is to get the thing to actually connect. A connect button would be great :)

I saw there was an app. for Linpus Lite called 'Mobile Partner' but couldn't find it, or anything like it, with synaptic.

Oh, and I’m running Ubuntu 9.04 on the Acer Aspire One, btw.

Any and all suggestions are greatly appreciated.

---

### Post by ddrichardson on 2009-04-30
I had a look through the source pacakges but can't see the Mobile Manager source:
[ftp://csdftp.acer.com.tw/Aspire_One_Linpus_Linux/](ftp://csdftp.acer.com.tw/Aspire_One_Linpus_Linux/)

---

### Post by lfmiller on 2009-04-30
> **ddrichardson said:**
> I had a look through the source pacakges but can't see the Mobile Manager source:
[ftp://csdftp.acer.com.tw/Aspire_One_Linpus_Linux/](ftp://csdftp.acer.com.tw/Aspire_One_Linpus_Linux/)

The ftp site is asking for a user name and password - Anonymous users are not aloud - Thanks,
LeRoy, KD8BXP

---

### Post by ddrichardson on 2009-04-30
Prefix it with guest: [ftp://guest@csdftp.acer.com.tw/Aspire_One_Linpus_Linux/](ftp://guest@csdftp.acer.com.tw/Aspire_One_Linpus_Linux/)

---

### Post by bitbud on 2009-05-08
The 3g issue is a known issue.  It is on Launchpad at:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/303665](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/303665)

Don't know when it will get solved - I'll keep XP on my AAO until then :-(

---

### Post by lfmiller on 2009-05-10
> **bitbud said:**
> The 3g issue is a known issue.  It is on Launchpad at:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/303665](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/303665)

Don't know when it will get solved - I'll keep XP on my AAO until then :-(

Unfortuntally I too have decided to keep XP on the machine -> I will keep an eye on launchpad thou, maybe someone will come up with a solution -

As well, I couldn't get my blackberry to work as a tethered modem (using my eeepc 901 running 9.04) - SO I don't know if this is still a work in progress or if I am doing something completely wrong --> 9.04 does have a lot more choices on service providers so that is a good thing! But not working for me yet anyway.

Thanks, LeRoy, KD8BXP

---

### Post by Chiapo on 2009-05-18
It was with great glee that I opened this thread, the anticipation of a solution seemed close at hand.
Now I know better.
This Acer 3G Connection Manager is extremely difficult to locate! 
The idea is to run the Acer 3G Manager in Ubuntu NetBook Remix using WINE.
I'm uncertain as to the actual executable filename and which accompanying files are needed to allow execution.
Apparently the Qualcomm "GOBI" chipset requires managed loading of firmware - constantly...
It's almost enough to drive me to use Windoze exclusively... (almost)

---

### Post by lfmiller on 2009-05-27
> **Chiapo said:**
> It was with great glee that I opened this thread, the anticipation of a solution seemed close at hand.
Now I know better.
This Acer 3G Connection Manager is extremely difficult to locate! 
The idea is to run the Acer 3G Manager in Ubuntu NetBook Remix using WINE.
I'm uncertain as to the actual executable filename and which accompanying files are needed to allow execution.
Apparently the Qualcomm "GOBI" chipset requires managed loading of firmware - constantly...
It's almost enough to drive me to use Windoze exclusively... (almost)

Hmmmm... I will look into your idea of running it via WINE, I have had limited luck with running some other "Propritary" software via wine - 

The fact that it requires managed loading of firmware constantly explains a few things - even under XP  I have some problems while connecting - I assumed it was because the 3G signal was not strong, but a few times the connection manageager crashed and I had to reboot, so it must be hooky software to start with...

I don't like the idea of using Windoze exclusively anymore then you - but it does seem (AT least on the Aspire One) I am stuck with XP...
But I will look into and play around with WINE, not a bad idea.

LeRoy, KD8BXP

---

### Post by lfmiller on 2009-05-27
The connection manager is in the folder/directory

c:\program files\acer 3g connection manager\bin\

the name of the program that I guess handles the connection is:
surlprx.exe

HERE is a problem thou - it appears that it needs a command line to start, with out the commands it doesn't know what to do....

the command line for me:
ShastaURL:PC=ExternalRunApplication();APPLICATION=sandpiper_1,AUTHCODE= (mine omitted as I don't know what this does really)

It also appears that there is a QUALCom directly in the root of C: 
not sure looks like drivers to me.....

So is there a way to pass a command line while using WINE? 
I am still willing to give this a try.......
but it does looks a little complicated. :)

LeRoy, KD8BXP

---

### Post by Chiapo on 2009-12-04
Here's what I have found: [http://ubuntuforums.org/showthread.php?t=1157846&page=6](http://ubuntuforums.org/showthread.php?t=1157846&page=6)

I'm surfing in xubuntu 9.10 using the Qualcomm 9212 & I've almost reached my 5GB data cap already!

Many thanks to jamere & msignor for their advice! :KS

---

