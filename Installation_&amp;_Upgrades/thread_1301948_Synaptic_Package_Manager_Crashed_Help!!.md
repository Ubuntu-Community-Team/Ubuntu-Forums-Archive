---
title: "Synaptic Package Manager Crashed Help!!"
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by Wazz72 on 2009-10-26
Can Anyone please help me.
My Synaptic Package Manager crashed whilst installing some software, every time I start it I get  the following error in a msg box ' E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. '

i have tried 
sudo dpkg --configure -a

and I get the folowing:

Setting up initramfs-tools (0.92bubuntu29) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.28-16-server
cpio: ./bin/udevinfo: Function stat failed: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.28-16-server
dpkg: subprocess post-installation script returned error exit status 1

can someone please help,  I dont want to reinstall Ubuntu.

---

### Post by dstew on 2009-10-26
See [this thread]("http://ubuntuforums.org/showthread.php?t=1206227") about a dpkg bug that can cause something like your problem. My post near the end of the thread has a fixed that sometimes works.

---

### Post by Wazz72 on 2009-10-27
Thanks, Tried it and it wouldnt work.

---

### Post by dstew on 2009-10-27
Check to see if you have a /bin/udevinfo folder. The script is running a command  that is looking for this file under its current directory. If you have a /bin/udevinfo file, but are running dpkg from a different directory than root, maybe it can't find that folder. Make sure you are in the root directory when you run dpkg.

---

### Post by Wazz72 on 2009-10-27
I have the directory, but there is nothing in it?

---

### Post by dstew on 2009-10-28
Did you run the dpkg command from the root directory '/' ? I assume you did, and it still does not work. I am pretty sure this is the [bug that is caused by the depmod program]("https://bugs.launchpad.net/ubuntu/+source/isdnutils/+bug/346909"). This program works with the kernel modules (like drivers) and is used when a kernel is upgraded, or removed. It pops up when the postremoval scripts are run. Apparently, if there is a corrupt module present, depmod crashes when it encounters the module. It should not do this. Apparently this depmod bug has been fixed with 9.10, but can pop up with earlier versions. The official workaround is to uninstall your kernel, and all the kernel modules, then re-install the kernel and modules. Supposedly then the corrupt module is replaced. I am not sure this will work in your case. You can try it though. ```
sudo apt-get remove linux-image-2.6.28-16-server
sudo rm -rf /lib/modules/2.6.28-16-server
sudo apt-get install linux-image-2.6.28-16-server
```

I don't know if you have actually installed the 2.6.28-16 kernel. Check the output of ```
uname -r
```to see what kernel you are actually running. Whatever answer it is, use that instead of 2.6.28-16-server in the above commands.

Usually this depmod bug pops up when the postremoval scripts are being run after a kernel upgrade. These scripts are in the /var/lib/dpkg/info directory, and have the .postrm extension.

I am going partly from the experiences documented in [this thread]("http://ubuntuforums.org/archive/index.php/t-1147434.html") now.

One poster in that thread found that creating a /usr/bin/udevinfo directory got rid of the error, but there is no explanation why.

I like the approach of another poster, who used the output of the command```
sudo dpkg --audit
```to guide a workaround for this bug that essentially bypasses the postremoval scripts that create this problem. He identified the postremoval scripts that were associated with the problem packages, renamed them by adding a .bak extension, and then did dpkg --remove -a, and it worked.

That pretty much exhausts all my thoughts on your problem. Hope you can get straightened out.

---

### Post by sausageandeggs on 2009-11-06
Hi, I know this threads a  little old but wanted to say thanx & post in case anyone else gets stuck and because the other member didn't say if they resolved the issue or not.

I had a very similar problem with apt-get/synaptic after installing software (half installed initramfs-tools, apt-get stuck, "apt-get configure -a" not fixing prob) and after reading through post #5 etc. was able to fix the issue.

What i did
```

sas@simon / $** dpkg -C**
The following packages are only half configured, probably due to problems
configuring them the first time. The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
initramfs-tools      tools for generating an initramfs

sas@simon / $** sudo dpkg --remove --pending**
sas@simon / $ **sudo mkdir /usr/bin/udevinfo**
sas@simon / $** sudo dpkg --configure -a**
Setting up initramfs-tools (0.92bubuntu29) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.28-15-generic
sas@simon / $
  
```So thanks dstew for pointing me in the right direction.

---

