---
title: "Automatic underclock when CPU is working hard"
date: 2012-05-17
forum: Hardware
---

### Post by MFH86 on 2012-05-17
Hi everybody.

In the last month I've worked on the analysis of some billions of  numbers distributed on some 1000 files. As you may imagine, it's an  intense process that requires from 4 to 8 hours of work for every run.
Since it is such a long process and I like to know how much work has  been done, I made the program print on the shell how much time did it  use to completely process a file. I noticed that when I leave the  computer alone, the CPU goes at full power (2.4 GHz) but when I listen  to music, check my e-mail or in general actively use another program, in  less than a minute the CPU is automatically underclocked at half power  (1.2 GHz) and it requires about 30 minutes to go back to full power.
I even tried to force the CPU at higher frequencies with the Gnome  CPUFreq Applet, but when I select "performance" the CPU remains at 1.2  GHz and when I select an higher frequency my selection becomes 1.2GHz.
This means that I have to choose between not using my computer during the analysis or waiting some extra hours.

So my question is: why does that occur and how can I avoid/contol this situation, if possible?

My computer is an Acer TimelineX 4830TG, CPU is Intel Core i5-2430M @ 2.4 GHz, I use Ubuntu 11.04 with Gnome desktop. I also have a cooling board under the laptop, that lowers the CPU temperature of about 10°C (18°F) in normal circumsances (from 75°C to 65°C - 167°F to 149°F).
The programs run are in Python, but I also noticed the same problem while using Flash and compressing lots of files, so I believe the problem aren't my scripts.
I'm a medium level user of Ubuntu, so I don't have big problems using the shell, I just like to understand what I'm typing.

I hope what I wrote is clear and correct, english is not my mother tongue.
Thanks in advance for the help!

---

### Post by ahallubuntu on 2012-05-17
Sounds like Ubuntu doesn't have the correct power management driver installed, so that whenever the CPU gets any load, it automatically slows down to prevent it from overheating.

A modern laptop should not require a cooling pad unless it is poorly designed or not functioning as designed.  75C is far too hot in my opinion; even 65C is borderline too hot.  Can you check the temps under Windows?

---

### Post by MFH86 on 2012-05-17
Acer is known to have a poor heat management, as far as I know. My two older laptops, also Acer, had the same problem.

I'm sorry but I'm Windows-free since 2007 and have no possibility to install it at the moment.

I have to say that in general the support for this laptop is poor, since it was a new model when I installed Natty, so it's possible that if I install the new version most of these "problems" will disappear, but I can upgrade only in a few weeks and I want to be sure, if possible, that the problem depends on Ubuntu and not on the hardware.

---

### Post by idoitprone on 2012-05-17
> **MFH86 said:**
> Acer is known to have a poor heat management, as far as I know. My two older laptops, also Acer, had the same problem.

I'm sorry but I'm Windows-free since 2007 and have no possibility to install it at the moment.

I have to say that in general the support for this laptop is poor, since it was a new model when I installed Natty, so it's possible that if I install the new version most of these "problems" will disappear, but I can upgrade only in a few weeks and I want to be sure, if possible, that the problem depends on Ubuntu and not on the hardware.

i have the same laptop i believe and i will help

you have to enable the intel power saving features i915 features
Do you have a nvidia optimus graphic card? Do tell because I will advise you to install a newer version of ubuntu to get better hardware support

Always remember to do this when you install any version of linux

[http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1)

```
i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1
```

add these boot parameters to
/etc/default/grub

Change
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to

```
GRUB_CMDLINE_LINUX_DEFAULT="i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1 quiet splash"
```

```
sudo update-grub
```

---

### Post by MFH86 on 2012-05-17
Sorry, I don't understand how this can help me. If I did understand correctly, you are suggesting me improvements for battery life. How can these improvements help me having always the CPU at maximum power?

---

### Post by ahallubuntu on 2012-05-17
If you don't have power saving features enabled, your CPU may get too hot (sounds like it from the temperatures you report) and it will have to slow down the CPU to avoid overheating.

If power saving features allow your laptop to run at a lower temperature, the CPU can run at full speed because it won't get too hot.

---

### Post by MFH86 on 2012-05-17
Seems reasonable. I have just two questions:
1) Are the bugs quoted in the blog you linked before rare or do they occur frequently? What are their consequences?
2) In the worst case scenario, where it will be impossible to log in after the modification of grub, how can I revert the changes?

---

### Post by ahallubuntu on 2012-05-17
In answer to question #2, to fix a broken Grub installation, you can boot your live CD, mount the / partition, then edit the /etc/default/grub file, then update grub.  I prefer the "chroot method" - used it successfully with 10.04 to 11.10 haven't yet tried 12.04:

