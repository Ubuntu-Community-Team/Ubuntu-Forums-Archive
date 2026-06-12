---
title: "Exclude Bad Memory"
date: 2009-12-01
forum: Hardware
---

### Post by DuXati on 2009-12-01
Hi all,

About three weeks ago, Ubuntu 9.10 started freezing at seemingly random moments. With freezing, I mean everything on the screen freezes except for the mouse and the only thing I can do is a manual restart. 

I've searched what could be the error and eventually ran memtest. It seems there is faulty RAM, at 282.5MB (40 error in 6hours of testing). I've searched for solutions for this and I've come up with the following solutions:

[LIST=1]
[*]Buy new RAM: nah :)
[*]use the kernel option mem=###M: this would half my amount of RAM memory, don't want to use that option neither
[*]build a custom kernel with the badram module: never done anything like it, I would prefer an easier solution
[*]use the memmap option for grub
[/LIST]

I prefer to do the last option (found it at [http://gquigs.blogspot.com/2009/01/bad-memory-howto.html]("http://gquigs.blogspot.com/2009/01/bad-memory-howto.html") and tried to follow the instructions (just adding some stuff to /boot/grub/menu.lst). But it seems that Ubuntu 9.10 uses GRUB 2 and menu.lst isn't there anymore...

Does anyone have an idea how to do this with GRUB 2?

Thanks in advance,

DuXati

---

### Post by sisco311 on 2009-12-01
First test if the memmap option works for you. Reboot the computer. At the grub menu highlight the Ubuntu menu entry (You may have to hold down the Shift key to see the menu). Press e for edit. Add your option to the kernel line and press Ctrl+x to boot.

If you can boot in Ubuntu, then test it for a while, open a lot of applications to fill up the RAM...

To make the changes permanent, edit the /etc/default/grub file:
```
gksu gedit /etc/default/grub
```
and add the boot parameter to the *GRUB_CMDLINE_LINUX* line:
```
GRUB_CMDLINE_LINUX="20M\$280M"
```

NOTE: $, % and # are special characters you have to escape them. \ preserves  the literal  value  of the next character that follows.

Run:
```
sudo update-grub
```

Open /boot/grub/grub.cfg for read to see if the menu entries are created correcly.

---

### Post by DuXati on 2009-12-02
Thanks for the quick reply!

I've given it a try but got an error when booting, could you take a look at what I've done?

In grub, I edited the entry for booting Ubuntu. Specifically, there was this line:

```
linux /boot/linuz-2.6.31-15-generic root=UUID=89...2be ro  quiet splash
```

Notice the two spaces between 'ro' and 'quiet splash', do they matter?

I added memmap=10M$280M to the line in the following ways:

```
linux /boot/linuz-2.6.31-15-generic root=UUID=89...2be ro  quiet splash memmap=10M$280M
```

```
linux /boot/linuz-2.6.31-15-generic root=UUID=89...2be ro memmap=10M$280M  quiet splash
```

In both cases, I got this error:

```
[ 0.125377]Kernel panic - not syncing: Out of memory and no killable processes...
[ 0.125383] <cursor here>
```

Don't know if the number in front gives you any info :p Anyway, is there something wrong with the memmap command? For example, are there fixed number which I can exclude or can I exclude any range of memory? Or is the location of the memmap command in the grub line wrong?

Thanks again!

---

### Post by sisco311 on 2009-12-02
The location of the memmap kernel parameter and the spaces in the parameter list do not matter.

After playing a little with memmap I think I found the solution.

With memmap=10M$280M I got a kernel panic too. :)

memmap=280M@0M memmap=734M@290M worked for me.


so try:
```
linux /boot/linuz-2.6.31-15-generic root=UUID=89...2be ro  quiet splash memmap=280M@0M memmap=734M@290M
```

Where 734M is the total amount of RAM minus 290 (in megabyte).

memmap=280M@0M - use 280M of RAM from 0

memmap=734M@290M - and 734M of RAM from 290M

I have 1G=1024M of RAM. 734M=1024M-290M

```
memmap=nn[KMG]@ss[KMG]
                        [KNL] Force usage of a specific region of memory
                        Region of memory to be used, from ss to ss+nn.
```

---

### Post by DuXati on 2009-12-02
This seems to work, I'll give it a try for a while.

Thanks a lot for the quick replies!!

DuXati

---

