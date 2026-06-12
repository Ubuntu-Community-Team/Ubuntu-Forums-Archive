---
title: "Slower boot time"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by pnw on 2009-11-01
After the upgrade from 9.04 my boot time has doubled, from 19 seconds to about 40 seconds.
When booting i first get what seems to be the shutdown splash thingy ( [http://3.bp.blogspot.com/_FJH0hYZmVtc/St9n3Icl3mI/AAAAAAAAD_s/Xk22LKz2VN4/s1600-h/karmic_shutdown.png](http://3.bp.blogspot.com/_FJH0hYZmVtc/St9n3Icl3mI/AAAAAAAAD_s/Xk22LKz2VN4/s1600-h/karmic_shutdown.png) ) then after awhile i get the 'normal' boot splash thing ( [http://2.bp.blogspot.com/_FJH0hYZmVtc/St9cIC7g6XI/AAAAAAAAD9c/ST943-FE8Qc/s1600-h/xsplash-3%5B3%5D.png]("http://2.bp.blogspot.com/_FJH0hYZmVtc/St9cIC7g6XI/AAAAAAAAD9c/ST943-FE8Qc/s1600-h/xsplash-3%5B3%5D.png") ).

I cant figure out what has happened :S

My hdd is formatted to ext 4.
If you need any more information please ask

Thanks

---

### Post by pnw on 2009-11-02
*cough* bump *cough*

---

### Post by peter d on 2009-11-02
I have exactly the same issue. I'm afraid I have no solution but would be interested if anyone else can suggest one.

I'm still using Ext3.

Everything else seems perfect. It seems as if there's a false start to the booting process.

---

### Post by andrewabc on 2009-11-02
It is normal to get both animated graphics when starting computer.

When you state boot time has gone from 19 to 40 seconds, what are you timing? power button to desktop? bootchart? GRUB to desktop?

Install bootchart (search synaptic) and maybe it will tell us what is making it take longer to boot.
Once installed and you reboot a couple times, you can find images at /var/log/bootchart/ Upload one where your uploading your other images.

Do you have other partitions on the hard drive? Only one hard drive? laptop/desktop? What's your computer specs?

---

### Post by Dasda on 2009-11-02
I agree, My boot time has doubled too with same screens coming up. I thought it was normal but I guess it might be abug. thanks in advance.

---

### Post by pnw on 2009-11-15
[FONT=monospace]Sorry
for not replying, didn't get an email saying a reply had been posted on this topic. I will look bootchart when i have time but for now:

I have a Samsung q45(NP-Q45A007/SUK) Lappy with:
Intel Core 2 Duo T7500 (2.20GHz)
2Gb RAM
200 GB SATA HDD (5400rpm) - 11GB unrecognised :S, 107GB NTFS partiton, 80 ext4, 2gb swap
some intel integrated mobile graphics

I'm timing from pressing enter on grub to login screen. The reason i thought that having the two login screens was odd is because it doesn't happen on my friends pc, or atleast i don't think it does.

[/FONT]

---

### Post by pnw on 2009-11-15
here are the boot graphs

[Graph1]("http://tinyurl.com/bootgraph1")
[Graph2]("http://tinyurl.com/bootgraph2")

Thanks

---

### Post by andrewabc on 2009-11-18
Is your friend running 9.10?
There was only the one splash screen on 9.04. 9.10 has two now. Although with my SSD I only see the first one for 1 second.

I don't see anything odd in bootchart. Other than it is taking you same length of time to boot as my old pentium4 desktop does.

Probably biggest thing slowing boot time is hard drive. But then I'm not sure why it is booting slower than 9.04. It should be around same.

Do you have autologin (no user/password needed when starting) enabled?

---

### Post by pnw on 2009-11-18
Mr friend is running 9.10 but i might have been mistaken about the single boot screen. I am timing till the login screen appears, no i don't have autologin, which is the same as when i had 9.04.

thanks pnw

---