[https://help.ubuntu.com/community/Grub2/Installing#ChRoot](https://help.ubuntu.com/community/Grub2/Installing#ChRoot)

If you are still able to boot Grub but can't completely boot, you can choose the recovery option from the Grub menu list and do the edit/update Grub that way instead of using the live CD.

---

### Post by idoitprone on 2012-05-17
> **MFH86 said:**
> Sorry, I don't understand how this can help me. If I did understand correctly, you are suggesting me improvements for battery life. How can these improvements help me having always the CPU at maximum power?

Your cpu is not working much at all. In fact it is your gpu that is having those problems. Enabling these power saving features will help your laptop stay cool, hereby extending both the cpu and it battery life.


> Since it is such a long process and I like to know how much work has   been done, I made the program print on the shell how much time did it   use to completely process a file. I noticed that when I leave the   computer alone, the CPU goes at full power (2.4 GHz) but when I listen   to music, check my e-mail or in general actively use another program, in   less than a minute the CPU is automatically underclocked at half power   (1.2 GHz) and it requires about 30 minutes to go back to full power.
I even tried to force the CPU at higher frequencies with the Gnome   CPUFreq Applet, but when I select "performance" the CPU remains at 1.2   GHz and when I select an higher frequency my selection becomes 1.2GHz.
This means that I have to choose between not using my computer during the analysis or waiting some extra hours.So wait you want to manually change the scheduler to always use the full cpu power to ensure all background process get full power. It not going to work because it might be bottleneck by your harddrive. Acer do not spend much money getting good harddrives especially after the Thailand flood. It underclocks for a reason, because it cannot use all of the available resources and also it much ensure system responsiveness

If I were you, I might add noatime to fstab, to reduce writes to the harddrive hereby increasing the speed of your computer

Reverting changes in grub is not hard. all you have to do is delete the changes in grub default and ```
sudo update-grub
```

---

### Post by MFH86 on 2012-05-17
I just tried your suggestion, but the screen goes to 1024x768, which is really bad for a 16:9 screen, and there wasn't any other resolution possible, so I had to go back to the old settings.
Is there a way to force the screen to be 1366x768 with these new settings?

---

### Post by idoitprone on 2012-05-17
> **MFH86 said:**
> I just tried your suggestion, but the screen goes to 1024x768, which is really bad for a 16:9 screen, and there wasn't any other resolution possible, so I had to go back to the old settings.
Is there a way to force the screen to be 1366x768 with these new settings?

```
 acpi_osi=Linux apci_backlight=vendor
```

add these too

I forgot one of these might fix it. I was forgetting why I added those two kernel parameters

---

### Post by MFH86 on 2012-05-18
I added this line in GRUB_CMDLINE_LINUX, but the resolution is always 1024x768.

---

### Post by idoitprone on 2012-05-18
> **MFH86 said:**
> I added this line in GRUB_CMDLINE_LINUX, but the resolution is always 1024x768.

are you sure you added it all

```
cat /proc/cmdline
```

or else there is not much support in natty hmmmmmm

---

### Post by MFH86 on 2012-05-18
Sorry, I don't understand what you are suggesting. :oops:

---

### Post by idoitprone on 2012-05-18
> **MFH86 said:**
> Sorry, I don't understand what you are suggesting. :oops:

i want to know if you put all the parameters in it should work

---

### Post by MFH86 on 2012-05-18
Yes, I wrote:
```
GRUB_CMDLINE_LINUX_DEFAULT="i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1 quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi=Linux apci_backlight=vendor"
```

Is there maybe an explicit way to force the dimension of the screen?

---

### Post by idoitprone on 2012-05-18
> **MFH86 said:**
> Yes, I wrote:
```
GRUB_CMDLINE_LINUX_DEFAULT="i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1 quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi=Linux apci_backlight=vendor"
```Is there maybe an explicit way to force the dimension of the screen?

acpi_osi=linux fixes your fn keys
acpi_xbacklight=vendor should  fix your screen resolution



Did you run ```
sudo update-grub
```?
If you have not updated your grub then the changes are not added to grub.cfg
it should be like mine which has those kernel parameters at the end of linux
```

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub2-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if loadfont unicode ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
set timeout=5
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Fedora (3.3.4-5.fc17.x86_64)' --class fedora --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-25eeb02b-8dab-45aa-bd5b-b3294789f042' {
    load_video
    set gfxpayload=keep
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  25eeb02b-8dab-45aa-bd5b-b3294789f042
    else
      search --no-floppy --fs-uuid --set=root 25eeb02b-8dab-45aa-bd5b-b3294789f042
    fi
    echo 'Loading Fedora (3.3.4-5.fc17.x86_64)'
    linux    /boot/vmlinuz-3.3.4-5.fc17.x86_64 root=UUID=25eeb02b-8dab-45aa-bd5b-b3294789f042 ro rd.md=0 rd.lvm=0 rd.dm=0 SYSFONT=True  KEYTABLE=us rd.luks=0 LANG=en_US.UTF-8 rhgb quiet **acpi_osi=Linux apci_backlight=vendor i915.lvds_downclock=1**
    echo 'Loading initial ramdisk ...'
    initrd /boot/initramfs-3.3.4-5.fc17.x86_64.img
}
menuentry 'Fedora (3.3.2-8.fc17.x86_64)' --class fedora --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-25eeb02b-8dab-45aa-bd5b-b3294789f042' {
    load_video
    set gfxpayload=keep
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  25eeb02b-8dab-45aa-bd5b-b3294789f042
    else
      search --no-floppy --fs-uuid --set=root 25eeb02b-8dab-45aa-bd5b-b3294789f042
    fi
    echo 'Loading Fedora (3.3.2-8.fc17.x86_64)'
    linux    /boot/vmlinuz-3.3.2-8.fc17.x86_64 root=UUID=25eeb02b-8dab-45aa-bd5b-b3294789f042 ro rd.md=0 rd.lvm=0 rd.dm=0 SYSFONT=True  KEYTABLE=us rd.luks=0 LANG=en_US.UTF-8 rhgb quiet** acpi_osi=Linux apci_backlight=vendor i915.lvds_downclock=1**
    echo 'Loading initial ramdisk ...'
    initrd /boot/initramfs-3.3.2-8.fc17.x86_64.img
}
menuentry 'Fedora (3.3.2-1.fc17.x86_64)' --class fedora --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-25eeb02b-8dab-45aa-bd5b-b3294789f042' {
    load_video
    set gfxpayload=keep
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  25eeb02b-8dab-45aa-bd5b-b3294789f042
    else
      search --no-floppy --fs-uuid --set=root 25eeb02b-8dab-45aa-bd5b-b3294789f042
    fi
    echo 'Loading Fedora (3.3.2-1.fc17.x86_64)'
    linux    /boot/vmlinuz-3.3.2-1.fc17.x86_64 root=UUID=25eeb02b-8dab-45aa-bd5b-b3294789f042 ro rd.md=0 rd.lvm=0 rd.dm=0 SYSFONT=True  KEYTABLE=us rd.luks=0 LANG=en_US.UTF-8 rhgb quiet** acpi_osi=Linux apci_backlight=vendor i915.lvds_downclock=1**
    echo 'Loading initial ramdisk ...'
    initrd /boot/initramfs-3.3.2-1.fc17.x86_64.img
}
submenu 'Advanced options for Fedora Linux' $menuentry_id_option 'gnulinux-advanced-25eeb02b-8dab-45aa-bd5b-b3294789f042' {
}
if [ "x$default" = 'Fedora Linux, with Linux 3.3.0-1.fc17.x86_64' ]; then default='Advanced options for Fedora Linux>Fedora Linux, with Linux 3.3.0-1.fc17.x86_64'; fi;
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Recovery Environment (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-0CFEF3BEFEF39E60' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1 --hint='hd0,msdos1'  0CFEF3BEFEF39E60
    else
      search --no-floppy --fs-uuid --set=root 0CFEF3BEFEF39E60
    fi
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry 'Windows 7 (loader) (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-40CCF40ECCF3FFC8' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  40CCF40ECCF3FFC8
    else
      search --no-floppy --fs-uuid --set=root 40CCF40ECCF3FFC8
    fi
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

### BEGIN /etc/grub.d/90_persistent ###
### END /etc/grub.d/90_persistent ###


```this is why i ask for you to```
 cat /proc/cmdline
```to see if you are running those parameters


```
cat /boot/grub/grub.cfg
```[http://www.linlap.com/wiki/acer+aspire+4830tg+timelinex](http://www.linlap.com/wiki/acer+aspire+4830tg+timelinex)


IF that does not  help 
i guess remove  i915_enable_fbc=1 or i915_enable_rc6=1  because there is marginal benefit compared to lvds downclock which lower power on idle

It should support it natively. I am using it right now with 1366x768 resolution and kernel 3.3

You can try to install a newer kernel which will help with your hardware support, but

If you still wish to force resolutions then

here is a guide to force resolutions
[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)




check it with
```
xrandr -q
```One more thing
Did you add noatime to /etc/fstab?
It should add performance since it is not writing as much which also might bottleneck your system causing latency
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by MFH86 on 2012-05-19
Ok, I removed
```
i915.i915_enable_fbc=1
```and the screen is now perfect.

If I run
```
cat /proc/cmdline
```I obtain
```
BOOT_IMAGE=/boot/vmlinuz-2.6.38-15-generic root=UUID=a1228c51-d55b-42ab-969f-42a12976ea86 ro acpi_osi=Linux apci_xbacklight=vendor i915.i915_enable_rc6=1 i915.lvds_downclock=1 quiet splash vt.handoff=7
```so grub is using the parameters inserted.

I have just a last question: it's "apci_xbacklight" or "apci_backlight"?
(I tried both before removing the code in the first box and there was no difference, it's just not to have a useless command)

Edit:
I never added noatime to /etc/fstab. What exactly does this modification do?

---

### Post by idoitprone on 2012-05-19
Its acpi_backlight=vendor


If a file is only read

The kernel will not update its access modifier

This is a problem as it can cause massive slow because it is writing to a file that is only read. It only updates when you write to the file

Noatime is only troublesome if you have a file server such as mutt. If not then your fine.

This will decrease latency and increase through output at the same time because you are doing less.
[http://lwn.net/Articles/244829/](http://lwn.net/Articles/244829/)

---

### Post by MFH86 on 2012-05-19
Just to understand better: I just opened a file, last modified one month ago, and then closed it without any modification.
After I closed the file the "last modified" date remained the same, while the "last accessed" date was updated to today.
What would have happened with noatime? Both of the dates would have remained unchanged?

I'm trying now to run one of the scripts and use firefox, after some minutes the CPU blocked to 1.2 GHz again, the temperature was still high (85°C - 176°F) before, after the block it went down to 75°C.

Since the script has to access 3500 files sequentially, if noatime reduces the load maybe this could help more than ating con the GPU. Where exactly do I have to add noatime in /etc/fstab?

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=a1228c51-d55b-42ab-969f-42a12976ea86 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=679ff7d2-fa27-41f2-b18c-73e84389211d /home           ext4    defaults,user_xattr        0       2
/dev/sda1       none            swap    sw              0       0
```

Thanks a lot for all the help provided until now!

---

### Post by idoitprone on 2012-05-19
> **MFH86 said:**
> Just to understand better: I just opened a file, last modified one month ago, and then closed it without any modification.
After I closed the file the "last modified" date remained the same, while the "last accessed" date was updated to today.
What would have happened with noatime? Both of the dates would have remained unchanged?

I'm trying now to run one of the scripts and use firefox, after some minutes the CPU blocked to 1.2 GHz again, the temperature was still high (85°C - 176°F) before, after the block it went down to 75°C.

Since the script has to access 3500 files sequentially, if noatime reduces the load maybe this could help more than ating con the GPU. Where exactly do I have to add noatime in /etc/fstab?

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=a1228c51-d55b-42ab-969f-42a12976ea86 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=679ff7d2-fa27-41f2-b18c-73e84389211d /home           ext4    defaults,user_xattr        0       2
/dev/sda1       none            swap    sw              0       0
```Thanks a lot for all the help provided until now!

  noatime does not help the gpu. I wanted you those i915 power saving features because the bios might try to protect the cpu from heat by throttling the cpu which does not help much, since the gpu is eating your battery.  I advise you to turn on as many powersaving features that wont affect performance much because less power translate to less heat which mean less wear and tear on your computer

noatime just tell the kernel that you do not want to update the access time every time you read a file. This should help throughout put because you are doing one less thing.

> Just to understand better: I just opened a file, last modified one month ago, and then closed it without any modification.
After I closed the file the "last modified" date remained the same, while the "last accessed" date was updated to today.
What would have happened with noatime? Both of the dates would have remained unchanged?Relatime the default only updates the access time when it is older than modified or creation time

In this case, no modifications are made so the access time should not change.

The access time should get updated when you write to the file since there is no penalty doing it, however there is a penalty writing to file when you only reading it. 



```
UUID=679ff7d2-fa27-41f2-b18c-73e84389211d /home           ext4    defaults,user_xattr,**noatime**
```Before I continue did you change your power settings to never sleep? By default ubuntu throttle both the cpu and harddrive after a period of time and I assume you knew and already changed it, so i have to suggest other things. I believe the throttling of the harddrive is the big performance killer







look at both
```
sudo apt-get install iotop 
sudo iotop
top
```it might be io bottleneck and noatime one help a little

---

### Post by MFH86 on 2012-05-19
Yes, I can't let the computer sleep, it interrupts every process and connection.

Isn't this iotop similar to the system monitor?

---

### Post by idoitprone on 2012-05-19
> **MFH86 said:**
> Yes, I can't let the computer sleep, it interrupts every process and connection.

Isn't this iotop similar to the system monitor?

yep it is. I always keep forgetting because i never used it 

If I know how to collect data that will make sense I would tell you to run it so me or someone else can advise a better solution. I only help manage the could be problems like heat and power. and other common one access write bottlenecks

---

### Post by matt_symes on 2012-05-19
Hi

From here

[http://gadgetholic.net/acer-aspire-timelinex-4830tg-review.html](http://gadgetholic.net/acer-aspire-timelinex-4830tg-review.html)

> We should mention that, at most stressing the &#8216;Acer TimelineX 4830TG for several hours, the CPU throttling undergoes the phenomenon: the frequency of the processor is in fact lowered (and therefore there is a decrease in performance) in order to keep temperatures in the range Security, however, this situation occurs only in the phase of maximum stress and will not affect routine operations.

Your underclocking is being caused by temperature by the looks of it. (like the other posters, that was my initial thought anyway).

You can test this with cpuburn (be careful with this program) and lm-sensors.

What is your fan doing ? What power saving features are you using ? What is the ambient temperature where you are ?

How old is the lappy ? Have you cleaned it for dust recently ? Have you checked the junction between the CPU and heatsink recently ? Have you considered replacing the thermal paste ?

The above suggestions will be dependent on the age of the lappy. I concur with the two above posters though and i think your problem is heat. 

Without the laptop in front of me though i never make 100% cast iron statements :D

Kind regards

---

### Post by MFH86 on 2012-05-19
I won't install cpuburn, I'm already doing enough to stress my CPU. ;)
If lm-sensors is the widget that shows the CPU temperature in one of the bars, it doesn't see any device with this computer. I use xsensors instead, but it's not so immediate to consult.

I suspect my fan isn't working early enough, I suppose it could be a great improvement to trigger it at a lower temperature.
Power saving: just what was suggested before in this topic. Modification of /etc/default/grub and /etc/fstab.
The room temperature is around 21°C, not hot and not cold.
The computer is new, I bought it less than a year ago. Sadly is one of these thin laptops, so I can't open it. No possibilities to unmount the battery, RAM or hard disk, or just clean inside. It's ironic: I bought this computer because of the high performance promised by the components and I can't use the full power.

---

### Post by idoitprone on 2012-05-20
> **MFH86 said:**
> I won't install cpuburn, I'm already doing enough to stress my CPU. ;)
If lm-sensors is the widget that shows the CPU temperature in one of the bars, it doesn't see any device with this computer. I use xsensors instead, but it's not so immediate to consult.

I suspect my fan isn't working early enough, I suppose it could be a great improvement to trigger it at a lower temperature.
Power saving: just what was suggested before in this topic. Modification of /etc/default/grub and /etc/fstab.
The room temperature is around 21°C, not hot and not cold.
The computer is new, I bought it less than a year ago. Sadly is one of these thin laptops, so I can't open it. No possibilities to unmount the battery, RAM or hard disk, or just clean inside. It's ironic: I bought this computer because of the high performance promised by the components and I can't use the full power.

It not that hard to open, but it gets a little involved
It is way easier than this
[http://www.youtube.com/watch?v=OpCJzdWxEbQ](http://www.youtube.com/watch?v=OpCJzdWxEbQ)

I have a similar laptop with nvidia optimus card
```
coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +42.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +41.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +41.0°C  (high = +86.0°C, crit = +100.0°C)
```It runs like this and I almost never hear the fan
At most it shoot up to 60C and that is it. It makes me wonder if you have something that is killing the battery and adding heat

Do you have nvidia optimus? If so we can do another battery saving feature like turning off the descrete gpu on demand

---

### Post by MFH86 on 2012-05-20
I should have Nvidia Optimus, but I don't understand exactly what's my situation. Is it working (is switches on and off the GPU) and you are suggesting to completely disable the GPU or it's not working and the GPU is always on?

---

### Post by idoitprone on 2012-05-20
> **MFH86 said:**
> I should have Nvidia Optimus, but I don't understand exactly what's my situation. Is it working (is switches on and off the GPU) and you are suggesting to completely disable the GPU or it's not working and the GPU is always on?

arrrgs say that sooner because it creates alot of heat issues. nvidia optimus must be controlled by the os or else it will just run at full power without stopping, hereby killing your battery and adding heat

NOTE: I am assuming that you have  nouveau driver
if you have nvidia then we have to make modifications to over place that says nouveau
```
sudo apt-add-repository ppa:bumblebee/stable
sudo apt-get install bbswitch
sudo apt-get install bumblebee

sudo rmmod nouveau
sudo modprobe bbswitch load_state=0
```this should stop making your computer sound like a hot rod


```
sudo bash -c 'echo "options bbswitch load_state=0">  /etc/modprobe.d/bbswitch.conf'
```there a little bug with bbswitch. If nouveau is loaded first the the card is not off at boot. To fix it we delay the nouveau or nvida card by adding a parameter

```
sudo bash -c 'echo "options nouveau msi=1" > /etc/modprobe.d/nouveau.conf'
```You should installed bbswitch and bumblebee and hve 2 new files in modprobe.d with contents

```
options bbswitch load_state=0 
options nouveau msi=1
```respectively

---

### Post by MFH86 on 2012-05-20
Sorry, I didn't even know what Nvidia Optimus was before you wrote here that name. :oops:

What's the name of the nouveau driver? I found "nouveau-firmware", not installed.
Is there something to know about the installation or is it straightforward?

---

### Post by idoitprone on 2012-05-20
> **MFH86 said:**
> Sorry, I didn't even know what Nvidia Optimus was before you wrote here that name. :oops:

What's the name of the nouveau driver? I found "nouveau-firmware", not installed.
Is there something to know about the installation or is it straightforward?


lspci -nnk
 to check
if you ahve a nvidia card

and what driver your are using

those command is practically the entire installation

---

### Post by MFH86 on 2012-05-20
```
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: agpgart-intel
00:01.0 PCI bridge [0604]: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port [8086:0101] (rev 09)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: i915
    Kernel modules: i915
00:16.0 Communication controller [0780]: Intel Corporation 6 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
00:1a.0 USB Controller [0c03]: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 6 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 3 [8086:1c14] (rev b4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 [8086:1c16] (rev b4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge [0601]: Intel Corporation HM65 Express Chipset Family LPC Controller [8086:1c49] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel modules: iTCO_wdt
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series Chipset Family SMBus Controller [8086:1c22] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel modules: i2c-i801
01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:0df4] (rev a1)
    Subsystem: Acer Incorporated [ALI] Device [1025:0550]
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nouveau, nvidiafb
02:00.0 Ethernet controller [0200]: Atheros Communications Device [1969:1083] (rev c0)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: atl1c
    Kernel modules: atl1c
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e034]
    Kernel driver in use: ath9k
    Kernel modules: ath9k
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: rts_pstor
    Kernel modules: rts_pstor
04:00.1 SD Host controller [0805]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:5209]
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
05:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci-hcd
```

The driver in use is "nvidia". I don't know exactly what the kernel modules are, but there is also "nouveau".

```
01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:0df4] (rev a1)
    Subsystem: Acer Incorporated [ALI] Device [1025:0550]
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nouveau, nvidiafb
```

---

### Post by idoitprone on 2012-05-20
> **MFH86 said:**
> ```
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: agpgart-intel
00:01.0 PCI bridge [0604]: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port [8086:0101] (rev 09)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: i915
    Kernel modules: i915
00:16.0 Communication controller [0780]: Intel Corporation 6 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
00:1a.0 USB Controller [0c03]: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 6 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 3 [8086:1c14] (rev b4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 [8086:1c16] (rev b4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge [0601]: Intel Corporation HM65 Express Chipset Family LPC Controller [8086:1c49] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel modules: iTCO_wdt
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series Chipset Family SMBus Controller [8086:1c22] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel modules: i2c-i801
01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:0df4] (rev a1)
    Subsystem: Acer Incorporated [ALI] Device [1025:0550]
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nouveau, nvidiafb
02:00.0 Ethernet controller [0200]: Atheros Communications Device [1969:1083] (rev c0)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: atl1c
    Kernel modules: atl1c
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e034]
    Kernel driver in use: ath9k
    Kernel modules: ath9k
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: rts_pstor
    Kernel modules: rts_pstor
04:00.1 SD Host controller [0805]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:5209]
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
05:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci-hcd
```The driver in use is "nvidia". I don't know exactly what the kernel modules are, but there is also "nouveau".

```
01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:0df4] (rev a1)
    Subsystem: Acer Incorporated [ALI] Device [1025:0550]
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nouveau, nvidiafb
```

ok a few things

You do have a nvidia card

remove that nouveau.conf that I told you to make

```
sudo rm /etc/modprobe.d/nouveau.conf
``````
sudo modprobe -r nouveau
```make sure nouveau is blacklisted.

 ```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates 
 sudo apt-get update
sudo apt-get upgrade
sudo apt-get install bumblebee bumblebee-nvidia

```reboot

to make sure the card is off

```
cat /proc/acpi/bbswitch
```


more info [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by MFH86 on 2012-05-20
I didn't do anything of what you said in the previous post because I wasn't sure it was the correct procedure because of your assumption.

What is the complete procedure to follow?

---

### Post by idoitprone on 2012-05-20
```
sudo add-apt-repository ppa:bumblebee/stable
```
add bumblebee ppa


[LIST]
[*]```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates 
```
[/LIST]
add driver repo


```
sudo apt-get update
```
update repo


```
sudo apt-get install bumblebee bumblebee-nvidia bbswitch
```


install proper packages


reboot

```
cat /proc/acpi/bbswitch
```

check if nvidia card is off

If not then

```
sudo bash -c 'echo "options bbswitch load_state=0">  /etc/modprobe.d/bbswitch.conf'
```

run this

reboot
and check again

---

### Post by MFH86 on 2012-05-20
The installer says there is no package called "bbswitch". There is "bbswitch-dkms" instead. Is this the correct one?

---

### Post by idoitprone on 2012-05-20
> **MFH86 said:**
> The installer says there is no package called "bbswitch". There is "bbswitch-dkms" instead. Is this the correct one?


sure it is a dkms module. the most important package
install it

---

### Post by MFH86 on 2012-05-20
There is a *little* bug: when I reboot the upper and lower bars is disappeared and also the upper bar of every window vanishes. I can't access from the graphic window any program, even the command line, so I had to remove the three packages.
I suppose this means that the nvidia card is off...

---

### Post by idoitprone on 2012-05-20
> **MFH86 said:**
> There is a *little* bug: when I reboot the upper and lower bars is disappeared and also the upper bar of every window vanishes. I can't access from the graphic window any program, even the command line, so I had to remove the three packages.
I suppose this means that the nvidia card is off...

nope
the card is off when 
cat /proc/acpi/bbswitch
returns OFF

Well it pretty obvious to tell when the card is off. When it stops blowing out air and the fan slowly dies down

what you describe there shouldnt happen because the disply port should be connect to the intel gpu
The way nvidia optimus works is that the intel gpu offload work to the nvidia gpu.
unless the nvidia module is loaded and creating that modesetting thingy
which means the card is not offf

hmmmmmmmmmmmmmmmm
the nvidia install was a little botched
I usually do not configure nvidia because it is a pain

it a  little difficult to tell what has happened if i do not see configurations files. I am feeling like I am getting information blind
Sighhhh the bbswitch is the most important package because if you enable it then temperature will go down at least 10C

the rest of the packages is meant to dynamically control your card

or

If you do not want to use your nvidia graphic card at alll

You can simply go to the bios and turn it off.
I have a feeling that trying to configure your card will be a little involved

---

### Post by MFH86 on 2012-05-20
I checked again, when the 3 packages are installed the nvidia card is off, when only bbswitch is installed if I run the command "cat /proc/acpi/bbswitch" it says "cat: /proc/acpi/bbswitch: no such file or directory". :confused:

---

### Post by idoitprone on 2012-05-20
> **MFH86 said:**
> I checked again, when the 3 packages are installed the nvidia card is off, when only bbswitch is installed if I run the command "cat /proc/acpi/bbswitch" it says "cat: /proc/acpi/bbswitch: no such file or directory". :confused:


check if the module is loaded

```
lsmod | grep bbswitch
```

in order for bbswitch to work, no kernel modules that manages the graphic card cannot be loaded

```
sudo modprobe -r  nvidia-current nouveau nvidiafb
``````
sudo modprobe  bbswitch load_state=0
```this should shutown your card
```
cat /proc/acpi/bbswitch
```

---

### Post by MFH86 on 2012-05-20
The card is shut down, the temperature drops slowly, but when I reboot there is again this bug.

---

### Post by idoitprone on 2012-05-20
> **MFH86 said:**
> The card is shut down, the temperature drops slowly, but when I reboot there is again this bug.

seriously....

```
lspci -nnk
```nvidia module should not be in use, since it is unloaded
Is kvm on? or off?

Can I see your configuration files

```
cat /etc/modprobe.d/*
```and

```
cat /var/log/Xorg.0.log
``` You might want to post it on pastebin and give us the link

---

### Post by MFH86 on 2012-05-20
Since I can't use a browser while there is the graphic problem, I can't copy the output of the first command, but I remember that the line about the nvidia card was something like:
```
01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:0df4] (rev a1)
    Subsystem: Acer Incorporated [ALI] Device [1025:0550]
```
With no indication of kernel driver or kernel modules.

Now it is:
```
01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:0df4] (rev a1)
    Subsystem: Acer Incorporated [ALI] Device [1025:0550]
    Kernel modules: nvidia-current, nouveau, nvidiafb
```
There is no more the driver.

[cat /etc/modprobe.d/*]("http://pastebin.com/uvCdHG7d")
[cat /var/log/Xorg.0.log]("http://pastebin.com/dVQhtCVQ")

I don't know how useful can be this log, since it seems to be about this session, with none of the packages installed.

---

### Post by idoitprone on 2012-05-20
> **MFH86 said:**
> Since I can't use a browser while there is the graphic problem, I can't copy the output of the first command, but I remember that the line about the nvidia card was something like:
```
01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:0df4] (rev a1)
    Subsystem: Acer Incorporated [ALI] Device [1025:0550]
```With no indication of kernel driver or kernel modules.

Now it is:
```
01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:0df4] (rev a1)
    Subsystem: Acer Incorporated [ALI] Device [1025:0550]
    Kernel modules: nvidia-current, nouveau, nvidiafb
```There is no more the driver.

[cat /etc/modprobe.d/*]("http://pastebin.com/uvCdHG7d")
[cat /var/log/Xorg.0.log]("http://pastebin.com/dVQhtCVQ")

I don't know how useful can be this log, since it seems to be about this session, with none of the packages installed.

pipe the output to pastebinit

[https://help.ubuntu.com/community/Pastebinit](https://help.ubuntu.com/community/Pastebinit)

sudo apt-get install pastebinit
```
cat /etc/modprobe.d/* | pastebinit
```

copy the url
paste it on this site

I am just searching for things that went wrong, but without info, then I will not be able to diagnose it.

 Or you can try using the nouveau driver

Go to your /etc/modprobe.d/blacklist.conf
comment out lines that has
```
blacklist nouveau
```
to
```
#blacklist nouveau
```

add 
```
blacklist nvidia-current 
blacklist nvidiafb
```

---

### Post by MFH86 on 2012-05-21
[cat /etc/modprobe.d/*]("http://paste.ubuntu.com/999313")
[cat /var/log/Xorg.0.log]("http://paste.ubuntu.com/999318")
I checked the time in the log, it's about the last session, where the 3 packages were installed.

lspci -nnk:
```
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: agpgart-intel
00:01.0 PCI bridge [0604]: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port [8086:0101] (rev 09)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: i915
    Kernel modules: i915
00:16.0 Communication controller [0780]: Intel Corporation 6 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
00:1a.0 USB Controller [0c03]: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 6 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 3 [8086:1c14] (rev b4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 [8086:1c16] (rev b4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge [0601]: Intel Corporation HM65 Express Chipset Family LPC Controller [8086:1c49] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel modules: iTCO_wdt
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series Chipset Family SMBus Controller [8086:1c22] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel modules: i2c-i801
01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:0df4] (rev ff)
02:00.0 Ethernet controller [0200]: Atheros Communications Device [1969:1083] (rev c0)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: atl1c
    Kernel modules: atl1c
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e034]
    Kernel driver in use: ath9k
    Kernel modules: ath9k
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: rts_pstor
    Kernel modules: rts_pstor
04:00.1 SD Host controller [0805]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:5209]
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
05:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci-hcd
```

In detail:
```
01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:0df4] (rev ff)
```

To try the nouveau driver, how can I enable it? It's sufficient to just blacklist nvidia-current and nvidiafb? Because now there is no driver active.

---

### Post by idoitprone on 2012-05-22
> **MFH86 said:**
> [cat /etc/modprobe.d/*]("http://paste.ubuntu.com/999313")
[cat /var/log/Xorg.0.log]("http://paste.ubuntu.com/999318")
I checked the time in the log, it's about the last session, where the 3 packages were installed.

lspci -nnk:
```
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: agpgart-intel
00:01.0 PCI bridge [0604]: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port [8086:0101] (rev 09)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: i915
    Kernel modules: i915
00:16.0 Communication controller [0780]: Intel Corporation 6 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
00:1a.0 USB Controller [0c03]: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 6 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 3 [8086:1c14] (rev b4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 [8086:1c16] (rev b4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge [0601]: Intel Corporation HM65 Express Chipset Family LPC Controller [8086:1c49] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel modules: iTCO_wdt
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series Chipset Family SMBus Controller [8086:1c22] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel modules: i2c-i801
01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:0df4] (rev ff)
02:00.0 Ethernet controller [0200]: Atheros Communications Device [1969:1083] (rev c0)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: atl1c
    Kernel modules: atl1c
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e034]
    Kernel driver in use: ath9k
    Kernel modules: ath9k
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: rts_pstor
    Kernel modules: rts_pstor
04:00.1 SD Host controller [0805]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:5209]
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
05:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci-hcd
```In detail:
```
01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:0df4] (rev ff)
```To try the nouveau driver, how can I enable it? It's sufficient to just blacklist nvidia-current and nvidiafb? Because now there is no driver active.

remove bumblebee-nvidia package

and go though 
/etc/modprobe.d/blacklist.conf

to confirm that
blacklist nouveau 
line does not exist

when bbswitch is working then it shouldnt have a kernel module loaded
like i said
```
cat /proc/acpi/bbswitch 
```should tell if its on or off

If you want to use your nvidia card
it simple
open a terminal
```
optirun programName
```
this will use the kernel module to turn on your card just for this program.

I am trying to decipher your xorg, but I do not know what is going on
looks pretty normal

---

### Post by MFH86 on 2012-05-22
Ok, now it works!

I have to say that it's not possible to install only bumblebee and bbswitch, I had to install also bumblebee-nvidia (it's required) and then remove it after the installation.

The nvidia card is off and the temperature drops slowly. Right now it's around 55°C. I'll wait until it's stable to call the problem solved.

I think it's time to go deeper in the knowlegde of ubuntu, I'm not used to feel like a newbie. :)

Thanks a lot for the help! I just hope that now the computer can resist better some hours of calculation.

---

### Post by MFH86 on 2012-05-22
Last update: at "rest" the computer temperature is around 48°C, in 4 minutes at full power it goes up to 90°C with fan and cooling board off, then the fan starts. With the cooling board on the temperature oscillates between 70 and 80°C, which is below the "underclock zone".
I'll look if I can switch the fan on before the temperature rises to 90°C, but the general problem is solved!

Thanks a lot!

---

### Post by MFH86 on 2013-02-26
Saldy, after less than a year I'm back with more problems. :(
Just yesterday everything was fine, the graphic card was off by default and I could start using the GPU with optirun. There are two main differences between the current and past situation: I now use Ubuntu 12.04 and, in order to use optirun, I couldn't remove the package bumblebee-nvidia.
What I did when I installed ubuntu 12.04:
```
sudo add-apt-repository ppa:bumblebee/stable
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install bumblebee bumblebee-nvidia bbswitch-dkms
```
After this, running
```
cat /proc/acpi/bbswitch
```
returned OFF and
```
lspci -nnk
```
returned that no driver was in use for the graphic card (see previous posts for a precise output)
I used optirun yesterday, so I'm sure everything was fine (I check before and after the use of optirun to see if the graphic card is off).
This morning I installed the updates and after a few minutes the fan began to spin wildly. Running the two lines written here above yelds:
```
$ cat /proc/acpi/bbswitch 
0000:01:00.0 ON
```
```
$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: agpgart-intel
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port [8086:0101] (rev 09)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: i915
    Kernel modules: i915
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: mei
    Kernel modules: mei
00:1a.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 [8086:1c14] (rev b4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 [8086:1c16] (rev b4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge [0601]: Intel Corporation HM65 Express Chipset Family LPC Controller [8086:1c49] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel modules: iTCO_wdt
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel modules: i2c-i801
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108 [GeForce GT 540M] [10de:0df4] (rev a1)
    Subsystem: Acer Incorporated [ALI] Device [1025:0550]
    Kernel modules: nvidia, nouveau, nvidiafb
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: atl1c
    Kernel modules: atl1c
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e034]
    Kernel driver in use: ath9k
    Kernel modules: ath9k
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader [10ec:5209] (rev 01)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: rts_pstor
    Kernel modules: rts_pstor
04:00.1 SD Host controller [0805]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader [10ec:5209] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader [10ec:5209]
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
05:00.0 USB controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:054f]
    Kernel driver in use: xhci_hcd
```
In detail:
```
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108 [GeForce GT 540M] [10de:0df4] (rev a1)
    Subsystem: Acer Incorporated [ALI] Device [1025:0550]
    Kernel modules: nvidia, nouveau, nvidiafb
```
(If everything works correctly only the first line should appear.)
I tried to find the problem, this is where I looked:
```
$ optirun -vv firefox
[ 2240.108111] [DEBUG]Reading file: /etc/bumblebee/bumblebee.conf
[ 2240.108980] [ERROR]The Bumblebee daemon has not been started yet or the socket path /var/run/bumblebee.socket was incorrect.
[ 2240.109048] [DEBUG]Socket closed.
[ 2240.109096] [ERROR]Could not connect to bumblebee daemon - is it running?
```
```
$ sudo bumblebeed -vv
[ 2270.845042] [DEBUG]Found card: 01:00.0 (discrete)
[ 2270.845074] [DEBUG]Found card: 00:02.0 (integrated)
[ 2270.845085] [DEBUG]Reading file: /etc/bumblebee/bumblebee.conf
[ 2270.845458] [DEBUG]Process /sbin/modprobe started, PID 6598.
[ 2270.845543] [DEBUG]Hiding stderr for execution of /sbin/modprobe
[ 2270.846778] [DEBUG]SIGCHILD received, but wait failed with No child processes
[ 2270.847040] [DEBUG]Process /sbin/modprobe started, PID 6599.
[ 2270.847090] [DEBUG]Hiding stderr for execution of /sbin/modprobe
[ 2270.849457] [DEBUG]SIGCHILD received, but wait failed with No child processes
[ 2270.849600] [DEBUG]bbswitch has been detected.
[ 2270.849614] [INFO]Switching method 'bbswitch' is available and will be used.
[ 2270.849626] [DEBUG]Active configuration:
[ 2270.849635] [DEBUG] bumblebeed config file: /etc/bumblebee/bumblebee.conf
[ 2270.849646] [DEBUG] X display: :8
[ 2270.849655] [DEBUG] LD_LIBRARY_PATH: 
[ 2270.849664] [DEBUG] Socket path: /var/run/bumblebee.socket
[ 2270.849673] [DEBUG] pidfile: /var/run/bumblebeed.pid
[ 2270.849683] [DEBUG] xorg.conf file: /etc/bumblebee/xorg.conf.DRIVER
[ 2270.849692] [DEBUG] ModulePath: 
[ 2270.849701] [DEBUG] GID name: bumblebee
[ 2270.849711] [DEBUG] Power method: auto
[ 2270.849720] [DEBUG] Stop X on exit: 1
[ 2270.849729] [DEBUG] Driver: 
[ 2270.849738] [DEBUG] Driver module: 
[ 2270.849747] [DEBUG] Card shutdown state: 1
[ 2270.849757] [ERROR]Invalid configuration: no driver configured.
```
As far as I understand, bumblebee can't find a driver. How can I suggest him where to look? (If that's the problem, there is a not negligible possibility that I watched in the wrong direction.)

---

### Post by MFH86 on 2013-02-26
Some updates: if I run
```
sudo bumblebeed -vv --driver nvidia
```or
```
sudo bumblebeed -vv --driver nouveau
```it writes:
```
[  402.080555] [DEBUG]Found card: 01:00.0 (discrete)
[  402.080636] [DEBUG]Found card: 00:02.0 (integrated)
[  402.080673] [DEBUG]Reading file: /etc/bumblebee/bumblebee.conf[COLOR=Red]
[  402.081396] [DEBUG]Skipping auto-detection, using configured driver 'nvidia'[/COLOR]
[  402.081629] [DEBUG]Process /sbin/modprobe started, PID 3036.
[  402.081769] [DEBUG]Hiding stderr for execution of /sbin/modprobe
[  402.084856] [DEBUG]SIGCHILD received, but wait failed with No child processes
[  402.085007] [DEBUG]bbswitch has been detected.
[  402.085022] [INFO]Switching method 'bbswitch' is available and will be used.
[  402.085038] [DEBUG]Active configuration:
[  402.085047] [DEBUG] bumblebeed config file: /etc/bumblebee/bumblebee.conf
[  402.085058] [DEBUG] X display: :8
[COLOR=Red] [  402.085067] [DEBUG] LD_LIBRARY_PATH: /usr/lib/nvidia-current:/usr/lib32/nvidia-current[/COLOR]
[  402.085077] [DEBUG] Socket path: /var/run/bumblebee.socket
[  402.085087] [DEBUG] pidfile: /var/run/bumblebeed.pid
[  402.085097] [DEBUG] xorg.conf file: /etc/bumblebee/xorg.conf.nvidia
[COLOR=Red] [  402.085106] [DEBUG] ModulePath: /usr/lib/nvidia-current/xorg,/usr/lib/xorg/modules[/COLOR]
[  402.085117] [DEBUG] GID name: bumblebee
[  402.085126] [DEBUG] Power method: auto
[  402.085135] [DEBUG] Stop X on exit: 1
[COLOR=Red][  402.085145] [DEBUG] Driver: nvidia
[  402.085155] [DEBUG] Driver module: nvidia-current[/COLOR]
[  402.085164] [DEBUG] Card shutdown state: 1
[COLOR=Red][  402.085365] [DEBUG]Process /sbin/modprobe started, PID 3037.
[  402.085471] [DEBUG]Hiding stderr for execution of /sbin/modprobe
[  402.088426] [DEBUG]SIGCHILD received, but wait failed with No child processes
[  402.088465] [ERROR]Module 'nvidia-current' is not found.[/COLOR]
```resp. for nouveau:
```
[  820.436151] [DEBUG]Found card: 01:00.0 (discrete)
[  820.436167] [DEBUG]Found card: 00:02.0 (integrated)
[  820.436171] [DEBUG]Reading file: /etc/bumblebee/bumblebee.conf
[COLOR=Red][  820.436368] [DEBUG]Skipping auto-detection, using configured driver 'nouveau'[/COLOR]
[  820.436394] [DEBUG]bbswitch has been detected.
[  820.436398] [INFO]Switching method 'bbswitch' is available and will be used.
[  820.436401] [DEBUG]Active configuration:
[  820.436404] [DEBUG] bumblebeed config file: /etc/bumblebee/bumblebee.conf
[  820.436407] [DEBUG] X display: :8
[  820.436410] [DEBUG] LD_LIBRARY_PATH: 
[  820.436412] [DEBUG] Socket path: /var/run/bumblebee.socket
[  820.436415] [DEBUG] pidfile: /var/run/bumblebeed.pid
[  820.436418] [DEBUG] xorg.conf file: /etc/bumblebee/xorg.conf.nouveau
[  820.436421] [DEBUG] ModulePath: 
[  820.436423] [DEBUG] GID name: bumblebee
[  820.436426] [DEBUG] Power method: auto
[  820.436429] [DEBUG] Stop X on exit: 1
[COLOR=Red][  820.436432] [DEBUG] Driver: nouveau
[  820.436434] [DEBUG] Driver module: nouveau[/COLOR]
[  820.436437] [DEBUG] Card shutdown state: 1
[COLOR=Red][  820.436513] [DEBUG]Process /sbin/modprobe started, PID 3056.
[  820.436538] [DEBUG]Hiding stderr for execution of /sbin/modprobe
[  820.437479] [DEBUG]SIGCHILD received, but wait failed with No child processes
[  820.437512] [ERROR]Module 'nouveau' is not found.[/COLOR]
```(In red the differences between these outputs and the one from the previous post.)

nvidia-current is blacklisted in /etc/modprobe.d/blacklist.conf:
```
blacklist nvidia-current 
blacklist nvidiafb
```but until yesterday this wasn't a problem. I already tried to comment the first of these two lines, the problem won't go away.
It seems there is a problem in the location of drivers, but that's as far as I can go. I hope the problem  isn't too new to find a solution around the web, but until now every search gave no useful result.

Edit: I forgot to tell that my graphic card is an nvidia geforce GT 540M, everything else is on the first post.

---

