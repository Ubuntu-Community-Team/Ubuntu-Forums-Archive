---
title: "how to remove vista from ubuntu !?"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by drwolf on 2009-07-06
i had recently installed ubuntu 8.10 along with vista in same partition  ( dual boot ) and i like it a lot , now i am thinking to remove vista in order to get more space 
do somebody know how to do so 
thanks

---

### Post by darolu on 2009-07-06
The easiest way would be formatting the Vista partition, you can do it with GParted (install it with add/remove or synaptic) and then editing GRUB to remove vista from it. To do this you can comment (by adding # at the beginning of the line) Vista lines from my /boot/grub/menu.lst file, using StartUpManager may work too.

---

### Post by elitenoobboy on 2009-07-06
After you do what darolu said, you can make use of the extra space created also by using gparted, but you will have to boot with the live cd (gparted is on the live cd by default) to expand the ubuntu partition (I am assuming that's how you want to use the extra space). It should be easy to do with the partition editor. Make sure to backup your data first.

---

### Post by JC Cheloven on 2009-07-06
> **drwolf said:**
> i had recently installed [COLOR="Red"]**ubuntu 8.10 along with vista in same partition**[/COLOR]  ( dual boot ) and i like it a lot , now i am thinking to remove vista in order to get more space 
do somebody know how to do so 
thanks

Hey, I think you installed ubuntu under windows using wubi or something similar. This is not a true dual boot ! The ideas on the previous posts are not applicable in that case.

As far as I know, there is no way to wipe windows while retaining the inner linux install. It would have be different with a true dual boot.

I suggest you to save your valuable data first, and then doing a fresh ubuntu install with the "use entire disk" option.

---

### Post by lukeiamyourfather on 2009-07-06
Assuming you used Wubi? This might be of interest from the Wikipedia article about Wubi.

> While Wubi does not install Ubuntu directly to its own partition (which the developers consider a feature) this can also be accomplished by using LVPM, the Loopmounted Virtual Partition Manager, to transfer the Wubi-generated Ubuntu installation to a dedicated real partition, including a bootable USB keydrive.[1] 

[http://en.wikipedia.org/wiki/Wubi_%28installer%29](http://en.wikipedia.org/wiki/Wubi_%28installer%29)

Check that out. If that's not what you're talking about then you'll have to clarify a little more on what you want to do. Cheers!

---

### Post by drwolf on 2009-07-07
yes it was wubi install !! and both of them are in same partition .

---

### Post by raymondh on 2009-07-07
If you really want to remove Vista and just single-boot Ubuntu ...

- You can clean-install Ubuntu and "use entire drive" (on the partitioning part)
- You can use Gparted (from the liveCD) to delete all partitions and then create partitions for your ubunt (swap, root .. plus, /home and/or /usr) and then when you install, use MANUAL

Or, if you still want to dual-boot Ubuntu and Vista, you can uninstall UBUNTU from Vista (as it is a WUBI install), shrink Vista, and install Ubuntu on its' own partition.

So many choices.

For your reference/reading

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)
[https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?](https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?)
[http://ubuntuforums.org/showthread.php?t=1195503](http://ubuntuforums.org/showthread.php?t=1195503)
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html) 
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[http://www.psychocats.net/ubuntucat/a-home-users-successful-migration-strategy-from-windows-to-ubuntu-2/](http://www.psychocats.net/ubuntucat/a-home-users-successful-migration-strategy-from-windows-to-ubuntu-2/)

Happy Ubuntu-ing.

---

### Post by RD1 on 2009-07-07
Save yourself the headaches. Backup your data and do a clean install of Ubuntu using the entire disc.

---

