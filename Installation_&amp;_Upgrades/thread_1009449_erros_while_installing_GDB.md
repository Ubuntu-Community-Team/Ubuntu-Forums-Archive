---
title: "erros while installing GDB"
date: 2008-12-12
forum: Installation &amp; Upgrades
---

### Post by joker@ on 2008-12-12
HI
I trying install GDB on my U 8.10 
this is what i get after send command 'make" its polish language but is simple what is where,any sugiestion??
regards

make[2]: Nie ma nic do zrobienia w `all'.
make[2]: Opuszczenie katalogu `/home/rav/Pulpit/gdb-6.8/libdecnumber'
make[2]: Wej&#347;cie do katalogu `/home/rav/Pulpit/gdb-6.8/readline'
make[2]: Nie ma nic do zrobienia w `all'.
make[2]: Opuszczenie katalogu `/home/rav/Pulpit/gdb-6.8/readline'
make[2]: Wej&#347;cie do katalogu `/home/rav/Pulpit/gdb-6.8/sim'
make[2]: Opuszczenie katalogu `/home/rav/Pulpit/gdb-6.8/sim'
make[2]: Wej&#347;cie do katalogu `/home/rav/Pulpit/gdb-6.8/gdb'
gcc -c -g -O2   -I. -I.././gdb -I.././gdb/config -DLOCALEDIR="\"/usr/local/share/locale\"" -DHAVE_CONFIG_H -I.././gdb/../include/opcode -I.././gdb/../readline/.. -I../bfd -I.././gdb/../bfd -I.././gdb/../include -I../libdecnumber -I.././gdb/../libdecnumber   -DMI_OUT=1 -DTUI=1  -Wall -Wdeclaration-after-statement -Wpointer-arith -Wformat-nonliteral -Wno-pointer-sign -Wno-unused -Wno-switch -Wno-char-subscripts -Werror linux-nat.c
cc1: warnings being treated as errors
linux-nat.c: In function &#8216;linux_nat_info_proc_cmd&#8217;:
linux-nat.c:2879: error: ignoring return value of &#8216;fgets&#8217;, declared with attribute warn_unused_result
make[2]: *** [linux-nat.o] error 1
make[2]: Opuszczenie katalogu `/home/rav/Pulpit/gdb-6.8/gdb'
make[1]: *** [all-gdb] error 2
make[1]: Opuszczenie katalogu `/home/rav/Pulpit/gdb-6.8'
make: *** [all] error 2
rav@rav-laptop:~/Pulpit/gdb-6.8$

---

### Post by cariboo on 2008-12-12
GDB is in the repositories, there is no need to compile it yourself. Go to System-->Administration--Synaptic Package Manager and search for gdb.

Jim

---

### Post by Jeff-in-OR on 2009-02-25
Yeah-but...  

I have a development environment (different version of gcc/tool chain) for an embedded product that fails to build gdb 6.8 when that environemnt is installed on 8.10 (works on 8.04).  It fails in the exact same way as when attempting to build gdb 6.8 from source on a fresh 8.10 build using the Ubuntu-supplied toolchain.  after ./configure I can successfully execute the make targets inidividually until:

make all-host

then the error occurs. 

Is there a way to see how the package was built for Ubuntu?

---

### Post by Jeff-in-OR on 2009-02-25
that assumes I skip make all...

---

### Post by skierpage on 2009-09-21
I had this and several similar compiler errors trying to compile gdb 6.8 under Kubuntu 9.04 64-bit.  I filed bugs [10674]("http://sourceware.org/bugzilla/show_bug.cgi?id=10674") and [10675]("http://sourceware.org/bugzilla/show_bug.cgi?id=10675") against gdb at sourceware.org. You can get past them by declaring a junk variable of the right type, e.g. char *junk; at the top of the program block, then assigning junk = [the problem function call].[URL="http://sourceware.org/bugzilla/show_bug.cgi?id=10675"]
[/URL]
I compiled gdb myself hoping to avoid gdb crashes in iterate_over_threads , possibly because Ubuntu should have repackaged gdb for kernel and/or libc updates since 9.04, which might be [Launchpad bug 258578]("https://bugs.launchpad.net/ubuntu/+source/gdb/+bug/258578").  But it didn't help.

---

### Post by PLayer_unu on 2010-07-04
> **skierpage said:**
> I had this and several similar compiler errors trying to compile gdb 6.8 under Kubuntu 9.04 64-bit.  I filed bugs [10674]("http://sourceware.org/bugzilla/show_bug.cgi?id=10674") and [10675]("http://sourceware.org/bugzilla/show_bug.cgi?id=10675") against gdb at sourceware.org. You can get past them by declaring a junk variable of the right type, e.g. char *junk; at the top of the program block, then assigning junk = [the problem function call].[URL="http://sourceware.org/bugzilla/show_bug.cgi?id=10675"]
[/URL]
I compiled gdb myself hoping to avoid gdb crashes in iterate_over_threads , possibly because Ubuntu should have repackaged gdb for kernel and/or libc updates since 9.04, which might be [Launchpad bug 258578]("https://bugs.launchpad.net/ubuntu/+source/gdb/+bug/258578").  But it didn't help.

It's a good solution to declare a junk variabile. I've tried this and worked, but then I've got another 5-6 similar errors and I've found another FAST solution.
Edit the Makefile and delete this line:
     
            WERROR_CFLAGS = -Werror

That's because you will be prompted for an error everytime the compiler will get a warning.

---

### Post by asifhu on 2012-08-02
Do this:

./configure --disable-werror

you might want to specify --prefix and --exec-prefix.

And then:

make

---

