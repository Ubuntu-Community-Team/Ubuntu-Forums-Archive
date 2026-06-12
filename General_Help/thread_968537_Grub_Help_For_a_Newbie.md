---
title: "Grub Help For a Newbie"
date: 2008-11-02
forum: General Help
---

### Post by heavenly_blade101 on 2008-11-02
Hey all, I'm running Ubuntu 8.04 dual booted with Windows Vista and have a few questions about Grub.

1) Everytime I have ever installed any version of ubuntu, grub gives me 5 options: 2.6.24-16-generic
         2.6.24-16-generic(recovery)
         2.6.22-14-generic
         2.6.22-14-generic(recovery)
         memtest86+
Why is this? is it two different copies of ubuntu and their recovery modes?

2) in 2.6.24-16-generic, my wifi doesn't work, but in 2.6-22-14-generic it does. Is there a command I can enter to switch the boot order so it will automaticly boot into either the latter or Vista?

Any help is greatly appreciated and please remember this is my first time using ubuntu, I have only ever installed it on old computers for friends.

---

### Post by fooman on 2008-11-02
yes, it will have an entry for every kernel that gets installed + its recovery mode + memtest

you can change which kernel/os is the first boot by editing the /boot/grub/menu.lst file...but a far easier method is to use startupmanager.  it is available from synaptic (system > administration > synaptic package manager). search there for startupmanager.

or install from a terminal by typing or copy/paste the following:

```
sudo apt-get install startupmanager
```

after it installs find it in system > administration > startup-manager

click the boot options tab and under "default operating system",  you can choose which kernel/os boots first.

---

### Post by doorman on 2008-11-02
hello heavenly_blade101 and welcome to ubuntu :)

1) every time you update your system with a new kernel image, a new entry shows up in the boot menu. The reason is simple: every update of the kernel either introduces new features or fixes some bugs that existed in the previous release. As such, it is possible it messes up your system somehow (as you've experienced it yourself with the wireless problem). To be able to use your system correctly, ubuntu doesn't remove the "old" kernel image, but leaves it there "just in case".

2) sure, you can change your default boot option. Just open up a terminal, and issue the command:
```
$ sudo gedit /boot/grub/menu.lst
```
A text editor opens up with the boot menu list config file. Find the line which reads
```
default 0
```
and change it to your liking. The number (0 in this case) is the ordinal number of the image in the list. So, in your case, the *-14 would be number 2, while vista is probably located at number 6.

Very important note: if people suggest you to do something with the "sudo" or "gksudo" commands, be sure to fully understand what the command does, as it can compromise your system ( this goes for my post too :P )

---

### Post by heavenly_blade101 on 2008-11-02
Thanks very much, both posts were extremely helpful, i'll be sure to forward this to my friends.

---

