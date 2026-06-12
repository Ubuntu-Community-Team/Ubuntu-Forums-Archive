---
title: "Help installing Predict software"
date: 2008-10-14
forum: General Help
---

### Post by pscl227 on 2008-10-14
Hi hoping i can get some help here I have been tearing my hair out with this problem! I am no Linux guru so please be kind!

I am running 32-bit ubuntu 8.0.4 on VMware workstation, I am using Linux for a project I am doing to map satellite orbits in real time. 

Anyway i am trying to install a program called "Predict-2.2.3" (which can be found [here]("http://www.qsl.net/kd2bd/predict.html") for anyone interested)

Here is what I am doing:
==================
sudo bash
cd /home/paul/Desktop
    tar xvzf predict-2.2.3.tar.gz
==================


it then decompresses successfully 

========================
cd /home/paul/Desktop/predict-2.2.3
    ./configure
========================

after which it throws up these errors:
> root@paul-desktop:~/Desktop/predict-2.2.3# ./configure
One moment please... installer.c:16:20: error: curses.h: No such file or directory
installer.c:17:20: error: unistd.h: No such file or directory
installer.c:18:20: error: stdlib.h: No such file or directory
installer.c:19:20: error: string.h: No such file or directory
installer.c:20:19: error: fcntl.h: No such file or directory
installer.c:21:23: error: sys/ioctl.h: No such file or directory
installer.c:22:27: error: sys/soundcard.h: No such file or directory
installer.c: In function ‘logo’:
installer.c:28: warning: implicit declaration of function ‘attrset’
installer.c:28: warning: implicit declaration of function ‘COLOR_PAIR’
installer.c:28: error: ‘A_REVERSE’ undeclared (first use in this function)
installer.c:28: error: (Each undeclared identifier is reported only once
installer.c:28: error: for each function it appears in.)
installer.c:28: error: ‘A_BOLD’ undeclared (first use in this function)
installer.c:29: warning: implicit declaration of function ‘mvprintw’
installer.c: In function ‘main’:
installer.c:41: error: ‘FILE’ undeclared (first use in this function)
installer.c:41: error: ‘infile’ undeclared (first use in this function)
installer.c:41: error: ‘outfile’ undeclared (first use in this function)
installer.c:41: warning: left-hand operand of comma expression has no effect
installer.c:43: warning: implicit declaration of function ‘initscr’
installer.c:44: warning: implicit declaration of function ‘start_color’
installer.c:45: warning: implicit declaration of function ‘cbreak’
installer.c:46: warning: implicit declaration of function ‘scrollok’
installer.c:46: error: ‘stdscr’ undeclared (first use in this function)
installer.c:46: error: ‘TRUE’ undeclared (first use in this function)
installer.c:48: warning: implicit declaration of function ‘init_pair’
installer.c:48: error: ‘COLOR_WHITE’ undeclared (first use in this function)
installer.c:48: error: ‘COLOR_BLUE’ undeclared (first use in this function)
installer.c:49: error: ‘COLOR_RED’ undeclared (first use in this function)
installer.c:50: error: ‘COLOR_CYAN’ undeclared (first use in this function)
installer.c:51: error: ‘COLOR_GREEN’ undeclared (first use in this function)
installer.c:52: error: ‘COLOR_YELLOW’ undeclared (first use in this function)
installer.c:56: warning: implicit declaration of function ‘getcwd’
installer.c:57: warning: implicit declaration of function ‘open’
installer.c:57: error: ‘O_WRONLY’ undeclared (first use in this function)
installer.c:60: warning: implicit declaration of function ‘close’
installer.c:62: warning: implicit declaration of function ‘fopen’
installer.c:63: warning: implicit declaration of function ‘fscanf’
installer.c:63: warning: incompatible implicit declaration of built-in function ‘fscanf’
installer.c:64: warning: implicit declaration of function ‘fclose’
installer.c:66: warning: implicit declaration of function ‘bkgdset’
installer.c:66: error: ‘A_BOLD’ undeclared (first use in this function)
installer.c:67: warning: implicit declaration of function ‘clear’
installer.c:68: warning: implicit declaration of function ‘refresh’
installer.c:73: warning: implicit declaration of function ‘printw’
installer.c:88: warning: implicit declaration of function ‘getch’
installer.c:96: warning: implicit declaration of function ‘curs_set’
installer.c:110: warning: implicit declaration of function ‘fprintf’
installer.c:110: warning: incompatible implicit declaration of built-in function ‘fprintf’
installer.c:130: warning: implicit declaration of function ‘system’
installer.c:158: warning: implicit declaration of function ‘strncpy’
installer.c:158: warning: incompatible implicit declaration of built-in function ‘strncpy’
installer.c:165: warning: implicit declaration of function ‘strlen’
installer.c:165: warning: incompatible implicit declaration of built-in function ‘strlen’
installer.c:177: warning: implicit declaration of function ‘sprintf’
installer.c:177: warning: incompatible implicit declaration of built-in function ‘sprintf’
installer.c:178: warning: implicit declaration of function ‘unlink’
installer.c:180: warning: implicit declaration of function ‘symlink’
installer.c:200: warning: implicit declaration of function ‘beep’
installer.c:208: warning: implicit declaration of function ‘endwin’
installer.c:209: warning: implicit declaration of function ‘exit’
installer.c:209: warning: incompatible implicit declaration of built-in function ‘exit’
Compilation failed.  Are you sure you have a C compiler (gcc) installed?
root@paul-desktop:~/Desktop/predict-2.2.3#

any help much appreaciated!

Paul

---

### Post by justleen on 2008-10-14
it cant find the required librares and executables.. i have the same problem here.. Its not very well documented what flags the configure scripts uses.. 

How ever, there is a debian installer.. And its available trough apt, yuy!
```

apt-cache search predict |grep -i satellite
gpredict - Satellite tracking program for GNOME
ktrack - KDE Satellite tracking program
predict - Satellite Tracking Program with Optional Voice Output
predict-gsat - Graphical Satellite Tracking Client Program

```

---

