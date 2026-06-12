---
title: "Grub loading stage1.5read error"
date: 2009-04-24
forum: Hardware
---

### Post by mmjensen on 2009-04-24
Hello
 
I have just downloaded and tried to install ubuntu 9.04, but I have some problems that I'm hoping you guys could help me with.
 
After first reboot I get this message:
Grub loading stage1.5read error
 
I have a Asus P4S800-MX motherboard and a Maxtor Diamondmax 160GB (STM3160215A) harddrive. Need more information? Tell me please.
 
I gave ubuntu the entire harddrive.
 
But I get this message.
 
Any help is appreciated!
 
Mads

---

### Post by meierfra. on 2009-04-24
The Grub Read Error is somewhat unusual.  Is your hard drive detected in the bios?

In order to get a clearer picture of your setup, I suggest to boot from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

