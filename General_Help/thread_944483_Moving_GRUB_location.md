---
title: "Moving GRUB location?"
date: 2008-10-11
forum: General Help
---

### Post by Jaded Misanthrope on 2008-10-11
When I install a distro that comes with a bootloader, I generally install the bootloader on the partition that contains the actual OS (the / mount point; generally sda3 for me) so that I can easily change distros and keep my Vista partition untouched.

However, I forgot to specify that I wanted GRUB to install to sda3 during the installation of Ubuntu and it installed to whatever its default location is; is it possible to move GRUB to sda3 from its default location, and if so, how?

---

### Post by caljohnsmith on 2008-10-11
If you have only one HDD, Grub would by default be installed to the MBR (Master Boot Record) of that drive. Also, when Grub is installed to the MBR, Grub's stage1.5 file gets embedded in the sectors immediately following the MBR, but this doesn't happen when you install Grub in a partition boot sector; therefore there is no easy way to "move" Grub from the MBR to your partition boot sector, but it is really easy to simply "install" Grub to the partition boot sector of sda3 with:
```
sudo grub
grub> root (hd0,2)
grub> setup (hd0,2)
grub> quit
```
So if you don't want Grub in the MBR, you can replace it with the Windows Vista boot loader by booting your Win Vista Install/Recovery CD and running:
```
bootrec /fixmbr
```
If you don't have a Vista Recovery CD, you can download one from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). Let me know how it goes.

---

### Post by Jaded Misanthrope on 2008-10-11
> **caljohnsmith said:**
> If you have only one HDD, Grub would by default be installed to the MBR (Master Boot Record) of that drive. Also, when Grub is installed to the MBR, Grub's stage1.5 file gets embedded in the sectors immediately following the MBR, but this doesn't happen when you install Grub in a partition boot sector; therefore there is no easy way to "move" Grub from the MBR to your partition boot sector, but it is really easy to simply "install" Grub to the partition boot sector of sda3 with:
```
sudo grub
grub> root (hd0,2)
grub> setup (hd0,2)
grub> quit
```
So if you don't want Grub in the MBR, you can replace it with the Windows Vista boot loader by booting your Win Vista Install/Recovery CD and running:
```
bootrec /fixmbr
```
If you don't have a Vista Recovery CD, you can download one from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). Let me know how it goes.

I'm going to download the x86 version linked to in the article you gave me instead, since my computer is x86--I presume I do the same thing?

I've run the GRUB commands you gave me, and they seem to have worked perfectly, so if I download the x86 recover and run bootrec /fixmbr I will be able to select which O.S. to use using the GRUB menu, but it will be on sda3 instead? If so, brilliant; thanks. :)

---

### Post by caljohnsmith on 2008-10-11
> **Jaded Misanthrope said:**
> I'm going to download the x86 version linked to in the article you gave me instead, since my computer is x86--I presume I do the same thing?

I've run the GRUB commands you gave me, and they seem to have worked perfectly, so if I download the x86 recover and run bootrec /fixmbr I will be able to select which O.S. to use using the GRUB menu, but it will be on sda3 instead? If so, brilliant; thanks. :)
I assumed since you wanted to put Grub in the partition boot sector and not the MBR, you wanted to use Vista's boot loader on start up to manage all your OSes and not Grub. If you want to use Grub on start up to boot your OSes, you should leave Grub in the MBR. Can you clarify exactly what your ultimate goal is? Then I can give you more accurate advice. :)

---

### Post by Jaded Misanthrope on 2008-10-11
> **caljohnsmith said:**
> I assumed since you wanted to put Grub in the partition boot sector and not the MBR, you wanted to use Vista's boot loader on start up to manage all your OSes and not Grub. If you want to use Grub on start up to boot your OSes, you should leave Grub in the MBR. Can you clarify exactly what your ultimate goal is? Then I can give you more accurate advice. :)

Previously, I have installed GRUB to sda3 and it has allowed me to select which O.S. to use at boot, but I forgot to install it to sda3 this time around.

Of course, if Vista's default bootloader allows me to select between Ubuntu 8.10 and Vista at boot too, that's fine.

---

### Post by meierfra. on 2008-10-11
> I have installed GRUB to sda3 and it has allowed me to select which O.S. to use at boot, 

caljohnsmith instruction will achieve this, you just need to add a couple of steps. Altogether  to this:

```
sudo grub
grub> root (hd0,2)
grub> setup (hd0,2)
grub> makeactive        
grub> quit
```

```
gksudo gedit /boot/grub/menu.lst
```
and remove the line "makeactive" from your Vista item.

Then  boot from the Vista CD:
```
bootrec /fixmbr
```

---

### Post by caljohnsmith on 2008-10-11
> **Jaded Misanthrope said:**
> Previously, I have installed GRUB to sda3 and it has allowed me to select which O.S. to use at boot, but I forgot to install it to sda3 this time around.

