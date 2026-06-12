---
title: "Need GLIBC_2.2"
date: 2008-08-29
forum: General Help
---

### Post by kuloch on 2008-08-29
At least, I'm hoping that's all I need.  I'll include details as they're requested or seem pertinent.

I'm trying to compile/install a Cisco VPN client, more-or-less required by my university to use their wireless network.  The included "installation instructions" are rather paltry (and there's no README or INSTALL), but do note: "The VPN Client now requires GLIBC_2.2 and libstdc++.so.5".

I managed to pull from the forum that: 
```
apt-get install libstdc++5
```
... takes care of the second dependency, but doing the same with "glibc-2.2*" yields: "Note, selecting glibc-2.7-1 for regex 'glibc-2.2*'".  Using "GLIBC_2.2" doesn't match anything, nor does "glibc-2.2-*" or just "glibc-2.2".

That aside, running what I assume is the installer ('./driver_build.sh') tells me to provide the kernel source folder as a parameter.  I ended up finding '/usr/src/linux-headers-2.6.24-19', so I ran: 
```
./driver_build.sh /usr/src/linux-headers-2.6.24-19
```
... which tells me:
> ERROR: Kernel configuration is invalid.
         include/linux/autoconf.h or include/config/auto.conf are missing.
         Run 'make oldconfig && make prepare' on kernel src to fix it.

Ok, so I cd to the above src dir and run 'make oldconfig && make prepare'.  That spits out a whole slew of errors that complain about nonexistent files.  Perhaps this is all due to not having GLIBC_2.2?

Sorry if this is a bit all over.  I'm much more used to Fedora's yum.  I recall adding repositories with different packages, but I don't know where to start with atp-get.  And the ridiculous documentation for the VPN client has me wondering whether I'm even in the right direction.

---

### Post by fooman on 2008-08-29
glibc-source is available from the repos.  ...that should give you the latest glibc library.  i would try that,  then try installing vpn client again.  you could use synaptic (system > administration > synaptic package manager) or in a terminal:

```
sudo apt-get install glibc-source
```

also -you can use synaptic to enable the universe/multiverse repositories...just open synaptic and in the toolbar, go to settings > repositories

click on the ubuntu software tab and check off all the choices.  next, click the updates tab...put a check next to the top 3 choices under ubuntu updates.  click the close button and you will see a warning that the repos have changed...click close on that box,  then click the "reload" button.  next, you can click "mark all updates",  then "apply".  that will update all your packages.

---

### Post by kuloch on 2008-08-29
Oh...  I had thought that the "Applications > Add/Remove..." was Synaptic (which it apparently is, as an error was thrown when I opened them at the same time).

Ok, so now I have glibc-source installed (and confirmed that Synaptic sees libstdc++5).  Unfortunately, that doesn't seem to have any effect on the error messages I'm getting.  ./driver_build.sh still says I need to 'make oldconfig && make prepare' in the kernel's source folder, and doing so spits out the following:

