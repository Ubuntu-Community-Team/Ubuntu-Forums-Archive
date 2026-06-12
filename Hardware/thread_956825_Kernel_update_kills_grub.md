---
title: "Kernel update kills grub"
date: 2008-10-23
forum: Hardware
---

### Post by SyCo123 on 2008-10-23
Laptop is an HP DV5215us that works fine now but every Kernel update wipes Grub and I have to go edit the boot/grub/menu.lst (I'm remembering where it is but on a Windows PC art work so location might not be correct)

Ubuntu 7.10 went on first over the old Win Media Edition wiping it and being the only OS on the computer. Then because I simply wanted to watch netflix I had to install an entire other operating system for that pleaure (XP pro). So I had to move Ubuntu off the start of the drive because poor old windows just has to be first. So now kernel updates kill my grub script and I have to manually edit it each time. Bit of a pain but no big problem for me. I would imagine it would be beyond a total noob and their PC would effectively be bricked until they can boot it. 

Just thought I'd throw it out there in case it's not a well known problem.

The fix is simply editing line for hda(0,0) to the new partition location, in my case hda(0,1) (I think) and adding the windows boot option again. Of course I have a back up of the file before doing the update now. It's all a bit of a pain though. (still on 7.10, stable and happy)

---

### Post by tCarls on 2008-10-23
I have the same problem with a Dell Inspiron 1525n. It was a well known problem when Dell started preloading Ubuntu. I was under the impression it was Dell specific, but apparently not.

I haven't found a solution. It's not hard to change the partition lines every few months so I just deal with it.

---

### Post by caljohnsmith on 2008-10-23
I think the solution for both of you might be really easy. If you open up your menu.lst, you'll see a line that says:
```
# groot=(hdX,Y)
```
Where X and Y are numbers. That is the line that the "update-grub" script uses to figure out which partition Ubuntu is on, and update-grub is run every time you get a new kernel. Therefore, probably that line has the wrong partition for your Ubuntu, and all you need to do is change it. Another line to check would be:
```
# kopt=root=UUID=77677cb5-6e56-4936-a373-80c15de06bca ro
```
Make sure that line has the correct UUID for your Ubuntu partition. You can find the Ubuntu partition UUID by doing:
```
sudo blkid
```
Once you have those lines correct in your menu.lst, then run:
```
sudo update-grub
```
And you should see that all your Ubuntu entries will now use whichever partition you specified with the groot line and the UUID you specified with the kopt line. Let me know if that works for you. :)

---

### Post by plucky on 2008-10-23
> **SyCo123 said:**
> Laptop is an HP DV5215us that works fine now but every Kernel update wipes Grub and I have to go edit the boot/grub/menu.lst (I'm remembering where it is but on a Windows PC art work so location might not be correct)

Ubuntu 7.10 went on first over the old Win Media Edition wiping it and being the only OS on the computer. Then because I simply wanted to watch netflix I had to install an entire other operating system for that pleaure (XP pro). So I had to move Ubuntu off the start of the drive because poor old windows just has to be first. So now kernel updates kill my grub script and I have to manually edit it each time. Bit of a pain but no big problem for me. I would imagine it would be beyond a total noob and their PC would effectively be bricked until they can boot it. 

Just thought I'd throw it out there in case it's not a well known problem.

The fix is simply editing line for hda(0,0) to the new partition location, in my case hda(0,1) (I think) and adding the windows boot option again. Of course I have a back up of the file before doing the update now. It's all a bit of a pain though. (still on 7.10, stable and happy)

When the new kernel is installed,it uses the options in menu.lst to rebuild the boot menu.So if you edit menu.lst and search for and  change ```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)
```
the groot line to what it should be,then when the kernel is updated,the correct information is put into the grub root line.

P.s. Do not remove the # from the line when you edit it.

Good Luck

---

