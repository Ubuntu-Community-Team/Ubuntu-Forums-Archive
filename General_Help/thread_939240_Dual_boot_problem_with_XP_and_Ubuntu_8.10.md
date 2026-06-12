---
title: "Dual boot problem with XP and Ubuntu 8.10"
date: 2008-10-05
forum: General Help
---

### Post by Casinero on 2008-10-05
Hi I'm pretty new to Linux/ ubuntu and have tried to install ubuntu 8.10 on my D: drive on a windows XP machine. The installation appears to have run without a hitch but when I try and select ubuntu from the dual boot menu. I get an error1  absolute file pathname or bloclist must be used. on further investigation by rapidly pressing the insert button I get a message that says "the size of the MBR does not match the size of the BIOS
is there a fix for this ????
Thanks in advance for any help

---

### Post by Sef on 2008-10-06
Did you use wubi to install, or did you install it another way?

---

### Post by Casinero on 2008-10-06
I used wubi

---

### Post by Casinero on 2008-10-06
installed to my D: drive
xp is on C:
allocated 8 gb for the ubuntu install

---

### Post by ago on 2008-10-06
You can try using the new grub4dos, download the latest zip  from [http://grub4dos.nufans.net/](http://grub4dos.nufans.net/)

Extract grldr, grldr.mbr as c:\wubildr and c:\wubildr.mbr, then copy c:\ubuntu\winboot\menu.lst to c:\

Please let me know if it works

---

### Post by Casinero on 2008-10-06
is that a solid fix and wont screw up my windows boot?

---

### Post by ago on 2008-10-06
> **Casinero said:**
> is that a solid fix and wont screw up my windows boot?

It's not a solid fix as I am not sure yet what your issue is, but it will not screw up your windows bootloader. It simply upgrades the wubi bootloader mechanism (grub4dos).

---

### Post by Casinero on 2008-10-06
ok I'll give it a try thanks

---

### Post by Casinero on 2008-10-06
I have a question!!
I'm using winrar to extract 
Do i extract just the gldr and gldr.mbr to my c: root and replace the wubuilder files or do I extract the complete grub4dos?
Sorry I'm a newbie at this so bear with me please

---

### Post by Arabiest on 2008-10-06
I have the same problem and will try ur solution to copy the grub4dos and menu.lst files to the root directory (c:\) and will come back with the result as soon as possible...since this issue is becoming an annoying one.

---

### Post by Arabiest on 2008-10-06
WOW

It worked fine.

Summary of what was confusing above to most and am one of them since most of the ppl here are IT wise guys and assumes that they are talking/helping another wise guys and therefore uses strange commands and terminology.

Well here we go.

First of all, your Ubuntu installed the above required files by default in the location exactly specified above by our friend AGO (i.e. root directoy of c drive), except for the last file named Menu.lst, which you need to copy it from the directory spcified by the same friend and past it in the root directory.

By this, your problem will be solved since it worked with me after many re-installation of Ubuntu to a limit I felt like quiting on LINUX and go t my old OS windows xp.

I will try to post the same again, but with images for better illustration and take the lead from most of LINUX wise guys who like to put in in writing and strange command lines.

---

### Post by ago on 2008-10-06
> **Casinero said:**
> I have a question!!
I'm using winrar to extract 
Do i extract just the gldr and gldr.mbr to my c: root and replace the wubuilder files or do I extract the complete grub4dos?
Sorry I'm a newbie at this so bear with me please

You only need those 2 files. And they need to replace the c:\wubildr ones. Wubildr and Wubildr.mbr are identical to those except that they are older versions and wubildr.mbr does have a built-in menu.lst. Hence if you overwrite wubildr.mbr you also have to add C:\menu.lst from C:\ubuntu\winboot

---

### Post by ago on 2008-10-06
Since I am evaluating whether to use the new grub4dos version please report any success/failure.

---

### Post by Casinero on 2008-10-06
ok will do thanks

---

### Post by Casinero on 2008-10-06
Heres what I did
I deleted wubild and wubild.mbr from my C:root I copied gldr and gldr.mbr from the folder I had extracted them into to the c:root.Copied menu.lst from ubunu \winboot to c:root.
I rebooted
selected Ubuntu as my OS
got an error
"windows could not start because the following file is corrupted or missing.
windowsroot\system32\hal.dll
please reinstall a copy of the above file."

---

### Post by ago on 2008-10-06
sorry my fault, copy grldr.mbr as c:\wubildr.mbr, then delete c:\wubildr and copy grldr as c:\grldr (not as c:\wubildr). Your bootloader is set to look for wubildr.mbr. But the standard grldr.mbr (which you renamed wubildr.mbr) will look for "grldr", which in turn will look for "menu.lst".

---

### Post by Casinero on 2008-10-06
ok will try that

---

### Post by Casinero on 2008-10-06
heres what happened
I renamed the gldr.mbr to wubildr.mbr
rebooted
selected ubuntu
got a message saying" press enter for previous mbr any other key to continue " there was a count down clock.
it then went to another screen with a count down and message press esc for menu
after the countdown it went to the original fault that I had whic was that it had to have a absoute path name or blocklist
. Sort of back to square one 

Did I do something wrong? abbsolutely bt i dont know what

---

### Post by ago on 2008-10-06
You should have 3 files in C:\

c:\wubildr.mbr (which is grldr.mbr from the grub4dos zip)
c:\grldr (from the grub4dos zip, do not rename it)
c:\menu.lst (copied from c:\ubuntu\winboot)

---

### Post by Casinero on 2008-10-06
thats what I've got but I get my original fault abbout absolute pathname or bocklist

---

### Post by Casinero on 2008-10-07
Hi Ago,
Do you have any further advice. I checked my system on boot up, pressing the insert key and got the following message.
Ive left out all the sector information but the warning message says that my mbr cylinders(1024) is not equal to the BIOS one.
warning total sectors (16450560) is greater than the total bios one (164344950)
I hope you can help me out of this hole as I want to move away from windows and commit to an Ubuntu os one but it looks as though I might have to stay with windows,I hope not. thanks anyway

---

### Post by ago on 2008-10-07
See this [http://ubuntuforums.org/showthread.php?t=877750](http://ubuntuforums.org/showthread.php?t=877750)
I will contact the grub4dos devs for more insights

---

