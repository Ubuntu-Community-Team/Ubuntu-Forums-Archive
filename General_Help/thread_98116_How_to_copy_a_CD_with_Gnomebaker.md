---
title: "How to copy a CD with Gnomebaker?"
date: 2005-12-02
forum: General Help
---

### Post by wargames on 2005-12-02
I have one CD/DVD burner and tried to copy a audio cd using Gnomebaker but so far it will not copy it. Using Gnomebaker, I tried using Copy Data CD and checking ISO image but that doesn't work either. I tried using Copy audio CD and that doesn't work either. The Copy Data cd option just puts a small garbage iso file in my home directory. And trying to use the Copy Audio CD with one CD drive will read the CD until around 53% and then stops, ejects the CD, then closes the CD door real quick, and then states it has Failed. Does Gnomebaker just suck, or am I doing something wrong? I've tried for almost an hour and still can't figure out why it doesn't work. I even followed the Help section for Gnomebaker and that doesn't work. I tried using the basic Gnome Copy to ISO feature but it takes forever and I have DMA turned on for my drives as well.

I need to make several copies of my audio cd and so far I can't find any way to do it without the errors and without it taking forever.

Any ideas what's wrong or what I'm doing wrong?

---

### Post by teaker1s on 2005-12-02
did you install with synaptic if so use preferences to see recomended files as dependencies also tick burnfree-to avoid underwrite.

---

### Post by ozorba on 2005-12-02
Have you tried to run it in super user mode?

i.e. sudo gnomebaker

--
OZ

---

### Post by cstudent on 2005-12-02
Put the CD in you want to copy and open terminal

Enter:

sudo  dd if=/dev/cdrom of=/path_you_want_to_save_to/cdrom_image_name.iso

Then use Gnomebaker to write the .iso file to a new disk.

Bill

---

### Post by wargames on 2005-12-02
[QUOTE=teaker1s]did you install with synaptic if so use preferences to see recomended files as dependencies also tick burnfree-to avoid underwrite.[/QUOTE]

This is not an installation problem. I also checked burnfree option but this is not the problem either. I can't even get to the point of burning the cd because Gnomebaker fails on just reading the source cd, even though the source cd is fine.

Thanks anyway.

---

### Post by wargames on 2005-12-02
[QUOTE=ozorba]Have you tried to run it in super user mode?

i.e. sudo gnomebaker

--
OZ[/QUOTE]

Why would I need it to run in super user mode? I'm not doing any administrating tasks.

Thanks anyway.

---

### Post by wargames on 2005-12-02
[QUOTE=cstudent]Put the CD in you want to copy and open terminal

Enter:

sudo  dd if=/dev/cdrom of=/path_you_want_to_save_to/cdrom_image_name.iso

Then use Gnomebaker to write the .iso file to a new disk.

Bill[/QUOTE]

I guess I could try this, but how is this any different than using the basic Gnome Copy CD to ISO option? Would this ternimal command still take just as long as using the basic Gnome option?

---

### Post by wargames on 2005-12-02
I went ahead and tried the dd command and that does not work either. It gives an cdrom error. I then decided to try the basic Gnome CD copy to ISO option and it gets about 1/4 the way into it and then seems to freeze up. I tried Gnomebaker and it doesn't work either. What's weird is that I can play this CD just fine with the CD player but I can't make a ISO image file of it. The basic Gnome CD copy to ISO option reports that it will take 20-30 minutes just to create a ISO image!  What's wrong?

My system is an AMD64, with 1.5Gigabytes Ram, CD/DVD Dual layer burner, 80GB HD, ATI Radeon PCIe x200 graphics, etc.  DMA is turned "on" on all drives too. I don't want to use k3b because I don't what the kde stuff that comes along with it. 

Any idea what's wrong? Maybe CD functions in Linux are still in beta or something. Any suggestions would be great. If I can't fix this problem pretty soon, then I'll have to load up Windows and do the copy.

---

