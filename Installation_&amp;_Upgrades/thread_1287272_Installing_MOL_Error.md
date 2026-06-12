---
title: "Installing MOL Error"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by mikethedj4 on 2009-10-09
ok so I extracted the mol-0.9.72.1 folder in the tarball onto my desktop, opened the terminal, and put it into the folder, and then ran ./autogen.sh. Everything went perfect untill I tried make install.

This is what I got in the terminal

speed@ubuntu:~$ cd ~/Desktop/mol-0/9/72.1
bash: cd: /home/speed/Desktop/mol-0/9/72.1: No such file or directory
speed@ubuntu:~$ cd ~/Desktop/mol-0.9.72.1
speed@ubuntu:~/Desktop/mol-0.9.72.1$ ./autogen.sh
==================================================
 Invoking autoheader and autoconf.
 The next step is 'make'
==================================================
speed@ubuntu:~/Desktop/mol-0.9.72.1$ make
checking whether ln -s works... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for bison... no
checking for byacc... no
checking for flex... no
checking for lex... no
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for strings.h... (cached) yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking poll.h usability... yes
checking poll.h presence... yes
checking for poll.h... yes
checking obstack.h usability... yes
checking obstack.h presence... yes
checking for obstack.h... yes
checking dependency style... new
checking for clearenv()... yes
checking ncurses.h usability... no
checking ncurses.h presence... no
checking for ncurses.h... no
checking for snd_pcm_open in -lasound... no
checking alsa/asoundlib.h usability... no
checking alsa/asoundlib.h presence... no
checking for alsa/asoundlib.h... no
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for working XDGA headers... no
checking whether XDGA workaround works... no
checking for m4... m4
checking for as... as
checking for strip... strip 
checking for ld... ld
checking for nm... nm
checking for objdump... objdump
checking for install... install
checking whether off_t is 64 bit... yes
checking for broken syscall macro... yes
checking for uc_context.gregs... yes
checking for png_read_png in -lpng... yes
checking png.h usability... yes
checking png.h presence... yes
checking for png.h... yes
checking for -fno-stack-protector support... yes
checking for inflate in -lz... yes
configure: creating ./config.status
config.status: creating unconfig
config.status: creating Makefile.defs
config.status: creating config.h
+ Entering lxdialog
    Compiling    checklist.o         
In file included from checklist.c:24:
dialog.h:31:20: error: curses.h: No such file or directory
In file included from checklist.c:24:
dialog.h:128: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;use_colors&#8217;
dialog.h:129: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;use_shadow&#8217;
dialog.h:131: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;attributes&#8217;
dialog.h:143: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
dialog.h:146: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
dialog.h:147: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
dialog.h:148: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
dialog.h:149: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
dialog.h:151: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
checklist.c:31: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
checklist.c:59: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
checklist.c:95: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
checklist.c: In function &#8216;dialog_checklist&#8217;:
checklist.c:117: error: &#8216;WINDOW&#8217; undeclared (first use in this function)
checklist.c:117: error: (Each undeclared identifier is reported only once
checklist.c:117: error: for each function it appears in.)
checklist.c:117: error: &#8216;dialog&#8217; undeclared (first use in this function)
checklist.c:117: error: &#8216;list&#8217; undeclared (first use in this function)
checklist.c:117: warning: left-hand operand of comma expression has no effect
checklist.c:121: warning: implicit declaration of function &#8216;endwin&#8217;
checklist.c:122: warning: implicit declaration of function &#8216;fprintf&#8217;
checklist.c:122: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
checklist.c:122: error: &#8216;stderr&#8217; undeclared (first use in this function)
checklist.c:140: error: &#8216;COLS&#8217; undeclared (first use in this function)
checklist.c:141: error: &#8216;LINES&#8217; undeclared (first use in this function)
checklist.c:143: warning: implicit declaration of function &#8216;draw_shadow&#8217;
checklist.c:143: error: &#8216;stdscr&#8217; undeclared (first use in this function)
checklist.c:145: warning: implicit declaration of function &#8216;newwin&#8217;
checklist.c:146: warning: implicit declaration of function &#8216;keypad&#8217;
checklist.c:146: error: &#8216;TRUE&#8217; undeclared (first use in this function)
checklist.c:148: warning: implicit declaration of function &#8216;draw_box&#8217;
checklist.c:148: error: &#8216;attributes&#8217; undeclared (first use in this function)
checklist.c:149: warning: implicit declaration of function &#8216;wattrset&#8217;
checklist.c:150: warning: implicit declaration of function &#8216;mvwaddch&#8217;
checklist.c:152: warning: implicit declaration of function &#8216;waddch&#8217;
checklist.c:156: warning: implicit declaration of function &#8216;print_title&#8217;
checklist.c:159: warning: implicit declaration of function &#8216;print_autowrap&#8217;
checklist.c:166: warning: implicit declaration of function &#8216;subwin&#8217;
checklist.c:191: warning: implicit declaration of function &#8216;print_item&#8217;
checklist.c:197: warning: implicit declaration of function &#8216;print_arrows&#8217;
checklist.c:200: warning: implicit declaration of function &#8216;print_buttons&#8217;
checklist.c:202: warning: implicit declaration of function &#8216;wnoutrefresh&#8217;
checklist.c:204: warning: implicit declaration of function &#8216;doupdate&#8217;
checklist.c:207: warning: implicit declaration of function &#8216;wgetch&#8217;
checklist.c:214: error: &#8216;KEY_UP&#8217; undeclared (first use in this function)
checklist.c:214: error: &#8216;KEY_DOWN&#8217; undeclared (first use in this function)
checklist.c:224: error: &#8216;FALSE&#8217; undeclared (first use in this function)
checklist.c:225: warning: implicit declaration of function &#8216;scrollok&#8217;
checklist.c:226: warning: implicit declaration of function &#8216;wscrl&#8217;
checklist.c:235: warning: implicit declaration of function &#8216;wrefresh&#8217;
checklist.c:285: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
checklist.c:286: warning: implicit declaration of function &#8216;delwin&#8217;
checklist.c:290: error: &#8216;KEY_LEFT&#8217; undeclared (first use in this function)
checklist.c:291: error: &#8216;KEY_RIGHT&#8217; undeclared (first use in this function)
make[2]: *** [../../obj-amd64/build/config/lxdialog/checklist.o] Error 1
make[1]: *** [sub-lxdialog-all] Error 2
make: *** [do-bootstrap] Error 2
speed@ubuntu:~/Desktop/mol-0.9.72.1$ 

