---
title: "Reinstall - What to backup"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by neilneil2000 on 2009-02-10
Hi all,

I have a media server that I have been playing with for a long time, currently running Mythbuntu.  I have had a few issues so want to replace it with Ubuntu Server Edition.  My question is this:  What should I backup?

I'm not worried about keeping the packages I have although I realise I can get a list from apt-get and restore this later.  Its more the configuration I am interested in.

Obviously /etc holds most of the config files, is it worth backing up the whole directory or should I be more specific?

Are there any other config files I should be aware of.

Another thing is that support for my hardware is working in 2.6.27-7-generic, but nothing later.  So I need to ensure I use this kernel in the next installation.  How would I go about this?  Can I just back up /boot and replace it on the new machine?

Any input would be welcome

---

### Post by zazake on 2009-02-10
Hi,
The whole of /etc is worth backing up as it is not very big. You should probably also backup files in /var such as /var/mail, /var/log, /var/lib/mysql which contains the mythtv database... And /home of course as users' directory also contain config files.

> Can I just back up /boot and replace it on the new machine?

If you mean you want to install with a later kernel and then replace the kernel file in /boot with an older one I guess it is a very bad idea as the kernel depends on many other files elsewhere in the filesystem. It really must be installed properly.

---

### Post by neilneil2000 on 2009-02-11
Thanks very much.

How do I go about downgrading the Kernel if I install a newer one first?  I assume there is some kind of process.

If you know a console approach that would be best.

---

### Post by zazake on 2009-02-13
Install it from the repositories :
```
sudo apt-get install linux-image-2.2.27-7-generic linux-headers-2.6.27-7-generic
```
This should install the new kernel image in /boot and automatically update your menu.lst file.
Then you must select that kernel as your default kernel :
```
sudo gedit /boot/grub/menu.lst
```
Look for the entry that looks like this (root and uuid will be different)

```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.27-7-generic root=UUID=243505a2-d5b8-4c53-8c87-e058d615f61b ro splash 
initrd		/initrd.img-2.6.27-7-generic
quiet
```
Now you can either move that whole paragraph to the top of the list of entries, just under the line that says :
```
## ## End Default Options ##
```
Or you count how many entries there are for kernels between "## ## End Default Options ##"and the 2.6.27-7-generic one.
You then go up in the file and look for the line :
```
default		0
```
And you change "0" to whatever the position of your kernel in the list is (you must start counting from 0).
Be careful when editing that file.

---

