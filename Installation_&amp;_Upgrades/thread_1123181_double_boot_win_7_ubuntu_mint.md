---
title: "double boot win 7 ubuntu mint"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by johanbo80 on 2009-04-11
Hello,

Greeetings from a Swedish newbie to Linux living in France.

I have a big start-up problem.

Let me explain:

1. I have 4 hard disks in my computer.

2. I have installed for testing purpose one windows 7 on one disk, I use that one for office work - all important data are on that disk -and the second Windows 7 on a second disk, I use that disk for media connections and web sites creations. I used Vista before but was unhappy with this program because of its too many freezes (X or Y or Z have stopped working,..). That's why I wanted to test windows 7..

3. On the third disk I have installed Linux Mint and on the fourth disk Ubuntu. When I installed these 2 OS the programs were asked to import the Windows bootloader.

After the installa tion of Linux Mint, when rebooting this OS only found the windows bootloader, but not itselfs own Linux grub loader. Very generour to Windows! Mint opened the door for Windows but remaind outside itself!

4. So I installed the Ubuntu on the fourth disk, hoping that this OS would show its own grub loader together with Linux Mint and the Windows boot loader on the reboot. What deception. Same thing again. Only the windows bootloader did show up, nada for Mint and Ubuntu.

This is extemely frustrating. I have a strong wish to say definitely goodbuy to Windows after more than 10 years "fidelity" - too many craches and problems of all kinds.

However, How can I switch over to Linux if I cannot run the Linux OS parallelly with windows duringa first period?

I have followed the instructions in the note "Recovering Ubuntu after installation Windows". I have also used the "Super Grub Disk", all to no avail. In spite of all the efforts, only the windows boot looader is visible on reboot.

So I am completely stuck, turning around in the same vicious circle.

What is the problem? Why does not Mint, nor Ubuntu, show other program's boot loaders on reboot?
A description in detail, step by step, to follow to solve this boot problem will be highly apprciated and with much gratitude.

Can some one help me as fast as possible. I have important things to do with my computer during this week end.

Best wishes
johanbo80

---

### Post by meierfra. on 2009-04-11
Sounds like grub got installed on the wrong hard drive. See what happens if you  boot from  one of the other drives (try them all).

**If that did not solve your problem:**

In order to get a clearer picture of your setup, I suggest to boot from the Linux Mint LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

