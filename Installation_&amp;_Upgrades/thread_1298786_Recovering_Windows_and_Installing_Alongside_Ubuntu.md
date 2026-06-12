---
title: "Recovering Windows and Installing Alongside Ubuntu"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by Noobs*McGee on 2009-10-23
I'm currently running Ubuntu 9.10 (just upgraded to the beta from 9.04) and I have kind of a unique question:  When I originally installed Ubuntu on my laptop, I was coming from WinXP, and had originally intended to partition my drive and install Ubuntu alongside Windows.  However, due to some complications in installation (and the fact that I wasn't really that attached to Windows in the first place) I decided to just wipe the drive and do a clean install.
Recently, however, I have run into some frustrations with compatibility issues, and have decided it would just make my life a whole lot less complicated if I could just have Windows back.  However, I'm hoping I can have my cake and eat it too:  I really want to restore Windows, but keep my Ubuntu install as well, either both on the same harddrive or one (primary OS) on the internal drive and one (secondary) on an external (if that's possible?).
So, here's what I have to work with.  I don't have an actual install disc for WinXP, but I do have the recovery disc that came with my laptop (which I guess installs the factory disc image to your hard drive?).  So I'm figuring I:
1) will have to format my computer's internal drive and do a clean install from the recovery disc, in which case I would like to back up my current installation of Ubuntu (as well as all data) and either reinstall alongside Windows (preferred) or install on an external drive and run Ubuntu from that.
OR
2) If it's possible to partition the drive as it is and use the recovery disc to install Windows alongside Ubuntu without doing any reformatting, that would be ideal.
OR
3) If it's possible to designate the external drive for the recovery disc to format/install on, that would be good too.  (I assume I will have to partition the external drive first).

I know basically zero about partitioning drives or installing OSes, so I need a lot of help on this one.  If anyone can tell me if any of the above options are possible, and can walk me through one of them, I would be eternally grateful.

Hoping for a response,
NM

Oh, also, I'm running Ubuntu 9.10 Desktop Kernel 2.6.31-14-generic, GNOME ver 2.28.0, on a Toshiba M45 Satellite with 1.60GHz Intel Pentium M Processor and 1GB RAM (if any of that is useful).

---

### Post by mikewhatever on 2009-10-23
1)I'd recommend backing up the Ubuntu partitions to an external drive with Partimage or Clonezilla. Basically, you can backup a partition into an image file and restore the data to a different partition later.

On the other hand, you could backup only the home folder with rsync, then reinstall Ubuntu and restore the home folder.
[http://psychocats.net/ubuntu/backup](http://psychocats.net/ubuntu/backup)

2),3)There are questions to whoever made the recovery disks for your computer. Generally speaking, the procedure should format the entire drive and reinstall Windows. I also very much doubt the recovery process will work on a USB device.

Since you aren't really comfortable with partitioning, and there is possibly no way to accomplish what you want without that, perhaps you could practice manual partitioning in Virtualbox first.

---

### Post by Mark Phelps on 2009-10-23
> **mikewhatever said:**
> ... 
2),3)There are questions to whoever made the recovery disks for your computer. Generally speaking, the procedure should format the entire drive and reinstall Windows. I also very much doubt the recovery process will work on a USB device.

+1

I've done system recoveries on several XP machines, and in every case where I used a set of vendor-supplied recovery CDs, they completely wiped and reformatted the hard drive -- and in NO cases did they provide me any options.

Plus, they typically took HOURS to run.

So, if you take this route, wait as long as it takes for the process to finish -- best to let it run overnight.

---

### Post by Noobs*McGee on 2009-10-24
Hey guys, thanks for the replies.

