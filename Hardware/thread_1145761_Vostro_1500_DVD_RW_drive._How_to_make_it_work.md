---
title: "Vostro 1500 DVD RW drive. How to make it work?"
date: 2009-05-01
forum: Hardware
---

### Post by DeusExM1 on 2009-05-01
Hello, everyone

I just installed Ubuntu on my Vostro 1500 and managed to get nearly everything working. I was very impressed with out of the box functionality.

The only  thing that i cannot make work is the DVD drive. I have looked on the web and did not find anything useful. But that might be because i am very new to Ubuntu (4 hours so far). 

The laptop drive is [SIZE=3]TSST TS-L632H slim 8x DVD+/-RW . [SIZE=1]Dell has Xp and vista drivers but like usual nothing else. 

Any ideas? =]
[/SIZE][/SIZE]

---

### Post by DeusExM1 on 2009-05-02
I think i fixed my own problem. I kept looking on google and apparently you can mount a cd somehow with the terminal. I will say what i did to fix it so other people will know if they come across a similar issue. So all i had to do was:

1. type in the terminal "sudo lshw" . This gave a lot of information, and i looked under te -cd rom line. It basically told me all the information about my drive. (including what linux was calling it). 

2. I then typed in 'sudo mount /dev/cdrom" and then tried "sudo mount /dev/cdrw" . One of those fixed the issue.

Edit: Upon restart the issue persists. For some reason i have to keep mounting the image every time the computer is started. does anyone know how to bypass this?

---

### Post by DeusExM1 on 2009-05-02
bump. Does anyone know how to fix the issue permanately? Is there any way to mount the drive so it stays mounted?

---

