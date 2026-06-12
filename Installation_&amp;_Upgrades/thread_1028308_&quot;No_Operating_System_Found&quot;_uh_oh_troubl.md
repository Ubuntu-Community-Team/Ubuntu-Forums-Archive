---
title: "&quot;No Operating System Found&quot; uh oh troubles"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by uberbuntufan64y on 2009-01-02
I purchased a new dual core desktop about a month ago and have been using it with Windows Vista. Yesterday I decided to try and install Ubuntu on my computer and dual boot.

I went through the install seemingly without problems, but I think I messed something up because I get a "No Operating System Found" error... I hope that it's fixable because I have a months worth of data on my Windows drive ...

---

### Post by oldos2er on 2009-01-02
Can you post the output of both these commands?

 sudo fdisk -l

 cat /boot/grub/menu.lst

---

### Post by donkyhotay on 2009-01-02
Sounds like grub didn't install correctly. Your vista is (probably) just fine, but you'll need to reinstall grub to get access to it. There could be something else going on though so before doing that why don't you post the fdisk and grub information requested by oldos. To get it you'll probably need to use a liveCD to temporarily regain access to your system.

---

### Post by albinootje on 2009-01-02
> **uberbuntufan64y said:**
> I purchased a new dual core desktop about a month ago and have been using it with Windows Vista. Yesterday I decided to try and install Ubuntu on my computer and dual boot.

I went through the install seemingly without problems, but I think I messed something up because I get a "No Operating System Found" error... I hope that it's fixable because I have a months worth of data on my Windows drive ...

Did you leave a usb-stick or floppy disk with only data in the machine by mistake ?

And is your BIOS still "trained" to boot from the first hard disk ?
I've seen computers with annoying BIOS-es which simply mix up the boot-order after changing it to cdrom first.

Can you boot from the Ubuntu installation cdrom, choose the "non install" session, and post the output of :
```

sudo fdisk -l

```

---

### Post by caljohnsmith on 2009-01-02
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

### Post by uberbuntufan64y on 2009-01-11
I think I understand now how to run commands but I am still not sure. I know in windows you just type cmd in the run box thingy.

I cant get my live CD to boot, I followed instructions somewhere to change my bios back to make it go faster booting and it doesn't try to start up the Ubuntu live cd anymore.

---

### Post by uberbuntufan64y on 2009-01-11
I am currently trying to convert my setup to 100% ubuntu, but I still need to dual boot this machine in order to have access to windows just in case I need it (plus the data that I need to get back too)

---

### Post by albinootje on 2009-01-11
> **uberbuntufan64y said:**
> I think I understand now how to run commands but I am still not sure. I know in windows you just type cmd in the run box thingy.

You would open a terminal first.
Either -> Applications -> Accessories -> Terminal
Or : alt-F2 and then type in :
```

gnome-terminal

```
> 
I cant get my live CD to boot, I followed instructions somewhere to change my bios back to make it go faster booting and it doesn't try to start up the Ubuntu live cd anymore.

The cdrom- or dvd-drive needs to be the first.
Pretty often you can use F12 or F8 to have a boot choice menu popped up.
 
Is the Ubuntu cdrom OK ? Can you try it in another machine ?

---

