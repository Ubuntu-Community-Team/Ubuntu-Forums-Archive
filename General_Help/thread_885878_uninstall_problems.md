---
title: "uninstall problems"
date: 2008-08-10
forum: General Help
---

### Post by ESV0720 on 2008-08-10
I have been using Wubi and ubuntu for several months now. But I needed to uninstall it to free up some hard drive space.

The uninstall went fine and clean, but now when I go to do a reboot, it still comes up with the boot screen where I have to select either ubuntu or vista.

How can I get rid of this?

Thanks in advance

E

---

### Post by Jaxco on 2008-08-10
I cannot get it to uninstall at all!  I can solve your problem though, You need to edit the C:/boot.ini file... Just remove the last line that says:

c:\wubildr.mbr="Ubuntu"

You will probably have to check file permissions so you can see hidden and system files.

Can anyone help me uninstall ubuntu?  I am going to use a separate drive later to re-install it.

---

### Post by ESV0720 on 2008-08-10
The two ways they describe are

through the add remove program file
or
through the uninstall tool that comes with it (in the ubuntu folder)

Describe the problem more. What have you done? What's left? etc

---

### Post by ESV0720 on 2008-08-10
ok. apparently vista doesnt have a boot.ini file. At least not one I can find on the C drive

[http://www.neowin.net/forum/lofiversion/index.php/t411005.html](http://www.neowin.net/forum/lofiversion/index.php/t411005.html)

doesn't help me, as I have no idea what to do. I'm afraid of ruining my partition as my laptop is basically my life

---

### Post by FXEF on 2008-08-10
> **ESV0720 said:**
> I have been using Wubi and ubuntu for several months now. But I needed to uninstall it to free up some hard drive space.

The uninstall went fine and clean, but now when I go to do a reboot, it still comes up with the boot screen where I have to select either ubuntu or vista.

How can I get rid of this?

Thanks in advance

E

 Run bcdedit.exe /? from cmd prompt to read the help documentation. This should tell you how to remove the Ubuntu boot option.

---

### Post by ago on 2008-08-11
[https://wiki.ubuntu.com/WubiGuide#Cannot%20uninstall%20Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot%20uninstall%20Ubuntu)

---

### Post by ESV0720 on 2008-08-11
> **FXEF said:**
> Run bcdedit.exe /? from cmd prompt to read the help documentation. This should tell you how to remove the Ubuntu boot option.


thanks for the reply

I've never used bcdedit.exe before, and am worried about doing something wrong with my vista partition. Can you help me out with doing it right?

@ago - the link you gave doesnt seem to help. when I download the tool, and run it, it doesn't do anything.

Thanks for the help

---

### Post by ago on 2008-08-12
> **ESV0720 said:**
> thanks for the reply

I've never used bcdedit.exe before, and am worried about doing something wrong with my vista partition. Can you help me out with doing it right?

@ago - the link you gave doesnt seem to help. when I download the tool, and run it, it doesn't do anything.

Thanks for the help

That only works if you didn't remove the ubuntu folder manually. In any case in the guide there is also a manual disinstallation procedure.

---

### Post by ESV0720 on 2008-08-12
Ago-

Thank you for the help. But the alternative uninstall (system>advanced>...) doesn't get rid of the ubuntu entry. If someone can tell me how to use bcdedit, I would really appreciate it.

---

### Post by ESV0720 on 2008-08-14
bump for some help...

---

### Post by spike.robinson on 2008-08-14
I don't know if Vista has a boot.ini file as I only know XP. However if it works like XP, boot.ini is a hidden file, so to find it you need to set your Folder Options in Windows Explorer to show hidden and system files. Then you can edit it using Notepad. 

There will be a single line that refers to the wubildr.mbr, just delete that single line, save the file, and reboot. Take a backup copy first in case you screw up. If you mess up boot.ini, you WILL be in big trouble.

---

### Post by ESV0720 on 2008-08-15
spike-

it doesn't have a boot.ini file. It's apparently only accessible through the bcdedit.exe command line. That's why I'm trying to find someone who knows what they're doing so I don't screw it up

Thanks for the help

---

