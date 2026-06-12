---
title: "Having trouble with Conky text files"
date: 2008-09-19
forum: General Help
---

### Post by RobertWaelder on 2008-09-19
I'm trying to use conky to display a to do list on my desktop. Should be pretty simple, but I'm having trouble configuring the conkyrc config file correctly. I get nothing on the desktop, sometimes I can even tell that it started (because I see the desktop flicker) but nothing shows up. Here is how it looks:

```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# Maximum size of buffer for user text, i.e. below TEXT line.
max_user_text 16384

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color orange}TO DO ${hr 2}$color
${execi 2 less /home/robert/Documents/todo/todo.txt}

```

I have fiddled around with it quite a bit. At first I used cat instead of less for the last line. But replacing it with less worked, until I rebooted. I am running Hardy Heron, GNOME, and Compiz on a HP dv9000, with conky version 1.6.1.

Thanks in advance!

---

### Post by easybake on 2008-09-19
> **RobertWaelder said:**
> I'm trying to use conky to display a to do list on my desktop. Should be pretty simple, but I'm having trouble configuring the conkyrc config file correctly. I get nothing on the desktop, sometimes I can even tell that it started (because I see the desktop flicker) but nothing shows up. Here is how it looks:

I have fiddled around with it quite a bit. At first I used cat instead of less for the last line. But replacing it with less worked, until I rebooted. I am running Hardy Heron, GNOME, and Compiz on a HP dv9000.

Thanks in advance!

I ran your code but change the path to a text file I had. It worker fine. If you start conky through terminal do you get any errors?

---

### Post by RobertWaelder on 2008-09-20
This is what I get when I run conky in the terminal:

```

robert@robert-laptop:~$ conky
Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: can't load font 'arial'
Conky: desktop window (10000ba) is subwindow of root window (1a6)
Conky: window type - override
Conky: drawing to created window (0x3c00003)
Conky: drawing to double buffer
/home/robert/Documents/todo/todo.txt: No such file or directory
/home/robert/Documents/todo/todo.txt: No such file or directory
/home/robert/Documents/todo/todo.txt: No such file or directory
/home/robert/Documents/todo/todo.txt: No such file or directory
/home/robert/Documents/todo/todo.txt: No such file or directory

```

When I read that I remembered I had changed the location of the directory where todo.txt is located. So I edited the .conkyrc file and ran it again. This time, it gave me this  long winded error:

