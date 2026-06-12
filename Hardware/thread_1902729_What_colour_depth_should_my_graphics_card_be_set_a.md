---
title: "What colour depth should my graphics card be set at?!"
date: 2011-12-31
forum: Hardware
---

### Post by teh'p3nsi0n3r on 2011-12-31
Everything is working as it should. I am using a ATI HD 5570 grahpics (ASUS EAH 5570). I just think the colour. (wallpapers etc.) show show a little degradation. 

I ran this command in the terminal, with the following output:

> :~$ cat /etc/X11/xorg.conf | grep Depth
	DefaultDepth     24
	DefaultDepth     24
		Depth     24
	DefaultDepth     24
		Depth     24


I'm sure the graphics should be higher than this?. If so, how can I amend this. I have looked in the ATI Catalyst Control Center, I can't see an option to change this.

ATI catalyst control center version 11.8. from default, 11.10 install. I am using this from the restricted drivers. Also running Unity.

---

### Post by MoreOrLess on 2011-12-31
Depth 24 (which is actually 32) is correct for modern GPU's.

Unity and Catalyst are known for not playing nice together. You may want to try Catalyst 11-12.

---

### Post by teh'p3nsi0n3r on 2011-12-31
> **MoreOrLess said:**
> Depth 24 (which is actually 32) is correct for modern GPU's.

Unity and Catalyst are known for not playing nice together. You may want to try Catalyst 11-12.

Thanks for your quick reply.

Is this a straight forward update?.

---

### Post by MoreOrLess on 2011-12-31
As long as you completely remove the current driver install and build packages with the new installer, it is fairly straightforward.

[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx)

[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

---

