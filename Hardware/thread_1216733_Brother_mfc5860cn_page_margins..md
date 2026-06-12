---
title: "Brother mfc5860cn page margins."
date: 2009-07-18
forum: Hardware
---

### Post by ajgreeny on 2009-07-18
I am using ubuntu 9.04 and have just bought a Brother MFC5860CN, having made sure first that it was supported by linux and Ubuntu. 
 
Great machine and I thought everything was working OK until I tried to print pages and then found no top margin on the page in spite of having everything set correctly in OO or other application, and also in cups configuration, and everywhere else I could think of. 
 
After a lot of searching (most of yesterday evening) I eventually found that I needed to edit a file named /usr/Brother/Printer/mfc5860cn/inf/brmfc5860cnrc which still listed the paper as Letter, presumably the USA default. This particular file has moved from the location that the solution article told me of, but a search of the file system found it quickly, and now, thank goodness all is well.

I thought it worth offering this information, as a search on this forum did not find anything, so others may now find this useful.

---

### Post by ghed on 2010-02-04
I have the same problem wit my printer Brother DCP-7045N, the top right of the page is not printed. As the printable area is moved from the centre. The printer istalled in i local network. I can't find the files "/usr/Brother/Printer/mfc5860cn/inf/brmfc5860cnrc" not even the directory.

---

