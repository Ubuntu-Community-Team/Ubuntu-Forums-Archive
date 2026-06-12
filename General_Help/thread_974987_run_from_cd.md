---
title: "run from cd"
date: 2008-11-08
forum: General Help
---

### Post by stealthc on 2008-11-08
what is the password to gain root access from terminal for ubuntu install disk when running it from the cd without installing on computer?

I did this because my install disk is corrupt, it won't let me install properly on my hard drive.  So I've downloaded a new install disk but could not open my cdrom
had to use eject /dev/cdrom from the terminal
put in a blank disk
won't let me burn I get an i/o error
won't let me mount
tried "mount -a"
detects the blank disk after but still get i/o error.
tried burning from the terminal but that doesn't seem to work either.
Any help would be appreciated as I don't want to wait till late tomorrow for my boyfriend to bring his laptop over just so I can burn a friggin install disc.

I did however install the server software properly, perhaps this can be done from the command line there?

any help would be appreciated so that I can get this done easily without having to go surfing around to gain every little inch towards my goal.

---

### Post by stealthc on 2008-11-08
it isn't saving the file to the hard drive, because nothing F**king mounts from the live cd.

---

### Post by stealthc on 2008-11-08
bump

---

### Post by stealthc on 2008-11-08
what an aggrivating issue, I'm going to file a bug report, ubuntu should include a utility within the live cd in order to download updated version and install, as an alternative to using the install icon on the desktop.

Nevermind that, there should be a live download and install version that is ultra lite, right on every cd.  If a file is found to be corrupt on the cd, that should be immediately offered so this (and other similar issues) never occur.  What a friggin pain this is.  Nevermind what I've already had to go through trying to figure out how to install xp on this usb drive (or vista, I'd be happy with either even though microcrap doesn't think people's hard drives will die and that they'll have an external drive to keep things running till the warranty sends 'em something back that works).

---

### Post by ad_267 on 2008-11-08
To run a command as root in the terminal you put sudo in front of the command, there is no password in the live CD. You can run "sudo -i" to get a root login. I think if the CD is corrupt there's not much you can do other than burn a new CD. And as you've found that probably won't work from the live CD if the CD is corrupt.

What do you mean you installed server software? Did you manage to install some server applications in the live CD, or did you install the Ubuntu server edition? You can install the Ubuntu desktop on the server version.

---

### Post by TeXtonyx on 2008-11-08
I am not sure I understand all your issues. 
[url]http://www.howtoforge.com [make into one line and paste into browser]
/how-to-upgrade-ubuntu-8.04-to-ubuntu-8.10-desktop-and-server

That is how it normally works. If your cd is corrupt then you don't
know if any utility on the cd will work. Somebody burned the cd you 
are using. The downloaded file should be checked for errors before 
it is burned. Then the cd itself it verified for no burn errors. 
And since cds don't work if they get scratched, burn a backup. If a 
user doesn't have a backup the consequences are always user error.

I had about 10 disasters before I learned to follow the advance that
_they_ constantly give and make a backup in and for any situation.

---

### Post by stealthc on 2008-11-08
well that certainly is annoying cause I like to use the su command so I don't have to do that every friggin line.

Aside from that, my issue has evolved now:
now I am trying to burn the ubuntu iso to a dvd from ubuntu server.

I was thinking I gotta download the cdrecord rpm if I can find it, try to figure out how to get it on the hard drive sorta like I got the iso on there (I dragged and dropped it right from the get-go and that seemed to work regardless if the hard drive was mounted), so I'm gunna do the same, then figure out how to install the rpm from command line (thinking sudo install cdrecord-blah-blah.rpm but I'm sure that'll be a pain too till I figure it out).
then once installed I should be-able to burn it to disk unless the poor crippled server software has issues with the dvd writer and it's drivers or something else..... meh
what a friggin pain!!!

---

