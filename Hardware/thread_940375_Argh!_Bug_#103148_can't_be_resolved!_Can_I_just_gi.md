---
title: "Argh! Bug #103148 can't be resolved! Can I just give up trying to boot from an image?"
date: 2008-10-06
forum: Hardware
---

### Post by Volmarias on 2008-10-06
I am experiencing [Bug #103148]("https://bugs.launchpad.net/ubuntu/+bug/103148"). It's something I've put up with but not really tried to fix until just now.

I have done:

swapoff -a
fdisk -l to verify the right partition (it is sda6)
mkswap /dev/sda6 (got the UUID)
set /etc/fstab and /etc/initramfs-tools/conf.d/resume to use that UUID
set the last value on that line in fstab to 2
swapon -a
swapon -s (to verify)
update-initramfs -u
shutdown -r now

and, still nothing. My laptop that used to boot up in 10 seconds CONTINUES to take 3x as long as it used to, looking for a resume image that IS NOT THERE!

swapon -s shows that the UUID is in use, so I'm NOT making a mistake copying/pasting that UUID.

Well, enough! I don't care! I don't want hibernate, and I never did. How can I just prevent this from attempting to look for a resume image in the first place? I've looked at /usr/share/initramfs-tools, and NORESUME=y in there.

Hell, I've modified /etc/initramfs-tools/conf.d/resume and commented out the line, just to see what would happen. Pretty much the same thing as before, except instead of taking 20 seconds to tell me failure, it just takes 20 seconds to say nothing.

I am seriously considering just backing up everything important, reformatting my partition, and reinstalling from a boot disk.

Can anyone suggest something else I can try, before I go completely bonkers?

---

