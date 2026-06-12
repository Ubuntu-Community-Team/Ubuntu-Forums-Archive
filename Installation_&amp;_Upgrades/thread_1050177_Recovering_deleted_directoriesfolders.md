---
title: "Recovering deleted directories/folders"
date: 2009-01-25
forum: Installation &amp; Upgrades
---

### Post by Adock on 2009-01-25
Hello,
I'm running Ubuntu 8.04 LTS Hardy Heron Desktop CD 32 bit, 
on a multi-boot system.
I'm not able to get on the internet with it as yet.

After it installed; I realized I was in over my head,
being a new user on this platform.

There were four or five directories/folders, including
the uninstall icon, on my "E" drive; plus Ubuntu was
installed in control panel of Win' XP- Pro, on my "D"
drive. 

I've uninstalled it, and deleted the directories/folders;
to my surprise it still remained on the bootstrap, and
I'm able to boot into it.

Question? Is there a way that I can recover these 
directories/folders, through the terminal?

Your help will be much appreciated.

Thank you.

---

### Post by oldos2er on 2009-01-25
By default Ubuntu installs grub (its bootloader) to your MBR, and keeps grub's configuration file in /boot/grub.

 You should be able to use your WinXP CD to run "fixmbr" which will get you back to Windows (but not Ubuntu). Or, you can use your Ubuntu LiveCD to restore grub; or yet another option would be to download Super Grub Disk [http://www.supergrubdisk.org](http://www.supergrubdisk.org)[SIZE=2] and restore grub with it.

[/SIZE]

---

### Post by caljohnsmith on 2009-01-25
Was your Ubuntu a Wubi install? In other words, was it installed inside of Windows? If so, you might be still seeing it in your Windows boot loader on start up. Do you have a Ubuntu Live CD you can boot and use? If so, how about booting that, download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup related to any booting problems you might have.

---

### Post by Adock on 2009-01-25
Hello,
Oldos2er thanks for the reply, however the link you gave, returned
Address not found.

caljohnsmith. No!It was not a Wubi install, but from the CD that I
bought.
Yes, I still see Ubuntu in my Windows boot loader on startup.

Yes, I do have a Ubuntu live CD. How do I boot again? Do I just
put the CD in the CD rom drive? If yes, what do I do next?

I downloaded the Boot Info Script to my Windows desktop; as I am 
unable to get on the net from Ubuntu (modem config problems), at
the moment.
Awaiting your reply.
Thank you all.

---

### Post by caljohnsmith on 2009-01-25
Yes, just put the Live CD in your CD drive, make sure your BIOS is set to boot the CD drive before your HDD, and then you should be able to boot the Live CD. At the first main menu choose "try Ubuntu without making changes", and once you get to the Ubuntu desktop, if you go under the "Places" menu you should see your Windows partition listed there. Click on that, and then you should be able to navigate to wherever you have the boot_info_script*.sh stored, and copy it to your Ubuntu desktop. From there you can run it as instructed in my previous post. Let me know how it goes or if you run into problems.

---

### Post by oldos2er on 2009-01-25
"Oldos2er thanks for the reply, however the link you gave, returned
Address not found."

 Fixed.

---