Of course, if Vista's default bootloader allows me to select between Ubuntu 8.10 and Vista at boot too, that's fine.
That's curious, because installing Grub to sda3 will not make Grub boot on start up unless you still had a Windows boot loader in the MBR and your Ubuntu partition was marked as active (bootable) instead of the Vista partition. So you're saying that on start up, you got the Grub menu where you could choose your OS? 

If you don't care which boot loader you use, personally I would go with Grub. So if you want to stick with Grub to boot all your OSes, then you can make sure it is correctly installed to the MBR with:
```
sudo grub
grub> root (hd0,2)
grub> setup (hd0)
grub> quit
```
Which assumes your Ubuntu is on sda3. That should at least get you the Grub menu on start up, and if you have problems booting either Ubuntu or Vista from the menu, let me know and we can fix that too. You'll need to post the output of:
```
sudo fdisk -lu
```
So I can see what your setup is. Otherwise let me know how it goes.

EDIT: Once again meierfra beats me to the punch. :) I'm curious though, why bother using Vista's boot loader to chain load Grub, meierfra? Why not just stick Grub back in the MBR? Either could work of course.

---

### Post by meierfra. on 2008-10-11
> why bother using Vista's boot loader to chain load Grub, meierfra?
(I wouldn't describe it this way.  The MBR is  not really part of the Vista boot loader. It just calls the boot sector of the active partition. In particular, the vista partition is not involved in the booting process. So if the Vista partition gets corrupted it will not interfere with Grub) 

Why not?  Either way works just fine. The only differences I see:

Advantage of MBR calling Grub on the bootsector of sda3:
   If Ubuntu gets corrupted or  deleted, one just has to set the boot flag  to the Vista partition and can boot into Vista. 

Disadvantage:  Stage1.5 files are not installed. So if something goes wrong with grub, one does not receive any error message.

---

### Post by caljohnsmith on 2008-10-11
> **meierfra. said:**
> (I wouldn't describe it this way.  The MBR is  not really part of the Vista boot loader. It just calls the boot sector of the active partition. In particular, the vista partition is not involved in the booting process. So if the Vista partition gets corrupted it will not interfere with Grub) 

You're right, I should have used more precise terminology and said the Windows MBR, not Vista boot loader, but I'm glad you understood what I meant anyway. :)

---

### Post by TeXtonyx on 2008-10-11
I once had two drives on one ide cable. XP and UbuntuA on the primary drive and
Vista and UbuntuB on the slave drive. My mainboard was damaged by an electrical
surge and is not totally reliable. I could not boot Vista when I switched from drive 0
to drive 1 in Bios. However, I could boot Vista by leaving the boot order of the drives
as 0 and then 1, when I chose to boot UbuntaA from the XP boot.ini choices. I had
added an entry in UbuntuA's menu.lst to boot Vista; I think it was root (hd1,0). Now
that was rather a remote lucky break. Suppose XP had a problem and wouldn't boot.
Those Super Grub Disk's which are very handy, would have allowed me to boot
UbuntuA and then boot Vista. If grub is in the MBR and the Ubuntu partition fails,
then Windows won't start without repairing the mbr. Windows doesn't have the easy
equivalent of a Super Grub boot disk. So Linux/grub is more versatile when it is
installed in the Linux boot partition while Windows is more inflexible because it 
functions best, only in the mbr, not in either position like grub. I am not sure of the
Vista bootloader yet. But, boot.ini and grub as bootloaders are like a million % 
reliable, so that isn't an the issue. Grub has additional functionality when looking
at the entire potential of a dual boot system, only when installed in the Linux
boot partition. It makes troubleshooting easier; it is a lot easier for one OS to stay
online until the other is repaired. Having an ultimately efficient computer which
uses both OS, Windows and Linux, is obtained by maximizing options for future
expansions or dealing with present problems. It is a fact, not an opinion, that the
overall computer efficiency is enhanced when grub is in the boot partition rather
than the MBR. Not because grub is a less capable bootloader per se, but 
because it contributes an additional capability/efficiency to the potential of the 
system when located in the boot partition and not in the MBR. There is not one,
and I mean not *not one* good reason to put grub in the MBR of a dual-booting
system. People do it because they have learned a bad habit. Grub located in the
MBR is never going to help optimize the system for future OS changes/expansions
and it someone thinks it can, just name *one* example where it works better for a
dual booting system in the MBR, where it helps the end user in terms of time and
effort. What I'm saying is not to be confused with the default choice of MBR. It
may be that in Step 7 of the live cd install under "Advanced" that choosing the
correct partition to install grub into the boot partition is too difficult too grasp for
the average user installing Ubuntu. That is a reason for why it is the default, and
works for non dual-booters, but Ubuntu is 60% a dual-booting system. Thus a 
reason why the MBR is a default is a reason based on user limitation. And not on
what would produce the most efficient and functionally organized future system.
So in this case the OP is capable of transcending difficulty of concept. Even if 
only one in thirty users proceeds to the point where he/she realizes the potential
of the advantage of a grub boot partition install, that is enough of a reason to
start if possible with the best plan for the future of the future, when there is no
downside to having Linux in the boot partition. That capability is a great strength
of Ubuntu which Windows doesn't enjoy, its adaptability, so why despise its use?!
This post is intended for those who hold the lethargic opinion that the ability to 
have more choices somehow doesn't matter, because it doesn't matter to them.

---

### Post by Sam on 2008-10-11
> **TeXtonyx said:**
> <snip>

:shock: Ouch that's painful to read... Please use line breaks next time !

---

### Post by TeXtonyx on 2008-10-11
I did use line breaks according to my browser, Firefox. I don't like those really wide
default lines. I guess you mean making new paragraphs with a space separating them.

---

### Post by TeXtonyx on 2008-10-12
meierfra wrote: Disadvantage [TeX: of grub installed on bootsector]: 
Stage1.5 files are not installed. So if something goes 
wrong with grub, one does not receive any error message.

--------------------

[http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_13.html#SEC104](http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_13.html#SEC104)

Errors reported by the Stage 1.5

The general way that the Stage 1.5 handles errors is to print an error number 
in the form Error num and then halt. Pressing CTRL-ALT-DEL will reboot.

The error numbers correspond to the errors reported by Stage 2.

-------------------------------

I certainly don't have your expertise in this area, meierfra, so I have a question.
Since 1.5 stage files are not installed in the bootsector of the boot partition, they
cannot provide any error messages as you say. But I understood the above quote
from the Grub manual to mean that the errors/numbers would be reported by the
stage 2 of grub, so there would be no loss of information? The conclusion wasn't
reached by proven experience, as I haven't had enough grub errors to make a 
comparison, and so is based on my reading ken (or lack thereof).

---

### Post by meierfra. on 2008-10-12
> But I understood the above quote from the Grub manual to mean that the errors/numbers would be reported by the stage 2 of grub, so there would be no loss of information?

Yes, but only if grub is able to reach  stage 2. If you look at the grub cases in this forum, you will see  that  error messages are  often reported by  stage1.5 and that means the grub never got to stage2.

---

### Post by TeXtonyx on 2008-10-12
meierfra wrote:
"Yes, but only if grub is able to reach stage 2. If you look at the grub cases in this forum, 
you will see that error messages are often reported by stage1.5 and that means 
the grub never got to stage2."

TeX: "GRUB uses this region [62 sectors after MBR] to store its stage 1.5, which 
is filesystem specific code used to find the operating system image on the "boot" 
filesystem." My idea about this was that there was no stage 1.5 because none was
needed. Bootpart or dd identifies  the partition and sector and when these 512 
bytes were saved into a file, it replaced the work done by stage 1, finding the OS
image on the "boot" filesystem. So my boot.ini entry is
c:\ubuntu.bin="Ubuntu"
This fails and I get a Bootpart grub screen for input, or I shortly see the menu.lst
with several choices, which is past the stage 1.5 errors. It seems to me that 1.5
errors are only possible when grub is installed to the MBR so that it fails at stage 1
or stage 2, if it fails. I thought I was at stage 2 when I saw the grub menu.lst.

I've had grub fail using c:\ubuntu.bin="Ubuntu", but not because this mechanical
copy lacked fidelity. I've wanted more space for my swap file and resized the
partitions slightly with a poor result. I have to run Bootpart again and make a new
copy of the boot sector. I think that is a stage 1 error, Bootpart exiting to a grub 
screen. The two relevant, I think, of the 5 listed stage 1 errors are

The following is a comprehensive list of error messages for the Stage 1:

Hard Disk Error
The stage2 or stage1.5 is being read from a hard disk, and the 
attempt to determine the size and geometry of the hard disk failed. 

Geom Error
The location of the stage2 or stage1.5 is not in the portion of the 
disk supported directly by the BIOS read calls. This could occur 
because the BIOS translated geometry has been changed by the user or 
the disk is moved to another machine or controller after installation, 
or GRUB was not installed using itself (if it was, the Stage 2 version 
of this error would have been seen during that process and it would 
not have completed the install). 

TeX: Do you think when I resized the partition and the current ubuntu.bin failed,
that this would actually be discovered and reported by stage 1.5 errors and not 2?

---

### Post by meierfra. on 2008-10-12
> My idea about this was that there was no stage 1.5 because none was
needed. 


No, there just isn't enough free space in the boot sector of a partition to store stage1.5

> I've had grub fail using c:\ubuntu.bin="Ubuntu", but not because this mechanical copy lacked fidelity. I've wanted more space for my swap file and resized the partitions slightly with a poor result.

If Grub is  installed with stage1.5  resizing the partitions does not cause any  problems. 

But if Grub is installed without stage1.5  resizing the partition causes grub  to fail while looking for stage2.

Explanation:

Grub's stage1.5 has the ability to search for files. So to reach stage2, grub just searches for the file "/boot/grub/stage2".

Without stage1.5 grub cannot search for files. Instead the exact physical location of /boot/grub/stage2" is stored in Stage1 (namely the numbers of sectors from the beginning of the hard drive to the file "boot/grub/stage2")  If you resize a partition, files get moved around. Stage2 will be in a different physical location and stage1 cannot find stage2.

> Do you think when I resized the partition and the current ubuntu.bin failed, that this would actually be discovered and reported by stage 1.5 errors and not 2?

This error will be reported by stage1, since stage2 will not be found.
(and with stage1.5 you wouldn't  even have a problem)

---

### Post by TeXtonyx on 2008-10-13
Hello, I've been thinking about this a couple of days. I realize that being smart and
having a CS degree is no substitute for experience. I'm also persistent, and like to
understand the logic of how things work. 

---------------------------

Quote:
Do you think when I resized the partition and the current ubuntu.bin failed, that 
this would actually be discovered and reported by stage 1.5 errors and not 2?

meierfra wrote: This error will be reported by stage1, since stage2 will not be found.
(and with stage1.5 you wouldn't even have a problem)

-----------------------------

TeX: Your statement above was the conclusion that I was driving at when I wrote,
"I think that is a stage 1 error, Bootpart exiting to a grub screen. The two relevant, 
I think, of the 5 listed stage 1 errors are .. Hard Disk error and Geom error."

A recent experience. I booted to Ubuntu and instead got the Bootpart info screen.
I went back to XP and ran Bootpart, which works like fdisk, reporting all partitions
and their formatting. So I only had one ext3 partition on the first drive, thus I typed
bootpart 4 ubuntu.bin taking less than 12 seconds, it briefly flashes a sector count
"(namely the numbers of sectors from the beginning of the hard drive to the file 
"boot/grub/stage2")".

---------------------------------

Quote: But I understood the above quote from the Grub manual to mean that the
 errors/numbers would be reported by the stage 2 of grub, so there would be no loss of information?

meierfra replied:
Yes, but only if grub is able to reach stage 2. If you look at the grub cases in this forum, 
you will see that error messages are often reported by stage1.5 and that means the grub never got to stage2. 

-------------------------------

My focus is on your observation that there's a 'disadvantage to not getting stage 
1.5 error reports'. My experience is that Bootpart infallibly gets you to stage2
which is where the grub menu.lst screen appears, unless there is a stage1 error.
That means that Bootpart fulfills the function of grub 1.5 except in the case of the
stage1 error where the disk is resized and grub automatically finds the new location
of the stage2 files. Bootpart does this manually within seconds. 

So my question is what grub stage 1.5 error messages are needed for diagnosis
that aren't provided when Bootpart transports one to the menu.lst screen. The
stage2 error reports (identical in content to stage1.5) are generated when one 
makes a choice and hits 'Enter'. 
Another way of phrasing my question: There are no stage1.5 errors nor process,
when Bootpart gets you to the grub.lst menu where after selection, stage2 error
reporting begins. What stage1.5 error is only reported during stage1.5 that is not
available or meaningful if reported by stage2 error reporting? What is significant
about diagnosing a stage1.5 report *then* rather than later? Since Bootpart works
rather infallibly without stage1.5 and stage1.5 errors for diagnosis, in getting the
user to the initial screen where stage2 error reports begin after selection, my
conclusion is that there is no general loss of information which matters from 
getting error reports later at stage2. 

I premise my remarks with installing grub to the boot partition and then using
Bootpart, as relevant to a dual boot system with Windows and Linux. What shows
up in stage1.5 errors that need to be detected just then and matter to the system
getting to stage2. When stage1.5 is eliminated and Bootpart is substituted there
doesn't seem to be any such key stage1.5 errors. What errors are there that can't
be discovered and dealt with after Bootpart gets you to the grub menu.lst screen?
Because Bootpart works there does not appear to be any such preventive issues
relevant to stage1.5, so where does the loss of information occur? What can't be
fixed a little later? Why is knowing error messages sooner important in this case?

I appreciated your explanations, but you didn't address the point of my question,
so I'm repeating my actual question(s) a bit redundantly :-) I've tried to reason about
 this soundly, but computers always seem to generate possibilities beyond prediction! 

Edit: It isn't grub which is getting to stage2, it is Bootpart writing the .bin + boot.ini in C:\ 
I think Vista doesn't invoke grub sooner than the grub menu.lst also.
For stage1 errors Bootpart has the fairly equivalent "Cannot load from harddisk" 
and for a stage1 Geom error, less informatively exits to the Bootpart shell info.

---

### Post by meierfra. on 2008-10-13
> Edit: It isn't grub which is getting to stage2, it is Bootpart writing the .bin + boot.ini in C:\ I think Vista doesn't invoke grub sooner than the grub menu.lst also.

You seem to  misunderstand the role of "bootpart". It only does two things:

1) It copies  the bootsector of the Ubuntu partition  to the file "ubuntu.bin".

2)  It adds a line to "boot.ini:

The boot sector of the Ubuntu partition contains the code for Grub's stage1. So  "ubuntu.bin"  now contains Grub's "stage1".  Once you select "Ubuntu" at the Windows Boot Menu, Grub's stage 1 is loaded.
Stage1 loads Stage 2 and then stage2 displays menu.lst.

So it is Grub's stage1 which tries to reach stage 2, not bootpart,

>  My experience is that Bootpart infallibly gets you to stage2

Your own experience with resizing partitions shows  that it is not "infallible"

> So my question is what grub stage 1.5 error messages are needed for diagnosis that aren't provided when Bootpart transports one to the menu.lst screen.

None. Once you reach "menu.lst" you already have reached stage2. And stage2 provides an even better error analysis than "stage1.5"
The error messages from stage1.5 are only used when stage2 is not reached.

So let me state  the advantages of the Stage 1.5  more clearly:


1)  With Stage1.5 it is more likely to reach the stage2. 

