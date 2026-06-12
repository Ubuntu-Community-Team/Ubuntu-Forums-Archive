---
title: "Another Low Screen Resolution Question"
date: 2005-06-30
forum: Hardware &amp; Laptops
---

### Post by Irony on 2005-06-30
I've done a clean install of Ubuntu 5.04 on an old Pentium II, 300MHz, 128MB RAM, 6GB disc laptop.

After some initial problems the laptop now boots up fine but is in 640x480 screen resolution - this is the only option in the screen resolution window.

However if I use the live CD of Ubuntu the screen resolution is 1024x768, with options of 800x600 and 640x480.

How do I get the screen resolution to 1024x768 when running from the installed version?

I've read about altering the /etc/X11/xorg.conf file but as a total Linux newbie I don't know how to actually save this file (after altering it) as it is read only. Do I have to boot up in shell mode, if so how do I do this and how do I locate the /etc/X11/xorg.conf file in this mode.

I'm confident when doing Windows stuff but Linux is totally alien at the moment.

---

### Post by rachii on 2005-06-30
you cant edit the file because you dont have permission, and you can still do it in graphical mode, dont worry. type:```
sudo gedit /etc/X11/xorg.conf
``` into a console, and it will open up the file allowing you to edit it.  it will prompt for a password, this is your account password

sudo gives you "super user" permissions allowing you to do stuff when needed

---

### Post by andlinux21 on 2005-06-30
yes do a sudo gedit xorg.conf and i just change the 24 to 16 and I get several screen resolutions after i save and reboot.

---

### Post by rachii on 2005-06-30
also if just adding the resolutions doesnt work (it should), i found it necessary with mine, to add the horizontal and vertical rates in the monitor section before it would work

HorizSync     #-#
VertRefresh  #-#

---

### Post by Irony on 2005-07-01
Oops.

I changed the resolution Default Depth to 16 but this didn't work. I then messed with the Sync and Refresh rates but it now won't boot into GUI mode, of course I didn't know what these were supposed to be so just used some values I found in another post.

I then somewhat belatedly understood what you meant by resolution settings after viewing another post.

However it occurred to me that as the Live CD works I could look at the xorg.conf settings there - and this shows me the correct Sync and Refresh rates and also the correct Depth and Mode values which aren't shown in the actual install.

I'm now reinstalling Ubuntu and will change the values to that shown in the Live CD.

I'll report later on if this works.

---

### Post by Irony on 2005-07-01
Success!!!

By following your instructions regarding sudo gedit I altered the xorg.conf file by adding HorizSync and VertRefresh values shown in the Live CD.

I then rebooted but it got only so far before going blank. So I booted again and hit Esc when it gave that option, then I selected the Ubuntu normal start (not recovery) and its now at full resolution and thus useable.

Thanks for advice.

---

### Post by Irony on 2005-07-02
Having successfully resolved the screen resolution problem I then decided to install XP again because I was going to select the install as FAT system so I could then partition it using the FIPs system.

However during the XP install I noticed that I can actually create and delete partitions. I missed this before. I therefore deleted all existing partitions to create one big unallocated space and then created a 2GB partition leaving 4GB of the total 6GB unallocated.

I've now installed XP. This unallocated partition isn't usable but through admin tools in XP can be created as a usable partition. I did this then unallocated in admin tools by way of experimentation.

The thing is that creating the partitions in the XP install is exceedingly simple.

I'm now installing Ubuntu to the 4GB of free space that the unallocated drive shows.

The reason I'm doing this is I want to practice before I install Ubuntu on my big desktop computer. I've noticed that I can set the second drive on the desktop to unallocated so perhaps this is what I will do.

Ubuntu is currently installing so I'll report back on if it works.

---

### Post by Irony on 2005-07-02
Its worked!

I now have a dual boot laptop. I had to alter the screen resolution of Ubuntu again, but that is quick now know how to do it.

---

### Post by douglash on 2005-09-30
I am having the same problem (res 640x480 when 1024x768 is possible).

I have:
 - lowered the bit depth to 16
 - added 800x600 to the resolutions (it only shows 640x480)
 - tried redetecting the monitor specs as on the how to page
[https://wiki.ubuntu.com/FixVideoResolutionHowto](https://wiki.ubuntu.com/FixVideoResolutionHowto)

but none of this has worked.

I am on a Tecra 8000 laptop.

I have been unable to find the horizsync and vertrefresh rates
The controller(?) is a neomagic corporation nm2200 magicgraph 256av

any help greatly appreciated, i have never used linux before so assume nothing,
Thanks.

---

