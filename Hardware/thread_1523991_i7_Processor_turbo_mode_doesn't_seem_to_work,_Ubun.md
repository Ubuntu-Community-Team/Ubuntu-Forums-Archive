---
title: "i7 Processor turbo mode doesn't seem to work, Ubuntu 10.04"
date: 2010-07-04
forum: Hardware
---

### Post by danbaark on 2010-07-04
I have a Dell Studio XPS 16 with an i7-820 QM processor and Ubuntu 10.04. 

I'm under the impression that unless all 4 cores are being heavily used the i7 processors should automatically use turbo mode to overclock the cores that are being used past the stock speed of 1.73ghz. However, using the CPU frequency monitor integrated into the gnome panel it doesn't ever go above 1.73ghz no matter what settings are used.

Do I need to change something in the bios to activate turbo mode or is this just being misreported by the panel applet?

Thanks very much

---

### Post by dukhia on 2010-07-07
> **danbaark said:**
> I have a Dell Studio XPS 16 with an i7-820 QM processor and Ubuntu 10.04. 

I'm under the impression that unless all 4 cores are being heavily used the i7 processors should automatically use turbo mode to overclock the cores that are being used past the stock speed of 1.73ghz. However, using the CPU frequency monitor integrated into the gnome panel it doesn't ever go above 1.73ghz no matter what settings are used.

Do I need to change something in the bios to activate turbo mode or is this just being misreported by the panel applet?

Thanks very much
You should check this out

[http://code.google.com/p/i7z/](http://code.google.com/p/i7z/)

---

### Post by danbaark on 2010-07-07
Hi thanks for that link I've seen that mentioned in a couple of forums now. I'm having a bit of trouble getting it to run though (fairly new to Ubuntu)

I've downloaded it and extracted the files to the /opt directory and read the readme file but using the make command or trying to run anything just returns a load of errors:

dan@Dan-laptop:/opt/i7z-0.25$ make
If the compilation complains about not finding ncurses.h, install ncurses (libncurses5-dev on ubuntu/debian)
gcc  -g -O0 -fomit-frame-pointer -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -DBUILD_MAIN -Wall -Dx64_BIT -lncurses -lpthread  i7z.c helper_functions.c i7z_Single_Socket.c i7z_Dual_Socket.c -o i7z
i7z.c:21:21: error: ncurses.h: No such file or directory
i7z_Single_Socket.c:21:21: error: ncurses.h: No such file or directory
i7z_Single_Socket.c: In function &#8216;Single_Socket&#8217;:
i7z_Single_Socket.c:51: warning: implicit declaration of function &#8216;initscr&#8217;
i7z_Single_Socket.c:52: warning: implicit declaration of function &#8216;start_color&#8217;
i7z_Single_Socket.c:53: warning: implicit declaration of function &#8216;getmaxyx&#8217;
i7z_Single_Socket.c:53: error: &#8216;stdscr&#8217; undeclared (first use in this function)
i7z_Single_Socket.c:53: error: (Each undeclared identifier is reported only once
i7z_Single_Socket.c:53: error: for each function it appears in.)
i7z_Single_Socket.c:54: warning: implicit declaration of function &#8216;refresh&#8217;
i7z_Single_Socket.c: In function &#8216;print_i7z_socket_single&#8217;:
i7z_Single_Socket.c:70: warning: implicit declaration of function &#8216;mvprintw&#8217;
i7z_Dual_Socket.c:20:21: error: ncurses.h: No such file or directory
i7z_Dual_Socket.c: In function &#8216;Dual_Socket&#8217;:
i7z_Dual_Socket.c:45: warning: implicit declaration of function &#8216;initscr&#8217;
i7z_Dual_Socket.c:46: warning: implicit declaration of function &#8216;start_color&#8217;
i7z_Dual_Socket.c:47: warning: implicit declaration of function &#8216;getmaxyx&#8217;
i7z_Dual_Socket.c:47: error: &#8216;stdscr&#8217; undeclared (first use in this function)
i7z_Dual_Socket.c:47: error: (Each undeclared identifier is reported only once
i7z_Dual_Socket.c:47: error: for each function it appears in.)
i7z_Dual_Socket.c:48: warning: implicit declaration of function &#8216;refresh&#8217;
i7z_Dual_Socket.c: In function &#8216;print_i7z_socket&#8217;:
i7z_Dual_Socket.c:181: warning: implicit declaration of function &#8216;mvprintw&#8217;
make: *** [bin] Error 1

Could you help me get it to work?

Thanks in advance

---