I don't know what VirtualBox is, nor how to use it.  I have partitioned a hard drive before, as I had to when I was installing Ubuntu on this box, so I have a vague idea of the process.  I mainly was just wondering about what was possible in terms of backing up my current install of Ubuntu or installing Windows alongside it.  However, I'm pretty sure my recovery disc will wipe the hard drive and do a clean install, so the latter isn't really an option.
Mikewhatever, I like what you suggested about backing up my Ubuntu partitions to an external drive and then restoring to a different partition later.  I have a couple questions about that:
1)  Would the USB Startup Disk Creator that comes with Ubuntu be applicable for this?  I'm just not familiar with Partimage or Clonezilla, and I'd like to work with whatever utilities have the shallowest learning curve possible, as I'd like to get all this taken care of as soon as possible.
2)  If I went with the external backup approach (regardless of what utility I used) would that preserve all my settings?  I've done a lot of customization with the user interface since installing Ubuntu, and I wouldn't want to have to go through setting it up all over again.  Also, it  would be nice if I didn't have reconfigure my browser/mail client settings, and I'm sure there's a thousand other little changes I've made that I'm not thinking of right now.
3)  What are the advantages of backing up only the home folder, and would I still be able to retain all my settings (assuming that the answer to #2 is "Yes"...)?

Also, I'm not sure if anyone here would be able to answer this, but I was considering purchasing a copy of Windows 7 Professional, since I can take advantage of Microsoft's student discount, and I was wondering if you would recommend purchasing this or sticking with Windows XP?  Furthermore, if I do end up getting Windows 7, would it be possible to just install it alongside the currently installed Ubuntu (I think I left 8 or 10GB open when I partitioned my HDD for the Ubuntu install)?  And assuming it is possible, would you recommend doing this, or just doing a clean install and backing up Ubuntu like I was planning on doing with the XP restore?

Sorry for the long reply, but as I said (and my name implies) I'm a bit of a n00b, so I need all the help I can get :biggrin:

Looking forward to your response,
NM

---

### Post by skyiscrying on 2009-10-25
Well, if you are going to purchase a copy of Windows7 - a full install copy, not the upgrade, - you can always re-format, start afresh, and use the Wubi Ubuntu Installer through Windows7 when that OS is installed.  Back up to USB drive or CD/DVD anything that is important to you, first. 
I am a great fan of Wubi, and never had any trouble booting into the Windows OS or Ubuntu.

---

### Post by Mark Phelps on 2009-10-25
> **skyiscrying said:**
> ... you can always re-format, start afresh, and use the Wubi Ubuntu Installer through Windows7 when that OS is installed...

Unfortunately, Windows 7 default install to a clean disk has produced situations where Wubi installs do not appear to work.  Folks have been reporting LOTS of problems going that route and no apparent solution has been reported.

---

### Post by Noobs*McGee on 2009-10-26
Hey skyiscrying, thanks for the suggestion.  I'm not really familiar with Wubi, but I checked it out, and it looks pretty cool.  However, I'm not really looking for anything like that, I just want to have my full install of Ubuntu 9.10 on a separate partition -- I don't think I (personally) like the idea of having Ubuntu as an "application".  Also, in my experience, that sort of thing is kind of heavy on the processor.  And given the problems Mark Phelps pointed out, it doesn't seem like Wubi would be practical anyway if I go with Windows 7.

Any other thoughts on my last post though?  I'd really like to get this sorted out soon.

Thanks,
NM

---

### Post by Noobs*McGee on 2009-10-26
Couple of things:

1) Nevermind about the USB Startup Disk Creator question, I know what that is now.  However, I seem to recall something from when I was installing Ubuntu about a utility for partitioning drives - does this sort of thing exist in Ubuntu (as in, included with the OS, as opposed to a program you have to download)?

2) I checked out Clonezilla and Partimage, and while the page for Partimage was a little easier to follow, I'm still unsure if I can accomplish what I want with either program, or if I can, how.

I going to try laying out exactly what my situation is and what it is I want to accomplish here, and hopefully someone can give me a step by step on how to do it:

[LIST]
[*]I have Ubuntu 9.10 installed on my laptop (100GB) HDD, configured and customized just the way I want it, with a number of non-standard UI changes, applications, etc.
[*]I have a 250GB FAT32 USB harddrive, which is totally unused.
[*]I want to backup my current installation of Ubuntu -- configuration tweaks, installed programs, and all -- to my USB harddrive
[*]I then want to restore WinXP on my laptop's internal HDD, or do a clean install of Windows 7* (which I did end up ordering, and should be getting sometime in the next week), whichever would make the next step easier.
[*]Next I want to partition my internal HDD so that I can restore the backed-up installation of Ubuntu alongside Windows so I can boot to either one.
[/LIST]
This doesn't seem like it should be all that hard to accomplish given the know-how.  I feel like *someone* on here should be able to help me out...  I would really, really appreciate the help [-o<

Anybody...?

-NM

*p.s. unless it would be easier for some reason to do the restore of WinXP and then upgrade later to Win7 after restoring the Ubuntu install, I'd be inclined toward a solution involving a clean Win7 install, since I will be switching to Win7 either way.

p.p.s. I just checked the email I got after ordering Win7, and it says "Windows 7 Professional Upgrade 32-bit Disc Kit" so I'm guessing it's not the install copy.  Does that mean I will have to restore to WinXP and then upgrade to Win7 before partitioning/restoring the Ubuntu install?  (sorry to add another question)

---

### Post by Noobs*McGee on 2009-10-26
Still no responses?  Why do my posts never get any love? :(

I came across the following link in the mean time: 
[http://www.mydellmini.com/forum/ubuntu-netbook-remix/13077-backing-up-ubuntu.html](http://www.mydellmini.com/forum/ubuntu-netbook-remix/13077-backing-up-ubuntu.html)
and I'm wondering if it would give me the results I want?

Also, I think I should clarify that **ideally what I'm looking for here is to be able to basically "copy" my Ubuntu installation to an external hard drive in a fashion that, if I wanted to, I could boot/run it from the external drive, and then restore it to my internal after I restore Windows**.  So basically, I want to have it so I can boot to the external and test out and make sure everything "copied" correctly, before I wipe my internal drive to install Windows.

Could someone *please* respond?  Even if you can't answer me, if you could direct me to a forum where someone *could* answer my questions, I would be equally grateful.

Cheers,
NM

---

