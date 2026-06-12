---
title: "Problems on the startup."
date: 2005-07-07
forum: Hardware &amp; Laptops
---

### Post by Pale on 2005-07-07
Please endure me, I'm fairly noob to this, and lack the common googling-skillz.

Well. The thing is that I mounted the windows partition to my warty ('cause my windows had crashed completely, being unable to boot). And while I was at it, I configured some permission-thingys at the Filesystem and set new login-greeters. It seemed to work at the time, I tested the things by logging out and back in. So everything seemed fine... ***Until...***

The next time I started the Warty, it complained about the gdm ("Server Authorization directory (daemon/ServAuthDir) is set to /var/lib/gdm but ths does not exist. Please correct gdm configuration /etc/gdm/gdm.conf"). The solution to that was removing the old gdm and apt-getting a new one (any editing to the gdm.conf was useless, because I'm an idiot, whee). So after I did this and restarted the new gdm, it booted as fas as to the nVidia-screen, so at that point, I was thrilled. But but after that it went right back to the usual command prompt.
So where's the problem? I haven't been able to get to the graphical greeter yet, and I'm stuck to the command line by so far...

Hoary has the exact same problem, having some crooked configs in the gdm.conf. But I presume the solution to that is the same as to this, so it's not too important.

And while I'm at it, how do you make a read-only directory writeable (can you)? I'm sure someone knows.

---

### Post by fig_jam_uk on 2005-07-07
ok semi easy one forst to make a directory writeale you can in console type

chdir /<route to dir>
sudo chmod 777 <foldername>

then enter your root password hey presto RW directory  [-X

---

### Post by fig_jam_uk on 2005-07-07
And the other problem...

when booted into console and ready to go type

startx

hopefully should work, let me know...

---

