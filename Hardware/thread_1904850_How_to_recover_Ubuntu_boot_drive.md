---
title: "How to recover Ubuntu boot drive"
date: 2012-01-05
forum: Hardware
---

### Post by Narzugon on 2012-01-05
I have a home file server that I slapped together out of spare parts and the boot drive has failed. If possible I would like to recover to another drive with the OS in tact. All of my important data is on another drive so it's not a huge deal. The only thing I would gain by recovering this drive is the experience and not having to install and reconfigure everything again. I'm a novice Ubuntu/Linux user so I've done a fair amount of reading to get as far as I have. But I feel that I'm really taking stabs in the dark.

Symptoms: No clanking but the disk utility reports: Disk Failure is Imminent - ID 5 Reallocated Sector Count Assesment "Failing" 117-117-140-663 sectors.

Drive setup is this:

40gig /dev/sdf
Partitions: 255mb ext2
40gb Extended
40gb LVM2 Physical Volume

Multi Disks Devices:
38gb LVM2 ext4(v1.0) Extent Size 4.0 MiB (4,194,304 bytes) Capacity 40gb (39,757,807,616 bytes) /dev/dm-0
1.7gb Swap

Here's what I've done thus far. Using another Ubuntu computer (11.04 Natty Narwhal) I created an image of the failing drive (we'll call it "sdf" from now on) using the older ddrescue. None of the partitions were mounted or active in Disk Utility. Loaded that image to a new drive ("sdn") and attempted to boot and or read. It wouldn't boot and the only partition I could mount and read was the filesystem partition - 255mb ext2. The other partitions were there although the LVM2 partition didn't show up under the Multi Disks Devices.

After more reading found the GNU-ddrescue. Performed the same steps and created a second image. Then created a third image using successive passes. Tried those on my new drive with the same results. I just connected sdf again to get the details for this post and found that I can start the LVM partition (dm-0) and browse the files. 

So it sounds as if everything is there, I'm just missing something. Any help would be greatly appreciated.

---

### Post by Paddy Landau on 2012-01-06
I see no one has answered you, so here is my answer.

I think you'll find that reinstalling probably would have been quicker :)

It takes very little time to install a program and all the updates (unless you do not have broadband).

When you configure your desktop, *all* the settings are stored in your /home/username folder (unlike in Windows, which uses the Registry), using your actual user name instead of *username*. Therefore, for future note, if you back up your entire /home/username folder including hidden files and folders, you will get your settings back just by restoring that folder.

However, many people, me included, don't bother with that because it's so easy to reinstall and reconfigure Ubuntu.

If you wish to back up your entire disk to be able to restore it intact, look at a ghosting program such as [CloneZilla]("http://www.clonezilla.org/").

---

### Post by Narzugon on 2012-01-06
I agree. It would have been quicker. Coming from the Win world in this type of situation I normally Ghost the drive and in most cases if the drive isn't too far gone, I can either boot the system and Win will straighten things out (imagine that) or worse case I do a repair install of the OS which keeps apps and data in tact. I was thinking I could clone the drive, learn a few things in the process and move on. As with anything, if you know what you're doing it helps. :)

My main concerns were  my video and wifi. I had a heck of a time getting those working correctly and had just spent a lot of time setting up and configuring a few other programs.  But I do have the Home folder now and those program's config files are there so not much if anything lost.

Thanks for the replay and the info Paddy!

---

### Post by Paddy Landau on 2012-01-06
> **Narzugon said:**
> My main concerns were  my video and wifi.
Ah, that could be a different kettle of fish.

11.10 obviously has updated drivers, so hold thumbs that they work.

I always make notes of how I get something to work, so that if a new release doesn't work, I can refer back to the notes.

System-wide settings are not held in your home folder (because they are applicable to everyone), but there is no simple place to back up for those.

If the video and wifi do not work with the new installation, perhaps you can refer to your old posts on the forum (assuming that you found the solution here)?

---

