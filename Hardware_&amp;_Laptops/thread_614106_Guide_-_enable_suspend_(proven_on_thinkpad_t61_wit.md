---
title: "Guide - enable suspend (proven on thinkpad t61 with nvidia)"
date: 2007-11-15
forum: Hardware &amp; Laptops
---

### Post by jimmy the saint on 2007-11-15
One of the many problems associated with the Thinkpad *61 series and nvidia is the suspend/hibernate feature being broken.  Thinkwiki is a great resource for information on getting Ubuntu and other distros working on a Thinkpad, but I found a much simpler way to enable suspend than the method that they have.  I have drawn on two sources (both listed below) for this guide, one with the method to enable suspend, and one for instructions on how to add Kernel parameters.  Since I am so new with linux, the second was extremely helpful.

First, for my fellow newbies, let me explain how you will make the modifications.  Since I am coming from windows, and am not quite comfortable with the command line, I created a menu entry that launches gedit with admin privileges.  use the command "gksudo gedit" as the command in the launcher.  This will enable you to edit and save files that require root privileges.  Use this only when you have to and be very careful.

The files you will modify are /boot/grub/menu.lst and /etc/default/acpi-support.  If you open them with the privileged gedit I described above, make sure to save a backup before modifying them.  

You will be adding a kernel parameter to the grub menu list.  In the last section, you will see the various menu entries and their parameters.  Each of these correspond to the boot menu options you should see when you power up your computer, especially if you dual boot.  For more details go to the "grumpymole" link I have provided.  At the end of the "kernel" line for the boot session you wish to enable suspend in, add the following to the end of that line : 
"acpi_sleep=s3_mode" without the quotations if you use the Proprietary drivers, or  
"acpi_sleep=s3_bios"  if you use the vesa drivers.
make sure you include a space before you add this.

Now on the the acpi-support file.  These should be modified regardless of the driver you are using.  Rather than adding options, you will simply be changing their values.  What I did was comment out the relevant line as it was originally and duplicate it with the new value below.  That way, it's easy to change back by just switching which one is commented.   The values to change are:
SAVE_VBE_STATE=false
POST_VIDEO=false

Now suspend to RAM should work.  It did for me!!  Sorry if this was too long winded, but for newbies like me, the more detail the better.  For more details I would definitely recommend checking out the grumpymole link below, it taught me a lot.

Sources:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html]("http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html")
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/139089]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/139089")

---

### Post by romeyde on 2007-11-15
Don't use a thinkpad but do have suspend issues.   Does this issue relate to the PC suspending fine but not waking back up?  Been trying to fix this problem for awhile now without luck.

---

### Post by jimmy the saint on 2007-11-18
Yeah, that is the problem I had.  I have an nvidia card, so that may make a difference.

---

### Post by edvisser on 2007-11-26
After trying several other "solutions" this one works perfectly.  I have an Acer Aspire 5630 with NVidia card.

Thank you for assembling and describing the solution.

Ed

---

### Post by jsully1 on 2007-11-27
Doesn't work for ATI unfortunately.  My thinkpad T60 manages to turn the screen off, but the suspend light flashes indefinitely and I can't wake it.  The last thing that's written to syslog is a bit about deactivating eth1 (wireless), though I don't suspect it's related.

---

### Post by mma8x on 2007-12-05
great advice.  on my r61 running kernel 2.6.22-14-generic, nvidia proprietary drivers,  and gutsy, the "acpi_sleep..." boot option isn't needed--worked fine with just the changes to acpi-support

---

### Post by steveneddy on 2007-12-05
This worked on my Serval Performance Type 1from System76.

Gutsy 64 bit
Core 2 Duo @ 2 Ghz
2 Gig RAM
nVidia
USB, Bluetooth, Firewire

It works on the 2.6.22-14-generic kernel, but **NOT** the** -rt** kernel.

But I do different things with the rt kernel and really don't need it to suspend while on that kernel, but the generic kernel I use for work and need suspend often.

Thanks for this guide.

---

### Post by Auslegung on 2007-12-07
How do I know if I'm using proprietary drivers or vesa drivers?

---

### Post by mma8x on 2007-12-09
> **Auslegung said:**
> How do I know if I'm using proprietary drivers or vesa drivers?

lsmod|grep nvidia

gives you something like this:
```
nvidia               7013492  26
i2c_core               30208  1 nvidia

```

also, on bootup there's a big nvidia splash screen if using their drivers.

---

### Post by jimmy the saint on 2007-12-11
Im glad the post was helpfull.  I spent weeks trying to find a simple enough solution, so when I found it just had to share it!!

---