```

kuloch@kuloch-laptop:/usr/src/linux-headers-2.6.24-19$ sudo make oldconfig && make prepare
  HOSTCC  scripts/basic/fixdep
scripts/basic/fixdep.c:107:23: error: sys/types.h: No such file or directory
scripts/basic/fixdep.c:108:22: error: sys/stat.h: No such file or directory
scripts/basic/fixdep.c:109:22: error: sys/mman.h: No such file or directory
scripts/basic/fixdep.c:110:20: error: unistd.h: No such file or directory
scripts/basic/fixdep.c:111:19: error: fcntl.h: No such file or directory
scripts/basic/fixdep.c:112:20: error: string.h: No such file or directory
scripts/basic/fixdep.c:113:20: error: stdlib.h: No such file or directory
scripts/basic/fixdep.c:114:19: error: stdio.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.2.3/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.2.3/include/limits.h:11,
                 from scripts/basic/fixdep.c:115:
/usr/lib/gcc/i486-linux-gnu/4.2.3/include/limits.h:122:61: error: limits.h: No such file or directory
scripts/basic/fixdep.c:116:19: error: ctype.h: No such file or directory
scripts/basic/fixdep.c:117:23: error: arpa/inet.h: No such file or directory
scripts/basic/fixdep.c: In function ‘usage’:
scripts/basic/fixdep.c:131: warning: implicit declaration of function ‘fprintf’
scripts/basic/fixdep.c:131: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:131: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:131: error: (Each undeclared identifier is reported only once
scripts/basic/fixdep.c:131: error: for each function it appears in.)
scripts/basic/fixdep.c:132: warning: implicit declaration of function ‘exit’
scripts/basic/fixdep.c:132: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c: In function ‘print_cmdline’:
scripts/basic/fixdep.c:140: warning: implicit declaration of function ‘printf’
scripts/basic/fixdep.c:140: warning: incompatible implicit declaration of built-in function ‘printf’
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:143: error: ‘NULL’ undeclared here (not in a function)
scripts/basic/fixdep.c: In function ‘grow_config’:
scripts/basic/fixdep.c:156: warning: implicit declaration of function ‘realloc’
scripts/basic/fixdep.c:156: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:158: warning: implicit declaration of function ‘perror’
scripts/basic/fixdep.c:158: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c: In function ‘is_defined_config’:
scripts/basic/fixdep.c:174: warning: implicit declaration of function ‘memcmp’
scripts/basic/fixdep.c: In function ‘define_config’:
scripts/basic/fixdep.c:187: warning: implicit declaration of function ‘memcpy’
scripts/basic/fixdep.c:187: warning: incompatible implicit declaration of built-in function ‘memcpy’
scripts/basic/fixdep.c: In function ‘use_config’:
scripts/basic/fixdep.c:206: error: ‘PATH_MAX’ undeclared (first use in this function)
scripts/basic/fixdep.c:214: warning: incompatible implicit declaration of built-in function ‘memcpy’
scripts/basic/fixdep.c:220: warning: implicit declaration of function ‘tolower’
scripts/basic/fixdep.c:222: warning: incompatible implicit declaration of built-in function ‘printf’
scripts/basic/fixdep.c:206: warning: unused variable ‘s’
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:225: error: expected declaration specifiers or ‘...’ before ‘size_t’
scripts/basic/fixdep.c: In function ‘parse_config_file’:
scripts/basic/fixdep.c:227: error: ‘len’ undeclared (first use in this function)
scripts/basic/fixdep.c:233: warning: implicit declaration of function ‘ntohl’
scripts/basic/fixdep.c:244: warning: implicit declaration of function ‘isalnum’
scripts/basic/fixdep.c: In function ‘strrcmp’:
scripts/basic/fixdep.c:261: warning: implicit declaration of function ‘strlen’
scripts/basic/fixdep.c:261: warning: incompatible implicit declaration of built-in function ‘strlen’
scripts/basic/fixdep.c: In function ‘do_config_file’:
scripts/basic/fixdep.c:272: error: storage size of ‘st’ isn’t known
scripts/basic/fixdep.c:276: warning: implicit declaration of function ‘open’
scripts/basic/fixdep.c:276: error: ‘O_RDONLY’ undeclared (first use in this function)
scripts/basic/fixdep.c:278: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:278: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:280: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c:282: warning: implicit declaration of function ‘fstat’
scripts/basic/fixdep.c:284: warning: implicit declaration of function ‘close’
scripts/basic/fixdep.c:287: warning: implicit declaration of function ‘mmap’
scripts/basic/fixdep.c:287: error: ‘PROT_READ’ undeclared (first use in this function)
scripts/basic/fixdep.c:287: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
scripts/basic/fixdep.c:287: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:294: error: too many arguments to function ‘parse_config_file’
scripts/basic/fixdep.c:296: warning: implicit declaration of function ‘munmap’
scripts/basic/fixdep.c:272: warning: unused variable ‘st’
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:301: error: expected declaration specifiers or ‘...’ before ‘size_t’
scripts/basic/fixdep.c: In function ‘parse_dep_file’:
scripts/basic/fixdep.c:304: error: ‘len’ undeclared (first use in this function)
scripts/basic/fixdep.c:306: error: ‘PATH_MAX’ undeclared (first use in this function)
scripts/basic/fixdep.c:308: warning: implicit declaration of function ‘strchr’
scripts/basic/fixdep.c:308: warning: incompatible implicit declaration of built-in function ‘strchr’
scripts/basic/fixdep.c:310: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:310: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:311: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c:313: warning: incompatible implicit declaration of built-in function ‘memcpy’
scripts/basic/fixdep.c:314: warning: incompatible implicit declaration of built-in function ‘printf’
scripts/basic/fixdep.c:306: warning: unused variable ‘s’
scripts/basic/fixdep.c: In function ‘print_deps’:
scripts/basic/fixdep.c:343: error: storage size of ‘st’ isn’t known
scripts/basic/fixdep.c:347: error: ‘O_RDONLY’ undeclared (first use in this function)
scripts/basic/fixdep.c:349: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:349: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:351: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c:355: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:359: error: ‘PROT_READ’ undeclared (first use in this function)
scripts/basic/fixdep.c:359: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
scripts/basic/fixdep.c:359: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:366: error: too many arguments to function ‘parse_dep_file’
scripts/basic/fixdep.c:343: warning: unused variable ‘st’
scripts/basic/fixdep.c: In function ‘traps’:
scripts/basic/fixdep.c:378: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:378: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:380: warning: incompatible implicit declaration of built-in function ‘exit’
make[1]: *** [scripts/basic/fixdep] Error 1
make: *** [scripts_basic] Error 2

```