### Post by stealthc on 2008-11-08
I started drinking earlier I may as well do that till I pass out and then try to fix it in the morning (or early afternoon probably) and if not get my boyfriend to bring his laptop cuz he wants money from me.... so maybe I'll do that as a last resort and make him bring his laptop, redownload ubuntu since it won't let me access the network from the live cd even though I could with my previous install and copy the file to the windows xp computer here... woulda saved a few minutes with that one....
ugh
WTF.  How on earth could nobody have ran into this issue before considering they put in a cd integrity check?  There had to be a reason for that---so why nobody have this problem yet?

---

### Post by stealthc on 2008-11-08
> **TeXtonyx said:**
> I am not sure I understand all your issues. 
[url]http://www.howtoforge.com [make into one line and paste into browser]
/how-to-upgrade-ubuntu-8.04-to-ubuntu-8.10-desktop-and-server

That is how it normally works. If your cd is corrupt then you don't
know if any utility on the cd will work. Somebody burned the cd you 
are using. The downloaded file should be checked for errors before 
it is burned. Then the cd itself it verified for no burn errors. 
And since cds don't work if they get scratched, burn a backup. If a 
user doesn't have a backup the consequences are always user error.

I had about 10 disasters before I learned to follow the advance that
_they_ constantly give and make a backup in and for any situation.

who the heck wastes their time checking a file for errors whenever they download something??? LMAO.... I don't have that much time, and I have yet to encounter a computer issue I can't lick even though it mean hours of banging my head sometimes....

---

### Post by stealthc on 2008-11-08
oh and normal backups wouldn't have worked, not with the errors I was experiencing with my partition table.... everything had to go cuz of that, otherwise I'd never ever be-able to consider putting windows xp on this drive, and I'd never be-able to run the software I wanted to cuz wine runs like crap for a fair amount of things....

some things just rule out using linux.

although what I want to do, since windows won't install on a usb drive, is perhaps trying to figure out installing it in vmware with ubuntu loaded on, then reload the boot stap for ubuntu on here, then run it in ubuntu through vmware...

but I dunno if windows will still have an issue with it being a usb drive or not... and if it does then I have to unpack the iso image of my install disk, then modify a few files, repack, reburn, retry the install, and if that don't work, I'm waiting several weeks for my replacement drive to come in the mail from asus for my g1s.

---

### Post by SPr on 2008-11-08
Deleted my unhelpful post. Mods, please remove this. Thank you.

---

### Post by stealthc on 2008-11-08
ugh they should at least have flash on the live cd, so much of the web uses the flash client, I never even noticed entirely till now.

---

### Post by TeXtonyx on 2008-11-08
> **stealthc said:**
> ugh they should at least have flash on the live cd, so much of the web uses the flash client, I never even noticed entirely till now.

You seem to have a bright future as an Ubuntu developer when you
have credentials like "and I have yet to encounter a computer issue
I can't lick..." Everybody knows how well paid they are! You could
also showcase your talents as a politician with your influential use 
of facts, or raise comedy to a ground breaking level of appreciation.  :popcorn:

---

### Post by stealthc on 2008-11-08
yeah I wish I got paid just as much as an ubuntu developer, lol I could look like a starving ethiopian.

---

### Post by stealthc on 2008-11-08
Well some more updates:
The idea with using cdrecord was a blunder.
I found a site to download rpm packages of cd record and converted them to a deb file using alien.
This part worked, and cdrecord was installed on ubuntu server.
It did not however record the iso properly even though it looked like it did.
it wouldn't work till I specified dev=0,0,0 and -dao and set the speed=4 parameters.
the disc booted, got into the initial menu, but crashed whenever i tried a disk check or running the live cd.

So I used the old disk to boot into live cd, ran the install app, and swapped the disks using "eject /dev/cdrom" in the terminal.
the disk failed the checks (but perhaps the -pad -v options were bad, or perhaps the whole idea was doomed to fail anyways).

So I went digging and found an ubuntu install disk in a dvd case, the only burned disk that wasn't sitting in my spindle and the only one I didn't try.  It was scratched I didn't think it would work but gave it a try anyways.

Bingo.

Working ubuntu install.

So now I'm going to install vmware and see if it can help me get windows xp on.

---