2)  If stage2 is not reached, stage1.5 will give better error messages than stage1. So it will be easier to diagnose why stage2 was not reached.

But  once  you reached stage2, it does not matter anymore whether you reached stage 2 via stage 1 or via stage1.5.

---

### Post by TeXtonyx on 2008-10-14
Quote:
My experience is that Bootpart infallibly gets you to stage2

meierfra replied:
Your own experience with resizing partitions shows that it is not "infallible"

Tex: I didn't say it was "infallible", you snipped the rest of the
sentence, "unless there is a stage1 error." I thought resizing the
partition would be a stage1 error which I communicated with
"except in the case of the stage1 error where the disk is resized 
and grub automatically finds the new location of the stage2 files.
Bootpart does this manually within seconds."

meierfra writes:
So let me state the advantages of the Stage 1.5 more clearly:
1) With Stage1.5 it is more likely to reach the stage2.

TeX: I agree that the resizing problem is solved automatically
by the stage1.5 process is a slight advantage to manually 
running Bootpart again. Not the time but figuring that Bootpart
should be rerun. But if stage1.5 discovers/searches automatically
then it doesn't count as an advantage of stage1.5 error reports.

So Bootpart exits before menu.lst if the partition was resized.
There is no stage1.5, and I conclude it is therefore a basic
stage1 kind of error, not stage1.5, which is after stage1.

