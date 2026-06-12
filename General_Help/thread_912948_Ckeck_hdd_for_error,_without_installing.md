---
title: "Ckeck hdd for error, without installing"
date: 2008-09-07
forum: General Help
---

### Post by SpinningAround on 2008-09-07
I have problem with installation and the program say it might be because of my hard drive so I wonder if it's possible to check the disk for errors without without having ubuntu installed

---

### Post by Scunge on 2008-09-07
Well you need to run the check from *something*, but that something can be an Ubuntu installation in memory from a Live CD. This will not install anything on your actual disk unless you tell it to.

So from a Live CD, you can run a disk checking program on each of your partitions. If you have no partitions yet, I suggest you create the ones you are going to use, formatted as you want, so that the bad block information can be preserved for when you install.

See the second part of [**[color=blue]this post[/color]**](http://ubuntuforums.org/showthread.php?p=5694697#post5694697) for the command I would run in this situation.

Now, the "p" option (missing in that example) repairs the disk if it is safe to do so, otherwise fsck exits. You can add this if you like, but to be honest, unless you know exactly what each fix question means you'll just end up running fsck without the "p" and pressing "y" to every question anyway. And if you knew enough to do that, you probably wouldn't be asking in here about what to do.

So add "y" to the option list instead, making it ```
fsck -ycckfv /dev/sdax
```

What this does is to answer "yes" to every fix question without you having to sit there looking for them. If that doesn't work (the manual page says sometimes it doesn't), do ```
fsck -cckfv /dev/sdax < yes
```which inputs "y" every time a question is asked (run "yes" in a terminal to see what I mean, "<" means use that output as input to the main program being run).

Then wait quite a while...

After it's all finished, and you've done every partition, do the install but don't format any partitions that had errors. If you do, you'll lose any bad block info stored by fsck during your checks.

---

### Post by caljohnsmith on 2008-09-07
Another option is you can download something like the [Ultimate Boot CD]("http://www.ultimatebootcd.com"), which has lots of HDD diagnostic tests you can run. It's also a very useful CD for troubleshooting when things go wrong on your computer.

---

### Post by SpinningAround on 2008-09-13
Thanks for the replays, but happened to notice that fsck can't check ntfs, where I think I problem is even if not SCANDISK or samsungs own test program report any errors. If there would be a error on a disk would it be enough for ubuntu's installation parition program to crash?

---

