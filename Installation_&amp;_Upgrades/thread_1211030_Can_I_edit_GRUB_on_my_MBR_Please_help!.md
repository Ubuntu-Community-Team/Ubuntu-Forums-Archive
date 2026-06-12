---
title: "Can I edit GRUB on my MBR? Please help!"
date: 2009-07-12
forum: Installation &amp; Upgrades
---

### Post by Pipps on 2009-07-12
I am having difficulty in editing the GRUB which is installed on my MBR.

Please tell me what I am doing wrong with the following:

I enter:
```
sudo grub
find /boot/grub/stage1
```
Output:
> (hd0,2)
(hd0,3)
(Where (hd0,2) is a Ubuntu installation, and (hd0,3) is a separate GRUB partition.)

Then I enter...
```
root (hd0,3)
setup (hd0)

```
However, after performing the setup command, I find that the settings, which I know to exist within the menu.lst file of the (hd0,3) partition, are not reflected in what I see in GRUB when GRUB now boots - such as menu colors, for example.

What am I doing wrong here? Please help! Thank you.

---

### Post by presence1960 on 2009-07-12
open up the menu.lst file you want to edit and change the settings in there.

If not let's get a better look at your setup and boot process. Download to your desktop the Boot Info Script 0.32 from here: [http://sourceforge.net/projects/bootinfoscript/files/](http://sourceforge.net/projects/bootinfoscript/files/)  Then open a terminal and run this command > sudo bash ~/Desktop/boot_info_script*.sh This will create a RESULTS.txt file on your desktop. Copy & paste the entire contents of that file back here. Once pasted here highlight all text pasted and click # on the toolbar to place code tags around the text. WE'll then have a clearer picture of your setup and be better able to help.

---