Perhaps Bootpart has error reports which correspond to helpful
stage1.5 errors. I've not seen one. Just one error where Bootpart
exits. Then when fixed Bootpart gets one to the menu.lst screen.
Obviously, no stage1.5 error reports are needed for Bootpart to
transport the system to the menu.lst where stage2 errors become
available after I make a selection (I've had this experience).

I've never seen an instance where stage1.5 error messages were
needed, so I never seen an advantage to those reports ^^. You've
mentioned the searching of stage1.5 but that isn't a benefit of an 
error message. When I acknowlege your greater experience, I'm
looking for a real example of how a stage1.5 error report would
have helped Bootpart to bring the system to the menu.lst. I've
only seen the resizing problem error untrack Bootpart and that
doesn't benefit or need any stage1.5 error reports. That is why
I'm looking for a real example from your experience, rather than
some type of counterfactual speculation; I don't trust their causality :-)

---

### Post by meierfra. on 2008-10-14
TeXtonyx: Bootpart does not take part in the booting process. So your  previous post makes no sense to me.

---

### Post by TeXtonyx on 2008-10-14
Quote:
So my question is what grub stage 1.5 error messages are needed for 
diagnosis that aren't provided when Bootpart transports one to the menu.lst screen.

----------------------

meierfra answered:

None. Once you reach "menu.lst" you already have reached stage2. And stage2 
provides an even better error analysis than "stage1.5"
The error messages from stage1.5 are only used when stage2 is not reached.

So let me state the advantages of the Stage 1.5 more clearly:


1) With Stage1.5 it is more likely to reach the stage2. 

