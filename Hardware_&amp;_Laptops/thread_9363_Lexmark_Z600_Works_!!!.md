---
title: "Lexmark Z600 Works !!!"
date: 2004-12-27
forum: Hardware &amp; Laptops
---

### Post by autek on 2004-12-27
I did a lot of Googling on this one, but I successfully installed the printer. I would write a "how-to" but I'll leave that to the experts. It really wasn't that hard, even for a newbie like myself. You will need the following tarball from Lexmark, cjlz600le, I just put it in my home directory. I used file roller to open it , ignoring the depends error for some lib file.  Next  as sudo you want to use alien -d to convert the 2 rpm's
 into .deb files. Then sudo dpkg -i the 2 .deb files, then you need to reboot.  Go to systems settings>printing and there will be the correct driver for the printer. Just follow along with the prompts and you are set.  I ignored the part about a ppd file as I have no idea what it is, or what it is used for, plus I couldn't find it.  Maybe someone can clue me in on that one. Please do not tell me to do a google for ppd, as it is a form of autism and my 4 year-old grandson is autistic and lives with ppd.  

Ed

---