How can I fix this, and get mol running???

---

### Post by aheckler on 2009-10-10
Try "sudo make install".

---

### Post by mikethedj4 on 2009-10-10
same error

speed@ubuntu:~/Desktop/mol-0.9.72.1$ sudo make install
[sudo] password for speed: 
mkdir: cannot create directory `./obj-amd64/lib/modules': No such file or directory
make: *** [install-modules] Error 1

Now when I put in the missing folders (lib and modules in the obj-amd64 folder) I get this.

speed@ubuntu:~/Desktop/mol-0.9.72.1$ sudo make install
cd: 4: can't cd to ./obj-amd64/lib/bin
cd: 3: can't cd to ./obj-amd64/lib/bin
install: cannot stat `startmol': No such file or directory
make: *** [install] Error 1
speed@ubuntu:~/Desktop/mol-0.9.72.1$

---

### Post by Partyboi2 on 2009-10-10
> In file included from checklist.c:24:
dialog.h:31:20: error: curses.h: No such file or directory
Hi, try installing the libncurses5-dev package
```
sudo apt-get install libncurses5-dev
```
then
```
./autogen.sh
```

---

### Post by mikethedj4 on 2009-10-10
After I successfully installed the package I accidentally closed out of the terminal, but opened it back up  ran ./autogen.sh in the terminal, and this is what I got.

speed@ubuntu:~$ cd ~/Desktop/mol-0.9.72.1
speed@ubuntu:~/Desktop/mol-0.9.72.1$ ./autogen.sh
==================================================
 Invoking autoheader and autoconf.
 The next step is 'make'
==================================================
speed@ubuntu:~/Desktop/mol-0.9.72.1$ make
config.status: creating unconfig
config.status: creating Makefile.defs
config.status: creating config.h
config.status: config.h is unchanged
+ Entering lxdialog
    Compiling    checklist.o         
    Compiling    menubox.o           
    Compiling    textbox.o           
    Compiling    yesno.o             
    Compiling    inputbox.o          
    Compiling    util.o              
    Compiling    lxdialog.o          
lxdialog.c: In function ‘j_inputbox’:
lxdialog.c:192: warning: format not a string literal and no format arguments
    Compiling    msgbox.o            
= Building lxdialog              
+ Entering kconfig
    Compiling    zconf-y.o           
lex.yy.c:2992: warning: ‘input’ defined but not used
    Linking      libkconf.a            
    Compiling    mconf.o             
mconf.c: In function ‘exec_conf’:
mconf.c:225: warning: ignoring return value of ‘pipe’, declared with attribute warn_unused_result
mconf.c: In function ‘show_textbox’:
mconf.c:553: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
= Building mconfig               
    Compiling    conf.o              
conf.c: In function ‘conf_askvalue’:
conf.c:94: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
conf.c: In function ‘conf_choice’:
conf.c:350: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
= Building config                
can't find file config/Kconfig-amd64
make[2]: *** [menuconfig] Error 1
make[1]: *** [menuconfig] Error 2
make: *** [do-bootstrap] Error 2
speed@ubuntu:~/Desktop/mol-0.9.72.1$ 

I feel I'm missing other packages, but I don't know what to do from here.

---