### Post by ArmyOfOrr42 on 2007-12-28
worked for me too, i didn't have to make any grub changes either.  thanks alot for the solution!

---

### Post by TrinitronX on 2008-02-05
I think with the -rt kernel there's a special little kernel hack that involves changing 2 lines in kernel/rcupreempt.c in the kernel source.  This worked for me to actually get fglrx to compile.

[http://gentoo-wiki.com/HOWTO_ATI_Drivers#Build_ati-drivers_on_rt-kernels_failed](http://gentoo-wiki.com/HOWTO_ATI_Drivers#Build_ati-drivers_on_rt-kernels_failed)

---

### Post by uchihaitachi on 2008-02-27
Thank you so much for the post. 
The configuration also allowed me to suspend and return from suspend with no issues.

Thinkpad T61P 6460-A27

---

### Post by LaszloKv on 2008-03-21
Just wanted to add that this fix works on the r61 with intel video too, but you have to use "acpi_sleep=s3_bios".

---

### Post by jimmy the saint on 2008-04-06
Glad to see this guide is still helpful!  Thanks to everyone who added their experience.

---

### Post by acron1 on 2008-04-07
Eventhough my R61i with integrated intel X3100 suspends just fine, I saved your post as I am thinking of getting a new laptop with nvidia graphics in the near future.
Thanks

---

### Post by FliesLikeABrick on 2008-04-20
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_(Hardy_Heron)_on_a_ThinkPad_T61#Suspend_with_Nv140m](http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_(Hardy_Heron)_on_a_ThinkPad_T61#Suspend_with_Nv140m)

Those instructions helped me get it working on a T61 with an NVIDIA Quadro.  I also did what was in the original post as well as created the file for HAL that is described in there.  For me I needed the second one containing

> <?xml version="1.0" encoding="ISO-8859-1"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
  <device>
    <match key="system.hardware.vendor" string="LENOVO">
      <merge key="power_management.quirk.s3_mode" type="bool">true</merge>
      <merge key="power_management.quirk.s3_bios" type="bool">false</merge>
      <merge key="power_management.quirk.save_pci" type="bool">true</merge>
    </match>
  </device>
</deviceinfo>


in /etc/hal/fdi/information/lenovo.fdi

After this, resuming from suspend to RAM worked perfectly

---

### Post by turned2black on 2008-04-24
This worked for me on my Dell. Thanks a million! :)

---

### Post by david412 on 2008-05-03
> **jimmy the saint said:**
> One of the many problems associated with the Thinkpad *61 series and nvidia is the suspend/hibernate feature being broken.  Thinkwiki is a great resource for information on getting Ubuntu and other distros working on a Thinkpad, but I found a much simpler way to enable suspend than the method that they have.  I have drawn on two sources (both listed below) for this guide, one with the method to enable suspend, and one for instructions on how to add Kernel parameters.  Since I am so new with linux, the second was extremely helpful.

First, for my fellow newbies, let me explain how you will make the modifications.  Since I am coming from windows, and am not quite comfortable with the command line, I created a menu entry that launches gedit with admin privileges.  use the command "gksudo gedit" as the command in the launcher.  This will enable you to edit and save files that require root privileges.  Use this only when you have to and be very careful.

The files you will modify are /boot/grub/menu.lst and /etc/default/acpi-support.  If you open them with the privileged gedit I described above, make sure to save a backup before modifying them.  

You will be adding a kernel parameter to the grub menu list.  In the last section, you will see the various menu entries and their parameters.  Each of these correspond to the boot menu options you should see when you power up your computer, especially if you dual boot.  For more details go to the "grumpymole" link I have provided.  At the end of the "kernel" line for the boot session you wish to enable suspend in, add the following to the end of that line : 
"acpi_sleep=s3_mode" without the quotations if you use the Proprietary drivers, or  
"acpi_sleep=s3_bios"  if you use the vesa drivers.
make sure you include a space before you add this.

Now on the the acpi-support file.  These should be modified regardless of the driver you are using.  Rather than adding options, you will simply be changing their values.  What I did was comment out the relevant line as it was originally and duplicate it with the new value below.  That way, it's easy to change back by just switching which one is commented.   The values to change are:
SAVE_VBE_STATE=false
POST_VIDEO=false

Now suspend to RAM should work.  It did for me!!  Sorry if this was too long winded, but for newbies like me, the more detail the better.  For more details I would definitely recommend checking out the grumpymole link below, it taught me a lot.

Sources:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html]("http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html")
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/139089]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/139089")

This worked great for the suspend problem on the hp tx1000 using s2ram for that session. it worked about 8 times in a row. When i rebooted, it still would not return from suspend.

---

