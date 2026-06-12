---
title: "Grub Error 15 after adding openSUSE"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by Svensk023 on 2009-02-26
Hi, 
I have three separate internal HDD's, and today I decided to give openSUSE 11.1 a try, so I re-formatted the FAT32 partition that had taken up my entire HDD with a fresh openSUSE install. everything installed fine but now when I go to boot into Ubuntu, I get "error 15, file not found." I can still boot into my windows HDD, but i cannot boot into my Ubuntu HDD, or access it withing openSUSE.

Help appreciated

-Thanks

---

### Post by caljohnsmith on 2009-02-26
In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD, download the **Boot Info Script** to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by bobmatino17 on 2009-02-26
this could help you a bit...
[http://ubuntuforums.org/showthread.php?t=1081550]("http://ubuntuforums.org/showthread.php?t=1081550")

---

### Post by Habboblob on 2009-04-11
> **caljohnsmith said:**
> In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD, download the **Boot Info Script** to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

I have also gotten the Grub Error 15: File not found error and have the result log for you to see.

[http://pastebin.com/f72795fc1](http://pastebin.com/f72795fc1)

Also, if you could, I would like it if you could post the solution onto my thread so that when other people see it they can also find it out.

---

### Post by Habboblob on 2009-04-13
I received the same problem and in my other thread I had found out the solution. Here is a quote of how to fix it.
Hope it helps :p :


> **meierfra. said:**
> The Suse Grub does not understand "UUID's". So you have to use "chainloader" instead of "configfile":

Boot into Suse and open a terminal and install grub to the boot sector of the Ubuntu partition:

```
sudo grub
```
and at the grub prompt:

```
root (hd0,0)
setup (hd0,0)
quit
```

You also need to edit the Suse menu.lst

```
gksudo gedit /boot/grub/menu.lst
```
(If you don't have "gedit"  try "kate" instead of "gedit")

Then change 

title Ubuntu 8.10, kernel 2.6.27-11-generic (/dev/sda1)
    root (hd0,0)
    configfile /boot/grub/menu.lst

to

title Ubuntu 8.10, kernel 2.6.27-11-generic (/dev/sda1)
    root (hd0,0)
    chainloader +1


Save the file,  and see whether you can boot into Ubuntu.

---

### Post by Habboblob on 2009-05-29
Thank you everyone who helped me out. I was a noob back then, first time to use Ubuntu =D

---

