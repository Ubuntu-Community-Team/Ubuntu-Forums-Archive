---
title: "Why can't this be mounted?"
date: 2006-09-03
forum: Hardware &amp; Laptops
---

### Post by pentium on 2006-09-03
I recently had boot problems with my old SGI and in order to find the problem, I needed to view the drive and perform a backup. The problem is that I don't have the irix tapes anymore and the closest thing to unix I own is ubuntu. I can plug the drive in and the system can see the drive. The problem is that it can't see any of the partitions and thus can't mount the drive. I have been told that there two ways to fix this:

-enable EFS disk support and SGI disk labeling support
or
-load a custom kernel that includes the support

I am probably still way too new to ubuntu to be switching kernels and I can't find EFS disk support and SGI disk labeling support anywhere!

There is data on that drive that I need by the end of september for a project. I have school marks on the line.
I really need help on this one.

---

### Post by pentium on 2006-09-04
okay, I found a new kernel that can handle the disk but I don't know how the hell to run "make manuconfig".
any help?

---

### Post by christhemonkey on 2006-09-04
that should be:
```
make menuconfig 
```

and you will need build-essential aswell.
```
sudo apt-get install build-essential
```

---

### Post by pentium on 2006-09-04
> make manuconfig

oops, typo.](*,) 
I'll try it again and get back to you.

---

### Post by pentium on 2006-09-04
Okay, I ran sudo apt-get install build-essential and that went fine. I then retried make menuconfig and this is what I got:

john@ubuntu:/usr/src/linux-2.6.17$ make menuconfig
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/split-include
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/kconfig/conf.o
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/mconf.o
  SHIPPED scripts/kconfig/zconf.tab.c
  SHIPPED scripts/kconfig/lex.zconf.c
  SHIPPED scripts/kconfig/zconf.hash.c
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/mconf
  HOSTCC  scripts/kconfig/lxdialog/checklist.o
