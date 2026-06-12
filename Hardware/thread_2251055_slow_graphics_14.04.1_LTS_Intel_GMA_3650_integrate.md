---
title: "slow graphics 14.04.1 LTS Intel GMA 3650 integrated graphics"
date: 2014-11-01
forum: Hardware
---

### Post by geoffrussell on 2014-11-01
I recently upgraded my shuttle xs35v3l from 12.04 LTS to 14.04 LTS to try and resolve a bug

[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1300235](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1300235)

The bug is still present and the graphics is VERY slow. I was warned about this during the
upgrade but having upgraded another machine ad got the same warning (but which subsequently
worked fine), I proceeded. 

Does anybody have any idea how to find a suitable driver to fix this problem? Or if it will ever be
fixed?

Obviously there were drivers in 12.04 so what's chnaged to make them unavailable?

Thanks,

---

### Post by Mark Phelps on 2014-11-02
Drivers for Intel video chipsets are bundled with the kernel, so unlike with Nvidia or AMD, you don't go hunting around for drivers, or bother with Additional Drivers.

There is a link to an Intel site for drivers -- but I don't have any idea which one you need, or if they will do any good: [https://downloadcenter.intel.com/SearchResult.aspx?lang=eng&keyword=video%20drivers]("https://downloadcenter.intel.com/SearchResult.aspx?lang=eng&keyword=video%20drivers")

---

### Post by Bashing-om on 2014-11-02
geoffrussell; Hello;

There is also this thought, and it is only a thought :
Check out the Intel Graphics driver installer.
[http://www.webupd8.org/2013/03/intel-releases-linux-graphics-drivers.html](http://www.webupd8.org/2013/03/intel-releases-linux-graphics-drivers.html)
for the latest drivers direct from intel .

Be aware, if these drivers are installed, and do not work out, I have no idea how to revert the changes . Consider carefully what you do.


[INDENT][INDENT]kind regards
[/INDENT][/INDENT]

---

