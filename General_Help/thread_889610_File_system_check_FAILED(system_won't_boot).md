---
title: "File system check FAILED(system won't boot)"
date: 2008-08-14
forum: General Help
---

### Post by kindlinux on 2008-08-14
Um,can anyone help me with this please :-(.

while system file check was running,it checking the disk for any problems

then It stopped and said hda4 had an unexpected inconstancy

it also said...

*a log is being saved in /ver/log/fsck/checkfs if that location is writable.Please repair the file system manually.

and to press control+D to terminate maintenance and continue boot.

HELP please 
thank you...:-)

edit:I think I should run a fsck on hda4,but I want hlep before I do so...

---

### Post by RealPSL on 2008-08-16
It is asking you to run a check on hda4 using ```
fsck /dev/hda4
```Hopefully the problems can be repaired.

---

### Post by joshuntu on 2009-12-24
I am having a similar problem except when mine starts to check file systems it stays at zero percent for a while then just tells me that file system check failed and the press control-d to try again, if i press controle d the same thing happens, it tries and fails and offers for me to press control d again ect. it says opened maintenence shell or something like that and says that the file system can not be found. any help??

---

### Post by Herman on 2009-12-24
The program fsck doesn't check your file system itself, it is a program which runs other programs. It is mainly useful because other programs can be given the fsck command without the need to know exactly what kind of file system is going to be checked.
The fsck program will choose which file system checker is appropriate for the file system to be checked and run a safe, (but not always effective) file system check on it.

---

### Post by Herman on 2009-12-24
It's better to run a file system check yourself.

When you're running your file system check personally, you can find out exactly what kind of file system you intend to check, and choose the appropriate program for it yourself, rather than leaving it up to fsck. 
The fsck program would have run the e2fsck program for you if your Ubuntu installation has an ext series file system.
By running e2fsck yourself, you can set more powerful options.

Always best to run a file system check from a different Linux installation in the computer or else from a live CD.

You need to make sure the file system you want to check is not mounted.

To find out what device number will represent the file system you want to run a check on, you can use 'sudo blkid', 
```
sudo blkid
```An example of how to run e2fsck follows,
> sudo e2fsck -C0 -p -f -v /dev/sda1Where: the file system to be checked is an ext series file system,
Where: the device containing the file system is known as '/dev/sda1', as indicated by the blkid command run previously.

That command will gently 'preen' your file system and fix most problems and give you an output to show you what has been done. 
Otherwise it will report back to you and tell you if you need to run the command again with more powerful options.

Normally this command will fix all your ext series file system problems. It will always do your ext series file system good and it's safe enough to run as often as you like.

---

