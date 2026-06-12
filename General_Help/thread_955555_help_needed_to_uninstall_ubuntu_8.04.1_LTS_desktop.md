---
title: "help needed to uninstall ubuntu 8.04.1 LTS desktop edition!!!"
date: 2008-10-22
forum: General Help
---

### Post by turbo71113 on 2008-10-22
i recently installed ubuntu on one of my hard drives...i found that i cannot access the files from ubuntu present on that drive.

now i want to make a seperate partition for ubuntu and install on that drive.

can anyone help me out to install inside windows....and also to uninstall the ubuntu which i have recently installed....

---

### Post by Rainstride on 2008-10-22
to install inside windows you just put your disk in when your logged in, it should open the auto run and there is a button for that (theres only 3 buttons).

as for uninstalling, you just delete the partition or format it. just becareful as to what you are deleting or formating. and know what something is before hand or you might accedently delete your window partition.

---

### Post by northern lights on 2008-10-22
Exactly what files can you not access from what OS?
There's most likely a better workaround than "uninstalling" your current Ubuntu and "reinstalling" inside Windows.

Running Wubi (inside Windows) is a decent options to check out a new OS, but not a long-term solution.

Linux has been able to read from and write to FAT for ages. It could read NTFS for a while now also. And with the appearance of ntfs-3g, which is installed by default since Gutsy (i.e. for about a year) it also writes to NTFS by default.

Installing the second party app [fs-driver]("http://www.fs-driver.org") allows your Windows to access ext2 and ext3 formatted partitions as well.

Theoretically though, if you're still determined to rid yourself of the permanent Ubuntu install, do the following:
Within Windows, open the "Run" dialog. Type 'mmc' (without quotation marks) and hit Enter. From the 'File' menu select 'Add/Remove Snap-In'. Add 'Disk Management'. Close menu. In the left-hand column, highlight 'Disk Management'. In the right-hand column, a representation of your drive structure should just have appeared. Right click the Linux partition and choose to delete. Create a new one or append the unallocated space to an existing partition.

But really, please, for your own and society's benefit, don't give up so easily.

---

### Post by etdsbastar on 2008-10-22
**Step by step process:**

1. Boot your machine with windows xp.
2. After the boot up process has been completed just insert the Ubuntu CD.
3. Select Install inside Ubuntu option from the autorun menu of the Ubuntu CD.
4. Select a folder to install too.
5. After the installation has been completed, reboot your machine but now with Ubuntu.
6. Further, You can delete your old Ubuntu partition with Disk Management Option of Windows XP.

---

### Post by turbo71113 on 2008-10-22
seems that all of you did not understand my problem.
i installed ubuntu on E: drive on my computer which is of 40 gb.
thers lots of stuff on E: drive.
during installation it displayed a message that ubuntu requires just min of 4 gb. and so i selected one of my 4 drives thas E:,
now though it has uninstall option,thats not working.

if i just delete the ubuntu,will the grub appear during booting.

please help>>

---

### Post by turbo71113 on 2008-10-22
please reply anyone....

i cannot format the drive in which i installed ubuntu because i have soo much other data on that drive.....
:confused:

---

### Post by northern lights on 2008-10-23
Mkey.

I can only speak for myself, but at least I, for once really had not understood your problem. And I'm still confused.

Did you install Ubuntu from within Windows (via Wubi) the first time also?
Or did you install by booting from the LiveCD?

In the latter case you can probably format the third partition (the "E" drive, if you so will), because you erased the data at the point of install already.
GNU/Linux is an operating system after all and not some handy-dandy app. It uses a completely different filesystem and hence formats the partition is installed to.

If you installed from within Windows, you can simply delete the Ubuntu instance. However you shouldn't have problems accessing your files on "E" either.
I never used Wubi, but it seems weird you should have the need of a bootloader (GRUB) if you installed that way. Meaning most likely you can wave your files on "E" good-bye.

I hope for your sake that's not the case and I still haven't quite understood you right. If you feel that's the case, please follow up with an in-depth step-by-step description of how you ended up with this problem. Thanks.

