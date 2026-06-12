---
title: "installing bootloader"
date: 2009-08-14
forum: Installation &amp; Upgrades
---

### Post by redrivergorge on 2009-08-14
I had ubuntu 9.04 installed on my desktop. It was installed on my second hard drive. I was out of town for awhile and I got a laptop. My dad pulled my hard drives for me so I could transfer my music to the laptop. Everything I needed is on the second drive with my linux install. I'm back home now and went to get my desktop back up and running. Well it turns out my dad didn't think I needed the first drive. He ended up formating it and putting it in some ones computer he was working on at the time. So my question is is there a way for me to put grub on this second drive and point it to the install thats already there? I'm on the desktop right now I have it booted with the live cd.

---

### Post by ajgreeny on 2009-08-14
This shouldn't be a problem that can't be sorted quickly, so:-
Boot into the ubuntu live CD
open a terminal and run :
    ```
sudo grub
```This gets you to a simple grub command line.
Then:
    ```
find /boot/grub/stage1
```This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. If you have more than one linux install you may get more than one answer here.  Use the one from which you want to use grub.  Replace the question marks in the following command with the output of the this last command :
    ```
root (hd?,?)
```[like : root (hd0,1) ,probably]
then:
    ```
setup (hd0)
```This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default, but as you now only have one disk, I don't think this will apply to you; just leave it as (hd0).
Then:
    ```
quit
```Finally reboot, and hopefully you will now have a working grub bootloader.

It is possible that you may need to edit the grub menu.lst file as it has come from a setup with two drives but if it uses the UUID for the ubuntu partition, even that may not be necessary.

---

### Post by redrivergorge on 2009-08-14
That worked flawlessly thanks for the help.

---

### Post by Marti68 on 2009-08-16
Not a thread-jack but I think this may solve my issues with some slight adaptation.
Added 9.04 to my XP desktop from the live CD which had worked perfectly on the laptop.  Unfortunately, at reboot CHKDSK ran to completion.  I think it saw the partition changes as a fault and wrote to the MBR so now the system boots straight to XP without Ubuntu boot options.

Can I edit this to get the same Ubuntu (default) and XP option list I have with the laptop?

Thanks for you guidance; community is amain factor in my switch to Ubuntu

---

### Post by presence1960 on 2009-08-16
Marti, let's get a better look at your setup. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Marti68 on 2009-08-20
YEA!  My first use of an Ubuntu forum for help and first use of Terminal CLI commands to resolve an issue with the new OS - _**Thanks guys.**_  Jaunty is on the desktop

Minor issue with XP now reporting that NTLDR is missing (it's an XP - 9.04 duel boot) and I still need the old system for the things I don't know in Ubuntu but it's getting there

Am I right in thinking I got this issue because I let the bootup disk check run.  Duel booting my Dell d620 was a faultless procedure?

---

