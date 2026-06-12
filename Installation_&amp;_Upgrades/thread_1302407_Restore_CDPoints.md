---
title: "Restore CD/Points"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by FireStorm102389 on 2009-10-27
Is there a way to create a CD with all your prefferences saved on them so you can either:
a) Totally install your system back to normal with one CD install
-or-
b) Create a CD with all your settings on it where you can just upload when you are finished making the original ubuntu install

Cuz, i have had my linux for a while and im no good with a terminal, and if something happened to the video drivers I would like to know my personal data as far as themes, saved data and everything is fine if i wipe it out and redo everything, im mostly concerned with the settings that take so long to do, such as compiz, icons, and what not, files i copy to a thumb drive.

Or is there a way to create a restore point or something, because i know windows has restore discs they can use, anything like that for ubuntu 9.04?
I hope u all understand what im trying to get at :)

---

### Post by mr_steve on 2009-10-27
You can mostly accomplish this by backing up your home directory, as all of your user-specific settings will be stored in various hidden files and folders inside it.

Another alternative might be to use a tool like [Clonezilla]("http://clonezilla.sourceforge.net") to make an image of your entire hard drive once you have everything tweaked the way you want it. If something were to go wrong, you'd be able to restore to the point at which you made the image.

---

### Post by FireStorm102389 on 2009-10-27
ok, for the first option you're ssaying i can just basically copy all my files in my /home or /home/david folder? and then when i do a fresh install if it happens i can just overwrite those  files so that my stuff is all there? idk how i would go about doing that exactly cuz wouldn't some things not be installed or what not?...details please :/

and as far as the second option goes with the image file of my hard drive, how does that work? so i download that app and then make an .iso file of my entire hard drive and then if i do a fresh install i can put the .iso file of my hard drive i made in to install it or do i need to do a fresh install and then ?somehow? get that file to restore what i had all done?

---

### Post by mr_steve on 2009-10-27
> **FireStorm102389 said:**
> ok, for the first option you're ssaying i can just basically copy all my files in my /home or /home/david folder? and then when i do a fresh install if it happens i can just overwrite those  files so that my stuff is all there? idk how i would go about doing that exactly cuz wouldn't some things not be installed or what not?...details please :/

With backing up your /home/david folder, you would be able to restore all your personal settings. You would still need to re-install whatever apps you had installed before, but once you did, they would use the settings you restored from your backup.

> **FireStorm102389 said:**
> and as far as the second option goes with the image file of my hard drive, how does that work? so i download that app and then make an .iso file of my entire hard drive and then if i do a fresh install i can put the .iso file of my hard drive i made in to install it or do i need to do a fresh install and then ?somehow? get that file to restore what i had all done?

Clonezilla has a bootable CD which lets you copy your entire hard drive, and create an image much like what comes on a computer's factory restore discs. The image would probably be too big to fit on a single CD or DVD, but if you have another hard drive, or another computer on a network, you would be able to copy the image there. Then if you wanted to restore, you'd boot from the Clonezilla CD again, and copy the image back onto your hard drive. Sorry if that's kind of vague, but I haven't personally used Clonezilla yet. I've only used similar tools like Symantec Ghost, which is commercial software.

---

### Post by FireStorm102389 on 2009-10-27
What if i made the .iso of my hard drive with a DVD CD instead of a regular Blank CD?

---

### Post by mr_steve on 2009-10-27
> **FireStorm102389 said:**
> What if i made the .iso of my hard drive with a DVD CD instead of a regular Blank CD?

Well, it wouldn't actually be an ISO, rather some kind of Clonezilla-specific image format. But that aside, it just depends on how much space is used on your hard drive when you make the image. If you have less than 4.7GB of files, like maybe with a pretty fresh installation, it would fit on a DVD-R just fine.

---

### Post by oldos2er on 2009-10-27
Something else to consider is Remastersys: [http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

---