```
robert@robert-laptop:~$ conky
Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: can't load font 'arial'
Conky: desktop window (10000ba) is subwindow of root window (1a6)
Conky: window type - override
Conky: drawing to created window (0x3c00003)
Conky: drawing to double buffer
*** glibc detected *** conky: malloc(): memory corruption (fast): 0x000000000065b560 ***
======= Backtrace: =========
/lib/libc.so.6[0x7ffd147683b2]
/lib/libc.so.6(__libc_malloc+0x90)[0x7ffd14769360]
/usr/lib/libX11.so.6(_XReply+0xa0)[0x7ffd157b9ee0]
/usr/lib/libX11.so.6(XQueryTree+0x93)[0x7ffd157a8fa3]
conky[0x434d5a]
conky[0x41e997]
conky[0x42345e]
/lib/libc.so.6(__libc_start_main+0xf4)[0x7ffd147111c4]
conky[0x4053b9]
======= Memory map: ========
00400000-00441000 r-xp 00000000 08:07 230697                             /usr/bin/conky
00640000-00641000 rw-p 00040000 08:07 230697                             /usr/bin/conky
00641000-00670000 rw-p 00641000 00:00 0                                  [heap]
7ffd0c000000-7ffd0c021000 rw-p 7ffd0c000000 00:00 0 
7ffd0c021000-7ffd10000000 ---p 7ffd0c021000 00:00 0 
7ffd12dbb000-7ffd12dc8000 r-xp 00000000 08:01 122463                     /lib/libgcc_s.so.1
7ffd12dc8000-7ffd12fc8000 ---p 0000d000 08:01 122463                     /lib/libgcc_s.so.1
7ffd12fc8000-7ffd12fc9000 rw-p 0000d000 08:01 122463                     /lib/libgcc_s.so.1
7ffd12fc9000-7ffd12fce000 r-xp 00000000 08:07 481664                     /usr/lib/libXdmcp.so.6.0.0
7ffd12fce000-7ffd131cd000 ---p 00005000 08:07 481664                     /usr/lib/libXdmcp.so.6.0.0
7ffd131cd000-7ffd131ce000 rw-p 00004000 08:07 481664                     /usr/lib/libXdmcp.so.6.0.0
7ffd131ce000-7ffd131e7000 r-xp 00000000 08:01 122524                     /lib/libselinux.so.1
7ffd131e7000-7ffd133e7000 ---p 00019000 08:01 122524                     /lib/libselinux.so.1
7ffd133e7000-7ffd133e9000 rw-p 00019000 08:01 122524                     /lib/libselinux.so.1
7ffd133e9000-7ffd133ea000 rw-p 7ffd133e9000 00:00 0 
7ffd133ea000-7ffd1340f000 r-xp 00000000 08:07 482213                     /usr/lib/libpcre.so.3.12.1
7ffd1340f000-7ffd1360f000 ---p 00025000 08:07 482213                     /usr/lib/libpcre.so.3.12.1
7ffd1360f000-7ffd13610000 rw-p 00025000 08:07 482213                     /usr/lib/libpcre.so.3.12.1
7ffd13610000-7ffd13632000 r-xp 00000000 08:07 481890                     /usr/lib/libexpat.so.1.5.2
7ffd13632000-7ffd13832000 ---p 00022000 08:07 481890                     /usr/lib/libexpat.so.1.5.2
7ffd13832000-7ffd13834000 rw-p 00022000 08:07 481890                     /usr/lib/libexpat.so.1.5.2
7ffd13834000-7ffd1383d000 r-xp 00000000 08:07 481690                     /usr/lib/libXrender.so.1.3.0
7ffd1383d000-7ffd13a3c000 ---p 00009000 08:07 481690                     /usr/lib/libXrender.so.1.3.0
7ffd13a3c000-7ffd13a3d000 rw-p 00008000 08:07 481690                     /usr/lib/libXrender.so.1.3.0
7ffd13a3d000-7ffd13a53000 r-xp 00000000 08:07 482504                     /usr/lib/libz.so.1.2.3.3
7ffd13a53000-7ffd13c53000 ---p 00016000 08:07 482504                     /usr/lib/libz.so.1.2.3.3
7ffd13c53000-7ffd13c54000 rw-p 00016000 08:07 482504                     /usr/lib/libz.so.1.2.3.3
7ffd13c54000-7ffd13ccd000 r-xp 00000000 08:07 481569                     /usr/lib/libfreetype.so.6.3.16
7ffd13ccd000-7ffd13ecc000 ---p 00079000 08:07 481569                     /usr/lib/libfreetype.so.6.3.16
7ffd13ecc000-7ffd13ed1000 rw-p 00078000 08:07 481569                     /usr/lib/libfreetype.so.6.3.16
7ffd13ed1000-7ffd13ed3000 r-xp 00000000 08:07 481653                     /usr/lib/libXau.so.6.0.0
7ffd13ed3000-7ffd140d2000 ---p 00002000 08:07 481653                     /usr/lib/libXau.so.6.0.0
7ffd140d2000-7ffd140d3000 rw-p 00001000 08:07 481653                     /usr/lib/libXau.so.6.0.0
7ffd140d3000-7ffd140d5000 r-xp 00000000 08:01 122455                     /lib/libdl-2.7.so
7ffd140d5000-7ffd142d5000 ---p 00002000 08:01 122455                     /lib/libdl-2.7.so
7ffd142d5000-7ffd142d7000 rw-p 00002000 08:01 122455                     /lib/libdl-2.7.so
7ffd142d7000-7ffd142f2000 r-xp 00000000 08:07 482492                     /usr/lib/libxcb.so.1.0.0
7ffd142f2000-7ffd144f1000 ---p 0001b000 08:07 482492                     /usr/lib/libxcb.so.1.0.0
7ffd144f1000-7ffd144f2000 rw-p 0001a000 08:07 482492                     /usr/lib/libxcb.so.1.0.0
7ffd144f2000-7ffd144f3000 r-xp 00000000 08:07 482490                     /usr/lib/libxcb-xlib.so.0.0.0
7ffd144f3000-7ffd146f2000 ---p 00001000 08:07 482490                     /usr/lib/libxcb-xlib.so.0.0.0
7ffd146f2000-7ffd146f3000 rw-p 00000000 08:07 482490                     /usr/lib/libxcb-xlib.so.0.0.0
7ffd146f3000-7ffd1484b000 r-xp 00000000 08:01 122438                     /lib/libc-2.7.so
7ffd1484b000-7ffd14a4b000 ---p 00158000 08:01 122438                     /lib/libc-2.7.so
7ffd14a4b000-7ffd14a4e000 r--p 00158000 08:01 122438                     /lib/libc-2.7.so
7ffd14a4e000-7ffd14a50000 rw-p 0015b000 08:01 122438                     /lib/libc-2.7.so
7ffd14a50000-7ffd14a55000 rw-p 7ffd14a50000 00:00 0 
7ffd14a55000-7ffd14b14000 r-xp 00000000 08:07 485296                     /usr/lib/libglib-2.0.so.0.1600.4
7ffd14b14000-7ffd14d13000 ---p 000bf000 08:07 485296                     /usr/lib/libglib-2.0.so.0.1600.4
7ffd14d13000-7ffd14d15000 rw-p 000be000 08:07 485296                     /usr/lib/libglib-2.0.so.0.1600.4
7ffd14d15000-7ffd14d44000 r-xp 00000000 08:07 481898                     /usr/lib/libfontconfig.so.1.3.0
7ffd14d44000-7ffd14f44000 ---p 0002f000 08:07 481898                     /usr/lib/libfontconfig.so.1.3.0
7ffd14f44000-7ffd14f46000 rw-p 0002f000 08:07 481898                     /usr/lib/libfontconfig.so.1.3.0
7ffd14f46000-7ffd14f59000 r-xp 00000000 08:07 481674                     /usr/lib/libXft.so.2.1.2
7ffd14f59000-7ffd15159000 ---p 00013000 08:07 481674                     /usr/lib/libXft.so.2.1.2
7ffd15159000-7ffd1515a000 rw-p 00013000 08:07 481674                     /usr/lib/libXft.so.2.1.2
7ffd1515a000-7ffd1515f000 r-xp 00000000 08:07 481670                     /usr/lib/libXfixes.so.3.1.0
7ffd1515f000-7ffd1535e000 ---p 00005000 08:07 481670                     /usr/lib/libXfixes.so.3.1.0
7ffd1535e000-7ffd1535f000 rw-p 00004000 08:07 481670                     /usr/lib/libXfixes.so.3.1.0
7ffd1535f000-7ffd15361000 r-xp 00000000 08:07 481662                     /usr/lib/libXdamage.so.1.1.0
7ffd15361000-7ffd15560000 ---p 00002000 08:07 481662                     /usr/lib/libXdamage.so.1.1.0
7ffd15560000-7ffd15561000 rw-p 00001000 08:07 481662                     /usr/lib/libXdamage.so.1.1.0
7ffd15561000-7ffd15572000 r-xp 00000000 08:07 481668                     /usr/lib/libXext.so.6.4.0
7ffd15572000-7ffd15771000 ---p 00011000 08:07 481668                     /usr/lib/libXext.so.6.4.0
7ffd15771000-7ffd15772000 rw-p 00010000 08:07 481668                     /usr/lib/libXext.so.6.4.0
7ffd15772000-7ffd15871000 r-xp 00000000 08:07 481647                     /usr/lib/libX11.so.6.2.0
7ffd15871000-7ffd15a70000 ---p 000ff000 08:07 481647                     /usr/lib/libX11.so.6.2.0
7ffd15a70000-7ffd15a75000 rw-p 000fe000 08:07 481647                     /usr/lib/libX11.so.6.2.0
7ffd15a75000-7ffd15af5000 r-xp 00000000 08:01 122475                     /lib/libm-2.7.so
7ffd15af5000-7ffd15cf4000 ---p 00080000 08:01 122475                     /lib/libm-2.7.so
7ffd15cf4000-7ffd15cf6000 rw-p 0007f000 08:01 122475                     /lib/libm-2.7.so
7ffd15cf6000-7ffd15cfe000 r-xp 00000000 08:01 122522                     /lib/librt-2.7.so
7ffd15cfe000-7ffd15efd000 ---p 00008000 08:01 122522                     /lib/librt-2.7.so
7ffd15efd000-7ffd15eff000 rw-p 00007000 08:01 122522                     /lib/librt-2.7.so
7ffd15eff000-7ffd15f15000 r-xp 00000000 08:01 122516                     /lib/libpthread-2.7.so
7ffd15f15000-7ffd16115000 ---p 00016000 08:01 122516                     /lib/libpthread-2.7.so
7ffd16115000-7ffd16117000 rw-p 00016000 08:01 122516                     /lib/libpthread-2.7.so
7ffd16117000-7ffd1611b000 rw-p 7ffd16117000 00:00 0 
7ffd1611b000-7ffd16138000 r-xp 00000000 08:01 122418                     /lib/ld-2.7.so
7ffd162db000-7ffd1631a000 r--p 00000000 08:07 507147                     /usr/lib/locale/en_US.utf8/LC_CTYPE
7ffd1631a000-7ffd16324000 rw-p 7ffd1631a000 00:00 0 
7ffd1632e000-7ffd16335000 r--s 00000000 08:07 483863                     /usr/lib/gconv/gconv-modules.cache
7ffd16335000-7ffd16338000 rw-p 7ffd16335000 00:00 0 
7ffd16338000-7ffd1633a000 rw-p 0001d000 08:01 122418                     /lib/ld-2.7.so
7fff1e324000-7fff1e339000 rw-p 7ffffffea000 00:00 0                      [stack]
7fff1e3fe000-7fff1e400000 r-xp 7fff1e3fe000 00:00 0                      [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
Aborted

```

