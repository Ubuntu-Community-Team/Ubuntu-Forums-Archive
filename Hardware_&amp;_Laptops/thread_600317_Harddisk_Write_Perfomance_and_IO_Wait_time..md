---
title: "Harddisk Write Perfomance and IO Wait time."
date: 2007-11-02
forum: Hardware &amp; Laptops
---

### Post by petterit on 2007-11-02
I have a trouble with my workstation harddisk. It is very slow and when using hd intensive applications it freezes the whole computer for a while. When runnign top IO waittimes are someting between 30-99% when writing to disk. Reading doesn't cause that much lag. **Professional help needed.**

Computer Specs:
[INDENT]AMD 3000+
Gigabyte GA-K8NF-9
120gt Seagate's Sata harddisk. I don't remeber the actual model
Ubuntu 7.10 upgraded from Feisty
[/INDENT]

I measured hd perfomance with bonnie. I think that 9 mb/s is cuite low hd write perfomance? Writing a 1gb file lasts for two minutes with that speed. Reading speed is propably ok. Another thing is also weard bonnie output shows that writing characters one by one is almost fast as writing longer block. Anyone got any ideas why my hd is is so slow? On XP i had no this kind of problems.

For a note: On different computer External IDE drive connected through USB to got 27mb/s write speed. So something is wrong if PATA drive connected with USB is four times faster than SATA drive which is directly connected to motherboard.

Bonnie output:

```

Writing with putc()...done
Writing intelligently...done
Rewriting...done
Reading with getc()...done
Reading intelligently...done
start 'em...done...done...done...
Create files in sequential order...done.
Stat files in sequential order...done.
Delete files in sequential order...done.
Create files in random order...done.
Stat files in random order...done.
Delete files in random order...done.
Version  1.03       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
lightning        4G  9950  29  9995   5  8205   3 30189  70 41684   5 158.0   0
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16  2369  84 +++++ +++ +++++ +++  2550  91 +++++ +++  9646  97
lightning,4G,9950,29,9995,5,8205,3,30189,70,41684,5,158.0,0,16,2369,84,+++++,+++,+++++,+++,2550,91,+++++,+++,9646,97

```

---

### Post by petterit on 2007-11-14
Doesn't anyone have a clue?

It must be harddiskcontroller or something that causes this lag. 

I am using vmware player that might also cause the problems?

Anyone else having similar problems?

---