2) If stage2 is not reached, stage1.5 will give better error messages than stage1. 
So it will be easier to diagnose why stage2 was not reached.

But once you reached stage2, it does not matter anymore whether 
you reached stage 2 via stage 1 or via stage1.5.

-----------------------------------------------

TeX analyzed: 

1) That seems true, but it is not because of being helped by error messages,
but by its search mechanism. The contested statement is 'the disadvantage of
of boot partition installation of grub versus MBR installation of grub is that only
the MBR install of grub provides helpful to diagnosis stage1.5 error reports.'

2) But if (MBR) stage1 fails there are no stage1.5 error messages. When Bootpart
fails, it fails at stage1, so although there is no existing stage1.5, there is not a loss
to diagnostic information compared to grub in the MBR failing in stage1 since no
stage1.5 error messages provide diagnostic information in either case.
Bootpart appears to always get to stage2 if if passes stage1, so there is no help
needed from stage1.5 diagnostic messages and Bootpart has no stage1.5 step.
Thus, the key is, as you observe, stage2 (which has more comprehensive errors?).

meierfra wrote: "So it will be easier to diagnose why stage2 was not reached."

Bootpart hasn't always just exited when failing. Sometimes I get to a grub> screen
where I can input to grub. I figure this is part of stage2. Now the problem has been
that the menu.lst had an error, (hd0,5) when it should have read (hd0,4). 

