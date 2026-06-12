---
title: "acpid service won't start, yet some Fn combination could use"
date: 2006-10-18
forum: Hardware &amp; Laptops
---

### Post by atery on 2006-10-18
Hi everyone, before asking this question, I searched two day for answers, but all I got is something like this is a bug of xorg, but I upgraded all I could by "sudo apt-get dist-upgrade", I still got the error message when boot up, saying "acpid: can't open /proc/acpi/event Device or source busy".

I disabled the notebook boot-up service that came along with Ubuntu 6.06, yet I can get my T43's Fn+Home, End, Up, F7 (brightness, light, switch screen) working without any setting. Also the volume up and down, mute buttons work. But nothing happens when my lid is closed, not event black my screen...

There is nothing in my /var/log/acpid, except only the lasted message from months ago... and nothing said about caught any IBM hotkey event. 

I wonder: (1) why I could use some of my Fn functions without acipd; (2) how could I use other Fn functions, such as Fn+F3 to shut screen. (3) relevant to (2), how to let my acpid function?

PS: Ubuntu 6.06, IBM Thinkpad T43

Thanks

---

### Post by AgenT on 2006-11-18
[ThinkWiki]("http://www.thinkwiki.org/wiki/ThinkWiki")
[Ubuntu on IBM ThinkPad T42]("http://www.columbia.edu/%7Eem36/ubuntuhoarythinkpadt42.html")
[Thinkpads Forum]("http://forum.thinkpads.com/")

---

### Post by lingnoi on 2007-01-13
I'm having the same problems apart from acpid is started but when I press the hotkey combos (fn+up, fn+down, fn+f2, etc) nothing shows up in the log.

At the same time I can turn off and on my screen and volume up and down hotkeys work.

I'm on a samsung r55.

---

