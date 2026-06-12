---
title: "Terminal Session Screen Resolution Question"
date: 2008-11-30
forum: General Help
---

### Post by Predatorian on 2008-11-30
Hello, 
I was wondering how would i go about changing the Terminal Session default screen resolution from 80 characters to say 1024, keeping a size 12 or 16 font? im talking about a real terminal, not the one in X, but like when you press Ctrl+Alt+F2. thanks for any help.

---

### Post by KeyserSoze93 on 2008-11-30
add "vga=791" to your kernel entry in /boot/grub/menu.lst, for more info, google "ubuntu framebuffer"

---

### Post by lswb on 2008-11-30
> **KeyserSoze93 said:**
> add "vga=791" to your kernel entry in /boot/grub/menu.lst, for more info, google "ubuntu framebuffer"

That alone will probably not work in ubuntu; it does not enable framebuffer by default. It can be enabled by adding some modules to the initrd.img that is loaded at boot. If you don't find instructions for doing this via google post back here.

---

### Post by Predatorian on 2008-12-01
i found a tutorial when i googled "ubuntu framebuffer" it didnt give me the nitty gritty like TLDP did, which most of it when over my head, but i realize it was talking about older video cards and drivers. here is that URL for the tutorial:

[http://www.savvyadmin.com/console-framebuffer-in-ubuntu/](http://www.savvyadmin.com/console-framebuffer-in-ubuntu/)

---

### Post by lswb on 2008-12-01
Here is one I found on the forums for gutsy but it will work for hardy and intrepid as well. 

[http://ubuntuforums.org/archive/index.php/t-652038.html](http://ubuntuforums.org/archive/index.php/t-652038.html)

I would edit the files mentioned directly rather than fooling with that echo|tee|sed stuff, it is safer and you get to see the contents of the file, sometimes there are explanatory comments that will help you understand what's going on.

Just make backups in a safe place and edit where necessary with "sudo vi filename" or "sudo nano filename" or for a gui editor you can use "gksudo gedit"

If you have any questions post them to this thread and I will try to help. After you get the framebuffer working there are a few programs you may want to try out, like fbi image viewer and links2 graphical browser that can run in a vt without X, not to mention different text-mode programs that all work so much better with the higher resolution console. With a vga mode of 0x317 or 0x318 (decimal 791 or 792) your vt will have 48 lines of 132 characters.

---

### Post by Predatorian on 2008-12-01
what are the names of those programs, or are they on a website? i found one called [http://www.cli-apps.org]("http://www.cli-apps.org"). some of them are a little iffy, but i found a sudoku program that i would be interested in workign with. i also found rTorrent, which is super nifty. 

but as for the framebuffer, i wouldnt expect the people of *buntu to change that very much, it should be a standardized thing. so it should be all the same modules and blacklisted items for gusty on up, i would hope. thanks though guys. ya'll helped a lot.

---