### Post by olavi on 2005-12-02
I probably don't have an answer, but what's the drive model? Are you running the AMD64 version of Ubuntu?

I've heard that some Plextor models use their own interface extensions that are blocked by the Linux kernel or something.

I had different kind of problems with GnomeBaker, but everything worked with the standard Gnome utilities. :(

---

### Post by wargames on 2005-12-02
My CD/DVD burner is model: HL-DT-ST DVDRRW GWA-4164B

I uninstalled Gnomebaker and then installed Graveman.

Graveman does not work either. Here is the error message from graveman:

Cannot create image: /usr/bin/readcd: Success. read_g1: scsi sendcmd: no error
CDB:  28 00 00 00 00 00 00 00 40 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0E 00 00 00 00 64 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x64 Qual 0x00 (illegal mode for this track) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 131072
cmd finished after 0.002s timeout 40s

Weird, I can play audio CD's just fine, and play DVD movies as well, so why can't I burn, or make ISO image files?

---

### Post by wargames on 2005-12-02
I'm running the 32bit version of Ubuntu 5.10.

---

### Post by nix4me on 2005-12-02
Sounds like you have hardware problem or hardware incompatibilty.

I copy cds and dvds all the time with my pioneer drive and with graveman, k3b, gnomebaker.

nix4me

---

### Post by teaker1s on 2005-12-02
GnomeBaker depends on 'cdrecord' make sure it's installed or no cd burning

---

### Post by xmastree on 2005-12-02
It sounds to me like the drive is having trouble reading the disc. Is it just data? If so try to copy all the files into a folder somewhere. If that works it ought to be possible to use nautilus' built in burner to copy them to the new disk.
If it's bootable, audio, or something other than plain data they you'll need to make an image.
But try just reading the disc first. if it's audio, play it.

personally I don't like gnomebaker, I prefer k3b. There's also nero for linux, but it's not free. Shareware works for 30 days.

---

### Post by dcstar on 2005-12-02
[QUOTE=wargames]I went ahead and tried the dd command and that does not work either. It gives an cdrom error. I then decided to try the basic Gnome CD copy to ISO option and it gets about 1/4 the way into it and then seems to freeze up. I tried Gnomebaker and it doesn't work either. What's weird is that I can play this CD just fine with the CD player but I can't make a ISO image file of it. 
........
Any idea what's wrong? Maybe CD functions in Linux are still in beta or something. Any suggestions would be great. If I can't fix this problem pretty soon, then I'll have to load up Windows and do the copy.[/QUOTE]
There are CDs that have "Copy protection", this could be one of them.

---

### Post by wargames on 2005-12-03
Hi again.

I have cdrecord already installed.

This audio CD does not have copy protection, because it was made by someone I know on their Windows PC.

This audio cd plays just fine using the CD Player installed in Gnome. All the tracks seems to play just fine and DVD's play fine too.

DMA is turned ON.

I can't burn anything, and I can't seem to make a ISO image either using the terminal or any GUI program for some strange reason. On one of my past posts above, Graveman won't even access the cd burner drive to read the audio cd, it just gives the error message I posted earlier. Graveman seems to see the drive and has it listed in it's drop down menu but still no go.

Gnomebaker will start to read the audio cd and then it stops around 53%, ejects the CD real quick and closes the tray again, and then issues a Failed message.

Using the Gnome Copy CD to ISO option will give me different cd megabyte sizes as well as being slow as heck to read the CD to image file and will seem to hang around having 1/4 of it done. One second the drive will report the size as 149MB, then if I try again it might report 589MB and if I try again it might report 324MB. Weird!

I tried changing the /etc/default/cdrecord setting file from /dev/cdrw to /dev/hdc but that didn't work. I tried changing the /etc/fstab setting and put "rw" in the /dev/hdc line and rebooted and that didn't work.

When I open terminal and issue the command "cdrecord -scanbus" here is the output:

Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.12-10-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

It makes me wonder if the real problem may be with this version of cdrecord because it states above "cdrecord: There are unsettled issues with Linux-2.5 and newer." And Ubuntu 5.10 uses a 2.6 kernel.

I did more searching on the Ubuntu forums and a saw alot of other people having CD burning issues as well. Any idea what is going on and how to fix this?

Using the past Ubuntu 5.04 Hoary I was able to burn cd's on this same PC and don't recall having this issue. So what changed?

---

### Post by xmastree on 2005-12-03
Just a thought here, but when you copy a CD you need space to create the image first. You're not running out of disk space are you?

---

### Post by wargames on 2005-12-03
[QUOTE=xmastree]Just a thought here, but when you copy a CD you need space to create the image first. You're not running out of disk space are you?[/QUOTE]

Nope. Lots of space left on my 80GB drive.

---

### Post by wargames on 2005-12-03
Ok, I did a test.

I used Sound juicer to rip a different audio cd, and ripped 2 tracks off of it. That worked ok even though it was doing it at only 2.x speed.

Then I used the nautilus CD/DVD Creator and inserted a blank CDRW disc and burned the two ogg files and that seemed to work.

I then reinserted the original audio cd I just test ripped, and then tried to use the Gnome Copy CD to ISO option and again, just like before it didn't work. It reached about 1/4 maybe a little bit more and then seemed to hang, or start going extremely slow. I waited for a little while and nothing seemed to be happening so I canceled the image job.

So I can rip with Sound juicer even though it seems really slow at 2.2 to 2.4 speed. And I can burn a data cd in using nautilus. But why can't I use Gnomebaker, Graveman, or make a ISO image file? Why does running "cdrecord -scanbus" result in cdrecord not detecting my cd burner? Why does it seem so slow to rip?

---

### Post by xmastree on 2005-12-03
Well, using sound juicer is a workaround, but if you're fussy then creating ogg files is going to cause degradation. You might want to set it to lossless quality in the preferences, especially as you'll (presumably) not be keeping the temporary files.

I have no idea why you might not be able to use other programs, unless there's some sort of protection on it which was copied with it in windows.

I would try a different Audio DC, an original one. Just to see what happens.

---

### Post by wargames on 2005-12-03
[QUOTE=xmastree]Well, using sound juicer is a workaround, but if you're fussy then creating ogg files is going to cause degradation. You might want to set it to lossless quality in the preferences, especially as you'll (presumably) not be keeping the temporary files.

I have no idea why you might not be able to use other programs, unless there's some sort of protection on it which was copied with it in windows.

I would try a different Audio DC, an original one. Just to see what happens.[/QUOTE]

The audio cd has no copy protection on it. It was made by a singer I know, and they burned their own cd on their Windows machine.

I still cannot use Gnomebaker or Graveman, and I cannot make a ISO of any cd I've tried so far. Why do I get such slow rip speeds of 2.2 to 2.4 in Sound juicer? This is a 52x CD/DVD dual layer burner with DMA turned on. I know I'm not the only one with this slow rip speeds and weird cdrecord issues because I've read plenty of posts on here of people with the same problem but so far I have not seen an answer to it. This problem seems to have been introduced with Ubuntu Breezy, because several other people report the same problem and they tried Mandrake and Suse and their drives worked just fine under those distros. So I believe something is going on in Breezy, some kind of bug or error or something. I'm still looking for a solution and if I find one or someone else knows whats going on and how to fix it then please post it here. This issue is really starting to annoy me.  ](*,)

