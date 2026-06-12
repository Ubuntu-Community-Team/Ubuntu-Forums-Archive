---
title: "Help mighty Ubuntu gods"
date: 2012-02-02
forum: Hardware
---

### Post by Marzr83 on 2012-02-02
I have a compaq laptop with widows 7 on it, something happened and my bootmgr is gone. I asked the best buy guys and they said all my docs, music, movies, and pics are still there but i needed to restore to factory settings thus losing my stuff. Here's my question can i use ubuntu or any other linux to boot up and back them up on a external disk?

---

### Post by nothingspecial on 2012-02-02
Well you can try at least.

It should be possible.

Boot a live cd or Usb and run the file browser. See if you can see your files.

---

### Post by Marzr83 on 2012-02-02
For the live cd do i need to change the boot order so it sees tue disk drive first?

---

### Post by nothingspecial on 2012-02-02
Yes you would need to do that.

---

### Post by Marzr83 on 2012-02-11
I've gotten a LiveCD of ubuntu and its up and running, but I can't seem to find the files. Are those files hidden or did the guy from Best Buy lie to me to try and get me to pay for things i don't need

---

### Post by ahallubuntu on 2012-02-12
I don't know what happened to your hard drive.  If it completely failed, you will not be able to get your files/documents/pictures off yourself.  But if the bootmanager file is simply corrupt as you suggest, then the Best Buy guy may be right: it may all still be there.

If what was the C: partition filesystem is still intact, then you should be able to find it with a Ubuntu CD.  I'm not sure which version of Ubuntu you are using - the desktop managers have changed in the last few versions.  The latest, 11.10 uses the Unity desktop manager, with which I am not yet that familiar.  But, after booting the CD, you want to find "Places" and look for all the possible devices you can mount.  The name may not be familiar - it may not say C: or Windows, but it could be a garbled-looking name.  Do some poking around in Places, via trial and error.

It's also possible the filesystem is damaged and you would have a shot at recovering your files but you might have to use a file recovery program.  In Windows, I use Recuva for that; you could remove the hard drive and attach it to another computer to do that (even another laptop if you get a USB hard drive enclosure or adapter).  I'm not familiar with Ubuntu-based file recovery programs that work for Windows files, but such programs may exist.

---

### Post by Marzr83 on 2012-02-12
i'm using Version 11.10, and I can see the hard drive and folders. The best buy guy told me that windows 7 was erased and they could back it up for $130, and then they would charge me for recovering the computer to factory settings.

---

### Post by ahallubuntu on 2012-02-12
OK.  So now you can plug in an external hard drive and copy the files/folders you want over to it.  You saved some money, eh?

You should probably test the hard drive before doing any sort of factory restore.  Linux has a thing called GSmartControl to test the S.M.A.R.T. status of the drive.  (S.M.A.R.T. is built-in self-monitoring/testing available in most hard drives.)  If it is failing, don't even bother trying to do a factory restore on it - better to replace the drive.

If you now know how to burn the Ubuntu image ISO file to a CD, you can try another one: google the Ultimate Boot CD and burn/boot that.  Then choose Parted Magic from the menu.  Follow it through the menus...and eventually you'll get a desktop with some icons.  Click on the one that says SmartControl, and you can look at the S.M.A.R.T. Attributes for the drive.  If any of them show up highlighted in pink/red, they are issues with the drive.  If not, you probably just had a corruption.

You could actually do your own factory restore of Windows 7 if you want, too.  You can even download legit copies a Windows 7 install DVD, though you'll need the COA sticker product key from your computer to activate it.  There may be better ways to do it.

---

### Post by Marzr83 on 2012-02-12
I have the recovery disks. so I was going to do it that way. I'm actually using the laptop with ubuntu right now, I can see the folders but they don't anything in them that's the problem.

---

### Post by savanna on 2012-02-12
Boot off a live distro like Knoppix.

The hard drive should be mounted automatically.

Copy all the files from the Windows hard drive to a USB key.

---

### Post by Marzr83 on 2012-02-13
I can see the hard drive, the files arent there but the folders are. And the best buy guy told me they could recover them. If they're there why can't i see them

---

