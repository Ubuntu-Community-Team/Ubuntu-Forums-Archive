---
title: "Installation fail..."
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by headbuster on 2009-11-04
Today I installed windows and left some space to install Ubuntu. I started the install and when it reached 53% it told me there is an error and I have to clean the CD because it might be dirty or the cdrom lens or something... (wtf... absolutely clean disk)
I click OK and it boots from the cd?!?!?! then I restart and click Install again and it boots from the CD AGAIN but this time it wants username and password...I enter them but it doesn't accept them...
And now there's no way I can install ubuntu without formating the whole HD again...
What should I do?

---

### Post by padibona on 2009-11-04
I have this same problem, and am currently trying a couple things I will let you know if I get an answer for you.

---

### Post by coffeecat on 2009-11-04
The fact that the first time you booted from the CD it didn't prompt you for a username and password (the default behaviour), but that the next time you did does indeed suggest there is a problem with the CD, your optical drive, or perhaps the original downloaded ISO.

Do not ignore error messages - they are there for a purpose. They can only give a limited number of suggestions as to what is wrong and for you to react with 'wtf' disadvantages only you.

Suggest:
1 - check the md5sum of the ISO if you have not done so already.
2 - burn a new CD at a low speed.
3 - use a lens cleaner on the optical drive.
4 - select the disk check option in the live CD boot up menu (Can't remember what it's called).
5- try again with new CD.

Personally, I would not bother with a CD that is giving me that sort of trouble. I've had this sort of thing happen occasionally over the 4+ years I've been running and installing dozens of distros/versions. It's usually down to a dud CD - even brand new unused ones can be dud. CDs cost pence. My time is more valuable.

By the way, the CD is prompting you for the live CD username and password. It wouldn't know anything about the account you tried to set up in the failed install. For what it's worth the login details for the live CD are "ubuntu" and a blank password. But you shouldn't be seeing the login screen unless you do a logout from the live session. Almost certainly you have a bad CD.

---

### Post by padibona on 2009-11-04
Ok I did a disk check on bootup and there was an error with 1 file but it passed an MD5 checksum...is that because MD5 isn't 100% foolproof?

Hmm some weird behavior here...when the system time keeps changing is this typically a problem with a CMOS battery? It's all over the place.

Could this affect the installation by chance?

---

### Post by coffeecat on 2009-11-04
> **padibona said:**
> Ok I did a disk check on bootup and there was an error with 1 file but it passed an MD5 checksum...is that because MD5 isn't 100% foolproof?

Do you mean a md5sum on the downloaded ISO? If the ISO md5sum checks out then this means there wasn't a corruption during the download. This happens occasionally and you get an ISO from which you can burn a CD, but the filesystem on the CD will also be corrupted somewhere.

So if you mean that the ISO md5sum was OK but that you get an error on the disk check, then throw that disk away. Use another.

> **padibona said:**
> Hmm some weird behavior here...when the system time keeps changing is this typically a problem with a CMOS battery? It's all over the place.

A failing CMOS battery is the most likely. They don't cost much. Best to change it to be sure.

> **padibona said:**
> Could this affect the installation by chance?

To be honest, I don't know. I wouldn't have thought so. I would have thought it would simply give you wrong date/time stamps all over the place. Although this could affect you on rebooting. The system hates to find files it thinks are in the future. It throws a major wobbly and insists on doing a filesystem check. I've seen this occasionally when there's some confusion between system local time, GMT and British Summer Time in the installer. Immediately after an install during the first boot it finds that all the system files are dated 1 hour into the future. It doesn't like it. It doesn't like it at all. :)

---

### Post by padibona on 2009-11-04
Hmm using windows 7 and when I right click to burn ISO to disk (built in feature) it doesn't let me change the burn speed...any ideas?

---

### Post by coffeecat on 2009-11-04
> **padibona said:**
> Hmm using windows 7 and when I right click to burn ISO to disk (built in feature) it doesn't let me change the burn speed

Hmmph! Windows! Tch! :roll:

:wink:

