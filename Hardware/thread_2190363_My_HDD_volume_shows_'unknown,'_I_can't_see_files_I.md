---
title: "My HDD volume shows 'unknown,' I can't see files I've moved previously."
date: 2013-11-27
forum: Hardware
---

### Post by Mynxenoa on 2013-11-27
[COLOR=#000000][FONT=Segoe UI]Everytime that I plug in my external WD HDD it asks me to format the drive on Windows. I know that there is plenty of data on this drive and formatting the drive will cause the data to be erased on Windows, and that will not do me any good.


[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]I was hoping there is a way to view the files and possibly get them to be viewed on Windows or even linux and moved elsewhere correctly. I have some experience with linux (Ubuntu) and plenty with Windows. I'm not sure what options I have but I would appreciate if anyone can give me some feedback. I can't even get a photo to show up in Ubuntu but its giving me alot more options to browse the inactive files of the OS that was on it previously (Windows 7). If you got any questions or need anymore information please don't hesitate to ask, I don't want this thing to be a paperweight, or re-purposed.


[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]Below is some information about the external HDD that Ubuntu displays to me:[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]WD My Book 1140[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]Size - 2.0 TB[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]Partition Type: HPFS/NTFS (0x07)[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]Device - /dev/sdd[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]Volume - Unknown[/FONT][/COLOR]

---

### Post by andyfied on 2013-11-28
Hello

This is a common problem with external drives and can be caused by failing to unmounts the drive before disconnecting the cable or just because the drive felt like it that day!

Check this thread [http://ubuntuforums.org/showthread.php?t=387922](http://ubuntuforums.org/showthread.php?t=387922) for instructions on rescuing your data. Do NOT do anything that will write to the USB drive. No repairing or formatting! Use the recovery tools to copy your data to a safe location then you can reformat the drive and see if it is okay with gsmartmontools and badblocks before trusting it with your data again.

---

### Post by andyfied on 2013-11-30
Right, I have had time to play with Testdisk now and I can help out with some detail.

1. Testdisk is available from Synaptic and that will give you the latest version. Don't bother with the instructions to get it from the link I gave.

2. I took a USB flash drive and deleted its partition in Windows. (Nothing critical on the drive, just some junk.)

3. I used Testdisk to restore the partition table and the drive worked again as normal with the files all accessible. (This step is different from the instructions in the link though.)

Follow the instructions in the link in my last post which (should) will pull all the files out.

If this doesn't work then you might consider trying to recreate the old partition or repair it. Before you go ahead and do the same I urge you to make a clone of your HDD if you have the space to put it somewhere. [B]If this goes wrong it will be way harder to recover your data.
[/B]
Now there are plenty of tools to clone your drive. Let me know if you need to know about them in detail (I tend to use DD). Once you can a safe clone somewhere then you can navigate to your /repair/ directory and run
```
sudo testdisk
```
Select your dodgy drive. Select INTEL/PC Partition. Select 'Analyze' then 'Proceed' then select 'Search'. (As per other instructions.) Once it finds the partition you can choose to "Write". This will hopefully restore your drive to its original functionality.

If you have *any* doubts about what you are doing then **do not write to your dodgy drive**. Come and discuss your concerns and we'll try to work them out :)

Once you get your data back and your drive seems to be back okay then please install gsmartmontools from Synaptic and run some tests on it to make sure it's not throwing up any "imminent failure" errors and then we might run badblocks over it to make sure there are no dodgy sectors.

Hope all that makes sense!

---

