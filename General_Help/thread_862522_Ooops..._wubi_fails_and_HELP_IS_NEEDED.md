---
title: "Ooops... wubi fails and HELP IS NEEDED"
date: 2008-07-17
forum: General Help
---

### Post by vitoroli on 2008-07-17
Hi everybody, I'm in deep trouble.

I have a Wubi Ubuntu / Vista dualboot system. Suddenly I get the following error message when trying to boot ubuntu:

udevd [1171] parse_config_file: can't open '/etc/udev/udev.conf' as config file: Invalid argument

udevtrigger [1173] (same phrase)

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)

Enter 'help' for a list of built-in commands.

(initramfs) _


And that's it!

Can't type a thing (wireless keyboard) and my only way out is to hard reset the machine.

The problem is I have some files on the ubuntu environment that I need to get my hands to and can't do it from Vista.

Any ideas? Please help, thanks a million.

---

### Post by Tosh78 on 2008-08-13
Hi there, I got the same problem, please, let me know if you find a solution. What I did is to start with an old kernel (you have to press after you choose Ubuntu in the grub).

---

### Post by jmszr on 2008-08-14
vitoroli/Tosh78,
  
This is from the Wubi Wiki-lots of good information there:

The Ubuntu splash screen loads for awhile then exits to a BusyBox/(initramfs) prompt.

Try The Following Solutions : 1) Boot into Windows, Goto "My Computer", Right click the drive that you have installed Ubuntu in.Click Properties.
Select the "Tools" tab and click "check now" under error checking( On Vista, You might be asked for administrative rights). Make Sure "Automatically fix file system errors" is checked and click Start. After The checking is done, restart the pc by using the start menu(Do not hard reboot) and try using ubuntu now.

2) Reboot and hit Esc when prompted to enter the boot menu. Hit 'e' to edit the first line. Next select the second line and hit 'e' again. Input 'irqpoll' towards the end of the bootline. Then hit 'enter' and then 'b' to boot.

Hope this works for you.

---

### Post by fiddler616 on 2008-08-15
When I wanted to get my feet wet with Ubuntu, but not commit to anything, I used Wubi, and could never get it to work. I ended up biting the bullet and partitioning my hard drive (which really isn't so bad with the installer). Anyway...
For accessing your files, have you tried Win2fs? [http://win2fs.sourceforge.net/](http://win2fs.sourceforge.net/)
Even when everything is going great, it's convenient to be able to access Linux stuff from Windows.
------------
As for Wubi, in all honesty, I'd go back to Vista, uninstall it (Wubi, not Vista :) ), burn a live CD, check Ubuntu out thoroughly, and make an executive decision about whether you want it or not. If you change your mind later, I believe it's just as easy as popping the Live CD back in, runnning gparted (Alt+F2, type in gksudo gparted, I think), and getting rid of the Linux partition(s), though I'd wait for confirmation from someone else with more than 5 cups of Ubuntu before trying it :)
---
Hope that helps...

---

