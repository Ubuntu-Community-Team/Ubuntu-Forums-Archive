---
title: "TuxOnIce with swap partition on Sony VAIO VGN-CR320E"
date: 2008-03-20
forum: Hardware &amp; Laptops
---

### Post by MooshMoosh on 2008-03-20
hi ,

I've recently bought the vaio cr320 laptop and installed Ubuntu Gusty on it (kernel 2.6.22-r14).
It had some compatibility issues which I managed to resolve using this cool thread: [http://ubuntuforums.org/showthread.php?t=650790]("http://ubuntuforums.org/showthread.php?t=650790")

Everything but suspend/hibernate ...

I read numerous posts regarding this problem and tried them all until I've decided to compile a new kernel with TuxOnIce. 

I compiled kernel version 2.6.24 and patched it with TuxOnIce but it still doesn't work.
I followed the howto guide: [http://www.tuxonice.net/HOWTO.html]("http://www.tuxonice.net/HOWTO.html"). 
Since I have a swap partition (4GB in size), I patched in only the swapwriter.

I started my swap partition:
```

$ swapon /dev/sda7
$ swapon -s
Filename          Type           Size           Used          Priority
/dev/sda7        partition     3903752    0                -2

```

TuxOnIce parameters:
/sys/power/tuxonice/swap/enabled => > 1
/sys/power/tuxonice/swap/headerlocations => > For swap partitions, simply use the format: resume=swap:/dev/hda1.
/sys/power/tuxonice/swap/swapfilename => empty

After trying to hibernate either from the power management gnome I just receive a logon panel.
If I try the hibernate script I receive the following:
> /bin/echo: write error: Device or resource busy

I did exactly as instructed on the howto guide section for using a swap partition:
[http://www.tuxonice.net/HOWTO-7.html#swapfiles]("http://www.tuxonice.net/HOWTO-7.html#swapfiles") 

I've attached two files to this post: **/etc/fstab** and **/sys/power/tuxonice/debug_info**.

I've tried echoing "0" into swap/enabled and the hibernate behaved exactly the same.
The only difference is that the line "- SwapAllocator inactive" didn't appear in debug_info.

I'd appreciate any help, this problem frustrates me a lot!
Thanks, 
Alik

---

### Post by mariner09 on 2008-04-13
I recently did this for Hardy and it wasn't as easy as they make it on Fedora.

Nigel gave me the pointers I needed.

1st, either patch a vanilla kernel or use GIT to get a TuxOnIce patched Ubuntu kernel.

Compile.

At this point, I could hibernate, but powering on gave me the same result that you see, a normal login.

By modifying the modules file and creating the tuxonice script below, I have a working hibernate/resume.  I'm still trying to figure out the userui, but it requires a newly compiled initrd with the tuxoniceui_text binary included.  I may just forego the userui and just stick with what works while less flashy...

nigel@nigel-laptop:~$ cat /etc/initramfs-tools/modules
# List of modules that you want to include in your initramfs.
#
# Syntax:  module_name [args ...]
#
# You must run update-initramfs(8) to effect this change.
#
# Examples:
#
# raid1
# sd_mod
#
# Only needed if you build TuxOnIce as modules...
tuxonice_core
tuxonice_userui
tuxonice_block_io
tuxonice_swap
tuxonice_file
tuxonice_compress

nigel@nigel-laptop:~$ ls -al /etc/initramfs-tools/scripts/local-premount/
total 12
drwxr-xr-x  2 root root 4096 2008-03-09 18:06 .
drwxr-xr-x 11 root root 4096 2008-02-02 08:30 ..
-rwxr-xr-x  1 root root   50 2008-03-09 18:05 tuxonice
nigel@nigel-laptop:~$ cat /etc/initramfs-tools/scripts/local-premount/tuxonice
#!/bin/sh

echo 1 > /sys/power/tuxonice/do_resume

---

