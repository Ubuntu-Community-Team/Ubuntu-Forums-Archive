---
title: "Ubuntu 8.10 grub errors?"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by Jordan777 on 2009-01-03
I keep trying to install Ubuntu 8.10 again. I have a partition for Windows already on my hard drive and when I make 3 new ones for /, swap, and /home grub doesn't seem to install correctly.  After running through a full install all I get is error 22, I think, partition not found and when I go to boot up windows xp it says it's unrecognized or something.  What's up with that?  I've used the cd before successfully.  Any thoughts?  I don't think it's the cd.  As the same thing is now happening with my xubuntu cd.  But I've successfully used them both before.  Now they are giving my trouble.

---

### Post by caljohnsmith on 2009-01-03
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it.

If you don't have internet connectivity when using the Live CD, you can instead right-click [this link]("http://home.comcast.net/~ubuntu_grub/boot_info_script.txt") to the script in your web browser, choose "Save link as...", save the "boot_info_script.txt" file, transfer it to your Ubuntu desktop on the Live CD via USB stick, floppy, or however you want to do it, and then do the following in a terminal:
```
sudo bash ~/Desktop/boot_info_script.txt
```
The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by Jordan777 on 2009-01-03
```
ubuntu@ubuntu:~$ cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
--2009-01-04 00:28:27--  http://home.comcast.net/~ubuntu_grub/boot_info_script.txt
Resolving home.comcast.net... 216.87.188.9
Connecting to home.comcast.net|216.87.188.9|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 23641 (23K) [text/plain]
Saving to: `boot_info_script.txt.1'

100%[======================================>] 23,641      38.4K/s   in 0.6s    

2009-01-04 00:28:33 (38.4 KB/s) - `boot_info_script.txt.1' saved [23641/23641]

: command not foundt: line 31: 
: command not foundt: line 32: 
: command not foundt: line 52: 
: command not foundt: line 53: 
: command not foundt: line 69: 
: command not foundt: line 84: 
: command not foundt: line 85: 
'oot_info_script.txt: line 87: syntax error near unexpected token `{
'oot_info_script.txt: line 87: `titlebar_gen () {
ubuntu@ubuntu:~/Desktop$ 

```

That's the output.  I think something is wrong with that script.  Is there just something I'm doing wrong during the install?  They don't ask for anything about grub.  My partitions are

hda1 NTFS Windows
hda2 EXT3 /
hda3 SWAP
hda4 EXt /home

I might be wrong about the hda part.  That's not really important.  That is my outline for partitioning though.

---

### Post by caljohnsmith on 2009-01-03
How about deleting all the boot_info_scripts.txt* files from your Ubuntu desktop and trying again, because according to the output you posted, there was all ready a "boot_info_script.txt" on your desktop and you downloaded it again; thus wget renamed the script to "boot_info_script.txt.1". If you start clean, then the script should run OK hopefully.

---

### Post by Jordan777 on 2009-01-03
Okay that worked.  So this is a really long code string so I'll just upload the file.  Hopefully yyou find something.  I'll look over it too.  Maybe something is just edited wrong.  That'd be great if it's just an easy text file fix.

---

### Post by caljohnsmith on 2009-01-03
Can you set your BIOS to boot the Ubuntu sdb drive? If so, then the solution to your problem might be really simple. If you can do that, how about installing Grub to its MBR to make it bootable:
```
sudo grub
grub> root (hd1,1)
grub> setup (hd1)
grub> quit
```
Next modify your menu.lst:
```
sudo mount /dev/sdb2 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
And then change all your Ubuntu entries to use (hd0,1) similar to:
```
title		Ubuntu intrepid (development branch), kernel 2.6.27-4-generic
root		[COLOR="Blue"](hd0,1)[/COLOR]
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=7f7be1ce-2fc7-40fe-abc8-dbfb73e7c9fa ro quiet splash 
initrd		/boot/initrd.img-2.6.27-4-generic
quiet
```
And change the "# groot=(hd1,1)" line to:
```
# groot=(hd0,1)
```
And finally change the Windows entry at the bottom to:
```
title		Microsoft Windows XP Professional
root		(hd0,0)
chainloader	+1
```
Save, reboot, check to make sure your BIOS is set to boot the Ubuntu sdb drive, and then you should get a Grub menu and be able to boot Ubuntu or Windows. Let me know how it goes.

---

### Post by Jordan777 on 2009-01-03
Okay boot the sdb?  I just need to clarify.  That's the only hard drive physically located in my computer and my computer is set to boot from that hard drive.  Do I still need to go into the BIOS and change that?  The 500gb is external and the 4gb is just my memory stick.

---

### Post by caljohnsmith on 2009-01-03
> **Jordan777 said:**
> Okay boot the sdb?  I just need to clarify.  That's the only hard drive physically located in my computer and my computer is set to boot from that hard drive.  Do I still need to go into the BIOS and change that?  The 500gb is external and the 4gb is just my memory stick.
According to the fdisk output in that script, you have a 500 GB drive (sda) and also a 320 GB drive (sdb) with Ubuntu and Windows XP on it. You can see for yourself if you do:
```
sudo fdisk -lu
```

---

### Post by Jordan777 on 2009-01-03
Well I know it's set to sda...  I'll check my bios first I think and see if maybe somehow the boot order got mixed up.  If it did then that should explain everything.  But it shouldn't have cause I never changed it.  I've seen my external listed as sda but when i just use windows with nothing else on it doesn't seem to matter.

Edit*

So I checked my BIOS and my partitioned hard drive is set to boot first.  I don't know what else I could do to it.  So I just need to go ahead and make the changes you suggested?

---

### Post by caljohnsmith on 2009-01-04
> **Jordan777 said:**
> Well I know it's set to sda...  I'll check my bios first I think and see if maybe somehow the boot order got mixed up.  If it did then that should explain everything.  But it shouldn't have cause I never changed it.  I've seen my external listed as sda but when i just use windows with nothing else on it doesn't seem to matter.

Edit*

So I checked my BIOS and my partitioned hard drive is set to boot first.  I don't know what else I could do to it.  So I just need to go ahead and make the changes you suggested?
That's actually the point of running those Grub commands at the beginning of post #6: without doing them, your Ubuntu sdb drive is currently unbootable. How about just running those commands:
```
sudo grub
grub> root (hd1,1)
grub> setup (hd1)
grub> quit
```
Please post the output, reboot, and if you get the Grub menu OK, then you can continue on with the rest of the directions from post #6 to correct your menu.lst.

---

### Post by Jordan777 on 2009-01-04
Well after a reinstall my hard drive was listed as sda and grub now works just fine.  I believe because it automatically is set to install on (hd0) or something like that.  So I believe if I had just changed that to (hd1), which wasn't an option, it may have solved my problem.

Edit*

Forgot to say thank you very much!!  You were a lot of help!  :P

---

