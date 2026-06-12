---
title: "SD Card.. Ubuntu works XP doesn't?"
date: 2008-05-25
forum: Hardware
---

### Post by Obssoyo on 2008-05-25
Hello All,

Thankyou for reading my post,  I have been using Ubuntu for a few weeks now and love it! Just yesterday something weird happened with my computer I went to copy some things from ubuntu to windows with my SD Card and when I booted windows xp it doesn't even notice that I plugged in my SD card (built in reader) I may as well of had a brick connected to it.

I have access to 3 laptops. One dual boots ubuntu/vista(my buddies) one does ubuntu/xp and my eee pc runs only ubuntu.  The SD card works in every machine but in the ubuntu/xp one.  It runs fine in ubuntu and not in the XP partition.

It also ran in XP up until yesterday the only thing I did different was I tried to make wine boot starcraft and failed so I tried to move it to xp with my SD card couldnt and went on with life and just mounted my xp partition and moved it that way.  However my wife isn't so great at Linux yet and kinda needs xp around for a few things.  

Any ideas? is it a setting? all help is appreciated I'm out of ideas at the moment.

EDIT: I Just tried other SD cards... and they all work fine in XP... Just this one Sd card doesn't work in XP.

---

### Post by EXCiD3 on 2008-05-25
Thats pretty odd. Theres a possibility the drivers for the reader are messed up in windows...but thats about all i can think of that would cause that.

---

### Post by ljonesj on 2008-05-25
check ur format of the sd card it might be wrong

---

### Post by Obssoyo on 2008-05-26
my format like ntfs fat fat32?  I know it is set to fat32 what exactly do you mean?  also thanks for the replies

---

### Post by Obssoyo on 2008-05-26
Still looking for an answer if anyone has it :D

---

### Post by Obssoyo on 2008-05-27
Sorry to keep posting again and again I just keep hoping someone who knows what to do will see this.

---

### Post by EXCiD3 on 2008-05-27
Since it works fine in Ubuntu, do you think its more of a Windows problem? You could also run fsck on it to make sure the format is not corrupted anywhere. Other than that i cant really think of much else.

---

### Post by stchman on 2008-05-27
I would be interested in this answer as well.  My girlfriend has a laptop with a 5 in 1 card reader and in Vista you can plug in an xD card and viola.  You plug in an SD card and nothing.

I booted the Hardy LiveCD and the exact opposite.  No xD but SD works.

Strange.

---

### Post by EXCiD3 on 2008-05-27
> **stchman said:**
> I would be interested in this answer as well.  My girlfriend has a laptop with a 5 in 1 card reader and in Vista you can plug in an xD card and viola.  You plug in an SD card and nothing.

I booted the Hardy LiveCD and the exact opposite.  No xD but SD works.

Strange.

That could just be your reader drivers in linux. I know that the builtin reader on my laptop will only read SD and one other format, but not the other 3. I'm not sure why in vista an SD card wont work, checked to update the drivers there also?

---

### Post by stchman on 2008-05-27
> **EXCiD3 said:**
> That could just be your reader drivers in linux. I know that the builtin reader on my laptop will only read SD and one other format, but not the other 3. I'm not sure why in vista an SD card wont work, checked to update the drivers there also?

I just purchased a Toshiba laptop with the Ti 5 in 1 reader and the same thing.  SD works but xD does not.  I did some reading and apparently the xD drivers for the Ti card reader are not yet written for Linux so I can accept that.  I would expect them to work for Vista though as the laptop comes with Vista.

---

### Post by EXCiD3 on 2008-05-27
> **stchman said:**
> I just purchased a Toshiba laptop with the Ti 5 in 1 reader and the same thing.  SD works but xD does not.  I did some reading and apparently the xD drivers for the Ti card reader are not yet written for Linux so I can accept that.  I would expect them to work for Vista though as the laptop comes with Vista.

Being advertised as supportin xD cards they should. I would check Toshiba's website for drivers for the card reader. My laptop is an HP and i know that there have been many driver updates released...including a custom Nvidia driver which means that i cant even use the official nvidia driver from nvidia.com. :(

---

### Post by Obssoyo on 2008-05-29
You know I originally thought it might have been a windows problem as well but then other SD cards worked just fine so I figured maybe there was some permissions or some weird formatting that Linux could have done to it to make just this one sd card not work.  Is Fsck in ubuntu? and where?

---

### Post by EXCiD3 on 2008-05-29
fsck is in ubuntu and you can either use terminal to do it or another way that i prefer to do is to install GParted and then right click on the partition of the drive and choosing to Check For Errors (or something like that). Here is a little bit about fsck from terminal: [http://www.adminschoice.com/docs/fsck.htm](http://www.adminschoice.com/docs/fsck.htm)

---

### Post by dranoweb on 2010-06-17
The fix is quite simple,

reboot, 

press f2 for bios menu

change os status to "complete" instead of "start"

---