---

### Post by AmphetaMarinE on 2005-12-04
[QUOTE=wargames]
I still cannot use Gnomebaker or Graveman, and I cannot make a ISO of any cd I've tried so far. Why do I get such slow rip speeds of 2.2 to 2.4 in Sound juicer? This is a 52x CD/DVD dual layer burner with DMA turned on. ](*,)[/QUOTE]

You do NOT have a 52x cd/dvd burner mate... trust me on this...
These are the specs for you **LG GWA-4164B Super Multi-DVD+-RW**
[LIST]
[*]40xCDR CAV
[*]24xCDRW ZCLV 	
[*]16xDVD-R CAV
[*]6xDVD-RW ZCLV
[*]4xDVD-RDL CLV
[*]16xDVD+R CAV
[*]8xDVD+RW ZCLV
[*]6xDVD+RDL ZCLV 
[/LIST]

Anyway.. on to your problem... have you tried updating your firmware? A lot of different DVD burners (notably LG and Liteon models) have trouble reading specific CD's upon release... I have found many of these problems are firmware related....
In most cases you will need a windows installation handy to perform the update, as not many manufacturers supply linux binaries for their firmware, and **none** seem to supply source code for them... (This, I assume, is because of the MANY people hacking their firmware to allow 'upgrading' or 'overclocking' of their drives, to support features available in drives which theirs has hardware support for, but not firmware support)...