Any suggestions?  I don't even know where to start with all of that, as I'm more of a Java programmer.

---

### Post by kuloch on 2008-08-29
... if it helps, a find on string.h and types.h indicates that they're in /usr/src/linux-headers-2.6.24-19/include/, under various sub-folders such as 'asm-generic' and 'asm-x86'.

Can I just move these to where make seems to be looking for them?

---

### Post by kuloch on 2008-08-29
Copying string.h from include/linux/ back into /usr/src/linux... doesn't seem to help (still can't find it), nor does copying it into scripts/basic/.  I take it there's an environment var for the include path?  Perhaps something didn't set it correctly?  Or do I need glibc-2.2?

---

### Post by kuloch on 2008-08-30
Another problem that I suspect will have a very similar solution:

I'm trying to compile a .cpp file that uses GLUT, which was already installed but I went ahead and told Synaptic to also grab freeglut (which it looks like glut uses behind the scenes) and freeglut-dev.  I also got g++, as I couldn't seem to compile C++ (which just... seems odd that no C++ compiler was present).

Anyway, g++ seems to complain about 'undefined reference'(s), which are all of the gl* calls.  However, if I change '#include <GL/glut.h>' to '#include <glut.h>', it states that it can't find glut.h and says that all the gl* functions are 'not declared in this scope'.  It also seems to complain about some GL* constants that aren't mentioned in GL/glut.h's errors, so clearly <GL/glut.h> is hitting something.

Two of the complained-about functions are glutInit and glutInitWindowPosition, both of which are in the [freeglut API]("http://freeglut.sourceforge.net/docs/api.php#Initialization").  So I confirmed that it's at least seeing the header, but it's obviously not seeing something.

The compile command I used is:
```
g++ -o LineStipple LineStipple.cpp
```
Looking through freeglut_std.h, I can see the glutInit(...) definition.  Hmm, and running find on the fglut_init.c file that it mentions above that define isn't hitting anything.  I would tend to assume that either freeglut or freeglut-dev should provide either the .c source or some linkable binaries for the compiler to use.  Does Ubuntu require manual configuration for such things?

I can provide terminal pastes and source code as requested.  I'd prefer to not have to resort to using VisualC++, as the professor recommended.

---

### Post by kuloch on 2008-08-30
Adding yet again to my little personal blog, here...

I found a (somewhat dated) [linuxquestions.org post]("http://www.linuxquestions.org/questions/linux-software-2/help-installing-glut-157895/") that helped me get it to compile.  I guess it's necessary to tell g++ that it needs to use the glut library:
```
g++ -lglut -o LineStipple LineStipple.cpp
```

I need to figure out how to get it to display inside a usable window, but it's now in the realm that I can probably work with it.

Now if only I could figure out how to get the VPN client to compile...

---

