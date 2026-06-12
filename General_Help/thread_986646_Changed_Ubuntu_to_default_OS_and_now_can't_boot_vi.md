---
title: "Changed Ubuntu to default OS and now can't boot vista"
date: 2008-11-18
forum: General Help
---

### Post by aaaarrrggh on 2008-11-18
Not sure if this is a Wubi probem probably not but...

So I set up Ubuntu using Wubi, but I couldn't get it to give me it as an option in startup, so I downloaded EasyBCD aand in a fit of irritation changed the defualt OS to Ubuntu. Now Ubuntu loads fine but I get no option to load vista. I can't seem to get into the bios either tried pressing F2 and F12 at start up and it just hangs. Any ideas, I need to get access to the vista part of my PC pretty urgently!

PC is a dell Inspiron 531.

Any help greatly appreciated,

Thanks.

---

### Post by caljohnsmith on 2008-11-18
Do you have a Windows Vista Install CD? If not you could instead download a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"), boot that up, go to the command line and first do:
```
diskpart
```
And at the diskpart prompt do:
```
list volume
exit
```
The first command should show the drive letter of your Vista partition, and use it in the following commands in place of "C" if the drive letter is different:
```
bcdedit /store C:\boot\bcd /set {default} osdevice boot
bcdedit /store C:\boot\bcd /set {default} device boot
bcdedit /store C:\boot\bcd /set {bootmgr} device boot
bcdedit /store C:\boot\bcd /set {memdiag} device boot
```
That should get your Vista booting again. Let me know how it goes. 

P.S. forum member meierfra deserves the credit for the above really useful Vista hack.

---

### Post by aaaarrrggh on 2008-11-19
I've got the vista disk so I just need to get the PC to boot off it.

What happens is the PC starts to power up I press a function key and then it just stops, sounds like it's gone into sleep mode. I don't get any options come on the screen to enter the bios if I just let it load normally.

Is there a way to get it too boot off the CD from Ubuntu?

---

### Post by markg48 on 2008-11-19
vista sucks i downgraded to xp and now have a dual boot of xp and ubuntu

however there is a command that fixes this but i forogt it sorry -.-

AH! found it  boot of you cd and run Command Prompt option and type:

(not sure if this only for recovery drive only but u can give it a try)

	Replace x: in the commands below with the letter to your CD drive as detected by the Windows Recovery environment


bootrec.exe /fixmbr

x:\boot\bootsect.exe /nt60 all /force

Then ask it (nicely!) to try and rebuild your BCD data from scratch:

del C:\boot\bcd

bootrec.exe /rebuildbcd

If you're lucky, this'll work and you'll see a message telling you everything went OK.

Reboot your PC by typing in this command or by closing all the dialogs:

shutdown -r -t 0

Don't forget to remove your Windows Vista DVD or Recovery DVD from the drive!

---

### Post by markg48 on 2008-11-19
sounds like us stuffed your computer completely

you could try downloading a recovery cd from here 

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

dont no if it will work since u cant boot from vista cd

---

### Post by aaaarrrggh on 2008-11-19
Have now managed to make things worse. I tried to edit the boot order so opened up /boot/grub/menu.lst and swapped round windows and ubuntu hoping that this would boot windows first. Now it just hangs when I turn the computer on. As in it starts to power up and then nothing happens, at all. Doh!

Any ideas?

I can't get to the boot menu otherwise there wouldn't be a problem. Any ideas why I can't get into the bios?

---

### Post by aaaarrrggh on 2008-11-19
all good now no idea what the problem was. I unplugged everything left it for the day then wired it back up and turned it on, the bios menu popped straight up, booted into windows and all is good.

Thanks for the help.

---

