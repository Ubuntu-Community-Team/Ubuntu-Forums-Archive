---
title: "Dell Vostro 1400"
date: 2007-09-25
forum: Hardware &amp; Laptops
---

### Post by The Big M on 2007-09-25
Hey, everyone. I have been using Ubuntu for over a year but I recently got a brand new Dell Vostro 1400 with Vista preinstalled. I am trying to dual boot Vista and Ubuntu but the Live CD refuses to even boot up and instead gives me this message: "cant access tty, job control turned off.":confused:
Here is my Hardware configuration:
Processor: Intel Core 2 Duo
Memory: 2gb DDR2
Graphics: Mobile Intel (R) 965 express chipset family
Sound: Sigmatel

---

### Post by w4ett on 2007-09-25
Here is a selection of fixes for that error message:

[http://ubuntuforums.org/showpost.php?p=3408055&postcount=4](http://ubuntuforums.org/showpost.php?p=3408055&postcount=4)

---

### Post by The Big M on 2007-09-25
I tried the modprobe command but it booted up into command line mode which left me in the dark since I havent used command lines since the days of MS Dos. Is it supposed to do that? One of the posts in the other threads suggested leaving a USB drive plugged in but that didnt work at all.

---

### Post by yther on 2007-09-25
I just got a Dell Inspiron 1520, and I had the same problem; no LiveCD would boot for me because of that error.  I wound up installing Gutsy with an "alternate installer" CD, which I think is available for Feisty as well.  It's a text based installer with menus, so it can get around problems like incompatible graphics hardware... or *whatever* causes that "job control" message.  :-P

One hint for you, if you decide to go the way of text menus:  Don't take the default method (I think it's called "easy" or something) and opt for "medium" instead.  I had wanted to try some things like encrypted partitions that more advanced installer modes were supposed to handle, but I missed out because the installer was in that very simple mode and didn't ask me many questions.

Good luck!  :)

---