Buh?? Something is wrong with glibc, apparently, but what? Also, I compiled conky from source (because conky from the repositories wasn't working either), so it is possible I may have set something up incorrectly.

---

### Post by easybake on 2008-09-20
> **RobertWaelder said:**
> 
Buh?? Something is wrong with glibc, apparently, but what? Also, I compiled conky from source (because conky from the repositories wasn't working either), so it is possible I may have set something up incorrectly.

Definitely is a problem with Conky itself. You can try and reinstall it. I've been running 1.5.1 without any problems.

---

### Post by RobertWaelder on 2008-09-20
OK, I just changed an option in the conkyrc file:

own_window_type override

When I changed that to "normal" instead, it worked fine! woot. Thanks so much for your help, easybake.

Now my only problem is figuring out why my PATH variable in .bashrc for todo.sh isn't working.... but that's a post for another day, hehe.

---

### Post by Bruce M. on 2008-10-27
> **RobertWaelder said:**
> 
```

${color orange}TO DO ${hr 2}$color
${execi 2 less /home/robert/Documents/todo/todo.txt}

```


Well, this worked for me ... a huge thank you!

Have a GREAT Day!
Bruce

---

### Post by RobertWaelder on 2008-10-27
Awesome! I'm glad someone could use the information I posted!

---

