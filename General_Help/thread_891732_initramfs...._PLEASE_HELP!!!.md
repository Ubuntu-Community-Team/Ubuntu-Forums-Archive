---
title: "initramfs.... PLEASE HELP!!!"
date: 2008-08-16
forum: General Help
---

### Post by russell1921 on 2008-08-16
Hi people I have finally fixed it, all i had to do was change a BIOS hard drive setting to disable the jmicron raid controller to disabled

---

### Post by gabo.cr on 2008-08-16
I had the same problem with a Dell Inspiron, it got fixed using **acpi=off** at the beginning of the LiveCD under "Options".
Who knows? it may work for you too.
:)

---

### Post by russell1921 on 2008-08-16
aww thanku!!! i will try it now nd let u know :)

---

### Post by gabo.cr on 2008-08-16
Well, remember to change the grub too after you install Ubuntu.
Otherwise, you will have the same problem again.
In terminal:

**sudo gedit /boot/grub/menu.lst**

You will get a window, search for the first line that begins with "kernel" not "#kernel" and then add at the end of that line "acpi=off"

---

### Post by russell1921 on 2008-08-16
I tried the 'acpi=off' and it didnt work :( but i did take a photo of what come up on screen:

[http://img49.imageshack.us/img49/1944/errorubuntuui5.jpg](http://img49.imageshack.us/img49/1944/errorubuntuui5.jpg)

hope u can help, many thanks

---

### Post by rlanham on 2008-08-16
Are you dual booting with a windows install of some sort? This problem is also caused when you boot into windows and do no do a complete shutdown. 

If this is a laptop and the windows hibernated or you simply held the power button down, or hard reset it then windows will not properly disconnect from the NTFS/MBR. 

So the solution to your problem if you are dual booting, is to boot windows and do a proper shutdown, then boot into ubuntu.

---

### Post by russell1921 on 2008-08-17
Hi I only have Windows XP installed on my Desktop computer and I do a complete shutdown but it still doesn't work but I do have 2 IDE Hard drives if that helps at all?

---

### Post by _Rosco_ on 2008-09-03
> **russell1921 said:**
> [B]Hi can anyone please help me, I have looked everywhere I could to get help on this error/problem and it is really driving me nuts now I really wanna try the Ubuntu live CD without installing it but it just wont start, I'm very new to Linux and I aint very gd with sorting out code like 'sudo' and stuff but anyway as far as I know its related to that 'can't access tty, job control turned off' error but I am using the latest version 8.04 :S it loads the little slash screen and then stops and says: 

BusyBox v1.1.3 (Debian 1:1.1.3-ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs)


I havent got a clue where to start sorry people :( :([/B]

I've seen this message occur when an NTFS partition is incorrectly shutdown after installing Ubuntu from the live cd.  Here's a solution: [http://www.proposedsolution.com/solutions/ps0017.php](http://www.proposedsolution.com/solutions/ps0017.php)

Hope this helps

~Rosco~

---

### Post by kentbower on 2008-09-07
in WinXP, try:

**chkdsk c: /f**

(you may need to 'schedule' the chkdsk and reboot windows)

That finally fixed my initramfs problem that happened after my laptop ran out of battery while ubuntu was running.

I was getting:
ALERT! /host/ubuntu/disk/root.disk does not exist

and then the 

initramfs_ prompt

---

### Post by russell1921 on 2008-09-18
> **_Rosco_ said:**
> I've seen this message occur when an NTFS partition is incorrectly shutdown after installing Ubuntu from the live cd.  Here's a solution: [http://www.proposedsolution.com/solutions/ps0017.php](http://www.proposedsolution.com/solutions/ps0017.php)

Hope this helps

~Rosco~

Ok thanku very much for ur help, I will try those solutions now, I will let u know if it works or not THANKS!!!!!

---

### Post by russell1921 on 2008-09-18
> **russell1921 said:**
> Ok thanku very much for ur help, I will try those solutions now, I will let u know if it works or not THANKS!!!!!

**hmm none of the solutions seemed to fix my problem because when I use the mount command it says 'No such file/directory found' or something like this? And I tried to find what my mount command would be but I cant seem to find it, can anyone help? thanks!**

---

### Post by russell1921 on 2008-09-28
Its odd because Knoppix or Knoppix based linux seems to boot fine into the live CD, just not distros like Ubuntu, Mandriva...

---