If you do this, you will likely have to add your drive back into breezy somehow, (I'm unsure how... I'm quite new to linux), but if you say the disc is good, and there is no copy protection, then the only thing i can think of is firmware, or a dying drive....

Now the fact that it works in other distros, could also mean that support is sketchy under breezy, but that is hard to believe since ubuntu is based on debian, which should be one of the more heavily reliable distros, and should offer very good hardware compatibility....

Regardless, a firmware update will rule out **everything** except for a dead (or dying) burner, and sketchy support under breezy....

If the firmware update doesn't work, try copying from a different drive, as burning is not your issue, because your copy fails during the read process....

If another drive works, then you probably have a dead drive... if not, then the problem is somewhere inside ubuntu itself.

Hopefully you have access to a windows installation to perform the firmware upgrade, and if so, here is a link to LG's Support Page where you can obtain the files you will need...

[http://www.lge.com/support/software_gcsc.jsp](http://www.lge.com/support/software_gcsc.jsp)

Once there, select your location, then on the next page, choose 'DVD-ROM(Writer)' and any OS you happen to have access to....

After that you will see a link called 'LG ODD Auto_FW.exe'...
Should maybe help out.

Cheers,
Amph

---

### Post by wargames on 2005-12-04
There is nothing wrong with my CD/DVD burner and it does not need a firmware upgrade. It is only a few months old. The same drive plays this same cd just fine under the CD player and vlc plays dvd's just fine as well using the same drive. As far as the drive's speed being 52x, my bad, I must have been thinking of my other PC, but this doesn't really matter, since it is fast enough and should be ripping cd's alot faster than 2.x. This drive works great and is very fast under Windows XP and as stated above, I'm trying to make an ISO of a cd of a friends that he made of himself singing. This is not a commerical cd and it does not have copy protection. I've tried multiple other cd's as well and nothing works. I've searched these forums for many hours and have found plenty of other posts stating the same or very similar errors such as the one I'm having with cdrecord. So if other's are experiencing the same thing as me, then I know it's not just my hardware, it's something in Ubuntu Breezy. Either a setting or a bug or something.  I saw where some people started having trouble as soon as they upgraded or installed Breezy with burning cd's and dvd's, so I think this might have been introduced in the Breezy release. Me along with several others are trying to figure this one out, but so far no go. I'll keep experimenting with different settings, applications, etc. and see if I found out anything.

If anyone else knows anything or has another suggestion just let me know.
Thanks.

---

### Post by AmphetaMarinE on 2005-12-04
regardless of whether you bought it a few months ago, or a few days ago, it will still most likely have an old firmware revision....
How can it hurt to give this a try?
My only other suggestion is to visit [http://www.speedlabs.org](http://www.speedlabs.org) (**Not** a shameless plug, but a site dedicated to optical burning) and post in the forum there, specifically asking a member named chakkers, and another named zebra...
They will need the output you posted previously which details the burning process and errors there....

---

### Post by wargames on 2005-12-04
First, there is not a firmware upgrade for this drive. Also, you should not be upgrading CD/DVD drives firmware unless there is a very very good reason to do so, because there is always a chance that the firmware upgrade could go bad and leave you with a dead drive. Same rule goes for BIOS upgrades as well. 

Also, since I just stated that this drive works great under Windows then I think this pretty much rules out any need for a firmware upgrade, and it also rules out that the drive is bad.

This is a Ubuntu Linux problem, whether it's a setting, a bug, or application fault or some hardware support issue in the kernel, I still working on it. I'll keep searching.

Any other suggestions would be welcomed.

---

### Post by AmphetaMarinE on 2005-12-04
But it **does not** rule out the possibly that breezy might not play nice with your drive **under it's current firmware revision.**
Anyways.. I'm not one to argue... offered advice, you obviously don't like it...
So good luck mate, hope you sort it out yourself :)

---

### Post by angrykeyboarder on 2005-12-04
[quote=wargames]I have one CD/DVD burner and tried to copy a audio cd using Gnomebaker but so far it will not copy it. Using Gnomebaker, I tried using Copy Data CD and checking ISO image but that doesn't work either. I tried using Copy audio CD and that doesn't work either. The Copy Data cd option just puts a small garbage iso file in my home directory. And trying to use the Copy Audio CD with one CD drive will read the CD until around 53% and then stops, ejects the CD, then closes the CD door real quick, and then states it has Failed.....[/quote]

By chance is this one of the newer sucky audio CDs (that's technically not a CD anymore) that has copy-protection built in?  If so, that could be your problem.  If it is, I believe there are devious ways of bypassing this in Linux, but I'm not familiar with them.

To the best of my knowledge, "COPY-PROTECTED" is usually on the outside label somewhere (I've only bought one so far. I'm not keen on these).

---

### Post by xmastree on 2005-12-04
From a previous post (#21), the CD was made on a Windows machine by the artist himself.

---

### Post by aclaunch on 2005-12-04
What are your permissions for your CD/DVD ROM and CD burner.  Presumably you have both so do "ls -l /dev/cdrom" and "ls -l /dev/cdrom1"; this should show something like this:

aclaunch@moria:~$ ls -l /dev/cdrom1
lrwxrwxrwx  1 root root 3 2005-11-30 22:08 /dev/cdrom1 -> hdd

This is my CD/DVD ROM. Next do "ls -l /dev/hdd"

aclaunch@moria:~$ ls -l /dev/hdd
brw-rw-r--  1 root cdrom 22, 64 2005-11-30 22:07 /dev/hdd

Note the permissions; read and write permissions for root and people in the group "cdrom" and read permissions for all others. You can also check what groups you are in with "less /etc/group"; you should be in the cdrom group.

Good Luck ,
Alan

---

### Post by angrykeyboarder on 2005-12-04
[quote=xmastree]From a previous post (#21), the CD was made on a Windows machine by the artist himself.[/quote]

DOH! ](*,)

---

### Post by apolyak on 2005-12-04
Try NeroLinux. I think that NeroLinux doesn't use cdrecord and other Linux CD/DVD related utilities. That way you can separate hardware / software possible problems.
Regards

---

### Post by wesdeboer on 2005-12-04
Well just because it's frustrating seeing people keep giving you the same replies that you've already ruled out, i'll try helping with something new.

you said that you are using ubuntu 510 386 when you stated that you have amd64, now i'm not much of a linux geek but when ubuntu releases an amd64 version of ubuntu 510 you should maybe try that as this seems to be an ubuntu/hardware related problem. if you don't want to re-install or perform the upgrade, try the live cd and see if that works, then you know and you can perform the upgrade/reinstall then.

---

### Post by wargames on 2005-12-04
Just to repeat myself again, this cd is not copy protected, no Sony rootkit or other DRM silly stuff to worry about.

Now that, that is out of the way. For those that might not know, you don't have to use the 64bit version of Ubuntu just because you have a AMD64 processor. 32bit OS versions run just fine, just like the regular Windows XP or the 32bit version of Ubuntu. The reason I don't run 64bit version Ubuntu is because certain programs are not made in 64bit versions and from what I can tell, you won't really see a speed improvement anyway, plus the 64bit version seems like it's too bleeding edge for me to mess with, since the 64bit goodness is still being sorted out, while the 32bit version has a longer track record. I hope that made sense.

And about the firmware not being the problem, to further support that idea, the other people that had this same type of problem had different cd/dvd burner drives all made by different companies. So unless there is a major firmware conspiracy going on, this it not the problem.

I've already checked and yes, I'm in the cdrom group too.

Anyway, I getting ready to do more trouble shooting now on this subject so if anyone else would like to add their 2 cents go ahead. If you need a recap on what the problem is, then start on page 1 of this post and please read my posts.

---

### Post by xmastree on 2005-12-04
You're a very tenacious man. I think that by now I would have *'just done it'* in windows. I admire your spirit. :-)

---

### Post by wargames on 2005-12-05
[QUOTE=xmastree]You're a very tenacious man. I think that by now I would have *'just done it'* in windows. I admire your spirit. :-)[/QUOTE]

Thank you. I guess I could do it in Windows, but I'm determined to use Linux and try to get away from Windows. I don't give up easily. ;)

Now, back to work....

---

### Post by AmphetaMarinE on 2005-12-05
[QUOTE=wargames]

When I open terminal and issue the command "cdrecord -scanbus" here is the output:

Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.12-10-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
**[COLOR="Red"]cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.[/COLOR]**
cdrecord: For possible targets try 'cdrecord -scanbus'.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

[/QUOTE]

Just a thought, but maybe it's to do with this ???

I mean, I know a LOT of programs which access cd drives directly rely on a scsi driver... (specifically an aspi driver, which essentially translates scsi commands to work on atapi drives)

And I also learned last night, that scsi support is not built into breezy, but requires a command line option during the kernel compile.....

Not sure just how much effort you want to put into this, but a kernel recompile including scsi support may help....

---

### Post by aclaunch on 2005-12-05
FWIW, I think this has to be a permission problem or something else equally simple but not necessarily intuitive. If it worked in Hoary and in Windows as the OP said it's not a hardware problem. When I set up Breezy last week (after being frustrated with Dapper's bugginess/broken ways), I got all sorts of messages about not being able to "write to device" when trying to play a CD and hence, no sound/would not play. I changed permissions and it all works fine. After I started reading this thread, I installed Gnomebaker and copied a commercial CD without a problem; so I don't think its something broken in Breezy or with Gnomebaker.

My .02$ worth.

Alan

---

### Post by xmastree on 2005-12-05
[QUOTE=aclaunch]FWIW, I think this has to be a permission problem [/QUOTE]I don't think so. If it were, then I'm sure the process wouldn't even start to read the CD. AIUI, it starts but doesn't complete reading and creating an image.

---

### Post by aclaunch on 2005-12-05
I'll probably get flamed for this but... is the OP just having an interface problem? I just tried copying a CD using only a single drive. Put the CD in, click "copy audio CD". The progress bar goes to 50% (cause the job is only half done) and then ejects the disc. I didn't grab it out in time and so the tray retracted and then tried to burn onto the original audio disc. After about 10 sec, I get a sound and the "Failed" message comes up. If you drop down the "Show output" window you get:

Starting to write CD/DVD at speed 16 in real TAO mode for single session.
Last chance to quit, starting real write in 5 seconds.   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is ON.
Performing OPC...
cdrecord: Success. read track info: scsi sendcmd: no error
CDB:  52 01 00 00 00 FF 00 00 1C 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 30 06 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x06 (cannot format medium - incompatible medium) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 28
cmd finished after 0.000s timeout 240s
Writing  time:    0.049s
Average write speed 999.0x.
Fixating...
cdrecord: Cannot get next writable address for 'invisible' track.
cdrecord: This means that we are checking recorded media.
cdrecord: This media cannot be written in streaming mode anymore.
cdrecord: If you like to write to 'preformatted' RW media, try to blank the media first.
cdrecord: Cannot get next writable address.
cdrecord: Success. close track/session: scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 30 06 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x06 (cannot format medium - incompatible medium) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.011s timeout 480s
cmd finished after 0.011s timeout 480s
Fixating time:    0.023s
cdrecord: Cannot fixate disk.
cdrecord: fifo had 64 puts and 0 gets.
BURN-Free was never needed.
cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.

So 2 things come to mind: he didn't switch to a blank disc quickly enough and it tried to write back to the original disc and couldn't and failed or, second, he keeps talking about making an iso of an audio disc. I'm not sure if you can even do this as iso images are for data and meant to be mounted like a regular drive (for booting off of etc.). This is NOT the way to copy an audio CD.

I wish the OP would repost his step by step experience with output from the "Show output" window of Gnomebaker.

Thats it - fire away.
Alan

---

### Post by wargames on 2005-12-05
Updated, and fixed!! \\:D/ 

Yes that's it Aclaunch.

I was doing some testing and found out that Gnomebaker was ejecting the audio cd very fast and then trying to write back to it. So what I did was after it gave the Failed message, I noticed that it keeps all the audio tracks in it's temp. folder, so I inserted a blank cdrw disc, choose Copy audio CD and it asked if I wanted to use the already stored tracks. I answered Yes and it burned the audio tracks to the blank cdrw as a audio cd and it played great. I just wish Gnomebaker would have asked for me to insert a blank cd and then proceed with the copy, but at least I now know that Gnomebaker is working just fine. It was just unclear at first what was going on there. Now I know the steps for Gnomebaker with a single CD/DVD burner drive.

I feel so stupid about the next part. I did not know this but you cannot make a ISO of a audio CD using the basic Gnome Copy CD to ISO option. This only works with data CD's. I just figured that it would read the 1's and 0's raw into a CD image, but I guess this doesn't work with audio CD's because of the audio CD's format. So yes, I can make ISO's of data CD's just fine.

Now with Graveman. This is basically the same thing that happened with the basic Gnome Copy CD to ISO mistake. I fired up Graveman, choose Duplicate CD option and told it to make an ISO of the audio CD. Well, it would spit out an error message doing this, but would work just fine with a data CD.

I'm guesssing this would be true of using the dd command on a audio cd as well. I guess you can only use the dd command on data cd's and not audio cd's. Is that correct?

I just wished that the Gnome option and Graveman would have detected that it was an audio CD and told me with a Warning message window, that a audio CD could not be made into an ISO. And I wished that Gnomebaker would have paused, given me a message to insert a blank cd into the drive before it attempted to write the cd.

Most of this was due to things being done in an unclear manner and not providing good feedback to the user about what the problem was. Now that I know what's going on, I feel alot better about it. Maybe the developers will consider putting better feedback to the user when a error occurs since this stuff seemed unclear to what the real problem was.

Anyway, thanks guys for your input and suggestions. Maybe someone else will find this information useful too.

---

### Post by xmastree on 2005-12-05
[QUOTE=wargames]Updated, and fixed!! \\:D/ [/quote]

[SIZE="4"][COLOR="Red"]W00T![/COLOR][/SIZE] \\:D/


> I did not know this but you cannot make a ISO of a audio CD using the basic Gnome Copy CD to ISO option.I didn't know that either. However, I have seen audio CDs distributed as .BIN/.CUE packages, maybe that's the reason.

> Maybe someone else will find this information useful too.Indeed. This thread is going in my 'useful stuff' folder.

---

### Post by SlugO on 2006-02-08
I had the same problem, Gnomebaker gave me 1/10 of a second to switch an empty CD to the tray. "Think fast!!!" :twisted:

As a whole I'd say that burning tools in Linux are still in alpha stage :???:
What with all the cdrecord's and other flimsy solutions that won't even work with normal priviledges :P

---

### Post by Titi on 2007-07-06
i've had the same problem. so i can not make iso's of audio cd's? i didn't know that at all. so i should rip the tracks and burn them? good to know, thanks a lot :)

---

