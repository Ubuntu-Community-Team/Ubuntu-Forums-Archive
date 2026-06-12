---
title: "Can't Boot to XP after I formatted HD containing Ubuntu. Pls help!"
date: 2008-11-12
forum: General Help
---

### Post by Tonet on 2008-11-12
I have two harddisks, one containing Ubuntu and the other contains XP. The XP was installed first. 

I formatted the hard disk using XP because I plan to install Ubuntu 8.10 to another PC instead. When I restarted the computer, I couldn't boot to XP anymore!! I forgot the message that appeared.

After that, I installed the Ubuntu again in the other hard disk, and this time, I could boot to XP again.

However, my Ubuntu crashed. I want to format the hard disk again but I am afraid that I wouldn't be able to boot to XP again if I do that.

What will I do?:(

P.S. I'm a newbie at Ubuntu.

---

### Post by Afkpuz on 2008-11-12
When you install ubuntu, it installs it's own bootloader called grub.  Grub is able to start both ubuntu and windows.  when you erase ubuntu, you erase the bootloader.  So, here's what you need to do.

If you're taking out the ubuntu hard drive, you need to get a hold of a windows install disc and install the windows bootloader.  Boot off the disc and when it says "press r to enter repair mode", do it.  Once in a command line, enter your password.  Usually, this is blank.  Then, enter this
```
FIXMBR
```

That should make windows self-sufficient.

---

### Post by Tonet on 2008-11-12
Thank you, I'll try that.:)

---

### Post by Tonet on 2008-11-13
> **Afkpuz said:**
> When you install ubuntu, it installs it's own bootloader called grub.  Grub is able to start both ubuntu and windows.  when you erase ubuntu, you erase the bootloader.  So, here's what you need to do.

If you're taking out the ubuntu hard drive, you need to get a hold of a windows install disc and install the windows bootloader.  Boot off the disc and when it says "press r to enter repair mode", do it.  Once in a command line, enter your password.  Usually, this is blank.  Then, enter this
```
FIXMBR
```

That should make windows self-sufficient.

Is there any other way? I can't seem to get it right. When I pressed the R, It asks me which windows installation to repair, whatever I press, nothing happens but when I pressed enter, my PC merely restarted. :confused:

By the way, how do you install the windows bootloader?

---

### Post by louieb on 2008-11-13
> **Tonet said:**
>  how do you install the windows bootloader?
[B]
Afkpuz[/B] described the normal way.  Might be something odd about your setup and thats why it did not work. 

Here are some alternative options. [IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

---

### Post by Tonet on 2008-11-15
> **louieb said:**
> [B]
Afkpuz[/B] described the normal way.  Might be something odd about your setup and thats why it did not work. 

Here are some alternative options. [IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

Thanks, it worked!!

Now I have to remove this option to choose OS:

Choose which Operating System to use:

Windows XP Professional
Ubuntu

How do I remove this?

---

### Post by louieb on 2008-11-15
It seems that you install Ubuntu inside windows using wubi?
If so you want to edit c:\boot.ini.

---

### Post by TeXtonyx on 2008-11-15
"Thanks, it worked!!

Now I have to remove this option to choose OS:

Choose which Operating System to use:

Windows XP Professional
Ubuntu

How do I remove this?"

TeX: Something seems not right to me. Unhook the power cable to the
drive which has Ubuntu installed. Now reboot and pick XP Pro to boot.
I think it's not going to boot XP because you haven't removed grub.
I think you are looking at the boot options from grub's menu.lst
Because it is too advanced for you to be looking at the XP
boot options that are used by XP's boot.ini.

Your XP install disk _will_ fix this, I'll give detailed instructions.
FIXMBR
FIXBOOT
BOOTCFG /REBUILD
The last one will rebuild your boot.ini which has the boot options.

Getting to the right "Repair" screen is a bit tricky, I'll see
if I can you some pictures; there are two such menus.

[http://www.simplyguides.net/guides/recovery_console/recovery_console.shtml](http://www.simplyguides.net/guides/recovery_console/recovery_console.shtml)
This is the main page with pictures and a howto.

[http://www.simplyguides.net/images/guides/recovery_console/4.jpg](http://www.simplyguides.net/images/guides/recovery_console/4.jpg)
This is the fourth image down (blue) on the first page, I wanted
you to see it expanded. So click on the 4th image to expand it
or I think the above url (4.jpg) shows the screen enlarged.

"To Repair a Windows XP installation using Recovery Console, press R."

So press R. Just follow the instructions.I don't think you need
to run chkdsk, unless there is a problem, so at first just try
the three commands I mentioned, which are also covered on the
webpage provided. You might not remember the steps, so you could
write them down or print them out to use in the recovery process.

You are better off not creating an Administrator password if 
there is any chance at all you will forget it or lose it. They
do have programs which will reset the Administrator password but
that is a bit of a pita. I add that Recovery Console to my
boot up options, but for now skip it, you can do it later after
this is working right. 

So now I don't think you will see the boot up screen with options
because there is only one choice which isn't shown. If you do
see it, it means you haven't mentioned something like Wubi or I
don't know what! :popcorn:

Now if you connect the power cable to your second disk, Ubuntu,
it might not boot. That means you need to reinstall grub to
the MBR of the ubuntu second drive. That is called hd1 or sdb
and don't confuse that with your first drive, hd0 or sda.

Anyway, post here if you get to that stage, many people on the
forum can tell you how to fix that. Get XP working first.

I think before with the XP install disk, you might have chosen,
"To set up Windows XP now, press ENTER" which is the wrong choice.

If you did use Wubi, often you can uninstall it using Windows
Add/Remove programs. The boot.ini file itself, is a hidden file
which means you need to enable viewing it. Use Windows Help and 
Support to learn how to enable the viewing of hidden files. Once 
you see boot.ini in Windows Explorer, right-click on the file.
Choose Properties, it usually is set as "read-only" which means
you can't edit the file in Notepad in order to delete the Ubuntu
entry unless you uncheck that "read-only" box. Delete "Ubuntu"
and don't forget to _save_ the file so that your edit sticks.

---

### Post by caljohnsmith on 2008-11-15
If you are seeing Ubuntu listed in the Windows boot menu, then as louieb mentioned, that means you must have had a Wubi install of Ubuntu at some point. You can easily correct that by editing your boot.ini file via [these directions]("http://support.microsoft.com/kb/289022") from Microsoft, and simply remove the line in boot.ini that says:
```
C:\wubildr.mbr="Ubuntu"
```
That should remove the Ubuntu choice in your Windows boot menu. Let us know how it goes. :)

---

### Post by Tonet on 2008-11-16
No I didn't install wubi, whatever that is.:confused:

---

### Post by TeXtonyx on 2008-11-16
Why don't you copy and paste the content of boot.ini? 
There is another way an entry for Ubuntu could be in boot.ini
and show up on your boot menu, but I think it is unlikely that
you know of that method, or used it.

That is besides the point, whether you installed Wubi or not.
You want Ubuntu not to show up on your menu options. The content
of boot.ini controls the menu options. So put the file in a text editor 
like Notepad (change from files of type .txt to all files)
and unhide the file and change the read-only permissions as 
previously described. This proceeds after first booting to XP.
The boot.ini file is found in your root directory, C:\> Unless you've enabled 'show extensions' the file will show as boot, without the .ini

You want to delete some line which refers to Ubuntu, and save it.

If you don't have a line referencing Ubuntu in the boot.ini file,
then it has to be generated from some other bootloader-> menu file,
not Windows. Grub would then be the most likely bootloader->menu file.

---

### Post by alwayshere on 2008-11-16
I always use a hard drive for  windows  and another for ubuntu and always have the one im not using turned off in bios.sounds like a pain but better than reinstalling both os all the aye.

---

