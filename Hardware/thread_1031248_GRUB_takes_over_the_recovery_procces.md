---
title: "GRUB takes over the recovery procces"
date: 2009-01-05
forum: Hardware
---

### Post by eyezdk on 2009-01-05
Hi, I have a laptop from HP with "preinstalled vista" 

i got ubuntu up and running, but now i need to make a clean recovory of the system 

I try it when i boot up (presing f11) i get the option, but when i go on with it, GRUB takes over the boot proces, and i can only boot up the systems (ubuntu or Vista)
means the "recovery" that i need to make... naver takes place

any one can help me out with this? can i remove GRUB or Ubuntu, så my recovery system can run?

/Thomas

---

### Post by caljohnsmith on 2009-01-05
Do you have a Ubuntu Live CD? If so, how about booting that, open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. If you don't have internet connectivity when using the Live CD, you can instead right-click [this link]("http://home.comcast.net/~ubuntu_grub/boot_info_script.txt") to the script in your web browser, choose "Save link as...", save the "boot_info_script.txt" file, transfer it to your Ubuntu desktop on the Live CD via USB stick, floppy, or however you want to do it, and then do the following in a terminal:
```
sudo bash ~/Desktop/boot_info_script.txt
```
The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by eyezdk on 2009-01-05
Right now i found my recovery dvds, and bootet up with them, (system can boot up from cd/dvd) and it is reformating my system as i type this. so i will return if that did not helped me. 
but thx for now

---