Would I have gotten a #8 : "No such partition" or a #11 : "File not found" error 
generated by stage1.5, or would this have been discovered only at stage2? I'm
looking for a tangible case where stage1.5 error reports help diagnosis when the
the MBR method is used, while Bootpart with the boot partition method, suffers.
An example from your own experience where a stage1.5 error report would have
helped Bootpart execute to stage2 successfully is the type of substantial evidence
I'm looking for to establish your claim that stage1.5 error reports would be advantageous
when also using the Bootpart (or Vista Bootloader) sector method. Something that 
makes me realize your claim actually realizes this, rather than it is only possible that 
it could really do this. The benefit of stage1.5 search for stage2 is not disputed.

---

### Post by meierfra. on 2008-10-14
> when Bootpart transports one to the menu.lst screen


Before you realize that bootpart does not take part in the booting process, any further discussion will be useless.

---

### Post by TeXtonyx on 2008-10-14
Quote:
when Bootpart transports one to the menu.lst screen

meierfra equivocated:
"Before you realize that bootpart does not take part in the booting process, any further discussion will be useless."

Bootpart was just short for the Bootpart method. I thought this was clarified when
I wrote: "to establish your claim that stage1.5 error reports would be advantageous
when also using the Bootpart (or Vista Bootloader) sector method."

Making this type of connection, considering context, is part of useful reading skills.
Besides, I know that Bootpart is involved in this process because when it fails, 
the exit is to a Bootpart informational screen, so the usage isn't that strained.

I don't think you are capable of providing the example I asked for so you diverted
the subject once again. All your posts contained helpful explanations but none of 
them established your original claim, which remained a speculation. I was willing
to defer to your experience, but you never demonstrated a specific experience to 
establish your original claim. I'm a little disappointed, but I realize that one can't 
make a silk purse out of a pig's ear. When you go to college it  could be a good 
idea to take a class in critical thinking (and speedreading). One states their premise,
and then marshals arguments to support the premise. That does not include
repeating the same original speculation as if it were evidence of a fact. :guitar:

---

### Post by meierfra. on 2008-10-18
> meierfra:  You seem to misunderstand the role of "bootpart". It only does two things:

1) It copies the bootsector of the Ubuntu partition to the file "ubuntu.bin".

2) It adds a line to "boot.ini:


> meierfra: Bootpart does not take part in the booting process.

Well, I was wrong about both of those statement. Bootpart does play a role in the booting process.
The file "ubuntu.bin" is NOT a copy of the ubuntu bootsector. Instead it contains:

I) Some code  (written by bootpart) which allows to chainload a boot sector.

II)  The location of the Ubuntu Partition: the number of sectors from the beginning of the hard drive to the begining of the Ubuntu partition. (Grubs Stage 1 is located at the beginning of the Ubuntu partition)

III) An error message, which  will be displayed if bootpart fails to  chainload the Ubuntu boot sector.

So the boot process works like this:

Bios->MBR->XP Boot sector-> NTLDR-> BootPart-> Grub's Stage 1->Grub's Stage 2-> Linux Kernel.


When you resized your Ubuntu partition, you got an error messages from Bootpart, since BootPart could not find Grub's Stage 1 anymore.


> Tex: I've never seen an instance where stage1.5 error messages were needed, so I never seen an advantage to those reports

Here are a couple of  recent cases where the Stage1.5 error messages  were the only indication  what could be wrong:

[http://ubuntuforums.org/showthread.php?t=944088]("http://ubuntuforums.org/showthread.php?t=944088")

[http://ubuntuforums.org/showthread.php?t=941038]("http://ubuntuforums.org/showthread.php?t=941038")

---

### Post by TeXtonyx on 2008-10-19
Thanks for a very educational post! I haven't read the links yet,
but I will. I also didn't realize the process described below:

"The file "ubuntu.bin" is NOT a copy of the ubuntu bootsector. Instead it contains:
I) Some code (written by bootpart) which allows to chainload a boot sector."

TeX: The reason is that earlier I have used the standard dd command
and then copied the output file to a fat32 folder, booted to XP, and 
copied the linux.bin into C:\ and it worked, invoked from boot.ini menu choice.
So I thought they were the same. Of course an error message from 
Bootpart isn't possible. I guess ntldr handles it.

But a similar odd thing, the old-fashioned method of adding
linux.bin to bcd/bcdedit. I'll just quote the quite relevant part.

[http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx](http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx)

"Step 2 – Get a copy of Linux boot sector

We will need to instruct Windows Boot Manager how to boot correctly Linux 
using Linux boot sector, which we will extract using dd.

•        On Linux, launch a Terminal with root privileges

•        Take a copy of Linux boot sector : dd if=/dev/sda1 of=/tmp/linux.bin bs=512 count=1

•        Copy linux.bin on a FAT formatted USB key or any storage accessible from Windows Vista"

TeX: This was the same method I used earlier, only with XP
and boot.ini, before I discovered Bootpart. 

"Step 4 –  Configure dual booting in Windows Vista 
•        Copy Linux boot sector on the root of the Windows boot (active) partition, namely the one containing bootmgr. If you don’t know for sure you can use diskpart or diskmgmt.msc to find out which one it is.

•        Create an entry for GRUB :

o   bcdedit /create /d “GRUB” /application BOOTSECTOR

o   Note: bcdedit will return an ID for this entry that we will call {LinuxID} below. You will need to replace {LinuxID} by the returned identifier in this step. An example of {LinuxID} is {81ed7925-47ee-11db-bd26-cbb4e160eb27}

•        Specify which device hosts a copy of the Linux boot sector

o   bcdedit /set {LinuxID} device boot

•        Specify the path to a copy of the Linux boot sector

o   bcdedit /set {LinuxID}  PATH \linux.bin

•        Add Linux entry to the displayed menu at boot time

o   bcdedit /displayorder {LinuxID} /addlast

• Let the menu be displayed 10 seconds to allow for OS selection

o   bcdedit /timeout 10

TeX: The only candidate I see for some "chainload" action is
o   bcdedit /create /d “GRUB” /application BOOTSECTOR (I think)

Now here is the (to me)intersting part that involves the modern
Easybcd method of making Linux a boot option from Vista bootloader

[http://neosmart.net/blog/2006/easybcd-15-multidual-boot-vista-linux-mac-os-x-bsd/](http://neosmart.net/blog/2006/easybcd-15-multidual-boot-vista-linux-mac-os-x-bsd/)
"You can’t get much simpler than this. With our new release of EasyBCD 1.5, booting into Linux, Mac OS X, or BSD straight from the Vista bootloader without ever having to add a single line of code reconfigure a thing is but a touch away!
You don’t have to configure a single thing! Once you specify a name for the entry and choose the platform + booting method (for Linux), you’re all set! If you can boot into Vista, you can boot into Linux or Mac OS X! No more re-configuring GRUB or Lilo, it just works – from the very first time."

TeX: A lot going on behind the scenes. About EasyBCD

"Chainloading is a dual-boot term that refers to one bootloader handing off the boot process to another. In this case, we configure the Vista bootloader to ask either Grub or Lilo (the most common Linux bootloaders) to complete the boot process for us - minimizing configuration requirements and ensuring maximum compatibility."

---

### Post by TeXtonyx on 2008-10-19
quote: Here are a couple of recent cases where the Stage1.5 error 
messages were the only indication what could be wrong:

[http://ubuntuforums.org/showthread.php?t=944088](http://ubuntuforums.org/showthread.php?t=944088)

[http://ubuntuforums.org/showthread.php?t=941038](http://ubuntuforums.org/showthread.php?t=941038)
--------------------------------------------------------

I found the first example very interesting, particularly your
figuring out about the old grub lurking in the woodpile. 

I have a question about the second example, error 18,
"Selected cylinder exceeds maximum supported by BIOS" which is
about exceeding the 8GB bios limitation. In this case the 
problem was fixed by making a 200mb partition before Windows. 

Ubuntu was installed at around the 25GB mark; install seemingly
works ok. Suppose grub was installed to the /boot partition
around that area. And the dd command was used to capture the
first 512 bytes, the file ubuntu.bin was moved to C:\ and
the proper entry was made in boot.ini to boot Ubuntu.

When you select Ubuntu from the boot.ini menu, won't it(ntldr?)
bring one to the menu.lst screen where you have your options to
boot different functions of Ubuntu?

My basic question is how does one know when an error message is
a stage1.5 or a stage2 error message since the error list is
identical. In the above paragraph, after one picks Ubuntu, won't
it try to load some kernel and fail, producing the error 18
message but it won't be a benefit of stage1.5 error reporting 
but stage2, since there is no stage1.5? Recall that the situation is
about dual booting Windows and Linux (grub installed to boot /).
I'm thinking that with stage1.5 one would find out there is a
problem at most a few seconds before stage2 would inform one in
this case. Have I made some fundamental assumption errors :-) ?

So right now I'm not sure that was a good example to prove your
point, but I think you did make the point that there is an
advantage to 1.5 error messages in some situations with a 
Windows Linux(->boot partition) dual boot. They don't seem yet 
to amount to be a large advantage equal to an important motivation.

You also made the point about the stage1.5 searching which 
Bootpart or dd doesn't include as far as I can tell, a definite + 
Thanks for your considered response.

---

### Post by meierfra. on 2008-10-19
> My basic question is how does one know when an error message is
a stage1.5 or a stage2 error message since the error list is
identical. 

 A stage 1.5 error message like this:

stage1.5 loading...
grub error 18

a stage 2 error message:

stage2 loading
grub error 18   Selected cylinder exceeds maximum supported by BIOS 

The OP in the link only reported "error 18".  So it could be Stage1.5 or Stage2.  

Error 18 can occur in three different ways:

1) stage 2 is out of reach of the bios (this gives grub error 18  from the stage1.5 files)

2) stage2 is  in the reach of the bios, but menu.lst is not.   I'm not 100% sure what happens in this case . One might  boot to the grub command line. Or one gets a stage2 grub error 18.

3)  stage2   and menu.lst  are within the reach of the bios, but the kernel is not.  The grub menu appears, and one gets the stage 2 grub error 18  after selecting  Ubuntu at the  grub menu.

