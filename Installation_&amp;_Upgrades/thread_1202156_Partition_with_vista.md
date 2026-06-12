---
title: "Partition with vista ?"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by roomp3 on 2009-07-01
Hello

ok i installed ubuntu 9.04 on my PC along with windows vista
and when im on the partition step of the installation it gave me the option if i want to install it along with vista or not.
like this:
[IMG]http://news.softpedia.com/images/extra/LINUX/small/ubuntu904installation-small_007a.png[/IMG]

ok it was installed perfect . 


the problem.
now i wanted to do the same on my Acer Aspire Laptop
but when i reached the partition step , it gave me only 2 options :S
1. use entire desk (this will delete vista loader)
2. manual (advanced)

why it did ave me the same option like the PC installation ?
how do i install ubuntu with vista :(

Help 




Thanks

---

### Post by tvtech on 2009-07-01
for some reason your hard drive probably wasn't fully formatted, or had an empty partition. who knows? lazy imagers magic hard drive your guess is as good as mine.

as far as installing it on your acer with vista go into vistas disk management disable the page file. delete the pagefile.sys file reboot. defrag the poop outah your hdd. then use vistas resize tool to shrink the partition.  

once you've done this run the install again.  select manual.  install ubuntu to the unused partiion.  ENJOY

---

### Post by roomp3 on 2009-07-01
is there any other way to do that ?
it seems to be complicated

---

### Post by tvtech on 2009-07-01
unfortunately there really isn't with Vista if you use the linux programs like parted gparted qtparted etc.... it can render vista unusable.  

It's fairly easy.  all you have to do is right click on my computer in vista and go to properties then navigate to virtual memory and it's under a couple tabs.  and disable it.  reboot the sytem and then find and delete the pagefile.sys.  reboot again then right click on my computer again. click manage disk and defragment the volume.  once you've done that right click the volume and click I think it's "shrink volume" button.  and it will give you how much you can shrink it by.  There are a number of tutorials on how to do this if you want a step by step just google "shrink vista partition"

the manual install is really easy to follow along with and there is little fear of damaging your system if you pay attention.

---

