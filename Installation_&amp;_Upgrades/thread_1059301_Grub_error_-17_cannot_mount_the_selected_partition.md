---
title: "Grub error -17 cannot mount the selected partition"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by sathibabu on 2009-02-03
Hi ubuntu community,

I want to install ubuntu 8.04 LTS on my external hard drive completely. i.e when i don't plugin my hard drive, my laptop should boot into windows XP as usual.But if i plugin my hard drive and changed the bios seetings to boot from external hard drive first, it should boot into ubuntu. it would be great if i take my hard drive to somether windows computer and get it to boot by only changing that computer's bios settings. 

i have already installed ubuntu on my external hard drive completely. but once i restart my computer, i get [COLOR="Black"]**"grub loading error -17: cannot mount the selected partition"**[/COLOR]. 
I know that i have to change my grub menu.lst file. but i want someone to give me very simple explanation as i m very new to linux.

thanks
sathi.

---

### Post by caljohnsmith on 2009-02-03
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by ajgreeny on 2009-02-03
I think your problem is due to the fact that ubuntu has put grub on the MBR of the windows disk but the menu.lst file that it points to for the grub configuration is on the external disk.  The best way to overcome this is to firstly restore your windows MBR with your windows install disk, then boot the ubuntu live CD and run ```
sudo grub
```
```
find /boot/grub/stage1
```
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. If you have more than one linux install you may get more than one answer here.  Use the one from which you want to use grub.  Replace the question marks in the following command with the output of the this last command :
    ```
root (hd?,?)
```
then:
    ```
setup (hdx)
```
This should be the same as the root commad above to put grub on your external disk, but use just the disk dev name not the partition, ie hdx not hdx,x
Then:
    ```
quit
```
Now set your BIOS to boot first from the external disk and second from the hard disk, so that when the external is attached you will get a grub menu, but when it is not attached the windows MBR will take you straight into windows.

---

