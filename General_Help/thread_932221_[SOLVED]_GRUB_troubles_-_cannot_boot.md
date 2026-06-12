---
title: "[SOLVED] GRUB troubles - cannot boot"
date: 2008-09-28
forum: General Help
---

### Post by MunkyJunky on 2008-09-28
Last night I installed the QGrubEditor (or something by a very similar name) from Add/Remove programs. It was, as the name suggests, an editor for the GRUB menu (since my GRUB still suggests I can boot from the install on /dev/sdb, which no longer exists). After opening the program, it crashed a few seconds later, and wouldn't open again. I thought nothing of it until this morning. 

Now when I turn on my computer, GRUB just gives me an input prompt, which looks like this:

```

GRUB LOADING, PLEASE WAIT...

GRUB > 

```

Anyone know how I can fix this? I have a copy of the Ubuntu 8.04 LiveCD with me, but thats about it. 

Any help appreciated!

---

### Post by Naiki Muliaina on 2008-09-28
If you get properly stuck with this, and need to just reinstall grub, this thread may help:

[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

The secound post is better :)

---

### Post by fooman on 2008-09-28
have a look at this:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by MunkyJunky on 2008-09-28
Thanks for the speedy help! I'll get on doing that now.

---

### Post by MunkyJunky on 2008-09-28
When running the command 'Setup (hd0)' I get the error message:
> Error 17: Cannot mount selected partition

Little confused. Help?

---

### Post by fooman on 2008-09-28
what was the output of "find /boot/grub/stage1" ?

---

### Post by davidryder on 2008-09-28
Do you know what partition Ubuntu is on?

---

### Post by Naiki Muliaina on 2008-09-28
Youll need a comma and a secound number (first number is for drive, secound is partition grub is on). So it may be : ```
Setup hd(0,1) 
```
It depends where your Ubuntu is.

---

### Post by MunkyJunky on 2008-09-28
Ubuntu is the only thing installed on here. Here's a full list of everything: ```

         [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd0,0)
grub> root (hd0,1)
grub> setup (hd0)

Error 17: Cannot mount selected partition

grub> 

```

Also, grub> setup (hd0,0) and grub> setup (hd0,1) provide the same error.

---

### Post by Naiki Muliaina on 2008-09-28
Ignore this post, i didnt read properly :)

---

### Post by fooman on 2008-09-28
try:  grub> root (hd0,0)

instead of grub> root (hd0,1)

---

### Post by MunkyJunky on 2008-09-28
That gives more response. Running grub > setup (hd0) gives a few lines of output, and the nice word 'Succeeded', but when rebooting, nothing happens. 

Running setup (hd0,0) also shows a few lines, but has an error (not fatal). Wargh. Still no linux.

Bare with me while I type it all out!

---

### Post by MunkyJunky on 2008-09-28
```

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.

grub >

```

and 

```

grub> setup (hd0,0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed this is not fatal)
Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed this is not fatal)
 Running "install /boot/grub/stage1 (hd0,0) /boot/grub/stage2 p /boot/grub/menu.lst"... succeeded
Done.

grub >

```

and 

```

grub> setup (hd0,1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,1)"... failed this is not fatal)
Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed this is not fatal)
 Running "install /boot/grub/stage1 (hd0,1) /boot/grub/stage2 p /boot/grub/menu.lst"... succeeded
Done.

grub >

```

---

### Post by fooman on 2008-09-28
> **MunkyJunky said:**
> That gives more response. Running grub > setup (hd0) gives a few lines of output, and the nice word 'Succeeded', but when rebooting, nothing happens. 

sorry,  but what do you mean by "nothing happens"?

when you boot,  do you get to the grub menu?

if so,  what happens when you choose ubuntu? ...please post any error messages.

---

### Post by MunkyJunky on 2008-09-28
The computer goes through BIOS, then tries loading GRUB. Instead of the usual GRUB menu I've always got, I now get only

```

         [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub>
```

Thats it. I can't boot into Ubuntu off my HDD at all.

---

### Post by MunkyJunky on 2008-09-28
Fixed it. I decided to go have a browse though my boot/grub folder, via the Live CD. turns out I was missing a menu.lst file, but there was a menu.lst_origional in there. Copied, renamed, and I'm back booting in. Solved!

---

### Post by fooman on 2008-09-28
nevermind,  i see you got it fixed.  :)

---

