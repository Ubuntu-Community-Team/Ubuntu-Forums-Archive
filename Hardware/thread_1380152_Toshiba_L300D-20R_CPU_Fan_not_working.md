---
title: "Toshiba L300D-20R CPU Fan not working"
date: 2010-01-13
forum: Hardware
---

### Post by kelldownie on 2010-01-13
Im running 9.10, theres a fix for 9.04 however this involves editing a file /boot/gedit/menu.lst which doesnt appear to exist in 9.10(just appears as a blank document) whereas  there should be some text which needs changing

---

### Post by ajgreeny on 2010-01-13
9.10 uses grub2, which is very different in its workings to legacy grub in 9.04 that used the menu.lst.

Depending on what you want to do, I am certain it can be done by editing one of the files in /etc/grub.d, probably 40_custom, but we need to know more about your needs, and what you had to do in legacy grub to get things working properly, in order to tell you how to proceed.

---

### Post by kelldownie on 2010-01-13
title  Ubuntu 9.04, kernel 2.6.28-11-generic
uuid  a91f7379-e93b-490c-b541-0681173bccc2
kernel  /boot/vmlinuz-2.6.28-11-generic root=UUID=a91f.. ro quiet splash **acpi_osi="Linux"**
initrd  /boot/initrd.img-2.6.28-11-generic
quiet

whats in bold is the change made in order to make the fan work, not sure what the original would be

---

### Post by ajgreeny on 2010-01-13
You probably need to edit the 40_custom file as I mentioned before.

Firstly copy the first entry paragraph in your **/boot/grub/grub.conf** file which should look something like this below.

```
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 499975f7-bef1-4de5-9b9d-da96c1bd6c9f
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=499975f7-bef1-4de5-9b9d-da96c1bd6c9f ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
```  Make sure you get everything from the word "menuentry" down to the } bracket.

Now past that into the **/etc/grub.d/40_custom** file, but add the **acpi_osi="Linux"** at the end of the line that ends **quiet splash** again just like before.  Now save that 40_custom file as 06_custom and make it executable.  Finally run ```
update-grub
``` in terminal

That should do it for you.  Good luck.

---

### Post by kelldownie on 2010-01-13
Thanks, but im having a little problem saving the file as 06_custom as i 'dont have the necessary permissions'

---

### Post by ajgreeny on 2010-01-14
The easiest way to do this is to either use ```
gksudo nautilus
```in a terminal, and then open the file from that file manager window, which will now give you root privileges

Alternatively you can install **nautilus-gksu** from synaptic.  You will then be able to open any file by right clicking on it in nautilus and choosing "Open as administrator"

You can not simply edit any file from the linux filesystem as a normal user, only using root privileges.  That is one of the many great strengths of the linux operating system, so though it may appear a nuisance, it is something to be thankful for.

---

