---
title: "Multiples OS"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by frosklo on 2009-07-29
[SIZE=2]Hello friends.[/SIZE]
  [SIZE=2] [/SIZE]
  [SIZE=2]I have this problem. I have multiples OS in my PC. In the past I installed more than a Linux to choose one. I installed mandriva (for KDE desktop which I used allways) and ubuntu (for his good reviews in a lot of forums) and I use WinXP too.[/SIZE]
  [SIZE=2] [/SIZE]
  [SIZE=2]My history of installation is:[/SIZE]
  [SIZE=2]1)[FONT=&quot]    [/FONT]Win XP (hd0,…)[/SIZE]
  [SIZE=2]2)[FONT=&quot]    [/FONT]Ubuntu 8.04 (hd0,3).   [/SIZE]
  [SIZE=2]3)[FONT=&quot]    [/FONT]Mandriva 2008 (hd0,7)[/SIZE]
  [SIZE=2] [/SIZE]
  [SIZE=2]So my PC boot with grub but this grub is in (hd0,7) because mandriva is the last SO which I installed.[/SIZE]
  [SIZE=2] [/SIZE]
  [SIZE=2]Now I really like Ubuntu and I will not use mandriva anymore so I want that my start with grub of my ubuntu (hd0,3). After that I want to remove mandriva.[/SIZE]
  [SIZE=2] [/SIZE]
  [SIZE=2]Thanks[/SIZE]
  [SIZE=2] [/SIZE]
  [SIZE=2]PS: I update my ubuntu from 8.04 to 9.04 (sorry for my bad English)[/SIZE]

---

### Post by running_rabbit07 on 2009-07-29
I don't know how to reconfigure your old grub, but yesterday I installed debian alongside my Ubuntu and XP. I ran into some problems from the Debian install and had to delete it. Of course that ruined grub and gave me the grub 15 error.

Do you have the /home partition?

I***f so, be ready to reinstall Ubuntu so that it can repair Grub. Do not do it yet though if you don't have to. I am sure there is a guru that may post later telling how to fix grub without doing all of that. ***

_**Please be patient.**_ I have installed Ubuntu at least 15 times in the past month and it isn't fun if you haven't had practice.

If your Ubuntu is still working, install APTonCD from your Synaptic Package Manager and use it to copy all installed programs and updates. Then after reinstalling (if thats what you end up doing) Ubuntu, you can through the APTonCD disk in and reinstall all your programs and updates much faster than downloading.

---

### Post by stlsaint on 2009-07-29
thanks for this help goes out to the user "PRESENCE1960"!

"you don't have to reinstall to restore GRUB. Just do this:

Code:

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

HE POST THIS TO HELP ANOTHER grub issues...THANKS PRESENCE1960!

---

### Post by running_rabbit07 on 2009-07-29
That looks like it would fix it. I didn't bother searching because it only takes me about 30 minutes to completely reinstall Ubuntu and have all my programs reinstalled and running.

---

### Post by frosklo on 2009-07-30
Thanks [running_rabbit07]("http://ubuntuforums.org/member.php?u=840719")!

But i don´t want reinstall because I try to learn about ubuntu and how resolve my problems on it without reinstall :)

---

### Post by stlsaint on 2009-07-30
did my post above help any?

---

### Post by frosklo on 2009-07-30
> **stlsaint said:**
> thanks for this help goes out to the user "PRESENCE1960"!

"you don't have to reinstall to restore GRUB. Just do this:

Code:

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

HE POST THIS TO HELP ANOTHER grub issues...THANKS PRESENCE1960!

Thanks!!!

I´ll try that but a little change:

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.

for

4. root (hd0,3) because this is where my ubuntu grub.

:P

---

### Post by stlsaint on 2009-07-30
k...understood...let me know how it turns out!

---

### Post by Malac on 2009-07-30
You will probably still need to update the grub in the MBR with setup(hd0) as this will still point to (hd0,7).

---

### Post by frosklo on 2009-07-30
> **Malac said:**
> You will probably still need to update the grub in the MBR with setup(hd0) as this will still point to (hd0,7).
My pc boot from grub on (hd0,7). This is mandriva´s grub so when I update my ubuntu that grub boot my ubuntu with the older kernel so I need edit menu every time that I update my ubuntu.

Because that I want boot from grub on (hd0,3) (ubuntu)

---

### Post by frosklo on 2009-08-03
> **stlsaint said:**
> k...understood...let me know how it turns out!

Thanks stlsaint!

Last weekend I solved that problem with your help :)


I wrote:

1. Boot my computer up with older Ubuntu CD (6.06)
2. Open a terminal window.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "root (hd0,3)"
6. Type "setup (hd0)"
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

Thank :D

---

