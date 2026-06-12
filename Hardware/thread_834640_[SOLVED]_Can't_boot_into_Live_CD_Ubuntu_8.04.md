---
title: "[SOLVED] Can't boot into Live CD Ubuntu 8.04"
date: 2008-06-19
forum: Hardware
---

### Post by Beowulf.1000 on 2008-06-19
No joy trying to boot into Ubuntu 8.04 live cd on my new Toshiba Satellite A305-S6843  I get the same error issues as in this thread:
[http://ubuntuforums.org/showthread.php?t=832299&highlight=Toshiba+Satellite+A305](http://ubuntuforums.org/showthread.php?t=832299&highlight=Toshiba+Satellite+A305)

I tried disabling the LAN nic in the BIOS, made no difference. 

I am open to suggestions-- even trying a different distro, anything to get linux with GUI on this laptop PC. I prefer Ubuntu, but if another distro would work so be it. I am also downloading Xubuntu, thought I would give that a shot.

Am I out of luck, should I just wait for the next release of Ubuntu in October 2008 and see if that kernel recognizes my laptop hardware?

---

### Post by phidia on 2008-06-19
There are kernel boot argument you can type at the boot prompt to see if that will allow you to complete the boot process. You can try > acpi=off or > noapic. I am not an expert at boot arguments and I wish there was a easy to access list of them available.
There is a thread on using noapic [here]("http://ubuntuforums.org/showthread.php?t=334083").

---

### Post by Beowulf.1000 on 2008-06-20
> **phidia said:**
> There are kernel boot argument you can type at the boot prompt to see if that will allow you to complete the boot process. You can try  or . I am not an expert at boot arguments and I wish there was a easy to access list of them available.
There is a thread on using noapic [here]("http://ubuntuforums.org/showthread.php?t=334083").

Success! :guitar: I am typing this reply from the Toshiba Satellite A305-S6843 with Wifi (802.11N, yup, the newer N wifi). I disabled the LAN (nic) in the BIOS, per another post, I will reactivate the onboard LAN and see what happens. But I am typing this from the Live CD (Ubuntu 8.04 x86 Desktop iso). 

What I did was boot the live CD, press F6 to add boot options, then I manuallly added "noapic" (without quotes) on the boot parameters line just before the "splash" near the end of that line.

I am hopeful that I can now install Ubuntu to this laptop. I will have to decide to totally trash VISTA, I am not going to try putting both on the one system. I tried that with the smaller subnotebook version of this laptop, and VISTA refused to boot even though Grub booted. So I guess it is Ubuntu all the way or no way.  Off topic a bit-- the reason I sort of decided I needed MS VISTA was the screenwriting software I was using, Movie Magic (does not work with Wine, heavy antipiracy in Movie Magic). I found some nice macro scripts for OpenOffice for screenwriting, so I might just go that route, or Celtx, or Sophocles, all linux compatible; although I discovered Celtx for linux did not import files, but Celtx for MS Windows runs great in Ubuntu using Wine install.

---

### Post by Beowulf.1000 on 2008-06-20
Added note (all from off Live CD boot): Audio works! Harman / Kardon speaker system on laptop works. USB flashmemory stick detection works -- I plugged in my 8GB flashstick and it appeared as an icon on the Desktop, I was able to open and view folders and files. N wifi works. LAN (wired internet) does not work, but that is not a big deal since I use wifi pretty much exclusively now; I can wait for the drivers in a future kernel or version of Ubuntu. Video works great. Able to play .ogg sample video. I am amazed I have both N wifi, video, and multimedia audio; no hassles, works automagically off the live CD (as long as I add that "noapic" boot parameter.

I can't play mp3 yet, will need to install codecs for that once I install Ubuntu to the hard drive. Not a big deal.

---

### Post by Beowulf.1000 on 2008-06-20
More info, very interesting and useful: I downloaded and burned an XUbuntu Live CD, the desktop i386 version of xubuntu. Xubuntu live CD boots just fine, without any need to alter the boot parameters like I had to do with Ubuntu. N wifi, GUI, ogg music, USB flashmemory stick detected, all with Xubuntu.

---

### Post by phidia on 2008-06-20
Glad you got it working-good to hear! :) 

There is an [ubuntu laptop testing wiki]("https://wiki.ubuntu.com/LaptopTestingTeam") if you feel like contributing or sharing your experiances there I'm sure it would be helpful for other users, and that site could be more exploited/advertised too.

---

### Post by ktechman on 2008-08-18
Beowulf.1000, how did you accomplish wireless, I have LAN working?  Also do you have the Function keys working?  

  Thank you for your reply, Ktechman

---

