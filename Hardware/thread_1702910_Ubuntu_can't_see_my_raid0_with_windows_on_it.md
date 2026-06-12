---
title: "Ubuntu can't see my raid0 with windows on it"
date: 2011-03-08
forum: Hardware
---

### Post by NoMercyZL on 2011-03-08
Hi, I have two sata drives in raid 0 with windows 7 installed on them and I just installed Ubuntu on an IDE drive and I want to see my windows drive from ubuntu but everything that ubuntu sees is two seperate drives even thogh I have them in raid so I can't acces them. This is my first time using Ubuntu so I am still not good at it so please explaine it with that in mind.

---

### Post by fjgaude on 2011-03-08
Welcome to the world of the non-mainstream.

There is a program in Ubuntu that permits mounting, reading and writing to NTFS FaikRAID arrays produced by the BIOS intended for Windows use.

Download **dmraid** and then read the **man dmraid** pages. This starts you on a journey to discover just what Linux is all about. In a terminal, do this:

```
sudo apt-get install dmraid
```

Answer with your password and after the download is complete you can read the man pages in that same terminal:

```
man dmraid
```

If you have questions, ask us for answers. We might have them. <smile>

---

### Post by NoMercyZL on 2011-03-10
Thanx very much. it worked with the program you told me about:)

---

