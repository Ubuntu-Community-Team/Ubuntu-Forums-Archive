---
title: "Is my Laptop Overheating?"
date: 2007-05-25
forum: Hardware &amp; Laptops
---

### Post by malachi on 2007-05-25
I can't use Feisty for fifteen minutes without it slowing down to a crawl. If I run any CPU-intensive programs like QDVDAuthor or Tremulous, it crawls in about 5 minutes. I'm assuming it's a overheating issue, but I don't know how to make sure, and I don't know how to remedy it. Any and all help will be appreciated.

---

### Post by Denn1s on 2007-06-02
try:
```
watch acpi -V
```

to see the temperature of your sistem, this may give u a clue if it is overheating

---

### Post by FuriousLettuce on 2007-06-02
Have you identified the processes which cause it to slow to a crawl? Try leaving system monitor open on the processes tab, with the entries sorted by CPU usage. I've just posted an issue, which has yet to be remedied, although I can find similar problems as far back as 2002. The processes causing a slowdown on my laptop are kacpid and kacpi_notify.They kick in using ~100% CPU between them whenever I run any CPU-intensive task. My original post is at [http://ubuntuforums.org/showthread.php?t=462057](http://ubuntuforums.org/showthread.php?t=462057). Please let me know if you are having a similar issue.

---

### Post by hessiess on 2007-06-02
open a termanal and type "top" this will tell you what is using the most resorses

do you have acsess to a air compressor? if yes then blow out all of the vents, your heat excangers may be cloged with dust. if you dont, then its inposable without dismantaling the comp

---

### Post by malachi on 2007-06-02
Hey guys, I've followed all of the suggestions, and it looks like Xorg is using the most resources....hm.

My ATI card, I presume.

Thanks for the help, though.

---

### Post by kzm. on 2007-06-02
hey.

i read recently about this. its not xorg. its something that keeps xorg busy.. at that post they were running xorg without anything else and xorg went idle as it should. i dont have the link to that post anymore, but one of its resource links:
[http://www.linuxpowertop.org/](http://www.linuxpowertop.org/)

may be this would help you to get some clue.

---

