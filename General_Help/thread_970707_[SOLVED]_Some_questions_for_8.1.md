---
title: "[SOLVED] Some questions for 8.1"
date: 2008-11-04
forum: General Help
---

### Post by qwe99 on 2008-11-04
I install the Ubuntu 8.1. I use windows xp when I can not do something in UBuntu. But now my windows xp has crashed (like always). But &#305; can not format it because I worried about mbr. I don't know the command to insatll the mbr for me. I search on the internet but the commands are seperate for every different partitions. Can you tell what should I write to terminal after I format windowsxp ?
My partitions are here : 
sda1 ntfs (windows)
sda5 ntfs (my documents)
sda6 swap
sda8 /data
sda7 /

 I want ask some more questions. In the other forum, the users told me that my files which are in /data, are not deleting when I format the sda7 ( "/" ). That is true ?:confused:

Also I have a problem when I close Ubuntu. After the orange bar is finished, the screen turning black and waiting 20-25 seconds with a white line ( - ) which is flashing (like in terminal) . After 20-25 seconds, it writes "acipid exiting", and after 3-4 seconds it rights some numbers (like ip [57843548874] (I don't remember now) ) and "power down" and when the computer closing ... :( It is very bad to waiting for it. What it do you think ? I had not any problems like it in Ubuntu 8.04 :( Can you hep me ?

Thank you !

---

### Post by mindwarp on 2008-11-04
You can boot your windows CD is rescue mode and it should have commands 'fixboot' and 'fixmbr' to install a boot record.  Then you can boot with a Ubuntu CD and install grub again and have it point to your windows partition if it is actually broke.

If you delete 'sda7 /', your files in 'sda8 /data' will not be deleted.

Powering down all the way is recommended, but the filesystem you're using has a journal so it shouldn't be a huge deal.

---

### Post by qwe99 on 2008-11-04
Do I have to wait so long when my computer shut downs ??

I know that MBR can be installed with LiveCD, but which commands should be entered to the terminal

---

### Post by qwe99 on 2008-11-07
Please help me! I have to format windows xp immediatly !! :(

---

### Post by soro2005 on 2008-11-07
You shouldn't format sda7 if it's about the windows xp partition (sda1). sda7 seems to be your Ubuntu root partition, meaning that, if you format it, you will lose your Ubuntu installation. The partition that's mounted at /data (sda8) will not be destroyed if you only format sda7.

BUT: All these hd and partition references look very different from outside linux (would be more something like hda(0,1) ), so you want to make extra sure that you are getting the right one. Keep a meticulous record of the file systems installed on each partition, and the partition sizes, so you can match and compare. And PLEASE back up all your important data to an external hard drive which you disconnect from the computer before you start formatting.

WinXP, if you reinstall it, will take care of the MBR. It will most likely take it over, to the effect that you won't be able to find your Grub menu (and the Ubuntu installation) any more. You will have to use a Live CD to get your Grub back in place. Don't worry about MBR, worry about how to get your Grub start menu back.

If you're on your way out of Windows, you may as well just install it into a Virtualbox virtual machine inside Ubuntu and shrink your original windows partition so that you only keep it for the boot loader (Grub).

---

### Post by qwe99 on 2008-11-07
soro2005, I think you missunderstood me! I said that I'm going to format the windowx xp (which is the first part sda1 (ntfs) ). And after formating I will install windows xp again in sda1. I didn't undertand what you want to tell me (sorry for my english). What is the connection about the other part. Ijust want the commands to install the grup. (because after I will installed windows xp, windows automatically delete the grup).

(For example when I was using Ubuntu without sway and /data I just write the following commands :
xterm
sudo grup
find /boot/grub/stage1
root(hd0,2) 
setup(hd0)

But now I don't know the commands, because my partitions changed with adding swap and /data parts. My latest partition list is top on the page)

---

### Post by soro2005 on 2008-11-07
Ok, I haven't used Windows in a while, so I don't know how to instruct it to write something non-standard to the mbr.

To point the mbr to your existing grub installation: It all depends on where your grub installation is actually located. If you have it, for instance, on the same partition with the Windows installation, then it will be razed when you reformat the windows partition. But you have realized that.

I am not going to try that out here now, but if you start your Computer from an Intrepid Ibex Live CD, you get, at the very first screen, an option to "Rescue a broken system." I am pretty sure that there will be a choice to reinstall the grub loader. Try that.

---

### Post by qwe99 on 2008-11-07
sudo grub

find /boot/grub/stage1

   (hdx,y)

root (hdx,y)

setup (hd0)

These are the commands for every differnet parrittiosn. I found it from other linux forums :)

---