---

### Post by etdsbastar on 2008-10-23
> **turbo71113 said:**
> seems that all of you did not understand my problem.
i installed ubuntu on E: drive on my computer which is of 40 gb.
thers lots of stuff on E: drive.
during installation it displayed a message that ubuntu requires just min of 4 gb. and so i selected one of my 4 drives thas E:,
now though it has uninstall option,thats not working.

if i just delete the ubuntu,will the grub appear during booting.

please help>>

Yes you can rewrite the master boot record dear.

I am telling you the step by step process:

1. Boot from the XP cd.
2. On the first screen, select Repair option.
3. Select the XP operating system from the text menu that appears (basically its option one).
4. Now, type your administrator password.
5. Now the C:/Windows> or like prompt appears, type WRITEMBR command and press enter with Yes option.
6. Your master boot record will be re-written and then type exit (remove your XP cd).
7. Now, XP will be booted by default and GRUB will be removed.
8. Now, Uninstall your Ubuntu installation from the D: drive by just removing the Ubuntu folder.
9. Go to Add or Remove Programs... Select Uninstall Ubuntu and remove it from add or remove programs list.
10. Now, your Ubuntu is completely uninstalled.

Reply...

---

### Post by turbo71113 on 2008-10-23
@northern lights

i have installed ubuntu 8.04.1 LTS when iam logged on in vista,
it has an option of installing with minimun space of 4gb.

and the drive i installed is on E: drive without formatting it.

to be more clear ubuntu installed on my system like any other softwares we install on vista or xp.

though it has an uninstall option its not working.

i dint install it from live cd or from boot up.

am i clear bro!!!

---

### Post by turbo71113 on 2008-10-23
> **etdsbastar said:**
> "Yes you can rewrite the master boot record dear.

I am telling you the step by step process:

1. Boot from the XP cd.
2. On the first screen, select Repair option.
3. Select the XP operating system from the text menu that appears (basically its option one).
4. Now, type your administrator password.
5. Now the C:/Windows> or like prompt appears, type WRITEMBR command and press enter with Yes option.
6. Your master boot record will be re-written and then type exit (remove your XP cd).
7. Now, XP will be booted by default and GRUB will be removed.
8. Now, Uninstall your Ubuntu installation from the D: drive by just removing the Ubuntu folder.
9. Go to Add or Remove Programs... Select Uninstall Ubuntu and remove it from add or remove programs list.
10. Now, your Ubuntu is completely uninstalled.

Reply..."

thanks for the reply...but will this same process work with VISTA:confused:

---

### Post by turbo71113 on 2008-10-24
> **northern lights said:**
> Mkey.

I can only speak for myself, but at least I, for once really had not understood your problem. And I'm still confused.

Did you install Ubuntu from within Windows (via Wubi) the first time also?
Or did you install by booting from the LiveCD?

In the latter case you can probably format the third partition (the "E" drive, if you so will), because you erased the data at the point of install already.
GNU/Linux is an operating system after all and not some handy-dandy app. It uses a completely different filesystem and hence formats the partition is installed to.

If you installed from within Windows, you can simply delete the Ubuntu instance. However you shouldn't have problems accessing your files on "E" either.
I never used Wubi, but it seems weird you should have the need of a bootloader (GRUB) if you installed that way. Meaning most likely you can wave your files on "E" good-bye.

I hope for your sake that's not the case and I still haven't quite understood you right. If you feel that's the case, please follow up with an in-depth step-by-step description of how you ended up with this problem. Thanks.

i have installed ubuntu 8.04.1 LTS when iam logged on in vista,
it has an option of installing with minimun space of 4gb.

and the drive i installed is on E: drive without formatting it.

to be more clear ubuntu installed on my system like any other softwares we install on vista or xp.

though it has an uninstall option its not working.

i dint install it from live cd or from boot up.

am i clear bro!!!

---

### Post by turbo71113 on 2008-10-24
reply please......!!!!!!

---

### Post by turbo71113 on 2008-10-24
reply please

anyone help to solve my problem

---

