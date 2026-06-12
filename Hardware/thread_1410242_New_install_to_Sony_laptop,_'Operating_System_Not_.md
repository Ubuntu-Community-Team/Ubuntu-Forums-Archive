---
title: "New install to Sony laptop, 'Operating System Not Found'"
date: 2010-02-18
forum: Hardware
---

### Post by shooglebun on 2010-02-18
We just downloaded the .iso for ubuntu and burned it to a CD.
Went through the complete install, restarted computer and all we get is 'Operating System Not found'
Tried it all again with same result.
The Sony is probably 6 or 7 years old, h/d about 80 g, ram 1g

With some other help did the following:

Booted up on clean CD
> to terminal mode
>     did     sudo su
                 fdisk -l
                 (partition 1 for ubuntu, 5 for swap)
                 
                  mkdir /mnt/sda1
                  mount /dev/sda1 mnt/sda1
                  chroot /mnt/sda1
                  grub-install /dev/sda
         Here's where I get a message that the fundtion did not take (forgot to write it down)

Tried this all over again with same results and am now stuck as to what to do next.

= This was a clean reformat of the drive that had WinXP Pro on it
= Also  it still comes up with the SONY logo on screen before loading; do they have a hook in the BIOS, maybe!

thanks            s-bun

---

### Post by ubuwatson on 2010-02-18
> **shooglebun said:**
> We just downloaded the .iso for ubuntu and burned it to a CD.
Went through the complete install, restarted computer and all we get is 'Operating System Not found'
Tried it all again with same result.
The Sony is probably 6 or 7 years old, h/d about 80 g, ram 1g

With some other help did the following:

Booted up on clean CD
> to terminal mode
>     did     sudo su
                 fdisk -l
                 (partition 1 for ubuntu, 5 for swap)
                 
                  mkdir /mnt/sda1
                  mount /dev/sda1 mnt/sda1
                  chroot /mnt/sda1
                  grub-install /dev/sda
         Here's where I get a message that the fundtion did not take (forgot to write it down)

Tried this all over again with same results and am now stuck as to what to do next.

= This was a clean reformat of the drive that had WinXP Pro on it
= Also  it still comes up with the SONY logo on screen before loading; do they have a hook in the BIOS, maybe!

thanks            s-bun

Sorry if this is an obvious question (and yes I have been guilty of this myself), but is there any external drives, thumb drives, memory sticks or the like installed ?

I myself have had not too much luck with older Sony laptops, their very proprietary and even finding Windows drivers for them is difficult.

---

### Post by shooglebun on 2010-02-18
No external drive or any of the above!

---

### Post by Seq on 2010-02-18
> **shooglebun said:**
>                   grub-install /dev/sda
         Here's where I get a message that the fundtion did not take (forgot to write it down)

The error message you receive when trying to install grub is somewhat important in debugging why grub can not be installed.

---

### Post by shooglebun on 2010-02-18
To 'seq' and 'ubuWatson'
My instruction was to create a mounting point, mount the partition then change root into the installed ubuntu on the hard drive.  I understood that the grub-install is to place Grub inside the MBR....then 'exit' back to the Cd

Here is the response after the 'grub-install':

No path or device specified
Try ``grub-probe ---help'' for more information
Auto-detection of file system module failed
Please specify the module with the option  1 --modules' explicitly

..then it's back to the command line
rook@ubunto:/#

Actually this is all new to me so I'm asking for  any direction.  Sure would like to get this laptop working for my wife with ubuntu on it.          Thanks,

---

### Post by shooglebun on 2010-02-20
..further to ...

We went ahead and re-installed Win XP and came up with the same message on reboot!

'Operating System Not Found'   ....sheesh!

I'm thinking Sony has a hook in the BIOS or something is directing it to the wrong file on boot up.

This  is a Sony VIAO  GR370, by the way.

Searches on the internet indicate others have had problems installing Linux systems with some laptops.   still haven't found one to match this tho'

Thanks guys

---

### Post by shooglebun on 2010-02-21
Looks like I've solved the problem!
It was as simple as fixing the MBR.
After all the re-installs (Windows, ubuntu then SUSE) found that it would boot up on the .iso CD and select either Win or Linux (actually SUSE this time).
Downloaded filePhoenex WinPhlash for VIAO flashed new BIOS and now it is booting up ok from the hard drive.
Thanks to all.

---

