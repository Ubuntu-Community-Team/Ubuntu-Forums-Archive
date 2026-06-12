---
title: "kvm core dump (exception 12)"
date: 2007-04-30
forum: Hardware &amp; Laptops
---

### Post by aztechclan on 2007-04-30
I'm running a fully updated Feisty, with a Dell D620.  I've got virtualization turned on and the kvm-intel module loaded + perms set.  However, when I attempt to run 'kvm -no-acpi -m 384 -cdrom /home/jeremy/cdimage.iso -boot d windows.img' the core dumps (see error below).  I saw a few people in the Feisty development forum with the same issue but didn't see a solution.  Also didn't see a bug, but since the dev forum was closed I'm posting here before filing a bug report.  Anyone know how to fix this?  

exception 12 (0)
rax 0000000000002595 rbx 0000000000040080 rcx 0000000000002000 rdx 0000000000012c00
rsi 00000000ffff0800 rdi 0000000000040000 rsp 0000000000087bdc rbp 0000000000000000
r8  0000000000000000 r9  0000000000000000 r10 0000000000000000 r11 0000000000000000
r12 0000000000000000 r13 0000000000000000 r14 0000000000000000 r15 0000000000000000
rip 000000000000a4bc rflags 00033206
cs 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
ds 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
es 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
ss 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
fs 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
gs 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
tr 0000 (20850000/00002088 p 1 dpl 0 db 0 s 0 type b l 0 g 0 avl 0)
ldt 0000 (00000000/0000ffff p 1 dpl 0 db 0 s 0 type 2 l 0 g 0 avl 0)
gdt fa4d1/37
idt 0/3ff
cr0 60000010 cr2 0 cr3 0 cr4 0 cr8 0 efer 0
Aborted (core dumped)

With a slight variation on my command line, I get exception 13 instead.. (booting direct from cdrom instead of an iso image.)
kvm -no-acpi -m 512 -cdrom /dev/cdrom -boot d windows.img

Dump:
exception 13 (0)
rax 000000000000f001 rbx 000000000000d6a2 rcx 0000000080000000 rdx 0000000000000000
rsi 00000000ffff000c rdi 000000000004f7f4 rsp 000000000008ffb8 rbp 000000000000ffcc
r8  0000000000000000 r9  0000000000000000 r10 0000000000000000 r11 0000000000000000
r12 0000000000000000 r13 0000000000000000 r14 0000000000000000 r15 0000000000000000
rip 0000000000000a45 rflags 00033002
cs f000 (000f0000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
ds 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
es 0ffd (0000ffd0/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
ss 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
fs 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
gs 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
tr 0000 (20850000/00002088 p 1 dpl 0 db 0 s 0 type b l 0 g 0 avl 0)
ldt 0000 (00000000/0000ffff p 1 dpl 0 db 0 s 0 type 2 l 0 g 0 avl 0)
gdt fa4d1/37
idt 0/3ff
cr0 60000010 cr2 0 cr3 0 cr4 0 cr8 0 efer 0
Aborted (core dumped)

---

### Post by sjpwong on 2007-05-01
I get a core dump if my Windows virtual guest OS reboots.

It starts and runs fine (so far!).

---

### Post by aztechclan on 2007-06-06
Sweet, after the last upgrade to the Feisty kernel I tried KVM again and guess what, it WORKS!

Also, if anyone else has this problem.. make sure you have a bootable cd in your drive, otherwise you will get a core dump.  This may have been the problem from the begining ..  :o;)

---

