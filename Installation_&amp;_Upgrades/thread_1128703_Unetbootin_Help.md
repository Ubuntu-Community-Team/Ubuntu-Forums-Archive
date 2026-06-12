---
title: "Unetbootin Help"
date: 2009-04-17
forum: Installation &amp; Upgrades
---

### Post by getenet on 2009-04-17
Hi All,

So today for some reason I tried to install 8.10 using Unetbootin. Unfortunately it looks like it worked. I think I may have installed it on the hard drive. Whenever I boot up my computer I get the Automatic countdown that that says  "Will boot in 10 seconds". I dont know why it keeps showing this. There is no USB device connected to the computer. I have tried to run the normal boot but it wont let me exit. 

Is there a command which lets be delete UNetbootin from the computer perhaps. Please someone help me.

---

### Post by Daisuke_Aramaki on 2009-04-17
> **getenet said:**
> Hi All,

So today for some reason I tried to install 8.10 using Unetbootin. Unfortunately it looks like it worked. I think I may have installed it on the hard drive. Whenever I boot up my computer I get the Automatic countdown that that says  "Will boot in 10 seconds". I dont know why it keeps showing this. There is no USB device connected to the computer. I have tried to run the normal boot but it wont let me exit. 

Is there a command which lets be delete UNetbootin from the computer perhaps. Please someone help me.

unetbootin is a program to create bootable linux distros, like ubuntu. this way one can use just a usb stick to install ubuntu instead of a cd. if you prepared the stick and used it to install ubuntu , obviously it is installed on your hard disk.

---

### Post by getenet on 2009-04-17
How do I remove it so I can normal boot. I mean it just shows that default screen. I tried the bios and everything. Escape works buts just says "Boot:"

I dont know what to type.

---

### Post by Daisuke_Aramaki on 2009-04-17
> **getenet said:**
> How do I remove it so I can normal boot. I mean it just shows that default screen. I tried the bios and everything. Escape works buts just says "Boot:"

I dont know what to type.

So you have ubuntu on your hardisk, and you want to remove it? is that what you are asking? if you intend to keep ubuntu, and want to use windows, and assuming your windows partition is still there , just choose the windows boot option in boot menu and login to windows. don'T screw up anything BIOS, unless you know what you are doing.

---

### Post by getenet on 2009-04-17
No I still want to use the installed Version of Ubuntu on my computer. Infact I dont plan on using Unetbootin to upgrade the computer. All i want to do is get back to the normal Desktop.

Thank You.

---

### Post by Dougie187 on 2009-04-17
It sounds like you just have your usb stick plugged in still. Or a Cd in the drive. You only get the "boot:" prompt if you boot to a live cd, or unetbootin, and then press esc when it gives you the options "Use ubuntu without changing your computer...". Also at that prompt you could select the "Boot to hard drive" option to boot your computer like normal.

---

### Post by Daisuke_Aramaki on 2009-04-17
> **getenet said:**
> No I still want to use the installed Version of Ubuntu on my computer. Infact I dont plan on using Unetbootin to upgrade the computer. All i want to do is get back to the normal Desktop.

Thank You.

upgrading to a new release of ubuntu can be done from the hard disk, unetbootin just helps you to create a bootable usb disk, it is just like a cd writer that one can use to write cds. and u cannot use unetbootin to upgrade. so relax. you are confused about unetbootin and what it does.

if you have unplugged the stick, it should be alright.

---

### Post by getenet on 2009-04-17
Is there a way to delete it so I can boot up normally.

The computer turns on. Shows the Unetbootin screen and shows the automatic countdown. Nothing Happens. NO USB in the computer. I need to remove it.

---

### Post by Daisuke_Aramaki on 2009-04-17
> **getenet said:**
> Is there a way to delete it so I can boot up normally.

The computer turns on. Shows the Unetbootin screen and shows the automatic countdown. Nothing Happens. NO USB in the computer. I need to remove it.

Go to BIOS, and change the boot priority, and choose hard disk as the primary boot device. save and then exit and restart

---

### Post by getenet on 2009-04-17
yes...i did. Though unfortunately it shows up again. Its as if Ubuntu was replaced with this Unetbootin Menu. The only options I have are to press tab or exit. When I press tab I am able to type things. When I press EXIT it says:
"boot:"

Any idea? Will I have to loose everything I have? If so please say, I wouldnt want you all to spend too much time on this. But if there is a way I would be so happy.

---

### Post by sesheron on 2009-04-17
Sounds like a question for a Unetbootin forum.  Cause somehow you selected your harddisk to copy the livecd to and not the USB drive.

---

