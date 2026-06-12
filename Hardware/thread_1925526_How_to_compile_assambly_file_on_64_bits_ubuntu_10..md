---
title: "How to compile assambly file on 64 bits ubuntu 10.10"
date: 2012-02-14
forum: Hardware
---

### Post by alcapone-g on 2012-02-14
Can anybody tell me how to compile assembly to executable file on ubuntu 10.10
64 bits operating system?
1string.asm text file with assembly code
now I create 1string.o using
angela@angela-Aspire-7551:~/asme$ nasm -f elf 1string.asm
I get this
angela@angela-Aspire-7551:~/asme$ l
1string.asm  1string.o
now I want to make executable 1string file doing it 
angela@angela-Aspire-7551:~/asme$ gcc 1string.o -o 1string
I get error message:
/usr/bin/ld: i386 architecture of input file `1string.o' is incompatible with i386:x86-64 output
collect2: ld returned 1 exit status
angela@angela-Aspire-7551:~/asme$ 
Please step by step code how to do it?
Thank you.

---

### Post by alcapone-g on 2012-04-04
How to Compile 32-bit Assembly Programs on a 64-bit PC in Linux
$ nasm -f elf filename.asm       //no included calls for external c functions
$ ld -m elf_i386 -o filename filename.o
$ ./filename                    //to execute

OR
sudo apt-get install gcc-multilib   //has to be installed
$ nasm -f elf string.asm           //can be included calls for externall c functions
$ gcc -m32 string.o -o string
$ ./string                               // to execute

---

