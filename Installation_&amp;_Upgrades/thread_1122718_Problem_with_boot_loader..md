---
title: "Problem with boot loader."
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by milespaulson on 2009-04-11
Hello, im new to the forums and a total noob when it comes to Linux, but ive always wanted to mess around with it and i finally got around to trying it. My problem is that im trying to install Ubuntu on my new laptop pre-installed with Vista, i dont want to loose my vista install as i have alot of settings and programs that i use, so i dont want to mess anything up since i dont have any recovery disks. 

My laptop is a HP Pavilion dv9628nr, and its equipped with 2 hard drives that ive upgraded to 2 320s. My problem is when i got to the last screen before installation it has the advanced button, well i didnt know where to install the boot loader and the default settings were wrong(invalid hard drive selected), and i didnt want to mess up my windows installation. So I selected the partition on the second drive, since that was where i was installing it, and went on with business. well now i cant seem to boot into Linux at all, no matter what i do i cant boot into it. I tried a program called EasyBCD and tried to use the windows boot loader to let me boot into Linux but still no go, always some kind of error saying file missing or something.

When i boot up with a live cd the partitions are there and intact, i just dont know where to go from here. i dont know if i am just missing something or what, or if i need to install GRUB over the Microsoft boot loader. If anyone can help out this NOOB i would be very grateful. BTW, sorry for any spelling, grammar, or syntax errors in my post, i never was very good in English class.

---

### Post by meierfra. on 2009-04-11
In order to get a clearer picture of your setup, I suggest to boot from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

