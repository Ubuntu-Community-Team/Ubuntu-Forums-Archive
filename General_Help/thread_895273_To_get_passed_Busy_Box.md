---
title: "To get passed Busy Box?"
date: 2008-08-20
forum: General Help
---

### Post by TreadLight on 2008-08-20
I just updated my Ubuntu OS, then I restarted the computer, used Ubuntu aggain, restarted the computer and used Windows XP, then restarted again and tried to use Ubuntu. For some reason, BusyBox v1.1.3 pops up with this message:

"BusyBox v1.1.3 (Debain 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) *I can type text here*"

I don't know what to do fronm here, though.

The only two operating systems I have installed on my computer are Windows XP Home Edition and the newest version of the Ubuntu Linux operating system.

Windows XP works fine, though.

How do I get past BusyBox to use my Ubuntu operating system?

---

### Post by prshah on 2008-08-20
> **TreadLight said:**
>  For some reason, BusyBox v1.1.3 pops up with this message:

"BusyBox v1.1.3 (Debain 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) *I can type text here*"


Check if you have any Ubuntu CDs lying in your CD drive, and, if you have, remove them.

---

### Post by macvr on 2008-09-09
> **prshah said:**
> Check if you have any Ubuntu CDs lying in your CD drive, and, if you have, remove them.


i had changed the permissions for my ubuntu files>[http://ubuntuforums.org/showthread.php?p=5755601#post5755601]("http://ubuntuforums.org/showthread.php?p=5755601#post5755601")
i dont have a cd in the drive but i get stuck at busyBOX how do i get past this?

---

### Post by Zorael on 2008-09-09
Use a live cd or equavilent to gain access to your ubuntu root drive. Open up /etc/fstab in a text editor. It'll have a section that looks *similar* to the following.
```
# **[COLOR="Lime"]/dev/sda1[/COLOR]**
**[COLOR="Red"]UUID=7dd116b0-a37c-4780-97fc-ed32c1c648f0[/COLOR]** **[COLOR="DeepSkyBlue"]/[/COLOR]**               ext3    relatime,errors=remount-ro 0       1
```
Find the line which has the slash (/) at the second column, here painted blue. Replace the UUID text in red with the /dev/sd* text in green. Make note of this green text, jot it down for later.

Then open up /boot/grub/menu.lst and find the section that looks like the following.
```
title		Ubuntu 2.6.24-21-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-21-generic root=**[COLOR="Red"]UUID=7dd116b0-a37c-4780-97fc-ed32c1c648f0[/COLOR]** ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet
```
It'll be somewhere under the line saying "## ## End Default Options ##". Replace the text in red with the *green* text from the earlier file (/etc/fstab).

There will be more kernel entries (recovery mode entries, earlier kernels), but you should only need to fix one. Pick the most recent. Save the file, reboot. Should work.

Once back in the real Ubuntu installation, enter the following in a terminal.
```
$ sudo update-grub
```

---

### Post by macvr on 2008-09-09
> **Zorael said:**
> Use a live cd or equavilent to gain access to your ubuntu root drive. Open up /etc/fstab in a text editor. It'll have a section that looks *similar* to the following.
```
# **[COLOR="Lime"]/dev/sda1[/COLOR]**
**[COLOR="Red"]UUID=7dd116b0-a37c-4780-97fc-ed32c1c648f0[/COLOR]** **[COLOR="DeepSkyBlue"]/[/COLOR]**               ext3    relatime,errors=remount-ro 0       1
```
Find the line which has the slash (/) at the second column, here painted blue. Replace the UUID text in red with the /dev/sd* text in green. Make note of this green text, jot it down for later.

Then open up /boot/grub/menu.lst and find the section that looks like the following.
```
title		Ubuntu 2.6.24-21-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-21-generic root=**[COLOR="Red"]UUID=7dd116b0-a37c-4780-97fc-ed32c1c648f0[/COLOR]** ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet
```
It'll be somewhere under the line saying "## ## End Default Options ##". Replace the text in red with the *green* text from the earlier file (/etc/fstab).

There will be more kernel entries (recovery mode entries, earlier kernels), but you should only need to fix one. Pick the most recent. Save the file, reboot. Should work.

Once back in the real Ubuntu installation, enter the following in a terminal.
```
$ sudo update-grub
```


WOW!!! worked, now i'm able to get past the BusyBox...
BUT, not able to login ...says> unable to CD to my home directory!!!

---

### Post by Zorael on 2008-09-09
Do you, perhaps, have your /home directory on a separate partition? If so, do the same /etc/fstab procedure on the line that has **/home** in its second column instead of just **/** (root).

---

### Post by macvr on 2008-09-09
NO... still have the same problem.... 
keep getting stuck at the BusyBox!!!

the last time after i went past BUsyBox, i didnt try to rebot again but i got back to liveCD, so i thought i'd try rebooting once again, and keep getting stuck at the BusyBox error... even if i try the recovery mode[i have changed to/dev/sda5 it that too]

wht do i do?

---

### Post by macvr on 2008-09-09
> **Zorael said:**
> Do you, perhaps, have your /home directory on a separate partition? If so, do the same /etc/fstab procedure on the line that has **/home** in its second column instead of just **/** (root).

i dont have a different home directory, but i think i messed up with permissions! as since my problem started with the GDM issue as in the link i'v posted in my first post

---

### Post by Finlandman on 2011-02-22
is there any simple word to but and get **** from it?

---

