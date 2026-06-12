---
title: "Suspend and Hibernate on my Dell XPS M1530"
date: 2008-03-26
forum: Hardware &amp; Laptops
---

### Post by JaggedOne on 2008-03-26
Suspend and Hibernate have never worked right for me. Sometimes when I close the lid the laptop does not suspend to memory and more irritatingly, when I reopen the laptop it locks up half the time.

I googled around a bit and found this guide: 
[http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855)

It suggests I install uswsusp and run a command s2ram. 

When I was installing uswsusp I got an error message saying something about how the it could not find swap. I was confused and told it to continue. Then when I ran the s2ram command it said command not found.

I removed and reinstalled uswsusp. This time I got no error message about the swap not being detected (perhaps it found the swap, or perhaps it just found some config file left over and didn't bother looking for the swap again.) After the reinstall s2ram still got me command not found.

I don't care how I get this suspend working. If you can help me get uswsusp working that would be great. If you have other methods of achieving the same ends those are welcome too.

edit: I also installed pm-utils and powersaved in my quest to fix this problem. Installing those removed apmd and powernowd. Im not sure if that is significant or not.

---

### Post by JaggedOne on 2008-03-27
bump

---

