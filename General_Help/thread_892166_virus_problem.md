---
title: "virus problem"
date: 2008-08-16
forum: General Help
---

### Post by rdpsycho on 2008-08-16
hello, i am trying to fix a friend's computer and theres a virus on it that seems to be replicating itself, and ive alrdy formated it twice but still recreates itself on the freshly formatted harddrive somehow, anyways, i was wondering if i installed ubuntu and then formated again and reinstalled windows if it would stop the virus. or else how do i clear it out?

---

### Post by CautionaryX on 2008-08-16
It sounds like that its actually on the MBR (Master Boot Record) of the hard drive. Installing Ubunutu might fix it, if GRUB overwrites the MBR but I really dont know for sure.

---

### Post by tamoneya on 2008-08-16
that wouldnt clear it anymore than just formatting.  You could try using something like DBAN but I doubt it will make much of a difference.  Are you positive this is a virus because it shouldnt be able to do that.  Also what have you done about your friends personal files.  Are you just copying them over to the new install because if you are that would be a very simple way for the virus to persist.

[http://www.dban.org/](http://www.dban.org/)

---

### Post by Cl0ud9 on 2008-08-16
Write zeros on the whole drive. Google should guide you to a program that will get the job done. But take warning that this will erase everything on the drive.

---

### Post by lisati on 2008-08-16
Your friend really needs to get a good antivirus system on his machine, keep it updated, and do regular scans.

Most of the reputable anti-virus companies also have tools that you can download that hunt down specific groups of viruses.

Be careful of Windows disks of the "don't ask too many questions where it came from" variety - I've encountered one or two which have malware on them.

I don't see any great advantage of installing *nix then replacing it with Windows - why not a dual-boot, with a Linux version of antivirus software on it that can scan the Windows partition?

---

### Post by Twitch6000 on 2008-08-16
You could use Boot N Nuke to clear the drive.

Then install ubuntu and use an anti virus to double check before reinstalling windows.
I suggest AVG or Clanvm.

---

### Post by jimv on 2008-08-16
Two questions:

1.  How does he know he has a virus?
2.  What virus is it?

---

### Post by rdpsycho on 2008-08-16
is it possible for a virus to create its own secret partition? because i think the hard drive is suppose to be 40 gb per the dell website, but its only 30 gb in windows setup formatter. 

i know there is a virus because after format and reinstall, there is 2 seperate boot options, if i edit the file one of the options ends in ".0" . so i looked at the c drive and saw that their are 2 windows directories, one is named "WINDOWS.0" and the other just "WINDOWS"

p.s. i did not backup ANY files, so there is no way that "I" am copying the virus. It must be on the Master Boot Record, or else its own secret partition.

p.s.s. this copy of windows is 100 percent clean, i have used it several times w/ zero problems

---

### Post by tamoneya on 2008-08-16
well use dban then.  It will destroy EVERYTHING.

---

### Post by rdpsycho on 2008-08-16
ok after my 3rd format it is now gone or appears to be, i hate windows, i personally use ubuntu.

---

### Post by mb_webguy on 2008-08-17
Me too.  I used to scrub my hard drive and reinstall everything once a year or so to remove any lingering malware and registry errors.  

Ubuntu has no viruses and no registry, and if I didn't tend to break things while fiddling with the system, I could just let it run forever without feeling like I needed to do anything to it.

---

### Post by tamoneya on 2008-08-17
> **mb_webguy said:**
> Me too.  I used to scrub my hard drive and reinstall everything once a year or so to remove any lingering malware and registry errors.  

Ubuntu has no viruses and no registry, and if I didn't tend to break things while fiddling with the system, I could just let it run forever without feeling like I needed to do anything to it.

I used to do it every 6 months with windows.  Once during the summer and once during winter break.

---

### Post by colobix on 2008-08-17
I couldn't b more agree. Windows is a big pain with bugs.
Good you got rid of the virus btw.
You should tell your friend to changed to Linux so it does not happend again.
More viruses like that and when you have to format everything can kill the disks.
And another thing is that your friends private data will be gone forever.

No, no, no... Windows is painfull, so thank god for Ubuntu.

:)

Stay virus free, use Linux

---

### Post by rdpsycho on 2008-08-17
hah i will never tell anyone to install linux ever again unless they have done so before, such a pain in the butt when noobs have your phone number...

---

### Post by doas777 on 2008-08-17
> **rdpsycho said:**
> hah i will never tell anyone to install linux ever again unless they have done so before, such a pain in the butt when noobs have your phone number...

no doubt.

this is just a thought, but if your windows install disk doesn't have a shiny hologram on it, you might look for you're culprit there. make sure your actually formatting the drive (quick format won;t do it) and if the malware is storing itself in ADS, then you may want to format the drive with fat32, and then reformat as ntfs. it's probably unneeded, but I have no idea what a format does to a ADS. 

good luck

---

