---
title: "running out of space"
date: 2008-09-09
forum: General Help
---

### Post by majikhotline on 2008-09-09
Hello Ubuntu country,
Im running out of space, is there a way to compress my HD or defrag it to allow more space, or where or how do i clean the junk files.

---

### Post by iaculallad on 2008-09-09
> **majikhotline said:**
> Hello Ubuntu country,
Im running out of space, is there a way to compress my HD or defrag it to allow more space, or where or how do i clean the junk files.

Try cleaning your cache:

```
sudo apt-get clean
sudo apt-get autoclean
```

You may want to delete the *.bak files in your /boot folder too.

```
sudo rm /boot/*.bak
```

---

### Post by tuxxy on 2008-09-09
You may need to delete some of your root trash, open a terminal and type

```
gksudo nautilus /root/.local/share/Trash

```

[http://www.ubuntugeek.com/how-to-empty-root-trash.html](http://www.ubuntugeek.com/how-to-empty-root-trash.html)

---

### Post by majikhotline on 2008-09-12
i did the autoclean and it clean a little too much....i have to reconfigure synergy...it erased the conf file lol

---

### Post by Sef on 2008-09-13
Also there is ```
sudo apt-get autoremove
```.

---

### Post by Herman on 2008-09-13
:) You could take a look in your /boot directory and see how many vmlinuz's and initrd.img files you have in there.
The Linux kernel is called vmlinuz and the initrd.img file is the initial ramdisk. You don't really need the old ones if your system is working okay on the most recent pair.

You can uninstall them by opening Synaptic Package Manager, click the 'status' button in the lower left corner, and then choose 'Installed' in the left-hand pane.
In the right-hand pane, you can then scroll down the list of installed software in your system until you come to something that looks like 'linux-image-2.6.24-10-generic'.

I have a whole list of them, as follows,
linux-image-2.6.24-10-generic
linux-image-2.6.24-11-generic
linux-image-2.6.24-12-generic
linux-image-2.6.24-14-generic
linux-image-2.6.24-15-generic
linux-image-2.6.24-16-generic
linux-image-2.6.24-18-generic
linux-image-2.6.24-19-generic
linux-image-2.6.24-2.3-generic
linux-image-2.6.24-7.12-generic
linux-image-2.6.24-8.14-generic

Now, take a look at your /boot/grub/menu.lst file to see which kernel GRUB is booting, 
```
gksudo gedit /boot/grub/menu.lst
```Mine contains the following booting stanza at the top of the list for Ubuntu,
```
title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=6178d387-9ab5-4f23-a56d-8e0cba0addc3 ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic
quiet
``` I have a whole list of those that are messing up my grub menu, and I can delete most of those while I'm in here. I don't want to see them.
I just leave the top two, my normal boot and recovery mode for the latest kernel, and delete all the way down to the memtest86+ entry.

Back in Synaptic Package Manager, **I can uninstall all except my linux-image-2.6.24-19-generic kernel.**
To uninstall a kernel, select that line in the right-hand pane in Synaptic, and right-click on it and choose 'mark for removal'. (I'm not sure if it's better to select 'mark for removal', or 'mark for complete removal' actually).
Confirm it and click 'Apply'
After you click 'Apply', you'll see how much disk space you will free, 67.8 MB for one kernel and initrd.img and associated files, for example.

If you want to select a whole bunch of them at a time, use your shift key after you select one at the top of the list and and select one at the bottom of the list while holding your shift key down, to highlight the top, bottom and all in between.

In my case I will be removing 30 packages and freeing 1216 MB of hard disk space. That's over 1 GB isn't it? I think 1024 MB = 1.0GB.

**Before**
According to the output from the df -h command, I had 
```
Filesystem               Size    Used    Avail   Use%    Mounted on
/dev/sda3                21G    13G      7.2G    64%      /
```**After**
According to the output from the df -h command, I now have only,
```
Filesystem               Size    Used    Avail   Use%    Mounted on
/dev/sda3                21G    11G      8.5G    57%      /
```Regards, Herman :)

EDIT, here are a few links that explain how to do just about the same thing but in slightly different ways,
[Remove Ubuntu Kernels You Don't Need]("http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/") - Tombuntu,  
[Removing Those Extra Kernels in Ubuntu]("http://www.alterego7.com/2008/04/removing-those-extra-kernels-in-ubuntu.html") -Alter Ego, 
[How to: Linux delete or remove kernel]("http://www.cyberciti.biz/faq/debian-redhat-linux-delete-kernel-command/") - Nixcraft, and, 
[Remove Old Kernel From Ubuntu]("http://sandakith.wordpress.com/2007/11/25/remove-the-old-kernel-from-ubuntu/") - Lahiru Sandakith&#8217;s Web Log.

---

### Post by flabdablet on 2008-09-13
Before you go in boots and all cleaning out "junk" files, have a look at your disk with Applications->Accessories->Disk Usage Analyzer and see what's actually chewing up the space.  There's a fair chance that you will find one large file you've forgotten about, getting rid of which will free up more space than an hour's worth of random junk deletion.

---

### Post by todak on 2008-09-13
Move all of your multimedia files to another drive or archive them on DVD. I'll bet THAT will give you a lot of space back! :lolflag:

---

