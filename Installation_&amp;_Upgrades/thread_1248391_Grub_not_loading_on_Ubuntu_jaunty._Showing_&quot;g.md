---
title: "Grub not loading on Ubuntu jaunty. Showing &quot;grub&gt;&quot; promt"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by ashulinux on 2009-08-24
I have Ubuntu 9.04 installed on my laptop. It was working fine till yesterday, but now when i switched on my laptop I am getting an error.
It throws a grub> promt.
Earlier it was saying "Error 15".
Grub is not getting loaded. 
I went through some of the forums but could not get a fix.

/dev/sda3 is my / partition.

Steps taken :

I booted off the live cd. 
Mounted /dev/sda3 on /mnt
mounted /dev & proc as well
when I chrooted to /mnt I again get an error -
' /bin/bash' file/directory not found

I visited this link [http://rothfuchs.net/2008/11/chroot-cannot-run-command-binbash-no-such-file-or-directory/]("http://rothfuchs.net/2008/11/chroot-cannot-run-command-binbash-no-such-file-or-directory/") but couldn't get it.

Only thing left to fix now is to get chrooted environment. After this I can install 'grub' as mentioned in this thread [http://ubuntuforums.org/showthread.php?t=922678]("http://ubuntuforums.org/showthread.php?t=922678")

Can anyone on list help me ?

---

### Post by junke1990 on 2009-08-24
looked at this?

[http://www.gentoo.org/doc/en/grub-error-guide.xml](http://www.gentoo.org/doc/en/grub-error-guide.xml)

-->
This error can occur in two different stages of the GRUB configuration, either during the initial configuration (installing GRUB in the master boot record) or after booting the system and attempting to launch Linux (or any other entry).

---

### Post by pawhtiobo on 2009-08-24
Hi :)

You can also try this **[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)** to try to fix your Grub.


see ya....

---

### Post by ashulinux on 2009-08-24
> **junke1990 said:**
> looked at this?

[http://www.gentoo.org/doc/en/grub-error-guide.xml](http://www.gentoo.org/doc/en/grub-error-guide.xml)

-->
This error can occur in two different stages of the GRUB configuration, either during the initial configuration (installing GRUB in the master boot record) or after booting the system and attempting to launch Linux (or any other entry).

Ya, I have visited this link earlier. The problem is I am not able to 'chroot' into the directory where I have mounted my / partition [/dev/sda3].

Contents of /boot are :

ubuntu@ubuntu:/mnt/boot/grub$ ls
default        fat_stage1_5       minix_stage1_5     stage2
device.map     installed-version  reiserfs_stage1_5  xfs_stage1_5
e2fs_stage1_5  jfs_stage1_5       stage1

Earlier there was nothing inside /boot directory. I did a grub-install to get the above contents.All I need is a menu.lst for which I need to do apt-get install grub.

Also, None of the partitions have error !

I am not able to source out where am I wrong. :-(

---

### Post by ajgreeny on 2009-08-24
Have you tried reinstalling grub with the live CD?  If not give it a go, it may not sort the problem, but it's got to be worth trying.
Boot into the ubuntu live CD
open a terminal and run :
    ```
sudo grub
```This gets you to a simple grub command line.
Then:
    ```
find /boot/grub/stage1
```This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. If you have more than one linux install you may get more than one answer here.  Use the one from which you want to use grub.  Replace the question marks in the following command with the output of the this last command :
    ```
root (hd?,?)
```[like : root (hd0,1) ,probably]
then:
    ```
setup (hd0)
```This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    ```
quit
```Finally reboot, and hopefully you will now have a working grub bootloader.

---

### Post by junke1990 on 2009-08-24
so the only thing you're missing is the menu.lst? you'll have to create one yourself since the grub install doesnt do that for you as far as I know.

maybe this will help 

```

title		Ubuntu karmic (development branch), kernel 2.6.31-6-generic
uuid		8a91b0a5-36bb-4eea-b638-35b4c1f7921c
kernel		/vmlinuz-2.6.31-6-generic root=UUID=a18b5bbc-97aa-41f7-ad3a-7ea979eae97b rw splash vga=771 
initrd		/initrd.img-2.6.31-6-generic
quiet

```

---

### Post by ashulinux on 2009-08-24
I have downloaded the tar-ball of SGD.I am running off live CD. USB drive is not getting detected. mount doesn't show any such device. Any idea why?

---

### Post by junke1990 on 2009-08-24
is smart boot manager an option?

---

### Post by ashulinux on 2009-08-24
> **junke1990 said:**
> so the only thing you're missing is the menu.lst? you'll have to create one yourself since the grub install doesnt do that for you as far as I know.

maybe this will help 

```

title		Ubuntu karmic (development branch), kernel 2.6.31-6-generic
uuid		8a91b0a5-36bb-4eea-b638-35b4c1f7921c
kernel		/vmlinuz-2.6.31-6-generic root=UUID=a18b5bbc-97aa-41f7-ad3a-7ea979eae97b rw splash vga=771 
initrd		/initrd.img-2.6.31-6-generic
quiet

```

uuid on the second line of code is that of /boot right ?
uuid on the third line i.e root=UUID is the one of / ?
I ran sudo blkid to get the list of UUIDs.
Correct me if I am wrong.

---

### Post by ashulinux on 2009-08-24
> **junke1990 said:**
> is smart boot manager an option?

What is that ?

---

### Post by junke1990 on 2009-08-24
should be something simular to SGB, it's in the list of unetbootin should be tool to boot too.

---

### Post by ashulinux on 2009-08-25
> **junke1990 said:**
> should be something simular to SGB, it's in the list of unetbootin should be tool to boot too.

Hey,

I was not able to recover because there was no /usr and /opt directory under the mounted partition. Probably someone would have messed up with it. 
Kernel was missing so as the initrd :-( something serious would have happened. I had /home in a different partition so I recovered my personal stuffs as well as codes but lost some virtual machines.
Re-installed Jaunty over night.

I think this thread can be closed now. Good to know some new stuffs like Unetbootin etc; THANKS everybody for your help! :-)

---

