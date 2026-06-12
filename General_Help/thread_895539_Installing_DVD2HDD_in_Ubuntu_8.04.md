---
title: "Installing DVD2HDD in Ubuntu 8.04"
date: 2008-08-20
forum: General Help
---

### Post by spazsui on 2008-08-20
Hey guys, maybe someone can help me on this one.  I've installed DVD2HDD 0.2-12 on every ubuntu version since Dapper.  Recently I tried to install it on hardy but when I go to use the program it says that there is nothing in my bin file so the program won't open.  Never had that problem on any other ubuntu version so I was wondering if there is something I can do to fix that.  Sorry if I am missing something obvious here.  That's why I come to the forums.  Thanks for any help you can give.

---

### Post by mikeuhlik on 2009-01-24
It looks like I was not built for ubuntu 8.10 for higher the /usr/bin/dvd2hdd.gambas file dose not look like I launches gambas2 but the first on and I thinks the new ubuntu 8.10 and up use gambas2 but I am not that sure still looking for a fix my self. I have tried so many ways to to burn a dvd successfully and have not been able to I thought this little tool would do the job and I cant get it to work I have the same problem.

I did find some link that might help you burn dvds.

It to bad there is not a software for ubuntu thats like DVD Decrypter, and AnyDVD for linux I would have thought some one would have made one by now because all the dvd rippers for ubuntu are worthless until there is a DVD Decrypter that works in ubuntu.

Here are some link to guides I found that might help.

Ubuntu Linux DVD Shrink, DVD Decrypter Guide

[http://www.mrbass.org/linux/ubuntu/dvdshrink/]("http://www.mrbass.org/linux/ubuntu/dvdshrink/")

Restricted Formats Ripping DVDs

[https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs")

DVD2HDD - the DVDDecrypter for Linux (0.3-0 out. test it with your distro)

[http://forum.doom9.org/archive/index.php/t-115787.html]("http://forum.doom9.org/archive/index.php/t-115787.html")

DVDShrink Guide

[http://www.mrbass.org/dvdshrink/]("http://www.mrbass.org/dvdshrink/")

DVDShrink Preferences

[http://www.mrbass.org/dvdshrink/advanced/]("http://www.mrbass.org/dvdshrink/advanced/")

DVD Ripping DVDDecrypter, DVD43

[http://www.mrbass.org/dvdrip/]("http://www.mrbass.org/dvdrip/")

10 DVD Newbie Tips

[http://www.mrbass.org/dvdnewbie/]("http://www.mrbass.org/dvdnewbie/")

AnyDVD for Linux?

[http://club.cdfreaks.com/f88/anydvd-linux-150096/]("http://club.cdfreaks.com/f88/anydvd-linux-150096/")

making copies of encrypted DVDs

[http://ubuntuforums.org/archive/index.php/t-153706.html]("http://ubuntuforums.org/archive/index.php/t-153706.html")

Want to run RipIt4Me? Here's how...

[http://www.linuxquestions.org/questions/linux-desktop-74/want-to-run-ripit4me-heres-how...-516253/]("http://www.linuxquestions.org/questions/linux-desktop-74/want-to-run-ripit4me-heres-how...-516253/")

Here is a list of dvd Ripping and DVD Decrypter software.
Windows

DVD Shrink 3.2

[http://www.softpedia.com/progDownload/DVD-Shrink-Download-4128.html]("http://www.softpedia.com/progDownload/DVD-Shrink-Download-4128.html")
	
DVD43 4.4.0

[http://www.softpedia.com/progDownload/DVD43-Download-13878.html]("http://www.softpedia.com/progDownload/DVD43-Download-13878.html")

RipIt4Me

[http://www.softpedia.com/progDownload/RipIt4Me-Download-44816.html]("http://www.softpedia.com/progDownload/RipIt4Me-Download-44816.html")

AnyDVD 6.5.1.9 Beta / 6.5.1.8

[http://www.softpedia.com/progDownload/AnyDVD-Download-6612.html]("http://www.softpedia.com/progDownload/AnyDVD-Download-6612.html")

Free DVD 1.0
[http://www.softpedia.com/progDownload/Free-DVD-Download-23188.html]("http://www.softpedia.com/progDownload/Free-DVD-Download-23188.html")

DVD2HDD 0.2-10

[http://linux.softpedia.com/progDownload/DVD2HDD-Download-17412.html]("http://linux.softpedia.com/progDownload/DVD2HDD-Download-17412.html")

[http://home.arcor.de/amsoft-linux-department/dvd2hdd.html]("http://home.arcor.de/amsoft-linux-department/dvd2hdd.html")

DVDDecrypter 3.5.4.0

[http://www.mrbass.org/dvdrip/SetupDVDDecrypter_3.5.4.0.exe]("http://www.mrbass.org/dvdrip/SetupDVDDecrypter_3.5.4.0.exe")

P.S. There are a lot of was to accomplish this on you windows software in wine or use windows software in virtualbox other wise I don't think there is a way to fully do it with any windows software I know of. dvd2hdd is suppose to be the DVDDecrypter for linux but it is unreliable.

So I  wish you the best luck and hope one of these solutions work I have not tested them all and I am still trying them till I can find a good solution to get this perfect I will post the one that work best if you found it please post here thanks.
:p

---

### Post by Rob-e on 2009-01-24
another program is handbrake ( [http://handbrake.fr/](http://handbrake.fr/) ) it rips dvds to a video file, i prefer the command live version, but theres also a gui

if you download the cli version the command to rip a dvd is:
./HandBrakeCLI -i /media/cdrom0 -o /home/*yourname*/myvideo.mp4

it can also rip from a folder on the HDD (replace /media/cdrom0 with the path)

---

### Post by mikeuhlik on 2009-01-25
Ya but handbrake dose not Decrypt the protection on dvds that make it not able to burn or rip them thats why all these rippers are worthless unless you have a good Decrypt to clean all the junk they put to block you from ripping it and there is no good Decrypter for linux yet except DVD2HDD which is like DVD Decrypter for windows but not stable yet 

Anydvd, Freedvd, Dvd Decrypter are the only good ones out there after Decrypting the dvd you can use a ripper then burn it.

I am testing a full solution for decrypting & ripping dvds in ubuntu now.

The solutions seams to be using wine with Dvdshrink, Dvd Decrypter, RipIt4Me, Freedvd, & k3b.

I will also test to see if you can use k9copy after decrypting the dvd first.

---

