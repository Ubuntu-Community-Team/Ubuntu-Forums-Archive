---
title: "graphics cards"
date: 2008-03-15
forum: Hardware &amp; Laptops
---

### Post by jolx on 2008-03-15
im upgrading my graphics card and not sure if i should get an 8600GTS or an 8800GT.
1st of all is one going to be easier to get working?
and is there a big difference in performance?

---

### Post by schiznik on 2008-03-15
the 8800GT is more powerful than the 8600 - have a look at the [tomshardware.com vga charts]("http://www23.tomshardware.com/graphics_2007.html"). You might want to have a look at the new 9600GTs - roughly as powerful as the 8800gt in some areas, but cheap (£100-£150, not sure what that is in Aus $)

There shouldnt be any need to do anything, just pull the 7300 that you have in there and pop the new one in.

---

### Post by jolx on 2008-03-15
thanks
for me the 8800GT's are ~$250 and the 9600GT's ~$230
apparently the 9600GT's have a problem with kernel versions > 2.6.23, will this still be a problem when the final hardy comes out?

---

### Post by Neo0351 on 2008-03-15
> apparently the 9600GT's have a problem with kernel versions > 2.6.23, will this still be a problem when the final hardy comes out?

I sure hope not.  I went from my sad little 7300LE to the 9600GT and all I can say is WOW.  I'm using the 171.06 driver and it gets the job done, but its a beta driver.  It's not hard to install the driver.  I hear the 8800 series doesn't work out of the box either, but you can use envy to install the driver.  Here's how I got my working for reference if you go with a 9600GT

Download the driver
[ftp://download.nvidia.com/XFree86/Linux-x86_64/171.06](ftp://download.nvidia.com/XFree86/Linux-x86_64/171.06)

Then grab what the driver needs to compile.
```
uname -r
sudo apt-get install linux-headers-'uname -r'
sudo apt-get install linux-restricted-modules-'uname -r'
sudo apt-get install linux-source-2.6.22 build-essential
```

Of course make sure to replace 2.6.22 with whatever kernel you're using

Then ctrl+alt+F1 and log in as root

```
killall gdm
chmod a+x /location/to/driver
sh /location/to/driver
```

follow the directions, then

```
nano /etc/default/linux-restricted-modules-common
```

The last line should look like

```
DISABLED_MODULES="nv"
```

After that cross fingers and reboot

---

### Post by PopnPaul on 2008-03-15
> **schiznik said:**
> the 8800GT is more powerful than the 8600 - have a look at the [tomshardware.com vga charts]("http://www23.tomshardware.com/graphics_2007.html"). You might want to have a look at the new 9600GTs - roughly as powerful as the 8800gt in some areas, but cheap (£100-£150, not sure what that is in Aus $)

There shouldnt be any need to do anything, just pull the 7300 that you have in there and pop the new one in.

Yeah defn not. the 8800GT is way better than the 9600GT. 112 sp's vs 64 sp's. 9600GT in SLi works very well though.

---

### Post by jolx on 2008-03-15
i was thinking about that but then ive read too many reviews saying that 8800GT's are hot and loud, which is definitely not what i want and the 9600GT's are ~$30 more than the 8600GTS's but about a 90% increase in performance, so i think ill get the 9600GT :confused:

---