In file included from scripts/kconfig/lxdialog/checklist.c:24:
scripts/kconfig/lxdialog/dialog.h:31:20: error: curses.h: No such file or directory
In file included from scripts/kconfig/lxdialog/checklist.c:24:
scripts/kconfig/lxdialog/dialog.h:128: error: syntax error before ‘use_colors’
scripts/kconfig/lxdialog/dialog.h:128: warning: type defaults to ‘int’ in declaration of ‘use_colors’
scripts/kconfig/lxdialog/dialog.h:128: warning: data definition has no type or storage class
scripts/kconfig/lxdialog/dialog.h:129: error: syntax error before ‘use_shadow’
scripts/kconfig/lxdialog/dialog.h:129: warning: type defaults to ‘int’ in declaration of ‘use_shadow’
scripts/kconfig/lxdialog/dialog.h:129: warning: data definition has no type or storage class
scripts/kconfig/lxdialog/dialog.h:131: error: syntax error before ‘attributes’
scripts/kconfig/lxdialog/dialog.h:131: warning: type defaults to ‘int’ in declaration of ‘attributes’
scripts/kconfig/lxdialog/dialog.h:131: warning: data definition has no type or storage class
scripts/kconfig/lxdialog/dialog.h:143: error: syntax error before ‘*’ token
scripts/kconfig/lxdialog/dialog.h:143: warning: function declaration isn’t a prototype
scripts/kconfig/lxdialog/dialog.h:146: error: syntax error before ‘*’ token
scripts/kconfig/lxdialog/dialog.h:146: warning: function declaration isn’t a prototype
scripts/kconfig/lxdialog/dialog.h:147: error: syntax error before ‘*’ token
scripts/kconfig/lxdialog/dialog.h:147: warning: function declaration isn’t a prototype
scripts/kconfig/lxdialog/dialog.h:148: error: syntax error before ‘*’ token
scripts/kconfig/lxdialog/dialog.h:148: warning: function declaration isn’t a prototype
scripts/kconfig/lxdialog/dialog.h:149: error: syntax error before ‘*’ token
scripts/kconfig/lxdialog/dialog.h:150: warning: function declaration isn’t a prototype
scripts/kconfig/lxdialog/dialog.h:151: error: syntax error before ‘*’ token
scripts/kconfig/lxdialog/dialog.h:151: warning: function declaration isn’t a prototype
scripts/kconfig/lxdialog/checklist.c:31: error: syntax error before ‘*’ token
scripts/kconfig/lxdialog/checklist.c:33: warning: function declaration isn’t a prototype
scripts/kconfig/lxdialog/checklist.c: In function ‘print_item’:
scripts/kconfig/lxdialog/checklist.c:37: warning: implicit declaration of function ‘wattrset’
scripts/kconfig/lxdialog/checklist.c:37: error: ‘win’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:37: error: (Each undeclared identifier is reported only once
scripts/kconfig/lxdialog/checklist.c:37: error: for each function it appears in.)
scripts/kconfig/lxdialog/checklist.c:38: warning: implicit declaration of function ‘wmove’
scripts/kconfig/lxdialog/checklist.c:38: error: ‘choice’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:40: warning: implicit declaration of function ‘waddch’
scripts/kconfig/lxdialog/checklist.c:43: error: ‘selected’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:44: warning: implicit declaration of function ‘wprintw’
scripts/kconfig/lxdialog/checklist.c:44: error: ‘status’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:47: warning: implicit declaration of function ‘mvwaddch’
scripts/kconfig/lxdialog/checklist.c:47: error: ‘item’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:49: warning: implicit declaration of function ‘waddstr’
scripts/kconfig/lxdialog/checklist.c:52: warning: implicit declaration of function ‘wrefresh’
scripts/kconfig/lxdialog/checklist.c: At top level:
scripts/kconfig/lxdialog/checklist.c:59: error: syntax error before ‘*’ token
scripts/kconfig/lxdialog/checklist.c:61: warning: function declaration isn’t a prototype
scripts/kconfig/lxdialog/checklist.c: In function ‘print_arrows’:
scripts/kconfig/lxdialog/checklist.c:62: error: ‘win’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:62: error: ‘y’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:62: error: ‘x’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:64: error: ‘scroll’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:76: error: ‘height’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:79: error: ‘item_no’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:79: error: ‘choice’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c: At top level:
scripts/kconfig/lxdialog/checklist.c:95: error: syntax error before ‘*’ token
scripts/kconfig/lxdialog/checklist.c:96: warning: function declaration isn’t a prototype
scripts/kconfig/lxdialog/checklist.c: In function ‘print_buttons’:
scripts/kconfig/lxdialog/checklist.c:97: error: ‘width’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:98: error: ‘height’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:100: error: ‘dialog’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:100: error: ‘selected’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c: In function ‘dialog_checklist’:
scripts/kconfig/lxdialog/checklist.c:117: error: ‘WINDOW’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:117: error: ‘dialog’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:117: error: ‘list’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:117: warning: left-hand operand of comma expression has no effect
scripts/kconfig/lxdialog/checklist.c:117: warning: statement with no effect
scripts/kconfig/lxdialog/checklist.c:121: warning: implicit declaration of function ‘endwin’
scripts/kconfig/lxdialog/checklist.c:122: warning: implicit declaration of function ‘fprintf’
scripts/kconfig/lxdialog/checklist.c:122: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/kconfig/lxdialog/checklist.c:122: error: ‘stderr’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:140: error: ‘COLS’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:141: error: ‘LINES’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:143: error: ‘stdscr’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:145: warning: implicit declaration of function ‘newwin’
scripts/kconfig/lxdialog/checklist.c:146: warning: implicit declaration of function ‘keypad’
scripts/kconfig/lxdialog/checklist.c:146: error: ‘TRUE’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:166: warning: implicit declaration of function ‘subwin’
scripts/kconfig/lxdialog/checklist.c:199: warning: implicit declaration of function ‘wnoutrefresh’
scripts/kconfig/lxdialog/checklist.c:201: warning: implicit declaration of function ‘doupdate’
scripts/kconfig/lxdialog/checklist.c:204: warning: implicit declaration of function ‘wgetch’
scripts/kconfig/lxdialog/checklist.c:211: error: ‘KEY_UP’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:211: error: ‘KEY_DOWN’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:221: error: ‘FALSE’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:222: warning: implicit declaration of function ‘scrollok’
scripts/kconfig/lxdialog/checklist.c:223: warning: implicit declaration of function ‘wscrl’
scripts/kconfig/lxdialog/checklist.c:282: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/kconfig/lxdialog/checklist.c:283: warning: implicit declaration of function ‘delwin’
scripts/kconfig/lxdialog/checklist.c:287: error: ‘KEY_LEFT’ undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:288: error: ‘KEY_RIGHT’ undeclared (first use in this function)
make[2]: *** [scripts/kconfig/lxdialog/checklist.o] Error 1
make[1]: *** [menuconfig] Error 2
make: *** [menuconfig] Error 2

Something tells me this is not a good sign.

---

### Post by lupine_nickt on 2006-09-04
No, this is fine :). You also need to install the package "libncurses5-dev" (which the program build by make menuconfig uses)

To make your life easy, I'd suggest that you install that (sudo apt-get install libncurses5-dev), then run "make oldconfig" - this will mirror your current kernel settings to the new one. Then you just need to "make menuconfig", and change the specific options you need to, without worrying about the rest.

Note that any or all of the make commands might need preceeding by sudo, depending on how your kernel source directory is set up...

xF,

...Nick

---

### Post by pentium on 2006-09-04
I'll give it a go and post back when done.

---

### Post by pentium on 2006-09-04
okay, now I am really pissed.
I did what you said and everything went fine.
After I was done I opened the disks panel and suddenly one disk started to click at .5 second intervals and the system froze. After a hard shutdown and powerup the entire primary IDE system is not detecting drives and that drive is still clicking.
What the hell went wrong?

---

### Post by pentium on 2006-09-04
Oh yeah, something very big happened.
The clicking drive's chipset immdiately heats up to finger-burning levels so it's completely toasted!
The other drive, the drive that holds ubuntu has lost it's ability to be a master and can only boot halfway into ubuntu before hanging. This is terrible. Now not only am I back at square one with the sgi drive (which has survived the incident) but I also lost our entire home server and anything stored on it!
If I find out that this was software caused, I'm quitting linux for good!

---