Have a look at [http://infrarecorder.org/](http://infrarecorder.org/) . It's free. I've used it in XP and Vista. I don't know whether it will work in W7 but if it works in Vista, it ought to. If my memory is correct it allowed you to vary the burn speed.

Once you get Ubuntu up and running, you'll have some far superior burning apps to choose from. :p

---

### Post by headbuster on 2009-11-04
Wow I didn't expect so many answers!
So you are suggesting to try with a new CD and when it prompts me for user and pass when I click install I will provide ubuntu/blank and click the install shortcut on the desktop...
Am I right?
---
btw I am STILL waiting for my CD to come... why is it taking so long...

---

### Post by coffeecat on 2009-11-04
> **headbuster said:**
> So you are suggesting to try with a new CD and when it prompts me for user and pass when I click install I will provide ubuntu/blank and click the install shortcut on the desktop...
Am I wright?

Not quite! :wink:

Go through the checklist in my first post. A dud CD is the most likely, but you need to check the md5sum of the ISO, and possibly use a lens cleaner on the optical drive.

However, if a live CD prompts you for a username and password when it first boots up, this is not normal behaviour. This should only happen when you do a logout and login during a live session. Having said that, if you do get a login prompt from a new live CD and you've checked everything else, then proceed and try an install. Hopefully, you'll be luckier this time around.

If you do get the login screen, instead of entering "ubuntu" and no password, if you just leave it, it should autologin after 15 or 30 seconds - I can't remember which.

---

### Post by padibona on 2009-11-04
Ok here is what I had to do apparently CD quality blows chunks...I double checked the MD5 check sum and it was correct, so my ISO was legit. Instead of burning to a CD I just dragged and dropped the ISO to a flash drive that I know Ubuntu and Windows could read (FAT32). For whatever reason I could not get a CD to burn correctly with the 9.10 Ubuntu, but had a 9.04 version available that was fine. I installed 9.04 version. Copied the ISO from flash drive to Ubuntu desktop. Rebooted and then created a USB boot from /system/administration    its towards the bottom there. Make sure to use the ISO you just copied over to the Ubuntu desktop. Now that USB bootable is done, reboot and boot to the USB device and double check the disc for corruption using the built in function from the install menu. If fine, then install Ubuntu from USB.

Now I have another problem, I don't have wireless connection working, the function keys on my Dell D610 do not turn it on. I have the 4318 Broadcom wireless adapter, unfortunately my LAN/NIC card does not work so I cannot simply connect that way to get the correct driver. Anyone know a way to get this driver installed by maybe putting it on a flash drive or something?

---

### Post by headbuster on 2009-11-04
> **coffeecat said:**
> Not quite! :wink:

Go through the checklist in my first post. A dud CD is the most likely, but you need to check the md5sum of the ISO, and possibly use a lens cleaner on the optical drive.

However, if a live CD prompts you for a username and password when it first boots up, this is not normal behaviour. This should only happen when you do a logout and login during a live session. Having said that, if you do get a login prompt from a new live CD and you've checked everything else, then proceed and try an install. Hopefully, you'll be luckier this time around.

If you do get the login screen, instead of entering "ubuntu" and no password, if you just leave it, it should autologin after 15 or 30 seconds - I can't remember which.

So that's what I will do:

Burn a new CD (I suppose those errors are something common and I should not worry)
Check the CD for errors
click install
>> If I am prompted for a password I will wait and try the install
>> If not I will proceed the install as normal and format the broken drive

I hope it works well
Thanks

---

### Post by coffeecat on 2009-11-04
> **padibona said:**
> Now I have another problem, I don't have wireless connection working, the function keys on my Dell D610 do not turn it on. I have the 4318 Broadcom wireless adapter, unfortunately my LAN/NIC card does not work so I cannot simply connect that way to get the correct driver. Anyone know a way to get this driver installed by maybe putting it on a flash drive or something?

You need to start a separate thread in the [appropriate subforum]("http://ubuntuforums.org/forumdisplay.php?f=336"). People who could help, reading the thread title for this thread, won't know to drop in.

---

### Post by headbuster on 2009-11-05
Well I did everything I should do and it FAILED miserably again...
a disaster...:mad::mad::mad::mad::mad:
Why is it always happening to me? Can't a damn installation work from the first time... I've installed windows lots and lots and lots of times pirate versions on crapy disks original versions and it hasn't crashed even ONE time...one single time...
I have managed to install ubuntu only once from 15+ times
and it's not the disk

Well now I am waiting for my ORIGINAl disk to come. Which I ordered (the free one) and it hasn't come yet...

---

