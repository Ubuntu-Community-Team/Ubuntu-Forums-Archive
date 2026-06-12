---
title: "Old Sony Vaio will not boot from extern CD drive - BOOT ORDER IS A NO-GO"
date: 2006-01-05
forum: Hardware &amp; Laptops
---

### Post by dcon on 2006-01-05
I've switched my newer Toshiba Satellite laptop to Ubantu with few issues (other than scatterbrained glidepad control) however my old Windows 98 VAIO is another story. Change the boot order all I like, but the system will not boot from the CD drive.  This is one of the early thin VAIOs so there are no built in floppy or CD drive - they are external and connected via the PCMCIA slot.  

It appears that the drive only works when Windows is loaded.

Is there a utility out there that will let me boot from the CD?    Can anyone think of an alternative way to get Ubantu running on it?

---

### Post by Zelut on 2006-01-05
It sounds like you need a different method.  A far as I understand your options to boot are usually HDD, CDROM, Floppy or USB.  Do you have a USB drive that you could try booting from?

[https://wiki.ubuntu.com/Installation](https://wiki.ubuntu.com/Installation)

see if there are any tips here that you could try.

---

### Post by dcon on 2006-01-05
[QUOTE=kuyaedz]It sounds like you need a different method.  A far as I understand your options to boot are usually HDD, CDROM, Floppy or USB.  Do you have a USB drive that you could try booting from?

[https://wiki.ubuntu.com/Installation](https://wiki.ubuntu.com/Installation)

see if there are any tips here that you could try.[/QUOTE]

Still having no luck..I thought I found a solution here with a bootdisk that would get the CD flowing but all I get when I boot it from the floppy is an "X"

[http://ubuntuforums.org/showthread.php?p=631289#post631289](http://ubuntuforums.org/showthread.php?p=631289#post631289)

HELP!

---

### Post by Bytebull on 2006-01-05
get the boot disk .iso

burn with something... 

if your dealing with linux you know how to burn an iso and make it bootable by now...

if not... 

this isn't kindergarden.

---

### Post by Bytebull on 2006-01-05
find your systems (someone bitch slapped me so I be nice)

find your systems setup key....

during boot.... go into the boot sequence and make it boot from your FLOOPY/CD/HD

... make sure it doesn't boot from the HD before the CD....


(duh he knew that so dont slap me again)

---

### Post by dcon on 2006-01-05
Dear Bytebull,

No, this isn't kindergarden -agreed.  Hope you feel better.

Hence why I burned the ISO image to a CD.  THAT, is not the problem.  The problem is that the ever loving folks who made my octagenerian Sony Vaio deceided to go with an external PCMCIA drive which isn't bottable in the normal away. 

If you can help, much appreciated.  If not........I'm married....sarcasm is already available to me on a regular basis.

---

### Post by dcon on 2006-01-05
[QUOTE=Bytebull]find your systems (someone bitch slapped me so I be nice)

find your systems setup key....

during boot.... go into the boot sequence and make it boot from your FLOOPY/CD/HD

... make sure it doesn't boot from the HD before the CD....


(duh he knew that so dont slap me again)[/QUOTE]


...yes...the Key is F2 and yes, I set up the order as noted to hit the CD first.  Unfortunately, it almost looks like the PCMIA slot doesn't even fire up until Windows 98 gets rolling.

---

### Post by Bytebull on 2006-01-05
ok a question...

your trying to install ubuntu onto the same drive with your windows and multilple OS?...

GIMME MORE DETAILS..

ill help ya bro... 
./ sarcasm on
via
vio? what? why you bought that? 

./ sarcasm off

---

### Post by Bytebull on 2006-01-05
windows 98????? did I see that in there????????????????

****

---

### Post by dcon on 2006-01-05
[QUOTE=Bytebull]windows 98????? did I see that in there????????????????

****[/QUOTE]

Yup...top of the thread in painfully black letters.  Makes me cry.

---

### Post by Bytebull on 2006-01-05
I'm gonna help you man... keep replying.... sorry If i went of...

but your using windows 98???

is that real? lol...

reply to me what your trying to do...

you need at least a 60GB harddrive and a good partition manager to have dual boot options.. and install ubuntu

please reply...

I dont want to scare you off... I'm here to help you...

---

### Post by dcon on 2006-01-05
[QUOTE=Bytebull]ok a question...

your trying to install ubuntu onto the same drive with your windows and multilple OS?...

GIMME MORE DETAILS..

ill help ya bro... 
./ sarcasm on
via
vio? what? why you bought that? 

./ sarcasm off[/QUOTE]

Ok...plan/hope is to replace the Windows 98 on "old yeller" with UBANTU.  i am however a total loss at this point to make the magic happen.  I thought I had it with the floppy bud sadly...it didn't fly: [http://ubuntuforums.org/showthread.p...289#post631289](http://ubuntuforums.org/showthread.p...289#post631289)

---

### Post by Bytebull on 2006-01-05
any new linux user is a thorn in the side of the establishment that wants to charge us for even "humming" a tune.... so  lets go I got all night man... I"ll help you get set up... ok?


keep replying.. or we can go to msn messenger and chat , it's much easier

[email]michael_ec@hotmail.com[/email]

you got XMMS on your linux yet? or aMSN...

---

### Post by Bytebull on 2006-01-05
If it takes all night I'mma get your linux working...

so the problem is that your BIOS wont boot the cd before your HARDDRIVE right?

lets get this down to the basics... what exactly is your problem?

---

### Post by Bytebull on 2006-01-05
even in msn chat she is hard to teach.... but she listens....

maybe a love connection?

lmao...

this thread is null now , I'm helping her in chat...

nite guys.. I'll post how we got her up and running when we figure out her problem..


nite.

---

### Post by Bytebull on 2006-01-05
woops..... jealous husb and...


dont msn wiht her... 

he
gonna 
kill me...


forget this post..

---

### Post by dfreedman on 2006-01-05
Some of the older Vaios won't boot from the external CD drive when the CD drive's power supply is plugged in, oddly enough.  Have you tried letting it run off of the computer's power when you boot?  (And if you have, I suppose you could try it with the power in.)

---

### Post by dcon on 2006-01-06
[QUOTE=dfreedman]Some of the older Vaios won't boot from the external CD drive when the CD drive's power supply is plugged in, oddly enough.  Have you tried letting it run off of the computer's power when you boot?  (And if you have, I suppose you could try it with the power in.)[/QUOTE]

True...and this is one that won't power on in boot with the power plug in.

---

### Post by dcon on 2006-01-06
Sorry...ended up posting the same problem to two different threads.

[http://ubuntuforums.org/showthread.php?t=81280](http://ubuntuforums.org/showthread.php?t=81280)

I'll continue from here:

I wiped out the old windows 98 installation altogether. When rebooted, the CD responds (ie...there is some spinning) however all I get is the standard
"Invalid System Disk". I'm using a Live CD for 386 machines (PC (Intel x86) live CD) which runs great on my Toshiba. Here are the specs for the VAIO

Sony VAIO PCG-505TR
* Mobile Pentium MMX 233 Mhz
* 10.4 inch TFT XGA LCD screen (1024 x 76
* 6 GB Harddrive
* 128 MB RAM

Am I using the right version of Ubantu or is the Install version the answer?

---

### Post by dcon on 2006-01-06
[QUOTE=dcon]Sorry...ended up posting the same problem to two different threads.

[http://ubuntuforums.org/showthread.php?t=81280](http://ubuntuforums.org/showthread.php?t=81280)

I'll continue from here:

I wiped out the old windows 98 installation altogether. When rebooted, the CD responds (ie...there is some spinning) however all I get is the standard
"Invalid System Disk". I'm using a Live CD for 386 machines (PC (Intel x86) live CD) which runs great on my Toshiba. Here are the specs for the VAIO

Sony VAIO PCG-505TR
* Mobile Pentium MMX 233 Mhz
* 10.4 inch TFT XGA LCD screen (1024 x 76
* 6 GB Harddrive
* 128 MB RAM

Am I using the right version of Ubantu or is the Install version the answer?[/QUOTE]



- Correction- 64MB ram

---

### Post by dcon on 2006-01-06
OK...this is breaking into a downright pleading for help.

I have the above noted laptop with no OS whatsoever.  I've downloaded and burned both the Live and install versions of the Ubantu CD but no dice.  

The system boot order is set to CD/Flppy/Hard drive.  As is, the CD spins during the boot up sequence but that's it.  It spins...makes some noise...spins makes some noise...spins...and then just stops.  The system gives me the old INVALID SYSTEM DISK error and that's where we stand.

Can any one help?

...and BTW, I'm a little lost on bytebull's comment regarding the jelous husband bit.

---

### Post by dcon on 2006-01-06
Also...I've created a boot manager disk as instructed here:
[http://linux.simple.be/tools/sbm](http://linux.simple.be/tools/sbm)

It works - in the sense that the boot manager program runs and a menu appears.  I however can't find instructions on how to use it to get the CD to boot!

---

### Post by Nightwind on 2006-01-06
[QUOTE=dcon]Also...I've created a boot manager disk as instructed here:
[http://linux.simple.be/tools/sbm](http://linux.simple.be/tools/sbm)

It works - in the sense that the boot manager program runs and a menu appears.  I however can't find instructions on how to use it to get the CD to boot![/QUOTE]
Okay this is the problem I as I understand it,
you cannot boot from the cd rom but you can from the floppy drive is this correct?
You have the Ubuntu 5.10 disk to install from is that correct? You can PM me if you want to.

---

### Post by dcon on 2006-01-06
Thank you!

Yes...you understand it correctly.  Orginally, this granny laptop was running Win 98 and we could not even get the CD to power until Windows 98 kicked in - regardless of the boot order in the BIOS. This is apparently an issue on these laptops.  Note that the CD is an external unit connected via the PCMCIA slot.  

I formatted the C drive since.

I can boot to the floppy drive and bring up the Smart Boot software without issue.  Strangely, it seems to have instructions.  As of yet, I can't figure out how to get it to boot off the CD. 

Note that the CD does power on now in the boot but as noted, it never takes off.

---

### Post by dcon on 2006-01-06
Thanks again for taking the time on this.  The problem with the Smart boot instructions is this:
the problem with Smart boot is in Step #8

"When the Smart Boot Manager's menu appears, choose the menu option with "CDROM" in it, and press Enter. (don't think you need to install SBM to the HD - you can, but you don't need to.)"

*** The optionsI see when i run it are:

type:       name:
None       Quit to BIOS
NONE      Power off
NONE      Reboot
None      Floppy
None      hard disk
Fat32     Primary1

No CD!

---

### Post by dcon on 2006-01-07
OK...still no joy in mudville.


Smart Boot Manager does show the CD as an option tom pick from...just:


type: name:
None Quit to BIOS
NONE Power off
NONE Reboot
None Floppy
None hard disk
Fat32 Primary1

---

### Post by 13thfloor on 2006-01-09
I recently acquired my father's old Sony Vaio (PCG-FX170K) notebook.  It had a problem bootiing into Windows, apparently memory related from what I have been able to figure out.  It had no problem booting into Linux so I installed Red Hat 9 because no Fedora release would load, it always locked up.  When trying Ubuntu, same problem.  I found this thread and gave the Smart Bootloader a try but it didn't work, but I had changed the boot sequence to floppy, cd, hard drive and the install disc was in the drive so I gave it one more try and it worked.  So by changing the boot order to floppy, cd, hard drive something made it work and I have no explanation for it.  I have no idea if this would work for your situation, but since it worked for me I thought I should pass it along.  And it worked when rebooting too.  Now I have to get a few other things working and then I can keep my portable system current.  Good luck with getting yours running.

---

### Post by adriantry on 2006-01-10
Hi Dcon

I think I have the same laptop as you - and the same frustrating situation!

Last week someone asked me to install Linux on a low end HP desktop computer - 630 MHz, 64 MB RAM, 10 GB hard drive. Ubuntu crawled. Even Xubuntu wasn't too snappy.

Then I discovered Vector Linux ([www.vectorlinux.com)](www.vectorlinux.com)).

Vector Linux is designed to run at a decent speed on low end computers. It uses IceWM, XFCE and Fluxbox as its window managers. It works great on my friend's computer.

But here is the thing that is very interesting for you and me:

They give you the option of not having to install it from a CD. They have a program that will let you install the program directly from the hard drive, either from Windows or Linux. Details for installing it from Windows are here:

[ftp://ibiblio.org/pub/linux/distributions/vectorlinux/docs/vl50/manuals/vl5_installation_guide_en.html#iso_win](ftp://ibiblio.org/pub/linux/distributions/vectorlinux/docs/vl50/manuals/vl5_installation_guide_en.html#iso_win)

I haven't tried it yet, but it sounds very promising. Just what I've been looking for!

So this leaves us with one big question - are you able to reinstall Windows? Maybe from floppies? If you can do that, then Vector Linux might be an option for you.

Adrian

---

### Post by mips on 2006-01-10
dcon,

This sounds like a bad disk.

Do you have the originals from Ubuntu or did you burn and iso to disk ? Does this cd boot in other computers ? Can you boot something like a windows install cd ?

If you burned your own ISO to CD I would suggest you do it again and at nothing faster than x8 speed on a good quality disk. do a md5 checksum on the iso file and verify cd.

Try this new CD again and see what happens.

Should you get to the initial installer boot prompt enter this line: **linux ide2=0x180,0x386**
You might need this line during & after the install process.

If you have any display problems keep the following values in mind for your xorg.conf file:
HorizSync 31.5-48.5
VertRefresh 60

I had a look and everything indicates that this PCGA-CD5 CD-ROM is bootable without any exceptions and no drivers are required. Just google 'How to boot from VAIO PCG-505TR external cd-rom ?' and you will see that there are no issues.

[http://www.joechiu.com/computing/vaio/linuxon505.html](http://www.joechiu.com/computing/vaio/linuxon505.html)
[http://www-personal.umich.edu/~bfields/505TR_linux.html](http://www-personal.umich.edu/~bfields/505TR_linux.html)

---

### Post by mips on 2006-01-10
Also check the bottom of your CD drive and see it there is a switch that says "Cardbus-Recovery", Move it to the **Recovery** position and see if that makes it bootable.

Also try resetting your BIOS to default settings and save. try again, change boot order, try again.

---

### Post by xxzuppoxx on 2007-02-08
hi,
I have been looking for the setup key for this old sony vaio and i cant find it anywhere  which sucks cuz i cant even boot an operating system on it ><
I've tryed almost all the F-keys, esc, and del but nothing works.
Can someone please help me find it?

---

