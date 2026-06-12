---
title: "Hard-disk not recognized after install!"
date: 2011-07-20
forum: Hardware
---

### Post by imtheshade on 2011-07-20
Hi! 
I installed ubuntu on my laptop (Acer Aspire 7736ZG) from windows 7 using wubi and it detects only one (c: - the partition on which Windows is installed) of my two partitions (d: being the latter). Any clues on what can I do so that I can see d: (the partition on which ubuntu was installed)?

Thanks in advance!

---

### Post by jerrrys on 2011-07-21
wubi is a way of installing ubuntu inside windows.  therefor it needs to be installed in "C drive".  your "D" partition is not an option with this type of install.  more here:

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=wubi&sa=Search&cof=FORID:9#911](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=wubi&sa=Search&cof=FORID:9#911)

also be sure to have a windows restore cd on hand incase something goes wrong.

---

### Post by coffeecat on 2011-07-21
If your D: partition is an internal one it will be seen in the "Places" left pane of a Nautilus browser. (And in the Places menu if you are using the classic gnome desktop.) Simply click on it and the browser window will open in the "D:" filesystem. It will not be called "D:" because this is a Windows convention. In the Places list it will appear either with the partition label (if there is one) or the filesystem size. What you could do is to rename your D: partition in Windows with some distinctive name (say "Personal_Files") and then reboot into Ubuntu and it should be easily identifiable.

See:

[https://wiki.ubuntu.com/WubiGuide#How_do_I_access_the_Windows_drives.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_access_the_Windows_drives.3F)

---

