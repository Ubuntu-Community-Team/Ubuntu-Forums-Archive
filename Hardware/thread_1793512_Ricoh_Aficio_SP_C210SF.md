---
title: "Ricoh Aficio SP C210SF"
date: 2011-06-29
forum: Hardware
---

### Post by guerrier on 2011-06-29
Hello

I document here how to use this unsupported printer/scanner

The printer can be installed as a brother MFC-9420CN

For the scanner : 

install brscan2 from [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html)

```

sudo echo '0x01ad ,16,1,"MFC-9420CN"' | sudo tee -a  /usr/local/Brother/sane/models2/ext2.ini

```
This trick is perhaps not optimal.... especially the unknown parameters

the scanner should then work with "sudo xsane" at least

for normal users : [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html)

---

### Post by NeoDarin on 2012-04-27
Would this trick work for a Ricoh Aficio C3500?  I'm afraid to try your code if it might mess up my computer, or will this not affect anything if it doesnt work?

PS - I'm on an acer aspire 5755-6699 with ubuntu 11.10

Related Post [http://ubuntuforums.org/showthread.php?p=11853985#post11853985](http://ubuntuforums.org/showthread.php?p=11853985#post11853985)

I'm new to this forum thing, so if i need to post this somewhere else lemme know.

---

