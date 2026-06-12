---
title: "Clean Ubuntu Install/Upgrade"
date: 2009-04-17
forum: Installation &amp; Upgrades
---

### Post by EmyrB on 2009-04-17
Hi All,

I have been an Ubuntu user since 5.10 and whenever a new version came out, I always forced an upgrade through the command line. I have never had any major issues by doing this, but lately 8.10 seems to have a few niggles.

Over the past 3 years my hardware has also undergone some changes and Ubuntu has handled them without batting an eyelid. So, as 9.04 is around the corner, I have decided to take the plunge and install a fresh clean Ubuntu. I have some questions regarding this: -

1. When I first installed Ubuntu I only had 512MB and I used a 512MB swap file. I now have 8GB installed so do I need a swap file, if so how much should I use?

2. My e-mail client of choice is Thunderbird and over the last 3 years I have amassed a good number of contacts. How to I export my complete Thunderbird profile?

Those are my two biggest questions really.

Cheers in advance

EmyrB

---

### Post by Therion on 2009-04-17
> **EmyrB said:**
> 1. When I first installed Ubuntu I only had 512MB and I used a 512MB swap file. I now have 8GB installed so do I need a swap file, if so how much should I use?
A default install will give you a 2GB swap file.  I've never bothered to change it but if you want to manually partition the swap-partition you can.  Unless your tight for HDD space I'd just leave it at the default.  Opinions vary.  YMMV, et al.

> **EmyrB said:**
> 2. My e-mail client of choice is Thunderbird and over the last 3 years I have amassed a good number of contacts. How to I export my complete Thunderbird profile?
Cakewalk...  See this link for a walkthrough:

[http://www.freeemailtutorials.com/mozillaThunderbird/exportAddressBooks.cwd](http://www.freeemailtutorials.com/mozillaThunderbird/exportAddressBooks.cwd)

---

### Post by phasenew on 2009-04-17
> **Therion said:**
> A default install will give you a 2GB swap file.  I've never bothered to change it but if you want to manually partition the swap-partition you can.  Unless your tight for HDD space I'd just leave it at the default.  Opinions vary.  YMMV, et al.


Cakewalk...  See this link for a walkthrough:

[http://www.freeemailtutorials.com/mozillaThunderbird/exportAddressBooks.cwd](http://www.freeemailtutorials.com/mozillaThunderbird/exportAddressBooks.cwd)
For thunderbird profile: why not just copy the whole profile folder .mozilla_thunderbird to the new place?

---

### Post by EmyrB on 2009-04-17
> **phasenew said:**
> For thunderbird profile: why not just copy the whole profile folder .mozilla_thunderbird to the new place?

Hmmm... not sure if this will work just copying it and then pasting it back, I seem to remember that when doing the same on Windows you had to run a utility to finish the process. Not sure if it is the same with Linux though. I have looked on the net, but all I can see is tutorials on how to do it with Outlook Express (yeuch).

> **Therion said:**
> A default install will give you a 2GB swap file.

Does it!? Wow I had no idea. So it is best to go with 2GB even with 8GB of memory and a 64-bit install?

> **Therion said:**
> Cakewalk...

I shall have a look at that tutorial, thanks :)

---

### Post by Therion on 2009-04-17
> **EmyrB said:**
> Does it!? Wow I had no idea. So it is best to go with 2GB even with 8GB of memory and a 64-bit install?
I don't know if that's the "best" course of action or not... It's the simplest, and I like simple.  And yes, if memory serves me correct, it's 2GB swap partition by default -- but don't quote me on that.  

Are you wanting to install without a swap partition at all since you have so much RAM?  I believe you can do it if you don't mind setting up all your partitions manually during the install.  Personally I just let the installer do it's thing and then, if I want to adjust partitions, use a gParted LiveCD to adjust things as I need.  But that's me.  Then too, if I was sweating losing 2GB on my primary drive to the swap partition I'd simply install a bigger hard drive.

---

### Post by fballem on 2009-04-17
Some thoughts:

1/ Regarding Swap file, I also have 8 Gig of RAM. I have a 500Gig hard drive. Others have recommended a swap file of 2 Gig, and that has been working very well for me. I have been running 9.04 Beta. I believe that the default for the main partition is to use ext3. If you want to use ext4 instead, then you have to do a manual partition. When you first get to the manual partition screen, make a note of the size of the swap file, then delete both partitions. Specify the Swap file first (it should show up as sda5 or something similar). Use the rest for your primary partition, specify the ext4 as the format, and / as the mount point. You should be good to go.

2/ Thunderbird migration. If you have an external device, like a large USB drive, then open up your home folder in Nautilus, show the hidden files (Ctrl-H). Locate the .mozilla-thunderbird folder and go to it.

Copy the file named abook to your external drive (that's your address book). Then go into mail and local. Copy the files in the local folder to a folder on your external drive.

After installation of ubuntu, including Thunderbird, start Thunderbird and set up one of your e-mail accounts - make sure that you do not do a send and receive at this time! This will initialize the folder structure on your re-installed machine.

Open Nautilus, show the hidden files (Ctrl-H) and locate .mozilla_thunderbird folder.

Replace that abook file with the one that you copied originally.

Go to mail and local. Delete the files in the local folder and replace them with the ones that you copied originally.

When you are done, start Thunderbird and your folders and contacts should be there. You are then good to go. If you have multiple e-mail accounts, then configure the rest.

Hope this helps,

---

### Post by EmyrB on 2009-04-18
Well thanks for the help guys. As I will be creating my partitions manually, I will give my self a 2gb swap. As for thunderbird, poking around mozilla.com I found [this.]("http://www.mozilla.org/support/thunderbird/profile")

I have another question about ext4. I have read quite a bit about data loss and such, yet I have been testing it out on Jaunty quite a bit and I have not experienced any data loss. I was going to format my /home with ext4 and leave my "/" as ext3, should I go with ext4 or stick with ext3?

---

### Post by Interceptor125 on 2009-05-25
Hi All,
I have 8.10 installed in my system and it also has Windows XP in dual boot option. What would be the best installation option which i can take 
 
1. Clean Install
2. Upgrade 8.10
 
I am currently downloading the AMD64 full installation ISO image and can i use this to perform an upgrade. I upgrade guide suggest usage of alternate ISO image... Doesnt the full install image has the files which are present in a Alternate ISO image?

---

