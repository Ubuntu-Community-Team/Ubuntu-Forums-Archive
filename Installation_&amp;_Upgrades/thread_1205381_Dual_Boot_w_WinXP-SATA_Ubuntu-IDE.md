---
title: "Dual Boot w WinXP-SATA Ubuntu-IDE"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by diy_guy on 2009-07-06
I've found alot of how-to's and whatnot to get whis to work, with little to no clear instructions. I like things to be clear and specific as far as instructions go. So here's my example of how to get this to work, lets review the setup:

Primary SATA Master - HDD - WinXP Pro install
Primary IDE Master - HDD -Ubuntu
Primry IDE Slave - DVD-rom

Boot device Priority:
DVD-rom
Primary IDE Master
Disabled

To get to choose the IDE HDD make the IDE HDD the 1st bootable HDD device, it's another sub-menu on the same page as the Boot Device Priority submenu. This comment isn't as specific because not all BIOS menu's are the same.

Now let your PC boot into Ubuntu and open a terminal, type:
sudo gedit /boot/grub/menu.lst  <-- (LST not 1ST in lower case)
enter

In the new window is displayed the menu.lst file. Look for the block that starts with:
# title Windows .....

Remove the # from all the lines in this block, and add/edit the lines to look like this:
title        Windows XP Pro
root        (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader    +1

Save and exit. Reboot the system, upon booting a menu will appear only for 3 seconds, Windows XP Pro will be first, if you don't choose anything it will load WinXP automatically, hit the DOWN arrow key once and it will select the first standard Ubuntu boot option and hit ENTER, and you will boot Ubuntu for this session.

I hope this finally makes it clear, feel free to ask questions. Be patient as I'm no expert, just an experienced user.

---