1) is the most common case and I think that's what happened in the linked thread. But it might have been 2).  So you I right, it  might be a stage2 error. But I ensure you that Case 1) happens (but I'm too lazy to dig up a thread which contains absolute proof for this)

> When you select Ubuntu from the boot.ini menu, won't it(ntldr?)
bring one to the menu.lst screen where you have your options to
boot different functions of Ubuntu?

I don't think so. ntldr just loads "ubuntu.bin" which contains Grub's stage 1. Grub stage 1 will have the same problems trying  to reach  "stage2" as if stage1 is installed in the MBR. 

> So I thought they were the same.

Me too.  And if you google the ubuntu forums for "bootpart" you will see that everybody else seems to think so, too. But I downloaded bootpart yesterday and used a hex editor to look at the "ubuntu.bin" file created by boot part. To my surprise it had nothing  in common with Grub's stage1 file.


> TeX:
o bcdedit /create /d &#8220;GRUB&#8221; /application BOOTSECTOR
o bcdedit /set {LinuxID} device boot
o bcdedit /set {LinuxID} PATH \linux.bin 
o bcdedit /displayorder {LinuxID} /addlast


This is just Vista's way to add "linux.bin" to the vista boot loader. In XP you can do this by just adding "C:\linux.bin="Grub" to boot.ini.
linux.bin contains the Grub's stage 1. This code allows the Vista Bootloader to load Grub's stage1. So the Vista Bootloader chainloads Grub

Using EasyBCD has the same result. It just does all the steps for you.

---

### Post by TeXtonyx on 2008-10-19
So you are saying that when there are some errors, first reported in
stage1.5, so that there will be cases that the stage1->stage2 method 
used when grub is not installed to the MBR, but to the boot partition,
stage2 will simply fail, so that stage2 error reports will never happen,
thus those error reports will not ever be available as stage2 error
reports to help in diagnosing a problem, but only stage1.5 will provide this?

Above, I tried to restate what I understand you to mean, so that
if I understand you correctly, the answer to the question is "yes".

I went to the WinImage forum and read:

jaclaz wrote: "Bootpart does not "Load" anything, it just creates "alternative" 
bootsectors and adds (optionally) them to boot.ini or replaces current one. 

In a MBR or boot sector there is a "static" part and a "dynamic" part.
What bootpart actually does is to "automagically" combine the static 
part (which is inside the bootpart .exe) with the dynamic one that is 
extracted from the existing MBR/bootsector." 

"BOOTPART creates a 512 bytes file which contains an image of a boot 
sector that loads the boot sector of the partition. After, this file is declared 
in C:BOOT.INI (a text file used by Windows NT boot menu). The boot sector 
comes from FDFormat and WinImage."

Well, I guess that closes the issue. Thanks for your illuminating  remarks.

---

### Post by Abdul Haqq on 2008-10-24
This is the same question I have so I will post in this thread. The answers so far are totally confusing for a newbie: Hear simple is my problem.

Test Ubuntu install on hda1 an old ide drive. It worked so I went ahead and installed on sda1 over writing an XP installation. I forgot to tell the BIOS that the boot drive should be sda1 so grub wrote to the MBR of boot drive hda1.

Now can I get a step by step help on how to write grub to sda1 when I have to boot from hda1.

Eventually I want to take hda1 out of the case. :(

---

### Post by caljohnsmith on 2008-10-24
Abdul, first boot your Live CD, open a terminal (applications > accessories > terminal), and do:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd1,0), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
That will write Grub to the MBR (Master Boot Record) of the Ubuntu drive, so you should be able to boot from it; that should at least get you the Grub menu on start up, but most likely you will not be able to boot Ubuntu from the menu. 

To boot Ubuntu, when you get the Grub menu on start up, select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,Y)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Ubuntu. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent.

So if it works, when you get into Ubuntu, just do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "#groot=(hdX,Y)" to whichever (hd0,Y) that worked to boot Ubuntu. Save, quit gedit, then run:
```
sudo update-grub
```
And that should be all you need to do to boot Ubuntu from Grub. Let me know how it goes. :)

---

