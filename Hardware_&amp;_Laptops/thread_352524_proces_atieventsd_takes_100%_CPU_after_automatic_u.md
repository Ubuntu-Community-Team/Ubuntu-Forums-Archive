---
title: "proces atieventsd takes 100% CPU after automatic upgrade atidrivers"
date: 2007-02-03
forum: Hardware &amp; Laptops
---

### Post by Mr. Eddy on 2007-02-03
Hi

Here's my problem. I installed dapper and after that I installed my atidriver as described in the wiki. Later I dit een apt-upgrade and there were new drivers installed. After reboot I had this proces 'atieventsd' taking my whole processor. I can stop the froces without something to happen.

Can someone help me to fix this problem

---

### Post by lo900 on 2007-02-19
me too, and I have to kill it (when I boot with the the new 2.6.15.28 )
but when I reboot with the old 2.6.15.27 all is ok.

any idea

thanks

---

### Post by akatwofaced on 2007-03-03
I just realized that I had the same problem after upgrade to 2.6.15.28. I just turned off the process manually by running "sudo /etc/init.d/atieventsd stop". I guess I'll just patiently wait until ATI fixes this problem. Anyone has any idea how to fix this.Thanks.

---

### Post by brodiepearce on 2007-04-06
I have the same problem too, I'm going to assume it's due to an automatic update as it only showed up after I did an update yesterday.

There's another thread on this [here]("http://ubuntuforums.org/showthread.php?t=339390&highlight=atieventsd") too.  This is going to be hilarious if everyone running fglrx drivers experiences this.

---

### Post by kgr132 on 2007-04-13
Same problem here. After upgrading to 2.6.15.28 kernel today, atieventsd is using all of my CPU. Stopping the process manually helps, but it's kind of a pain to do it every time I reboot. Any advice?

---

### Post by kgr132 on 2007-04-14
For me, the solution was to completely  reinstall my original ATI driver package. I used Method 2 from here:

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

I substituted my original driver version 8.28.8 for my Mobility 9000 (R250) that I'd previously downloaded from the ATI web site in place of the one mentioned in the wiki. During the re-install, I got a message about "downgrading", so I assume something that came with the kernel update messed up my ATI driver packages. Be careful reading about the supported cards for the driver versions available on the ATI web site. The first time around I just used the newest version available from ATI and completely broke my X. It turned out that my video card was no longer supported in the newest driver version and I had to use an earlier one.

---

